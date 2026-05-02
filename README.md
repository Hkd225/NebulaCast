# 🌩️ NebulaCast AI — Edge Machine Learning Weather Predictor

![TensorFlow.js](https://img.shields.io/badge/TensorFlow.js-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white)
![GSAP](https://img.shields.io/badge/GSAP-88CE02?style=for-the-badge&logo=greensock&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)

**NebulaCast AI** is a premium, browser-based edge inference engine that predicts daily weather conditions (Clear or Rain) using a custom-trained Deep Learning model. By leveraging **TensorFlow.js**, the application performs high-speed, zero-latency inference entirely on the client side—eliminating the need for a backend server.

---

## ✨ Key Features

### 🧠 Machine Learning Pipeline
*   **End-to-End Training:** Includes a complete Python pipeline (Google Colab/Jupyter) for data ingestion, preprocessing, and model training using the Indonesian Climate dataset.
*   **Robust Architecture:** Built using Keras Functional API featuring Dense layers, Dropout for regularization, and Binary Crossentropy.
*   **Automated Export:** Safely exports model weights and architecture to `H5`, `TFLite`, and `TFJS` formats alongside a unified JSON metadata file for frontend scaling.
*   **Dynamic Thresholding:** Automatically calculates and exports the optimal F1-score probability threshold during validation.

### 💻 Edge-Inference Frontend
*   **Zero-Latency Processing:** Neural network calculations are performed locally via the user's browser CPU/WebGL.
*   **Immersive 3D UI:** Features awwwards-style 3D CSS parallax objects (Sun, Rain Clouds, Storms) that dynamically react to the model's output.
*   **Smooth User Experience:** Integrated with **Lenis** for smooth scrolling and **GSAP/ScrollTrigger** for staggered, high-performance animations.
*   **Interactive Terminal:** A built-in live console logger that tracks pipeline initialization, tensor extraction, and inference latency.
*   **Custom Interactions:** Ambient particle network background generated via HTML5 Canvas and a custom dynamic cursor.

---

## 🏗️ Technical Stack

**Model Development & Training:**
*   Python 3.x
*   TensorFlow / Keras
*   Scikit-Learn, Pandas, NumPy
*   Kagglehub (Dataset Integration)

**Web Application (Frontend):**
*   HTML5 / Modern CSS3 (Grid, Flexbox, Custom Variables)
*   Vanilla JavaScript (ES6+)
*   TensorFlow.js (`@tensorflow/tfjs`)
*   GSAP & ScrollTrigger (Animations)
*   Lenis (Smooth Scrolling)

---

## 📂 Project Structure

To ensure the web application can fetch the model weights and scaling parameters correctly, your project directory should look like this:
```text
📦 NebulaCast-AI
 ┣ 📂 models
 ┃ ┣ 📂 tfjs                 # TensorFlow.js exported model
 ┃ ┃ ┣ 📜 group1-shard1of1.bin
 ┃ ┃ ┗ 📜 model.json
 ┃ ┣ 📂 tflite               # TFLite model (Mobile ready)
 ┃ ┣ 📜 model_cuaca_webready.keras
 ┃ ┣ 📜 preprocessing_cuaca_webready.json # Important! Contains min-max scalers
 ┃ ┗ 📜 web_manifest.json
 ┣ 📜 index.html             # Main frontend application
 ┣ 📜 training_pipeline.ipynb # Original Colab Notebook
 ┗ 📜 README.md
```
*(Note: Ensure you adjust the fetch paths in `index.html` if you change this folder structure).*

---

## 🚀 Getting Started

Because the application fetches external JSON and `.bin` files via XHR/Fetch API, **it cannot be run directly by double-clicking the `index.html` file** (this will trigger CORS policy errors). You must serve it over a local web server.

### Prerequisites
*   Git
*   Python 3.x (or any preferred local web server like Node's `http-server`)

### Installation & Running Locally

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/nebulacast-ai.git](https://github.com/yourusername/nebulacast-ai.git)
   cd nebulacast-ai
   ```

2. **Start a local development server:**
   If you have Python installed, run:
   ```bash
   # For Python 3.x
   python -m http.server 8000
   ```
   *Alternatively, if you use Node.js:*
   ```bash
   npx http-server -p 8000
   ```

3. **Access the application:**
   Open your browser and navigate to `http://localhost:8000/index.html`.

---

## 📊 Input Parameters

The model accepts 6 continuous meteorological features to calculate the probability of rain for the next day:

| Parameter | Description | Unit |
| :--- | :--- | :--- |
| **Tn** | Minimum Temperature | °C |
| **Tx** | Maximum Temperature | °C |
| **Tavg** | Average Temperature | °C |
| **RH_avg** | Average Humidity | % |
| **ff_x** | Maximum Wind Speed | m/s |
| **ff_avg** | Average Wind Speed | m/s |

Missing inputs default to the training dataset's median values automatically to prevent NaN tensor errors.

---

## 👨‍💻 Author: Hakid
(Muhammad Auffa Hakim Aditya)
---
*If you find this project interesting or helpful, feel free to drop a ⭐ on the repository!*
```
