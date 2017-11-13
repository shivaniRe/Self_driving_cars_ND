# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./gray_image.png "GrayImage"
[image3]: ./blurred_image.png "BlurImage"
[image4]: ./masked_image.png "MaskedImage"
[image5]: ./cedges_image.png "CannyImage"
[image6]: ./line_image.png "LineImage"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I blurred the image by using Gaussian smoothing. Once I had the blurred image, I used Canny edge detection to detect edges in the image. Then I selected my region of interest and used Hough transform to detect straight lines within the selected region. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the slopes of each line segemnt and classifying the lines into right and left lines based on the slope value (if slope > 0, then right line and if slope < 0, then left line). Then I calculated the overall slope and intercept of the left and right lines using np.polyfit(). Using these slopes and intercepts and with the min and max y values, I drew lane lines on the image (y=mx+c).

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image2]![alt text][image3]
![alt text][image4]![alt text][image5]
![alt text][image6]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the region of interest changes in different scenarios. 

Another shortcoming could be (like in the challenge video) when there are curved lines, we cannot use straight lines to draw lanes.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to not specify a region of interest by specifying vertices. Rather, identify vertices from the image itself.



