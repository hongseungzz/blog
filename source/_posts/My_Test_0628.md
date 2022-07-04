---
title: "배운 내용 개인 테스트_0628"
output: 
  html_document:
    toc: true
    toc_float: true
    keep_md: true
date: '2022-06-28 08:22:22'
---


```python
for a in range(500321) :
  print("episode : ", a+1)
  if a == 5 :
    break
  print("우리들의")
  print("블루스")
```

    episode :  1
    우리들의
    블루스
    episode :  2
    우리들의
    블루스
    episode :  3
    우리들의
    블루스
    episode :  4
    우리들의
    블루스
    episode :  5
    우리들의
    블루스
    episode :  6
    


```python
average = [0.357, 0.392, 0.324, 0.407]

for avg in average :
  if avg == 0.324 :
    break
  print("타율 : ", avg)
```

    타율 :  0.357
    타율 :  0.392
    


```python
number = [10, 20, 30, 40, 50, 60 ,70 ,80]
sum = 0

for num in number :
  print("number : ", num)
  sum = sum + num
  print("total : ", sum)

print("결과 값 : ", sum)
```

    number :  10
    total :  10
    number :  20
    total :  30
    number :  30
    total :  60
    number :  40
    total :  100
    number :  50
    total :  150
    number :  60
    total :  210
    number :  70
    total :  280
    number :  80
    total :  360
    결과 값 :  360
    


```python
players = ["김광현", "류현진", "이대호", "이정후", "강백호"]
newlist = []

for mvp in players :
  print("최고의 선수 : ", mvp)
  if "이" in mvp :
    print("이씨 성의 선수 : ", mvp)
    newlist.append(mvp)

print(newlist)
```


```python
num = 10
while num < 150 :
  num = num + 10
  print(num)
```


```python
def ops(a, b) :
  return a + b

print(ops(0.425, 0.572))

def obh(a, b, c, d) :
  return a - b - c - d

print(obh(97, 16, 3, 13))
```

    0.9969999999999999
    65
    


```python
import numpy as np
print(np.__version__)
```

    1.21.6
    


```python
input = [19, 88, 4, 29]
output = [19, 95, 8, 18]

input_arr = np.array(input)
output_arr = np.array(output)

result = input_arr + output_arr
print(result)

result = input_arr - output_arr
print(result)

result = input_arr * output_arr
print(result)

result = input_arr / output_arr
print(result)

temp_res = np.around([result], 3)     # 임의의 소숫점 반올림 자리 응용
print(temp_res)
```

    [ 38 183  12  47]
    [ 0 -7 -4 11]
    [ 361 8360   32  522]
    [1.         0.92631579 0.5        1.61111111]
    [[1.    0.926 0.5   1.611]]
    


```python
temp_arr = np.zeros((5, 3, 6))
print(temp_arr)

temp_arr = np.ones((3, 5, 2))
print(temp_arr)

temp_arr = np.full((2, 4, 5), 22)
print(temp_arr)
```

    [[[0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]]
    
     [[0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]]
    
     [[0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]]
    
     [[0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]]
    
     [[0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]
      [0. 0. 0. 0. 0. 0.]]]
    [[[1. 1.]
      [1. 1.]
      [1. 1.]
      [1. 1.]
      [1. 1.]]
    
     [[1. 1.]
      [1. 1.]
      [1. 1.]
      [1. 1.]
      [1. 1.]]
    
     [[1. 1.]
      [1. 1.]
      [1. 1.]
      [1. 1.]
      [1. 1.]]]
    [[[22 22 22 22 22]
      [22 22 22 22 22]
      [22 22 22 22 22]
      [22 22 22 22 22]]
    
     [[22 22 22 22 22]
      [22 22 22 22 22]
      [22 22 22 22 22]
      [22 22 22 22 22]]]
    


```python
temp_arr = np.linspace(5, 7, 12)
print(temp_arr)
```

    [5.         5.18181818 5.36363636 5.54545455 5.72727273 5.90909091
     6.09090909 6.27272727 6.45454545 6.63636364 6.81818182 7.        ]
    


```python
temp_arr = np.arange(1, 20, 3)
print(temp_arr)
```

    [ 1  4  7 10 13 16 19]
    


```python
import numpy as np
arr_01 = [19, 95, 8, 18]
arr_02 = [30, 9, 70, 19]

newarr = np.add(arr_01, arr_02)
print(newarr)

newarr = np.subtract(arr_01, arr_02)
print(newarr)

newarr = np.multiply(arr_01, arr_02)
print(newarr)

newarr = np.divide(arr_01, arr_02)
print(newarr)
```

    [ 49 104  78  37]
    [-11  86 -62  -1]
    [570 855 560 342]
    [ 0.63333333 10.55555556  0.11428571  0.94736842]
    


```python
import numpy as np
arr = np.trunc([-14.45345345, 52.24235235])
print(arr)

arr = np.fix([-23.234134135, 14.235413525])
print(arr)
```

    [-14.  52.]
    [-23.  14.]
    


```python
arr = np.around([-24.346346457567, 200.1253235], 5)
print(arr)
```

    [-24.34635 200.12532]
    


```python
arr = np.floor([2.5324234, -1.435435346])
print(arr)

arr = np.ceil([2.5324234, -1.435435346])
print(arr)
```

    [ 2. -2.]
    [ 3. -1.]
    


```python
arr = np.arange(1, 21)
print(arr)
```

    [ 1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20]
    


```python
np.where(arr < 10, arr * 10, arr + 10)

np.where(arr < 10, arr + 10, arr + 5)
```




    array([11, 12, 13, 14, 15, 16, 17, 18, 19, 15, 16, 17, 18, 19, 20, 21, 22,
           23, 24])




```python
cond_list = [arr <= 5, arr <= 10, arr < 20]
value_list = [arr * 5, arr + 10, arr + 5]

np.select(cond_list, value_list, default = arr)
```




    array([ 5, 10, 15, 20, 25, 16, 17, 18, 19, 20, 16, 17, 18, 19, 20, 21, 22,
           23, 24, 20])




```python
import numpy as np
arr = np.zeros((3,8))
print(arr)
```

    [[0. 0. 0. 0. 0. 0. 0. 0.]
     [0. 0. 0. 0. 0. 0. 0. 0.]
     [0. 0. 0. 0. 0. 0. 0. 0.]]
    


```python
after_re = arr.reshape(2, 3, 4)
print(after_re.shape)
print(after_re)
```

    (2, 3, 4)
    [[[0. 0. 0. 0.]
      [0. 0. 0. 0.]
      [0. 0. 0. 0.]]
    
     [[0. 0. 0. 0.]
      [0. 0. 0. 0.]
      [0. 0. 0. 0.]]]
    


```python
after_re = arr.reshape(-1, 3, 2)
print(after_re.shape)
print(after_re)
```

    (4, 3, 2)
    [[[0. 0.]
      [0. 0.]
      [0. 0.]]
    
     [[0. 0.]
      [0. 0.]
      [0. 0.]]
    
     [[0. 0.]
      [0. 0.]
      [0. 0.]]
    
     [[0. 0.]
      [0. 0.]
      [0. 0.]]]
    


```python
import pandas as pd
print(pd.__version__)
```

    1.3.5
    


```python
temp_dict = {
    'var1' : [19, 95],
    'var2' : [8, 18]
}

df = pd.DataFrame(temp_dict)
print(df)
print(type(df))
```

       var1  var2
    0    19     8
    1    95    18
    <class 'pandas.core.frame.DataFrame'>
    
