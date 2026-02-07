# Wafer Defect Multi-Task Classification (VLSI)

This repository presents a **multi-task deep learning solution** for wafer defect analysis in **VLSI manufacturing**.

The trained model is provided in **ONNX format** for efficient, framework-independent inference.

Due to GitHub file size limitations, the **dataset is hosted externally**, while the **ONNX model is included directly in this repository**.

---

## 📁 Repository Contents

```text
Wafer-Defect-MultiTask/
├── README.md
└── wafer_defect_multitask_model.onnx
```

---

## 📊 Dataset

The dataset is hosted externally due to GitHub file size limitations.

- **Dataset ZIP (Google Drive):**  
  https://drive.google.com/file/d/1RySfy0fkOwzzTEh1w4gowlEppPftanUG/view

### Dataset Structure

After downloading and extracting `dataset.zip`, the dataset directory structure is:

```text
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
```

---

## 🧠 Model (ONNX)

- **Model Format:** ONNX  
- **Input Shape:** `224 × 224 × 3` (RGB image)  
- **Model Type:** Multi-task Convolutional Neural Network  

### Model Outputs

The ONNX model produces **three outputs**:

1. Clean vs Defected classification (2 classes)  
2. Material classification – Silicon / Germanium (2 classes)  
3. Defect type classification (7 classes)

### ONNX Model File

```text
wafer_defect_multitask_model.onnx
```

---

## ▶️ ONNX Inference (Optional)

Example inference using **ONNX Runtime**:

```python
import onnxruntime as ort
import numpy as np

session = ort.InferenceSession("wafer_defect_multitask_model.onnx")
input_name = session.get_inputs()[0].name

dummy_input = np.random.rand(1, 224, 224, 3).astype(np.float32)
outputs = session.run(None, {input_name: dummy_input})

print(outputs)
```

---

