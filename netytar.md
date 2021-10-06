---
layout: page
title: Netytar
permalink: /netytar/
---

![Netytar](/images/netytar_comp.jpg){:width="400"}

# Netytar

Netytar is a software Accessible Digital Musical Instrument controlled by gaze pointing and breath. I developed it as part of my master thesis project in Università degli Studi di Pavia, then continued its development during my PhD at Università degli Studi di Milano.

It is suitable for musicians having a quadriplegic disability, since it can be played without using their hands.

It's a monophonic instrument (i.e. able to play only one note at each time).

## Mapping

Gaze pointing controls note selection. It is detected through an eye tracker, a sensor which detects eye features through infrared cameras.

Breath controls note dynamics through a low pressure sensor. Netytar can somewhat be compared to a digital flute in this sense.

## Sensors

Netytar is compatible with Tobii Eye Trackers such as [Tobii Eye Tracker 5](https://gaming.tobii.com/product/eye-tracker-5/) (which have a cost of around 220€) or old, out of production Tobii 4C and Tobii EyeX.

Netytar's breath pressure sensor can be easily built DIY for under 30€.
A guide to build it can be found on my website following the link: [guide to sensors building](https://neeqstock.github.io/Sensors/).

## Download it and play!

Netytar is FOSS (Free Open-Source Software)! Download it and try it from [Netytar's GitHub Repository](https://github.com/LIMUNIMI/Netytar). Right now, it is only compatible with Windows 10 operative system, although in the future we'd like to make portings to other systems.
Just download the latest Release and run "Netytar.exe".
In order to run it correctly and enjoy it fully, you may need:

- Digital-7 font, which you can [download and install from Dafont](https://dl.dafont.com/dl/?f=digital_7);
- Since Netytar is a MIDI controller, you may need a software synthesizer to reproduce sounds. You can try it using Windows pre-built MIDI synthesizer, but you can get way better sounds for free following [this guide I've prepared](https://neeqstock.github.io/VST_Guide/).

## Virtual keyboard layout

The keyboard layout of the instrument was created ad-hoc for gaze interaction, and is therefore different from the keyboard of any traditional musical instrument. There is a fixed geometrical rule which determines the intervals between each key.

![Geometrical rule in Netytar](/images/netytar_geometrical_rule.png){:width="400"}

Numbers indicate the interval in semitones between a specific key and the central key. This rule is true for any key on the keyboard.
Given this, the layout is *isomorphic*. This means that transposing a musical piece means simply repeating the same geometrical shape elsewhere.

By maintaining breath pressure and shifting the key with gaze movement you can obtain a _legato_ effect, i.e. an immediate note change without pauses. Netytar's layout is such that the most common musical intervals can be performed without having to cross "intermediate keys" with your gaze (which would mostly be detected by the eye tracker, even if your eyes are fast!). 

The following figure shows all positive musical intervals (in semitones) and their relative key positions. It may be noted that some are simpler than others to perform.

![Intervals in Netytar](/images/netytar_intervals.png){:width="400"}

- **Red** intervals are very easy to play;
- **Green** intervals are more distant, but still very easy;
- **Blue** intervals still do not require to cross intermediate keys, but are more difficult and require a long movement;
- **Pink** intervals require to cross intermediate keys.

We're still working to implement a way to make an octave jump (12 semitones) without having to cross intermediate keys. However, all the intervals requiring intermediate key crossing are already feasible without the "legato" functionality: the musician should just interrupt the breath flow during the transition.

### Colors

Key colors indicate the note's degree in the current scale. Degrees are colored as follows: **Red (1st), Orange (2nd), Yellow (3rd), Green (4th), Blue (5th), Purple (6th), Pink (7th).**

A line connects the note from the given scale. A **Red** line denotes a major scale, while a **Blue** line denotes a minor scale.

You can change the highlighted scale by using the scale selector or by blinking (see below both).

## Autoscrolling

Netytar implements an *Autoscrolling* functionality. This means that the interface will scroll automatically and smoothly following your gaze, to put the gaze point at the center of the screen. This functionality ensures that the area of the virtual keyboard can be bigger than the actual computer screen, having potentially an unlimited extension and an unlimited number of keys drawn.

## Commands and functionalities

Let's see first all the keybindings, which are very important to know and understand before playing:

- The **Q** key locks the mouse cursor on the gaze and hides it; the **A** key releases it back. This is due to the fact Netytar works by controlling the mouse cursor.
- The **W** key activates the *Autoscrolling* function described above; **S** deactivates it.
- **Spacebar** plays the current note (at full intensity) while in "Keyboard dynamics" mode. Since the spacebar could unwantedly activate interface elements, click once on the _Neutral Area_ described below before playing.

Let's now see how the *Settings* interface works:

![Start and Exit buttons](/images/netytar_menu_startexit.png){:width="400"}

Before playing and being able to interact with any element in Netytar you must before press **Start** to init the instrument. **Exit** closes the program, since there are no application window borders nor "X" button.

![Scale selector and intensity indicator](/images/netytar_menu_scalebreath.png){:width="400"}

The list on the left can be used to change the selected musical scale, which results in Netytar highlighting with colors a different musical scale on the virtual keyboard.
The indicator on the left indicates dynamic intensity of the played note (e.g. breath pressure).

![Dynamic control mode](/images/netytar_menu_scalebreath.png){:width="400"}

These selectors change the way notes dynamics are controlled. **Keyboard** allow you to play notes using your PC keyboard (spacebar), while **Breath** allow you to use Netytar's breath sensor.

![Breath sensor port selector](/images/netytar_menu_breathport.png){:width="400"}

This selector is used to tell your computer which USB port is the breath sensor connected to. You must do it before playing with the breath sensor. "COM" is the standard prefix for USB ports. When the breath sensor is detected in a COM port, the indicator becomes green.

![MIDI port selector](/images/netytar_menu_midiport.png){:width="400"}

This is instead used to specify which MIDI port is Netytar communicating to. Netytar will output MIDI messages to that port.

![Current note indicators](/images/netytar_menu_noteinfo.png){:width="400"}

These indicators show informations on the currently note/key.

- The **left** one indicates the MIDI pitch;
- The **center** one indicates the name of the current note, followed by its octave;
- The **right** one shows a *"B"* if the user is blowing in the breath pressure sensor (or pressing spacebar in Keyboard dynamic mode), or a *"_"* otherwise.

!["Mod" and "BSwitch" switches](/images/netytar_menu_modbswitch.png){:width="400"}

These switches are used to control two specific performance parameters.

- **Mod**, if activated, sends a modulation/vibrato control when breath pressure reaches a certain level, and grows even more while adding more pressure;
- **BSwitch**, if activated, cuts off note dynamics management while blowing on the breath pressure. The breath sensor becomes like a switch: no intensity if you are not blowing, full intensity if you are blowing, even subtly.

![Other performance switches](/images/netytar_menu_sharpblinkslide.png){:width="400"}

- **Sharp notes** controls if sharp notes (accidentals) are shown on Netytar's virtual keyboard;
- **Blink scale**, if activated, allow you to change the highlighted scale on Netytar's virtual keyboard using eye blinks. A left eye blink will draw the major scale for the current gazed note; a right eye blink will draw the minor scale.
- **Slide play** allows you to play a "legato" by simply gazing another key, without having to interrupt your breath flux. If disabled, you are required to stop breathing and breath again to make a new note. This could be easier and enhance precision in given musical pieces.

![Keys distance slider](/images/netytar_menu_keysdistance.png){:width="400"}

This slider allow you to change the distance between keys on the virtual keyboard. Lower distances mean less eye movement, higher distances mean increased precision.

![Neutral zone](/images/neutralzone.png){:width="400"}

I've included this button to click it before playing with in *Keyboard dynamics* mode (explained above). This is due to the fact that the spacebar key could otherwise activate interface elements unwantedly.

## Blink based commands

- By **left/right blinking** while gazing a note, as said above and if "Blink Scale" mode is enabled, you can draw the relative major/minor scale having that note as root;
- By **blinking with both eyes at the same time** while a note is being played, that note is repeated (stopped and immediately played again).

## Want to be a virtuoso? Hmm...

Of course you can become a big player! But with regards to speed while playing Netytar, as with most of gaze based musical interfaces, the maximum execution speed (the maximum number of different notes you can play in a given time span) is bound to 3-4 notes per second. This is due to our physiology, since it has been measured that we as humans aren't able to make more than 3-4 saccadic movements (i.e. flashy eye movements) per second.

Note repetition speed instead is less bounded, since it depends on how fast you can blink both eyes or stop your breath and blow again.

## Scientific papers about Netytar

We talked about Netytar in the following papers, where you can find additional informations on the instrument:

- Davanzo N., Dondi P., Mosconi M. & Porta M. (2018). «Playing Music with the Eyes through an Isomorphic Interface». In *Proc. of the Workshop on Communication by Gaze Interaction*, 1–5. Warsaw, Poland: ACM Press, 2018. [Link (DOI)](https://doi.org/10.1145/3206343.3206350)
- Davanzo N. & Avanzini F. (2020). «A Method for Learning Netytar: An Accessible Digital Musical Instrument»: In *Proceedings of the 12th International Conference on Computer Supported Education*, 620–28. Prague, Czech Republic: SCITEPRESS - Science and Technology Publications, 2020. [Link (DOI)](http://dx.doi.org/10.5220%2F0009816106200628)
