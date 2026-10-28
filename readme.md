# Lung Cancer Classification Using Deep Learning

## Overview

This project implements a deep learning-based image classification system to classify lung CT scan images into three categories:

* **Benign Cases**
* **Malignant Cases**
* **Normal Cases**

The model uses **MobileNetV2 Transfer Learning** with TensorFlow and Keras to extract image features and predict the corresponding class.

This project was developed in Google Colab using the IQ-OTH/NCCD Lung Cancer Dataset from Kaggle.

> **Disclaimer:** This is an educational machine learning project and is not intended for clinical diagnosis or medical decision-making.

## Objectives

* Develop an image classification model for lung CT scans.
* Apply transfer learning using a pretrained MobileNetV2 model.
* Preprocess and resize CT images for model training.
* Evaluate the model using test data and classification metrics.
* Predict classes for newly uploaded CT images.
* Save the trained model for future use.

## Technologies Used

| Technology   | Purpose                          |
| ------------ | -------------------------------- |
| Python       | Programming language             |
| TensorFlow   | Deep learning framework          |
| Keras        | Model development and training   |
| MobileNetV2  | Transfer learning architecture   |
| NumPy        | Numerical operations             |
| Pandas       | Dataset organization             |
| Matplotlib   | Visualization                    |
| Scikit-learn | Dataset splitting and evaluation |
| Google Colab | Development environment          |

## Dataset

**Dataset:** IQ-OTH/NCCD Lung Cancer Dataset

Dataset link: https://www.kaggle.com/datasets/adityamahimkar/iqothnccd-lung-cancer-dataset

The dataset contains lung CT scan images categorized into three classes:

| Class     | Description                       |
| --------- | --------------------------------- |
| Benign    | Images labeled as benign cases    |
| Malignant | Images labeled as malignant cases |
| Normal    | Images labeled as normal cases    |

The project loads the images from their class folders and resizes them to 224 × 224 pixels before passing them to the model.

## Model Architecture

The project uses MobileNetV2, a convolutional neural network pretrained on ImageNet.

The architecture includes:

1. **Input Layer:** Accepts RGB images of size 224 × 224.
2. **MobileNetV2 Base:** Extracts visual features from the images.
3. **Global Average Pooling:** Reduces the feature maps into a feature vector.
4. **Dropout Layer:** Helps reduce overfitting.
5. **Dense Output Layer:** Uses softmax to produce scores for the three classes.

### Training Configuration

* Input size: 224 × 224 pixels
* Batch size: 16
* Optimizer: Adam
* Loss function: Categorical cross-entropy
* Initial training epochs: Up to 10
* Transfer learning: Pretrained MobileNetV2 layers frozen during initial training
* Early stopping: Monitors validation loss

## Project Workflow

1. Download the dataset from Kaggle.
2. Extract and inspect the dataset folders.
3. Load and preprocess the CT scan images.
4. Divide the data into training, validation, and test sets.
5. Build the MobileNetV2 classification model.
6. Train the model using the training dataset.
7. Monitor validation performance.
8. Evaluate the model on held-out test images.
9. Generate predictions for uploaded images.
10. Save the trained model in Keras format.

## Model Evaluation

The project evaluates the model using:

* Test loss
* Test accuracy
* Precision
* Recall
* F1-score
* Confusion matrix

**Results:** Add the actual evaluation results after running the final evaluation cell. No accuracy value is claimed in this README because the final results have not been independently verified.

For reliable evaluation, images from the same patient should not be distributed across training, validation, and test sets. Patient-level separation is important when patient identifiers are available.

## Running the Project

### Option 1: Google Colab

1. Open Google Colab: https://colab.research.google.com/
2. Create a new notebook.
3. Upload or download the dataset.
4. Run the notebook cells in sequence.
5. Train the model and review the evaluation metrics.
6. Upload a test image to generate a prediction.

### Option 2: Run Locally

Clone the repository:

```bash
git clone YOUR_REPOSITORY_URL
cd YOUR_REPOSITORY_FOLDER
```

Install the required packages:

```bash
pip install tensorflow numpy pandas matplotlib scikit-learn pillow
```

Run the notebook using Jupyter Notebook or JupyterLab.

**Note:** The dataset must be downloaded separately unless it is explicitly included in the repository.

## Making Predictions

After training, the model can classify a compatible uploaded image into one of the three dataset classes.

The model returns a predicted class and a score for each class.

These scores reflect the model's output, not a clinically validated probability of cancer. Predictions may be unreliable on synthetic images, unfamiliar scanners, or images with different preprocessing.

## Saving the Model

The trained model can be saved in Keras format:

```python
model.save("/content/lung_cancer_classifier.keras")
```

The saved file can be downloaded from Google Colab and reused in a compatible TensorFlow application.

## Limitations

* The model is trained on a specific public dataset and may not generalize to other populations or scanners.
* Dataset labels and image quality can affect model performance.
* Random image-level splitting can cause data leakage when several images belong to the same patient.
* A high classification score does not establish diagnostic accuracy.
* The model has not been clinically validated.

## Future Improvements

* Implement patient-level data splitting.
* Evaluate performance on an independent external dataset.
* Add Grad-CAM visualizations to inspect image regions influencing predictions.
* Develop a web interface for uploading CT images.
* Improve reproducibility through saved configurations and fixed random seeds.
* Seek appropriate clinical validation before considering any medical application.

## Ethical Considerations

This project is intended for educational and research purposes only. It must not be used to diagnose, rule out, or make treatment decisions about lung cancer. Clinical interpretation must be performed by qualified healthcare professionals.

## Author

Vansh Gupta GitHub: github.com/vanshguptaa14 LinkedIn: linkedin.com/in/vansh-gupta-62a117305.

## License

Add an appropriate license after confirming that the dataset and project dependencies permit the intended use.
