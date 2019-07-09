# **Finding Lane Lines on the Road** 



### 1. Pipeline Creation on static image

My pipeline for static image consisted of below steps
 
1. Convert the image to Gray Scale using cvtColor function

2. Applied the canny edge detection using the canny function with (255/3 and 255/2 as low and high treshold respectively)

3. A polygon is defined to identify the region of interest such that the lane region is covered

4. Then the image is sent to Hough transform to obtain the lines from the image

5. Then Draw line function was used to draw the Red lines on the lanes identified and also to extrapolate the lines where the lane is not continous

from the array of lines in the image, slope of the lines are calculated . if the slope is less than 0 (later made as 0.1 as the results for video were better) then the line is identified as left lane and right line otherwise and the sum of the slope and intecept of each line( left and right) is caluculated.

Now taking bottom of image as a point in y axis and using the mean of slope and intercept the bottom point x is calculated 
the second point is calculated using the silghtly higer than middle of image as a point in y axis

Now for left and right lane , a line is drawn from the bottom of image as 1st point and sightly middle of the lane as second point with average slope that is determined in previous step.

Below are the results of the 6 test images that were provided



![alt text](./Output/solidWhiteCurve.jpg?raw=true )solidWhiteCurve
![alt text](./Output/solidWhiteRight.jpg?raw=true )solidWhiteRight
![alt text](./Output/solidYellowCurve.jpg?raw=true )solidYellowCurve
![alt text](./Output/solidYellowCurve2.jpg?raw=true )solidYellowCurve2
![alt text](./Output/solidYellowLeft.jpg?raw=true )solidYellowLeft
![alt text](./Output/whiteCarLaneSwitch.jpg?raw=true )whiteCarLaneSwitch

the above image inupt were then provided to Video inputs solidWhiteRight.mp4 and solidYellowLeft.mp4 , the result was lanes were drawn but there were some stray line getting generated . this behaviour was high in challenge.mp4 video

So the slope range was fixed between 0.45 to 0.85 to draw the lane and avoid the stray lines

The final Video Output is Present in Output folder of this Notebook 
1. ![solidWhiteRight.mp4](./Output/solidWhiteRight.mp4)
2. ![solidYellowLeft.mp4](./Output/solidYellowLeft.mp4)
3. ![Challenge.mp4](./Output/challenge.mp4)

### 2.Potential shortcomings with  current pipeline


One potential short coming would be when there is steep curve as in challenge.mp4 Video there is a failure to draw and detect lines



### 3. Possible improvements to the pipeline

A possible improvement would be to have variable region of interest which might address the steep curve issue  

