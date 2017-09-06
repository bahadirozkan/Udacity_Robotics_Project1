
## Project: Search and Sample Return


This project is modeled after the [NASA sample return challenge](https://www.nasa.gov/directorates/spacetech/centennial_challenges/sample_return_robot/index.html) and it will give you first hand experience with the three essential elements of robotics, which are perception, decision making and actuation.  You will carry out this project in a simulator environment built with the Unity game engine.  

### The Simulator
The first step is to download the simulator build that's appropriate for your operating system.  Here are the links for [Linux](https://s3-us-west-1.amazonaws.com/udacity-robotics/Rover+Unity+Sims/Linux_Roversim.zip), [Mac](	https://s3-us-west-1.amazonaws.com/udacity-robotics/Rover+Unity+Sims/Mac_Roversim.zip), or [Windows](https://s3-us-west-1.amazonaws.com/udacity-robotics/Rover+Unity+Sims/Windows_Roversim.zip).  

### Dependencies
You'll need Python 3 and Jupyter Notebooks installed to do this project.  The best way to get setup with these if you are not already is to use Anaconda following along with the [RoboND-Python-Starterkit](https://github.com/ryan-keenan/RoboND-Python-Starterkit). 


Here is a great link for learning more about [Anaconda and Jupyter Notebooks](https://classroom.udacity.com/courses/ud1111)

### The goals / steps of this project are the following:

**Training / Calibration**

After downloading the simulator and take some data in the "Training Mode", functions are tested in the Jupyter Notebook provided with the repository.

Golden rocks are found with the **find_rocks** function which detects high red and green (above 110) and dim blue pixels (below 50) in the RGB channels. The golden rocks when examined can be found to have high red and green and low blue values in their RGB channels.

Obstacles are to be found with the **mask** and **color_thresh** functions. All pixels that are not in the view of the rover camera can be identified as obstacles and multiplying mask with the non-navigable terrain found from threshed **(threshed - 1)** gives us the ultimate obstacle map.

**Populating the process_image function:**

Source and destination is defined on the **perspect_transfrom** function and works fine. Then, for both warped and mask the perspective transform is applied. Warped view gives us the light and dark areas which light areas are where the navigable terrain are. Mask is a filter for defining rover's camera's sight. Area in white is the sight of the rover.

Color thresh function is provided with the Udacity project 1 repository is used for the warped view and from there as defined above the obstacle map is gathered.

Rover-centric coordinates are provided from the **rover_coords** function using threshed. Then the rover-centric coordinates are converted to world coordinates with the pix_to_world function provided with the project repository. The function gets rover-centric **x** and **y**, rover's **x**, **y position** and **yaw**, **shape** and **scale** as inputs. Obstacle pixel values are also converted to world coordinates with the same function.

Worldmap parametes are updated for the navigable terrain and obstacles with the world coordinates found. Rocks are also marked in the worlmap with the help of **find_rocks** function explained above. Rocks' x and y rover-centric coordinates are changed to world and then updated on the worldmap. **Rock_y_world** and **Rock_x_world** parameters are set to **255** for visibility.

Mosaic image code is used as is from the project repository as well as moviepy function to make the video from the processed image.

**Autonomous Navigation / Mapping**

Similar steps has been followed with the Jupyter notebook to create the **perception.py**. After providing **Rover.nav_angles** to the **decision.py** the rover somewhat starts to autonomously navigates. I have benefited from the project walkthrough video and plan to upgrade the navigation of the rover in the near future. 
