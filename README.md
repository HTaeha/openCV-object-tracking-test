<h1>Related ideas with Object Tracking</h1>

1. Dense Optical flow
2. Sparse optical flow
3. Kalman Filtering
4. Meanshift and Camshift
5. Single object trackers
6. Multiple object track finding algorithms

<h2>Tracking vs Detection</h2>

1. Tracking is faster than detection
2. Tracking can help when detection fails
3. Tracking preserves identity

OpenCV 3.4.1

<h2>Test OpenCV’s 8 different trackers.</h2>

1. BOOSTING

Boosting Tracker
Pros : None. This algorithm is a decade old and works ok, but I could not find a good reason to use it especially when other advanced trackers (MIL, KCF) based on similar principles are available.
Cons : Tracking performance is mediocre. It does not reliably know when tracking has failed.

2. MIL

MIL Tracker
Pros : The performance is pretty good. It does not drift as much as the BOOSTING tracker and it does a reasonable job under partial occlusion. If you are using OpenCV 3.0, this might be the best tracker available to you. But if you are using a higher version, consider KCF.
Cons : Tracking failure is not reported reliably. Does not recover from full occlusion.

3. KCF

KCF Tracker
Pros: Accuracy and speed are both better than MIL and it reports tracking failure better than BOOSTING and MIL. If you are using OpenCV 3.1 and above, I recommend using this for most applications.
Cons : Does not recover from full occlusion. Not implemented in OpenCV 3.0.
Bug Alert : There is a bug in OpenCV 3.1 ( Python only ) because of which incorrect bounding boxes are returned. See bug report . Thanks Andrei Cheremskoy for pointing this out.

4. TLD

TLD Tracker
Pros : Works the best under occlusion over multiple frames. Also, tracks best over scale changes.
Cons : Lots of false positives making it almost unusable.

5. MEDIANFLOW

MedianFlow Tracker
Pros : Excellent tracking failure reporting. Works very well when the motion is predictable and there is no occlusion.
Cons : Fails under large motion.

6. GOTURN

Notice : GOTURN being a CNN based tracker, uses a caffe model for tracking. The Caffe model and the proto text file must be present in the directory in which the code is present. These files can also be downloaded from the opencv_extra repository, concatenated and extracted before use.
Update: GOTURN object tracking algorithm has been ported to OpenCV. We have a separate blog post on it’s implementation here.

7. MOSSE

MOSSE Tracker

8. CSRT

CSRT Tracker

Reference : https://www.learnopencv.com/object-tracking-using-opencv-cpp-python/
