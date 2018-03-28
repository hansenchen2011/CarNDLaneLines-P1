# **Finding Lane Lines on the Road** 




**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Some reflections during the project on your work in a written report

---

### Reflection

### 1. Pipeline description:
In this project, I used Python and OpenCV to find lane lines in the test images and videos.

**The whole pipelines** are as below:
- Gaussian Blur
- Color Selection
- Canny Edge Detection
- Region of Interest Selection
- Hough Transform Line Detection
- Lines Processed to extract lanes
- Draw lanes on the images and videos  
For video a temporal average is used to decrease the flicking.

 **Lines Processed to extract lanes** is the alogrithm need to be mostly tuned:  

 The idea of this alogrithm is as below:
- sepeare line segments into left and right lines by slope
- remove outlier lines based on median absolut difference of slope
- caculate average slope and intrecept and weigh by line length for left and right lanes
- choose y_min and y_max
- caculate x_min and x_max using average intercept,slope,y_min and y_max

### 2. Identify potential shortcomings with the current pipeline


One potential shortcoming would be some dot lines in the heavy shadow not detected.   
Another shortcoming is that the thresolds are manually tuned for the delicated images and videos,which could cause failure in real scenarios in some complex light conditions. 


### 3. Possible improvements to the pipeline

A possible improvement would be to increase the robust of the edge and line detection by using information from previus frames,trying different color space and thresolds,and combing the detect results to get the final result.

Another potential improvement could be to use polynomial lines to fit the lanes since the lanes are not really straight due to perspective and lens distortion from camera.
### 4. Acknowledgement

Most funcitons' protypes are from Udacity's project Github.  
The Outlier reduciton comes from www.stackoverflow.com.  
The slope computation weighted by line length and the queue operation data structure is from Naoki Shibuya,
[Naoki's Github](https://github.com/naokishibuya/car-finding-lane-lines)  
Thank classmates for the valuable discussions.
