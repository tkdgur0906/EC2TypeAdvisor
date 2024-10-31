## EC2TypeAdvisor

<p align="center">
  <img src="https://github.com/tkdgur0906/EC2TypeAdvisor/assets/39580658/35284182-4989-41ed-951b-2ae67fbb77e3" width="250">
</p>

## 📃프로젝트 소개

ETA는 서비스의 트래픽에 따른 EC2의 하루동안의 CPU 사용량을 측정하고 분석합니다.

측정한 CPU 사용량을 바탕으로 적절한 EC2 인스턴스 타입과 추천 이유와 함께 Slack을 통해 전송합니다.

또한 추천된 서버의 예상 Credit Balance 사용량을 그래프로 제공합니다.

T 타입 인스턴스를 사용하는 경우에는 Credit Balance가 0.5 이하가 될 경우 경보를 Slack을 통해 전송합니다.


<br>

## EC2 Daily Report

### 아키텍처
<p align="center">
  <img src="https://github.com/tkdgur0906/EC2TypeAdvisor/assets/39580658/35d43e02-19f7-4a76-af48-b79d8181161e" width="700">
</p>

- Schedule를 통해 하루 한 번 분석 실행
- 모든 인스턴스의 상태를 cloudwatch, cloudwatch Agent 활용하여 수집
- EC2 상태 분석 및 데이터 기반 적절한 인스턴스 Type 추천 메시지 생성
- Credit Balance 예측 그래프 생성 후 S3 저장 및 이미지 slack 전송
- Incoming webhook Daily Report 생성

<br>

### 실행 결과
<p align="center">
  <img src="https://github.com/tkdgur0906/EC2TypeAdvisor/assets/39580658/3f59cc4b-1a97-489c-85cc-d3c801774302" width="350">
</p>

## Credit Balance 알리미

### 아키텍처
<p align="center">
  <img src="https://github.com/tkdgur0906/EC2TypeAdvisor/assets/39580658/8e9b243f-ecc9-4ca2-8ad2-6328fcc465c7" width="700">
</p>

- 사용자의 모든 T 타입 인스턴스 모니터링
- CloudWatch 알림으로 CreditBalance ≤ 0.5인 경우 SNS Trigger
- SNS Topic 통해 Lambda 에 상태 정보 전달
- 인스턴스 정보를 담은 메시지 생성 및 전송
- Incoming webhook 실시간 알림 생성

<br>

### 실행 결과
<p align="center">
  <img src="https://github.com/tkdgur0906/EC2TypeAdvisor/assets/39580658/8f88d8b5-fc2e-4d6f-a0ec-9b6321910610" width="350">
</p>


## 시연 영상

<p align="center">
  <video src="https://github.com/tkdgur0906/EC2TypeAdvisor/assets/39580658/5bfbaf56-8550-43fd-b0c4-3ef6365a227d" width="20">
</p>



