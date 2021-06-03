# 创建Vs工程进行编译  设定 OPENCVMODULESPATH的参数

取消勾选 pytohn  和 java 的包 因为不需要  
arm-himix200-linux-g++ -o draw_image draw_image.cpp -I ./include/ ./lib/libopencv_core.so ./lib/libopencv_imgcodecs.so ./lib/libopencv_imgproc.so

 # 编译OPencv踩过的坑 
 在Windows的编译过程中国尤其需要注意
