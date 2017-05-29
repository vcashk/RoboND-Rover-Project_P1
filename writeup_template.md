## Project: Search and Sample Return
### Writeup Template: You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---


**The goals / steps of this project are the following:**  

**Training / Calibration**  

* Download the simulator and take data in "Training Mode"
* Test out the functions in the Jupyter Notebook provided
* Add functions to detect obstacles and samples of interest (golden rocks)
* Fill in the `process_image()` function with the appropriate image processing steps (perspective transform, color threshold etc.) to get from raw images to a map.  The `output_image` you create in this step should demonstrate that your mapping pipeline works.
* Use `moviepy` to process the images in your saved dataset with the `process_image()` function.  Include the video you produce as part of your submission.

Answer:

Executed the orignal notebook and evaluated the flow.

Recorded data was capture in "Training Mode", the data is storded in the "../test_dataset/Sim2" folder.

Functions were added to detect obstacles and samples of interest (golden rocks)
The process_image() function was filled with the appropriate image processing steps (perspective transform, color threshold etc.) to get from raw images to a map. 

The output_image was created, the results demonstrated that our mapping pipeline works.
The moviepy function was used to process the images our saved dataset with the process_image() function. Video is included as "new_test_mapping.mp4"


**Autonomous Navigation / Mapping**

* Fill in the `perception_step()` function within the `perception.py` script with the appropriate image processing functions to create a map and update `Rover()` data (similar to what you did with `process_image()` in the notebook). 
* Fill in the `decision_step()` function within the `decision.py` script with conditional statements that take into consideration the outputs of the `perception_step()` in deciding how to issue throttle, brake and steering commands. 
* Iterate on your perception and decision function until your rover does a reasonable (need to define metric) job of navigating and mapping.  


Answer:
The perception_step() function was filled within the perception.py script with the appropriate image processing functions to create a map and update Rover().
The decision_step() function within the decision.py was tuned for better deicision making .


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
*Several functions were added to the original python notebook :
*Prespective transform with the indicated source and destination point using opencv function warpPrespective and getPrespective.
*Detecting the rock samples:This was done by selcting the pixels between upper and lower RGB threshold (between 60,60,45, and 255,255,0)
*Detecting obstacles:This was done by selcting the pixels between lower RGB threshold of (160,160,160) however a lower threshold was also implemented to not select the black pixels the unknow regiond that is why a lower threshold of (3,3,3) was put in place.
*The rotation and translation functions were added based on the formulas provided during the lessons.
You may refer to the below images for the actual results obtained :
[//]: # (Image References)

[image1]: ./output/AutonomousNavigationandMapping/implementation.png

#### 1. Populate the `process_image()` function with the appropriate analysis steps to map pixels identifying navigable terrain, obstacles and rock samples into a worldmap.  Run `process_image()` on your test data using the `moviepy` functions provided to create video output of your result. 
And another! 

![alt text][image2]
### Autonomous Navigation and Mapping

#### 1. Fill in the `perception_step()` (at the bottom of the `perception.py` script) and `decision_step()` (in `decision.py`) functions in the autonomous mapping scripts and an explanation is provided in the writeup of how and why these functions were modified as they were.
*The prection_step() was filled in basically with most of the function used as used previously in the jupyter notebook only difference is that the Rover.Vision clearly mapped the enviroment under 3 different categories (Rock , obstacle and free space ) you may refer to the below image in the lower left showing this mapping. The simulation for autonomous navigation ran on linux under a resolution of 1024x768 with a graphics quality of "Good"

#### 2. Launching in autonomous mode your rover can navigate and map autonomously.  Explain your results and how you might improve them in your writeup.  

**Note: running the simulator with different choices of resolution and graphics quality may produce different results, particularly on different machines!  Make a note of your simulator settings (resolution and graphics quality set on launch) and frames per second (FPS output to terminal by `drive_rover.py`) in your writeup when you submit the project so your reviewer can reproduce your results.**

*The logic behind  the rover is that the Rover starts always with a move forward status, under a maximuim velocity limit.In case the rover finds a lack of navigable terrain (Rov.nav_angles) the rover will start slowing down  and turn into stop mode. The rover will then steer around until a suffecient navigable terrain is found and will move on forward.
Approach also includes in tuning the parameters to limit Rov.nav_angles to determine if the robot should keep moving forward or stop. 
Further velocity parameters tweaked in order to map most of the area in fastest way possible  
Results obtained: fidelty 56.9% and a mapping  81.3% details of settings included

[image2]: ./output/AutonomousNavigationandMapping/AutonomousModel.png
[image3]: ./output/AutonomousNavigationandMapping/Settings.png
![alt text][image3]


