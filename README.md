# Sonar-simulator-blender
This is a 2D forward looking sonar simulator built in Blender.  

We released a new simulator with more realistic images and more functions. Please have a look. [link](https://github.com/sollynoay/ACSim)

![inBlender](https://user-images.githubusercontent.com/11170161/178634463-a0c1452d-5e8a-4788-b5dc-feb0bcf7f209.PNG)


The default parameter setting of the 2D forward looking sonar in this simulator is consistent with [ARIS EXPLORER 3000](http://www.soundmetrics.com/). Examples of the synthetic image from the simulator and the real image from a water tank are shown as follows (aritficial objects on the ground). Here, images are shown in polar coordinate systems.  

![sim_17](https://user-images.githubusercontent.com/11170161/178511300-2eb06d3d-9918-464c-8e77-dc09ae134cc0.png)
![real_17](https://user-images.githubusercontent.com/11170161/178511121-01974f5e-2346-40fd-ad5f-5508b2c4c602.png)

We also show another example on seabed. The left image is from the simulator, and the right image is captured on a ship. Here, images are shown in Euclidean coordiante systems.  

![terr_sim](https://user-images.githubusercontent.com/11170161/183140024-bda560ef-9e47-4b46-a877-31c831acc39a.png)
![terr1](https://user-images.githubusercontent.com/11170161/183140067-16880524-bef7-4a0b-b395-1368005de4ec.PNG)


# Basic idea
Inspired by [Cerqueira et al.](https://www.sciencedirect.com/science/article/abs/pii/S0097849317301371), we notice that an acoustic image can be generated by a backscattered intensity image and a depth (range) image. Although it is difficult to consider all the physical problems without modification of the render engine, for most of the cases the images from Blender statisfy our tasks like generating dataset to test learning-based or SLAM algorithms.  

# Why this simulator
The scalability and flexibility of the [previous simulator](https://ieeexplore.ieee.org/document/7165431) from our research group is low. In order for an easy use, current simulator was built in Blender. It is easier to modify the scene. Moreover, using python script can generate the trajectory of the sensor, or publishing other information such as 3D information with no effort. 

# Blender version
Currently support Blender 2.79, 2.80, 2.90.  
Blender 2.79 has a rectangular-shaped spot light in Blender renderer which is similar to the shape of sonar scope, in Blender 2.80, we build a box with absoprtion material to form the shape of sonar scope. The depth accuracy in Eevee does not satisfy our task, it is necessary to use physical rendered such as **Cycles**. Please use the experimental one in Blender 2.80. Note that the depth here is not the z value of the virtual optical camera, but the distance between the 3D point and the camera center.  
For Blender 2.90, we use Cylcles rendering engine, experimental version. The feature changed in Blender 2.90. The default depth map rendered is the z value map for optical camera. It is necessary to change it to the distance between the 3D point and the camera center. We add modification code for the transformation. 

# Dependencies
We use python script in Blender to generate acoustic images. It is necessary to install packages in the Python in Blender.  
Basic packages: OpenCV and OpenEXR.  
There is no strict version requirements for OpenCV and OpenEXR. Just to make sure the python version of Blender meets the dependencies version. 
For example, Blender 2.93 uses python 3.9, more recent OpenCV would be preferred, like 3.4.16. 
## Installation in Windows
### OpenCV
There are several methods to install OpenCV to the python in Blender.
Here, an example is given by downloading [OpenCV](https://opencv.org/releases/) first and link to the OpenCV library in Windows.
1. Download the compiled OpenCV for Windows and extract it.
2. Putting the world.dll file to several places to avoid dll problems.
  * Where you installed Blender, default under Program Files
  * Where the userpref is saved. Under <user>/AppData/
  * Where your .blend file is
3. To link Opencv to blender, try
```
import sys  
sys.path.append(path to the correct Python version in Opencv)  
```
After the aforementioned process, try
```
import cv2  
```
in Blender.
### OpenEXR
Installing a prebuilt .whl is simpler for Windows. 
If you known Japanese, installation for Windows can refer:  
https://www.kunihikokaneko.com/dblab/cg/bpypip.html  
However, the process is actually simple.
```
"C:\Program Files\Blender Foundation\Blender\2.80\python\bin\python.exe" -m ensurepip
"C:\Program Files\Blender Foundation\Blender\2.80\python\bin\python.exe" -m pip install --upgrade pip 
```
Pre-built Windows packages:  
[link](https://www.wheelodex.org/projects/openexr/)  
You can install everything you need in Blender.  
```
"C:\Program Files\Blender Foundation\Blender\2.80\python\bin\python.exe" -m pip install xxx.whl
```
Sometimes there may be problems if command prompt is not run in admin mode. **It is recommanded to run command prompt as administrator.**
# Save path
The rendered intensity image, depth and normal maps are first saved under  
"C:\\Users\\Yusheng Wang\\AppData\\Roaming\\Blender Foundation\\Blender\\2.91\\config\\BlenderPython\\"  in .exr as buffer.  
Then, they are read to generate acoustic images. Please check the name of the .exr files in system console in Blender.   
Please change the save path of the acoustic images as well.

# Tips
1. The Python script to generate acoustic images is written in "Sonar image simulator" in Text editor in Blender.  
2. Modifying the configuration of camera and objects can generate different images. With Blender's powerful GUI, a lot of scenes can be simulated easily.  
3. You can also try adding objects with different materials by defining different material characteristics.
# Tasks
- [x] Raw image generation  
- [x] Fan-shaped image generation
- [x] Underwater scene rendering
- [x] Rectangular-shaped spot light
- [x] Better intensity integration
- [ ] Combination of sonar simulation and underwater scene rendering
- [ ] Noise and distortion simulation  
- [ ] Anti-aliasing  
# Related papers
1. Kwak et al., Development of acoustic camera-imaging simulator based on novel model, 2015  
2. Mai et al., Acoustic Image Simulator Based on Active Sonar Model in Underwater Environment, 2018  
3. Cerqueira et al.,  A novel GPU-based sonar simulator for real-time applications, 2017       
4. Wook et al., Physically based Sonar Simulation and Image Generation for Side-scan Sonar, 2017
# Citation
If you are using our simulator, please cite any of our papers.
1. Yusheng Wang, Yonghoon Ji, Dingyu Liu, Yusuke Tamura, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "ACMarker: Acoustic Camera-based Fiducial Marker System in Underwater Environment", IEEE Robotics and Automation Letters, Vol. 5, No. 4, pp. 5018-5025, October 2020.
2. Dingyu Liu, Yusheng Wang, Yonghoon Ji, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "CycleGAN-based Realistic Image Dataset Generation for Forward-looking Sonar", Advanced Robotics, Vol. 35, No. 3-4, pp. 242-254, February 2021.
3. Yusheng Wang, Yonghoon Ji, Dingyu Liu, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "Elevation Angle Estimation in 2D Acoustic Images Using Pseudo Front View", IEEE Robotics and Automation Letters, Vol. 6, No. 2, pp. 1535-1542, April 2021.
4. Dingyu Liu, Yusheng Wang, Yonghoon Ji, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "Development of Image Simulator for Forward-looking Sonar Using 3D Rendering", Proceedings of the 16th International Conference on Quality Control by Artificial Vision (QCAV2021), Tokushima (Japan), May 2021.
