# VoiceWizards Deepfake Detection
**2024 Digital Competition (AI Category) hosted by the SW-Oriented University Program: Fake Voice Detection**  
**[Public Rank 11, Private Rank 11] - VoiceWizards Team**

**※ Data is not provided in this repository.**

<br>

## Model Flowchart
![image](https://github.com/user-attachments/assets/f770382a-443f-46b2-993d-cda5b57d3d8b)

<br>

## **Code**
After extracting the provided data (open.zip), the submission files should also be extracted in the same directory.

- **data_augment.ipynb**  
  Code for augmenting the train dataset to make it similar to the test set.  
  While the code runs, the random seed is not set, so the train data might change.  
  To reproduce our experiment, you must use the data inside the 'train_augmented1' and 'train_augmented3' folders as they are after extraction.
  
- **training_clean_AASIST.ipynb**  
  Code for training.  
  If data augmentation is redone in data_augment.ipynb, the results may differ from our experiment, leading to some score differences.  
  The first code cell, which includes the git clone command, must be executed for the code to run properly.
  
- **inference_clean_AASIST.ipynb**  
  Code for inference.  
  It assumes that git clone has been executed in training_clean_AASIST.ipynb.  
  Occasionally, there is a conflict between the test data and CleanUNet, causing files to contain NaN values. In such cases, the code below may not output an empty list, and you will need to reload the test data (this issue rarely occurs).

<br>

## **Weight File**
Filename: **clean_aasist7_18_3.pth**  
It is loaded in the inference_clean_AASIST.ipynb code.  
The CleanUNet weights are fetched via git clone in training_clean_AASIST.ipynb.  
Since CleanUNet sometimes produces slightly different outputs, the scores may vary slightly.

<br>

## **Pretrained Models Used**
- **CleanUNet**  
  Retrieved via git clone in the code. Pretrained parameters are also accessed within the code.  
  Source: https://github.com/NVIDIA/CleanUNet  
  Paper: https://arxiv.org/abs/2202.07790  
  
- **AASIST**  
  Downloaded from https://github.com/clovaai/aasist/blob/main/models/weights/AASIST.pth  
  (No need to download separately; the file is included in the zip and is identical to the link)  
  Source: https://github.com/clovaai/aasist  
  Paper: https://arxiv.org/abs/2110.01200  

<br> 

## **Development Environment**
Executed in Google Colab Pro+ environment  
- Gpu = A100  
**The GitHub code has been modified to work on local environments as well, not just in Colab.**  
Libraries: Listed in the requirements.txt file
