![GitHub language count](https://img.shields.io/github/languages/count/KaganBaldiran/OpenGL_Path_Tracer)
![GitHub top language](https://img.shields.io/github/languages/top/KaganBaldiran/OpenGL_Path_Tracer)
![GitHub last commit](https://img.shields.io/github/last-commit/KaganBaldiran/OpenGL_Path_Tracer)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
# Overview
A demo path tracer written in c++ with OpenGL graphics API. 
Path tracing is done on a compute shader using a hybrid BVH(top and bottom) for acceleration.
Currently the BVH construction done on the CPU but GPU based construction is in the bucket list for the future. 
The estimator can sample emissive lights using NEE(Next Even Estimation) and the analytical lights used in the rastered scenes alike.

Here are quick demo scenes. Scenes don't belong to me. 
[![Demo video](![thumbnail2](https://github.com/user-attachments/assets/64b6e5e5-7428-4d65-b055-0bf53d8894c6))](https://www.youtube.com/watch?v=0LtYzlawqec&t=38s)
![image](https://github.com/user-attachments/assets/bd9f15d4-54cd-46c2-80bc-5cca696cff8b)
![image](https://github.com/user-attachments/assets/5ae284cb-3443-42b4-841d-3d111443e79f)
