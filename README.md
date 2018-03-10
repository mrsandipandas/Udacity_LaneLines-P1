# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Understand shortcomings of the current methodology


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.png "Solid White Curve"
[image2]: ./test_images_output/solidYellowCurve.png "Solid Yellow Curve"

---

### Reflection

### 1. Description of pipeline, and the draw_lines() function.

My pipeline consisted of 5 step:

* Define a kernel size and apply Gaussian smoothing.
* Define our parameters for Canny and applying edge detection.
* Masking out the region of interest, with a four sided polygon.
* Run Hough transformation on detected edge and get an array containing endpoints of detected line segments.
* Overlaying and extrapolating the curve from the set of detected lines.

Finally this is how my dtected lines look for example:
![Solid White Curve][image1]
![Solid Yellow Curve][image2]

In order to draw a single line on the left and right lanes, I modified the draw_lines():

The draw lie function was improved by segregating the points for the left part of the lane from the points of the right part of the lane by computing the slope of the lines. Then 1D extraploation was peformed to fit all the points found on the left and right part of the lane. Finally the min and max of X-axis of the mask area was defined to realize the lines.

### 2. Identify potential shortcomings with your current pipeline


* One potential shortcoming would be what would happen when there will be many curves in the lanes.
* In different lighting conditions this would behave abruptly.
* Moreover, different lane colour dtection would be a challenge.


### 3. Suggest possible improvements to your pipeline

* Use generalized hough transform to improve the curve detection
* I have tried 2nd order polynomial fitting for the extrapolation of the points in the detected lines. However, it did not go so well. So one thing can be done is to divide the x-range in different segments and try out extrapolation again.

### 4. Video of real-time straight line detector in lanes

https://youtu.be/eBQMEXqEuhw
