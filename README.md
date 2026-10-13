# HueFocus

A webcam-based color detection project designed to help color-blind users identify colors. Built with **Python, OpenCV, and NumPy**.

## How it works

1. Capture frames from the default webcam.
2. Convert each frame from BGR to HSV.
3. Create masks using the color ranges in `color_ranges`.
4. Dilate each mask with a 5 × 5 kernel and find its contours.
5. Label regions with an area greater than 800 pixels using bounding boxes and color names.

The configured ranges cover red, green, blue, cyan, magenta, white, and black. Red uses two HSV ranges; the second is labeled `Red2` in the current implementation.

## Run locally

The current camera setup uses OpenCV's Windows DirectShow backend (`cv2.CAP_DSHOW`) and opens fullscreen display windows.

From the repository directory, install the imported packages and launch the script:

```bash
python -m pip install opencv-python numpy
python HueFocus.py
```

| Key | Action |
| --- | --- |
| `s` | Freeze a snapshot and show its detected colors |
| `r` | Return to the live feed |
| `q` | Quit and release the camera |

## Read the code

[HueFocus.py](HueFocus.py) contains the complete implementation. Start with `color_ranges`, then `detect_colors()`, then the capture loop and keyboard controls.

Detection is based on fixed HSV thresholds rather than a trained model.
