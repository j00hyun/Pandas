# 📊 Seaborn 차트 요약

---

## 🧭 개요
데이터 시각화의 목표는 단순히 그래프를 그리는 것이 아니라, **데이터가 말하고자 하는 이야기(story)** 를 명확하게 보여주는 것입니다.

Seaborn에서는 그래프를 다음의 세 가지 범주로 나눕니다:

1. **Trends (추세)** – 시간이 지나면서 값이 어떻게 변하는가
2. **Relationships (관계)** – 변수들 간의 상관관계나 영향
3. **Distributions (분포)** – 값들이 어느 구간에 몰려 있는가

---

## 📈 1️⃣ 추세 (Trends)
> **시간의 흐름에 따른 변화 패턴**을 시각화할 때 사용합니다.

### ▶️ `sns.lineplot()`
- 선 그래프(line chart)를 그리는 명령어입니다.
- 보통 X축에는 **시간(날짜)**, Y축에는 **값(value)** 을 둡니다.
- 여러 그룹의 변화를 한 번에 비교할 수 있습니다.

```python
sns.lineplot(data=spotify_data)
```
🧠 **활용 예:** 노래 스트리밍 수의 시간별 변화, 월별 매출 증가 추이 등

---

## 🤝 2️⃣ 관계 (Relationships)
> **변수들 간의 관계**를 분석할 때 사용합니다.

### 📊 `sns.barplot()`
- **막대그래프(bar chart)** 로, 그룹별 평균값 또는 총합을 비교합니다.
```python
sns.barplot(x="region", y="sales", data=df)
```

### 🌡️ `sns.heatmap()`
- **색상으로 수치의 크기를 표현하는 그래프**입니다.
- 숫자 테이블을 색상으로 변환하여 패턴을 파악할 수 있습니다.
```python
sns.heatmap(data=flight_data, annot=True)
```

### ⚪ `sns.scatterplot()`
- **산점도(scatter plot)** 로, 두 연속형 변수 간의 관계를 점으로 표시합니다.
- `hue` 옵션을 사용하면 제3의 범주형 변수를 색으로 구분할 수 있습니다.
```python
sns.scatterplot(x="bmi", y="charges", hue="smoker", data=insurance_data)
```

### 📉 `sns.regplot()`
- 산점도 위에 **회귀선(regression line)** 을 추가하여 선형 관계를 더 명확히 보여줍니다.
```python
sns.regplot(x="bmi", y="charges", data=insurance_data)
```

### 📏 `sns.lmplot()`
- 그룹별로 여러 개의 회귀선을 동시에 그릴 때 사용합니다.
```python
sns.lmplot(x="bmi", y="charges", hue="smoker", data=insurance_data)
```

### 🎯 `sns.swarmplot()`
- **범주형 vs 연속형 변수** 관계를 점으로 표현하는 산점도입니다.
```python
sns.swarmplot(x="smoker", y="charges", data=insurance_data)
```
🧠 **활용 예:** 흡연자와 비흡연자 그룹의 보험료 차이 비교

---

## 📊 3️⃣ 분포 (Distributions)
> 데이터가 **어느 구간에 몰려 있는지** 또는 **전체적인 형태(shape)** 를 분석할 때 사용합니다.

### 📦 `sns.histplot()`
- **히스토그램(histogram)** 으로, 데이터의 빈도(개수)를 구간별로 시각화합니다.
```python
sns.histplot(data=iris_data['Petal Length (cm)'])
```

### 🌊 `sns.kdeplot()`
- **커널 밀도 추정(KDE) 그래프**로, 히스토그램을 부드럽게 연결한 형태입니다.
- `fill=True` 옵션을 주면 곡선 아래 영역을 색으로 채웁니다.
```python
sns.kdeplot(data=iris_data, x='Petal Length (cm)', hue='Species', fill=True)
```

### 🌍 `sns.jointplot()`
- **2차원 KDE(결합 밀도) + 개별 KDE** 를 함께 보여주는 그래프입니다.
```python
sns.jointplot(x='Petal Length (cm)', y='Sepal Width (cm)', kind='kde', data=iris_data)
```
🧠 **활용 예:** 두 변수 간의 결합 확률 분포 및 개별 변수의 분포 확인

---

## 🧩 요약표
| 구분 | 명령어 | 설명 |
|------|----------|------|
| **추세 (Trend)** | `sns.lineplot()` | 시간에 따른 변화 시각화 |
| **관계 (Relationship)** | `sns.barplot()` | 그룹별 비교 (막대그래프) |
| | `sns.heatmap()` | 수치 패턴을 색상으로 표현 |
| | `sns.scatterplot()` | 두 연속형 변수의 관계 |
| | `sns.regplot()` | 회귀선 포함 산점도 |
| | `sns.lmplot()` | 그룹별 회귀선 비교 |
| | `sns.swarmplot()` | 범주형 vs 연속형 관계 |
| **분포 (Distribution)** | `sns.histplot()` | 데이터의 빈도 분포 |
| | `sns.kdeplot()` | 부드러운 확률 분포 곡선 |
| | `sns.jointplot()` | 2D 결합 분포 + 개별 KDE |
