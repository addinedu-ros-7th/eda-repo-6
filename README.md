# eda-repo-6
EDA 프로젝트 6조 저장소. way back home
---
> ### ***서울시 아파트 상승의 원인은 공급량 부족과 전세가율 상승 때문일까 ?***<br>앞으로 서울시 부동산 가격은 상승 or 하락 할 것인가 ?
<br />

## 🤖 프로젝트 소개
<details markdown="1">
<summary><h3>서울시 아파트 가격 변동 요인에 따른 시계열 상관관계 분석</h3></summary>
<li>현재 대한민국의 부동산 매매 시장이 과열 양상을 보이고 있습니다.</li>
  <li>주택 구매를 고려하는 시점에서 대출을 최대한 활용하여 '영끌' 방식으로 진입하는 것이 과연 타당한 결정인지에 대한 고민이 필요합니다.</li>
  <li>이를 위해 저희는 <b>과거 부동산 데이터를 분석하여 주요 급등 및 하락 시기의 원인과 추세를 파악한 뒤, 현재 시장 상황과 비교함으로써 합리적인 진입 시점을 결정</b>하고자 합니다.</li>
</details>
<br />

## 🧠 구성원 및 역할
|이름|업무|
|:---|:---|
|임시온|- 프로젝트 총괄 <br> - OPENAPI를 통한 KOSIS 데이터 수집 및 시각화 <br> - 데이터 베이스 설계 및 관리|
|이은효|- 뉴스 워드 클라우드 관리 및 조사<br>- 부동산 사이트 및 이슈조사<br> - 부동산 관련 특성 파악 브레인스토밍|
|공도웅|- 웹 스크롤링을 활용한 데이터 수집<br> - 부동산 사이트 및 시장조사<br> - 데이터 그래프 시각화|
|이헌중|- 한국은행 데이터 수집<br> - 데이터 분석 및 논리화 <br> - 데이터와 서울시 아파트 가격 관계 분석|
<br />

## 🖥️ 활용 기술
|구분|상세|
|:---|:---|
|개발환경|<img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" /> |
|IDE| <img src="https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white" /> <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" /> <img src="https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252" />|
|언어| <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />   |
|EDA 시각화 및 데이터 수집|<img src="https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white" /> <img src="https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white" /> <img src="https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black" /> <img src="https://img.shields.io/badge/Selenium-43B02A?style=for-the-badge&logo=Selenium&logoColor=white" /> <img src="https://img.shields.io/badge/BeautifulSoup-%23ffffff.svg?style=for-the-badge&logo=BeautifulSoup&logoColor=black" /> <img src="https://img.shields.io/badge/OPENAPI-%6BA539.svg?style=for-the-badge&logo=openapiinitiative&logoColor=black" />|
|DB|<img src="https://img.shields.io/badge/Amazon_RDS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white" /> <img src="https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white" />|
|협업| <img src="https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white" /> <img src="https://img.shields.io/badge/confluence-172B4D?style=for-the-badge&logo=confluence&logoColor=white" /> <img src="https://img.shields.io/badge/jira-0052CC?style=for-the-badge&logo=jira&logoColor=white" />|
<br />

## 📜 웹 크롤링 및 데이터 전처리 과정

