# Overview
A demo path tracer written in c++ with OpenGL graphics API. 
Path tracing is done on a compute shader using a hybrid BVH(top and bottom) for acceleration.
Currently the BVH construction done on the CPU but GPU based construction is in the bucket list for the future. 
The estimator can sample emissive lights using NEE(Next Even Estimation) and the analytical lights used in the rastered scenes alike.

Here are quick demo scenes. Scenes don't belong to me. 
[![Demo video](https://github.com/user-attachments/assets/0f1154a5-f9fc-41b5-ba77-01502016a833)](https://www.youtube.com/watch?v=0LtYzlawqec&t=38s)
![image](https://github.com/user-attachments/assets/992e35fa-7928-49dc-8cca-1e820cd92fca)
![image](https://github.com/user-attachments/assets/bd9f15d4-54cd-46c2-80bc-5cca696cff8b)
![image](https://github.com/user-attachments/assets/5ae284cb-3443-42b4-841d-3d111443e79f)
