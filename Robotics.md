## Robot Middleware Choices
1) ROS (Robot Operating System):
- Most widespread use
- Created by Morgan Quigly and Willow Garage
- Reduce "reinvention", increase interoperability and reproducibility
- Peer-to-peer architecture over network, inter-process communication for robots
- Software functionality modularized as ROS nodes
- Run-time system: nodes communicate over IP network
- Packaging System: nodes organized into distributable packages
- ROS is a moving target, stability issues, adaptation is often necessary
- Makes running experiments on robotics faster, share work with what everyone else is building
- Code can be ported into different robot platforms if they support same ROS distributions

2) LCM (Lightweight Communications and Marshalling)
- ROB 550 and EECS 467, probably most efficient messaging

3) Many Other Options:
- Yarp (Yet Another Robot Platform)
- JAUS (Joint Architecture for Unmanned Systems)
- MOOS
- Player/Stage

## Software (ROS)
1) A lot of problems that take time is usually compilers related rather than just implementing algorithms and tuning parameters ..
2) Lot's of packages used are built by students/researchers etc
3) ROS distributions and dependencies are well built .. most packages of ROS for industrial applications are built for customized applicaitons of the builder.. but then when you want to use their pacakges you run into lots of problems.
4) Progress and Software improvements aren't synced along the industry .. some companies move faster than others.. some ppl are using ROS2 others are still with ROS1 .. some ppl are still using python2.. kind of like the debate between ppl using python2.7 or python3.2.. a lot still needs to be done
5) For debugging parameters, use visualization tools to know what are the core factors into effecting our system! Like where's the W&B's for robotics?!
6) Open source packages in ROS are not aligned .. things will be old from ROS kinetic and others in ROS Lunar .. which also puts a constraint on python2 vs python3
7) Magic Nunmbers .. every robot has it's own magic numbers for each package/robot/env/task/sensors onboard .. maybe learning would be a greate forward force for this?!
8) A lot of times it feels like re-inventing the wheel .. a lot of packages are poorly and rarely documented cz ppl say "there's no time to work on documentation"
9) For lot's of tasks, you're often better off writing your own packages then using something off the shelf
10) A lot of docs page for robotics packages on ROS are very poor documented .. take for example the package that merges two laser scans.
11) Documentations for robotics software like ROS are not the easiest to understand and use.. compared to the ML docs pages and tutorials and examples to try out!
12) Software refactoring for different hardwares isn't as simple as you may think .. you need to tune according to robots parameters/materials etc.. doesn't seem to have a vertical integration architecture
13) ROS1 is not made for real time robotics control.. most folks use ROS2 or their own custom C++ packages
14) ROS and robotics isn't just pure software .. it relies on robot modelling and heavy mathematical equations that need to be carefully tuned in order for it to work.
15) It's quite hard to see packages in ROS that support multiple distributions of ROS .. most of the old ones support up to ROS Kinetic (ROS Melodic maybe?) .. and the gap between ROS2 and previous versions is quite big as well
16) Some low resolutions for example like the min_range for a lidar, will cause the robot to not see valuable information that you might need

## Hardware
1) Compute power is a strong factor here for the decision .. battle between capabilities limits and needs is overlapping
2) Some hardware have frequency limits that even if you passed them you won't see any progress
3) Upgrades in code efficiency depends on hardware suppliers like the SDK from stereolabs
4) Software Breakage in Robotics is a binary test.. it either works or doesn't and it's more than just software issues.. having a port with a low bandwidth will literally just break your whole system
5) Finding the optimal sensor setup is challenging, you might invest a lot of time finding whats the best configuration and setup that you will need!
6) You need to continously optimize hardware configs to be able to make them run on edge devices
7) A lot of the hardware stuff and algorithms that are STATE OF THE ART actually just don't work in the real life setting. 
8) Make sure that your ROS distribution is compatible with the rest of hardware .. and can be vertically integrated over it.
9) Always double check that dimensions are 100% correct, for example when gmapping was drifting cz of the distance between wheels wasn't correct

## Projects Management
1) Delta between observable results it quite bigger than different software projects.. A week might pass with lots of code being tested and written but poor performance on the unit test.. thats normal.. but then it just works
2) Progress in robotics isn't linear.. it works more on a cycle of big delta's.. you might spend weeks working on something with no visual progress .. but then you'll just see things working.. it's normal.. don't treat robotics projects as normal software ones.

