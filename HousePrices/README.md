# House Prices: Advanced Regresssion Techniques

* 캐글 House Prices: Advanced Regresssion Techniques 대회의 연습용 Repository입니다
* 파이썬 머신러닝 완벽가이드(권철민) 강의를 참고하였습니다


## Description

아이오와주 에임스(Ames)에 있는 주거용 주택의 모든 측면을 설명하는 79개의 설명 변수를 통해 각 주택의 최종 가격을 예측하는 Competition

![image](https://user-images.githubusercontent.com/67913569/131615896-47e2d6a8-4d4f-463c-b930-fa32e4e5e31a.png)


## Data

* 주거용 주택의 모든 측면을 설명하는 79개의 설명 변수
* Target 값은 맨 마지막 컬럼인 SalePrice
* 80개의 변수 중 43개가 문자형, 나머지는 숫자형 변수
* 데이터의 양에 비해 Null 값이 많은 피처도 존재


## Metric: Root Mean Squared Logarithmic Error (RMSLE)

![image](https://user-images.githubusercontent.com/67913569/131610816-3e5d73ba-a11e-4634-aed0-3455f66bb481.png)


## Feature Engineering

* Target값을 정규분포 형태로 바꾸기 위해 로그변환
* Null 값이 많은 일부 변수는 삭제
* 나머지 Null 피처는 Null값이 많지 않으므로 숫자형의 경우 평균값으로 대체
* 문자형 피처는 모두 One-Hot-Encoding으로 변환
* skew함수를 통해 왜곡 정도가 1이상인 피처를 로그 변환 (연속형 변수만 해당)
* 회귀 계수가 높은 피처에 대하여 이상치 제거

## Modeling

* Linear Regression
* Ridge
* Lasso
* XGBoost
* LightGBM

