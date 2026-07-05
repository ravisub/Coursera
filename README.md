This is submission for Coursera "CUDA at Scale Independent Project"
This code is based on "NPP Box Filter Laboratory" in the same course.
Instead of running the BoxFilter, this code converts 8-bit RGB images to 8-bit grayscale images.
THis has been built and tested on a Linux system.

HOW TO BUILD
1. Make sure you have FreeImage installed. https://freeimage.sourceforge.io/
2. In the directory rgb2Gray run the following commands
   make clean
   make build
   The executable is created in the same directory.

HOW TO RUN
1. Be in the same directory where ythe input RGB images are.
2. [path to rgb2Gray] --input <input image name>
   The output grayscale image is created in PNG format in the same directory.
3. If no input argument is given, it tries to run house.tiff

GENERAL
There are several tiff RGB images in rgb2Gray/input.
The output gray images from these are also present in the same location.

CHANGES FROM BASE

Common/UtilNPP/ImageIO.h:

Added
void loadImage(const std::string &rFileName, ImageCPU_8u_C3 &rImage) to load rgb images
Modified
void saveImage(const std::string &rFileName, const ImageCPU_8u_C1 &rImage) to save in PNG format
    
rgb2GrayNPP/Makefile based on boxFilterNPP/Makefile
Changed from boxFilterNPP to rgb2GrayNPP in all places
Changed default CUDA_PATH from /usr/local/cuda to /usr
Added -lnppicc_static to the set of libraries to be linked
Removed $(GENCODE_FLAGS) from compiler and linker options
Executable is created in rgb2Gray instead of ../../bin

rgb2GrayNPP/rgb2GrayNPP.cpp (based on boxFilterNPP/boxFilterNPP.cpp)

Changed default input file from Lena.pgm to house.tiff
Changed output filename tag from _boxFilter.pgm to _gray.png
Changed input image type from ImageNPP_8u_C1 to ImageNPP_8u_C3
Changed NPP function from nppiFilterBoxBorder_8u_C1R to nppiRGBToGray_8u_C3C1R
