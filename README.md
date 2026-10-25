# Territory War

A real-time war game for four on your phone: hire troops one at a time, steer them yourself and paint the map in your colour. No install, no login.

**Play here:** https://woodmandk.github.io/Territory-war/

## How it works

Four armies, one map, a bit like Supremacy but much simpler. You and three bots each start with a headquarters (HQ) in a corner, 100 gold and no troops.

- **Hire** soldiers, tanks and planes with the buttons at the bottom. They are built in your HQ, or in a town you own if you tapped it. You can have at most 10 troops at once.
- **Tap a troop** to select it, then tap the map to send it there. Or **drag a route** with your finger, starting on the troop.
- Every troop has health. Ground you walk on becomes yours. Walk out and **back into your land** in a loop, and everything inside is filled in, paper.io style. Planes don't paint.
- **Towns** pay gold and can build troops. Park a soldier or tank in one to capture it.
- Enemy ground troops **can't walk through each other**, so fronts form where armies meet, drawn as a thick line between two countries. Land an enemy troop stands near can't be painted.
- Troops fire on their own. **Tanks** beat soldiers, **planes** beat tanks and **soldiers** shoot planes down. Forest gives cover. Rivers can only be crossed at the bridges.
- Your own land heals your troops. Destroy the other HQs, or own 70% of the land, to win.

The map is one quadrant mirrored four ways, so every corner is the same fight. Bots play by the same rules. Three difficulties.

## Tech

Everything is in `index.html`: plain JavaScript, no build step. The map is an 80×80 grid generated from noise. A WebGL shader draws it, blending the 3×3 cells around each pixel with a quadratic B-spline so borders, shores and forests are soft curves, with animated water and swaying trees (plus a plain canvas fallback if WebGL is missing or the GPU drops it). Units walk grid paths found by breadth-first search and straightened with line-of-sight checks. Each tick (10 per second) the game moves units, paints and fills land, resolves fire, captures towns, builds queued troops and pays out gold.

It is a PWA (`manifest.webmanifest` and `sw.js`), so it can be added to the home screen and played offline. The same files can later be wrapped as a store app with Capacitor.
