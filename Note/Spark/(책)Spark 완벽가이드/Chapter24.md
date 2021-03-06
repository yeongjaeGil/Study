### CHAPTER 24 고급 분석과 머신러닝 개요   
  
#### 24.1 고급 분석에 대한 짧은 입문서   
머신러닝에서 가장 일반적으로 활용되는 작업은 아래와 같다.  
1. 다양한 Feature 을 기반으로 각 샘플에 부여된 레이블을 예측하는 분류/회귀 문제를 포함한 지도 학습  
2. 사용자의 과거 행동에 기반하여 제품을 제안하는 추천 엔진  
3. 군집 분석, 이상징후 탐지, 토픽 모델링과 같이 데이터 구조를 파악하기 위한 비지도 학습  
4. 소셜 네트워크상에서 유의미한 패턴을 찾는 그래프 분석  
  
##### 25.1.1 지도 학습  
- 레이블(종속변수) 을 포함하는 포함하는 과거 데이터를 사용하여 모델을 학습시킨 후 데이터 포인트(데이터) 의 다양한 특징을 기반으로 해당 레이블값을 예측하는 것.   
- 연령을 기반으로 개인의 소득을 예측하는 것을 예로 들 수 있다.  
- 이러한 학습은 일반적으로 경사 하강법(Gradient descent)과 같은 반복적 최적화 알고리즘으로 진행된다.  
- 학습 알고리즘은 기본 모델로 시작하여 반복적으로 진행하는 학습과정에서 다양한 내부 파라미터(계수) 를 조정하면서 단계적으로 모델을 개선한다.  
- 이러한 과정을 거쳐 최종 학습 모델이 선정되고, 이 모델을 사용하여 새로운 데이터가 주어졌을 때 예측을 할 수 있게 된다.  
- 지도 학습은 예측하고자 하는 변수의 타입에 따라 분류와 회귀로 구분할 수 있다.  
	- 분류  
	a. 지도 학습의 가장 일반적인 유형은 분류이다.  
	b. 분류란 범주형(분연속적이고 유한한 값의 집합) 종속변수를 예측하는 알고리즘을 학습시키는 행위이다.   
	c. 가장 일반적인 분류는 주어진 항목을 예측할 때 반드시 두 그룹 중 하나에 속한다고 예측하는 이진 분류이며, 대표적인 사례는 바로 스팸메일 분류이다.  
	d. 이러한 작업을 하기 위해서, 스팸인지 아닌지 여부가 식별된 과거 이메일 이력 데이터를 수집하고 해당 이메일이 포함하고 있는 단어와 다양한 속성을 분석하여 궁극적으로 스팸인지 아닌지 여부를 예측하는 알고리즘을 학습시킨다.  
	e. 항목을 세 가지 이상의 범주로 분류하는 경우를 다중 클래스 분류라고 한다.  
	- 회귀  
	a. 분류에서 종속변수가 불연속 값들의 집합이라면, 회귀는 연속형 변수(실수) 를 예측한다.  
	- 범주가 아닌 숫자값을 예측하는 것이다.  
  
##### 24.1.2 추천  
- 추천은 고급 분석에서 가장 직관적인 응용 영역 중 하나이다.  
- 다양한 제품이나 아이템에 대한 사람들의 명시적인 선호도(등급을 이용해)나 암시적인 선호도(관찰된 행동을 이용해)를 연구함으로써 알고리즘은 사용자 또는 아이템 간의 유사성을 도출하여 사용자가 선호할 만한 추천 아이템을 도출해낸다.  
- 추천 알고리즘은 이러한 유사성을 기반으로 특정 사용자와 유사한 사용자가 선호하는 상품이나 특정 사용자가 이미 구매한 상품과 비슷한 상품을 추천하게 된다.  
- 추천은 스파크의 대표적인 활용사례이자 빅데이터에 최적화된 주제이다.  
  
