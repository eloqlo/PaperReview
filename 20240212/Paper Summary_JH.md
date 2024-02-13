# Depth Anything: Unleashing the Power of Large-Scale Unlabeled Data
- Year: 2024
- Area: Computer Vision/Depth Estimation

## Research Motivation
최근 NLP, Computer Vision등의 연구 분야에서, 대량의 데이터를 기반으로 정보를 학습한 foundation model들이 다양한 downstream task에서 좋은 zero/few-shot 성능을 보이고 있다. 
하지만 Monocular Depth Estimation task(이하 MDE)의 경우, 수많은 데이터들의 depth를 라벨링 하는 것이 쉽지 않기 때문에 이러한 foundation model을 만드는게 어려웠다. 
비슷하게 많은 데이터를 활용한 이전 접근인 [MiDaS(2020)](https://arxiv.org/abs/2307.14460) 연구에서는, 서로 다른 방식으로 라벨링 된 depth 데이터셋들을 동시에 학습시키는 loss를 제안해 MDE 성능을 크게 향상시켰다. 
하지만, 약 2M장의 학습 이미지를 사용한 MiDaS도 400M장의 학습 이미지를 사용한 [CLIP(2021)](https://arxiv.org/abs/2103.00020)등의 Large-Vision Model에 비하면 충분히 많은 학습 데이터를 봤다고 말하긴 어렵다. 

따라서, 해당 연구는 기존 MDE 연구들의 한계를 적은 데이터셋으로 보고, unlabeled data들을 활용한 semi-supervised learning으로 데이터셋의 크기를 키우는 접근으로 MDE를 위한 foundation model을 만들어 보고자 하였다.

## Approaches to make foundation model
### 1. Using unlabeled images
해당 연구는 많은 데이터를 활용해 접근한 [MiDaS(2020)](https://arxiv.org/abs/2307.14460)을 baseline으로 unlabeled data를 추가적으로 활용하는 방향으로 수행된다.  

#### 학습 데이터
- labeled 데이터셋의 경우 BlendedMVS(115K images), DIML(927K), HRWSI(20K), IRS(103K), MegaDepth(128K), TartanAir(306K) 총 6개의 1.5M개의 이미지 데이터를 사용한다.
- unlabeled 데이터셋으론 BDD100K(8.2M), Google Landmarks(4.1M), ImageNet-21K(13.1M), LSUN(9.8M), Objects365(1.7M), Open Images V7(7.8M), Places365(6.5M), SA-1B(11.1M) 총 62M개의 이미지 데이터를 사용한다.

#### 학습 방식
- Teacher Model의 학습 방식으론 MiDaS의 학습방식을 활용해 unlabeled data에 대한 pseudo label 들을 생성한다.
- Student Model은 labeld data와 pseudo labeled data를 섞어서 학습하는데, 이 학습 방식은 [ST++](https://openaccess.thecvf.com/content/CVPR2022/papers/Yang_ST_Make_Self-Training_Work_Better_for_Semi-Supervised_Semantic_Segmentation_CVPR_2022_paper.pdf)의 학습방식을 따른 것 이다.
여기서 ST++는 Monocular Depth Estimation이 아닌 semantic segmentation 관련 연구인데, large scale unlabeled data를 활용한 MDE연구가 이뤄지지 않았기 때문에 다른 task의 학습방식을 참조했다고 저자는 밝힌다.

##### 구체적인 학습 방식: Training Teacher Model
pass
##### 구체적인 학습 방식: Training Student Model
pass

### 2. Semantic assisted perception


## Results

## Conclusion

## Discussion

