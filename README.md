# Motion_Detection-Project
Performing motion detection without making use of any PRETRAINED library.

Project Workflow and its execution.

Step 1 :- Importing library cv2,np.
Step 2 :- Reading video and storing it in a variable named cap.
Step 3 :- Reading two consecutive frames in video to understand moving objects with the help of backgroud subtractor.
Step 4 :- Creating an while condition and performing detection operations till the frames can be read.
Step 4.1 :- Creating absolute diff between two frames to understand the difference in the frames. In motion detection it gives us area where there is motion or change in frames.
Step 4.2 :- Converting the diff image into grayscale format to perform easier image processing using cv2.cvtColor().
Step 4.3 :- Creating a gaussian blur on grayscale image with kernel size of (5,5). 0 indicates that opencv should automatically calculate standard deviation based on kernel size.
Step 4.4 :- Creating binary threshold on image with pixel value greater than or equal to 20 are set to max value i.e 255 in this case and the rest pixel to 0. This operations helps emphasize regions with significant changes.
Step 4.5 :- Performing Dilation to increase the foreground region of thresh image, None argument plays a crucial role in determining how the dilation operation is applied. It indicates that the default structuring element, a 3x3 kernel of ones, will be used.Using None in this specific case results in a basic dilation that simply adds pixels to the immediate neighbors of the foreground objects in all directions.
Step 4.6 :- Contours are detected in the dilated image using the cv2.findContours function. Contours represent the boundaries of connected components in the binary image. 
Step 5 :- After detecting contours in a image I had iterated through each and every frame and draw bounding box around significant contours. To filter out small contours which represents noise or any insignificant changes I had created a condition using contourArea() i.e countourArea() < 800 pixels, if yes it skips the current contour and jumps to next iterations. I am also annotating the status of frame if any motion is detected. 
Step 6 :- After reading and performing operations on frame1, I initialize frame1 with frame2 and read the next frame and store it in frame2. So after these operations frame2 will now become frame1 and next new frame read will become as frame2.
Above operations will be running till key 'q' is pressed after that loops break out.
At the end the cap is released and all windows are freed.
