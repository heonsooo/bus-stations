# Seoul_DailyBus
서울특별시_ 버스노선별 승하차 인원 분석

### 시작한 이유  
집 앞에 271버스가 다닙니다.   
그러던 어느날, 271버스가 271A와 271B로 분할을 하여 운행을 시작했습니다.  
이로인해 버스의 배차간격이 길어지게 되었고 불편함을 느꼈습니다.  

그렇게 몇개월의 시간이 지난 어느날, 271A버스안에 한 장의 공고문이 붙어있었습니다.  
271A 와 271B를 다시 합쳐 운행한다는 공고문이였습니다.  

이에 분할 전 271과 분할 후 271A와 271B의 이용 승객 수를 비교해보기 위해 시작했습니다.  
  
* 2021.02.17 버스 별 이용현황만 분석 
* 2021.02.18 271분할 전, 후 비교 및 시각화(O)
* 2021.02.19 2019-2020: 코로나 전,  월별 버스 승객수 비교(O) 

#### 진행 순서
1) 일간 정류소 별 승하차인원(19.12 , 20.12).ipynb
2) 12월_일자별_143버스_이용현황.ipynb
3) 12월_일자별_버스이용현황_변동그래프.ipynb
4) 271분할_전,후.ipynb
5) 코로나 전, 후 버스 승객 이용 분석(7011 버스).ipynb
---- 
     
분석 전, 공공데이터 포탈에서 서울시 버스노선별 정류장별 시간대별 승하차 인원 정보 (12월, 11월) csv파일을 받았습니다.   
url : http://data.seoul.go.kr/dataList/OA-12913/S/1/datasetView.do;jsessionid=31D5954E273D1A112655EE5150E04982.new_portal-svr-11 

----
   
## 1) [일간 정류소 별 승하차인원(19.12 , 20.12).ipynb](https://github.com/heonsooo/Bus_Stations/blob/main/%EC%9D%BC%EA%B0%84%20%EC%A0%95%EB%A5%98%EC%86%8C%20%EB%B3%84%20%EC%8A%B9%ED%95%98%EC%B0%A8%EC%9D%B8%EC%9B%90(19.12%20%2C%2020.12).ipynb)  
#### 가장 많은 승,하차승객수 정류소  
- 2020-12  데이터 탐색을 했습니다.  
- 하차 총 승객 수 값으로 내림차순 정렬을 했고, 금천 03 버스노선의 '구로디지털단지역환슨셍터' 에서 하차 총 승객 수가 가장 많았습니다. (이후 5번째까지 같았습니다.)  
- 승차 총 승객 수 값으로 내림차순 정렬을 해보았고, 금천 03 버스노선의 '가산디지털단지역환슨셍터' 에서 승차 총 승객 수가 가장 많았습니다. (이후 5번째까지 같았습니다.)  
- 승하차 총 승객 수 column을 만들고 이를 기준으로 정렬한 결과, 상위 20개의 역은 모두 '구로디지털단지역 교통광장'이고, 버스는 금천 03이였습니다.  
  이를 통해 서울에서 가장 많은 승,하차승객이 이곳에서 발생하며 금천 03 버스를 타러 가자 많은 사람이 이용함을 알 수 있습니다.    
     
#### 271A 버스 분석  
- 271A의 승하차 총 승객 수 정렬 결과, 합정역에서 가장 많은 승객이 승,하차 하는 것을 알 수 있습니다.  
  경험으로 미루어볼 때, 상암동에서부터 승차하신 후 합정역 2호선 4번 출구 앞 정류소에서 가장 많이 내리는 경험이 있습니다.  
- 그리고 승차승객수가 가장 많은 버스정류장은 메세나폴리스 정류장입니다.  
  2, 6호선 모두 이용할 수 있는 합정역에서 나와 망원동 - 성산동 - 상암동을 향하는 가장 가까운 버스정류장이기에 가장 많은 사람이 이용한다고 판단이 됩니다.  
- 그리고 가장 적은 승객수의 정류소는 회차지 점인 대덕동 주민센터입니다.  
    
     
-----
## 2) [12월_일자별_143버스_이용현황](https://github.com/heonsooo/Bus_Stations/blob/main/12%EC%9B%94_%EC%9D%BC%EC%9E%90%EB%B3%84_143%EB%B2%84%EC%8A%A4_%EC%9D%B4%EC%9A%A9%ED%98%84%ED%99%A9.ipynb)     
  
- 2020-12 데이터를 분석  
- 위에 했던 분석에서 시간이 한 달여 정도 지났기 때문에 데이터 탐색부터 다시 진행했습니다.  
- 데이터 탐색: 일자, 노선번호, 각 정류소 명에 따라 정렬이 되어있음을 확인했습니다.    
  row가 약 118만 개임을 확인했고, unique를 통해 중복되지 않은 노선번호와 그 개수를 구했습니다. (총 623개 노선)      
