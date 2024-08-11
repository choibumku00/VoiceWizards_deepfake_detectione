# VoiceWizards_deepfake_detectione
SW중심대학에서 진행한 디지털 경진대회(2024) AI부분: 가짜음성탐지  
**※ 데이터는 제공하지 않습니다.**  

대회에서 제공된 데이터(open.zip)를 압축해제 후, 제출 파일도 같은 경로에 압축을 해제 해야 함  
  
---
## **코드**
- **data_augment.ipynb**  
Train 데이터 셋에서 test 셋과 비슷하게 만들기 위한 데이터 증강 코드  
코드 실행은 되나 랜덤 시드가 설정 안돼 있기 때문에 train 데이터가 변할 수 있음  
우리가 실험한 train 데이터를 사용하기 위해서는 압축을 푼 폴더에 ‘train_augmented1’폴더와 ‘train_augmented3’폴더 속 데이터를 그대로 사용해야지 재현이 가능  
- **training_clean_AASIST.ipynb**  
training을 위한 코드  
data_augment.ipynb에서 데이터 증강을 다시 했다면 우리의 실험과 달라지기 때문에 다소 점수 차이가 발생할 수 있음  
코드를 정상적으로 실행하기 위해 젤 위에 코드 셀인 git clone 명령어가 실행 되어야함  
- **inference_clean_AASIST.ipynb**  
inference를 위한 코드  
training_clean_AASIST.ipynb에서 git clone이 실행됐다고 가정  
가끔 test 데이터와 CleanUNet이 충돌이나서 파일이 nan 값을 가질때가 있음 그경우 아래의 코드에 빈 리스트가 출력이 안되는데, 이럴 경우 test 데이터를 다시 불러와야함 (대부분의 경우 문제가 발생하지 않음)  
 
## **weight 파일**
파일명: **clean_aasist7_18_3.pth**  
inference_clean_AASIST.ipynb 코드에서 불러온다.  
CleanUNet의 weight는 git clone으로 training_clean_AASIST.ipynb에서 가져옴.  
CleanUNet이 출력을 매번 조금씩 다르게 주는 것 같아, 점수가 다소 다를 수 있음  

## **사용한 사전 학습 모델 출처**
- **CleanUNet**  
코드에서 git clone을 통해 가져온다. 사전 학습 파라미터도 코드안에서 접근  
출처: https://github.com/NVIDIA/CleanUNet  
논문: https://arxiv.org/abs/2202.07790  
- **AASIST**  
https://github.com/clovaai/aasist/blob/main/models/weights/AASIST.pth 에서 다운로드  
(따로 다운로드 필요없이 압축 파일에 존재, 위 링크 파일과 동일)  
출처: https://github.com/clovaai/aasist  
논문: https://arxiv.org/abs/2110.01200  
 
## **개발 환경**
Google colab pro+ 환경에서 실행  
-	Gpu = A100  
**github 코드는 Colab환경이 아니더라도 로컬에서 가능하도록 수정하여 업로드됨**  
라이브러리: requirements.txt 파일에 기재
