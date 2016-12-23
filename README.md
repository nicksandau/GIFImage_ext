# GIFImage_ext
Extension of the GIFImage library on pygame.org written by Matthew Roe.

I found it here: http://pygame.org/project-GIFImage-1039-.html

Small bits of code - a couple of instance variables and methods have been added.
I've changed very little of Matthews code - most of the changes are additions,
but where I have made a change, I've commented out the original line so that
it's easy to see what was there vs. what is there now.

methods added:

next_frame()

    -pauses the animation if it is currently playing
    -advances to next frame if the animation is paused
    -goes to first frame if the current frame = frames[-1]
 
previous_frame()

    -inverse of next_frame()
 
slow_down()

    -slows the playback speed by increasing the 'duration' variable
     
speed_up()

    -increases the playback speed by decreasing the 'duration' variable
 
scale(scale_factor)

    -scale_factor is added to the image_scale variable - pass positive numbers to
     increase the image size, negative numbers to decrease size
         gif_image.scale(.05) #increases image size by 5%
         gif_image.scale(-.05) #decreases image size by 5%
    -in the .render method, pygame.transform.scale is called on the current frame if img_scale != 1
     and the width and height of the original image are multiplied by the image_scale value
     (It would be more efficient from a processing standpoint to copy all frames out to a new
      frame list as they are scaled, then use the cached frames in the new list for subsequent
      playback loops. That would be overkill for my needs though.)
    -the transformed image is assigned to a new surface which is blitted to the screen
     so that the original image quality is retained
   
reset_scale()

    -resets the img_scale value to 1
    
Persistant Problems:

    -there is still a pallet handling issue as described on the pygame.org website.
     Time permitting, I'll look into this, but I'm no expert on the GIF image format 
     and this was really a one-off kind of thing for a quick and dirty prototype for a 
     larger project.
