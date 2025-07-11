Project: Vehicle Detection and Classification using YOLOv8

This project implements a real-time vehicle detection and classification system in video streams using the YOLOv8 object detection model and OpenCV. It distinguishes between Light Motor Vehicles (LMVs) and Heavy Motor Vehicles (HMVs), providing both an annotated video output and a detailed CSV log of vehicle counts per frame.

---

**1. Prerequisites**

Before running the notebook, ensure you have the following installed:

* **Python 3.x**: Recommended version 3.8 or higher.
    * Download from: https://www.python.org/downloads/
* **pip**: Python package installer (usually comes with Python).
* **Jupyter Notebook**: The interactive environment to run `.ipynb` files.

**2. Setup Instructions**

Follow these steps to set up the environment and get the project running:

* **2.1 Create a Virtual Environment (Recommended):**
    Open your terminal or command prompt and run:
    ```bash
    python -m venv venv
    ```
* **2.2 Activate the Virtual Environment:**
    * **On Windows:**
        ```bash
        .\venv\Scripts\activate
        ```
    * **On macOS/Linux:**
        ```bash
        source venv/bin/activate
        ```
* **2.3 Install Required Libraries:**
    Install all necessary Python packages using pip:
    ```bash
    pip install ultralytics opencv-python jupyter pandas # pandas is useful if you want to analyze the CSV later
    ```
    * `ultralytics` will automatically handle downloading the `yolov8n.pt` model and the `bytetrack.yaml` configuration file for tracking the first time you run the script, if they are not found locally.

**3. Project Configuration within the Notebook**

Open the `your_notebook_name.ipynb` file in Jupyter. At the beginning of the notebook, you will find configuration parameters. You might need to adjust these directly within the notebook cells:

* **`MODEL_PATH`**: Path to the YOLOv8 model file (e.g., 'yolov8n.pt').
* **`VIDEO_PATH`**: **CRITICAL**: Update this path to point to your input video file.
    * Example: `VIDEO_PATH = 'path/to/your/video.mp4'`
    * The provided code sample uses `/home/linux/coding/elc_activities/computer_vision/mixkit-ride-through-the-streets-of-london-4263-hd-ready.mp4`. **You MUST change this to a valid path on your system.**
* **`CONF_THRESHOLD`**: Confidence threshold for object detection (e.g., 0.3 means 30% confidence).
* **`RESIZE_SCALE`**: Scale factor to resize the video frames (e.g., 0.75 means 75% of original size).
* **`TRACKER_CFG`**: Configuration file for the object tracker (e.g., 'bytetrack.yaml').
* **`CSV_OUTPUT`**: Name of the CSV file for vehicle counts (e.g., 'vehicle_counts.csv').

**4. Running the Code (Jupyter Notebook)**

1.  **Start Jupyter Notebook:**
    Navigate to the directory containing your `.ipynb` file in your activated virtual environment and run:
    ```bash
    jupyter notebook
    ```
    This will open a new tab in your web browser with the Jupyter dashboard.
2.  **Open the Notebook:**
    Click on your `.ipynb` file (e.g., `vehicle_detection.ipynb`) in the Jupyter dashboard.
3.  **Run Cells:**
    Execute each cell in the notebook sequentially. You can do this by selecting a cell and pressing `Shift + Enter`, or by going to `Cell > Run All`.
    * The video processing will start, and a new window (from OpenCV) will pop up displaying the annotated video.
    * To stop the execution and close the video window, go back to the Jupyter notebook, click the `Interrupt the kernel` button (square stop icon), or select `Kernel > Interrupt` from the menu. You can also try pressing 'q' in the OpenCV window, but interrupting the kernel is the most reliable way to stop execution in a notebook.

**5. Output Files**

Upon completion of the notebook cells, the script will generate two files in the same directory as your notebook:

* **Annotated Video**: A new video file (e.g., `your_input_video_name_out.avi`). This video will have bounding boxes, labels (class, ID, type, confidence), and LMV/HMV counts overlaid on each frame. The format is `.avi` using the `XVID` codec.
* **`vehicle_counts.csv`**: A CSV file containing a frame-by-frame log of detected Light Motor Vehicles (LMV Count) and Heavy Motor Vehicles (HMV Count).

**6. Dataset Information (for Model Training - Not required for running this code)**

The provided code uses a **pre-trained YOLOv8-nano model** (`yolov8n.pt`). This means you **do not need a separate dataset** to run this detection and classification script. The model has already been trained on a large dataset (like COCO) that includes common vehicle classes.

If you wish to train your own custom model for specific vehicle types or unique environments (as mentioned in "Potential Improvements" in the report), you would typically use datasets such as:

* **COCO (Common Objects in Context):** A large-scale object detection, segmentation, and captioning dataset.
    * Website: https://cocodataset.org/#home
* **Open Images Dataset:** Another large and diverse dataset for object detection.
    * Website: https://storage.googleapis.com/openimages/web/index.html
* **Custom Datasets:** For highly specialized vehicle types or conditions, you would need to collect and annotate your own images/videos. Tools like LabelImg or Roboflow can assist in this process.
**7. Results Summary**

    To evaluate the system’s performance, the vehicle detection and classification pipeline was tested on a subsample of the UA-DETRAC dataset comprising 8,379 traffic images. The following insights summarize the results:

    Total Images Processed: 8,379
    Total Light Motor Vehicles (LMVs) Detected: 35,122
    Total Heavy Motor Vehicles (HMVs) Detected: 2,498
    Average LMVs per Image: ~4.19
    Average HMVs per Image: ~0.30
    Maximum LMVs in a Single Image: 28
    Maximum HMVs in a Single Image: 5
    These results indicate that the system is effective at identifying and distinguishing between vehicle types, especially in scenes with high LMV density. The consistent detection across thousands of images highlights the robustness and scalability of the YOLOv8-based approach.
---
