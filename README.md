# NeuroHands V2 — Interactive AI Learning Lab

**NeuroHands** is a bilingual, free, static web app combining a trainable neural network, a visual neural graph, and webcam-based hand gestures. V2 makes hand actions **causally affect the model**, addressing V1's limited camera interaction.

## What changed in V2?

- **Pinch a blue Input neuron** to flip the live input value from `0` to `1` and back. A genuine feedforward pass immediately updates the live predicted class and `P(class 1)`.
- **Pinch a purple Hidden neuron** to mute/unmute it. This sets that neuron's hidden activation to zero for inference/evaluation, with real changes to predictions, loss and possibly accuracy. The node dims and its incoming/outgoing visual connections disappear in 3D.
- **Hold an open palm ~1 second** to train the network; it uses actual backpropagation and Adam, not simulated numbers.
- **Hold a fist ~1.5 seconds** to reset the network (gesture recognition may vary by device/lighting).
- **Point with index finger** to move a visible cursor. Near-neuron snapping highlights the current target and displays a contextual action label, rather than requiring a pixel-perfect pinch.
- Added a prominent **Live Prediction** bar showing inputs, neural prediction, predicted probability, expected answer, and whether the selected example is correct. Tappable `x1` and `x2` values work without a camera.
- Added a **three-stage interactive mission coach**: flip an input → train the model → mute a hidden neuron. Guidance is Arabic/English, and existing lessons now lead with these actions.
- Clearer model reset and V2 lesson-progress storage; V2 CSS/JS links include a version query to avoid browser cache after updating.

## The real learning model

- Two binary inputs, configurable hidden layer (2–8 units, tanh activation), one sigmoid output.
- Trainable neural network entirely in JavaScript; **cross-entropy**, backpropagation, **Adam** optimizer.
- XOR, AND, and OR datasets (four training examples each) with learning curves and a decision heatmap.
- The training accuracy reflects the **four examples used for training**, not unseen generalization data. Switching the currently inspected input doesn't inherently change this aggregate accuracy; the **live prediction and P(1)** reflect the selected input pair.
- Muting a neuron affects inference immediately. Starting training restores all muted nodes first, avoiding confusing mixed training/muting behavior.

## Play it

1. Open the deployed site on HTTPS and choose **Enable Camera**.
2. Move your index fingertip so that the cursor over the *big neural diagram* lands on a **blue input node**; watch that node glow brighter.
3. **Pinch thumb + index finger**, then release: the input changes between 0 and 1, updating the real prediction in the strip below the diagram.
4. **Open your palm for ~1 second**: the model trains; monitor loss and accuracy.
5. **Pinch a purple hidden neuron**: mute it and compare the new predicted probability and loss. Pinch again to restore.
6. **Hold a closed fist for ~1.5 seconds**: reset. Repeat or try the other training datasets.

Mouse/touch alternatives are supported: click input/hidden nodes in the graph, click `x1`/`x2` value buttons, and use Start Training / Reset.

## Updating an existing GitHub Pages site

1. Extract the release ZIP.
2. In your *existing* GitHub repository, upload the new `index.html`, `styles.css`, `app.js`, and `README.md` over the old files, keeping everything in the repository root. If GitHub's upload UI rejects same-name files, delete the previous version of the specific file and upload its replacement.
3. Commit the changes. You don't need to create a new repository or reconfigure Pages.
4. Reload your current published site. The sidebar footer should display `V2.0`.

If publishing for the first time, use GitHub → New repository → Public → Upload the extracted project files to the repository root → Settings → Pages → `Deploy from branch` → `main` + `/(root)`.

## Implementation and caveats

- HTML/CSS, JavaScript, Three.js (with 2D fallback), MediaPipe Tasks Vision, Canvas.
- No app backend, no accounts, no paid API, no camera upload; MediaPipe downloads model/library assets over the internet.
- Camera use requires a secure HTTPS origin or localhost and browser permission. Gesture recognition depends on the camera, lighting, distance and hand pose. There is an equivalent mouse/touch interaction for accessibility and troubleshooting.
- Automated browser smoke tests covered clicking input values and hidden neurons, model convergence, language switch, reset and basic responsive layout. **Real hand tracking was not physically tested on a camera in this environment**; confirm on your device.
- Dynamic neuron glow, line pulses and highlights explain the learning process visually but are not a step-for-step simulation of every exact backpropagation operation.

## Files

```text
NeuroHands/
├── index.html
├── styles.css
├── app.js
├── assets/favicon.svg
├── .nojekyll
├── README.md
└── ابدئي_من_هنا.md
```
