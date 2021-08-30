# Santander Customer Satisfaction

* 캐글 Santander Customer Satisfaction 대회의 연습용 Repository입니다
* 파이썬 머신러닝 완벽가이드(권철민) 강의를 참고하였습니다


## Description

370개의 피처로 주어진 데이터 세트 기반에서 고객 만족 여부를 예측하는 Competition

![image](https://user-images.githubusercontent.com/67913569/131330421-2ba8a012-dff2-4828-893e-a4e0d0375429.png)


## Data

* 피처 이름은 모두 익명 처리돼 이름만을 가지고 어떤 속성인지는 추정할 수 없음
* 클래스 레이블 명은 TARGET이며, 이 값이 1이면 불만을 가진 고객, 0이면 만족한 고객
* 대부분이 만족이고 불만족인 데이터가 일부

## Metric: ROC AUC

Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target

![image](https://user-images.githubusercontent.com/67913569/127975670-b2af66df-4bc0-4a5e-877f-72448a29daaf.png)

## Feature Engineering

* var3 피처 값 대체 및 ID 피처 드롭
* NULL값 없음

## Modeling

* XGBoost
* LightGBM
  
## Hyper Parameter Tuning

* GridSearchCV를 통한 최적화
 
 - Grid search (격자 탐색) 은 모델 하이퍼 파라미터에 넣을 수 있는 값들을 순차적으로 입력한뒤에 가장 높은 성능을 보이는 하이퍼 파라미터들을 찾는 탐색 방법
