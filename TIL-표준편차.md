* https://atarimae.biz/archives/5379#i-2

## 표준편차

| $ s=\sqrt {\frac {1}{n} \sum^{n}_{i=1}{(x_i-\overline{x}})^2} $

* s : 표준편차
* n : 데이터 수 (10개)
* $x_i$ : 각 데이터의 값 (70점)
* $\overline{x}$ : 데이터의 평균 (평균 60점) 

### 데이터 샘플

|  _  | $x$ |
|-----|---|
| A   | $x_1=35$ |
| B   | $x_2=55$ |
| C   | $x_3=70$ |
| D   | $x_4=80$ |

### 1. 평균

$\overline{x}=\frac {1}{n} \sum^{n}_{i=1}{x_i} = \frac{1}{4}{(35+55+70+80)}=60$

### 2. 편차, 제곱하기

|  _  | $ x_i -\overline x$ | $ (x_i -\overline x)^2 $ | 
|-----|---|---|
| A   | 35-60=-25 | 625 |
| B   | -5 | 25 |
| C   | 10  | 100 |
| D   | 20  | 400 | 

### 3. 데이터의 총 개수로 나누기

### 4. 편차, 제곱하기

|  _  | $ (x_i -\overline x)^2 $ | 
|-----|---|
| A   |  625 |
| B   | 25 |
| C   |  100 |
| D   |  400 | 
| 총합 | 1150 |
| 분산 | $s^2 = \frac{1150}{4}=287.5$|

### 5. 제곱근

$ s = \sqrt {s^2} = \sqrt {287.5} = 16.9558... $

* 4명의 수학점수의 표준편차는 `16.95`이다.

### 의미

* 평균 60점에서 70점을 받았다면
* case 1 : "0 / 5 / 10/ 70 / 80 / 80 /82 / 85 / 93 / 95"(평균 60점)에서라면 

```python
In [1]: import numpy as np

In [2]: a = np.array([0, 5, 10, 70, 80, 80, 82, 85, 93, 95])

In [3]: a.mean()
Out[3]: 60.0

In [4]: a.std()
Out[4]: 36.67151483099655

In [5]: np.median(a)
Out[5]: 80.0
```

* 표준편차가 36점/ 중간값이 80점
* 극히 일분의 학생이 평균을 낮췄을 뿐, 80점 이하는 잘 한게 아니라는.


* case 2 : "50, 52, 54, 60, 60, 61, 61, 70, 72"(평균 60점)에서라면 

```python
In [6]: b= np.array([50, 52, 54, 60, 60, 61, 61, 70, 72])

In [7]: b.mean()
Out[7]: 60.0

In [8]: b.std()
Out[8]: 7.039570693980958

In [9]: np.median(b)
Out[9]: 60.0
```

* 편차 7.03 / 중간값 60
* 잘받은 점수임

* 평균 : 정보량이 적고, 실제 그것만으로는 쓸모가 없을 수 있다는 의미
* 편차의 크기를 나타내는 "표준편차" 수를 보는게 필요

```
일반적으로 표준편차가 36점 -> 차이가 큰 시험 -> 평균 +10점은 음..
표준편차가 7점 -> 격차가 작음 테스트 -> 평균+10점은 잘한 것임
라고 판단 할수 있음
```

## 데이터 차이를 표현

* 데이터 : "0,5,10,70,80,80,82,85,93,95"(평균 60)
* 
### 1. 차이

$\sum^{n}_{i=1}{(x_i-\overline x)}$

* 수에서 평균을 뺀 합

```
In [10]: c = np.array([0,5,10,70,80,80,82,85,93,95])

In [11]: c.mean()
Out[11]: 60.0

In [12]: d = c-c.mean()

In [13]: d
Out[13]: array([-60., -55., -50.,  10.,  20.,  20.,  22.,  25.,  33.,  35.])

In [14]: np.sum(d)
Out[14]: 0.0
```
* 결과가 0이 됨

### 2. 절대값

$\sum^{n}_{i=1}{|x_i-\overline x|}$

```python
In [15]: d = [ np.absolute(x-c.mean()) for x in c]

In [16]: d
Out[16]: [60.0, 55.0, 50.0, 10.0, 20.0, 20.0, 22.0, 25.0, 33.0, 35.0]

In [17]: np.sum(d)
Out[17]: 330.0
```

* 데이터의 총수가 증가할수록 값이 증가함

### 3. 데이터의 총수로 나누면

$\frac {1}{n} \sum^{n}_{i=1}{|x_i-\overline x|}$

```python
In [15]: d = [ np.absolute(x-c.mean()) for x in c]

In [16]: d
Out[16]: [60.0, 55.0, 50.0, 10.0, 20.0, 20.0, 22.0, 25.0, 33.0, 35.0]

In [17]: np.sum(d)
Out[17]: 330.0

In [18]: np.sum(d)/len(d)
Out[18]: 33.0
```

* A : "40,45,60,75,80 '와 B : "30,55,60,65,90' 의 겨웅, 같은 평가가 이뤄 질수 있음

```
In [20]: aa = np.array([40,45,60,75,80])

In [21]: np.sum([np.absolute(x-aa.mean()) for x in aa])/len(aa)
Out[21]: 14.0

In [22]: bb = np.array([30,55,60,65,90])

In [23]: np.sum([np.absolute(x-bb.mean()) for x in bb])/len(bb)
Out[23]: 14.0
```

### 4. 제곱(=분산)

$\frac {1}{n} \sum^{n}_{i=1}{(x_i-\overline x)^2}$

* 데이터들의 차별을 두기 위해 제곱을 적용

```python
In [42]: a
Out[42]: array([ 0,  5, 10, 70, 80, 80, 82, 85, 93, 95])

In [43]: np.var(a)
Out[43]: 1344.8

In [30]: aa
Out[30]: array([40, 45, 60, 75, 80])

In [31]: np.var(aa)
Out[31]: 250.0

In [32]: bb
Out[32]: array([30, 55, 60, 65, 90])

In [33]: np.var(bb)
Out[33]: 370.0
```

* 제곱을 적용해서 값이 커지는 단점이 있음

### 5. 제곱근 (표준편차)

$s = \sqrt{ \frac {1}{n} \sum^{n}_{i=1}{(x_i-\overline x)^2}}$


```python
In [42]: a
Out[42]: array([ 0,  5, 10, 70, 80, 80, 82, 85, 93, 95])

In [43]: np.var(a)
Out[43]: 1344.8

In [44]: np.std(a)
Out[44]: 36.67151483099655

In [36]: aa
Out[36]: array([40, 45, 60, 75, 80])

In [40]: np.std(aa)
Out[40]: 15.811388300841896

In [38]: bb
Out[38]: array([30, 55, 60, 65, 90])

In [39]: np.std(bb)
Out[39]: 19.235384061671343
```

## 68% / 95% 규칙

![](https://atarimae.biz/wp-content/uploads/2016/02/sigma-three.png)

* 평균 점수 50점 / 표준편차 10점이라면

```
40~60점(평균+-표준편차)에 응시자의 68%가 존재하고
30~70점(평균+-(표준편차*2))에 응시자의 95%가 존재한다는
```

* `68%, 95% 규칙`
*  

