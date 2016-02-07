# ufpa-face-detection

Face detection for Octave / Matlab based on Viola &amp; Jones' algorithm [1].

This code runs both on Octave and Matlab. Note that Mathworks has its own implementation [2]. OpenCV also provides an implementation [3].

Convention: all files (scripts and functions) start with the prefix ufd_ (UFPA face detection). 

The face detector has a training and a test stages. The main scripts for training and testing are: ufd_train and ufd_test, respectively.

Development strategy:

- We will use the training stage of OpenCV and import the classifier in [4] (more than 30k lines). For that, we need code to import the XML file into Octave / Matlab. Note that Mathworks has support to OpenCV [5] but we will not use it for the sake of compatibility with Octave. This strategy will force us to use the same data structures as OpenCV but will allow to debug our code using OpenCV as a reference.
- We first concentrate on the test stage, with the following guidelines: 1) use a webcam video capture software to obtain a screenshot as an image file, 2) read the image from Octave / Matlab, convert it to gray scale and show it, 3) calculate the Integral Image, 4) for all required resolutions, calculate the needed parameters and invoke the classifier, 5) draw the rectangles according to the classifier's decisions.

<b>References:</b>

[1] Robust Real-Time Face Detection, Paul Viola and Michael Jones, International Journal of Computer Vision 57(2), 137–154, 2004.

[2] http://www.mathworks.com/help/vision/ref/vision.cascadeobjectdetector-class.html

[3] http://docs.opencv.org/master/d7/d8b/tutorial_py_face_detection.html

[4] https://github.com/Itseez/opencv/blob/master/data/haarcascades/haarcascade_frontalface_default.xml

[5] http://www.mathworks.com/help/vision/ug/opencv-interface.html

[6] http://www.lienhart.de/Prof._Dr._Rainer_Lienhart/Source_Code_files/ICIP2002.pdf (this provides more details about how the Haar features can be calculated)

[7] At http://www.lienhart.de/Prof._Dr._Rainer_Lienhart/Source_Code.html one can find, e.g., Rainer Lienhart, Alexander Kuranov, and Vadim Pisarevsky. Empirical Analysis of Detection Cascades of Boosted Classifiers for Rapid Object Detection. MRL Technical Report, Intel Labs, May 2002, revised Dec. 2002

[8] http://www.mathworks.com/matlabcentral/fileexchange/29437-viola-jones-object-detection (this set of Matlab scripts is a very good starting point to this project: it parses an XML (it seems the format is the old one), implements the classifier and outputs the results)

[9] There are other related codes at "Fileexchange": http://www.mathworks.com/matlabcentral/fileexchange/?search_submit=fileexchange&query=Viola+Jones+Object+Detection&term=Viola+Jones+Object+Detection

<b>References about face detector using OpenCV:</b>

- How to build OpenCV on Windows: http://www.anlak.com/2013/02/build-debug-opencv-vs2010.html

<b>References about training and testing a face detector using OpenCV, but not modifying its code (just invoking command line tools):</b>

- http://note.sonots.com/SciSoftware/haartraining/document.html

- http://www.cs.princeton.edu/courses/archive/fall08/cos429/CourseMaterials/Precept1/facedetect.pdf
