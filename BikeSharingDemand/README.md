# Bike Sharing Demand

* 캐글 Bike Sharing Demand 대회의 연습용 Repository입니다
* 파이썬 머신러닝 완벽가이드(권철민) 강의를 참고하였습니다


## Description

워싱턴 D.C.의 Capital Bikeshare 프로그램에서 자전거 대여 수요를 예측하는 Competition

![image](https://user-images.githubusercontent.com/67913569/131608645-fd0a8227-291a-4de5-bc07-0301cfa78ace.png)


## Data

* 피처 이름은 모두 익명 처리돼 이름만을 가지고 어떤 속성인지는 추정할 수 없음
* 클래스 레이블 명은 TARGET이며, 이 값이 1이면 불만을 가진 고객, 0이면 만족한 고객
* 대부분이 만족이고 불만족인 데이터가 일부

## Metric: Root Mean Squared Logarithmic Error (RMSLE)

![image](https://user-images.githubusercontent.com/67913569/131610816-3e5d73ba-a11e-4634-aed0-3455f66bb481.png)

## Feature Engineering

* var3 피처 값 대체 및 ID 피처 드롭
* NULL값 없음

## Modeling

* XGBoost
* LightGBM
  
## Hyper Parameter Tuning

* GridSearchCV를 통한 최적화
 
   - Grid search (격자 탐색) 은 모델 하이퍼 파라미터에 넣을 수 있는 값들을 순차적으로 입력한뒤에 가장 높은 성능을 보이는 하이퍼 파라미터들을 찾는 탐색 방법
