# Standard Operating Procedures for CanCam C1-23-ATAT CNC

## Turn on procedure
1. Connect the compressed air at the back of the CNC, and ensure at least 80 bar is available. You may need to disconnect the compressed air line with the quick-connect at the base of a nearby compressed air handgun (just pull back on the brass sleeve and the quick-connect should pop open). It is normal (we think) that compressed air is escaping at the spindle head. Don't stick your fingers in the spindle to investigate; we've done that and it doesn't help.
2. Ensure the CNC cutting table is free of parts and clamps to prevent unintended motion from either damaging parts or the machine itself.
3. Ensure the mains power is enabled at 'clock' wall mushroom estop and switch to the right of it.
4. Ensure the chiller main power switch is disabled for now (it will get power only when the CNC is turned on).
5. Disable the estops on the main unit and handbox. Nothing should happen when you do this.
6. Press the first (i.e. left-most) green on/off switch at front of CNC. This enables power to the gantry control, handbox, and tool changer pneumatics.
7. Turn on the chiller main power switch. Ensure no chiller alarms are audible and that the alarm light on the chiller is off. Check the chiller in/out flow for signs of flow (moving little air bubbles, may be hard to tell).
8. Carefully perform the reference point homing operation that the handbox suggests with "Back to Ref. point?", and press OK. This operation will move the head to the hardware home and then to the previous software home position, which may not be what you want (be ready to stop motion in case of obstruction on the CNC table). When hardware homing, keep an eye on X- limits as one of the cables gets rather close to being pinched.
9. At this point the CNC is capable of performing full navigation tests (but you are not able to turn on the spindle yet).
10. Press the second green on/off switch at the front of the CNC. This enables power to the spindle.
11. Press the third green on/off switch at the front of the CNC. This enables power to some other part of the machine that I haven't identified or isolated yet. This is potentially for the vacuum pump of the table, which is not a feature we purchased, but the hookup is available for a future upgrade.
12. Press the fourth green on/off switch at the front of the CNC. This enables power to some other part of the machine that I haven't identified or isolated yet. This is potentially ffor the chip and swarf vacuum, which is not a feature we purchased, but the hookup is available for a future upgrade.

## Turn off procedure
1. Press each of the enabled green buttons in opposite order as during the turn on procedure (i.e. when turning off, press them from right to left).
2. Turn off the chiller main power switch.
3. Enable the estops on the handbox and the main unit. Nothing should happen when you do this (since everything should be off already).
4. Disconnect the compressed air at the back of the CNC (optionally, reconnect the quick-connect to the compressed air handgun if that is how you found the compressed air when you arrived).

## Common handbox operations:
- K1: release/accept collet (it will ask to confirm that you are ready to catch the collet to prevent damage to the bit).
- K2: raise/lower the vacuum sleeve
- X+/X-: move head right/left
- Y+/Y-: move gantry away/towards you
- Z+/Z-: move the head up/down
- Sine(5): switch between slow/fast jog
- Zigzag+/Zigzag-: increase/decrease spindle speed (10% intervals)

## Creating appropriate gcode in OnShape (free and what we use in PHYS 4300):
1. Create a design in onshape.
2. Use the free kiri:moto app to export geometry. (follow their instructions)
    1. Select the stock you are starting from.
    2. Select the operations you are intending to use (roughing, finishing, etc).
    3. Take note of the zero in the coordinate system.
    4. Export to a gcode file with extension nc saved on a USB stick.
3. Insert the USB stick
    1. Load the nc file (select the file with OK and select the Load option with 1)
    2. Go to the zero of the CNC job and press the XY=0 and Z=0 buttons (or do them separately)
    3. Press the play button to start the job.
    4. Press IV+ or IV- to change the instructions speed.

## Using the automatic tool changer.
1. Ensure the correct tools are entered in the setup (gcode commands for T1, T2, T3, up to T6 will be automatically swapped out by the CNC.
2. Ensure that the slot for the currently installed tool is empty (check menu, 4. Oper. Params, 18. Tool Change), or it will try to put the tool back in a slot where there is already a tool inserted.

## References
- [CanCam NK105-G3 manual](https://www.cancam.ca/wp-content/uploads/2016/03/NK105-2015-G3-final.pdf)
- [Weihong NK105-G3 manual](http://doc.weihong.com.cn:8889/doc/nk105/topic/overview_en.html)
- [Weihong Gcode manual (reference manual, for fixing gcode specific to NK105)](http://doc.weihong.com.cn:8889/doc/gcode_programming/index_en.html)
