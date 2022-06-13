# drone

## Roadmap

```dot
digraph graphname {
  freestyle[label="Freestyle Flying and Racing"];
  autonomous[label="Autonomous Flying and Long Range"]

  purpose -> freestyle;
  purpose -> autonomous;

  freestyle -> copter;
  autonomous -> "fixed wing, glider";
  autonomous -> VTOL;

  subgraph cluster_frames {
    label="Frame"

    copter;
    "fixed wing, glider";
    "VTOL";
  }

  freestyle -> betaflight;
  autonomous -> inav;
  autonomous -> ardupilot;

  subgraph cluster_fcfirmaware {
    label="FC firmware"

    betaflight;
    inav[label="iNav"];
    ardupilot;
  }

}
```

## Frame types

https://docs.px4.io/master/en/airframes/airframe_reference.html#plane
https://ardupilot.org/copter/docs/frame-type-configuration.html

```dot
digraph graphname {
  splines="curved";
  drone -> copter -> VTOL;
  drone -> "fixed wing" -> VTOL;
  drone -> other;
}
```

**VTOL** - Vertical Take-Off and Landing
**FPV** https://ardupilot.org/plane/docs/fpv-plane.html

Params/features:

- low speed (stall speed)
- high speed
- resistance in case of crash
- acrobatics
- (compartment) is it enough space for flight controller etc?
- can it be dissabled for transportation?

https://www.youtube.com/watch?v=voHJ-VDGi4I

## Features

- Model remote controled (RC) airplane
  - Think of hobby airplane models controlled with RC before drone become a thing
  - Uses stabiliser
  - Often frames are build from styrofoam
- First Person View (FPV)
  - Next step you have the same RC, but as well you can see objects as if you are pilot on the drone. So drone can be manipulated even if it's out of sight
  - Uses flight controller
  - On Screen Display (OSD) - overlays technical info over FPV video
  - Inertial measurement unit (IMU)
  - Racing or acrobatics vs long range drones
- Autonomous drones
  - Those doesn't need pilot instead they are manipulated by flight computer and missin control software
  - Uses flight controller and flight computer

## Parts

- Frame
- [Flight controller (FC)](https://fusion.engineering/flight-controllers-explained-for-everyone/)
- GPS Module
- Electronic Speed Controllers (ESC)
- Battery
- Power Distribution Boards (PDB)
- Motor(s)
- Propeller(s)
- Servos
- Reciever (RX)
- Joystick/Controller
- Video Transmiter (VTX)
- FPV Anthena
- FPV Camera
- Video Receivers
- FPV Goggles

## Open source drone or DIY drone

### 3D print frame

See http://rc-plans.com/catalog/1004

Paid options:

- https://3dlabprint.com/product-category/3dlabgang/
- https://www.eclipson-airplanes.com/
- https://www.planeprint.com/
- https://www.rc3dprint.com/planes

### Flight controller

- Pixhawk
- Matek https://inavfixedwinggroup.com/shopping-list/flight-controllers/
- https://www.researchgate.net/publication/325134452_A_Survey_of_Open-Source_UAV_Flight_Controllers_and_Flight_Simulators
  - https://www.connectedpapers.com/
- [A survey of Open-Source UAV flight controllers and flight simulators](https://www.academia.edu/74379497/A_survey_of_Open_Source_UAV_flight_controllers_and_flight_simulators)

### Flight controller firmware

- Freestyle Flying and Racing
  - [Betaflight](https://github.com/betaflight/betaflight)
  - [Emuflight](https://github.com/emuflight/EmuFlight)
  - [KISS](http://kiss.flyduino.net/downloads/)
  - [FlightOne FalcoX](https://shop.flightone.com/product/falcox-fc-license/)
- Autonomous Flying
  - [iNav](https://github.com/iNavFlight/inav)
  - [Ardupilot](https://github.com/ArduPilot/ardupilot)
- Honorable Mentions
  - [Multiwii](http://www.multiwii.com/)
  - [Baseflight](https://github.com/multiwii/baseflight)
  - [Cleanflight](http://cleanflight.com/)
  - [Butterflight](https://github.com/ButterFlight/butterflight)
  - [OpenPilot](https://github.com/commaai/openpilot)
  - [LibrePilot](https://github.com/librepilot/LibrePilot)
  - [TauLabs](https://github.com/TauLabs/TauLabs)
  - [dRonin](https://dronin.org/)

[source](https://oscarliang.com/mini-quad-fc-firmware/)

[Firmwares for Flight Controllers, Matek](http://www.mateksys.com/?p=5159)

## Examples of flying wing setups

- https://www.fpv24.com/en/fpv-nurfluegler
- https://inavfixedwinggroup.com/category/recommended-setups/long-range-setups/
- https://www.fpvknowitall.com/ultimate-fpv-shopping-list/
- https://ardupilot.org/plane/docs/miniTalon-build.html

## Controller

aka Transmitter, Radio Transmitter, Radio

- [Introduction](https://www.youtube.com/watch?v=SrN6ps4NM10)

Example:

> - [UHF RC](https://www.youtube.com/watch?v=anLwhavmA1k) (433MHz)
> - TBS Crossfire (868MHz/915MHz)
> - [ExpressLRS / ELRS](https://github.com/ExpressLRS/ExpressLRS) (2.4GHz and 868MHz/915MHz)
> - TBS Tracer (2.4GHz)
> - Immersion Ghost (2.4GHz)
> - FrSky (2.4GHz)
>
> -- https://oscarliang.com/radio-transmitter/

TBS - team blacksheep
LRS - long range systems

Old:

- https://github.com/openLRSng
- https://github.com/DTFUHF

## GCS

- iNav https://www.rcgroups.com/forums/showatt.php?attachmentid=11240545&d=1538097119
  - Mission Planner for INAV (Android), MobileFlight (IOS) and mwp (Linux)
- https://ardupilot.org/plane/docs/common-choosing-a-ground-station.html
- [Mission planer](https://github.com/ArduPilot/MissionPlanner)
- [MobileFlight](https://flyinghead.github.io/mobile-flight/)
- [mwp](https://github.com/stronnag/mwptools)
- [APM Planner 2.0](https://github.com/ArduPilot/apm_planner)
- [MAVProxy](https://github.com/ArduPilot/MAVProxy)
- [QGroundControl](http://qgroundcontrol.com/)
- [UgCS - Universal Ground Control Station](https://github.com/ugcs)
- [Tower (a.k.a. “DroidPlanner 3”) ](https://github.com/DroidPlanner/Tower)
- MAV Pilot 1.4
- SidePilot
- [AndroPilot](https://github.com/geeksville/arduleader/tree/master/andropilot) not supported

Components:

- Flight controller firmware
- Autopilot
- Mission planer
- Flight tracker
- Simulator
