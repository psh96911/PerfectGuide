# Credit Card Fraud Detection

* 캐글 Credit Card Fraud Detection 대회의 연습용 Repository입니다
* 파이썬 머신러닝 완벽가이드(권철민) 강의를 참고하였습니다


## Description

신용카드 데이터 세트를 이용해 신용카드 사기 검출 분류 Competition

![image](https://user-images.githubusercontent.com/67913569/131335662-4b86ef87-258f-4125-922a-5523f341f072.png)

## Data

* 전체 데이터의 약 0.172%만이 레이블 값이 1, 즉 사기 트랜잭션
* 일반적으로 사기 검출(Fraud Detection)이나 이상 검출(Anomoly Detection)과 같은 데이터 세트는 레이블 값이 극도로 불균형함
* Over/UnderSampling이 필요해 보임

## Metric: ROC AUC

Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target

![image](https://user-images.githubusercontent.com/67913569/127975670-b2af66df-4bc0-4a5e-877f-72448a29daaf.png)

## Feature Engineering

* 중요 변수인 Amount변수의 분포가 심하게 skew되어 있으므로 로그변환
* Class변수와 상관관계가 가장 높은 V14변수의 이상치 데이터를 삭제
* 데이터 불균형을 해결하기 위해 SMOTE 오버 샘플링 적용

## Modeling

* Logistic Regression
* LightGBM


