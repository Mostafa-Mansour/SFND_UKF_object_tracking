# Unscented Kalman Filter for object tracking using Radar and Lidar measurements


<img src="media/ukf_highway_tracked.gif" width="700" height="400" />

## Addressed rubric points:
* 1- A README with instructions is included with the project
* 2- The README indicates which project is chosen.
* 3- The README includes information about each rubric point addressed.
* 4- The submission must compile and run.
* 5- The project demonstrates an understanding of C++ functions and control structures. (check ukf.cpp, you wil find a lot of functions and control structures).
* 6- The project reads data from a file and process the data, or the program writes data to a file. (In tools.cpp, line 129, there is a function that use PCL api library to read the point cloud from a file).  
* 7- The project accepts user input and processes the input. (in main.cpp file, the velcoity is asked at line 14 and used at line 41 ).
* 8- The project uses Object Oriented Programming techniques (check ukf.h and ukf.cpp files).
* 9- Classes use appropriate access specifiers for class members (in file ukf.h, line 8 and line 57).
* 10 - Class constructors utilize member initialization lists (in ukf.cpp, line 10).
* 11- Classes encapsulate behavior (in ukf.cpp, line 86, processMeasurement function encapsulates two update functions, one for radar measurements and one for lidar measurements).
* 12- The project makes use of references in function declarations (in ukf.h lines 36, 42, and 45).

In this project I implemented an Unscented Kalman Filter to estimate the state of multiple cars on a highway using noisy lidar and radar measurements. 

The main program can be built and ran by doing the following from the project top directory.

1. mkdir build
2. cd build
3. cmake ..
4. make
5. ./ukf_highway


<img src="media/ukf_highway.png" width="700" height="400" />

`main.cpp` is using `highway.h` to create a straight 3 lane highway environment with 3 traffic cars and the main ego car at the center. 
The viewer scene is centered around the ego car and the coordinate system is relative to the ego car as well. The ego car is green while the 
other traffic cars are blue. The traffic cars will be accelerating and altering their steering to change lanes. Each of the traffic car's has
it's own UKF object generated for it, and will update each indidual one during every time step. 

The red spheres above cars represent the (x,y) lidar detection and the purple lines show the radar measurements with the velocity magnitude along the detected angle. The Z axis is not taken into account for tracking, so I am only tracking along the X/Y axis.

---

## Other Important Dependencies
* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
 * PCL 1.2

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./ukf_highway`
