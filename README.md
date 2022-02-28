#       METHODOLOGY

### Female Humanoid Robot MAYA 1.0 Design

![img1](https://github.com/MAYA-1-0/MAYA1.0_Architecture/blob/main/images/Screenshot%20from%202022-02-28%2020-22-19.png)

The design of the humanoid depended on the following points
* The female humanoid named “MAYA” is 1.55m in height.
* The measurements for the body parts have been taken from the same previously mentioned anthropometric * reference.
* The entire design is covered externally by body panels, which provide support and give a good aesthetic appearance.
* The motor incorporated in the design is Dynamixel XM-430.
* The measurement values for different parts are mentioned here


Based on the identified role and working environment which implies that robots offer service to humans, which consists of frequent human-robot interactions, the  selected gender is the female which symbolizes a friendly and passionate personality. A female humanoid is often preferred in social and service robots as they are perceived as less threatening or more friendly than their male counterparts. The appearance of a humanoid robot consists of frame structures that function as skeletons and housings For frame components that support the weight of humanoid robot and generate movement, a very precise engineering approach is required and this step of the design process, the frame requirements, Kinematics and generate the conceptual designs based on the generated requirements.


### Part Specification of MAYA 1.0 
The below tables depicts detailed specifications of all the parts of the robot MAYA 1.0

### Head

**Neck: 71.40mm	Face: 182**

##### Calculated values for head


![img2](https://github.com/MAYA-1-0/MAYA1.0_Architecture/blob/main/images/Screenshot%20from%202022-02-28%2020-37-41.png)


### Torso 

**Torso: 404.6mm	Hand: 646.8mm**


##### Calculated values for Torso
![img3](https://github.com/MAYA-1-0/MAYA1.0_Architecture/blob/main/images/Screenshot%20from%202022-02-28%2020-37-31.png)


### Base

**Base: 742mm**


##### Calculated values for Base
![img4](https://github.com/MAYA-1-0/MAYA1.0_Architecture/blob/main/images/Screenshot%20from%202022-02-28%2020-37-08.png)


### Degrees of Freedom

![img](https://github.com/MAYA-1-0/MAYA1.0_Architecture/blob/main/images/Screenshot%20from%202022-02-28%2020-36-39.png)


## Assembly of MAYA 1.0

#### Navigation
The key to visual SLAM is motion estimation. The early stage of research involved a frame to frame matching method for estimating the motion of the camera and various other methods based on feature matching were developed. There are two types of feature-based methods in the literature: filter-based methods and BA-based methods. The first monocular visual SLAM was developed in 2003. It was named MonoSLAM. MonoSLAM is considered a representative method in filter-based vSLAM algorithms. In MonoSLAM, camera motion and 3D structure of an unknown environment are estimated simultaneously using an extended Kalman filter (EKF). The problem of this method is a computational cost that increases in proportion to the size of an environment. In large environments, the size of a state vector becomes large due to the large number of feature points. In this case, it is difficult to achieve real-time computation. Recently, structured light-based RGB-D cameras such as Microsoft Kinect have become cheap and small
Since such cameras provide 3D information in real-time, these cameras are also used in vSLAM algorithms. The appearance‑based SLAM uses the appearance information of the environment. It does not use the tracks of the robots or the landmarks in metric coordinates. The map is constructed based on the topological sense of the visited places. The spatial appearance SLAM uses the range data, rather than visual images, to detect the place and the loop closure. The combination of the visual and spatial information can improve robustness in recognizing the places and improve the distinctiveness of places using the place fingerprints, which contain color patches, vertical edges, and the extremity of line segments, to detect the loop closure. Topological maps are attractive due to the reduced storage requirements. They are more scalable to deal with larger environments. In addition, they have good integration with motion planning algorithms and are also more intuitive for persons to give navigation indications,



Visual SLAM framework mainly comprises of the following module:
* Initialization
* Tracking
* Mapping
In the initialization module, the global coordinate system is to be defined first, and then a part of the environment is reconstructed as an initial map in the global coordinate system. To continuously estimate camera poses the initialization is followed by tracking and mapping. In tracking, the camera pose of the image with respect to the map is tracked from the reconstructed map. In order to do this, 2D–3D correspondences between the image and the map are first obtained from feature matching or feature tracking in the image. The camera pose is then computed from correspondences by solving the Perspective-n-Point (PnP) problem. It should be noted that most vSLAM algorithms assume that intrinsic camera parameters are calibrated beforehand so that they are known. Therefore, camera pose is equivalent to extrinsic camera parameters with translation and rotation of the camera in the global coordinate system. In the mapping, the map is expanded by computing the 3D structure of an environment when the camera observes unknown regions where the mapping has not been performed before.


### Electrical Harnessing:

The below figure describes the electrical harnessing of Maya. Here 2 batteries are connected parallely which give 12 volts and 50 amps output. Further this output is further divided into two 12 volt supplies and one 5 volt supply. From the first 12 volts supply Jetson nano and LCD screen are  powered and using the second 12 volt supply Jetson Xavier is powered along with the arm and head motors and LED lights , and using a 5 volts supply router is powered. The depth camera and stereo camera are connected to Jetson nano and they receive power from the same. Lidar is connected to Jetson Xavier and it also receives power from the Xavier itself. For distribution of power along all the motors a separate PCB is designed which distributes required power to all the dynamixels. All the dynamixel motors are connected with each other in a daisy chain, so there is no need to power every motor separately. Neck motors have a separate daisy chain, arm motors have another daisy chain. While the base motors are connected to Jetson Xavier and they make another daisy chain. Mic and speaker receive the required amount of power and data from Jetson Xavier, they require 5 volts of supply. As Xavier do not have more than two USB ports, a separate USB Hub is connected to it and then the slave devices are connected to Xavier through the hub, this can supply upto 5 volts to the connected devices.

![img7](https://github.com/MAYA-1-0/MAYA1.0_Architecture/blob/main/images/Screenshot%20from%202022-02-28%2021-10-47.png)
