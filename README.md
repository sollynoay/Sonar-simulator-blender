# Sonar-simulator-blender ver 0.3
Sonar simulator based on blender ver 0.3. 
# Blender version
Currently support Blender 2.79 and 2.80.  
Blender 2.79 has a rectangular-shaped spot light in Blender renderer which is similar to sonar wave emission; however, the accuracy and precision of Blender renderer cannot be guaranteed. For other rendered, using Blenderer 2.80 would be much better, which has more functions. 
# Dependencies
Opencv and OpenEXR.  
For Opencv in Windows, don't forget to copy dll file to your workspace. To link Opencv to blender, try  
```
import sys  
sys.path.append(path to the correct Python version in Opencv)  
```
Although, the program is cross platform, the uploaded OpenEXR only supports windows.  
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
# Tasks
- [x] Raw image generation  
- [x] Fan-shaped image generation
- [x] Underwater scene rendering
- [x] Rectangular-shaped spot light
- [x] Better intensity integration
- [ ] Combination of sonar simulation and underwater scene rendering
- [ ] Noise and distortion simulation  
- [ ] Anti-aliasing  

# Tips
1. The Python script to generate acoustic images is written in "Sonar image simulator" in Text editor in Blender 2.80.  
2. Modifying the configuration of camera and objects can generate different images. With Blender's powerful GUI, a lot of scenes can be simulated easily.  
3. You can also try adding objects with different materials by defining different material characteristics.
# Related papers
1. Kwak et al., Development of acoustic camera-imaging simulator based on novel model, 2015  
2. Mai et al., Acoustic Image Simulator Based on Active Sonar Model in Underwater Environment, 2018  
3. Cerqueira et al.,  A novel GPU-based sonar simulator for real-time applications, 2017       
4. Wook et al., Physically based Sonar Simulation and Image Generation for Side-scan Sonar, 2017
# Citation
If you are using our simulator, please cite one of our papers.
1. Yusheng Wang, Yonghoon Ji, Dingyu Liu, Yusuke Tamura, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "ACMarker: Acoustic Camera-based Fiducial Marker System in Underwater Environment", IEEE Robotics and Automation Letters, Vol. 5, No. 4, pp. 5018-5025, October 2020.
2. Dingyu Liu, Yusheng Wang, Yonghoon Ji, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "CycleGAN-based Realistic Image Dataset Generation for Forward-looking Sonar", Advanced Robotics, Vol. 35, No. 3-4, pp. 242-254, February 2021.
3. Yusheng Wang, Yonghoon Ji, Hanwool Woo, Yusuke Tamura, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "Acoustic Camera-based Pose Graph SLAM for Dense 3D Mapping in Underwater Environments", IEEE Journal of Oceanic Engineering, Vol. 46, 2021.
4. Dingyu Liu, Yusheng Wang, Yonghoon Ji, Hiroshi Tsuchiya, Atsushi Yamashita and Hajime Asama: "Development of Image Simulator for Forward-looking Sonar Using 3D Rendering", Proceedings of the 16th International Conference on Quality Control by Artificial Vision (QCAV2021), Tokushima (Japan), May 2021.
