# 4th_paper_latest_V1

## V23으로 우선적으로 인식 진행
* DIscriminator - Local attention map 을 활용

* Class imbalance 문제 해결 ( ![수식](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20%5Cbg_black%20%5Cinline%20MAX(%5Cfrac%7BClass_n%7D%7BClass_t%7D)%20-%20(%5Cfrac%7BClass_n%7D%7BClass_t%7D)&plus;1%5Cfrac%7B%7D%7B) )

* Encoder 앞단은 pre-trained by imagenet weights 사용

* Target domain attention map 설계 (  ![수식](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20%5Cbg_black%20%5Cinline%20I=%5Cfrac%7Bx-%5Ctheta%20%7D%7BMAX(%5Csigma%20%5Cfrac%7B1.0%7D%7B%5Csqrt%7BN%7D%7D)), 
![수식](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20%5Cbg_black%20%5Cinline%20I=%5Cfrac%7B1%7D%7BN%7D%5Csum_%7B%7D%5E%7B%7D(%5Cfrac%7B1%7D%7BMAX(I)%7D&plus;MEAN(I)&plus;0.2))  )

* Generator에서 age loss 계산

* Adative training dataset 적용

## V24는 ablation study 로 예상 (이전 버전들도 포함할 것)

* DIscriminator - Local attention map 을 활용

* Class imbalance 문제 해결 ( ![수식](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20%5Cbg_black%20%5Cinline%20MAX(%5Cfrac%7BClass_n%7D%7BClass_t%7D)%20-%20(%5Cfrac%7BClass_n%7D%7BClass_t%7D)&plus;1%5Cfrac%7B%7D%7B) )

* Encoder 앞단은 pre-trained by imagenet weights 사용

* Target domain attention map 설계 (  ![수식](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20%5Cbg_black%20%5Cinline%20I=%5Cfrac%7Bx-%5Ctheta%20%7D%7BMAX(%5Csigma%20%5Cfrac%7B1.0%7D%7B%5Csqrt%7BN%7D%7D)), 
![수식](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20%5Cbg_black%20%5Cinline%20I=%5Cfrac%7B1%7D%7BN%7D%5Csum_%7B%7D%5E%7B%7D(%5Cfrac%7B1%7D%7BMAX(I)%7D&plus;MEAN(I)&plus;0.2))  )

* Generator에서 age loss 계산

* Adative training dataset 적용

* GAN 특성 중 생성된 이미지들의 패턴과 원본 이미지들의 패턴이 다르다는것이 실험적으로 입증됨 [1]. 그래서 위 처럼 원본 이미지들의 attention map 과 모든 생성된 이미지에 대한 attention map이 각각 고유한 패턴이라고 가정하고, loss 설계. ( [1] GANprintR: Improved Fakes and Evaluation of the State of the Art in Face Manipulation Detection )
  * 이 loss는 200 iterations 마다 학습되도록 설계하였음 (이유: 매 학습마다 생성된 모든 이미지들의 attention map을 구하는것은 학습에 소모되는시간이 많아지고, 생성되는 이미지의 blur가 심해질것으로 예상되기 때문)

## 모델을 아래와 같이 동일하게 설계

![그림](https://github.com/Kimyuhwanpeter/4th_paper_latest_V1/blob/main/f1.png)
<br/>

![그림](https://github.com/Kimyuhwanpeter/4th_paper_latest_V1/blob/main/f2.png)

## V24 training samples

![그림](https://github.com/Kimyuhwanpeter/4th_paper_latest_V1/blob/main/f3.png)
<br/>

## 실험 예정

* **(Morph train set)  WM ↔ BM style transform 실험 중**

* **(Morph train set) WF ↔ BM style transform 실험 중**

* (Morph train set) BF ↔ BM style transform 실험 예정

* (Morph test set) WM ↔ BM style transform 실험예정

* (Morph test set) WF ↔ BM style transform 실험예정

* (Morph test set) BF ↔ BM style transform 실험예정

* 1번에서 7번 실험이 끝난 후 인종 및 성별 인식 및 나이 추정 실험 예정

