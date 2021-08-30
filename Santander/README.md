# Santander Customer Satisfaction

* 캐글 Santander Customer Satisfaction 대회의 연습용 Repository입니다
* 파이썬 머신러닝 완벽가이드(권철민) 강의를 참고하였습니다


## Description

370개의 피처로 주어진 데이터 세트 기반에서 고객 만족 여부를 예측하는 Competition

![image](https://user-images.githubusercontent.com/67913569/127973500-14408130-6566-466e-b26b-39dff02f0e8e.png)


## Data

* application: 현재대출(고객 정보와 현재 대출 정보 제공)
* previous_application: 과거대출이력(고객의 현재 대출 이전 과거 대출 정보 제공)
* bureau: 타사 대출이력(고객의 현재 대출 이전 타사 대출 정보 제공)
* bureau_bal: 타사 대출 월별 잔액(타사 대출의 월별  채무 이행 이력)
* pos_cash_balance/installments/credit_card_balance: 현금/카드대출 잔액, 납부이력(월별 현금/카드대출 잔액, 대출 채무 이행 이력)

<img src="https://user-images.githubusercontent.com/67913569/127853093-b8797cbb-2508-420c-b37c-6940e0e7c61f.png">

## Metric: ROC AUC

Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target

![image](https://user-images.githubusercontent.com/67913569/127975670-b2af66df-4bc0-4a5e-877f-72448a29daaf.png)

## Feature Engineering

* 기본 feature engineering
  - 스케일링(Scaling): StandardScaler, MinMaxScaler
  - 변환(Transformation): 로그 변환(Log Transformation), Polynomial 피처 변환, PCA 변환
  - 인코딩(Encoding): 레이블 인코딩, 원핫 인코딩
  - 결측치(Null값)/이상치(Outlier) 치환: 
  - Skew 데이터 세트 보정: 오버/언더 Sampling

* 업무적으로 중요한 feature 들의 재 결합 및 재 가공
  - 중요도가 높은 feature들에 대해서 재 가공
  - 주요 컬럼 끼리 차 또는 합, 비율 등을 재 가공
  - 주요 컬럼 및 가공 컬럼들에 대한 다양한 aggregation 적용
  - 업무적으로 의미 있는 컬럼 재 생산

* 최근 데이터, Active인 데이터 위주 필터링 후 데이터 가공
  - 시계열성 데이터의 경우 오래전 데이터 보다는 최근 데이터를 기반으로 별도의 재 가공 적용
  - 업무적으로 여전히 유효한 최근 데이터를 필터링하여 재 가공  

## Modeling

* LightGBM
  
  - LightGBM은 Leaf-wise 방식으로 Tree를 생성하므로 보다 빠르게 Tree 생성을 할 수 있음. 
  - 하지만 Leaf-wise방식은 Level-wise방식보다 더 overfitting하기 쉬움(모델 성능이 떨어지기 쉬움)
  - 이런 단점을 다양한 내부 하이퍼 파라미터와 구현 기술로 극복하면서 XGBoost 대비 학습 시간은 4배 이상 빠르지만, 모델 성능은 거의 대등한 성능을 나타냄
  - 특히 feature 개수가 수백~수천개가 되어도 성능이 크게 저하되지 않고 뛰어난 성능을 여전히 나타냄

![image](https://user-images.githubusercontent.com/67913569/128003480-b9956744-9483-451a-9e27-b58ad7be0863.png)



## Hyper Parameter Tuning

* Bayesian Optimization을 통한 최적화
  
  - Bayesian optimization은 미지의 함수가 반환하는 값의 최대값을 매우 짧은 반복을 통해서 찾아내는 최적화 방식
  - Bayesian optimization은 Gaussian process를 통해 함수의 사후 분포(posterior distribution)을 생성하고 이를 기반으로 최적화 하려는 함수를 재 구성
  - 점차 많은 입력 값을 받아서 수행하면서 사후 분포가 점점 개선 되고, 함수 반환 값을 최대(최소)되는 입력 파라미터 영역을 보다 확실하게 찾게됨

* 하이퍼 파라미터 튜닝 개요

| 트리구조 | 샘플링 비율 | 손실함수 규제 | Feature histogram |
|:---:|:---:|:---:|:---:|
| max_depth, num_leaves, min_child_samples, min_child_weight | subsample, colsample_bytree | reg_lambda, reg_alpha | max_bin |
