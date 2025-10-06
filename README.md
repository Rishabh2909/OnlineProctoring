

# Headings (quick nav)

- **About**
- **Features**
- **Quick start (Windows PowerShell)**
- **Scripts (short guide)**
- **Models and where to place them**
- **Dependencies**
- **Commands (quick reference)**
- **Troubleshooting**
- **Contributing**
- **License & notes**

---

## About

**OnlineProctoring** is a set of small Python scripts and pretrained models to prototype local **online proctoring** features. It contains demos for **face detection**, **landmark-based analysis** (eyes, mouth, head pose), **face-spoofing checks**, and **person/phone detection**.

This repository is for **experimentation** and **research** — not for production use.

## Features

- **Face detection** (OpenCV DNN, Haar, optional MTCNN/Dlib)
- **Facial landmarks** extraction and landmark-based detectors
- **Eye tracking** and simple gaze heuristics
- **Head pose estimation** (pitch / yaw / roll)
- **Mouth opening** / speaking heuristics
- **Face-spoofing** classifier wrapper
- **Person & phone detection** (YOLO/TFLite SSD demos)

## Quick start (Windows PowerShell)

1) Create and activate a virtual environment

```powershell
py -3 -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2) Upgrade pip

```powershell
python -m pip install --upgrade pip
```

3) Install common dependencies

```powershell
pip install opencv-python numpy imutils pillow
```

Optional (for TFLite demos):

```powershell
pip install tflite-runtime
```

4) Run a simple webcam demo (example)

```powershell
python face_detector.py
```

If a script expects missing models it will print a clear message showing the filename to add.

## Scripts (short guide)

Main scripts and purpose (keywords bolded):

- `face_detector.py` — **face detection** from webcam or image (uses models in `models/`).
- `face_landmarks.py` — compute **facial landmarks** (eyes, nose, mouth).
- `eye_tracker.py` — **eye/iris tracking** and attention heuristics.
- `head_pose_estimation.py` — compute **head orientation** from landmarks.
- `mouth_opening_detector.py` — detect **mouth-open events**.
- `face_spoofing.py` — run **spoofing classifier** (`models/face_spoofing.pkl`).
- `person_and_phone.py` — **person** and **phone detection** demo (TFLite or YOLO).
- `audio_part.py` — **audio capture** and simple keyword analysis.

## Models and where to place them

Place the model files in the `models/` folder (or the matching `coco models/` subfolder). Key files:

- `models/res10_300x300_ssd_iter_140000.caffemodel` & `deploy.prototxt` — OpenCV DNN **face detector**.
- `models/opencv_face_detector_uint8.pb` & `.pbtxt` — alternate **DNN face detector**.
- `models/face_spoofing.pkl` — **face-spoofing** pickled classifier.
- `models/yolov3.weights` — optional **YOLOv3** weights.
- `coco models/tflite mobnetv1 ssd/detect.tflite` — **TFLite SSD** model (used by `person_and_phone.py`).

If a script cannot find a model it will list the **expected filename** in its error output.

## Dependencies

Recommended packages (install with **pip**):

- **opencv-python**
- **numpy**
- **imutils**
- **pillow**
- **tflite-runtime** (or **tensorflow**)

Consider adding these to `requirements.txt` for convenience.

## Commands (quick reference)

Each command is shown on its own line/block as requested.

Create & activate venv (PowerShell):

```powershell
py -3 -m venv .venv
```

```powershell
.\.venv\Scripts\Activate.ps1
```

Upgrade pip:

```powershell
python -m pip install --upgrade pip
```

Install common deps:

```powershell
pip install opencv-python numpy imutils pillow
```

Optional TFLite runtime:

```powershell
pip install tflite-runtime
```

Run webcam face detector example:

```powershell
python face_detector.py
```

Run individual modules (each on its own line):

```powershell
python face_detection/faces_detection.py
```

```powershell
python head_pose_estimation.py
```

```powershell
python eye_tracker.py
```

```powershell
python mouth_opening_detector.py
```

```powershell
python face_spoofing.py
```

```powershell
python person_and_phone.py
```

```powershell
python audio_part.py
```

## Troubleshooting

- **Missing module** errors — install missing packages using **pip** inside the activated venv.
- **Missing model files** — download the required model and place it in `models/`.
- **TFLite on Windows** — if `tflite-runtime` fails to install, use the full **tensorflow** package or run TFLite demos on Linux.
- **No webcam or mic** — check Windows **Privacy Settings** and device drivers.

## Contributing

Contributions are welcome. Suggested improvements:

- Fix documentation or add **usage examples** for scripts.
- Add `requirements.txt` and small **unit tests** for non-GUI code.
- Include sample images or short videos demonstrating expected outputs.

Before submitting a PR, run changed scripts locally and include a short description of your change.

## License & notes

This repository does not include a formal license file. If you intend to reuse or redistribute the code,
add an appropriate `LICENSE` file (MIT, Apache-2.0, etc.).

Privacy & ethics: ensure compliance with **local laws** and obtain **consent** before recording or processing people's video/audio.

---

If you want, I can now:

- extract exact CLI flags from each script and add a `Usage` subsection per file, or
- create a `requirements.txt` and a `run_demo.ps1` PowerShell helper that executes the key commands above, or
- add a small unit test for one of the utility functions.

Tell me which you'd like next and I'll implement it.
