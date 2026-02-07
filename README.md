Wafer Defect Multi-Task Classification (VLSI)



This repository presents a multi-task deep learning solution for wafer defect analysis in VLSI manufacturing.

The trained model is provided in ONNX format for efficient and framework-independent inference.



All required resources (dataset + ONNX model) are included directly in this GitHub repository, as mandated.



📁 Repository Structure

Wafer-Defect-MultiTask/

│

├── dataset.zip

├── wafer\_defect\_multitask\_model.onnx

└── README.md



\## 📊 Dataset



Due to GitHub file size limitations, the dataset is hosted externally.



\- \*\*Dataset ZIP (Google Drive):\*\*  

&nbsp; https://drive.google.com/file/d/1RySfy0fkOwzzTEh1w4gowlEppPftanUG/view?usp=drive\_link



\### Dataset Structure



After downloading and extracting `dataset.zip`, the dataset directory structure is:



dataset/

├── clean/

│   ├── clean\_si/

│   └── clean\_ge/

└── defected/

&nbsp;   ├── bridge\_si/

&nbsp;   ├── bridge\_ge/

&nbsp;   ├── cmp\_si/

&nbsp;   ├── cmp\_ge/

&nbsp;   ├── cracks\_si/

&nbsp;   ├── cracks\_ge/

&nbsp;   ├── ler\_si/

&nbsp;   ├── ler\_ge/

&nbsp;   ├── linebreak\_si/

&nbsp;   ├── linebreak\_ge/

&nbsp;   ├── pinhole\_si/

&nbsp;   ├── pinhole\_ge/

&nbsp;   ├── vias\_si/

&nbsp;   └── vias\_ge/



🧠 Model (ONNX)



Model Format: ONNX



Input Shape: 224 × 224 × 3 (RGB image)



Model Type: Multi-task Convolutional Neural Network



Model Outputs



The ONNX model produces three outputs:



Clean vs Defected classification (2 classes)



Material classification – Silicon / Germanium (2 classes)



Defect type classification (7 classes)



ONNX Model File

wafer\_defect\_multitask\_model.onnx



▶️ ONNX Inference (Optional)



Example showing how to run inference using ONNX Runtime:



import onnxruntime as ort

import numpy as np



\# Load ONNX model

session = ort.InferenceSession("wafer\_defect\_multitask\_model.onnx")



\# Get model input name

input\_name = session.get\_inputs()\[0].name



\# Dummy input (replace with actual preprocessed wafer image)

dummy\_input = np.random.rand(1, 224, 224, 3).astype(np.float32)



\# Run inference

outputs = session.run(None, {input\_name: dummy\_input})



print("Model outputs:", outputs)





This demonstrates how the ONNX model can be used for fast inference, edge deployment, and hardware-aware VLSI applications.

