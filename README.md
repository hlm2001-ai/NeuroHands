# NeuroHands — Learn AI by Doing

**NeuroHands** is a free, client-side interactive learning lab that teaches neural networks through real training, interactive neuron inspection, a 3D model, a step-by-step course, and hand gestures through your webcam.

## What's included

- 5 guided lessons: input neurons, hidden connections, model training, architecture experiments, and a knowledge check.
- A **real** 2 → N → 1 neural network implemented from scratch with a tanh hidden layer and a sigmoid output.
- Real gradient-based learning: **backpropagation with Adam optimization** and cross-entropy loss.
- XOR, OR and AND classification tasks, with a genuine prediction map, training-loss chart and accuracy updates.
- 3D visual network (Three.js), with mouse-based neuron selection and orbit-style dragging. A 2D fallback is available if the 3D CDN is unreachable.
- Optional camera-based gestures through Google's MediaPipe Hand Landmarker: pinch to select neurons, open palm for one second to begin training.
- English and Arabic (RTL) interface switch, responsive design, accessible buttons and local progress saved in `localStorage`.

## Free, easy publishing — GitHub Pages (no build required)

1. Sign in to your GitHub account and click **New repository**.
2. Repository name: `NeuroHands` (or another name). Choose **Public**, then **Create repository**.
3. Click **Add file → Upload files**. Upload `index.html`, `styles.css`, `app.js`, `.nojekyll`, and the folder `assets` (containing `favicon.svg`). If uploading folders isn't supported in your browser, create `assets/favicon.svg` from the GitHub file editor.
4. Click **Commit changes**.
5. Go to **Settings → Pages** in the repository.
6. Under **Build and deployment**, set **Source: Deploy from a branch** and choose **Branch: main / (root)**; click **Save**.
7. The URL will normally be `https://YOUR-USERNAME.github.io/NeuroHands/` (using the **exact capitalization** of the repository). GitHub Pages will show the actual address under Settings → Pages.
8. Open the published site through **HTTPS**, then choose **Enable Camera** and grant permission if you'd like to use gestures.

Since the project has no build system, you do not need to install Node, npm, Vite, React, or run a terminal command for publishing. Upload the files directly.

### Local testing

Double-clicking `index.html` may show the basic layout, but camera permissions and JavaScript modules work more reliably through a local server. If Python is installed, open a terminal in this folder:

```bash
python -m http.server 8080
```

Then visit <http://localhost:8080>.

## Privacy and usage

- The app has **no backend**, accounts, advertising, paid APIs, or API keys.
- Browser camera permission is **optional**; all lessons can be completed by mouse.
- Video frames and hand landmarks are processed in the browser via MediaPipe; they are not sent to an application server.
- Libraries, fonts and the pre-trained hand landmark model are downloaded from public CDN/model hosts when needed, which requires an internet connection. No app-controlled server receives camera frames.
- Camera access normally requires `localhost` or an HTTPS URL, along with user permission.
- `localStorage` only stores a 5-value lesson-completion list.
- The decision map displays the network's predictions for the XOR/AND/OR truth-table problem. The reported accuracy is **training accuracy on four examples**, not generalization accuracy on unseen datasets.
- The network animation is an explanatory visualization. It does not depict the exact numeric forward- or backward-pass computations in real time; the chart and predicted classes are computed using the actual network.

## Tech stack

Vanilla HTML, modern CSS, JavaScript, Three.js `0.187.0` (public CDN), Google MediaPipe Tasks Vision `0.10.22-rc.20250304` (public CDN + official model), Canvas 2D, GitHub Pages. The core teaching logic does not depend on either third-party library.

## Project structure

```text
NeuroHands/
├── index.html
├── styles.css
├── app.js
├── .nojekyll
├── assets/
│   └── favicon.svg
└── README.md
```

## Suggested portfolio description

> NeuroHands is a browser-based interactive AI education lab combining camera gesture recognition, 3D neural network visualization, and a fully functional trainable multilayer perceptron. I built a guided five-step learning experience, live training analytics, a customizable network architecture, and a bilingual UI — with no paid API and no backend.

---

**Note:** This is an educational demonstration, not a production ML training platform or an AI service. MediaPipe is used to detect hand landmarks; the neural network being taught is a separate model implemented in JavaScript.
