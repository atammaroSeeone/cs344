############################################################################
# <summary> CMakeLists.txt for OpenCV and CUDA. </summary>
# <date>    2012-02-07          </date>
# <author>  Quan Tran Minh. edit by Johannes Kast, Michael Sarahan </author>
# <email>   quantm@unist.ac.kr  kast.jo@googlemail.com msarahan@gmail.com</email>
############################################################################

cmake_minimum_required(VERSION 2.8)
project( problemSet1 )

# find cuda
FIND_PACKAGE(CUDA)

# find opencv 
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )

# collect source files
file( GLOB  hdr *.hpp *.h )
file( GLOB  cu  *.cu)
SET (HW1_files main.cpp reference_calc.cpp compare.cpp HW1.cpp)

CUDA_ADD_EXECUTABLE(HW1 ${HW1_files} ${hdr} ${cu})

target_link_libraries( HW1 ${OpenCV_LIBS} )