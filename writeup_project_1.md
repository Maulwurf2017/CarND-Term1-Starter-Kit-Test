# **Finding Lane Lines on the Road** 

## Writeup

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)


[image1]: ./examples/read_image.png

[image2]: ./examples/final_image.png

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 10 steps. 

step 1: define the global variable to hold the value of the x1,x2,y1,y2 of the left and right side lane from the previous frame. It help me to draw the lane even if the lane can't be detected.
step 2: define the function to transform the region of interst to the bird view image
step 3: apply color mask to find the yellow and white lane in the image
step 4: apply canny detector to the l and s channel of the image. We could find out that the s channel is resistant to the noise of shadows (like shadow of trees in the challenge video).
step 5: apply the canny edge detector to the gray scale image.
step 6: combine the output images from above (I ignored the s channel canny detected image)
step 7: Do the reverse perspective transformation to
step 8: do the hough space transformation to get the lane on the image.
step 9: draw the line back on a blank image.
step 10: add the image with lines on it and the original image to get the final image




### 2. Identify potential shortcomings with your current pipeline


In the draw line function,I've defined the slope to filter the line of shadow. But thers's still noise of the shadow that can't be filtered 100%. Also I've used the location of the lanes in the previous frame as help if the lanes can't be found with hough transformation. Because of this method, the location of the lane in the previous frame will influence the location in the current frame. The deviation will be accumulated. It will lead to deviation even the lane is correctly detected in the current frame.

I found out that the the canny detector on the s channel of the image is robut to shadow. But that also lead to information lose. Thus it wasn't implemented in my pipeline.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to improve the performance of the draw line function to overcome the shotcoming of the "accumulation effect" because of the 70% inherit of lane location described above.


