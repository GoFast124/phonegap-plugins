# Grand Theft Adelaide

A 3D, GTA-style browser game set in Adelaide, South Australia. It's a single HTML file with no build step. It renders with [Three.js](https://threejs.org) loaded from the jsDelivr CDN, so it needs an internet connection. Open `index.html` in a browser to play (some browsers need it served over HTTP rather than opened as a file, for example with `python3 -m http.server`).

The game has a third-person chase camera, real-time sun and shadows, a day/night cycle with lit office windows and headlights, glass towers that reflect the sky, and shiny cars.

## Controls

| Key | Action |
| --- | --- |
| WASD / arrows | Walk or drive (traffic keeps left) |
| F / Enter | Get in or out of a car, or jack one |
| Space | Handbrake |
| J / Ctrl / click | Punch or shoot |
| Shift | Sprint |
| Q | Switch weapon |
| Right-drag / swipe | Look around |
| M | Map |
| P / Esc | Pause and mission list |

On phones you get an on-screen joystick and buttons instead.

## The map

The map is a simplified Adelaide:

- **CBD square mile:** the real street grid, King William St, Rundle Mall (with the Mall's Balls), Victoria Square and the terraces.
- **North Adelaide:** Adelaide Oval and the Zoo.
- **River Torrens:** with bridges.
- **The Parklands:** includes the Adelaide 500 street circuit.
- **Suburbs:** Glenelg (with the Jetty and the tram), Port Adelaide docks, the western suburbs and Unley.
- **Hills:** the winding road up to Mt Lofty, plus Hahndorf.

## Missions

| Mission | Where it starts |
| --- | --- |
| Where'd You Go To School? | Railway Station, North Tce |
| Iced Coffee Run | Port Adelaide docks |
| Pie Floater | Adelaide Oval |
| Showdown | Hindley St |
| The Mall's Balls | Rundle Mall |
| Swooping Season | Victoria Square |
| Beat the Tram | Victoria Square tram stop |
| Adelaide 500 | East Tce |
| Kitchener Buns to Lofty | Central Market |

## Adding a mission

Missions are data in the `MISSIONS` array in `index.html`. Coordinates are map tiles: the map is 200×150 tiles, and the CBD runs from about x 60–152, y 50–122. Press M in game to see the map. Each step has one of these types:

| Step type | What it does |
| --- | --- |
| `getcar` | Waits until the player is in a car. |
| `goto` | Reach a point. Options: `x`, `y`, `r`, `needCar`, `onFoot`, `failInCar`, `text`, `done`. |
| `timer` | Starts a countdown with `t` seconds and `fail` text. |
| `wanted` | Sets the wanted level to `n` stars. |
| `lose` | Waits until the wanted level is gone. |
| `kill` | Spawns a fleeing car to wreck, with `x`, `y`, `car` and `color`. |
| `tramrace` | Sends the Glenelg tram off from Victoria Square as a rival. |
| `magpies` | Spawns `n` swooping magpies. |
