# Aesthetics and Image Filters

<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F33056294-356b-4366-a5b0-9be7a7118205_1024x768.jpeg" width="500px" />

*Solarpunk city by the Japanese anime artist Imperial Boy. One of the best aesthetics. [More images here](https://www.iamag.co/the-art-of-imperial-boy/).*


## Overview


This activity will allow you to practice implementing photo filters with **Pillow**, a Python image processing library. In addition to continuing our work from the first week on code generation, it will help demonstrate how you can use AI to understand and work with unfamiliar libraries and execute your own vision.

## Image Filtering

<img src="https://taplink.st/p/6/2/0/4/44061545.jpg?0?0" width="300px" />

*An example of Instagram's Nashville filter, which gives a faded, de-saturated vintage effect and cools the image by emphasizing purple shades. [Go here](https://taplink.at/en/blog/how_to_use_instagram_filters_and_where_to_find_them.html) for more side-by-side examples of popular Instagram filters.*

### Overview

You're going to experiment with some image processing using a Python library called **Pillow**. The Pillow library is an interface to PIL, the *Python Image Library*, and supports a large number of standard image manipulation algorithms.

A key to this section is **having opinions**. Think about what looks good to you and what effect you'd like to see.


### Setup
Start your Codespace. Look at the terminal at the bottom of your screen. You should see that the terminal prompt is set to your top-level directory. It should look like this, with you username in place of `dansmyers`:
```
@dansmyers ➜ /workspaces/codespaces-blank $ 
```
Change to the `1-Generation` directory that we made in the last class. Type the following command in the terminal and press ENTER:
```
cd 1-Generation
```
You should see your terminal prompt update to indicate that you're now working inside the `1-Generation` folder.

### Copy files

Copy `monochrome_filter.py` and `warm_filter.py` to your `1-Generation` directory. You can do this by making new files with `touch`, then copying the code into each file. For example, in the terminal:
```
touch monochrome_filter.py
```
Then open `monochrome_filter.py` and paste the code from the file into it.

Download the `cute_yarn_robot.jpeg` image (made by my son using DALL-E 3) and then upload it to your codespace. You can upload by dragging the JPEG into your file browser panel, then dragging it into the `1-Generation` directory.

### Install Pillow
Finally, go into your terminal and run the command
```
pip install Pillow
```
`pip` is the *package installer for Python*, a way to add new libraries to your Python environment. If you don't already have Pillow installed as part of your codespace, the pip command will install it for you.

### Monochrome filter
Open and run `monochrome_filter.py`:
```
python3 monochrome_filter.py
```
It will produce a file named `monochrome_output.jpeg` that contains a grayscale version of the example image.

Tip: If you get an error related to finding the image file, double-check that it's inside your `1-Generation` directory.

Take a look at the code. There are several things going on here that are not *too* difficult to understand, but that we haven't talked about yet. Get some help from your AI: paste the program into your chat and ask Claude to explain what each line does. Do you have follow-up questions? If so, ask them.

### Color images

<img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*vL8arP3J2ivmZluhHVv6bQ.png" width="400px" />

*RGB color channels in a Van Gogh painting. [From this Medium article](https://medium.com/@ConnectCode/extract-rgb-channels-with-cicolormatrix-vfx-programming-e6425fec06bb)*

An image is, fundamentally, a rectangular grid of pixels, where pixel is a number representing the intensity of light measured at that position. Grayscale images have one number associated with each pixel:

- A pixel with value 0.0 is pure black
- A pixel with a value of 1.0 is pure white
- Pixels in between 0.0 and 1.0 are shades of gray

As you'll recall from grade school art, you can create new colors by blending primary colors. In regular art, these are usually red, yellow, and blue, but in computer graphics it's more common to create colors by blending red, *green*, and blue. This is called the **RGB color model**.

Color images are composed of three **channels**, representing the intensities of red, green, and blue light that make up each pixel. The blend of RGB values for a given pixel determines its specific color and qualities. For example, a pixel with the RGB values (.90, .10, .90) has a lot of red and blue and only a little green, so it would have a purple color.

Ask Claude to give you more information on RGB colors in images:

*I'm learning about image processing. Can you give me some information on the RGB color model and how it's used in digital images? Include some examples of how different red, green, and blue mixtures can correspond to different colors in the visible image.*


### Warm and cool filters

Look at and run `warm_filter.py`. It implements a filter that emphasizes the red and yellow tones of the image, while slightly de-emphasizing the cooler blue component. Experiment with changing the specific numbers in the filter and observe how that changes the output image. 

Paste the code into your AI and ask it for an explanation of how the warm filter is implemented. Again, paste the response in your log document.

Once you understand the warm filter, make a new file named `cool_filter.py`. Copy the warm filter code, then modify it to create a cool version.


### Vintage filter

Let's make a vintage-style filter that gives the image an effect like an old film photograph. Make a new file named `vintage_filter.py`.

Prompt the AI to modify the warm filter program and produce a vintage-style filter. Log your prompt and the response you get in your document. Include, in your own words, a brief summary of how the filter works. Remember that you can ask for clarification of any lines that don't make sense.

Now run the program and look at the output. What kind of "vintage" did you get? Is it like an old-time sepia-tinted photograph, like a 1980's Polaroid, or something else? Prompt the AI to change the filter, and iterate until you get a version that you like.


### a e s t h e t i c s

Finally, make one more filter for an aesthetic of your choice. Put your code in a file named `diy_filter.py`.

Use AI to help you by suggesting the visual style you want, getting some code, then adjusting the paramters or iterating. Practice using rich, descriptive prompting language to clarify what you want. For example,

*Modify the program to create hazy, soft, lush nostalgic filter. Add soft blur, as if viewing a memory that's a little out of focus, and make the image slightly washed out and desaturated. The goal is to remove anything harsh or discordant from the image and create a relaxing effect in the viewer.*

(You can experiment with this one if you want, but make up your own example.)
