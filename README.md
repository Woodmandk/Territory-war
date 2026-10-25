# Territory War

A real-time territory conquest game for your phone, in the spirit of territorial.io and OpenFront. No install, no login.

**Play here:** https://woodmandk.github.io/Territory-war/

## How it works

Only your **troops** take land. There is no click-to-attack: you command armies, a bit like a much simpler Supremacy.

- Pick where your country starts. The first 30 seconds are a **truce**: everyone can only take free land.
- You start without an army. Tap **Army** (Hær) to hire **infantry**; the **Unit** slider sets how much of your reserve goes with it.
- **Drag** a unit where it should go (or tap it, then tap the target). It takes the land on its way and fights the enemies it meets. Free land costs nothing; enemy land costs troops.
- Turn on **Auto** and your troops march to the border by themselves, hold it and strike back at enemies who come close. A unit you move yourself leaves auto (its A badge disappears).
- **Encirclement**: cut off part of an enemy and the pocket surrenders. You get the land, gold and prisoners. Cut-off troops without supply grow weaker, and troops hit from several sides take more damage.
- **Forests** and **mountains** slow attackers and help defenders. **Fog of war**: you only see a little past your borders and around your troops (can be switched off in the menu).
- Under **Army** you can also hire **tanks** (fast, hard-hitting) and **aircraft** (fly over water and bomb) with gold.
- Land gives **gold** for cities (more troops), forts, ports (drag troops across the water and they sail), and missile silos with nukes.
- Hold your finger on a country to propose an **alliance** or ship an army there. Hold on your own land to build right there.
- You win with 70% of the land or as the last country standing.

Bots play by the same rules: they recruit, march, sail, ally and nuke. Choose 3 to 30 bots, three difficulties, a continent or archipelago map and three sizes.

## Tech

Everything is in `index.html`: plain JavaScript, no build step. The map is a grid of cells generated from noise. A WebGL shader draws it, blending a 4×4 block of cells around each pixel with a cubic B-spline so borders and coasts are soft curves, with animated waves, swaying forests, drifting cloud shadows and fog of war (plus a plain canvas fallback). Each tick (10 per second) the game moves armies, resolves fights and sieges, checks encirclements, moves boats and missiles, and pays out troops and gold.

It is a PWA (`manifest.webmanifest` and `sw.js`), so it can be added to the home screen and played offline. The same files can later be wrapped as a store app with Capacitor.