##### 24.1.3 비지도 학습  
- 비지도 학습은 주어진 데이터셋에서 특정 패턴을 찾거나 숨겨진 구조적 특징을 발견하는 행위이다.  
- 예측 대상이 되는 종속변수(레이블) 가 필요 없다는 것이 지도학습과 큰 차이점이다.  
  
##### 24.1.4 그래프 분석  
- Vertex, Edge 를 지정하는 구조에 대한 연구이다.  
- 예를 들어 정점은 사람과 상품을 나타내며, 에지는 구매를 나타낸다.  
  
##### 24.1.5 고급 분석 프로세스  
* 머신러닝 워크플로  
![image](https://user-images.githubusercontent.com/4033129/82756415-22965200-9e15-11ea-850c-9cbda8d505ac.png)  
	1. 분석 주제와 관련된 데이터를 수집한다.  
	2. 데이터 파악을 위해 데이터를 정제하고 검토한다.  
	3. 알고리즘이 데이터를 잘 인식하고 활용할 수 있도록 Feature Engineering 을 수행한다.( 데이터를 수치형 벡터로 변환 )  
	4. 후보 모델을 생성하는 하나 이상의 알고리즘을 학습시키기 위해 전체 데이터의 일부를 학습 데이터셋으로 사용한다.  
	5. 생성된 모델을 동일한 데이터에서 학습에 사용되지 않은 부분에 적용해 그 결과를 객관적으로 측정하고 분석 수행 시 정해 놓은 성공 기준과 비교하여 해당 모델을 최종 평가한다. 이를 통해 도출한 모델이 실세계에서 어느 정도의 성과를 낼지 더 잘 이해할 수 있다.  
	6. 앞의 과정을 거치면서 확보한 통찰력 및 모델을 상요하여 예측을 수행하거나 이상 현상을 감지하고, 더 일반적인 비즈니스 문제를 해결할 수 있다.  
  
	* 데이터 수집  
	* 데이터 정제  
		- 탐색적 데이터 분석(Exploratory Data Analysis, EDA)  
		- EDA는 일반적으로 대화형 쿼리 및 시각화 방법 등을 사용하여 데이터의 분포, 상관관계 및 기타 세부 현황을 파악하는 과정을 의미한다.  
		- 이 과정에서 수집 서버에 잘못 기록되어 삭제해야 하는 값이나 누락된 값이 무엇인지 파악할 숭 ㅣㅆ다.  
		- 어떤 경우이든 간에 오류를 방지하기 위해서는 분석하고자 하는 데이터를 사전에 명확히 파악해야 한다.  
	* 피처 엔지니어링  
		- 머신러닝 알고리즘에 적용 가능한 형식으로 데이털르 변환해야 한다.  
		- 데이터 정규화 > 다른 변수들과의 상호작용을 나타내는 새로운 변수 추가 > 범주형 변수 조작 및 머신러닝 모델에서 인식할 수 있도록 적절한 형식으로의 변환 작업이 필요하다.  
		- 스파크에서는 double 형 벡터로 입력되어야 한다.  
	* 모델 학습  
		- 과거 정보 데이터셋과 분석 목적이 주어지고, 입력을 받았을 때 그게 적합한 출력을 예측하는 모델을 학습시킨다.  
		- 모델 학습 과정에서 입력 데이터에 대해 모델이 얼마나 잘 동작하는지에 따라 모델 내부 파라미터가 달라질 수 있다.  
		- 최종 목적은 단순히 모델을 학습시키는 것이 아니라 그것을 활용해서 통찰력을 얻는 것이다. 따라서 모델이 본래 목적에 적합한 성능을 내는지 사전에 파악하는 것이 중요하며 이는 모델 튜닝과 평가로 수행할 수 있다.  
	* 모델 튜닝 및 평가  
		- 데이터를 여러 개로 나누어 그 중 하나의 데이터셋을 모델 학습용으로 사용해야 한다.  
		- 고급 분석 모델을 개발할 때 새로운 데이터에 대해서도 일반화 가능한 모델을 생성해야 하기 때문이다.  
		- 데이터를 여러 개로 나누는 것은 새로운 데이터에 대해 학습 모델의 효과성을 객관적으로 테스트할 수 있게 한다.  
		- 이를 통해 모델이 주어진 데이터셋의 기본적인 특성을 제대로 반영하고 있는지 또는 학습 데이터셋에만 특화되는 현상, 즉 새로운 데이터에 일반화되지 않는 과적합 현상이 발생하는지 여부를 확인할 수 있다.  
		- 이러한 테스트를 위해 사용하는 데이터셋을 보통 테스트셋이라고 한다.  
		- 이 데이터셋을 활용하여 학습에 영향을 주는 다양한 하이퍼 파라미터를 시험해보고 변형된 모델의 적합성을 테스트해야 한다.  
		- 이것을 검증셋이라고 하며, 이는 또 다른 형태의 테스트셋이다.  
  
#### 24.2 스파크의 고급 분석 툴킷   
##### 24.2.1 MLlib 이란  
* MLlib 은 언제 그리고 왜 사용해야 할까  
	1. 스파크로 데이터를 전처리하고 특징을 생성하여 대량의 데이터로부터 학습 및 테스트를 위한 데이터셋 생성에 걸리는 시간을 줄인 후 단일 머신 기반의 학습 라이브러리를 활용하여 주어진 데이터셋을 학습할 수 있다.  
	2. 입력 데이터나 모델 크기가 단일 머신에 올려놓기 너무 어렵거나 불편할 경우 스파클르 사용하여 분산 처리 기반의 머신러닝을 간단히 수행할 수 있다.  
  
#### 24.3 고수준 MLlib의 개념   
* 스파크에서의 머신러닝 워크플로우  
![image](https://user-images.githubusercontent.com/4033129/82756995-97b75680-9e18-11ea-8a4b-cbac1ce83a38.png)  
  
MLlib 에는 변환자, 추정자, 평가기, 파이프라인과 같은 구조적 유형이 있다.  
* 변환자  
	- 원시 데이터를 다양한 방식으로 변환하는 함수이다.  
	- 이는 새로운 상호작용 변수를 생성하거나, 컬럼을 정규화하거나, Integer 를 모델에 입력하기 위해서 Double 타입으로 ㅂ녀경하는 것 등이 될 수 있다.  
	![image](https://user-images.githubusercontent.com/4033129/82757035-da792e80-9e18-11ea-83e0-3e11d0a09e12.png)  
  
* 추정자  
	1. 데이터를 초기화하는 일종의 변환자를 의미한다.(통계학에서의 확률변수와 같은 개념인 추정량(Estimator) 을 의미한다.) 예를 들어 수치형 데이터를 정규화하려면 정규화하려는 컬럼의 현잿값 정보를 사용하여 변환을 초기화해야 한다. 이 과정에서는 데이터를 두 번 토오가시켜야 한다. 첫 번째 과정에서 초깃값을 생성하고, 두 번째 과정에서 생성된 함수를 데이터에 실제로 적용하게 된다.  
	2. 스파크에서는 사용자가 데이터로부터 모델을 학습시키기 위해 사용하는 알고리즘 역시 추정자라고 한다.  
  
* 평가기  
	- 주어진 모델의 성능이 수신사 조작 특성(Receiver Operating Characteristic, ROC) 고선 처럼 지정한 기준에 따라 어떻게 작동하는지 볼 수 있게 해준다.  
	- 평가기를 사용하여 테스트한 모델 중에서 가장 우수한 모델을 선택한 후 그 모델을 사용하여 최족 예측을 할 수 있다.  

#### 24.4 MLlib 실제로 사용하기   
  
#### 24.5 모델 배포 방식   
![image](https://user-images.githubusercontent.com/4033129/82757136-7c008000-9e19-11ea-9c1b-efe5e67d95c2.png)


#### 24.6 정리 
