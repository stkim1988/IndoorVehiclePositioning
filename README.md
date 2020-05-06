# External Vehicle Positioning System using Multiple Fish-eye Surveillance Cameras for Indoor Parking Lots,
Submitted for publication in IEEE Systems Journal
---
### Abstract
The autonomous positioning of a vehicle predominantly relies on the global positioning system (GPS). However, in indoor environments such as tunnels and indoor parking lots, the accuracy of GPS-based positioning can be significantly reduced due to weak GPS signals. To this end, we develop an accurate indoor vehicle positioning system using multiple fish-eye surveillance cameras. Our system first extracts vehicle segments from the top-view image of each fish-eye camera. These segments are then integrated into a common undistorted coordinate system. The center of the vehicle is finally determined using our simple but effective box fitting method. Moreover, a 1/18 scale indoor parking lot is designed to evaluate the performance of the proposed system. Throughout our experiments, we obtained average positioning errors of 30 cm or 24 cm in the regions covered by a single camera or multiple cameras, respectively<br/>

---
### Video results 
Note that the color results (perspective/orthographic bird's eye view) in the videos below are for visualization purposed to aid understanding, and only a binary segmentation map from capured fish-eye image is used overall stages of the proposed system. <br />

#### 1. 1:18 Testbed
We built a testbed that has a 1/18 scale of an indoor parking lot, and used diecast toy cars that have the same 1/18 scale as the environment. There are 4x4 pillars at 42cm( 7.56m in real scale) intervals along the horizontal and vertical directions. The pillars in testbed is represented by the rantangles in result videos to help understanding the loaclization results.<br /> 

Below are demo videos of our indoor vehicle localization results in 1:18 scaled testbed. In this experiment, our trained SegNet[1] is used to obtain vehicles region as inputs of the proposed system. The demo videos consists of multiple windows as shown in figures below.<br />

 - For single camera<br/>
 <img width="360" height="180" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/singleviewtable.png" ><br />
 
  - For two cameras<br/>
 | cam1 result | integrated result |<br /> 
 | cam2 result |&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  |<br />
<iframe width="612" height="360" src="https://www.youtube.com/embed/VqgMvtV6of4" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="612" height="360" src="https://www.youtube.com/embed/gZvD63LF_uQ" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="590" height="400"  src="https://www.youtube.com/embed/F_sz76jqGwg" frameborder="0" allowfullscreen></iframe><br/>

#### 2. Real enviroment
Below are demo videos of our indoor vehicle localization results in real parking lots.  
In this experiment, we used the GT segmentation results of vehicles as inputs of the proposed system.   
The demo videos consists of multiple windows as shown in figures below.<br />

 - For single camera<br/>
 <img width="360" height="180" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/singleviewtable.png" ><br/>
 - For two cameras<br/>
 <img width="450" height="180" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/multiviewtable.png"><br/>

<iframe width="780" height="360" src="https://www.youtube.com/embed/TVy8VizQbG0" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="780" height="360" src="https://www.youtube.com/embed/8LBCfdlbXOU" frameborder="0" allowfullscreen></iframe><br/>
<iframe width="980" height="360"  src="https://www.youtube.com/embed/cxhGteBag0M" frameborder="0" allowfullscreen></iframe><br/>

---
### Additional results 
Our system performed vehicle positioning calculations in every frame independently. Temporal integration needs to be performed for temporally coherent vehicle positioning. Therefore, we are now investigating a method to obtain more stable result for frame errors by applying a Kalman filter[2] to the center coordinates obtained in a continuous frame, and the result video is as follows.<br /> 
<img width="360" height="90" src="https://raw.githubusercontent.com/stkim1988/IndoorVehiclePositioning/master/img/filter_.png" ><br/>
<iframe width="724" height="192" src="https://www.youtube.com/embed/bmRLaFnCN38" frameborder="0" allowfullscreen></iframe><br />
<br />

<!--
    - camera 1<br/>
[![Watch the video](https://img.youtube.com/vi/TVy8VizQbG0/sddefault.jpg)](https://youtu.be/TVy8VizQbG0)<br/>
    - camera 2<br/>
[![Watch the video](https://img.youtube.com/vi/8LBCfdlbXOU/sddefault.jpg)](https://youtu.be/8LBCfdlbXOU)<br/>
- Multiple cameras<br>
    - camera 1&2<br>
[![Watch the video](https://img.youtube.com/vi/cxhGteBag0M/sddefault.jpg)](https://youtu.be/cxhGteBag0M)<br/>
-->

---
### References
[1] V. Badrinarayanan, A. Kendall and R. Cipolla, “SegNet: A deep convolutional encoder-decoder architecture for image segmentation,” IEEE Trans. Pattern Anal. Mach. Intell., vol. 39, no. 12, pp. 2481-2495, Dec. 2017.  
[2] Kalman, R. E., "A new approach to linear filtering and prediction problems," 1960.  


---
Source code(under construction)  
