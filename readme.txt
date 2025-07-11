Project: Vehicle Detection and Classification using YOLOv8
===========================================================

This project implements a real-time vehicle detection and classification system in video streams using the YOLOv8 object detection model and OpenCV. It distinguishes between Light Motor Vehicles (LMVs) and Heavy Motor Vehicles (HMVs), providing both an annotated video output and a detailed CSV log of vehicle counts per frame.

---

1. Prerequisites
----------------

Before running the notebook, ensure you have the following installed:

- Python 3.x (Recommended: 3.8 or higher)  
  Download from: https://www.python.org/downloads/
- pip: Python package installer (usually comes with Python)
- Jupyter Notebook: Interactive environment to run `.ipynb` files

2. Setup Instructions
---------------------

2.1 Create a Virtual Environment (Recommended)

    python -m venv venv

2.2 Activate the Virtual Environment

    On Windows:
        .\venv\Scripts\activate
    On macOS/Linux:
        source venv/bin/activate

2.3 Install Required Libraries

    pip install ultralytics opencv-python jupyter pandas

Note: ultralytics will handle downloading the `yolov8n.pt` model and `bytetrack.yaml` config file if not found locally.

3. Project Configuration within the Notebook
--------------------------------------------

Open the Jupyter Notebook (e.g., `main.ipynb`). At the top, update the configuration variables:

- MODEL_PATH: Path to the YOLOv8 model file (e.g., 'yolov8n.pt')
- VIDEO_PATH: Path to the input video file (e.g., 'path/to/video.mp4')
- CONF_THRESHOLD: Confidence threshold (e.g., 0.3)
- RESIZE_SCALE: Resize factor for frames (e.g., 0.75)
- TRACKER_CFG: Path to tracker config (e.g., 'bytetrack.yaml')
- CSV_OUTPUT: Output CSV name (e.g., 'vehicle_counts.csv')

Important: The provided path in the code sample uses:
    /home/linux/coding/elc_activities/computer_vision/mixkit-ride-through-the-streets-of-london-4263-hd-ready.mp4
You must replace this with a valid local path.

4. Running the Code (Jupyter Notebook)
--------------------------------------

1. Launch Jupyter:

       jupyter notebook

2. Open the notebook (e.g., `main.ipynb`)
3. Run the cells sequentially using Shift + Enter

- A video window will display the annotated results
- To stop execution:
    - Press 'q' in the OpenCV window (may not always work), or
    - In Jupyter: click Interrupt the kernel (square stop icon)

5. Output Files
---------------

After successful execution:

- Annotated Video: e.g., `input_video_out.avi` (bounding boxes, class, ID, confidence, LMV/HMV count)
- vehicle_counts.csv: Frame-wise log of LMV and HMV counts

6. Dataset Information (Model Training - Optional)
--------------------------------------------------

The project uses a pre-trained YOLOv8-nano model (yolov8n.pt) — no custom dataset is required.

To train your own model:

- COCO Dataset: https://cocodataset.org/#home
- Open Images Dataset: https://storage.googleapis.com/openimages/web/index.html
- Custom Datasets: Use LabelImg or Roboflow for annotation and management

7. Results Summary
------------------

Tested on a UA-DETRAC subsample of 8,379 images:

- Total LMVs Detected: 35,122
- Total HMVs Detected: 2,498
- Average LMVs per Image: ~4.19
- Average HMVs per Image: ~0.30
- Maximum LMVs in a Single Image: 28
- Maximum HMVs in a Single Image: 5

These results demonstrate effective classification and high robustness in dense traffic scenes.

---
