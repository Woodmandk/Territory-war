# Territory War

A real-time war game for four on your phone: hire troops one at a time, steer them yourself and paint the map in your colour. No install, no login.

**Play here:** https://woodmandk.github.io/Territory-war/

## Play online with friends

Tap **Spil online med venner**, create a room and share the link (or the five-letter code). Up to four people on one map; empty seats are bots. The host's phone runs the game and sends everyone else what happens; friends only send their orders. Phones find each other through the free PeerJS matchmaking server and then talk directly (WebRTC), so there is no server or account of our own. The host has to keep the game open until the match is over. If a friend drops out, a bot takes over their army.

## How it works

Four armies, one map, a bit like Supremacy but much simpler. You and three bots each start with a headquarters (HQ) in a corner, 100 gold and no troops.

- **Hire** troops: soldiers and tanks from the start; artillery, rocket launchers, anti-air, special forces, heavy tanks, planes and bombers once researched with the buttons at the bottom. They are built in your HQ, or in a town you own if you tapped it. You can have at most 10 troops at once.
- Counters: tanks beat soldiers, planes beat tanks and artillery, artillery shells into the neighbouring province, rocket launchers reach even further, bombers flatten tanks and HQs, anti-air shoots planes down.
- **Research tree** (flask button, top bar), three tabs: *Troops* (unlock artillery, anti-air, planes, then special forces, heavy tanks, rocket launchers and bombers, some needing other research first), *Upgrades* (each troop type three levels, +15% health and damage, existing troops too) and *Realm* (taxes, field hospital, radar, logistics, fortification, occupation). One project at a time; each takes 20-40 seconds. Bots research too.
- Sound effects (synthesized, can be turned off in the pause menu), explosions with sparks and smoke, and an end screen with stats and a graph of everyone's land over time.
- **Tap a troop** to select it, then **tap a province**: the troop finds its own way to the middle of it. **Vælg alle** sends the whole army.
- The map is cut into **provinces**, like Supremacy. Every troop has health. Park a soldier or tank in a province with no enemies in it, and it turns yours after a few seconds. Planes can't take land.
- Every province pays gold. Provinces with a **town** pay more and can build troops.
- Enemy ground troops **can't walk through each other**, so the front is wherever the armies meet, drawn as a thick line between two countries. A province with enemy troops in it can't be taken.
- Troops fire on their own. **Tanks** beat soldiers, **planes** beat tanks and **soldiers** shoot planes down. Forest gives cover. Rivers can only be crossed at the bridges.
- Ground troops cannot walk through enemy land: they must **capture an enemy province** before moving on into the next one. Towns and provinces with buildings take much longer to capture.
- Troops in enemy fire slow to a crawl and cannot push closer than their own range, so they cannot just run past an enemy army.
- **Stacks and roads, like Supremacy**: troops standing together form a stack, drawn as one token with a count; a tap picks the whole stack and the type chips split it. Provinces are linked by a road network, and ground troops march along the roads (a stack at the pace of its slowest troop); planes fly straight.
- Tap a troop to select just that one; tap it again to drop it. Hold your finger on more troops to add them. After you send troops to a province the selection is cleared. Chips above the buy buttons keep one type or clear the selection. Selected troops show their firing range.
- Fog of war is visible: land outside your territory and your troops' sight is darkened. Artillery sees a bit past its firing range.
- Tap one of your provinces to **build** there: a fort (shoots and makes the province slow to take), a factory (builds troops) or a market (more gold). Tap your **HQ** to expand it so you can field more troops (10, 13, 16, 19).
- Your own land heals your troops. Destroy the other HQs, or own 70% of the land, to win.

The map is one quadrant mirrored four ways, so every corner is the same fight. Bots play by the same rules. They pick fights with their nearest, weakest neighbour and avoid ganging up on one player. Three difficulties.

## Tech

Everything is in `index.html`: plain JavaScript, no build step. The map is an 80×80 grid generated from noise, cut into provinces grown from scattered seeds. A WebGL shader draws it, blending the 3×3 cells around each pixel with a quadratic B-spline so borders, shores and forests are soft curves, with animated water and swaying trees (plus a plain canvas fallback if WebGL is missing or the GPU drops it). Units walk grid paths found by breadth-first search and straightened with line-of-sight checks. Each tick (10 per second) the game moves units, resolves fire, captures provinces, builds queued troops and pays out gold.

It is a PWA (`manifest.webmanifest` and `sw.js`), so it can be added to the home screen and played offline. The same files can later be wrapped as a store app with Capacitor.