## Career
1) Hard to do interesting work without expensive hardware, unlike a career in software
2) Building a pattern recognition skill set is different for project management and estimation than traditional software projects
3) Not as much opportunities as in Tech
4) If you're a founder, attracting people with talent is much harder than in other software fields
5) ROS is easy to catch up with and learn, and easy to build software for robots
6) With Python, Cpp, ROS, and Linux you are unstoppable
7) Possibility of growing is different
8) Still hadn't hit the moment where robot's are all over the place
9) You have to work on hardware related things, a lot!
10) To be good in robotics, you need to warm up quite a bit on your python/C++/ROS/Linux skillset
11) Networking background is relevant and critical for a lot of robotics work, connecting machines with each others and parallelizing a lot of computation/memory work
12) You're a software engineer + robotics background .. a lot of work is just core software development
13) Control Theory is heavily taught at school, but doesn't seem that we need more than PIDs for a lot of use cases
14) Differential drive equations are really important for two wheeled robots .. parameters that actually represent the robot are critical to be tuned and are somehow included in the equations

## Day in the Life
1) Latency: If you're building robots on small edge devices, then you'd better expect to face a lot of latency challenges and try to optimize around it.
2) Optimize: If you're planning to deploy robots to finish a task in real-time, then you'd better make sure you don't fill up and have any memory leakage problems
3) Customization: Take mb for example, tuning the parameters and getting them right for a particular robot is much more harder .. and migrating to a different robot is pretty close to the same problem
4) Robot Modelling: Refactoring code from mobile to aerial robotics for example, each robot has it's own models and parameters thad need to be tuned
5) Scope of projects are longer than you might expect, getting an actual MVP is software + hardware related ..
6) Changing Design of Robotics: R&D takes time and migrating to new hardware is a whole other process
7) Robotics Vision is time and computationally expensive .. processing and rendering graphics in real time is challenging for a robot ..
8) Blind spots: robot not being able to sense obstacles at certain elevations and angles .. this may cause short collision with chairs
9) Getting Stuck: the robot might physically get stuck, and that's not like a software crash
10) Reality vs. Simulation: there's a difference between reality and simulation .. In reality, there are more obstacles with various shapes. For example, in the lab there is a vertical stick that is used to hold to door open. Bcz its too thin, the robot sometimes fails to detect it and hit on it. 
There are also more human activity.
11) Inconsistency: robots using ros navigation stack can exhibit inconsisntent behaviors, for example when entering a door, the local costmap is generated again and again with slight difference each time. Also, there is no memory for the robot. It does not remember how it entered the room from the door last time.
So it needs to start out fresh again every time it tries to enter. Thus, if it enters the door in a different angle than before, it may just get stuck and give up.
12) The costmap resolution has impact on the performance of your system.. always remember how much is the scale of your system compared to what is in the real world
13) The controller frequency essentially means that, for a controller freq of 2.5 HZ it means that it takes 1/2.5 sec to update the cmd_vel value.. and with an average/median velocity of 0.1 it means that it will only effect on a 10cm scale.
14) Boundry condition: for a resolution of 0.01 it sometimes might see a 3.0 narrow opening as 2.9 and 3.0
15) There's certain ratio's of freq that should try to maintain in your system, try not to exceed them .. Make sure to always match up frequencies within your system if you want things to work out well for you
16) Fuse primary sources, don't fuse same type of data more than once because it will add up with the noise you have.
17) Knowing which algorithms to use for specific problems don't predict if you will be able to implement it. Take the EKF/UKf example, there's lot's of configs that need to be set correctly and tuned in order for the system of yours to work.
18) 100ms is 10Hz .. syncing frequencies to get them right
19) You might spend a whole day tuning a few little parameters to get things done the way you would expect them to work!
20) 100 is okay, 10 is too low, you need a higher frequency than the camera frame rate
21) Total map size is = resolution*width x resolution*heigh
22) Reverse Engineering a lot of packages and tools and software online
23) Bandwidth: increase the bits of data transfer between hardware
24) Throughput:
25) Tuning might not solve, but make performance better and to narrow down things

## 3D Navigation
- 3D navigation is similar to 2D, except with the case that for avoiding obstacles
- Sending control input commands to robots is what makes it different, since you can jump over obstacles instead of avoiding them

## Legged/Arm Robots
- Similar to cmd_vel for mobile robots, they have their own kinematic equation packages and another package to publish to control them
