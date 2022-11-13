# Business_Analytics_ch3

# **Anomaly Detection**

## 📂 Contents
-----------------------------
* Background
* Dataset
* Result
* Analysis

-----------------------------
### :pushpin: Background
* Gaussian Density-based Anomaly Detection
- 모든 데이터는 1개의 gaussian 분포에서 생성되었음을 가정함

* LoF
- 분포를 추정하는 방식이 아닌 단순히 주변부 데이터의 밀도를 고려하여 이상치 스코어를 산출함

* Auto-Encoder
- [이상치 탐지] : 입력과 재구축된 결과 사이의 차이를 이용함

* Support Vector-based Anomaly Detection
- 1- SVM : 원점에서 가장 멀리 떨어진 hyperplane의 boundary를 찾음
- SVDD : 정상데이터를 감싸는 최소 반지름을 가지는 최적의 구를 찾음

* Isolation Forests
- 하나의 객체를 고립시키는 tree를 생성하자는 아이디어로 진행함
- 정상 데이터와 이상치 데이터를 고립시키는데 필요한 분기 수가 다를 것임을 이용함