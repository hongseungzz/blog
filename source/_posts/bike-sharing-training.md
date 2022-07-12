---
title: "Bike Sharing Demand Training"
output:  
  html_document:
    toc: true
    toc_float: true
    keep_md: true
date: '2022-07-08 09:22:22'
---


# 양식을 강사님께서 주실 예정
- 날짜
- 수강생 이름


```python
# This Python 3 environment comes with many helpful analytics libraries installed
# It is defined by the kaggle/python Docker image: https://github.com/kaggle/docker-python
# For example, here's several helpful packages to load

import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)

# Input data files are available in the read-only "../input/" directory
# For example, running this (by clicking run or pressing Shift+Enter) will list all files under the input directory

import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))

# You can write up to 20GB to the current directory (/kaggle/working/) that gets preserved as output when you create a version using "Save & Run All" 
# You can also write temporary files to /kaggle/temp/, but they won't be saved outside of the current session
```

# chapter 01. 필수 라이브러리 불러오기
## ※ 필수 라이브러리를 불러오는 작업
- 데이터 가공을 위한 Pandas
- 수치 연산을 위한 Numpy
- 시각화를 위한
    matplotlib
    seaborn
- 머신러닝 기본 라이브러리인 sklearn
    + 이후 머신러닝 모델 라이브러리는 그때마다 입력


```python
import pandas as pd   # 데이터 가공
import numpy as np    # 수치 연산
import matplotlib as mpl           # 시각화
import matplotlib.pyplot as plt    # 시각화
import seaborn as sns              # 시각화
import sklearn   # 머신러닝
# pyplot은 matplotlib 안에 속한 클래스이므로 따로 버전 확인을 할 필요가 없음

print("pandas version : ", pd.__version__)
print("numpy version : ", np.__version__)
print("matplotlib version : ", mpl.__version__)
print("seaborn version : ", sns.__version__)
print("sklearn version : ", sklearn.__version__)
```

# Chapter 02. 데이터 불러오기




```python
DATA_PATH = '/kaggle/input/bike-sharing-demand/'
train = pd.read_csv(DATA_PATH + 'train.csv')   # 훈련 데이터
test = pd.read_csv(DATA_PATH + 'test.csv')     # 테스트 데이터
submission = pd.read_csv(DATA_PATH + 'sampleSubmission.csv')

train.shape, test.shape, submission.shape
```

## 데이터 확인


```python
print(train.head(10))
train.info()
```


```python
print(test.head(10))
test.info()
```

## 결측치
- 현재 판단으로는 결측치가 없어 보임

# Chapter 03. 탐색적 자료 분석
- 시각화
- 날짜 기반 데이터
- train 데이터를 다이렉트로 변화를 주면 전처리 시 헷갈림
- 복제본 뜨기 (탐색적 자료 분석)
- 데이터 셋이 매우 작다면
    + 전체를 다 써도 큰 상관 없음
    + But, 데이터 셋이 크다면 전체 데이터에서 일부 샘플링 


```python
# 원본이 망가질 우려가 있어 복제본을 뜬다
temp_train = train.copy()
temp_train.info()
```

- 시각화를 위한 날짜 데이터 처리
- 연도, 월, 일, 시간, 분, 초


```python
temp_train['datetime'][:10]
```


```python
print(temp_train['datetime'][0].split()[1])
print(temp_train['datetime'][0].split()[1].split(':')[0])
```


```python
year = temp_train['datetime'][100].split()[0].split('-')[0]
month = temp_train['datetime'][100].split()[0].split('-')[1]
day = temp_train['datetime'][100].split()[0].split('-')[2]
hour = temp_train['datetime'][100].split()[1].split(':')[0]
minutes = temp_train['datetime'][100].split()[1].split(':')[1]
seconds = temp_train['datetime'][100].split()[1].split(':')[2]


year, month, day, hour, minutes, seconds
```


```python
temp_train['date'] = temp_train['datetime'].apply(lambda x : x.split()[0])
# apply 메서드 : 반복문 코드를 안 써도 반복문 효과를 주는 메서드
temp_train['date']
```

- 시간 데이터 전처리 방법론 (1)


