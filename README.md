**Intructions**

The file *ReadVideoData.m* contains the MATLAB code to read the algorithm to read the skeletons from videos and automatically detect the hip, knee, ankle, heel and metatarsal points of the skeletons while cycling.

In order to run it properly, first, you need to follow these steps:

1. Include the folder *MEX_file* in your MATLAB path.
2. Include all the files of this shared folder https://www.dropbox.com/sh/dxturx00xsxsjr5/AADcssOkZW7T0WwT2esof5d2a?dl=0 to the *MEX_file* folder.
3. You should place one webcam video from one side of the subject at videos/cam 1, and from the other side at videos/cam 2.
4. Change the name of your file in line 20 of *ReadVideoData.m* file.

We tested the files in Windows 10, Matlab versions R2016a and R2019b (x64). We cannot ensure that work in other versions of MATLAB. The MEX file will not work in other OS. If you have another OS or MATLAB version, or you want to simply modify the MEX file, we included the file Process_Image_MEX.cpp to compiled after compiling the OpenPose in your system, as explained in the OpenPose repository https://github.com/CMU-Perceptual-Computing-Lab/openpose.

**Use of code** 

The variable *pose* within the call:
[a b c pose(:,:,1) pose(:,:,2) pose(:,:,3)]=Process_Image_MEX(double(data));
contains the positions of all 25 keypoints of the skeleton.

The variable pose has 3 dimensions: nsubj x nkeypoints x 3
pose(:,:,1) and pose(:,:,2) contain the x and y positions of the points in the plane. pose(:,:,3) is the score of that keypoint, related to the confidence of the position of that point (see https://cmu-perceptual-computing-lab.github.io/openpose/html/structop_1_1_datum.html#a6d629b1f6f7b958fe4cf2ef4cdf57c5b).

You can check the performance of the MEX file running *TestCompilationMex_FromImage.m*. The results should be something like this:

![alt text](https://github.com/gilserrancoli/capture_2Dcycling/blob/master/MEX_file/upc_running_result.jpg?raw=true)

The order of the 25 keypoints is the following:
1. Nose
2. Neck
3. Right shoulder
4. Right elbow
5. Right wrist
6. Left shoulder
7. Left elbow
8. Left wrist
9. Mid abdomen
10. Right hip
11. Right knee
12. Right ankle
13. Left hip
14. Left knee
15. Left ankle
16. Right eye
17. Left eye
18. Right ear
19. Left ear
20. Left 1st metatarsal
21. Left 5th metatarsal
22. Left heel
23. Right 1st metatarsal
24. Right 5th metatarsal
25. Right heel
