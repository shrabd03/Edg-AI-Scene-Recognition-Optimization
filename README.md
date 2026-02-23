# Edg-AI-Scene-Recognition-Optimization
Benchmarking DenseNet+CBAM vs. EfficientNet+Coordinate Attention for Campus Scene Understanding.
Edge AI Campus Scene Recognition
Benchmarking Deep Learning Models for Scene Classification
  

The Goal
The primary objective of this project is to build a Deep Learning system capable of accurately detecting and classifying objects within a university campus environment.

The challenge wasn't just to identify a "Car" or a "Tree," but to distinguish between visually similar structures—specifically "Labs" vs. "Buildings"—which often confuse standard models. We wanted to see if we could achieve high accuracy not just on heavy servers, but also on lightweight architectures suitable for future mobile applications.

The Data
We created our own dataset from scratch to ensure the models were tested on real-world data, not just perfect internet images.

Source: Manually captured images around the University of Jordan.
Classes: 5 Categories (Building, Car, Lab, Person, Tree).

Processing: Images were manually filtered, resized to 224x224, and augmented (Rotation, Flip, Zoom) to increase dataset diversity.
The Engineering Breakthrough
Our research led to a critical discovery when testing different "Attention Mechanisms" to improve the classification:

The Heavyweight Test (DenseNet): When we added CBAM (Convolutional Block Attention Module) to the large DenseNet model, it worked perfectly, achieving 99.15% accuracy.
The Lightweight Test (EfficientNet): When we tried the exact same CBAM technique on the smaller EfficientNet, the performance actually dropped. It was too aggressive for the smaller network.
The Solution: We switched to Coordinate Attention (CA) for the lightweight models. This improved the model's ability to focus on specific features without losing information, boosting accuracy to 98.03%.

📊 Performance Benchmark
Category	Architecture	Attention Strategy	Accuracy	Verdict
Server	DenseNet121	CBAM	99.15%	🏆 Overall Best Accuracy
Edge	EfficientNet-B0	Coordinate Att.	98.03%	⚡ Best Efficiency
Edge	MobileNetV2	Coordinate Att.	High	✅ Outperformed MobileNetV3
Edge	MobileNetV3	Built-in SE	Lower	Lost to V2 + CA
Edge	EfficientNet-B0	CBAM	95.77%	❌ Performance Drop
Baseline	MobileNetV2	None	92.40%	Baseline (Too Low)
Key Finding: By manually adding Coordinate Attention to the older MobileNetV2, we achieved higher accuracy than the newer, pre-optimized MobileNetV3, proving the effectiveness of our custom attention strategy.

📂 Project Structure
01_Server_Track_DenseNet_CBAM.ipynb: The heavy model achieving the highest overall accuracy.
02_Edge_Track_EfficientNet_CBAM_Fail.ipynb: Our experiment showing that CBAM is not suitable for all architectures.
03_Edge_Track_EfficientNet_CoordAtt_Success.ipynb: The optimized lightweight model using Coordinate Attention.
04_Lightweight_Benchmarking_MobileNet.ipynb: Benchmarking MobileNet V2/V3 baselines against V2+CA.
Research_Paper.pdf: Full documentation of methodology and mathematical breakdown.
Project_Presentation.pdf: A visual summary of the project.
👥 The Team
Built by Yarah Al-Hindi, Malek Alsaudi, Sahar Abdulhay, and Tasneem Al-Dweiri.

University of Jordan | Deep Learning Project
