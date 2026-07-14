Original prompt: at motino, add a spin motion.

Updates:
- Added a Spin motion control to the motion panel.
- Spin is a standing rotation with a small balance pose and is included in Auto Moves.
- Verified script parse, Playwright state checks, and screenshots.

TODO:
- None for the spin feature after verification.

Theme switch update (2026-07-14):
- Added Bright and Dark display controls; Bright remains the default/current appearance.
- Dark mode uses charcoal interface surfaces and light-gray canvas mesh/grid ink.
- Added theme state to `window.render_game_to_text` for automated verification.

TODO:
- None for the theme switch after desktop/mobile visual verification and console checks.

Crouch and squat update (2026-07-14):
- Added separate Crouch and Squat controls with smooth pose blending.
- Both poses keep the boot soles planted while lowering the pelvis and bending the knees.
- Added both actions to Auto Moves and exposed their state/blend values for testing.

TODO:
- None for crouch and squat after side-view pose checks, standing-transition verification, and a complete Auto Moves pass through both actions.

Squat hand posture fix (2026-07-14):
- Rotated each complete hand mesh around its wrist to continue the forearm direction.
- Kept the palm plane facing inward while correcting the downward-hanging squat fingers.

TODO:
- None for the squat hand fix after side/initial-view checks, standing transition verification, and running-pose regression testing.

Dark figure color update (2026-07-14):
- Changed the uncolored Dark-mode figure mesh from light gray to dark gray.
- Kept slightly lighter dark-gray topology caps and slightly deeper pelvis shading for readable depth.

TODO:
- None for the Dark figure color after normal/close zoom checks, Bright-mode comparison, and console verification.

Face rollback (2026-07-14):
- Removed the experimental anatomical facial mesh and its eye/mouth overlays.
- Restored the original closed ellipsoid head and standard neck connection.

TODO:
- None for the face rollback after Bright/Dark and Run Motion verification.
