![header](https://capsule-render.vercel.app/api?type=wave&color=auto&height=300&section=header&text=MobilePrograming%20Team5&fontSize=50)

## Overview ⭐️

- Application Name: 대중교톡
- 지도 어플을 이용한 대중교통 커뮤니티 어플
- 노원구에 있는 지하철역과 버스 정류장에 대한 채팅방을 열어 익명의 사람들과 대중교통 출발 및 도착에 대한 정보를 공유하는 어플

## Main application use-cases 🍪

- Community Mapping: 지도를 만드는 과정에서 지역사회 구성원과 이해관계자들의 관심을 유도하고 이들의 커뮤니티에 대한 계획 및 의사결정에 참여하도록 하는 총제적인 과정을 의미
<img width="30%" src="https://user-images.githubusercontent.com/94777814/234574023-1b96b41b-146c-4510-a3d9-cf2618ac0e62.PNG"/>
커뮤니티 맵핑
<img width="30%" src="https://user-images.githubusercontent.com/94777814/234574202-e0e01a97-e2e5-436d-a1da-3797d01b19cd.PNG"/>

## Expected Components to be used for our development 🔧

### 지도 서비스 구현 
- naverMap api를 사용해서 mapView를 구성
- mapView안에 Marker, infowindow, 현재위치기능, cameraposition update를 사용

### 장소 검색 기능
- webView를 사용 
- firebase에 다음 도로명주소 api를 적용시킨 html을 hosting하여 webView 페이지를 불러옴

### 지하철역 도착 정보
- Odsay api를 이용
- api를 통해 json 데이터를 받아와서 retrofitConnection를 이용하여 json 데이터를 원하는 데이터구조로 처리
- mapView 내의 각 지하철역의 마커의 infoWindow에 가장 가까운 시간 2개의 정보를 가져옴

 ### 알람 기능
 - spinner를 통해 원하는 지하철 역명을 가져옴 
 - 라디어그룹버튼을 이용해 원하는 지하철 방향을 가져옴
 - broadcastReceiver와 notificationManager, alarmManager를 활용하여 원하는 지하철 역, 방향에 대해 제일 가까운 시간에 대해 알람 기능 

###채팅 기능
- Firebase와 연동
- Firebase Storage와 연동

## Function implementation 🔧
- Geocoder : 지오코더 함수로 주소를 위경도로 바꿔준다.
- Rgeocoder : 역지오코더 함수로 위경도를 주소로 바꿔준다.
- setAlarm : AlarmReceiver에 알람을 설정하고 싶은 시간을 넘겨주며 알람을 설정해준다.
- getPublicTransportationData : odsay api를 활용하여 얻은 지하철역 시간표 데이터를 retrofiConnection과 retrofitApi를 활용하여 DTO에 맞게 가져온 후 원하는 지하철 시간표를 가져오는 함수이다.

## 어플 사진 
- 메인 Activity 및 mapFragment
<div style="display: flex;">
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/241951029-b4b368a4-9660-4429-900d-af740d4bcedb.png" />
  <img style="width: 20%;" src="https://user-images.githubusercontent.com/94777814/241951425-9fbbaf23-5cd8-4216-88da-ead1bd079a6a.png" />
</div>
- searchActivity
<div style="display: flex;">
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/241951547-09aca064-78f3-4b22-86f0-edd65db6b36a.png" />
  <img style="width: 20%;" src="https://user-images.githubusercontent.com/94777814/241951772-f89b1177-db90-4071-ae5b-fe9a77a239ce.png" />
</div>
- 알람 버튼을 눌렀을 때
<img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/241952037-c5b62fcf-bfce-49c2-bc2e-aca0f0fcb8a5.png" />
- 검색한 장소 마커 위치 버튼을 눌렀을때(사람모양버튼)
<img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/241952114-c636cc43-b109-4d4a-92f8-3de04b053f0b.png" />




## Development History 🌳
- [프로젝트 개발 히스토리 feat map](https://github.com/unso99/FirstAndroidProject/issues/2) 
- [프로젝트 개발 히스토리 feat chat](https://github.com/unso99/FirstAndroidProject/issues/5)
- [Project Proposal](https://github.com/unso99/FirstAndroidProject/blob/main/MobileProgramming_ProjectProposal_5%ED%8C%80.pdf)
- [최종 결과물(대중교톡)](https://github.com/unso99/FirstAndroidProject/tree/main/final)



