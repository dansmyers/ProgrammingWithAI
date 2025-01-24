# Introduction to Bootstrap

## Background

Boostrap was originally developed by Mark Otto and Jacob Thornton at Twitter and was released as an open-source framework in 2011.

Bootstrap's main use is creating responsive, grid-based layouts. It provides convenient tools for dividing your page up into a layout of rows and columns and can automatically
adjust the layout based on the size of the viewing window, which is important for creating mobile-first sites. The framework also includes a set of style defaults that are 
better than your browser's bare HTML.

## Basic Bootstrap Layout

Here is an example HTML page that shows off the basic elements of Bootstrap. Put the following code in your `index.html` file.

```
<!doctype html>
<html>
    
    <head>
        
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" integrity="sha384-JcKb8q3iqJ61gNV9KGb8thSsNjpSL0n8PARn9HuZOnIxN0hoP+VmmDGMN5t9UJ0Z" crossorigin="anonymous">
        
    </head>
   
    <body>

        <!-- All Bootstrap content must be enclosed in a container div -->
        <div class="container">
            
            <!-- The container must contain one or more row divs -->
            <div class="row">
            
                <div class="col-6">
                    This is the left column.
                </div>   <!-- /col-6 -->  
                
                <div class="col-6">
                    This is the right column.
                </div>   <!-- /col-6 -->  
                
            </div> <!-- /row -->
            
        </div> <!-- /container -->
        
        <!-- JS, Popper.js, and jQuery -->
        <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
        <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js" integrity="sha384-9/reFTGAW83EW2RDu2S0VKaIzap3H66lZH81PoYlFhbGU+6BZp6G7niu735Sk7lN" crossorigin="anonymous"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js" integrity="sha384-B4gt1jrGC7Jh4AgTPSdUtOBvfO8shuf57BaghqFfPlYxofvL8/KUEfYiJOMMV+rV" crossorigin="anonymous"></script>
    </body>
    
</html>
```

Let's start by pointing out a few important things in this example.

### CDN Links

There is a link to the bootstrap CSS stylesheet in the `<head>` section. Similarly, there are three required JavaScript files being loaded at the bottom of `<body>`. Any HTML file you create that uses Bootstrap will contain these links at the same locations.

It's possible to setup your project so that the required files are hosted locally, rather than being loaded from a remote CDN site,
but we're going to stick with the link-based setup for now.

### `<div>` Tags

The page is made up of a series of `<div>` tags. Think of each `<div>` as representing a "division" of the page. By itself, `<div>` just functions like a `<p>` tag: it's main
purpose is to allow you to create **a named region of the page** that you can style and interact with.

**Everything** in Bootstrap runs off of `<div>` tags with attached class labels. If you want to do something in Bootstrap, there's a 90% chance you're going to do it by making
a `<div>` and then adding class labels that control the effect you want.

The downside of this approach is that you end up making a lot of `<div>` tags. Notice how I've used comments to mark the closing of each `<div>`: you want to do that or you'll
quickly get lost.

### Containers

Take a look at the first `<div>` inside the `<body>`. It has class label `container`.

**All page content must be inside a container**. Let me say that again: ***ALL PAGE CONTENT MUST BE INSIDE A CONTAINER***.

(Where must all page content be? ***INSIDE ONE TOP-LEVEL CONTAINER***.)

As you lay out the page, you're going to create additional rows and columns, discussed in more detail below, but everything you create must be enclosed by one top-level
container `<div>`.


### Rows and Columns

Bootstrap models the page as a series of one or more **rows**, with each row subdivided into **columns**.

Here is the core content from the example above:

```
        <!-- All Bootstrap content must be enclosed in a container div -->
        <div class="container">
            
            <!-- The container must contain one or more row divs -->
            <div class="row">
            
                <div class="col-6">
                    This is the left column.
                </div>   <!-- /col-6 -->  
                
                <div class="col-6">
                    This is the right column.
                </div>   <!-- /col-6 -->  
                
            </div> <!-- /row -->
            
        </div> <!-- /container -->

```

Inside the top-level container is a `<div>` with the class `row`. Inside that `<div>` are two columns, both with the class label `col-6`.

### The Twelve Columns

Bootstrap subdivides each row into **twelve equally spaced column units**. You can create column combinations that span any subset of the twelve column units.
In the example above, each column is labeled `col-6`: the two columns each span six of the twelve units and divide the page in half.

