🧩 Wafer Defect Multi-Task Classification (VLSI)

This repository presents a multi-task deep learning solution for wafer defect analysis in VLSI manufacturing.

The trained model is provided in ONNX format for efficient and framework-independent inference.

Due to GitHub file size limitations, the dataset is hosted externally, while the ONNX model is included directly in this repository.

📁 Repository Structure
Wafer-Defect-MultiTask/
├── README.md
└── wafer_defect_multitask_model.onnx

📊 Dataset

Due to GitHub file size limitations, the dataset is hosted externally.

Dataset ZIP (Google Drive):
👉 https://drive.google.com/file/d/1RySfy0fkOwzzTEh1w4gowlEppPftanUG/view?usp=drive_link

Dataset Structure

After downloading and extracting dataset.zip, the directory structure will be:

dataset/
├── clean/
│   ├── clean_si/
│   └── clean_ge/
└── defected/
    ├── bridge_si/
    ├── bridge_ge/
    ├── cmp_si/
    ├── cmp_ge/
    ├── cracks_si/
    ├── cracks_ge/
    ├── ler_si/
    ├── ler_ge/
    ├── linebreak_si/
    ├── linebreak_ge/
    ├── pinhole_si/
    ├── pinhole_ge/
    ├── vias_si/
    └── vias_ge/

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
wafer_defect_multitask_model.onnx

▶️ ONNX Inference (Optional)

Example showing how to run inference using ONNX Runtime:

import onnxruntime as ort
import numpy as np

# Load ONNX model
session = ort.InferenceSession("wafer_defect_multitask_model.onnx")

# Get model input name
input_name = session.get_inputs()[0].name

# Dummy input (replace with actual preprocessed wafer image)
dummy_input = np.random.rand(1, 224, 224, 3).astype(np.float32)

# Run inference
outputs = session.run(None, {input_name: dummy_input})

print("Model outputs:", outputs)


This demonstrates how the ONNX model can be used for fast inference, edge deployment, and hardware-aware VLSI applications.
