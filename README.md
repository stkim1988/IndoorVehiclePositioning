# External Vehicle Positioning System using Multiple Fish-eye Surveillance Cameras for Indoor Parking Lots  
Submitted for publication in IEEE Systems Journal <br/>

---
### Abstract
The autonomous positioning of a vehicle predominantly relies on the global positioning system (GPS). However, in indoor environments such as tunnels and indoor parking lots, the accuracy of GPS-based positioning can be significantly reduced due to weak GPS signals. To this end, we develop an accurate indoor vehicle positioning system using multiple fish-eye surveillance cameras. Our system first extracts vehicle segments from the top-view image of each fish-eye camera. These segments are then integrated into a common undistorted coordinate system. The center of the vehicle is finally determined using our simple but effective box fitting method. Moreover, a 1/18 scale indoor parking lot is designed to evaluate the performance of the proposed system. Throughout our experiments, we obtained average positioning errors of 30 cm or 24 cm in the regions covered by a single camera or multiple cameras, respectively<br/>

---
### Video results 
Note that the color results (perspective/orthographic bird's eye view) in the videos below are for visualization purposes to aid understanding, and only a binary segmentation map from capured fish-eye image is used overall stages of the proposed system. <br />

#### 1. 1:18 testbed enviroment
We built a testbed that has a 1/18 scale of an indoor parking lot, and used diecast toy cars that have the same 1/18 scale as the environment. There are 4x4 pillars at 42cm(7.56m in real scale) intervals along the horizontal and vertical directions.<br /> 

In this experiment, our trained SegNet[1] is used to obtain vehicles region as inputs of the proposed system, and the pillars in testbed were represented by the rantangles in result videos to help understanding the loaclization results. The demo videos consisted of multiple windows as shown in figures below.<br />

 - For single camera<br/>
 <img width="360" height="180" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/singleviewtable.png" ><br />
 
  - For two cameras<br/>
 | cam1 result | integrated result |<br /> 
 | cam2 result |&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; |<br />
 
 Below are demo videos of our indoor vehicle localization results in 1:18 scaled testbed.<br /> 
<iframe width="612" height="360" src="https://www.youtube.com/embed/VqgMvtV6of4" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="612" height="360" src="https://www.youtube.com/embed/gZvD63LF_uQ" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="590" height="400"  src="https://www.youtube.com/embed/F_sz76jqGwg" frameborder="0" allowfullscreen></iframe><br/>

#### 2. Real enviroment
To test the performance of the proposed system in real environments, we installed the same surveillance cameras to the ceiling of an indoor parking lot. The height of the ceiling is about 2.3 m and the distance between the two cameras is 8.8 m. We drew a horizontal line of length 19 m on the floor and marked 20 positions at intervals of 1 m. We located vehicles at these positions and captured images. The estimated center positions of the vehicles obtained by the proposed system were compared with these predefined positions.<br />

In this experiment, we used the GT segmentation results of vehicles as inputs of the proposed system, and the predetermined GT positions in parking lot were represented by blue cross in result videos to help understanding the loaclization results. The demo videos consisted of multiple windows as shown in figures below.<br />

 - For single camera<br/>
 <img width="360" height="180" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/singleviewtable.png" ><br/>
 - For two cameras<br/>
 <img width="450" height="180" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/multiviewtable.png"><br/>
 
Below are demo videos of our indoor vehicle localization results in real parking lots. <br />

<iframe width="780" height="360" src="https://www.youtube.com/embed/TVy8VizQbG0" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="780" height="360" src="https://www.youtube.com/embed/8LBCfdlbXOU" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="980" height="360"  src="https://www.youtube.com/embed/cxhGteBag0M" frameborder="0" allowfullscreen></iframe><br/> 


#### 3. Technical details of segmentation 
We constructed our own dataset to achieve reliable segmentation performance for our vehicle positioning system enviroment. To figure out the number of enough training semple, we trained SegNet [26] multiple times with different numbers of training samples ranging from 150 to 1428. For this experiment, SegNet was trained for 5,000 epochs using each training dataset. We evaluated the segmentation performance on 878 test images in terms of the popular F1-score. The results shown in Fig. 1 indicate that the accuracy gradually improves as the number of training samples increases, but the accuracy tends to saturate after 1000+ training samples. In conclusion, we can get stable segmentation results through more than 1000 training samples.

<img width="360" height="200" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/SegNet_training.png" ><br/>
Figure 1: The F1-scores of the SegNet trained by using different numbers of traning samples. The accuracy tends to saturate after 1000+ training samples.<br />



<!--
---
### Additional results 
Our system starts by segmenting vehicles from fisheye images. Depending on the application and enviroments, other existing segmentation techniques can be also applied. Thus, we are now testing an existing background subtracktion method in [2] to obtain segmenation of moving vehicle as inputs of the proposed system. In addition, our system performed vehicle positioning calculations in every frame independently. Temporal integration needs to be performed for temporally coherent vehicle positioning. Therefore, we are now investigating a method to obtain more stable result for frame errors by applying a Kalman filter[3] to the center coordinates obtained in a continuous frame, and the result video is as follows.<br />   
<img width="360" height="90" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/filter_.png" ><br/>
<iframe width="724" height="192" src="https://www.youtube.com/embed/bmRLaFnCN38" frameborder="0" allowfullscreen></iframe><br />
<br />
-->

---
### References
[1] V. Badrinarayanan, A. Kendall and R. Cipolla, “SegNet: A deep convolutional encoder-decoder architecture for image segmentation,” IEEE Trans. Pattern Anal. Mach. Intell., vol. 39, no. 12, pp. 2481-2495, Dec. 2017.  
<!--
[2] A. Sobral and A. Vacavant, “A comprehensive review of background subtraction algorithms evaluated with synthetic and real videos,” Comput. Vis. Image Underst., vol. 122, pp. 4–21, May 2014.  
[3] Kalman, R. E., "A new approach to linear filtering and prediction problems," 1960.  
-->

---
Source code(under construction)  