- 일자별로 나누어져 있는 걸 합쳐서 각 버스 노선별로 12월 한 달 동안 승,하차 승객수를 계산하기 위해 새로운 Data Frame을 만들었습니다.       
- 그리고 새로운 column인 총 승객수를 새로 구했습니다.       
- sum 함수를 통해 일자와 상관없이 버스노선별 각 승객수의 합을 구하였고,  
  이를 통해 각 버스 노선(column : 노선번호), 승차 총 승객 수, 하차 총 승객 수,     
  총 승객수 4개의 clomps로 데이터프레임 생성했습니다.  
  이때, 한번에 모든 버스노선을 다 계산하게 되면, 시간이 오래 걸리고 만약 오류 발생 시 시간이 추가로 오래 걸리게 되므로 앞의 5개 버스노선으로 실행했습니다.        
-  위의 과정을 성공적으로 끝낸 후 모든 버스 노선에 대하여 노선번호, 승차 총 승객 수, 하차 총 승객 수, 총 승객수의 칼럼을 가지 data frame을 생성했습니다. 
   (이때, 승객수의 숫자 자리를 구분하기 위해 format을 사용했지만, sort_values(정렬)를 사용 시에 정렬이 자릿수별 크기로 정렬이 되어 이를 철회했습니다.)      
-  그후 in[17]에서 볼 수 있듯이, 총 623개 버스 노선에 대해 총 승객수 내림차순으로 정렬할 수 있었습니다.      
-  12월, 총 승객수 1,432,630명이 탑승했던 143번 버스를 선택 후      
   x : 일자 y: 총 승객수를 통해 일자별 총 승객수 변화를 시각화하여 나타내었습니다.      
- 주말 혹은 공휴일(크리스마스)에 눈에 띄게 승객이 적다는 것을 발견했습니다.    
- 주말보다는 평일에 버스 이용이 많다는 사실을 데이터 시각화를 통해 쉽게 확인할 수 있었습니다.
   
   
- 이를 통해 밑에서 진행한 서울 시내에서 운영하는 버스의 일자별 총 승객수 변동 그래프를 그릴 수 있게 되었습니다.
   
   
   ----
## 3) [12월_일자별_버스이용현황_변동그래프](https://github.com/heonsooo/Bus_Stations/blob/main/12%EC%9B%94_%EC%9D%BC%EC%9E%90%EB%B3%84_%EB%B2%84%EC%8A%A4%EC%9D%B4%EC%9A%A9%ED%98%84%ED%99%A9_%EB%B3%80%EB%8F%99%EA%B7%B8%EB%9E%98%ED%94%84.ipynb)    

- 위에서 특정 노선의 일자별 총 승객수 변동을 알 수 있었습니다.  
- 이를 통해 for문을 통해 각 노선에서 일자별 총 승객수 변동을 구할 수 있습니다.  
- 623개의 모든 버스 노선의 변동을 시각화 하려고 했지만,  
  상위30개, 하위 23개의 버스의 일자별 총 승객수 변동을 시각화 했습니다.  
  
 ----
   
## 4) [271분할_전,후.ipynb스).ipynb](https://github.com/heonsooo/Bus_Stations/blob/main/271%EB%B6%84%ED%95%A0_%EC%A0%84%2C%ED%9B%84.ipynb)  
#### 가장 많은 승,하차승객수 정류소  
- 271 A,B 나뉘기 전/후 비교
- 2020.03.20기준으로 분할이 되었습니다.
- 결과적으로 분할 후 총 승객수는 거의 절반 가까리 줄었습니다.
- 하지만 이 결과는 분할 이슈 이외에도 코로나19로 인해 승객수가 줄어들 영향도 크다고 판단했습니다.
- 가설을 검정하기 위해서는 잠복변수를 최소화 해야하는데 코로나19는 결과에 영향을 크게 미치는 하이퍼변수라고 생각합니다.
- 따라서 코로나 이전, 이후의 271 승객수 변동 추이로 결과를 지었습니다.

----
  
## 5) [코로나 전, 후 버스 승객 이용 분석 (7011 버스).ipynb](https://github.com/heonsooo/Bus_Stations/blob/main/%EC%BD%94%EB%A1%9C%EB%82%98%20%EC%A0%84%2C%20%ED%9B%84%20%EB%B2%84%EC%8A%A4%20%EC%8A%B9%EA%B0%9D%20%EC%9D%B4%EC%9A%A9%20%EB%B6%84%EC%84%9D%20(7011%20%EB%B2%84%EC%8A%A4).ipynb)

- 위에서 271 버스 결과에 흥미를 느껴 2019년 1월 - 2020년 12월까지의 일별 버스 승,하차 데이터를 수집했습니다.  
  출처 : 서울 열린 데이터 광장 url : http://data.seoul.go.kr/dataList/OA-12912/S/1/datasetView.do#   
  총 24개월, 24개의 csv파일을 사용했는데, 이 중에서 컬럼이름과 컬럼의 값들이 조금 다르게 저장된 데이터가 있어 전처리 후 진행했습니다.  
- 이를 통해 서울시 버스노선별 총 승객수의 변화 추이를 살펴볼 수 있는 분석 및 시각화를 진행했습니다.
- 본 분석에서는 7011버스를 실행했습니다.
- busid = '  ' 변수에 원하는 버스를 입력한다면, 원하는 버스 노선의 승객 변화 추이를 확인할 수 있습니다.