### 기업 및 사이트 선정
- 기준 금리 데이터는 한국은행에서 진행.
- 그 외에 데이터는 [KOSIS](https://kosis.kr/index/index.do) 에서 진행.
- 워드 클라우드 크로링 기준 : 네이버 뉴스에서 영향력이 큰 주요 언론사 위주로 진행.
- 워드 클라우드 검색 키워드 : 부동산, 집값
<details markdown="1">
<summary><h3>1. 상승/보합/하락장에서 '부동산' 이슈 분석</h3></summary>
<li>기간 : 2012년 1월 ~ 2024년 8월</li>
  <li>기사 유형 : 지면 기사</li>
  <li>검색 키워드 : 부동산, 집값</li>
  <li>TF-IDF (Term Frequency-Inverse Document Frequency) 적용<br>:특정 문서에서 자주 등장하는 단어에 가중치 부여함, 전체 문서에서 흔히 등장하는 단어는 중요도를 낮춤</li>
</details>
<details markdown="1">
<summary><h3>2. 상승/보합/하락장에서 '부동산' 뉴스 개수 상관관계</h3></summary>
<li>기간 : 2012년 1월 ~ 2024년 8월</li>
  <li>기사 유형 : 지면 기사</li>
  <li>검색 키워드 : 부동산</li>
  <li>주택 가격의 상승/보합/하락장과 부동산 뉴스 개수의 관계 분석<br> 주택 시장의 관심도 파악 가능</li>
</details>

| 데이터 수집종류 | 출처 |
|:-----------------:|:----------------------:|
|주택공급량|[KOSIS](https://kosis.kr/index/index.do)|
|전세가격지수|[KOSIS](https://kosis.kr/index/index.do)|
|매매가격지수|[KOSIS](https://kosis.kr/index/index.do)|
|대출금액총액|[KOSIS](https://kosis.kr/index/index.do)|
|기준금리|[KOSIS](https://kosis.kr/index/index.do)|
|미분양 현황|[KOSIS](https://kosis.kr/index/index.do)|
|전세가율|[KOSIS](https://kosis.kr/index/index.do)|
|주택준공실적|[KOSIS](https://kosis.kr/index/index.do)|
|혼인건수|[KOSIS](https://kosis.kr/index/index.do)|
|전월세전환율|[KOSIS](https://kosis.kr/index/index.do)|
|주택멸실지수|[KOSIS](https://kosis.kr/index/index.do)|
<br />

> ### 서울시 아파트 가격 상승 원인 가설
> #### 1, 매매가대비 전세가율
> - 부동산 시장에서는 전세가율 60%를 황금율로 보고 있으며, 매매가격 대비 전세가격이 60% 이상일 경우 매매 심리가 상승하는 원인으로 조사.(전세 수요가 매매 수요로 전환되기 때문)
> - 매매가지수 대비 전세가율 분석, 매매가지수와 전세가변화 추이를 2012~2024 까지 비교, 전세가율 상승 시 매매가지수 상승하는지 확인, 전세가율 하락 시 매매가지수 하락하는지 확인
> - -> 이를 통해 매매가에 전세가율이 영향을 미치는지 분석
> #### 2. 기준 금리 & 대출금상승
> ##### (한국은행기준) 기준 금리가 하락 할 때
> - 주택 전월세 전환율 비율도 하락하는 관계 분석
> - -> 전월세 전환율이 낮아지면 전세에서 월세 전환비율이 높아져 <b>전세가구수 감수</b>가 발생하며 전세 수요대비 주택수가 감소하여 전세가 상승
> - 가계대출총량이 증가하는 관계 분석
> - -> 월세수요의 전세화 및 전세수요의 매매화가 발생하여 집값이 상승<br>
> *ex) 2012년 기준금리 3.07% 일때 5억 대출시 이자 1,535만원<br>2016년 기준금리 1.35% 일때 5억 대출시 이자<tab>675만원으로 -870만원 이상 떨어짐<br>
> #### 3. 수요증가 & 공급부족
> ##### 서울시 인구수 * 가구수 조사
> - 서울시 인구(24.07기준) 941만7,469명, 전체주택수(아파트, 단독, 연립, 다세대) 383만9800가구
> - 통계청 기준 2022년 가구당 2.2명이며, <b>서울시 기준 2.5명으로 0.3명 초과로 주택 수가 부족한 상태</b>
> - 2022년기준OECD 평균 462/1,000명당 이고 서울시 407/1,000명 55가구로 <b>전체 517,935가구 부족함</b>
> ##### 서울시 신혼 부부 발생 건수 & 전입/전출가구수 조사
> - 2023년 기준 서울시 전체 <b>혼인건수36,324건으로 신규 주택이 필요한 것</b>으로 파악됨
> - - 2023년 기준 서울시 전입가구수/전출인원가구수 -1,527
> ##### 서울시 아파트 준공 및 미분양 증감 조사
> - 2023.07 매일경제에서 주거형태 선호도 조사에서 68%이상 아파트를 선호하는것으로 조사됐으며
> - 2024년 3월 기준 결혼정보회사 에서 조사한 선호도 조사에서 74.6%가 아파트를 선호하는것으로 조사됨<br>
> [출처](https://www.mk.co.kr/news/culture/10782998) 

## 검증
<details markdown="1">
<summary><h2>1. 상승/보합/버블/하락 구간 별 이슈 분석</h2></summary>
  <img src="https://github.com/user-attachments/assets/52a25b81-7d65-4fe9-aa3e-7d2d356e0f0d" />
</details>
<details markdown="1">
<summary><h2>2. 상승 구간 이슈 분석</h2></summary>
  <img src="https://github.com/user-attachments/assets/9890267f-a067-467d-bf15-2918ca46bc7f" />
</details>
<details markdown="1">
<summary><h2>3. 보합 구간 이슈 분석</h2></summary>
  <img src="https://github.com/user-attachments/assets/83f96cf7-df0f-41c8-a33d-16f4769c017e" />
</details>
<details markdown="1">
<summary><h2>4. 버블 구간 이슈 분석</h2></summary>
  <img src="https://github.com/user-attachments/assets/1556fcd2-e332-4186-a963-fc445676b0dc" />
</details>
<details markdown="1">
<summary><h2>5. 하락 구간 이슈 분석</h2></summary>
  <img src="https://github.com/user-attachments/assets/173279b7-e62d-4f14-9849-516bd796e5bc" />
</details>

<details markdown="1">
<summary><h2>전세가율 상승시 매매가 상승</h2></summary>
  <img src="https://github.com/user-attachments/assets/f50e03f8-7e8b-4ba5-92c4-5d94bf2a12d0" />
<!--   ![image](https://github.com/user-attachments/assets/f50e03f8-7e8b-4ba5-92c4-5d94bf2a12d0) -->
</details>

<details markdown="1">
<summary><h2>미분양감소 / 공급부족시 매매가 상승</h2></summary>
  <img src="https://github.com/user-attachments/assets/4796f292-ca2d-4f45-b873-cd1ef8ff1946" />
<!--   ![image](https://github.com/user-attachments/assets/4796f292-ca2d-4f45-b873-cd1ef8ff1946) -->
</details>

<details markdown="1">
<summary><h2>기준 금리하락시 매매가 상승 및 전월세 전환율 하락</h2></summary>
  <img src="https://github.com/user-attachments/assets/4bb432c1-fdd9-4511-aaa1-87a3fb396e7a" />
</details>
<br>


## 결론
1. 전세가율과 매매지수의 관계
> 전세가율은 매매지수보다 선행하며 움직이며, 매매가 상승에 영향을 미침

<br>


2. 매매가격과 주택 공급량
> 매매가격이 상승하는 시기에는 주택 공급량이 증가하고, 하락 시에는 미분양 물량이 증가함

<br>


3. 대출금리와 전세 가격
> 대출금리가 낮아지면 전월세 전환율이 낮아져 전세에서 월세로의 전환이 많아지며, 이로 인해 전세 매물 수가 감소하여 전세 가격이 상승함


<br>


4. 부동산 키워드와 시장 흐름
> 상승장, 보합장, 하락장 모두에서 부동산 관련 키워드 뉴스가 증가하는 경향이 나타남














