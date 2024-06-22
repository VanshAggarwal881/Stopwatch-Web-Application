# Stopwatch-Web-Application
# Live Demo : https://vanshaggarwal881.github.io/Prasunet_WD_02/
# Understanding the Stopwatch
Core Components
# 1) Timer Display:
The primary element of a stopwatch is the timer display, which shows the elapsed time in a human-readable format (minutes, seconds, and milliseconds). This is crucial as it visually represents the passage of time for the user.

# 2) Start/Stop Button:
This button serves a dual purpose: to start the timing when pressed initially and to stop the timing when pressed again. This toggling functionality is essential for allowing the user to control the stopwatch.

# 3) Lap Button:
The lap button allows the user to record intermediate times without stopping the overall stopwatch. This is particularly useful for tracking multiple intervals within a single session.

# Core Functionalities
# 4) Elapsed Time Calculation:
To create a functional stopwatch, you need to calculate the elapsed time. This is done by recording the start time when the user begins the stopwatch and comparing it to the current time whenever the display needs to be updated. The difference between these times gives the elapsed time.

# Variables Needed:

* startTime: Stores the time when the stopwatch was started or resumed.........
* updatedTime: Captures the current time during each tick of the timer........
* difference: The difference between updatedTime and startTime, representing the total elapsed time......
* tInterval: Holds the interval ID for the timer, which allows us to start and stop the repeated execution of a function......
* running: A boolean flag indicating whether the stopwatch is currently running........
* savedTime: Stores the elapsed time when the stopwatch is paused, allowing the timer to resume from where it left off.....
* lapCounter: Counts the number of laps recorded, useful for labeling each lap........
# Starting and Stopping the Timer:
When the start button is pressed, the current time is recorded using JavaScript’s Date().getTime(), which returns the number of milliseconds since January 1, 1970. This value is stored in startTime. If the stopwatch is stopped and then restarted, the previously elapsed time (savedTime) is subtracted from the current time to ensure continuity.

# Updating the Display:
The display is updated at regular intervals (every 10 milliseconds) using setInterval. The getShowTime function calculates the elapsed time by subtracting startTime from the current time (updatedTime). This difference is then formatted into minutes, seconds, and milliseconds. The calculations use modulo operations to ensure values stay within their respective limits (e.g., seconds within 60, milliseconds within 1000):

* minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));..........
* seconds = Math.floor((difference % (1000 * 60)) / 1000);.........
* milliseconds = Math.floor((difference % 1000) / 10);..........
* This formatting ensures the displayed time is always in the correct format, enhancing readability.
# Recording Laps:
When the lap button is pressed, the current display time is captured and stored. This is achieved by appending the current displayed time to a list of laps, which is then displayed to the user. This allows for intermediate times to be recorded without stopping the main timer.

# Reset Functionality:
Resetting the stopwatch involves clearing the interval, resetting all variables to their initial states, and clearing the display. This ensures that the stopwatch can be started fresh without any residual data from previous sessions.

# Logical Flow in the Code
The logical flow of the stopwatch involves a series of checks and operations that are orchestrated through event handlers tied to the buttons. When the start button is pressed:

If the stopwatch is not running (running is false), the current time is recorded, and the interval to update the display is started.
If the stopwatch is running, the interval is cleared, stopping the updates, and the elapsed time is saved.
The getShowTime function, executed at each interval tick, updates the display with the formatted elapsed time, ensuring that the user sees an accurate and continuously updating time display.

The lap functionality records the current displayed time and increments the lap counter, allowing multiple laps to be recorded and displayed sequentially.

Finally, the reset function clears all timers and data, preparing the stopwatch for a new timing session.
