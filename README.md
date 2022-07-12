# SAMV71_TensorFlow-Lite-Micro-Hello-World
TensorFlow Lite Micro Hello_World example running on SAMV71 32-bit ARM Cortex-M7 processor

### Set up SAMV71 Atmel Start project C++ Project
1. Create Atmel Start C project
2. Follow this example to convert the project to C++: https://microchipsupport.force.com/s/article/C---Support-for-Atmel-START-C#:~:text=a.,create%20a%20C%2B%2B%20based%20project.
3. Copy the directories over to the ARM/GNU C++ Compiler directories as well
4. Add **\#include <atmel_start.h>** and **atmel_start_init();** to main.cpp

### Generate project code
1. Run the following:
    - > git clone https://github.com/tensorflow/tflite-micro.git
    - > cd tflite-micro
    - > make -f tensorflow/lite/micro/tools/make/Makefile generate_hello_world_make_project
4. Navigate to *tflite-micro\tensorflow\lite\micro\tools\make\gen\linux_x86_64_default\prj\hello_world\make*
5. Copy the **tensorflow** and **third_party** folders and paste them into your Atmel Start C++ project files

### Run the Hello_World example
1. Include the **tensorflow** and **third_party** folders in your project
2. In ARM/GNU C++ Compiler > Directories, add the **tensorflow**, **third_party/flatbuffers/include**, **third_party/gemmlowp**, and **third_party/ruy** folders
3. In ARM/GNU Linker > General set the Additional Specs dropdown to **Use syscall stubs (--specs=nosys.specs)**
4. Comment out the contents of tensorflow/lite/micro/examples/hello_world/main.cc to avoid having duplicate mains
5. Add code from main_functions.cc to main.cpp as I did to setup and run inference
6. Set a breakpoint at inference_count increment and watch x, y, and the real answer sin(x) to see how y and sin(x) should match up at each increment

![](https://github.com/andrewbmccullough/SAMV71_TensorFlow_Lite_Micro_Hello_World/blob/main/Documentation/Output.png)
