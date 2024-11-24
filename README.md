# 🏃 **캡티마 카르텔 러닝 코스 추천 시스템**  

### ✨ **프로젝트 개요**  
**캡티마 카르텔 러닝 코스 추천 시스템**은 **등교 전이나 하교 후, 학교 주변에서 러닝을 즐기고 싶은 학생들**을 위해 최적의 경로를 추천하는 프로젝트입니다.  
학교 주변의 주요 지점을 기반으로 효율적이고 안전한 러닝 코스를 설계하며, 누구나 웹에서 간단히 사용할 수 있는 서비스를 목표로 합니다.  

💡 **프로젝트 목표**  
- **맞춤형 러닝 코스 추천**: 거리, 시간, 난이도 등을 고려한 최적의 경로 제공  
- **데이터 기반 분석**: 정확한 거리 및 경로 데이터를 활용하여 신뢰도 높은 코스 제안  
- **사용자 친화적 인터페이스**: 웹을 통해 쉽게 접근 가능한 서비스 제공  

---

### 🗂️ **데이터 전처리**  
#### **1️⃣ 입력 데이터**  
- **`final_corner.csv`**: 학교 주변의 주요 지점을 담고 있는 CSV 파일로, 각 지점의 **위도(Latitude)**와 **경도(Longitude)** 정보를 포함합니다.  

#### **2️⃣ 전처리 과정**  

✅ **1. 고유 ID 부여**  
각 지점에 고유 ID를 부여하여 데이터를 관리하기 쉽게 구성하였습니다.  
```python
data['id'] = data.index + 1
data.to_csv('marker_id.csv')
```  

✅ **2. 좌표 조합 생성**  
지점 간 모든 조합을 생성하여 OSRM을 통해 경로 계산 준비를 완료했습니다.  
```python
import itertools
combinations = itertools.combinations(locations, 2)
```  

✅ **3. 거리 및 시간 계산 (OSRM 활용)**  
로컬 OSRM 서버를 사용해 각 조합의 **도보 거리**와 **예상 시간**을 계산하였습니다.  
```python
url = f"http://localhost:5050/route/v1/foot/{start};{end}?overview=false"
response = requests.get(url)
```  

✅ **4. 결과 저장**  
계산된 거리 데이터를 `dobo_dist.csv`로 저장하여 분석과 추천 알고리즘 개발에 활용할 수 있도록 준비했습니다.  
```python
dobo_dist.to_csv("dobo_dist.csv", index=False)
```  

---

### 🚀 **데이터 출처**  

---

### ❤️ **기대 효과**  
- 등하교 시간을 활용해 학생들이 건강한 라이프스타일을 실천할 수 있도록 지원.  
- 학교 주변 환경에 대한 이해도를 높이고, 안전한 러닝 코스 제공.  
- 간단하고 편리한 사용자 경험을 통해 러닝 문화 활성화 기여.  

---

### 🚀 **사용 라이브러리 / 기술 스택**  

---
