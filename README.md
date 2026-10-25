# Territory War

A real-time territory conquest game for your phone, in the spirit of territorial.io and OpenFront. No install, no login.

**Play here:** https://woodmandk.github.io/Territory-war/

## How it works

A real-time Risk with a bit of Supremacy on top. There is no click-to-attack: you move armies between provinces.

- The map is cut into **provinces**, each with a town holding a garrison that grows all the time. Cities (♜) and your capital (★) grow faster.
- **Drag** from one of your provinces to another to send troops (or tap yours, then the target). The **Send** slider sets the share that goes. Armies march town to town.
- When an army reaches a province that is not yours, a **battle** runs in real time until one side is gone. Mountains, forest, towns and **forts** help the defender. You can feed more troops into a running battle.
- The first 60 seconds are a **truce**: everyone can only take free provinces.
- Under **Army** (Hær) you buy **tanks** (count as 8 soldiers in attack and march faster) and **planes** (bomb a province from afar and fly home) for gold.
- Dotted **sea lanes** join islands and coasts; armies sail across them.
- **Encirclement**: cut off part of a country and it surrenders, and its garrison joins you. **Fog of war**: you only see near your own borders and armies.
- Hold your finger on your land to build **cities**, **forts** and **missile silos** with nukes. Hold on another country to propose an **alliance**.
- You win with 70% of the land or as the last country standing.

Bots play by the same rules: they recruit, march, sail, ally and nuke. Choose 3 to 30 bots, three difficulties, a continent or archipelago map and three sizes.

## Tech

Everything is in `index.html`: plain JavaScript, no build step. The map is a grid of cells generated from noise. The land is split into provinces grown from scattered seeds. A WebGL shader draws it, blending a 4×4 block of cells around each pixel with a cubic B-spline so borders and coasts are soft curves, with animated waves, swaying forests, drifting cloud shadows and fog of war (plus a plain canvas fallback). Each tick (10 per second) the game grows garrisons, moves armies and planes, resolves battles, checks encirclements and pays out gold.

It is a PWA (`manifest.webmanifest` and `sw.js`), so it can be added to the home screen and played offline. The same files can later be wrapped as a store app with Capacitor.
