## Project: Search and Sample Return

**The goals / steps of this project are the following:**  

**Training / Calibration**  

*After downloading the simulator and take some data in the "Training Mode", functions are tested in the Jupyter Notebook provided with the repository.
*Golden rocks are found with the find_rocks function which detects high red and green (above 110) and dim blue pixels (below 50) in the RGB channels. The golden rocks when examined can be found to have high red and green and low blue values in their RGB channels.
*Obstacles are to be found with the mask and color_thresh functions. All pixels that are not in the view of the rover camera can be identified as obstacles and multiplying mask with the non-navigable terrain found from threshed (threshed - 1) gives us the ultimate obstacle map.

**Populating the process_image function:
*Source and destination is defined on the perspect_transfrom function and works fine. Then, for both warped and mask the perspective transform is applied. Warped view gives us the light and dark areas which light areas are where the navigable terrain are. Mask is a filter for defining rover's camera's sight. Area in white is the sight of the rover.
*Color thresh function is provided with the Udacity project 1 repository is used for the warped view and from there as defined above the obstacle map is gathered.
*Rover-centric coordinates are provided from the rover_coords function using threshed. Then the rover-centric coordinates are converted to world coordinates with the pix_to_world function provided with the project repository. The function gets rover-centric x and y, rover's x, y position and yaw, shape and scale as inputs. Obstacle pixel values are also converted to world coordinates with the same function.
*Worldmap parametes are updated for the navigable terrain and obstacles with the world coordinates found. Rocks are also marked in the worlmap with the help of find_rocks function explained above. Rocks' x and y rover-centric coordinates are changed to world and then updated on the worldmap. Rock_y_world and Rock_x_world parameters are set to 255 for visibility.
*Mosaic image code is used as is from the project repository as well as moviepy function to make the video from the processed image.

**Autonomous Navigation / Mapping**

* Fill in the `perception_step()` function within the `perception.py` script with the appropriate image processing functions to create a map and update `Rover()` data (similar to what you did with `process_image()` in the notebook).
* Fill in the `decision_step()` function within the `decision.py` script with conditional statements that take into consideration the outputs of the `perception_step()` in deciding how to issue throttle, brake and steering commands.
* Iterate on your perception and decision function until your rover does a reasonable (need to define metric) job of navigating and mapping.  

[//]: # (Image References)

[image1]: ./misc/rover_image.jpg
[image2]: ./calibration_images/example_grid1.jpg
[image3]: ./calibration_images/example_rock1.jpg

## [Rubric](https://review.udacity.com/#!/rubrics/916/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  

You're reading it!

### Notebook Analysis
#### 1. Run the functions provided in the notebook on test images (first with the test data provided, next on data you have recorded). Add/modify functions to allow for color selection of obstacles and rock samples.
Here is an example of how to include an image in your writeup.

![alt text][image1]

#### 1. Populate the `process_image()` function with the appropriate analysis steps to map pixels identifying navigable terrain, obstacles and rock samples into a worldmap.  Run `process_image()` on your test data using the `moviepy` functions provided to create video output of your result.
And another!

![alt text][image2]
### Autonomous Navigation and Mapping

#### 1. Fill in the `perception_step()` (at the bottom of the `perception.py` script) and `decision_step()` (in `decision.py`) functions in the autonomous mapping scripts and an explanation is provided in the writeup of how and why these functions were modified as they were.


#### 2. Launching in autonomous mode your rover can navigate and map autonomously.  Explain your results and how you might improve them in your writeup.  

**Note: running the simulator with different choices of resolution and graphics quality may produce different results, particularly on different machines!  Make a note of your simulator settings (resolution and graphics quality set on launch) and frames per second (FPS output to terminal by `drive_rover.py`) in your writeup when you submit the project so your reviewer can reproduce your results.**

Here I'll talk about the approach I took, what techniques I used, what worked and why, where the pipeline might fail and how I might improve it if I were going to pursue this project further.  



![alt text][image3]
