# House Prices: Advanced Regresssion Techniques

* 캐글 House Prices: Advanced Regresssion Techniques 대회의 연습용 Repository입니다
* 파이썬 머신러닝 완벽가이드(권철민) 강의를 참고하였습니다


## Description

아이오와주 에임스(Ames)에 있는 주거용 주택의 모든 측면을 설명하는 79개의 설명 변수를 통해 각 주택의 최종 가격을 예측하는 Competition

![image](https://user-images.githubusercontent.com/67913569/131615896-47e2d6a8-4d4f-463c-b930-fa32e4e5e31a.png)


## Data

* 2011년 1월부터 2012년 12월까지 날짜/시간, 기온, 습도, 풍속 등의 정보를 기반으로 1시간 간격 동안의 자전거 대여 횟수가 기재되어 있음
* 결정 값은 맨 마지막 컬럼인 count로 '대여 횟수'를 의미함

## Metric:  Root-Mean-Squared-Error (RMSE)



## Feature Engineering

* Datetime 변수를 년, 월, 일, 시간과 같이 4개의 속성으로 분리
* Target값을 정규분포 형태로 바꾸기 위해 로그변환
* 범주형 변수를 One-Hot-Encoding

## Modeling

* Random Forest
* GBM
* XGBoost
* LightGBM

