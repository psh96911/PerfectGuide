# Bike Sharing Demand

* 캐글 Bike Sharing Demand 대회의 연습용 Repository입니다
* 파이썬 머신러닝 완벽가이드(권철민) 강의를 참고하였습니다


## Description

워싱턴 D.C.의 Capital Bikeshare 프로그램에서 자전거 대여 수요를 예측하는 Competition

![image](https://user-images.githubusercontent.com/67913569/131608645-fd0a8227-291a-4de5-bc07-0301cfa78ace.png)


## Data

* 2011년 1월부터 2012년 12월까지 날짜/시간, 기온, 습도, 풍속 등의 정보를 기반으로 1시간 간격 동안의 자전거 대여 횟수가 기재되어 있음
* 결정 값은 맨 마지막 컬럼인 count로 '대여 횟수'를 의미함

## Metric: Root Mean Squared Logarithmic Error (RMSLE)

![image](https://user-images.githubusercontent.com/67913569/131610816-3e5d73ba-a11e-4634-aed0-3455f66bb481.png)

## Feature Engineering

* Datetime 변수를 년, 월, 일, 시간과 같이 4개의 속성으로 분리
* Target값을 정규분포 형태로 바꾸기 위해 로그변환
* 범주형 변수를 One-Hot-Encoding

## Modeling

* Random Forest
* GBM
* XGBoost
* LightGBM
