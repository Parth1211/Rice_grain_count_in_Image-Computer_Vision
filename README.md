# Rice_grain_count_in_Image-Computer_Vision
Summary
Through this, we could find the number of rice grains in this image, it could have been any other object as well(ball, stars in the night sky etc).

This was the procedure I followed-
1) Loading image from the drive, and then passing it through the sharpening kernel(*)(this reason will be explained later on).

2) Converting the BGR image to RGB image, as we use RGB images in processing.

3) And then we convert it to aa grayscale image, as we would be needing a binary(black and white image), for better result.

4) Then on converting it to binary image I found out a lot of noise in the image, as the "threshhold" values set in the filter for it to convert to binary image were too low, that is, the values of gray pixels(0-255) for which it was convreting them to black pixels was too low. Therefore, I regulated the values to the extent till which I could remove most of the noise, the rice grains being uneffected.

5) Still, a lot of noise was visible in the image, hence I passed it through the median removal kernel, which removes Salt and Pepper noise(the type of noise my image had). And then I got the final image, I worked upon.

6) Then finally I used the OpenCV function cv2.findContours(), which as the name says, finds contours on the objects in the blaack and white image I had prepared, and then cv2.drawContours() draws contours that it recorded by the previous function, on the image we pass through it. cv2.RETR_TREE, cv2.CHAIN_APPROX_NONE are the 2 parameters of cv2.findContours() which I used to store contours of my image. And then I printed the number of contours(according to the function).

(*) - There are some rice grains that are very close to each other, and they have shared borders. Hence by sharpening the images, I reduced the number of such shared borders, which would have caused problem while detection of contours.

Scope of improvement-
I can still see that some rice grains which are very close to each other are being counted as a single cotnours, though I have decreased such an error to a great extent by the point(*) I mentioned above. And there is still some noise in the image, due to which there is an increase in the number of contours being detected, we can also think of reducing that to some more extent(some further proccesing in my point 5th point ).

Right now the model predicts the number of rice grains to be 108, and after counting it manually I found out 116 rice grains. Hence we can conclude that the model is performing well, to a good extent.
