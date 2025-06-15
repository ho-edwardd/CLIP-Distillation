
# README: Hyperparameter_Tuning Notebook

## Overview
This notebook are the instructions for how to properly run the hyperparameter tuning notebook. Again, like all the notebooks, they are meant to be run sequentially with no issues. However, if you want to change anything, the you can look below.

## Default Parameters:

- Temperature: 0.07
- Alpha (weight for KL term): 1.0
- Beta (weight for L2 term): 0.3
- Gamma (weight for synergy rewards): 0.7
- Learning rate: 1e-4

## Instructions

1. **Run the Notebook:**
   - Execute each cell sequentially to perform data loading, feature extraction, and evaluation.
2. **Evaluate Metrics:**
   - The notebook outputs metrics such as Recall@K to validate the teacher model's performance.
3. **Grid Search:**
   - The notebook performs a grid search on all combination of variables and saves the best combination based on Recall@K.
   
### 3. Changeable Parameters
- **Batch Size:** Modify `batch_size` in `DataLoader`:
```python
train_dataloader = DataLoader(train_dataset, batch_size=64, shuffle=True, num_workers=2, pin_memory=True)
```
- **Number of Epochs:** Update `num_epochs` in the training loop:
```python
num_epochs = 5
```
- **Grid Search:** Adjust any of the parameters by adding into what parameters you want to change:
```python
param_grid = {
    'learning_rate': [1e-3, 1e-4, 1e-5],
    'temperature': [0.07, 0.1],
    'alpha': [0.5, 0.1],
    'beta': [0.3, 0.7],
    'gamma': [0.3, 0.7],
}
```
- **K value:** Update the value of k for Recall@K for which the grid search compares:
```python
# Compute recall for the batch
k_val = 10 # just change this value here to whatever K you want.
recall = compute_recall_with_multiple_captions(sim_matrix.cpu(), batch_image_to_text_indices, k=k_val)
```

## Sample Output
--------------------------------------
Testing parameters: {'alpha': 0.5, 'beta': 0.3, 'gamma': 0.3, 'learning_rate': 0.001, 'temperature': 0.07}
Validation Recall@10: 0.1387
--------------------------------------
--------------------------------------
Testing parameters: {'alpha': 0.5, 'beta': 0.3, 'gamma': 0.3, 'learning_rate': 0.0001, 'temperature': 0.07}
Validation Recall@10: 0.3187
--------------------------------------
....
--------------------------------------
Best Parameters: {'alpha': 0.5, 'beta': 0.3, 'gamma': 0.3, 'learning_rate': 0.0001, 'temperature': 0.1}
Best Recall@{k_val}: 0.365234375
