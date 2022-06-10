CRX - controller reciever (TBS CRSF, ESLR, UHF)
ODA - Omnidirectional antenna
metrics - GPS, RSSI, voltage etc. https://oscarliang.com/best-osd-quadcopter-fpv-data-on-screen-display-video
GCS - [Ground Control Stations](https://ardupilot.org/plane/docs/common-choosing-a-ground-station.html)

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
