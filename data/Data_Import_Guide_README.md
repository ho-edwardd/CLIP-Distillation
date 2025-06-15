# README: Importing MSCOCO Data for All Files

## Overview
This guide explains how to correctly import and preprocess the MSCOCO 2014 dataset for use with all associated files. The dataset will be downloaded, extracted, and made ready for use in a local directory. This ensures consistency across all scripts and minimizes issues with data indexing.

---

## Why Local Extraction?
While directly unzipping the dataset to Google Drive might seem efficient, it has been observed that Google Drive can fail to handle all 80k+40k observations properly. This can lead to data indexing issues. To avoid these problems, the dataset is extracted to the local directory, ensuring proper indexing and accessibility.

---

## Steps to Import Data

### 1. Run the First Cell: Download Packages, Pretrained Models, and Dataset
The first cell in the scripts will:
- Download required Python packages.
- Fetch the pretrained CLIP model.
- Download the MSCOCO 2014 dataset (images and annotations).

### 2. Run the Second Cell: Extract and Unzip MSCOCO Data
The second cell will:
- Extract the zipped dataset files.
- Organize the files into the appropriate directory structure.

After extraction, the dataset will be available in:
- **Images Directory:** `content/coco2014/val2014`
- **Annotations Directory:** `content/coco2014/annotations`

---

## Directory Structure
Ensure that the dataset is organized as follows:
```
├── data/
│   ├── coco2014/
│   │   ├── val2014/         # Validation images
│   │   ├── train2014/       # Training images (if used)
│   │   ├── annotations/     # Annotations (captions, bounding boxes, etc.)
```

---