```python
import time
import datetime

# 시간 테스트
start_time = time.time()

temp_train['year'] = temp_train['datetime'].apply(lambda x : x.split()[0].split('-')[0])
temp_train['month'] = temp_train['datetime'].apply(lambda x : x.split()[0].split('-')[1])
temp_train['day'] = temp_train['datetime'].apply(lambda x : x.split()[0].split('-')[2])
temp_train['hour'] = temp_train['datetime'].apply(lambda x : x.split()[1].split(':')[0])
temp_train['minutes'] = temp_train['datetime'].apply(lambda x : x.split()[1].split(':')[1])
temp_train['seconds'] = temp_train['datetime'].apply(lambda x : x.split()[1].split(':')[2])

# temp_train[['year', 'month', 'day']]
# temp_train[['hour', 'minutes', 'seconds']]

end_time = time.time()
lambda_ctime = end_time - start_time

print("실행시간(second) : ", np.round(lambda_ctime, 3))
temp_train[['datetime', 'year', 'month', 'day', 'hour', 'minutes', 'seconds']]
```

- 시간 데이터 전처리 방법론 (2)


```python
temp_train['date'] = pd.to_datetime(temp_train['datetime'])
temp_train['year'] = temp_train['date'].dt.year
temp_train['year']
```


```python
import time
import datetime

# 시간 테스트
start_time = time.time()

temp_train['date'] = pd.to_datetime(temp_train['datetime'])
temp_train['year'] = temp_train['date'].dt.year
temp_train['month'] = temp_train['date'].dt.month
temp_train['day'] = temp_train['date'].dt.day
temp_train['hour'] = temp_train['date'].dt.hour
# temp_train[['year', 'month', 'day']]
# temp_train[['hour', 'minutes', 'seconds']]

end_time = time.time()
lambda_ctime = end_time - start_time

print("실행시간(second) : ", np.round(lambda_ctime, 3))
temp_train[['datetime', 'year', 'month', 'day', 'hour']]
```

- 요일 추출하기


```python
temp_train['date']
```


```python
temp_train['weekday'] = temp_train['date'].dt.day_name()
temp_train['weekday']
```

- 계절 문자로 변환


```python
temp_train['season'] = temp_train['season'].map({
    1 : 'Spring',
    2 : 'Summer',
    3 : 'Fall',
    4 : 'Winter'    
})
temp_train['season']
```


```python
temp_train['weather'] = temp_train['weather'].map({
    1 : 'Clear',
    2 : 'Few clouds',
    3 : 'Light snow, Rain',
    4 : 'Heavy snow, Rain'
})

temp_train['weather']

temp_train.info()
```


```python
temp_train.head()
```

# Chapter 04. 데이터 시각화
- 수치를 예측하는 대회
- 종속변수를 시각화해야 함
- 분포 확인 후, 로그변환을 줄지 말지를 결정해야 함
- 시각화를 하는 이유 : 어떤 컬럼을 삭제할 지 고민하기 위해서


```python
fix, ax = plt.subplots(nrows = 1, ncols = 2, figsize = (10, 8))

sns.histplot(train['count'], ax = ax[0])   # ax[0] = 그래프 도화지의 인덱스 위치
sns.histplot(np.log1p(train['count']), ax = ax[1])   # 로그변환 --> np.log1p(컬럼명)

# 제목 옵션
ax[0].set_title('Normal Graph')
ax[1].set_title('Log Transformed Graph')

plt.show()
```

- 막대 그래프
   + year, count
   + month, count
   + day, count
   + hour, count
- 각 그래프의 타이틀 추가


```python
fig, ax = plt.subplots(nrows = 2, ncols = 2)

## 1단계 : 전체 그래프 기본 설정
# 그래프 사이 간격 띄우기
fig.tight_layout()

# 전체 그래프 사이즈 관리
fig.set_size_inches(15, 12)

# 2단계 : 각 개별 그래프 입력
sns.barplot(x = 'year', y = 'count', hue = 'season', data = temp_train, ax = ax[0, 0], capsize=.01)
sns.barplot(x = 'month', y = 'count', data = temp_train, ax = ax[0, 1], capsize=.01)
sns.barplot(x = 'day', y = 'count', data = temp_train, ax = ax[1, 0], capsize=.01)
sns.barplot(x = 'hour', y = 'count', data = temp_train, ax = ax[1, 1], capsize=.01)

# 3단계 : 디테일 옵션
ax[0, 0].set_title('Rental amounts by Year')
ax[0, 1].set_title('Rental amounts by Month')
ax[1, 0].set_title('Rental amounts by Day')
ax[1, 1].set_title('Rental amounts by Hour')

ax[0, 0].tick_params(axis = 'x', labelrotation = 90)
plt.show()
```

- boxplot
    + season, count
    + weather, count
    + holiday, count
    + workingholiday, count


