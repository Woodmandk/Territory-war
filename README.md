# Territory War

A real-time territory conquest game for your phone, in the spirit of territorial.io and OpenFront. No install, no login.

**Play here:** https://woodmandk.github.io/Territory-war/

## How it works

Only your **troops** take land. There is no click-to-attack: you command armies.

- Pick where your country starts. You begin with one infantry unit. The first 30 seconds are a **truce**: everyone can only take free land.
- **Drag** a unit to where it should go (or tap it, then tap the target). An army on the move pushes the whole front around it and takes a wide, round bite of land; bigger armies hold a wider front. Countries always stay in one piece.
- Your reserve grows all the time. Tap **Army** (Hær) to turn it into **infantry** (tough on defence), **tanks** (fast, hard-hitting) or **aircraft** (fly over water and bomb). The slider sets how big the new unit is. You can also reinforce a selected unit standing on your land.
- Units that meet fight. Units standing on your own land make it hard to take. Mountains and forts cost attackers extra.
- **Encirclement**: free land that only you touch becomes yours, and a cut-off pocket of an enemy surrounded only by you surrenders.
- Land gives **gold** for cities (more troops, and new units muster there), forts, ports (drag a unit across the water and it sails), and missile silos with nukes.
- Hold your finger on a country to propose an **alliance** or ship an army there. Hold on your own land to build right there.
- You win with 70% of the land or as the last country standing.

Bots play by the same rules: they recruit, march, sail, ally and nuke. Choose 3 to 30 bots, three difficulties, a continent or archipelago map and three sizes.

## Tech

Everything is in `index.html`: plain JavaScript, no build step. The map is a grid of cells generated from noise. A WebGL shader draws it, blending each pixel's neighbouring cells with a smooth kernel so borders and coasts are soft curves (with a plain canvas fallback). Each tick (10 per second) the game moves armies, resolves fights and sieges, checks encirclements, moves boats and missiles, and pays out troops and gold.

It is a PWA (`manifest.webmanifest` and `sw.js`), so it can be added to the home screen and played offline. The same files can later be wrapped as a store app with Capacitor.
