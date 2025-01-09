# Edge_detection_part2
This project implements the Watershed algorithm in OpenCV which is used for image segmentation, particularly useful for separating touching or overlapping objects in images

First, essential libraries like cv2 for OpenCV functions, matplotlib.pyplot for image display, and numpy for numerical operations are imported. The display function is defined to visualize images using Matplotlib.

The process begins by reading the image pennies.jpg using OpenCV's imread function and displaying it. The image is then processed to make it suitable for segmentation using the following steps:

Median Blur: The image is smoothed using a median blur to reduce noise.

Grayscale Conversion: The blurred image is converted to grayscale for further processing.

Binary Threshold: A binary inverse threshold is applied to the grayscale image, converting it to a binary image where the coins become white, and the background becomes black.

Find Contours: Contours are detected in the binary image using cv2.findContours.

Initially, the contours found are for the entire set of coins as a single object, which is not desirable. To improve contour detection, the Watershed algorithm is applied.

The Watershed algorithm involves the following steps:

Read Image: The original image is read again.

Apply Blur: A median blur is applied to the image.

Convert to Grayscale: The blurred image is converted to grayscale.

Apply Threshold: A binary inverse threshold with Otsu's method is applied to the grayscale image, which automatically determines the optimal threshold value.

Noise Removal (Optional): Morphological operations are applied to remove noise from the binary image. cv2.MORPH_OPEN is used to remove background noise.

Dilate Background: The background is dilated to ensure that the sure background is obtained.

Distance Transform: The distance transform is applied to the binary image to calculate the distance of each foreground pixel from the nearest background pixel.

Generate Sure Foreground: A threshold is applied to the distance transform to obtain the sure foreground.

Generate Unknown Region: The unknown region is calculated by subtracting the sure foreground from the sure background.

Generate Markers: Connected components are labeled in the sure foreground, and markers are created for the Watershed algorithm. The background is labeled as 1, and the unknown region is labeled as 0.

Apply Watershed Algorithm: The Watershed algorithm is applied using cv2.watershed, which modifies the markers image to segment the objects.

Finally, contours are found again in the segmented image, and contours corresponding to the coins are drawn.

<img width="409" alt="image" src="https://github.com/user-attachments/assets/64f67f12-f1f3-4741-85ca-3bec7ae188df" />
<img width="398" alt="image" src="https://github.com/user-attachments/assets/4c024cfb-10e4-4165-8120-b895a77c2310" />
<img width="398" alt="image" src="https://github.com/user-attachments/assets/ddfa65b4-5039-4f10-a36a-7a65c6f73695" />
<img width="398" alt="image" src="https://github.com/user-attachments/assets/a38fcc50-11b9-4f7f-b8f7-7f401863a3b4" />


