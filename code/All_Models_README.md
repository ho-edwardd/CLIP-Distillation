# README: Models CLIP

## Overview
This notebook discusses all the change parameters possible in all the model based notebooks. Note, all the notebooks are meant to be run sequentially, thus, if you just go to Runtime -> Run all, everything should work smoothly. Below, we discuss some simple instructions, and all the changeable parameters across all the notebooks (some contain some or all the changeable parameters).

These include:
- Teacher_Model
- Strong_Baseline
- Simple_Baseline
- Extension_1
- Extension_2
- Sample_Output

## Instructions
### 1. Dataset Setup
- Run the first two cells to automatically download and extract the MSCOCO dataset. No manual setup is required.

### 2. Running the Notebook
- Run all cells sequentially:
  1. **Install dependencies and download the dataset.**
  2. **Define models and parameters.**
  3. **Train the student model (5 epochs by default).**
  4. **Evaluate retrieval metrics.**

### 3. Changeable Parameters
- **Batch Size:** Modify `batch_size` in `DataLoader`:
```python
train_dataloader = DataLoader(train_dataset, batch_size=64, shuffle=True, num_workers=2, pin_memory=True)
```
- **Number of Epochs:** Update `num_epochs` in the training loop:
```python
num_epochs = 5
```
- **Learning Rate:** Adjust in the optimizer:
```python
optimizer = torch.optim.Adam(parameters, lr=1e-4)
```
- **Recall@K:** Change the `k` value in evaluation:
```python
r1 = compute_recall_with_multiple_captions(sim_matrix, image_to_text_indices, k=1)
-**Temperature (Contrastive Loss):** Adjust in the loss function:
```python
def contrastive_loss(image_features, text_features, temperature=0.07)
-**alpha, beta, gamma, epsilon:** Adjust any of these extension parameters in the function contrastive_loss_with_kl_l2_pid.
```python
def contrastive_loss_with_kl_l2_pid(
    student_image_features,
    student_text_features,
    teacher_image_features,
    teacher_text_features,
    temperature=0.07,
    alpha=1.0,  # weight for KL term
    beta=0.3,   # weight for L2 term
    gamma=0.7,  # weight for synergy rewards
    epsilon=0.5  # weight for redundancy maximization
):

The above should be the only adjustable parameters in any of the notebooks I listed above. If they do not contain of these then they are meant to simply be run sequentially without anything to change (Sample_Output).


## Sample Output
### Image-to-Text Retrieval:
- Recall@1: 0.22%
- Recall@5: 0.97%
- Recall@10: 1.83%

### Text-to-Image Retrieval:
- Recall@1: 0.33%
- Recall@5: 1.39%
- Recall@10: 2.50%

