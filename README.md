HologramArcade - VisionLab
A browser-based, real-time demo that combines MediaPipe Hand Tracking with a Three.js overlay. 
It renders a mirrored webcam feed, draws 2D hand landmarks, and overlays an interactive neon 3D object that responds to simple gestures.

Prerequisites
A modern browser with camera support:

Chrome 89+, Edge 89+, Firefox 87+, Safari 14+ (desktop and mobile where supported)

A webcam (or device camera on mobile)

Basic static hosting if testing over HTTPS (recommended for camera permissions)

Note: Browsers typically require HTTPS to grant camera access. localhost is usually treated as secure.

Quick Start
Option A: Open directly (for quick testing)

Clone or download the repository.

Open the landing page (e.g., landing.html) in a modern browser.

Click “Start” to open the main demo page (e.g., index.html).

Allow camera permissions when prompted.

Option B: Serve locally (recommended)

Clone the repo.

Start a simple static server from the project root:

Python 3:

macOS/Linux: python3 -m http.server 8000

Windows: py -m http.server 8000

Node (http-server globally installed): npx http-server -p 8000

Open http://localhost:8000 in a browser.

Navigate to the landing page and press “Start”.

Local Development
Edit HTML/CSS/JS directly; the app uses CDN scripts for MediaPipe and Three.js.

Keep your edits incremental and reload the page to test.

For mobile testing, serve over LAN with HTTPS if possible, or use localhost tethering solutions.

Project Structure
Example structure (adapt to your filenames):

landing.html — Gamified histogram-themed front page (Start button)

index.html — Main demo (webcam + MediaPipe + Three.js)

assets/ — Optional directory for icons, fonts (if self-hosted), or future assets

README.md — This file

The main demo typically includes:

getUserMedia for webcam

MediaPipe Hands: model initialization and per-frame inference

Canvas overlay: 2D landmarks and skeleton

Three.js scene: transparent renderer, camera, object(s), animation loop

Gesture logic: pinch detection, proximity check, debouncing

Configuration
Landing page:

Ensure the Start button points to your main app:

For example, set data-href="/index.html" (and a small script that navigates window.location to this value on click)

If you use a different filename or path, update accordingly.

Main app:

Camera constraints can be tuned (e.g., 1280x720 for lower-end devices).

MediaPipe Hands options:

maxNumHands (default: 2)

modelComplexity (0–1; 1 is more accurate)

minDetectionConfidence (0–1)

minTrackingConfidence (0–1)

Gesture thresholds:

Pinch distance threshold (e.g., 0.05)

Debounce interval for color changes (e.g., 500 ms)

Three.js scene:

Geometry: BoxGeometry/SphereGeometry/etc.

Materials: solid + wireframe for visual clarity

Background alpha for overlay on webcam

Usage Tips
Good lighting improves detection accuracy.

Keep hands within the frame and avoid extreme angles.

For smoother movement, avoid rapid gestures; pinch, then move steadily.

If performance dips on mobile:

Lower modelComplexity

Reduce video resolution

Simplify Three.js geometry/materials

Troubleshooting
No camera prompt:

Ensure the page is served over HTTPS or on localhost

Check browser permissions and OS privacy settings

“No hands detected”:

Improve lighting, move closer, ensure hands are fully in frame

Refresh the page after granting permissions

Laggy or low FPS:

Reduce input video resolution (e.g., 640x480)

Lower modelComplexity in MediaPipe options

Close other heavy tabs or apps




Tech Stack :
MediaPipe
Three.js
AudioManager.js
SpeechManager.js



Verify the gesture thresholds (pinch distance)

Ensure the left/right hand roles match your expectations (mirrored view is intentional)
