# Territory War

A real-time territory conquest game for your phone, in the spirit of territorial.io. No install, no login.

**Play here:** https://woodmandk.github.io/Territory-war/

## How it works

- Pick where your country starts on the map. Everyone starts equally small.
- Your troops grow all the time. More land gives more income and a higher troop cap.
- Pick an **attack strength** with the slider and tap free land or a neighbouring country. Your troops eat their way across the border, cell by cell, until they run out. Whatever is left comes home.
- Free land is cheap. Enemy land costs more the more troops the defender has per cell, and mountains cost double.
- When two countries attack each other at the same time, the attacks cancel out.
- You win when you hold 80% of the land or are the last country standing.

Pinch to zoom, drag to move the map. The bots come in three difficulties, and you choose how many of them (3 to 30) and how big the map is.

## Tech

Everything is in `index.html`: plain JavaScript and a 2D canvas, no build step. The map is a grid of cells generated from noise; each tick (10 per second) the game scans all borders, advances every attack along its front and pays out income.

It is a PWA (`manifest.webmanifest` and `sw.js`), so it can be added to the home screen and played offline. The same files can later be wrapped as a store app with Capacitor.
