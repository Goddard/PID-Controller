## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`.

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* indent using spaces
* set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).

## Project Write-up
The values double Kp, double Ki, double Kd that are initialized in the PID classes Init() method are defined as follows; proportional coefficient, integral coefficient, differential coefficient.

**Kp** is the **proportional coefficient** which is calculated from the cross track error to get steering angles. This is only the P in the PID formula though and if used alone will make the object overshoot the intended trajectory. A lower value here moves the object in less drastic movements, but also means the object moves off the track.  A higher value here keeps the object on the track, but also makes for much more drastic steering angles, but of course used alone without the differential or integral the object moved off the track.

**Ki** is the **integral coefficient** is used to help with steady state error.  It is the sum of the cross track errors over time.

**Kd** is the **differential coefficient** is used in conjunction with the cross track error to help avoid overshooting.

The formula used : -Kp * p_error - Kd * d_error - Ki * i_error;

## Parameter Tuning
Picking the parameters to successfully make laps around the track was trial and error.  I tried high and low values around the same value used in the lessons to start.  I watched the car make laps and adjusted to get the best fit visually.  The car still jerks side to side and isn't as smooth as a human driver.  The PID formula is simple and concise.  If I had more time I would of liked to make the turning movements smoother so if a human was actually in the car they wouldn't get sick.


Default starting parameters were : P = 0.9, I = 0.004, D = 3.0

Final starting parameters were : P = 0.15, I = 0.004, D = 5.23


If given more time I would like to plot the correct trajectory and then the one taken then compare the two to figure out if I could improve them further with just the PID equation. One limiting factor is speed.  Since I don't take into account the capabilities of the car on the track it is hard to keep the car on the track at speeds over 30.  To make movements smoother I think speed would also need to be controlled.  

## Click the image below to watch the demonstration video
[![Watch the video](https://img.youtube.com/vi/zKsnU7Ixy-Q/0.jpg)](https://youtu.be/zKsnU7Ixy-Q)
