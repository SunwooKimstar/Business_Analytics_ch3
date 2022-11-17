# Business_Analytics_ch3

# **Anomaly Detection**

## 📂 Contents
-----------------------------
* Background
* Steps
* Dataset
* Result
* Analysis

### :pushpin: Background 
-----------------------------

* Isolation Forests
- 하나의 객체를 고립시키는 tree를 생성하자는 아이디어 이용
- 정상 데이터를 고립시키는 분기(split)수 > 이상치 데이터를 고립시키는 분기(split)수 임을 이용
- **정상 데이터** : tree의 말단 노드에 가까운 depth를 가짐
- **이상치 데이터** : root 노드에 가까운 depth를 가짐
- **outlier score** : 특정 한 개체가 isolation 되는 leaf 노드 (terminal 노드)까지의 거리

#### 🌳 Isolation Forest의 전체적인 과정
------
#### iTree
1. Sub-sampling : 비복원 추출로 데이터 중 일부 샘플링
2. 변수선택 : 데이터 x의 변수 중 q개를 임의로 선택
3. split point 설정 : 변수 q의 범위(min~max) 중 uniform하게 split point를 선택
4. 1~3번의 과정을 모든 관측치가 split되거나 임의의 split 횟수에 도달할 때까지 반복, 경로 길이를 모두 저장
#### Isolation Forest
5. 1~4의 과정(iTree)을 여러번 반복

#### 🌲 Isolation Forest의 특징
- **sub-sampling** : sampling한 데이터로 모델을 구성함
- **swamping** : 정상과 이상치 데이터가 가까이 위치하게 되는 경우 잘못 분류를 하게 됨
- **masking** : 이상치가 군집화 되어 있어 정상으로 잘못 분류하게 됨
- **high dimensional data** : 고차원의 데이터에서는 잘 동작하지 않을 수 있음

### :pushpin: Steps 
-----------------------------
* Step 1 : 데이터셋 생성 또는 불러오기
* Step 2 : Model fit
* Step 3 : 이상치 예측
* (Step 4 : 결과 시각화)

### :pushpin: Dataset 
-----------------------------
* make_blobs 함수 이용하여 임의의 데이터셋 생성
* Image Data : load_digits 함수 이용
* Synthetic Financial Datasets For Fraud Detection [download](https://www.kaggle.com/datasets/ealaxi/paysim1)

### :bar_chart: Result
-----------------------------
|Accuracy|Recall|Precision|F1-score|
|:--:|:--:|:--:|:--:|
|98|78|62|55|

### 📊 Analysis
------------------------------

위와 같이 정상(1)로 예측되는 경우 파란색으로, 이상치(-1)로 예측되는 경우는 빨간색으로 시각화합니다. cluster의 중심에 가까운 점들의 경우 정상으로 표시되고, cluster에서 벗어난 점들의 경우 이상치로 표시되는 것을 확인할 수 있습니다. Isolation Forest의 개념 자체와 연관시켜 생각해보면, cluster의 중심에 있는 점들의 경우에는 고립시키는데 많은 수의 분기(split)가 필요하기 때문에 정상으로 탐지하고, cluster의 외부에 있는 점들의 경우는 고립시키는데 비교적 적은 수의 분기(split)가 필요하기 때문에 이상치라고 할 수 있습니다. 

이번에는 anomaly score 값들을 시각화 해보도록 하겠습니다. score값이 높으면 빨간색으로, score값이 낮으면 파란색으로 표기되게 하였습니다. 즉, score값이 높을수록 이상치에 가깝다고 볼 수 있습니다. 위의 결과에서 정상이라고 판단되는 경우 (파란색 부분) 이라고 할 수 있으며, 이상치로 판단되는 경우 (빨간색 부분) 이라고 할 수 있습니다. cluster의 중심에 가까울수록 anomaly score의 값이 낮고, 중심에서 멀리 떨어져 있을수록 일반적으로 anomaly score값이 크다는 점을 알 수 있습니다. 추가적으로 위의 일반적인 데이터 분포 그림과 비교하여 보았을 때, 약 0.5 정도의 값을 기준으로 하여 정상과 이상치가 나뉘고 있음을 확인할 수 있습니다.

### 📂 References
------------------------------
* https://github.com/pilsung-kang/Business-Analytics-IME654-
