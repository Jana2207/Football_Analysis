# ⚽🔥 AI/ML Football Match Analysis 🚀  

![Sample Output](output_videos/screenshot.png)  

---

## 🎯 Introduction  
Welcome to the **AI-powered Football Match Analysis Project**! 🏆⚡  

This project uses **Deep Learning + Computer Vision** to detect, track, and analyze football gameplay in real-time. The system provides:  
- 👀 Continuous **ball & player detection**  
- 🏃‍♂️ Player tracking with unique IDs  
- 🎽 Team classification by jersey color  
- ⚡ Speed estimation of players  
- 📊 Ball possession stats for each team  
- 🎥 Camera motion compensation  
- 🧠 Smart visualizations for better game insights  

---

## 🤖 Models Used  
- 🟢 **YOLOv5x** → Custom trained for object detection (players, referees, ball).  
- 🔵 **YOLOv8x** → Tested for higher precision and real-time inference.  

---

## 🚩 Challenges, Solutions & Impact  

### 1️⃣ Ball not detected continuously + outside objects 🚫⚽  
- **Reason**: YOLO pretrained on generic dataset, detecting unnecessary objects.  
- **Solution**:  
  - Annotated dataset using **Roboflow**.  
  - Trained **YOLOv5x for 100 epochs** on players, referees, goalkeepers, and ball.  
- **Impact**: ✅ Ball detected more consistently, irrelevant objects ignored.  

---

### 2️⃣ Player Tracking Across Frames 🏃‍♂️🔢  
- **Reason**: Bounding boxes don’t correlate frame-to-frame.  
- **Solution**:  
  - Used **ByteTrack** → assigns `tracker_id` to each object.  
  - Merged goalkeepers into player class (due to small dataset).  
- **Impact**: ✅ Seamless tracking of players across the entire match.  

---

### 3️⃣ Cluttered Bounding Boxes 📦👀  
- **Reason**: Rectangles obscure gameplay & field view.  
- **Solution**:  
  - Replaced with **ellipses under players/referees**.  
  - Displayed **unique IDs** inside ellipses.  
- **Impact**: ✅ Cleaner visualization & smoother viewing experience.  

---

### 4️⃣ Differentiating Teams 🎽🔴🔵  
- **Reason**: YOLO detects players but not teams.  
- **Solution**:  
  - Extracted jersey color.  
  - Applied **K-Means (k=2)** for clustering into two teams.  
  - Segmented jersey from pitch using image segmentation.  
- **Impact**: ✅ Each player shown with ellipse in **team color** (e.g., red vs blue).  

---

### 5️⃣ Small Dataset → Ball Detection Issues ⚽❌  
- **Solution**:  
  - Applied **interpolation** → assumed linear motion frame-to-frame.  
- **Impact**: ✅ Continuous ball trajectory reconstructed.  

---

### 6️⃣ Highlighting Player in Possession 🌟👟  
- **Reason**: No direct relation between ball & player.  
- **Solution**:  
  - Found nearest player to ball using **distance threshold**.  
  - Highlighted player visually.  
- **Impact**: ✅ Clear indication of who controls the ball.  

---

### 7️⃣ Team Ball Possession Stats 📊🏆  
- **Solution**:  
  - Measured possession duration per player.  
  - Aggregated by team.  
- **Impact**: ✅ Generated meaningful stats like **team dominance %**.  

---

### 8️⃣ Camera Motion 🎥↔️  
- **Reason**: Camera pans/zooms → relative displacement.  
- **Solution**:  
  - Detected **static features** (ground corners, roof) via **Optical Flow**.  
  - Estimated displacement for camera motion.  
- **Impact**: ✅ Camera movement compensated → stable analysis.  

---

### 9️⃣ Independent Player Motion 🏃‍♂️➡️  
- **Solution**:  
  - Subtracted camera motion vector from player tracks.  
- **Impact**: ✅ True player movement isolated from camera shifts.  

---

### 🔟 Perspective Transformation 📐⚽  
- **Reason**: Camera not perpendicular → distorted measurements.  
- **Solution**:  
  - Selected trapezoid region of ground.  
  - Applied **perspective transform** for correct scaling.  
- **Impact**: ✅ Accurate distance & position mapping.  

---

### 1️⃣1️⃣ Player Speed Estimation ⚡🏃‍♂️  
- **Solution**:  
  - Used first & last detection frames + timestamps.  
  - Measured distance traveled (perspective-corrected).  
  - Converted to **km/h**.  
- **Impact**: ✅ Player speeds annotated live during gameplay.  

---

## 🛠️ Skills & Technologies Used  
- 🧠 **Deep Learning**: YOLOv5x, YOLOv8x, PyTorch  
- 👀 **Computer Vision**: OpenCV, Optical Flow, Perspective Transformation  
- 🎯 **Tracking**: ByteTrack  
- 🎨 **Clustering & Segmentation**: K-Means, Image Segmentation  
- 📝 **Data Annotation**: Roboflow  
- 💻 **Programming**: Python  
- 📊 **Visualization**: Ellipse annotations, Matplotlib  

---

## 🌍 Real-Life Applications  
- 📺 **Sports Broadcasting** → Enhanced viewer experience with AI overlays.  
- 🏆 **Team Analytics** → Coaches analyze player performance & ball control.  
- 🎯 **Scouting & Recruitment** → Track potential players’ stats.  
- 🎮 **Game Simulation** → Useful for esports training & tactical analysis.  

---

## 📌 Conclusion  
This project shows how **AI + Computer Vision** can **revolutionize football analysis** ⚽🤖.  
From real-time tracking to tactical insights, it delivers **data-driven intelligence** that benefits players, coaches, broadcasters, and fans alike.  

---

## 📬 Contact  
👤 **Janardhan Reddy Illuru**  
- 🌐 GitHub: [Jana2207](https://github.com/Jana2207)  
- 💼 LinkedIn: [Janardhan Reddy Illuru](https://www.linkedin.com/in/jana2207/)  
- 📧 Email: **janareddy2207@gmail.com**  

---