```
                          Full row spans 12 units
 -------------------------------------------------------------------------
|                                                                         |
v                                                                         v
 ------------------------------------ ------------------------------------
|                                    |                                    |
|               col-6                |               col-6                |
|                                    |                                    |
 ------------------------------------ ------------------------------------
```

You can use any combination of `col` classes to divide the row in any way that you want. For example, three four-unit columns will split the row into
thirds:

```
 ------------------------ ------------------------ ------------------------
|                        |                        |                        |
|         col-4          |         col-4          |         col-4          |
|                        |                        |                        |
 ------------------------ ------------------------ ------------------------
```

Creating unequal-width columns is useful:

```
 ------------------------------------------------- ------------------------
|                                                 |                        |
|                     col-8                       |         col-4          |
|                                                 |                        |
 ------------------------------------------------- ------------------------
```

Spanning all twelve units fills the entire row:

```
 --------------------------------------------------------------------------
|                                                                          |
|                                 col-12                                   |
|                                                                          |
 --------------------------------------------------------------------------
```

### Practice

Go back to your example and edit the column widths to create some different combinations.

Once you have tried two columns, and a third `<div>` (make sure it's within the row) and experiment with three-column layouts.

## Important Layout Rules (How to Not Screw Everything Up)

There are four layout rules that you must remember **and never violate** or terrible things will happen:

1. Everything must go into one top-level container `<div>`.

2. The only things that can be within the container are one or more rows.

3. Each row must contain one or more columns that span a total of twelve units.

4. The actual page content must only be placed within columns. 

Most Bootstrap layout errors are caused by violating the `container -> row -> column -> content` nesting rules. In particular, if you try to place page content outside of the
`container -> row -> column` structure, it will probably look like it's hanging in space, disconnected from the rest of the page layout.

**A super common error** is to put content in a row without declaring a column. You'd think this should work, but it doesn't.

If you spend some time reading other Bootstrap documents, you'll learn that there are cases where these rules can be relaxed. Notably, Bootstrap is smart enough to figure out
how to automatically space your columns in many cases, which can simplify how you declare your columns. For now, I recommend manually allocated all twelve units in each row
while you're getting comfortable with the layout rules.


## More Practice

Take a look at `hokusai.html` below, which shows off a few more feature. Try copying the page to a file and then opening it in your browser to see how the layout works.

### Responsive Layouts

Once you have the page up and running, experiment with changing the size of your browser. You should see the page content automatically shrink, then stack as the window gets smaller.

Bootstrap lets you control how the stacking behavior takes effect by adding size information to the column labels. In the `hokusai.html` file, you'll see columns labeled
with classes like `col-lg-8`. Here, the `lg` controls when the stacking behavior kicks in: specifically, it indicates that Bootstrap should start to stack the columns when the viewing window is smaller than 992 pixels, which is what Bootstrap considers to be "large". There are also `md`, `sm`, and other versions of the column classes that turn on stacking at different window sizes.

You don't need to memorize anything about the stacking behavior or the window sizes, but simply take comfort in knowing that it's one thing you can control in these turbulent times.


```
<!doctype html>
<html lang="en">
    <head>
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">

        <style>
            img {
                width: 100%;  <!-- Gives images 100% width of their parent element -->
            }
        </style>
        
        <title>A Bootstrap Example</title>
    </head>
    
    <body>
      
        <!-- A div is a division of the page -->
        <!-- Bootstrap runs off of divs with assigned classes -->
            
        <!-- Jumbotron is a big header for the top of the page -->
        <!-- text-center centers the text, bg-light makes the background light gray -->
        <div class="jumbotron text-center bg-light">
            <div class="container">

                <!-- The display classes make text big -->
                <h1 class="display-4">
                    <i>The Thirty-Six Views of Mount Fuji</i>
                </h1>
                
                <h2 class="display-4">
                    Katsushika Hokusai
                </h2>
            </div> <!-- container -->
        </div>
        
            
        <!-- All of the page's basic content must be in a container div -->
        
        <div class="container">

            <!-- Each row is a horizontal section of the page -->
            
            <!-- Each row is divided into 12 columns that evenly span the page -->
            <!-- You can group the 12 columns in any combination -->
            
            <!-- The row scales to the height of its tallest column -->
            <div class="row">
                
                <div class="col-lg-12 text-justify"> <!-- One big column that spans the whole row -->
                    <p>
                        <b>Katsushika Hokusai</b> (c. October 31, 1760 – May 10, 1849) was a Japanese artist, 
                        ukiyo-e painter and printmaker of the Edo period. Born in Edo (now Tokyo), 
                        Hokusai is best known as author of the woodblock print series 
                        <i>Thirty-six Views of Mount Fuji</i> (<i>Fugaku Sanjūroku-kei</i>, c. 1831),
                        which includes the internationally iconic print, <i>The Great Wave off Kanagawa</i>.
                    </p>
                    <p>
                        
                        Hokusai created the <i>Thirty-Six Views</i> both as a response to a domestic
                        travel boom and as part of a personal obsession with Mount Fuji. It was
                        this series, specifically <i>The Great Wave</i> print and <i>Fine Wind, Clear Morning</i>,
                        that secured Hokusai’s fame both in Japan and overseas. As historian Richard
                        Lane concludes, "Indeed, if there is one work that made Hokusai's name, both
                        in Japan and abroad, it must be this monumental print-series". While Hokusai's
                        work prior to this series is certainly important, it was not until this series
                        that he gained broad recognition.
                    </p>
                    
                    <p>
                        Example text from Wikipedia.
                    </p>
                    
                </div> <!-- col-lg-12 -->
                
            </div> <!-- Row -->
            
            <!-- Create a new row -->
            
            <!-- mt-4 is "margin-top", creates vertical space from the previous row -->
            
            <!-- An example of an offset layout -->
            <!-- The left column spans 4 of 12 units and the right spans 8 of 12 -->
            <div class="row mt-4">                            
                
                <div class="col-lg-4 text-justify">
                    
                    <p>
                        <b>The Great Wave off Kanagawa</b> (<i>Kanagawa-oki nami ura</i>, 
                        "Under a wave off Kanagawa"), also known as <i>The Great Wave</i> or simply
                        <i>The Wave</i>, is a woodblock print by the Japanese ukiyo-e artist Hokusai.
                        It was published sometime between 1829 and 1833 in the late Edo period
                        as the first print in Hokusai's series <i>Thirty-six Views of Mount Fuji</i>.
                        It is Hokusai's most famous work, and one of the most recognizable works of
                        Japanese art in the world.
                    </p>

                    <p>
                        The image depicts an enormous wave threatening boats off the coast of the
                        town of Kanagawa (the present-day city of Yokohama, Kanagawa Prefecture).
                        While sometimes assumed to be a tsunami, the wave is more likely to be a
                        large rogue wave. As in many of the prints in the series, it depicts the
                        area around Mount Fuji under particular conditions, and the mountain itself
                        appears in the background.

                    </p>
                    
                    <p>
                        Example text from Wikipedia.
                    </p>

                </div> <!-- col-lg-4 -->
                
                <div class="col-lg-8">
                    <p>
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Tsunami_by_hokusai_19th_century.jpg/2560px-Tsunami_by_hokusai_19th_century.jpg"/>
                    </p>
                </div> <!-- col-lg-8 -->
                
            </div> <!-- Row -->
            

            <div class="row mt-4">
                
                <div class="col-lg-8">
                    <p>
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/57/Red_Fuji_southern_wind_clear_morning.jpg/2560px-Red_Fuji_southern_wind_clear_morning.jpg" />
                    </p>
                </div> <!-- col-lg-8 -->
                
                <div class="col-lg-4 text-justify">
                    
                    <p>
                        <b>Fine Wind, Clear Sky</b> This print and Hokusai's other masterpiece from his <i>Thirty-six Views of Mount Fuji</i>
                        series, <i>The Great Wave off Kanagawa</i>, are perhaps the most widely recognized
                        pieces of Japanese art in the world. Both are superb examples of the
                        Japanese art of ukiyo-e, "pictures of the floating world". Although ukiyo-e can
                        depict anything from contemporary city life to classical literature, and Hokusai's 
                        notebooks show that his own interests spanned an equally wide range, it was
                        landscapes like this that earned him his fame. The saturated colors and stylized
                        forms in such prints helped inspire the Impressionist and Post-impressionist
                        movements decades later.
                    
                    <p>
                        Example text from Wikipedia.
                    </p>

                </div> <!-- col-lg-4 -->
                
            </div> <!-- Row -->
        
        </div>  <!-- Container -->
      
        <!-- Optional JavaScript -->
        <!-- jQuery first, then Popper.js, then Bootstrap JS -->
        <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script>
    </body>
</html>

```

