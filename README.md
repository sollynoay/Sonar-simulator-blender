# Sonar-simulator-blender
This is a 2D forward looking sonar simulator built in Blender. Inspired by Cerqueira et al., we notice that an acoustic image can be generated by a backscattered intensity image and a depth image. Although it is difficult to consider all the physical problems without modification of render engine, for most of the cases the images from Blender statisfy our task to generate dataset to test learning-based or SLAM algorithms.
# Blender version
Currently support Blender 2.79, 2.80, 2.90.  
Blender 2.79 has a rectangular-shaped spot light in Blender renderer which is similar to the shape of sonar scope, in Blender 2.80, we build a box with absoprtion material to form the shape of sonar scope. The depth accuracy in Eevee does not satisfy our task, it is necessary to use physical rendered such as Cycles. Please use the experimental one in Blender 2.80. Note that the depth here is not the z value of the virtual optical camera, but the distance between the 3D point and the camera center.  
For Blender 2.90, we use Cylcles rendering engine, experimental version. The feature changed in Blender 2.90. The default depth map rendered is the z value map. It is necessary to change it to the distance between the 3D point and the camera center. We add modification code for the transformation. 
# Dependencies
We use python script in Blender to generate acoustic images. It is necessary to install packages in the Python in Blender.  
Basic packages: Opencv and OpenEXR.   
For Opencv in Windows, don't forget to copy dll file to your workspace. To link Opencv to blender, try  
```
import sys  
sys.path.append(path to the correct Python version in Opencv)  
```
For windows users, we also upload the pre-built OpenEXR.  
Installation for Windows can follow:  
https://www.kunihikokaneko.com/dblab/cg/bpypip.html  
```
"C:\Program Files\Blender Foundation\Blender\2.80\python\bin\python.exe" -m ensurepip
"C:\Program Files\Blender Foundation\Blender\2.80\python\bin\python.exe" -m pip install --upgrade pip 
```
Pre-built Windows packages:  
https://www.lfd.uci.edu/~gohlke/pythonlibs/#wxpython  
You can install everything you need in Blender.  
```
"C:\Program Files\Blender Foundation\Blender\2.80\python\bin\python.exe" -m pip install xxx.whl
```
# Save path
The rendered intensity image, depth and normal maps are first saved under  
"C:\\Users\\Yusheng Wang\\AppData\\Roaming\\Blender Foundation\\Blender\\2.91\\config\\BlenderPython\\"  in .exr as buffer.
Then, they are read to generate acoustic images. Please check the name of the .exr files in system console in Blender.  
Please change the save path of the acoustic images as well.

# Tips
1. The Python script to generate acoustic images is written in "Sonar image simulator" in Text editor in Blender 2.80.  
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
