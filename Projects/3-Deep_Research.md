# Create Your Own Deep Research

## Due on or before 3/21


## Overview

For this, the final project, we're going to create our own version of **Deep Research**. Every AI company is now rolling out a tool with this name that can perform *agent-based search*.

All of the various Deep Research tools work by taking a query, performing a search for relevant documents, then evaluating those documents with a reasoning LLM. The evaluations may generate additional sub-queries, which then lead to more searches and evaluations, and so forth until the agent decides that the problem space has been explored. The final step synthesizes all of the results of the individual searches into a single document that provides an in-depth answer to the original question.

If you want to play with an example, you can use Perplexity's Deep Research for free. OpenAI's is currently the most powerful and can generate white paper-style reports that go into the multi-dozens of pages. [Here's an example of one of my searches](https://chatgpt.com/share/67c85eaf-53bc-800b-bcf3-6bfcaa7ebffc) on technology strategy.

## Background reading

- [An in-depth article on implementing deep search and research tools](https://jina.ai/news/a-practical-guide-to-implementing-deepsearch-deepresearch/). I recommend starting with the section below that gives an overview of the approach, then returning to this article to pick up some more details.

- Anthropic's article on [Building Effective AI Agents](https://www.anthropic.com/engineering/building-effective-agents). More general background on the agent concept and some typical architectures for agent-based applications.

The term "agent" itself is a bit tricky. There's no precise definition, and people are happy to label their tools as "agents" if they think it makes them sound more impressive.

A good working definition is that an agent is a program that uses an LLM to make some decision about its own operation. This could often include a loop, where the system continually evaluates its own plan or progress.

## Plan




## Example Google search code
The example below shows an example of using the Google API. Some details:

- It uses `.env` file to store the API and search engine keys and `load_dotenv` function to read them into the program. See the example below for the `.env` file.

- Use the search API key and the search engine ID that I e-mailed to you. The search engine is configured to search English-language Wikipedia pages.

```
"""
Using the Google search API

With help from Claude
"""

import os
import requests
from urllib.parse import urlencode
from dotenv import load_dotenv

def google_search(query, api_key, search_engine_id, **kwargs):
    """
    Perform a Google search using the Custom Search JSON API.
    
    Args:
        query (str): The search query
        api_key (str): Your Google API key
        search_engine_id (str): Your Search Engine ID
        **kwargs: Additional parameters to pass to the API
                 (e.g., num=10, start=1, etc.)
    
    Returns:
        dict: The JSON response from the API
    """
    base_url = "https://www.googleapis.com/customsearch/v1"
    
    # Default parameters
    params = {
        'q': query,
        'key': api_key,
        'cx': search_engine_id
    }
    
    # Add any additional parameters
    params.update(kwargs)
    
    # Make the API request
    response = requests.get(base_url, params=params)
    
    # Check if the request was successful
    if response.status_code == 200:
        return response.json()
    else:
        response.raise_for_status()

def extract_search_results(search_response):
    """
    Extract relevant information from the search results.
    
    Args:
        search_response (dict): The JSON response from the Google Search API
    
    Returns:
        list: A list of dictionaries containing information about each search result
    """
    results = []
    
    if 'items' in search_response:
        for item in search_response['items']:
            result = {
                'title': item.get('title'),
                'link': item.get('link'),
                'snippet': item.get('snippet'),
                'displayLink': item.get('displayLink')
            }
            
            # Add image information if available
            if 'pagemap' in item and 'cse_image' in item['pagemap']:
                result['image'] = item['pagemap']['cse_image'][0].get('src')
            
            results.append(result)
    
    return results

def main():
    # Load environment variables from .env file
    load_dotenv()
    
    # Get API credentials from environment variables loaded from .env file
    api_key = os.environ.get('GOOGLE_API_KEY')
    search_engine_id = os.environ.get('GOOGLE_SEARCH_ENGINE_ID')
    
    if not api_key or not search_engine_id:
        print("Error: Missing API credentials. Please create a .env file with GOOGLE_API_KEY and GOOGLE_SEARCH_ENGINE_ID values.")
        return
    
    # Example search query
    query = "Python programming"
    
    # Additional parameters (optional)
    additional_params = {
        'num': 5,       # Number of search results to return
        'start': 1,     # Start at the first result (pagination)
        'safe': 'active', # Safe search setting
        'lr': 'lang_en'  # Language restriction to English
    }
    
    try:
        # Perform the search
        search_response = google_search(query, api_key, search_engine_id, **additional_params)
        
        # Extract the relevant information
        results = extract_search_results(search_response)
        
        # Display the results
        print(f"Search results for: '{query}'\n")
        
        for i, result in enumerate(results, 1):
            print(f"Result {i}:")
            print(f"Title: {result['title']}")
            print(f"URL: {result['link']}")
            print(f"Description: {result['snippet']}")
            print(f"Display Link: {result['displayLink']}")
            if 'image' in result:
                print(f"Image: {result['image']}")
            print("-" * 80)
        
        # Display search information
        if 'searchInformation' in search_response:
            info = search_response['searchInformation']
            print(f"Total results: {info.get('totalResults', 'N/A')}")
            print(f"Search time: {info.get('searchTime', 'N/A')} seconds")
    
    except Exception as e:
        print(f"An error occurred: {e}")

if __name__ == "__main__":
    main()
```

### `.env`

Files starting with `.` are **hidden** in Linux: they don't show up in the default `ls` output unless you add the `-a` flag.

One strategy for managing your API credentials is to create a `.env` file that stores each property. Git ignores `.env` by default, so it won't get committed to any repository that you push your code to.

Here's an example of the `.env` file that stores the API parameters. 
```
# Google Search API Credentials
GOOGLE_API_KEY=your_google_api_key_here
GOOGLE_SEARCH_ENGINE_ID=your_search_engine_id_here
```
