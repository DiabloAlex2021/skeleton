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

Initial view framing update (2026-07-19):
- Increased Initial view zoom and shifted the camera framing upward to match the supplied full-body reference.
- Kept the existing three-quarter Initial rotation and left Front, Side, and Top presets unchanged.

TODO:
- None for the Initial preset after portrait framing and Front-to-Initial reset verification.

Initial view angle update (2026-07-19):
- Changed the Initial camera angle to the supplied near-level three-quarter view (X 0.005, Y -0.686 radians).
- Matched the reference framing with a 0.84 zoom and a small downward offset.

TODO:
- None after matching the desktop render to the reference and verifying the Front-to-Initial reset with no console errors.

Webcam facial mapping update (2026-07-20):
- Added a Track Face webcam toggle backed by MediaPipe FaceMesh.
- Smoothed live eye, brow, nose, lip, iris, and face-oval landmarks are projected onto the front ellipsoid surface of the figure head.
- The tracked overlay fades out when the figure turns away, leaving the original back-of-head topology unchanged.
- Added explicit camera cleanup and face-tracking state to render_game_to_text.

TODO:
- None after verifying the unavailable-camera retry state, synthetic live landmark render, front/back visibility, toggle cleanup, and console output.

Tracked head roll update (2026-07-20):
- Added real-time head roll from the tracked eye-line angle.
- Facial landmarks are de-rolled before projection, then the original head mesh and mapped face share the same clockwise/counterclockwise rotation around the neck.
- Roll returns smoothly to neutral when tracking stops or the face is lost.

TODO:
- None after verifying +20° clockwise, -20° counterclockwise, rear topology, neutral reset, and console output.

Tracked face base-mesh visibility update (2026-07-20):
- The original black head points and head-to-head links are now fully omitted while the live tracked face overlay is visible.
- The original head mesh returns automatically when tracking is stopped or the figure rotates away from the front.

TODO:
- None after verifying the clean tracked-face view, webcam-off restoration, 180-degree rear topology, and console output.

Dense tracked-face mesh update (2026-07-20):
- Added the full MediaPipe facial tessellation beneath the stronger eye, brow, nose, lip, iris, and oval contours.
- While the tracked face is visible, all original head points and every link connected to the original head are omitted.
- The tessellation connection count is exposed in render_game_to_text for verification.

TODO:
- None after verifying the 2,556-link MediaPipe tessellation, complete base-head removal, webcam-off restoration, 180-degree rear topology, and console output.

Procedural full-head mapping update (2026-07-20):
- Face width, face height, and jaw landmarks now drive smoothed head width, height, jaw taper, and an anatomically constrained cranial-depth estimate.
- Added a complete triangulated head-shell mesh that rotates with the tracked head and remains mapped through front, side, and rear views.
- The original head stays hidden for the full tracking session and returns when the face is lost or tracking stops.
- Added full-head activity, shell connection count, and estimated head-shape values to render_game_to_text.

TODO:
- None after verifying square/wide and tall/narrow shape adaptation, front/side/rear shell rendering, tracking-off restoration, and console output.

Procedural full-head mapping rollback (2026-07-20):
- Removed the inferred cranial shell and face-proportion head reconstruction at the user's request because it was simulated geometry rather than tracked webcam data.
- Restored the prior dense front-face MediaPipe tessellation behavior; side/back views and tracking-off use the original head mesh again.

TODO:
- None after verifying dense front-face mapping, original 180-degree rear head restoration, tracking-off restoration, and console output.

Tracked nose contour adjustment (2026-07-20):
- Removed the emphasized nose bridge, nostril, nose-to-mouth contour paths, and nose-tip marker.
- Kept the fine MediaPipe tessellation across the nose so tracking detail remains without a bold nose line.

TODO:
- None after verifying the close-up tracked face, webcam-off restoration, 180-degree rear restoration, and console output.

Tracked face color update (2026-07-20):
- Changed the live face tessellation, emphasized contours, and iris markers from teal to black.

TODO:
- None after verifying the black close-up face mesh, tracking-off restoration, 180-degree rear restoration, and console output.

Tracked outer-contour visibility update (2026-07-20):
- Temporarily disabled the emphasized outer face-oval contour while retaining the fine black tessellation boundary.
- Kept the outer contour definition behind SHOW_TRACKED_FACE_OUTER_CONTOUR so it can be restored by changing one flag.

