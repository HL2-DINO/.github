<p align="center">
  <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/main_banner.png" width="95%"/>
</p>

<body>
   <h3 align="center">HoloLens 2 &amp; <ins>D</ins>etection for <ins>I</ins>nfrared <ins>N</ins>avigation with <ins>O</ins>ST AR headsets</strong></p>
</body>

# Introduction
Welcome to the HL2-DINO landing page. In some of our research at the [Mechatronics in Medicine](https://www.imperial.ac.uk/mechatronics-in-medicine/) laboratory at Imperial College London, we've been exploring using AR headsets such as the Microsoft HoloLens 2 for tracking surgical instruments equipped with infrared reflective markers, which are commonly used in computer/robot-assisted surgery.

<p align="center">
  <img width="20%" src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/tool_example.png"/>
  <p align="center"><em>This project aims to enable the HL2 to track surgical tools with retroreflective markers</em></p>
</p> 

The HoloLens 2 contains a front facing time-of-flight depth-camera used for hand-tracking and spatial mapping. By using the Research Mode API, it is possible to access the underlying infrared response and depth map streams for this sensor. As part of our research, we have written software to use a combination of the Research Mode API and other libraries to enable the HoloLens 2 to detect of rigid tools equipped with flat retroreflective markers. 

This is a set of multiple repositories which shares the image-processing system used in our publication: [Semi-Automatic Infrared Calibration for Augmented Reality Systems in Surgery](https://ieeexplore.ieee.org/document/9982215) by Hisham Iqbal & Ferdinando Rodriguez y Baena.

# Modules
## (1) [DINO-DLL](https://github.com/HL2-DINO/DINO-DLL)

<p align="center">
  <a href="https://github.com/HL2-DINO/DINO-DLL">
    <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/dll_banner.png" width="60%"/>
  </a>
</p>
<hr>

`DINO-DLL` is a C++/WinRT project which interacts with Microsoft's [Research Mode API](https://arxiv.org/abs/2008.11239) and runs image-processing operations (enabled by OpenCV 4.5.3 and Eigen) on the raw sensor images to detect and estimate pose (position and orientation) for tools fitted with retro-reflective markers. The pose-estimation is done relative to the world-frame of the headset, and relies on the outputs of the self-locating algorithms which run by default on the HoloLens 2. 

The project is set up to produce a `.dll` and `.winmd` which can be consumed in a Unity environment. When originally setting up the structure of the project, I found this GitHub project  [HoloLens2-ResearchMode-Unity](https://github.com/petergu684/HoloLens2-ResearchMode-Unity) by [petergu684](https://github.com/petergu684) to be an excellent reference for how to interact with the Research Mode API.  

<p align="center">  
    <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/dll_gif.gif" width="90%"/>
   <br>
   <em>Image processing carried out onboard the HoloLens 2 via DINO-DLL</em>
</p>

## (2) [DINO-Unity](https://github.com/HL2-DINO/DINO-Unity)
<p align="center">
  <a href="https://github.com/HL2-DINO/DINO-Unity">
    <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/unity_proj_banner.png" width="60%"/>
  </a>
</p>
<hr>

`DINO-Unity` is a sample Unity project, demonstrating how you can consume the information exposed by `DINO-DLL` in the context of a C\# Unity project. If you 3D print and assemble the tools provided in `DINO-IR-Tools`, and then run the project on your HoloLens, you can get a hands-on experience of tool tracking. The repo provides further instructions for how you can track custom geometries and your own tools.

<p align="center">  
    <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/toolWiggle.gif" width="40%"/>
    <br>
    <em>DINO-Unity user app experience recorded by Mixed Reality Capture</em>
</p>

## (3) [DINO-IR-Tools](https://github.com/HL2-DINO/DINO-IR-Tools)
<p align="center">
  <a href="https://github.com/HL2-DINO/DINO-IR-Tools">
    <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/tools_banner.png" width="60%"/>
  </a>
</p>
<hr>

`DINO-IR-Tools` is a repo with 3D models and instructions for printing two example tools which are used in the Unity demos in `DINO-Unity`. It also provides some files which are intended to enable you to make your own 3D printed tools fitted with reflective markers for research and experimental setups.

<html>
<div align="center">
  <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/ir-tool-example.png" width="40%" height="auto">
  <img src="https://raw.githubusercontent.com/HL2-DINO/.github/main/profile/img/tool_assem_animation.gif" width="40%" height="auto">
</div>
<p align="center">
  <em>Left: An exploded view of a tool with flat IR-reflective markers. Right: A tool being assembled</em>
</p>
</html>

# Acknowledgements

This work was originally developed during my PhD in the Mechatronics in Medicine Lab at Imperial College London. The original software was developed during a number of studies which were supported by INNOVATE UK (ref: 103950) and the EPSRC (ref: EP/R511547/1). Several people were instrumental in helping with different aspects of setting up the project and in the efforts to open-source the project. More detail on individual contributions is provided within each repo.

Thanks go out to: 

*Prof Ferdinando Rodriguez y Baena, Arjun Muhunthan, Andreas Keller, Dr Stefano Galvan, Joseph Ball, Dr Fabio Tatti*
