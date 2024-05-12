# 2.6 - Robot Automation

Many BEST Robotics games allow you to complete an autonomous task for extra points. There are numerous ways to approach an autonomous task, depending on the type of autonomous task. This section discusses the most common autonomous tasks and some common ways to approach them.

## 2.6.1 - Line Following

A line following autonomous task requires the robot to follow a black, white, or striped line. Line following can be achieved by mounting IR sensors to face the ground and detect when a strong black or white line is hit and turn the motors accordingly. This task was done in 2023 for the "Incision Decision" game. That code can be viewed in [this repository](https://github.com/crcsrobotics/2023-IncisionDecision) in `main.c`. More information on line following can be found in the [BESTedu IR Sensor Course](https://bestedu.bestrobotics.org/courses/best-ir-sensor/lessons/ir-sensor-line-following/).

## 2.6.2 - Path Following (Unguided)

Some games have an autonomous task that requires the robot to follow a path that is not indicated by a line or any other game object. There are two approaches that can be used to repeat an arbitrary path.

### 2.6.2.1 - Input Playback

Using input playback, the path is followed by recording the driver's input using the RobotC debug stream (discussed in section `2.5`). The debug output is then copied and converted into code using a parsing program. The recording code is then flashed to the robot. The autonomous task replays these inputs to move to robot along the desired path. This technique was used in the [2020](https://github.com/crcsrobotics/2020-outbreak) and [2021](https://github.com/crcsrobotics/2021-demodaze) games.

The major downside of this technique is that it is unreliable. Any small change on the floor (such as tape or obstacles) may interfere with the robot and cause it to deviate from the path. The major upside of this technique is that it is easy to implement in hardware and requires no changes to the robot hardware.

### 2.6.2.2 - Distance Playback

Using distance playback, the path is followed by recording the distance the robot travels using the RobotC debug stream. Like with input playback, the debug output is parsed and converted to code. To record the distance the robot travels, dark tape must be equally spaced on the robot wheels. The robot uses an IR sensor to detect these lines to count how many rotations the wheel is making. Upon playback, the robot rotates the wheels the same amount of times to repeat the desired path. This technique has not yet been used by our team.

The upside of this technique is that it is (theoretically) more reliable than input playback. The downside of this technique is that it is significantly more difficult to implement in code and also requires hardware modifications to the robot.

[Up Next (3.1) ->](https://github.com/crcsrobotics/wiki/blob/main/3%20-%20WIRING/1%20-%20MOTORS.md)