TODO:
- None after verifying the close-up face without the thick outer contour, tracking-off restoration, 180-degree rear restoration, and console output.

Camera-toggle layout update (2026-07-20):
- Moved the Track Face webcam control out of the left motion panel and placed it as a full-width row directly below the Bright/Dark switcher.
- Preserved all existing tracking states, status labels, and error styling.

TODO:
- None after verifying desktop/mobile placement, Bright/Dark switching, active camera-toggle behavior, tracking cleanup, and console output.

Mesh-color menu and Dark face-color update (2026-07-20):
- Added an accessible Collapse/Expand button for the Mesh Color list while leaving Zoom and Motion controls available.
- Added meshColorMenuExpanded to render_game_to_text for state verification.
- Changed tracked face tessellation, contours, and iris markers to white in Dark mode while retaining black in Bright mode.

TODO:
- None after verifying expand/collapse behavior, color controls after re-expansion, responsive layout, black Bright-mode and white Dark-mode tracked faces, and console output.

Dark blue mesh palette update (2026-07-20):
- Changed the uncolored Dark-mode figure mesh to muted steel blue (#6F86A6), with lighter blue highlights and deeper blue shadows.
- Changed the Dark-mode tracked face tessellation, contours, and iris markers to ice blue (#9DD7FF).
- Bright-mode figure and tracked-face colors remain unchanged.

TODO:
- None after verifying Dark-mode body/face contrast, ice-blue tracked-face visibility, unchanged Bright mode, tracking-off/rear restoration, and console output.

Mesh-color default-collapse update (2026-07-20):
- Changed the Mesh Color list to start collapsed, with matching hidden markup, Expand label, ARIA state, and render_game_to_text state from the first frame.

TODO:
- None after verifying initial collapsed rendering without flash, expansion/re-collapse behavior, responsive layout, color controls after expansion, and console output.

Webcam upper-body gesture tracking (2026-07-20):
- Added MediaPipe Pose and Hands to the existing webcam lifecycle alongside FaceMesh.
- Mapped shoulder/elbow/wrist directions onto both figure arms with fixed anatomical lengths and temporal smoothing.
- Added tracked hand geometry driven by all 21 hand landmarks so the palm, thumb, and individual finger joints follow live gestures.
- Added short loss timeouts that restore the original arm/hand pose when landmarks leave the camera view.
- Renamed the shared control to Track Camera and exposed deterministic upper-body test hooks/state for local verification.

TODO:
- None after verifying synthetic two-arm/two-hand gestures, independent limb-loss restoration, complete tracking reset, MediaPipe Pose/Hands constructor loading, screenshots, and zero browser console errors.

Camera pipeline reliability fix (2026-07-20):
- Diagnosed the permanent Finding Body state as a runtime pipeline problem: three classic MediaPipe WebAssembly graphs were loaded and sent concurrently, while processing exceptions were silently discarded.
- Changed script loading and live inference to serialized round-robin processing so FaceMesh, Pose, and Hands never initialize or process the same video frame concurrently.
- Added per-model failure counters and visible retry/error state instead of leaving the UI indefinitely on Finding Body.
- Counted detected hands as active tracking even if Pose temporarily cannot see the shoulders.
- Added pipeline diagnostics to render_game_to_text.

TODO:
- None after verifying exact Face→Pose→Hands round-robin progression with maximum one active graph, four-failure escalation, tracked/restored arm and finger geometry, screenshots, syntax, and zero browser console errors.

Tracked face-to-neck gap adjustment (2026-07-20):
- Extended only the lower tracked-face region toward the neck by 0.055 figure units, with a smooth blend beginning below the mid-face.
- Kept the forehead, eyes, and upper-face placement unchanged while bringing the chin into a slight overlap with the neck top.
- Exposed the chin-drop value in render_game_to_text for regression checks.

TODO:
- None after verifying close-up tracked face/neck contact, unchanged tracking-off head/neck, front-camera rendering, syntax, and zero browser console errors.

Tracked jaw-to-neck transition buffer (2026-07-20):
- Added a three-row tapered wireframe transition derived from the tracked lower-jaw landmarks.
- Blended the moving jaw into the fixed front neck surface with light horizontal, vertical, and alternating diagonal connections.
- Kept the transition face-tracking-only and exposed its row/connection counts in render_game_to_text.

TODO:
- None after verifying the 160-connection transition band at close range, tracking-off removal, Bright/Dark colors, front-camera rendering, syntax, and zero browser console errors.

Arm, hand, and finger tracking buffers (2026-07-20):
- Added independent acquisition/release blends for both tracked arms and both hands.
- Arms now interpolate between the active animation/rest pose and webcam shoulder-elbow-wrist targets instead of snapping.
- Hands and all finger joints now interpolate from a neutral anatomical hand skeleton into the tracked 21-landmark gesture.
- Retained the last good pose briefly during landmark loss, then eased back before clearing it; camera-off uses the same buffered release.
- Exposed the four transition blend values in render_game_to_text.

TODO:
- None after verifying partial acquisition blends, full tracked stabilization, independent left-arm loss, retained hand landmarks during release, complete buffered cleanup, camera-off easing, screenshots, syntax, and zero browser console errors.

Arm/hand/finger buffer rollback (2026-07-20):
- Removed the latest acquisition/release blends and neutral-hand interpolation at the user's request.
- Restored the immediately responsive tracked arm targets, direct 21-landmark hand geometry, original short loss timeouts, and immediate camera-off restoration.
- Preserved the separate face-to-neck transition buffer and camera pipeline reliability fixes.

TODO:
- None after verifying restored tracked gesture geometry, immediate one-side/camera cleanup, preserved 160-connection face-to-neck buffer, screenshots, syntax, and zero browser console errors.

Learning Mode session recording and playback (2026-07-20):
- Added a bottom-right Learning Mode panel with a Start / Stop & Save recording toggle and a dedicated Stop Playing control.
- Recorded compact, timestamped JSON frames at 8 Hz from the tracked facial mesh, upper-body pose, and both 21-point hands.
- Reserved lower-body fields as `"N/A"` at both session and frame level for future tracking support.
- Persisted sessions in IndexedDB, listed them in the panel, and added JSON export and figure playback actions.
- Playback stops the live camera first, maps saved face/arms/hands onto the figure, follows saved timestamps, and supports manual or automatic stopping.
- Exposed learning-mode state through `render_game_to_text` and local deterministic test state.

TODO:
- None after verifying 478 face points, 17 upper-body pose points, 21 points per hand, JSON export, IndexedDB reload persistence, playback/stop cleanup, screenshots, syntax, and zero browser console errors.

Saved facial-mesh playback fix (2026-07-20):
- Fixed saved-session playback after a page reload rendering only eyes and lips while the base head was hidden.
- Playback now loads the MediaPipe face tessellation definition without opening the webcam or requesting camera permission before mapping facial frames.
- Added a cancellable Preparing state so the original head remains intact if the mesh definition cannot load.

TODO:
- None after verifying fresh-reload playback with all 2,556 tessellation connections, 478 saved landmarks, stop cleanup, screenshots, syntax, and zero browser console errors.

Contour-grown real-time back-head shell (2026-07-21):
- Replaced rear-view fallback to the original base head with a live procedural shell grown directly from the tracked 36-point face oval.
- Ring zero matches the tracked facial boundary exactly; nine posterior rings follow asymmetric cubic Bezier curves that briefly widen the upper cranium, taper the lower head, and lift into a computed rear pole/nape.
- Added 936 depth-sorted wireframe connections so the generated shell remains readable in front, side, rear, Bright, and Dark views.
- Kept the original head hidden for the entire tracked session and restored it immediately when live or saved facial tracking stops.
- Exposed shell activity, ring count, connection count, and computed depth in `render_game_to_text`.

TODO:
- None after verifying live synthetic contour growth, side/rear continuity, saved-session playback regression, Dark mode, camera-off restoration, screenshots, syntax, and zero browser console errors.

Last-face hold during camera loss (2026-07-21):
- Changed temporary face-loss behavior so Track Camera preserves the last valid 478 facial landmarks instead of removing the mapped head after 280 ms.
- Added an internal holding state while the camera continues searching; returning face data resumes normal smoothed tracking immediately.
- Preserved the last face roll, 2,556-point tessellation topology, jaw-to-neck buffer, and 936-connection contour-grown back-head shell until the camera is explicitly stopped.
- Added holding state diagnostics to `render_game_to_text` and deterministic local loss/resume test hooks.

TODO:
- None after verifying a simulated 10-second face absence, exact landmark-signature retention, active shell retention, resumed tracking, explicit camera-off cleanup, screenshots, syntax, and zero browser console errors.

Held-face side seam completion (2026-07-21):
- Fixed the half-head/cutaway appearance that remained when a held facial mesh was viewed near the side.
- Separated front-feature opacity from facial-surface opacity so the tracked 3D tessellation remains as a restrained cap through three-quarter and side angles without showing bold eyes, lips, or nose contours edge-on.
- Faded only the contour-plane ring of the generated rear shell as it turns away while retaining the curved Bezier bridge rings and rear cranium.
- Added foreshortening-aware facial-mesh opacity and line width so the side cap closes the head without becoming a solid black band.
- Added `surfaceVisible` diagnostics while preserving the existing `frontVisible` meaning.

TODO:
- None after verifying held Initial, Front, Side, Rear, and Dark views, exact landmark retention, live resume, camera-off restoration, screenshots, syntax, and zero browser console errors.

Licensed scan rear-head topology integration (2026-07-21):
- Replaced the nine-ring procedural Bezier rear shell with geometry derived from the Lee Perry-Smith `Infinite` 3D head scan supplied in `human-face-mesh-threejs`.
- Cropped the donor shoulders and donor neck before simplification, leaving 495 anatomical head vertices and 1,422 unique scan-topology connections for the crown, temples, ears, occiput, and nape.
- Fitted the scan's open front boundary to the live 36-point MediaPipe face oval with a depth-decaying deformation, preserving the scanned rear anatomy instead of adding the untouched stock model behind the face.
- Kept the existing live face tessellation, head roll, last-face hold, original figure neck, camera-off restoration, and saved-session playback behavior.
- Added visible Lee Perry-Smith / CC BY 3.0 attribution, a bundled license notice, and topology source/vertex/license diagnostics in `render_game_to_text`.

TODO:
- None after verifying 495 scan vertices / 1,422 connections in Front, Initial, Side, Rear, and Dark views; exact 10-second face-loss hold; camera-off base-head restoration; saved JSON playback/reload; and zero browser console errors.

Rear-head credit label visibility update (2026-07-21):
- Removed the visible Lee Perry-Smith rear-head attribution label from the left control panel at the user's request.
- Retained the bundled CC BY 3.0 license notice and scan source/license diagnostics in the code.

TODO:
- None after verifying the control panel ends cleanly after Auto Moves with no empty attribution spacing, attribution nodes, or console errors.

Camera capture front-view update (2026-07-21):
- Successful webcam capture now automatically selects the Front camera preset before tracking frames begin.
- The deterministic local tracking hook follows the same transition for regression testing.
- Stopping camera capture leaves the user in Front view; it does not unexpectedly return to the previous angle.

TODO:
- None after verifying Side → camera-on switches to Front, the Front button/readout/render state agree, camera-off remains Front, and the successful-start placement leaves failed capture unchanged.

Tracked head posture attachment fix (2026-07-21):
- Fixed the live/scanned head floating above the neck during Crouch, Squat, Jump, and leaning gait motions.
- Cached the exact body lean and vertical posture transform applied to the generated figure, then applied it to virtual tracked-face vertices and the jaw-to-neck bridge anchors.
- Preserved local head roll before applying the shared body posture so facial tilt remains centered on the head while the entire head follows the torso.
- Confirmed saved-session playback and reload still render the complete 2,556-connection face mesh attached to the neck.

TODO:
- None after visually verifying standing, full Crouch, full Squat, airborne Jump, Run lean, and camera-off restoration with continuous face/neck attachment and zero browser errors.

GitHub Pages deployment correction (2026-07-21):
- Added build ID `20260721-head-attachment` to the page metadata and deterministic render-state diagnostics.
- Added a versioned entry redirect so browsers do not reuse the pre-fix figure document after deployment.
- Kept the verified camera-on Front preset and shared body/head posture transform unchanged.

TODO:
- None after independently deploying `gh-pages` and confirming the live HTML reports the build ID, camera-on Front transition, and shared head/body posture transform.

Dark reference-cyan mesh update (2026-07-21):
- Matched the supplied wireframe reference's source cyan exactly at `#60E6D2`.
- Applied the same default Dark-mode ink to the base figure, tracked facial tessellation, facial features, rear-head scan shell, and jaw-to-neck bridge.
- Preserved explicit per-part colors selected from the mesh color menu.
- Updated the deployed build/cache ID to `20260721-cyan-dark-mesh` so GitHub Pages and browsers load the new color immediately.

TODO:
- None after inspecting the Dark base figure and tracked synthetic face/rear-shell render, confirming exact `#60E6D2` output pixels, checking the unchanged Bright render, and finding zero browser console errors.
