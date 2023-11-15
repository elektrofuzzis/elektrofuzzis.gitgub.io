---
title: Switches & Buttons
layout: category
lang: en
classes: wide
sidebar:
    nav: gettingstarted-en
---

The ftSwarm knows switches and buttons, isn't that the same thing? Switches are external buttons connected to inputs A1 to A6. Buttons are only available with the *ftSwarmControl* - the permanently installed buttons are addressed via a separate class.

### Normally closed & normally open

*fischertechnik* mini switches have 3 pins. In a standard configuration, use pin 1 & 3. The switch "normally open" and closes pressing the button. Using pin 1 & 2 the switch is normally closed and opens by pressing the button. This configuration is useful for e.g. emergency stops - a broken cable will activate the emergency stop as well.

```cpp
normallyOpen   = FtSwarmSwitch( 4711, FTSWARM_A1 );
normallyClosed = FtSwarmSwitch( 4711, FTSWARM_A2, false );
```

### Toggles

In many applications your're not interested in the state of a switch, you want to know if the switch has changed it's state. You could wait actively using

```cpp
while (switch.isReleased());
```

This works fine. But you block a core and it's a little bit difficult to do other things while waiting. Since the firmware polls regulary all inputs states in the background, it notices status changes, too.

```cpp
void loop() {

  if (switch.hasToggledUp()) motor.setSpeed(100);
  if (switch.hasToggledDown()) motor.setSpeed(0);
  
  // use the time and do someting else
```

is smarter, because you're not blocking your application.

**Attention:** Each call of the *Toggle* commands resets the toggle status. This is necessary so that only the signal changes are recognized. However, this leads to

```cpp
if ( (switch.hasToggeledDown()) || (switch.hasToggeledUp()) ) led.setColor( CRGB:Green );
```

only reacts to toggle-up events. If the condition is evaluated, ``switch.hasToggeledDown()`` is executed first.

- If there was a toggle-down event, the condition is true and the led turns green.
- If there was no toggle-down event, however ``switch.hasToggeledDown()`` causes the toggle status to be reset. An existing toggle-up event is therefore deleted, ``switch.hasToggeledUp()`` will always be false.

Pressing the switch will not switch the LED to green.
