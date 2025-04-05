# Image_Processing
Build an Image algorithm to identify the face of people

Clc; close all; clear; 
% Load the image 
Img = imread(“catherine.jpg”); 
% Convert the image to grayscale for better detection (optional but recommended) 
grayImg = rgb2gray(img); 
% Create a cascade detector object with a specific model 
faceDetector = vision.CascadeObjectDetector(); % Default detects frontal faces 
% Adjust the ‘MinSize’ and ‘MergeThreshold’ parameters for better accuracy 
faceDetector.MinSize = [50, 50]; % Minimum size of faces to detect (adjust as needed) 
faceDetector.MergeThreshold = 5; % Higher value reduces false positives 
% Detect faces 
Bbox = step(faceDetector, grayImg); 
% Check if any faces are detected 
If isempty(bbox) 
Disp(‘No faces detected.’); 
Else 
% Annotate detected faces in the image with thicker boxes 
Thickness = 5; % Specify the thickness of the box 
detectedImg = insertShape(img, ‘Rectangle’, bbox, ‘Color’, ‘green’, ‘LineWidth’, thickness); 
% Display the result 
Figure; 
Imshow(detectedImg); 
Title(‘Detected Faces’); 
End
Result:
![WhatsApp Image 2025-04-05 at 11 35 28_7c1b8677](https://github.com/user-attachments/assets/2fa87862-4ffe-4584-b1d6-5cb90cb241b3)
