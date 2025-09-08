# AI/ML Football Analysis System

This project is an **end-to-end AI/ML solution for football video analysis**, designed to detect and track players, referees, and footballs, and provide in-depth statistical insights such as **team ball acquisition, player speed, and distance covered**. The system robustly handles **camera movements and perspective distortions**, offering a comprehensive understanding of building a real-world machine learning system for sports analytics.

---

## 📖 Project Overview

The system analyzes football matches from video footage using **state-of-the-art object detection and tracking**. Beyond simple detection, it:

- Assigns players to teams.
- Estimates camera motion and corrects for perspective distortions.
- Calculates precise player statistics in **real-world units** (meters and km/h).
- Demonstrates handling of real-world challenges with a wide range of **computer vision and machine learning techniques**.

---

## ✨ Key Features & Components

1. **Object Detection**
    - Utilizes **YOLO (You Only Look Once)** for detecting players, referees, and footballs.
    - Fine-tunes the model on a **custom annotated dataset** to handle rare ball detections and avoid misclassifications.

2. **Model Training & Fine-tuning**
    - Trains **YOLOv5** on the "football player detection image dataset" from **Roboflow**.
    - GPU-accelerated training on **Google Colab** for efficient processing.

3. **Object Tracking**
    - Assigns consistent IDs to detected objects across frames using **ByteTrack-based tracker** (via the **supervision** library).

4. **Team Assignment**
    - Uses **K-means clustering** on player bounding box pixels to assign players to teams.
    - Handles ambiguous goalkeeper colors with hardcoded rules for consistency.

5. **Ball Acquisition Analysis**
    - Interpolates missing ball detections for continuity.
    - Assigns the ball to the closest player and calculates **ball possession percentage**.

6. **Camera Movement Estimation**
    - Uses **optical flow** (`cv2.calcOpticalFlowPyrLK`) to track camera shifts.
    - Adjusts player positions for camera motion for accurate movement analysis.

7. **Perspective Transformation**
    - Converts pixel coordinates into **real-world meters** using `cv2.getPerspectiveTransform`.
    - Filters out detections outside the transformed court area.

8. **Player Speed and Distance Calculation**
    - Calculates **player speed (km/h)** and **distance covered (meters)** using real-world positions.
    - Smooths speed calculations over a defined frame window.

9. **Advanced Visualizations & Annotations**
    - Uses **custom annotations**: semicircles for players, yellow semicircles for referees, green triangles for ball.
    - Displays **player IDs, team numbers, ball possession**, and **speed/distance metrics** on video overlays.

10. **Development Utilities**
    - `video_utils.py` for reading/saving videos.
    - `bbbox_utils.py` for bounding box calculations.
    - **Pickle caching** for expensive computations to accelerate development.

---

## 🛠️ Skills and Technologies Used

### Programming Languages & Concepts
- **Python**: Main language for ML, computer vision, and data processing.
- **OOP & Modular Programming**: Classes like `Tracker`, `TeamAssigner`, `CameraMovementEstimator` ensure reusable, maintainable code.

### Machine Learning & Computer Vision
- **YOLOv5 / YOLOv8**: Object detection models.
- **Ultralytics**: YOLO integration for training and inference.
- **OpenCV (cv2)**: Video I/O, image processing, optical flow, and perspective transformation.
- **K-means Clustering (scikit-learn)**: Team assignment via color segmentation.
- **Supervision (sv)**: ByteTrack object tracking.

### Data Handling & Scientific Computing
- **Pandas**: Data manipulation (e.g., ball interpolation).  
- **NumPy**: Numerical operations, distance calculations.  
- **pickle**: Cache intermediate results for faster development.

### Development Tools
- **VS Code**, **Google Colab**, **Jupyter Notebooks**: Development, GPU training, visualization.  
- **Git & GitHub**: Version control and collaboration.  
- **Matplotlib**: Visualization for development/debugging.

### Mathematical & Algorithmic Concepts
- **Optical Flow**: Motion estimation between frames.
- **Perspective Geometry**: Pixel-to-real-world coordinate transformation.
- **Euclidean Distance**: Calculating distances between players, ball, and features.

---

## 🚀 Getting Started

1. **Clone the Repository**
```bash
git clone <repository_url>
cd <project_directory>
