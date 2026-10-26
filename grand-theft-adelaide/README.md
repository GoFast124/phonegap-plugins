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

The world is "Light City", a GTA-style take on greater Adelaide traced from a fan-made map. It covers:

- **Light City:** the CBD's real street grid, Rundle Mall (with the Mall's Balls), North Tce, Adelaide Oval and the parklands.
- **North:** Old Port, the Barnacle Bay submarine base, Holdentown, Glasgow Military Base, Eucalyptus Plaza (via the J O Bahn) and Folly's End.
- **Coast:** Proclamation Bay with its jetty and the tram, the airport, Marketgrounds, and the De Tracht River.
- **Hills and wine country:** Mount Haughty, Bel Air Hills, Ironfold Wines, Vallei van Lof, New Hamburg and the Sluray River.
- **South:** Shiraz, Victory Harbour with the causeway to the Isle of Penguins, and the Bordeaux Peninsula.
- **Wallaby Island:** reached by the ferry at the end of Cape Rd.

Main roads follow the map: Main North Rd, Port Rd, Anzac Hwy, South Rd, the South Eastern Fwy, the Hills Loop and more. Traffic follows the road network, including curves and diagonals.

## Missions

| Mission | Where it starts |
| --- | --- |
| Where'd You Go To School? | Railway Station, North Tce |
| Iced Coffee Run | Old Port docks |
| Pie Floater | Adelaide Oval |
| Showdown | Hindley St |
| The Mall's Balls | Rundle Mall |
| Swooping Season | Victoria Square |
| Beat the Tram | Victoria Square tram stop |
| Adelaide 500 | East Tce |
| Kitchener Buns to Haughty | Central Market |
| Ironfold Grange | Ironfold Wines |
| Roo Island Run | Victory Harbour |

## Adding a mission

Missions are data in the `MISSIONS` array in `index.html`. Coordinates are map tiles: the map is 864×856 tiles, and the CBD runs from about x 418–510, y 340–412. Press M in game to see the map. Marker positions are snapped to the nearest footpath or road when the game loads. Each step has one of these types:

| Step type | What it does |
| --- | --- |
| `getcar` | Waits until the player is in a car. |
| `goto` | Reach a point. Options: `x`, `y`, `r`, `needCar`, `onFoot`, `failInCar`, `text`, `done`. |
| `timer` | Starts a countdown with `t` seconds and `fail` text. |
| `wanted` | Sets the wanted level to `n` stars. |
| `lose` | Waits until the wanted level is gone. |
| `kill` | Spawns a fleeing car to wreck, with `x`, `y`, `car` and `color`. |
| `tramrace` | Sends the tram from Victoria Square to Proclamation Bay as a rival. |
| `magpies` | Spawns `n` swooping magpies. |
