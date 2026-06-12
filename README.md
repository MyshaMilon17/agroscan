# AgroScan

A wheat leaf disease detection web app built with Flask and TensorFlow.

## Overview

AgroScan allows users to upload a wheat leaf photo through a browser UI and returns a disease prediction with confidence score. The application loads a pre-trained `MobileNetV2` model and performs image preprocessing before inference.

## Features

- Upload a wheat leaf image from your device
- Predict 1 of 5 wheat disease categories
- Display confidence score for the prediction
- Live preview of uploaded image
- Light/dark theme toggle and English/Bangla UI support
- Uses a pre-trained TensorFlow model stored in `model/MobileNetV2.keras`

## Supported Disease Classes

- Black Point
- Fusarium Foot Rot
- Healthy Leaf
- Leaf Blight
- Wheat Blast

## Project Structure

- `app.py` — Flask application entry point
- `model/MobileNetV2.keras` — pre-trained TensorFlow model file
- `templates/index.html` — front-end HTML template
- `static/css/styles.css` — site styling
- `static/uploads/` — folder for uploaded images
- `sample_test_images/` — example input images for quick testing
- `wheat-leaf-full-pipeline.ipynb` — training and evaluation notebook
- `website_outputs/` — generated output assets and visualizations

## Requirements

- Python 3.8+
- Flask
- TensorFlow 2.x
- numpy
- Pillow

## Installation

1. Create and activate a Python virtual environment:

   ```bash
   python -m venv venv
   venv\Scriptsctivate
   ```

2. Install the required Python packages:

   ```bash
   pip install flask tensorflow numpy pillow
   ```

3. Verify the model file exists:

   - `model/MobileNetV2.keras`

## Running the App

Start the Flask application:

```bash
python app.py
```

Open the site in a browser:

- `http://127.0.0.1:5000/`

Upload a wheat leaf image and click `Predict disease`.

## How It Works

1. The Flask app loads the saved MobileNetV2 model from `model/MobileNetV2.keras`.
2. Uploaded images are saved to `static/uploads/`.
3. The image is resized to `256x256`, converted to an array, and preprocessed with `mobilenet_v2.preprocess_input`.
4. The model predicts probabilities for the five classes.
5. The app displays the predicted class and confidence percentage.

## Training and Model Notes

- The notebook `wheat-leaf-full-pipeline.ipynb` contains the training pipeline, dataset exploration, augmentation, model selection, and evaluation.
- It uses a wheat leaf dataset organized into 5 classes.
- The deployed app uses a lightweight `MobileNetV2` model for inference.

## Notes

- Uploaded images are stored in `static/uploads/` by default.
- The application starts in debug mode when run directly from `app.py`.
- If the model file is missing, the app will fail to load and must be restored in the `model/` directory.

