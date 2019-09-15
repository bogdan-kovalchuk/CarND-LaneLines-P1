# **Finding Lane Lines on the Road** 

### Reflection

### 1. Describe your pipeline.

[im1]: test_images/solidWhiteCurve.jpg
[im2]: writeup_images/gray.jpg
[im3]: writeup_images/blur_gray.jpg
[im4]: writeup_images/canny.jpg
[im5]: writeup_images/masked_edges.jpg
[im6]: writeup_images/hough_lines.jpg
[im7]: writeup_images/image_with_lines.jpg

My pipeline consists the next 7 steps:

1.1. Loading and resize image to size appropriate for detection algorithms (960, 540)

![alt text][im1]

1.2. Grayscale the image

![alt text][im2]

1.3. Apply Gaussian smoothing

![alt text][im3]

1.4. Run Canny algorithms to detect lane lines

![alt text][im4]

1.5. Cut the lanes which are outside ot the region defined by the polygon

![alt text][im5]

1.6. Run Hough transform on edge detected image

This step consists some sub-steps:

1.6.1. Group and filter lines on left and right with slope

1.6.2. Extrapolate lines to tip and bottom border of the region

1.6.3. Average all lines to one line

![alt text][im6]

1.7. Draw right and lift lane lines on the initial image

![alt text][im7]


### 2. Identify potential shortcomings with your current pipeline

2.1. The region of interest was hardcoded to current set of images/videos and therefore is not dynamic and for another conditions it will not work correct.

2.2. The slope by which the right and left lines were determined was hardcoded and such approach will not work correctly on curved road and junctions.

2.3. The Canny algorithm works within color threshold and therefore in conditions of sufficient illumination or when the lines are very illuminated, the result will not be correct


### 3. Suggest possible improvements to your pipeline

3.1. To come up with an algorithm in which hardcoded values will be selected from the initial image conditions or computed based on some other algorithms

3.2. To come up with dynamic filter of threshold for Canny algorithms based on illumination conditions

3.3. Approximate lines by a polynomial of the third degree

3.4. Consider previous state to filter incorrect detection
