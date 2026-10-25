# Territory War

A real-time territory conquest game for your phone, in the spirit of territorial.io and OpenFront. No install, no login.

**Play here:** https://woodmandk.github.io/Territory-war/

## How it works

- Pick where your country starts. The first 30 seconds are a **truce**: everyone can only take free land, so new players get a fair start.
- Pick an **attack strength** with the slider and tap free land or a neighbouring country. Your troops eat their way across the border, cell by cell, until they run out. Whatever is left comes home. A badge on each front shows how many troops are still marching.
- Free land is cheap. Enemy land costs more the more troops the defender has per cell, and mountains cost double.
- When two countries attack each other at the same time, the attacks cancel out.
- Land gives troops and **gold**. Spend gold on:
  - **City**: higher troop cap, faster growth, more gold.
  - **Fort**: enemies pay 2.5× for your land inside its ring.
  - **Port**: send boats across the sea. Boats land on the nearest shore and fight their way inland. Ports also give gold.
  - **Missile silo** and **nukes**: wipe out everything in a large area. Expensive on purpose, so the endgame doesn't turn into nuke spam.
- Hold your finger on a country to see it, propose an **alliance**, attack it or send a boat. Hold on your own land to build right there.
- You win when you hold 80% of the land or are the last country standing.

Pinch to zoom, drag to move. Choose 3 to 30 bots, three difficulties, a **continent** or an **archipelago** map (where you need ports to reach anyone), and three map sizes. The bots build, sail, ally and fire nukes too (except on Easy).

## Tech

Everything is in `index.html`: plain JavaScript and a 2D canvas, no build step. The map is a grid of cells generated from noise; each tick (10 per second) the game scans all borders, advances every attack along its front, moves boats and missiles, and pays out troops and gold.

It is a PWA (`manifest.webmanifest` and `sw.js`), so it can be added to the home screen and played offline. The same files can later be wrapped as a store app with Capacitor.
