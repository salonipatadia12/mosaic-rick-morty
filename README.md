# Mosaic

This project is used to create mosaic of your chosen images from a set of tiles.
A mosaic is a collection of images put together to make it look like another image. 

To make these you need to have many pictures of different color combinations. Something like every frame of a movie, or any other images.
Just make sure the no. of images are atleast 100.

We will use Pillow Library of Pythonfor working with the images.

Do not worry about the size of image, as the script will crop and resize them before generating the results.

Enter this in command line to run the script, as follows:

<pre>python mosaic.py &lt;image_file_path&gt; &lt;tiles_directory&gt;
</pre>

*   The `image_file_path` argument should contain the path to the image for which you want to build the mosaic.
*   The `tiles directory` argument should contain the path to the directory containing the tile images (the directory will be searched recursively, so it doesn't matter if some of the images are contained in sub-directories)
*   Make sure the parent directory of ```mosaic.py``` and the directories image, tiles is same.

For example:

<pre>python mosaic.py images/tu.jpg tiles/
</pre>

The images below show an example of how the mosaic tiles are matched to the details of the original image:

![Mosaic Image](rick-morty/images/tu.jpg)  
<span class="smallText">Original</span>

[![Mosaic Image Detail](rick-morty/morty.png)](rick-morty/result/result.jpeg)  

<pre>
Explaining the code:

The uses of variables is given in the python script itself.
We created a class named TileProcessor and in that class the first method is process tile method. This method 
crops the images off the tiles that are used for making the whole mosaic.
Next we have get tiles in which we declared two lists. Using the os package we will Traverse through the tile 
directory and segregate images into large and small tiles. Now we talk about a new class named TargetImage 
this has a get data method which will increase the size of the original image and return a list small image 
and large image. 

Following process id from the class TileFitter : fit_tiles method will get image data of the small part of 
the main image using ```get``` and will call the method 'get_best_fit_tile' which check the difference 
between both the selected tile and the arguement passed. This difference is calculated by the
method '__get_file_diff'.

ProgressCounter class is used for printing the progress of our proces in recursively searching the tiles 
directory and placing them at mosaic parts.

The class MosaicImage helps in determining the added tile to the final Mosaic Image that is going to be 
generated.This method is called by another method build_mosaic which will check the active worker CPU count
and will add help in adding tiles for new images. There is also a keyboard interrupt in between to help us 
stop the process by breaking the whole process.



The build_mosaic method is called by a new method ```compose```.  In a try block this method uses built-in 
method of multiprocessing ```Process``` and one of the arguement is 'build_mosaic' so to call it everytime for
each tile.

The final method that is going to run in the __main__ app is ```mosaic``` method which will collect image data 
and tile data using the classes TargetImage and TileProcessor.

In the __main__ of the script the 'mosaic' method is called with 2 system arguements, and that is how we give 
the command to run the script (Example given above).

END
</pre>
