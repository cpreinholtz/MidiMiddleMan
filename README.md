# Midi Middle Man
Open source under the MIT License


## Overview
Midi Middle man is designed to be used between a midi controller and synthesisers, adding functionality like choord mode, and clock sharing


## Features
Choord mode (requires poly phonic syth) / Arp Choord Mode? / Passthorugh Mode
Dummy Mode / Passthorugh Mode
Clock Forwarding / Clock Maintaining / Clock Generation
Midi Looper

## references
midi circuit
    https://learn.sparkfun.com/tutorials/midi-tutorial/hardware--electronic-implementation
    https://electronics.stackexchange.com/questions/310899/midi-out-thru-circuit-questions
        https://www.ti.com/lit/ds/symlink/sn54ahct14-sp.pdf?HQS=dis-mous-null-mousermode-dsf-pf-null-wwe&ts=1673311696199&ref_url=https%253A%252F%252Fwww.mouser.com%252F


## Software
Midi reader
Midi writer x4 (is this possible?) really only have 3 dedicated serial outs
BLE connectivity, BLE midi out? BLE clk out?
Save presets into flash?
Load presets from flash?
USB midi in / out



## Hardware Circuits
    Microcontroller
        ESP32
            3 serial ins / outs
            80 MHz to 240 MHz
            BLE included
            24 ish GPIOs
            3.3V logic
        Teensy 4.0
            4 hardware serial
            600MHz
            No BLE
            24 IO
            3.3V logic
    Midi in
        optical encoder
            6N138
        capacitor
        resistors
    Midi Out Through
        Resistors
        Buffers
            74AHTC41 
                seems to work with our logic levels
                6 channels
                inverting
    Rotary encoder
        same as dorthy but with 1/4 the conection (if same number of dimples)

    Power
        USB?
        9V? / 12V?
    Display
        LCD
        Touch?




## Hardware Components
1x 5 pin midi in
4x 5 pin midi out (3 independent serial ports in esp32)
1x 5 pin midi through
1x 3.5mm jack TS clk pulse in?
1x 3.5mm jack TS clk pulse out?
1x USB port
1x LCD display
1x LED? for tempo etc?

1x rotary encoder + sw
4x Switch
BLE connectivity?


## User interface
Menu based UI
1x rotary encoder + sw for menus (tap = move in, hold = save and go back)
Or on additional button for "back" / "save"
    Play mode
        show note, channel, velocity
        show chords
        show usable keys
    key selection (encoder to select key, or just enter this menu and use midi input to select key)
    choord / arp mode / passthrough mode
    dummy mode enable / disable per output
    Preset
        load
        save
        dump to file?
    switch behavior menu
        sw1, 2, 3, 4
            enable choord mode
            looper add layer, clear layer
    clk menu
        tempo
        start / stopping rules
        source priority pulse, midi in, internal, tap tempo, looper inputs etc
    looper menu
        add layer
        mute layer
        clear layer
        Channel output?
    CC behavior 
        Start
        Stop
        etc








Directory structure  
Root
    |-Hardware contains eagle project
    |-VS (THIS DIRECTORY IS IGNORED in the gitignore, just used for setting up Visual Studio projects for testing and debugging)
    |-Test (constains sources specifically for testing)
    |-src
        |-.h and .cpp (for arduino libs sources must be in root folder or root/src)
    |-Examples 
        |-ExScetch (contains ExScetch.ino for arduino IDE usage)