```python
fig, ax = plt.subplots(nrows = 2, ncols = 2)

## 1단계 : 전체 그래프 기본 설정
# 그래프 사이 간격 띄우기
fig.tight_layout()

# 전체 그래프 사이즈 관리
fig.set_size_inches(15, 18)

# 2단계 : 각 개별 그래프 입력
sns.boxplot(x = 'season', y = 'count', data = temp_train, ax = ax[0, 0])
sns.boxplot(x = 'weather', y = 'count', data = temp_train, ax = ax[0, 1])
sns.boxplot(x = 'holiday', y = 'count', data = temp_train, ax = ax[1, 0])
sns.boxplot(x = 'workingday', y = 'count', data = temp_train, ax = ax[1, 1])

# 3단계 : 디테일 옵션
ax[0, 0].set_title('Rental amounts by Season')
ax[0, 1].set_title('Rental amounts by Weather')
ax[1, 0].set_title('Rental amounts by Holiday')
ax[1, 1].set_title('Rental amounts by Workingday')

ax[0, 0].tick_params(axis = 'x', labelrotation = 90)
plt.show()
```

- 포인트플롯
- 5개의 행 그래프 작성
    + workingday, holiday, weekday, season, weather
- 5개의 그래프를 한 이미지로 그리기


```python
sns.pointplot(x = 'hour', y = 'count', hue = 'season', data = temp_train)
```


```python
fig, ax = plt.subplots(nrows = 5)

fig.tight_layout()

fig.set_size_inches(12, 18)

sns.pointplot(x = 'hour', y = 'count', hue = 'workingday', data = temp_train, ax = ax[0])
sns.pointplot(x = 'hour', y = 'count', hue = 'holiday', data = temp_train, ax = ax[1])
sns.pointplot(x = 'hour', y = 'count', hue = 'weekday',  data = temp_train, ax = ax[2])
sns.pointplot(x = 'hour', y = 'count', hue = 'season',  data = temp_train, ax = ax[3])
sns.pointplot(x = 'hour', y = 'count', hue = 'weather',  data = temp_train, ax = ax[4])


plt.show()
```

- 회귀선을 포함한 산점도 그래프
- 총 4개의 그래프가 나와야 함


```python
# (scatter_kws = {'alpha : 0.2'}, line_kws = {'color' : 'blue'})
```


```python
temp_train.head()
```


```python
fig, ax = plt.subplots(nrows = 2, ncols = 2)

fig.tight_layout()

fig.set_size_inches(12, 18)

sns.regplot(x ='temp', y ='count', data = temp_train, scatter_kws = {'alpha' : 0.2}, line_kws = {'color' : 'blue'}, ax = ax[0, 0])
sns.regplot(x ='atemp', y ='count', data = temp_train, scatter_kws = {'alpha' : 0.2}, line_kws = {'color' : 'blue'}, ax = ax[0, 1])
sns.regplot(x ='humidity', y ='count', data = temp_train, scatter_kws = {'alpha' : 0.2}, line_kws = {'color' : 'blue'}, ax = ax[1, 0])
sns.regplot(x ='windspeed', y ='count', data = temp_train, scatter_kws = {'alpha' : 0.2}, line_kws = {'color' : 'blue'}, ax = ax[1, 1])

ax[0, 0].set_title('Rental amounts by Temp')
ax[0, 1].set_title('Rental amounts by aTemp')
ax[1, 0].set_title('Rental amounts by Humidity')
ax[1, 1].set_title('Rental amounts by Windspeed')

plt.show()
```


```python
temp_train['windspeed'].value_counts()
```

- 히트맵 그래프 그리기
- 상관계수 해석
    + 수치가 양수다 (양의 관계)
    + 수치가 음수다 (음의 관계)
    + 0 ~ +-0.2 : 두 변수 사이의 상관관계는 없다.
    + +-0.2 ~ +-1 : 값이 커지면 커질수록 두 변수 간 상관관계는 크다.


```python
corrMat = temp_train[['temp', 'atemp', 'humidity', 'windspeed', 'count']].corr()
corrMat
```


```python
sns.heatmap(corrMat, annot = True)
# Count와 컬럼들의 상관관계 비
```

## 데이터 전처리
- 첫번째 : train 데이터의 casual, registered 컬럼 제거할 것
- 두번째 : 날짜 데이터 처리, dt.month <-- 이렇게 할 것
- 세번째 : season 컬럼 처리 필요 (숫자를 문자로 변환)
    + 인코딩 변환(라벨 인코딩, 원핫 인코딩)
- 네번째 : weather 컬럼 처리 필요 (숫자를 문자로 변환)
    + 인코딩 변환(라벨 인코딩, 원핫 인코딩)
