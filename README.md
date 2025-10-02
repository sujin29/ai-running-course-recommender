# ai-running-course-recommender
n8n과 AI Agent를 활용하여 사용자 맞춤형 러닝 코스를 추천하는 워크플로우입니다. 
위치, 거리, 난이도 등을 입력하면 AI가 실제 존재하는 장소를 검증하고, 
도보 경로를 생성하여 카카오맵 링크로 제공합니다.

## 기술 스택
- 워크플로우: n8n
- AI 모델: gemini-2.5-flash
- 장소 검증: Kakao Maps API
- 경로 생성: OpenRouteService API
- 프롬프트 도움: Claude

## 주요 기능
1. 추천 코스 요약
2. 추천 코스 소개
3. 카카오맵 도보 경로 url

## 워크플로우 스크린샷
1. 전체 워크플로우
<img width="1261" height="716" alt="image" src="https://github.com/user-attachments/assets/826757b2-dbb8-494d-98eb-ccc843a65cb6" />

2. 메인 워크플로우
<img width="1249" height="495" alt="image" src="https://github.com/user-attachments/assets/497b8ae9-2e7c-47f9-8ba1-c6e2687d1b1e" />

3. 서브 워크플로우 (경로 생성)
<img width="1245" height="266" alt="image" src="https://github.com/user-attachments/assets/efcdac71-ae03-496d-94b1-6cf0ebfe2d42" />

## 필수 API 키
### 필수 요구사항
- n8n 설치
- 다음 API 키 발급:
  - [카카오 개발자센터](https://developers.kakao.com/)에서 REST API 키
  - [OpenRouteService](https://openrouteservice.org/)에서 API 키
  - Google Gemini API 키

### n8n 워크플로우 가져오기
1. n8n에서 워크플로우 Import
2. `20250923 - 지도api연결.json` 파일 업로드
3. API 키 설정
   - `search_place` 노드: 카카오 API 키 입력
   - `api로 도보경로만들기` 노드: OpenRouteService 키 입력
   - Google Gemini credentials 설정

## 개발 과정 상세 → 벨로그 학습일지
https://velog.io/@sujinzzang/series/AI%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-DT-%EC%84%9C%EB%B9%84%EC%8A%A4-%EA%B8%B0%ED%9A%8D%EC%9E%90

## 배운점
1. n8n 이틀 배워서 프로젝트 진행한건데 n8n은 정말 신세계다.
   1-1. 파이썬으로 하던 API 연동이 너무 쉽다.
   1-2. AI를 이용한 서비스도 너무 간편하다. 
2. 도보 길찾기 API는 네이버, 카카오 모두 제공하지 않았다. 대안으로 API를 탐색하는 것도 공부가 되었다.
3. AI Agent와 외부 API를 결합하여 장소를 검증하고, 도보 경로를 생성하는 프로세스를 구현해 보았다.
   도보 경로의 경우, 카카오맵과 네이버지도를 통해 도보 경로를 제공할 예정이기 때문에 외부 API를 통해 경로를 생성할 필요는 없지만
   추후 지도 시각화를 한다면 도보 경로를 그릴 수 있는 geojson을 얻는 것까지 진행해보았다.

## 향후 계획
1. 네이버지도 도보 경로 url 추가
2. web에 연결해서 서비스화
3. 날씨 정보 연동
4. 구글맵스를 활용한 해외 러닝 코스 추천
