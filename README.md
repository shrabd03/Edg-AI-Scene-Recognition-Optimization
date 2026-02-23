# 🎓 Edge AI Campus Scene Recognition
## Benchmarking Deep Learning Models for Scene Classification

---

## 🎯 The Goal
The primary objective of this project is to build a **Deep Learning system** capable of accurately detecting and classifying scenes and objects within a **university campus environment**.

The challenge wasn't just to identify obvious categories like **Car** or **Tree**, but to distinguish between visually similar structures—specifically **Labs vs. Buildings**—which often confuse standard CNN models.

Additionally, we aimed to achieve **high accuracy on both powerful servers and lightweight edge devices**, making the system suitable for **future mobile and embedded applications**.

---

## 📂 The Data
To ensure realism and robustness, we created our **own dataset from scratch** instead of relying on curated online datasets.

- **Source:** Manually captured images around the **University of Jordan**
- **Classes:** 5 Categories  
  - Building  
  - Car  
  - Lab  
  - Person  
  - Tree  
- **Preprocessing:**
  - Manual filtering
  - Resizing to **224 × 224**
  - Data augmentation:
    - Rotation
    - Horizontal Flip
    - Zoom

---

## 🧠 The Engineering Breakthrough
Our research focused on testing different **Attention Mechanisms** and their impact on **heavy vs. lightweight architectures**.

### 🏋️ Heavyweight Test (Server Models)
- **Architecture:** DenseNet121  
- **Attention:** CBAM (Convolutional Block Attention Module)  
- ✅ Result: **99.15% accuracy**
- 📌 CBAM worked perfectly with large-capacity networks.

### ⚡ Lightweight Test (Edge Models)
- **Architecture:** EfficientNet-B0  
- ❌ Applying CBAM caused a **performance drop**
- 📉 Conclusion: CBAM was too aggressive for small models.

### ✅ The Solution
- Switched to **Coordinate Attention (CA)** for lightweight models
- 🎯 Result:
  - Preserved spatial information
  - Improved feature focus
  - Boosted accuracy to **98.03%**

---

## 📊 Performance Benchmark

| Category | Architecture | Attention Strategy | Accuracy | Verdict |
|--------|-------------|-------------------|----------|--------|
| Server | DenseNet121 | CBAM | **99.15%** | 🏆 Overall Best Accuracy |
| Edge | EfficientNet-B0 | Coordinate Attention | **98.03%** | ⚡ Best Efficiency |
| Edge | MobileNetV2 | Coordinate Attention | High | ✅ Outperformed MobileNetV3 |
| Edge | MobileNetV3 | Built-in SE | Lower | ❌ Lost to V2 + CA |
| Edge | EfficientNet-B0 | CBAM | 95.77% | ❌ Performance Drop |
| Baseline | MobileNetV2 | None | 92.40% | Baseline (Too Low) |

🔑 **Key Finding:**  
By manually integrating **Coordinate Attention** into the older **MobileNetV2**, we achieved **higher accuracy than MobileNetV3**, proving that **custom attention strategies can outperform newer pre-optimized architectures**.

---

## 📁 Project Structure
📦 Edge-AI-Campus-Scene-Recognition ┣ 📘 01_Server_Track_DenseNet_CBAM.ipynb ┣ 📕 02_Edge_Track_EfficientNet_CBAM_Fail.ipynb ┣ 📗 03_Edge_Track_EfficientNet_CoordAtt_Success.ipynb ┣ 📙 04_Lightweight_Benchmarking_MobileNet.ipynb ┣ 📄 Research_Paper.pdf ┗ 📊 Project_Presentation.pdf

- **01:** Best-performing heavy model
- **02:** Failed CBAM experiment on edge
- **03:** Successful Coordinate Attention optimization
- **04:** MobileNet V2/V3 benchmarking
- **Research Paper:** Full methodology & math
- **Presentation:** Visual project summary

---

## 👥 The Team
Built by:
- **Yarah Al-Hindi**
- **Malek Alsaudi**
- **Sahar Abdulhay**
- **Tasneem Al-Dweiri**

---

**University of Jordan**  
*Deep Learning Course Project*
