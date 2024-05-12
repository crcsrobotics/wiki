# 4.1 - Cortex Troubleshooting

This section covers common problems you can have when working with the VEX Cortex and solutions that can solve them.

## 4.1.1 - The Cortex is not doing anything/doing the wrong thing when powered on.

### 4.1.1.1 - Dead/Low Battery

The Cortex battery may be low. 

1. Check that the "Robot" light is green.
2. If it is not green, turn the Cortex off and swap batteries.
3. Turn the Cortex back on.

### 4.1.1.2 - Confirm Wiring

Particularly with servos and the IR kit, it is easy to improperly wire the component, causing malfunctions.

1. Check all wiring junctions for correct connections (black to black, white to white, etc.).
2. Check the IR kit wiring for faults.
3. Restart the Cortex.

### 4.1.1.3 - Confirm VEXnet Connection

If the VEXnet connection is lost, the robot may not behave properly.

1. Check that the VEXnet light on both the robot and the controller are green.
2. If the lights are not green (and do not turn green within 20 seconds of robot power on), restart both the controller and the Cortex.
3. If VEXnet issues continue, see section `4.2` for VEXnet troubleshooting.

### 4.1.1.4 - Start the Debugger

When using the programming hardware kit, RobotC automatically starts the debugger after code is flashed. When the debugger is active, the code must be manually started. This behavior stops once the controller is not connected to the computer.

1. Check that you have hit the start button in RobotC.
2. If the debugger is stopped or paused, hit resume or start.

### 4.1.1.5 - Corrupted Firmware/Code

The Cortex code download may have been unsuccessful and the onboard firmware may be corrupted.

1. Re-download the master firmware to the Cortex.
2. Re-download the code to the robot.
3. If using VEXnet and this happens repeatedly, use direct USB cable connection between Cortex and computer and repeat above steps.

## 4.1.2 - The robot code download was unsuccessful.

The robot code download can be unsuccessful when using VEXnet at long distances or when flashing large amounts of code. When the code download is not successful, it can leave corrupted firmware on the Cortex.

1. Re-download the master firmware to the Cortex.
2. Re-download the code to the robot.
3. If using VEXnet and this happens repeatedly, use direct USB cable connection between Cortex and computer and repeat above steps.

## 4.1.3 - The robot light is solid red.

The robot battery is almost dead.

1. Turn off Cortex.
2. Connect new battery.
3. Turn on Cortex.

## 4.1.4 - The robot light is blinking red.

### 4.1.4.1 - Corrupted Firmware/Code

The Cortex code download may have been unsuccessful and the onboard firmware may be corrupted.

1. Re-download the master firmware to the Cortex.
2. Re-download the code to the robot.
3. If using VEXnet and this happens repeatedly, use direct USB cable connection between Cortex and computer and repeat above steps.

### 4.1.4.2 - Fatal Code Error

The Cortex may stop working and flash red if the code encounters an error.

1. Compile the program.
2. Check the compiler for errors or warnings.
3. Isolate the possible causes of an error.
4. Test each possible cause and remove root cause.
