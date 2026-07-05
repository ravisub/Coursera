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