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

### 실시간 지하철역 도착 정보
- Odsay api를 이용
- api를 통해 json 데이터를 받아와서 retrofitConnection를 이용하여 json 데이터를 원하는 데이터구조로 처리
- mapView 내의 각 지하철역의 마커의 infoWindow에 가장 가까운 시간 2개의 정보를 가져옴

### 알람 기능
- spinner를 통해 원하는 지하철 역명을 가져옴 
- 라디어그룹버튼을 이용해 원하는 지하철 방향을 가져옴
- broadcastReceiver와 notificationManager, alarmManager를 활용하여 원하는 지하철 역, 방향에 대해 제일 가까운 시간에 대해 알람 기능 

### 채팅 기능
- Firebase Authentication을 사용하여 사용자 인증을 처리, <br>signAnonymously()를 활용하여 사용자를 익명으로 등록
- Firebase Realtime Database를 사용하여 채팅 메시지를 저장,<br> 메시지를 작성하면 데이터베이스에 저장하고, 변경사항을 실시간으로 감지하여 화면에 업데이트
- Intent를 사용하여 카메라 어플로 이동
- Firebase Storage를 사용하여 이미지를 업로드, <br>업로드한 이미지의 URL을 Realtime Database에 저장하여 채팅방에 이미지를 표시

## Function implementation 🔧
- Geocoder : 지오코더 함수로 주소를 위경도로 바꿔준다.
- Rgeocoder : 역지오코더 함수로 위경도를 주소로 바꿔준다.
- setAlarm : AlarmReceiver에 알람을 설정하고 싶은 시간을 넘겨주며 알람을 설정해준다.
- getPublicTransportationData : odsay api를 활용하여 얻은 지하철역 시간표 데이터를 retrofiConnection과 retrofitApi를 활용하여 DTO에 맞게 가져온 후 원하는 지하철 시간표를 가져오는 함수이다.
- getInstance : retrofit 객체를 반환하는 함
- putMessage : 채팅창에서 입력한 메시지 Firebase database에 push하는 함수
- getMessage : 메시지 database에서 event가 발생했을 때 메시지를 firebase에서 가져오는 함수
- getDateTimeString : 현재 날짜 및 시간을 문자열로 반환하여 메시지 보낸 시각 불러오는 함수
- TakePicture : Intent를 활용하여 카메라 앱으로 이동하는 함수
- sendImage : 촬영한 이미지 메시지를 Firebase database에 push하는 함수
- uploadImageToFirebase : 사진촬영한 이미지를 Firebase Storage에 업로드하고 업로드한 이미지의 URL을 얻어와 sendImage를 호출하는 함수
- getDateText : adpater에서 전달된 날짜 및 문자열을 "오전 HH:mm" 혹은 오후 HH:mm" 형식으로 변환하여 문자열로 반환하는 함수

## 어플 사진 
- 메인 Activity 및 mapFragment
<div style="display: flex;">
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242008893-11c46c97-0b08-4622-9d81-aede21b8006a.png" />
</div>
- 지하철이 없을 때
<img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242030263-b374a811-935d-4a77-9f07-cc533daa164c.png" />
- 알람 버튼을 눌렀을 때
<div style="display: flex;">
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242006211-eed06a26-f4db-42b5-bd12-ad707e33ad35.png" />
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242007416-73161962-e883-4b08-a9ec-133eac3ca98b.png" />
</div>
- searchActivity
<div style="display: flex;">
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242006226-cb7e35b1-5333-4508-8f40-905493f51428.png" />
  <img style="width: 20%;" src="https://user-images.githubusercontent.com/94777814/242006231-f3f4701d-e9de-42a1-9b4b-e444e3cd16b9.png" />
</div>
- 검색한 장소 마커 위치 버튼을 눌렀을때(사람모양버튼)
<img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242006238-8cc7888e-c029-4304-afe9-6c29cefb1c25.png" />
- chatFragment
<div style="display: flex;">
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242006263-90a957bb-66e2-4387-a2b9-4810b7cc26d3.png" />
  <img style="width: 20%;" src="https://user-images.githubusercontent.com/94777814/242006270-45b82099-8d94-4f3a-8dfb-bdd77c9b6da6.png" />
</div>
- 카메라 버튼을 눌렀을 때
<div style="display: flex;">
  <img style="width: 20%; margin-right: 10px;" src="https://user-images.githubusercontent.com/94777814/242006274-7c1eccca-d9a7-4351-82ef-f4fe1c281749.png" />
  <img style="width: 20%;" src="https://user-images.githubusercontent.com/94777814/242006301-2f3e88d6-388c-4025-9ac6-0d1d3bfd72b6.png" />
</div>
-다른 사람의 채팅
<img style="width: 20%;" src="https://user-images.githubusercontent.com/94777814/242009145-f3398a50-46b1-429b-8ffb-2af43508a4e0.png" />






## Development History 🌳
- [프로젝트 개발 히스토리 feat map](https://github.com/unso99/FirstAndroidProject/issues/2) 
- [프로젝트 개발 히스토리 feat chat](https://github.com/unso99/FirstAndroidProject/issues/5)
- [Project Proposal](https://github.com/unso99/FirstAndroidProject/blob/main/MobileProgramming_ProjectProposal_5%ED%8C%80.pdf)
- [최종 결과물(대중교톡)](https://github.com/unso99/FirstAndroidProject/tree/main/final)



