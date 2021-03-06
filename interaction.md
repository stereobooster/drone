CRX - controller reciever (TBS CRSF, ESLR, UHF)
ODA - Omnidirectional antenna
metrics - GPS, RSSI, voltage etc. https://oscarliang.com/best-osd-quadcopter-fpv-data-on-screen-display-video
GCS - [Ground Control Stations](https://ardupilot.org/plane/docs/common-choosing-a-ground-station.html)

https://drones.stackexchange.com/questions/1855/is-it-possible-to-use-the-head-tracking-in-a-fpv-goggle-with-a-computer

```dot
digraph g{

ODA1 -> CRX   [dir=both];
ODA1 -> ODA2  [label="metric" style=dotted];
ODA2 -> ODA1  [label="commands 900Mhz"];
CTX -> ODA2   [dir=both ];
Controller -> CTX             [dir=both];
GroundStation -> CTX          [label="?" dir=both style=dotted]
Controller -> GroundStation   [label="?" dir=both style=dotted];

VTX -> ODA3;
ODA3 -> DA  [label="video 2.4 GHz"];
ODA3 -> DA  [label="OSD metric" style=dotted];
DA -> VRX;
VRX -> screen;

CTX -> "antenna tracking system" [label="GPS, altitude" style=dotted];
GroundStation -> "antenna tracking system" [label="Ground GPS, ground altitude" style=dotted];
"antenna tracking system" -> DA [arrowhead=none]

VRX -> GroundStation [label="?" dir=both style=dotted]

Camera -> VTX;

CRX -> FC [dir=both];
GPS -> FC;
Sensors -> FC;

FC -> VTX [label="OSD"];

FC -> ESC;
ESC -> motors;

PDB -> ESC;

}
```

|                              | LoS                | FPV                              | GCS                      |
| ---------------------------- | ------------------ | -------------------------------- | ------------------------ |
| Flight controller            | required (simpler) | required                         | required (more advanced) |
| Telemetry                    | required           | required, OSD                    | required, GPS            |
| Body                         | required           | required                         | required                 |
| TX                           | any                | ExpressLRS, Crossfire, etc       | SiK telemetry, RFD 900   |
| Control hardware             | Controller         | Controller + Screen or Goggles   | Laptop, phone, tablet    |
| Control software             | OpenTX, EdgeTX     | OpenTX, EdgeTX                   | Mission Planner etc.     |
| VTX                          |                    | required, WiFi broadcasting, etc |                          |
| Camera                       |                    | required, DVR, etc               |                          |
| Antenna tracker, gain antena |                    | optional                         |                          |
| GPS                          |                    | required for a. tracker          | required                 |

|       | ???maneuverability |                                    | long range???            |
| ----- | ---------------- | ---------------------------------- | ---------------------- |
| body  | multicopter      | VTOL                               | Fixed wing             |
| radio | WiFi, 2.4, 5.6   | Crossfire 900, ExpressLRS 900, 433 | SiK Telemetry 900, 433 |

Roadmap

```dot
digraph roadmap{
    rankdir="LR";

    FS[label="Flight Simulator"]
    VirtualController -> FS

    FS1[label="Flight Simulator"]
    Controller -> FS1

    Body1[label="Body with motor, servos, ECS, PDB etc"]
    RX1[label="RX the same as controller"]
    FC1[label="Flight controller"]
    S1[label="Sensors (can be built in)"]
    B1[label="Battery"]
    FS1 -> Body1
    FS1 -> RX1
    FS1 -> FC1
    FS1 -> S1
    FS1 -> B1

    Body1 -> LoS
    RX1 -> LoS
    FC1 -> LoS
    S1 -> LoS
    B1 -> LoS

    Camera[label="Camera and maybe DVR"]
    VTX[label="VTX and OSD"]
    Screen[label="Screen or goggles"]
    LoS -> Camera
    LoS -> VTX
    LoS -> Screen

    Camera -> FPV
    VTX -> FPV
    Screen -> FPV

    RX2[label="Better RX"]
    AT2[label="Antena tracker"]
    GPS2[label="GPS"]
    VTX2[label="Better VTX"]
    FPV -> RX2
    FPV -> GPS2
    GPS2 -> AT2
    FPV -> VTX2

    LRFPV[label="Long range FPV"]
    RX2-> LRFPV
    AT2-> LRFPV
    VTX2-> LRFPV

    GPS3[label="GPS"]
    Body3[label="Body with motor, servos, ECS, PDB etc"]
    RX3[label="SiK telemetry or similar"]
    FC3[label="Flight controller"]
    S3[label="Sensors (can be built in)"]
    B3[label="Battery"]
    MP[label="Mission Planer"]

    MP -> RX3
    MP -> Body3
    MP -> FC3
    MP -> S3
    MP -> GPS3
    MP -> B3

    RX3 -> GCS
    Body3 -> GCS
    FC3 -> GCS
    S3 -> GCS
    GPS3 -> GCS
    B3 -> GCS

    FS4[label="Flight Simulator"]
    MP1[label="Mission Planer"]
    MP1 -> FS4
}
```

- Determine path to upgrade. So I can start minimal, but upgrade later if I want to
- Determine how all parts would interact in the end

Simplest LoS https://www.youtube.com/watch?v=4ghxT9Di0Ag

- https://www.youtube.com/watch?v=lKw_jM2-JK8
- https://www.youtube.com/watch?v=3X2fknwE7SI
- Pulse-width modulation (PWM)

Simplest FPV https://www.youtube.com/watch?v=2FUDB2lHfMc

|                    | RX  | Stabilizer | Stabilizer with GPS | Flight controller |
| ------------------ | --- | ---------- | ------------------- | ----------------- |
| Manual             | +   | +          | +                   | +                 |
| Stabilization      |     | +          | +                   | +                 |
| Return to home     |     |            | +                   | +                 |
| Mission (Waypoint) |     |            |                     | +                 |
| Telemetry          | ?   | ?          | ?                   | +                 |
| OSD                | ?   | ?          | ?                   | ?                 |
| DVR                |     |            |                     | ?                 |
| Needs controller   | +   | +          | +                   |                   |
| OS firmware        | +   |            |                     | +                 |

|     | Telemetry | Remote commands | Video    |
| --- | --------- | --------------- | -------- |
| LoS |           | Required        |          |
| FPV |           | Required        | Required |
| GCS | Required  | Required        |          |

- [Crossfire vs. Tracer vs. Ghost vs. ExpressLRS vs. R9 vs. ACCESS vs. ACCST | RC control link shootout](https://www.youtube.com/watch?v=a8cy5BK5SbU)
- https://ardupilot.org/copter/docs/common-rc-systems.html
- https://ardupilot.org/copter/docs/common-telemetry-landingpage.html#long-range

|            | Telemetry | Remote commands | Video | Frequency      |
| ---------- | --------- | --------------- | ----- | -------------- |
| SiK        | +         | ?               |       | 430Mhz, 900MHz |
| ExpressLRS | +         | +               |       | 900Mhz, 2.4GHz |
| OpenHD     | +         | +               | +     | 2.4Ghz, 5.8Ghz |
| Crossfire  | +         | +               |       | 900Mhz         |

Power, Data Rate, Distance, Frequency (indirect influence on distance), Error correction, Ability to reconnect, Can change power (or frequency) depending on the distance.

Smaller frequency - smaller number of channels
Smaller frequency - bigger distance (depends)
Smaller frequency - smaller rate
Smaller frequency - better penetration
Bigger power - bigger distance
Bigger power - more noise in closed space
Bigger power - bigger battery drain and law limitations
Smaller frequency - more law limitations

Multiple rx/tx

Pros:

- Telemetry may have less rate and bigger distance, while other may have bigger rate and less distance
- Redundancy
- Telemetry may have omnidirectional anthena and other may have directional anthena and AAT

Cons:

- Bigger cost
- Bigger weight
- Bigger power consumption
- Harder to place all anthenas
- Need to use different frequencies
- Bigger interference
