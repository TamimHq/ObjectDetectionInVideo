# Automated Traffic Analysis & Object Tracking Pipeline

## Overview
This repository contains an end-to-end machine learning pipeline designed to ingest raw video feeds, detect and track specific objects, and export the tracking data into structured CSV reports. Built using the state-of-the-art YOLO11 architecture and ByteTrack algorithms, this project demonstrates how to transform unstructured computer vision data into actionable, quantifiable metrics suitable for enterprise reporting and analytics.

## Repository Structure

* `Models/` 
  * `best.pt`: The custom-trained YOLO11 weights (trained for 100 epochs).
* `NoteBook/`
  * `object_detection_in_video.ipynb`: The complete Google Colab notebook containing the data ingestion, training loop, validation, and inference scripts. *(Note: API keys have been securely removed for public repository sharing).*
* `outputs/`
  * `web_ready_output.mp4`: The final annotated video featuring bounding boxes, tracking IDs, a defined Region of Interest (ROI) counting zone, and live on-screen tallies.
  * `total_counts.csv`: The structured data export containing the final aggregated counts of detected objects.
* `Results/`
  * `Confusion_matrix.png`: Model evaluation matrix showcasing classification accuracy across the dataset.
  * `Training_result.png`: Graphs detailing the training/validation loss and Mean Average Precision (mAP) over the 100-epoch training cycle.

## Core Features
* **Custom Fine-Tuning:** Trained YOLO11m on a comprehensive 80-class COCO dataset, achieving stable generalization without overfitting.
* **Multi-Object Tracking:** Utilizes ByteTrack to assign and maintain unique persistent IDs to moving objects across consecutive video frames, preventing double-counting.
* **Region of Interest (ROI) Counting:** Implements a dynamic "Counting Zone" logic. Objects are only tallied when their calculated center coordinates intersect with a predefined spatial boundary.
* **Automated Data Extraction:** Seamlessly translates visual tracking events into a clean `.csv` spreadsheet for seamless integration into downstream databases or MIS dashboards.
* **Web-Optimized Export:** Integrates FFmpeg within the Python pipeline to automatically compress the final OpenCV output into an H.264 MP4 format for native browser playback.

## Tech Stack
* **Python**
* **Ultralytics YOLO11** (Deep Learning & Computer Vision)
* **OpenCV** (Video processing, spatial math, and visual annotation)
* **ByteTrack** (Tracking algorithm)
* **FFmpeg** (Video codec compression)

## How to View
To see the results immediately, navigate to the `outputs/` folder and view the `web_ready_output.mp4` video. The corresponding data tallies are available in `total_counts.csv`.

To review the training methodology, open `NoteBook/object_detection_in_video.ipynb`.