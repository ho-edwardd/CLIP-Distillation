# README: Using the Validation Subset Evaluation Script

## Overview
This script is designed to evaluate the performance of a student model trained using the CLIP architecture on the MSCOCO dataset. It processes a subset of 5000 images from the validation set to compute image-to-texts, such as Recall@K. The script also saves the predictions and ground truth labels in a JSON file and displays the top predictions for the first 5 images. Note, this file is mainly for the use of saving the prediction for the validation files, in terms of Recall@K metrics, the other files found in /code/ for each model (extension1, extension2, etc.) will all have evaluation metrics. So evaluation within in this file isn't the primary purpose.

---

## Prerequisites
To use this script, ensure the following dependencies are installed:

- Python 3.7+
- PyTorch
- torchvision
- CLIP (via `pip install git+https://github.com/openai/CLIP.git`)
- NumPy
- Matplotlib
- PIL (Pillow)

---

## Instructions for Use

### 1. Setting Up MSCOCO Dataset

#### Downloading the Dataset:
- Run the first cell which will download and extract the files to local Collab directory

### 2. Adjusting Parameters

#### Subset Size:
The script processes only the first 5000 images from the validation set. To change this:
```python
subset_indices = list(range(5000))  # Adjust the range to process more or fewer images.
```

### 3. Running the Script

#### File Output:
- Predictions and ground truth labels are saved in a JSON file at:
  `/content/drive/MyDrive/coco2014/predictions_and_labels.json`

#### Top 5 Predictions:
- The script displays the first 5 images along with their predicted captions and ground truth labels.

## Example Outputs

#### JSON File Structure:
```json
[
  {
    "image_index": 0,
    "predicted_captions": ["Caption 1", "Caption 2", ...],
    "truth_captions": ["Ground truth 1", "Ground truth 2", ...]
  },
  ...
]
```

#### Console Output:
For the first 5 images:
```
Image Index: 0
Top-5 Predicted Captions: ["A person riding a bike", "A man on a bicycle", ...]
Ground Truth Captions: ["A man is riding a bicycle", "A person cycling"]
```

---

## Notes
1. If memory issues occur, reduce the subset size since running the whole validation set of (~40k) will generally cause issues.
2. Results are saved in `/content/drive/MyDrive/coco2014` by default. Adjust the `output_dir` variable to save elsewhere.

---

