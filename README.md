# JoyCon-Driver
A vJoy feeder for the Nintendo Switch JoyCons with analog stick support and motion controls


## How to use
1. Install vJoy, found here: http://vjoystick.sourceforge.net/site/

2. Setup your vJoy Devices to look like this:
    * http://i.imgur.com/tRBtAWN.png
    * http://i.imgur.com/bF1re0X.png

3. Pair the JoyCon(s) to your PC

4. Run the Application, if it doesn't detect your JoyCon(s), make sure they are fully paired/connected and restart the program.
	* There's a precompiled version of the program in the release folder with all of the dlls it needs, just download the zip and extract it.

5. Once the program is running vJoy should register the input from the JoyCons.
    * To verify it's working you can use the vJoy monitor that comes with vJoy, it looks like this: http://i.imgur.com/x4Fn7Cq.png
    * To re-pair the JoyCons go into Settings and remove the JoyCon(s) and then pair them again.
    * You'll likely want to use this with something like x360ce (http://www.x360ce.com), which will let you map the vJoy device to a virtual xbox controller for games that support them.


## Important Notes
* The JoyCons seem to need to be re-paired anytime after they've reconnected to the switch.

These are the settings you'll want to change:
	* Command line arguments:
	* Run with "--combine" to combine the left and right joycons
	* Run with "--auto-center" to automatically center the sticks
	* Run with "--enable-gyro" to enable motion controls
	* Run with "--mario-theme" to play a (bad) version of the mario theme on the first JoyCon connected
	* Run with "--LXO 16000" to add an X Offset to the Left JoyCon of 16000
	* Run with "--LYO 16000" to add an Y Offset to the Left JoyCon of 16000
	* Run with "--RYO 16000" to add an X Offset to the Right JoyCon of 16000
	* Run with "--RYO 16000" to add an Y Offset to the Right JoyCon of 16000


These are the default settings:
```
// there appears to be a good amount of variance between JoyCons,
// but they work well once you find the right offsets
// these are the values that worked well for my JoyCons:
// alternatively just use --auto-center, it overrides these settings
int leftJoyConXOffset = 16000;
int leftJoyConYOffset = 13000;

int rightJoyConXOffset = 15000;
int rightJoyConYOffset = 19000;

// multipliers to go from the range (-128,128) to (-32768, 32768)
// These shouldn't need to be changed too much, but the option is there
// I found that 240 works for me
int leftJoyConXMultiplier = 240;
int leftJoyConYMultiplier = 240;
int rightJoyConXMultiplier = 240;
int rightJoyConYMultiplier = 240;

// Enabling this combines both JoyCons to a single vJoy Device(#1)
// when combineJoyCons == false:
// JoyCon(L) is mapped to vJoy Device #1
// JoyCon(R) is mapped to vJoy Device #2
// when combineJoyCons == true:
// JoyCon(L) and JoyCon(R) are mapped to vJoy Device #1
bool combineJoyCons = false;

bool reverseX = false;// reverses joystick x (both sticks)
bool reverseY = false;// reverses joystick y (both sticks)

// Automatically center sticks
// works by getting joystick position at start
// and assumes that to be (0,0), and uses that to calculate the offsets
bool autoCenterSticks = false;


// enables motion controls
bool enableGyro = false;

// plays a version of the mario theme by vibrating
// the first JoyCon connected.
bool marioTheme = false;

```








## Credits
  * To everyone who helped at: https://github.com/dekuNukem/Nintendo_Switch_Reverse_Engineering/