- 다섯번째 : month, day 컬럼 삭제 예정
- 여섯번째 : weather가 4인 데이터 삭제 (이상치)
- 일곱번째 : windspeed 컬럼 삭제 (놔둬도 상관없음)
- 여덟번째 : temp, atemp 중 하나 삭제 (옵션)
- 마지막 : 모든 문자를 숫자로 인코딩 (원핫 인코딩)

- 3시 10분까지
- 위 내용 처리 완료


### 첫번째 : train 데이터의 casual, registered 컬럼 제거


```python
train.shape
```


```python
train = train.drop(['casual', 'registered'], axis = 1)
train.shape
```

## weather 컬럼 삭제
- 4인 데이터는 삭제


```python
train = train[train['weather'] != 4].reset_index(drop=True)
train.shape
```


```python
train.info()
```

- 데이터 합치기


```python
all_data = pd.concat([train, test]).reset_index(drop = True)
all_data.info()
```

### 두번째 : 날짜 데이터 처리, dt.year 형태로!


```python
all_data['date'] = pd.to_datetime(all_data['datetime'])
all_data['year'] = all_data['date'].dt.year
all_data['hour'] = all_data['date'].dt.hour
all_data['weekday'] = all_data['date'].dt.day_name()

all_data.shape
all_data.info()   # date 컬럼의 dtype이 datetime64로 변경됐는지 확인
# all_data['year'], all_data['hour'], all_data['weekday']
```

### 세번째 : season 컬럼 처리 (숫자를 문자로 변환, 라벨 인코딩 or 원핫 인코딩)


```python
all_data['season'] = all_data['season'].replace(to_replace = [1, 2, 3, 4],
                                               value = ['Spring', 'Summer', 'Fall', 'Winter'])
print(all_data['season'])

all_data.shape
all_data.info()
```

### 네번째 : weather 컬럼 처리 (숫자를 문자로 변환, 라벨 인코딩 or 원핫 인코딩


```python
all_data['weather'] = all_data['weather'].map({
        1 : 'Clear',
        2 : 'Few Cloud',
        3 : 'Light rain, snow',
        4 : 'Heavy rain, snow'
})
```


```python
all_data['weather']
```

### 다섯번째 : month, day 컬럼 삭제
- 두번째 과정에서 함께 진행했음

### 여섯번째 : weather가 4인 데이터 삭제 (이상치)

- all_data가 아니라 train에서 삭제해야 함


```python
# all_data.drop(all_data.loc[all_data['weather'] == 'Heavy rain, snow'].index, inplace =True)
# all_data = all_data[all_data['weather'] != 'Heavy rain, snow']
```


```python
# all_data.shape
```

### 일곱번째 : windspeed 컬럼 삭제 (놔둬도 상관없음)



```python
all_data = all_data.drop(['windspeed'], axis = 1)
all_data.shape
```

### 여덟번째 : temp, atemp 중 하나 삭제 (옵션)


```python
all_data = all_data.drop(['atemp'], axis = 1)
all_data.shape
```

### 아홉번째 : datetime과 date 컬럼 제거하기


```python
all_data = all_data.drop(['datetime', 'date'], axis = 1)
all_data.shape
```

### 마지막 : 모든 문자를 숫자로 인코딩 (원핫 인코딩)


```python
all_data = pd.get_dummies(all_data).reset_index(drop = True)
all_data.shape
```


```python
all_data.info()
```

## 데이터셋 나누기
- 훈련데이터와 테스트데이터로 재분리
- count : 타킷 데이터(=종속 데이터)
    + 타킷 데이터가 있으면 훈련 데이터
    + 타킷 데이터가 없으면 테스트 데이터


```python
train = all_data[~pd.isnull(all_data['count'])]
test = all_data[pd.isnull(all_data['count'])]
```


```python
train.shape, test.shape
```

- count 컬럼 제거
- 타킷 데이터이기 때문
- 타깃 데이터만 y로 추출
    + train, test count 컬럼 제거


```python
y = train['count'] # 타깃 데이터
```


```python
X = train.drop(['count'], axis = 1)
test = test.drop(['count'], axis = 1)

X.shape, test.shape
```


```python
X.shape, y.shape, test.shape
```

## 모델 훈련
- LinearRegression 모형만 학습

### 과제
- 교차검증
- 모형추가
- 하이퍼파라미터 튜닝


```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split


lr_model = LinearRegression()

# 모형 학습 전
# 로그변환을 해준다.
log_y = np.log(y)
lr_model.fit(X, log_y)

# 모형 예측
lr_preds = lr_model.predict(test)
lr_preds[:10]
```

## 모형 예측



```python
# 지수변환
final_preds = np.exp(lr_preds)
final_preds
```

## 제출


```python
submission['count'] = final_preds 
submission.to_csv('submission.csv', index=False)
```
