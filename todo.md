### Body

- Simplest fixed wing (ZOHD Dart XL or similar)
  - Build kit
  - ELRS RX
  - Battery

### DIY body

- http://rc-plans.com/catalog/item421.html
- http://rc-plans.com/catalog/item254.html
- http://rc-plans.com/-how-to-video/2564-insanely-light-first-3d-printe.html

### Controller

- https://www.radiomasterrc.com/collections/tx16s/products/tx16s-mark-ii-radio-controller
  - ELRS ([How much channels](https://www.expresslrs.org/2.0/faq/#how-many-channels-does-elrs-support))
    - No chanels per se, but we can have CRSF to PWM adapter which will give 4 channels
  - 2.4 GHz
  - EdgeTX
  - Can it be connected to laptop and simulator?
- Which simulator to use?
  - https://oscarliang.com/fpv-simulator/
  - https://www.youtube.com/watch?v=BvFzHivbTTQ
  - [Picasim](http://www.rowlhouse.co.uk/PicaSim/): free and accurate simulation.
  - [Realflight](https://www.realflight.com/) 9.5 - Realistic, huge collection of RC aircraft including drones, helicopters and more.
  - [Aerofly RC](https://www.ikarus.net/en/) - Also realistic, drones, helicopters and more.
  - [Wings](https://www.wings-sim.com/) - Designed for RC FPV wing racing.
  - https://www.youtube.com/watch?v=I7lUTEJM62g
  - Best free simulator: [Orqa FPV.Skydive](https://skydive.orqafpv.com/)
  - Best sim for racing: [Velocidrone](https://www.velocidrone.com/)
  - Best sim for freestyle: [Uncrashed](https://store.steampowered.com/app/1682970/Uncrashed__FPV_Drone_Simulator/)
  - Best sim for Whoop Racing: Velocidrone w/ Micro Pack
  - Best free Whoop Racing sim: Tiny Whoop Go
  - The only sim with my house in it as a level: [Liftoff](https://www.liftoff-game.com/)
  - Best sim for low-spec computers: [FPV Freerider](https://store.steampowered.com/app/854250/FPV_Freerider/)
  - Largest open-world map: [GTA5 drone mod](https://www.gta5-mods.com/scripts/fpv-drone-racing)
  - Lets you emulate your actual drone physics: [AI Drone Sim](https://store.steampowered.com/app/1608560/AI_Drone_Simulator/)
  - Best value for money: [DRL Simulator](https://store.steampowered.com/app/641780/The_Drone_Racing_League_Simulator/)
  - https://apps.apple.com/de/app/controllers-lite/id673660806?mt=12

### OpenHD

- https://www.youtube.com/watch?v=ODw_qSzMan4
- 2x Raspberry pi
- 2x WiFi boards
- Camera
  - Which? https://openhd.gitbook.io/open-hd/hardware/cameras
  - latency (fps 60, speed of transmittion from camera to board)
  - quality (lens width, resolution 1080p, size of matrix, other chipset features)
  - size of tranmsition (codec, h.265?)
- TouchScreen ?
- Estimate cost

### GCP

- Which app to use?
- Flight controller
  - Which?
- GPS + compass
- RX
  - I guess SiK Telemetry

# Parts

[Blue stick: 15 Euero, 2.4 GHz, no diversity](https://www.aliexpress.com/item/4000051464939.html)

[anthena 5 Euero, 2.4 GHz](https://www.aliexpress.com/item/1005001968013220.html)

Raspberry pi 4 50-100 Euero

Pi Cam HQ 50Euero + lens

Touchscreen 70Euero

**Total**: About 330?

Problem 2.4 Ghz may interfer with ELRS on joystick

ELRS900 TX + RX 30 euro

Joystick 200 euro

Wing 100 euro

Motor, servos, esc, battery (look in wing spec)

FC ?

https://www.youtube.com/watch?v=nsergu_J1vM

- [F405, 63 Euro](https://www.banggood.com/30_5+30_5mm-Matek-System-F405-HDTE-Flight-Controller-5V-1_5A-BEC-for-FPV-Racing-RC-Drone-p-1958580.html?cur_warehouse=CN&rmmds=search)
- F745 copter
- [F765 wing, 83 Euro](https://www.banggood.com/Matek-Systems-F765-WSE-STM32F765VIh6-Flight-Controller-Built-in-OSD-for-RC-Airplane-Fixed-Wing-p-1890404.html?cur_warehouse=CN&rmmds=search)
- H743

Copter ?

[Sik 900MHz, 60 euro](https://shop.holybro.com/sik-telemetry-radio-v3_p1103.html?)

[Sik 433MHz, 60 euro](https://store.mrobotics.io/product-p/mro-sikv2airgnd-mr.htm)

[Mapple](https://www.aliexpress.com/item/1005001638854607.html?spm=a2g0o.productlist.0.0.6a8195c3HgygiI&algo_pvid=a542ed57-5da1-4ce2-a5ef-44ed955e6529&algo_exp_id=a542ed57-5da1-4ce2-a5ef-44ed955e6529-1&pdp_ext_f=%7B"sku_id"%3A"12000016928054435"%7D&pdp_npi=2%40dis%21EUR%21%2126.49%21%21%21%21%21%402103399116565939874605014e5867%2112000016928054435%21sea)

[Mapple](https://www.aliexpress.com/item/32989509234.html?spm=a2g0o.detail.1000014.4.5c0b26eaWvxUbk&gps-id=pcDetailBottomMoreOtherSeller&scm=1007.40050.281175.0&scm_id=1007.40050.281175.0&scm-url=1007.40050.281175.0&pvid=43dbde8d-9846-4742-b1a5-65feef3dae08&_t=gps-id:pcDetailBottomMoreOtherSeller,scm-url:1007.40050.281175.0,pvid:43dbde8d-9846-4742-b1a5-65feef3dae08,tpp_buckets:668%232846%238110%231995&pdp_ext_f=%7B"sku_id"%3A"66866394036"%2C"sceneId"%3A"30050"%7D&pdp_npi=2%40dis%21EUR%21%2119.9%21%21%21%21%21%402101d1bd16565929613467802ec396%2166866394036%21rec)

[lollipop](https://www.aliexpress.com/item/32813557046.html?spm=a2g0o.productlist.0.0.25484c57Bvh2Ur&algo_pvid=b557cc36-7b31-4022-9f67-fb142501cbc3&algo_exp_id=b557cc36-7b31-4022-9f67-fb142501cbc3-0&pdp_ext_f=%7B"sku_id"%3A"64655346262"%7D&pdp_npi=2%40dis%21EUR%21%214.65%21%21%21%21%21%402101d91e16566002541885828e150a%2164655346262%21sea)
