<div align="center">
    <img src="https://github.com/user-attachments/assets/a8bb22af-d53a-4c84-b575-ad634fc8429d">
    <h2></h2>  
    <p><b>커뮤니티형 중고차 거래 애플리케이션 서비스, 타볼카</b></p>
    <h4>
      <a href='https://www.figma.com/design/ckY510YXPKJJUoURVxlmYz/Cam'on?node-id=0-1&node-type=canvas&t=BIq7ck3oUBLHea8J-0'>🎨 Figma</a>
    </h4>
    <h3>
    </h3>
<br>
</div>
<br/>

# 🖼️ 프로젝트 기획 배경

1. 커뮤니티 기능(피드)과 **사용자 중심의 데이터 기반 추천 시스템**을 통해 거래 과정에서의 즐거움과 편리함을 제공하고자 했습니다.
2. **알림 기능**을 통해 관심 차량의 매물 정보 및 거래 상태를 제공 받고 싶었습니다.

# 🎯 핵심 기능

### ✅ 추천 기능

- 최초 로그인 시, 설문조사를 통해 차량을 추천 기능을 제공합니다.
- 일주일마다 전체 사용자 중 활동이 누적된 사용자의 추천 차량 리스트를 갱신합니다.

### ✅ 차량 등록 및 관리

- 유효한 차량 번호를 입력 받은 후 자동으로 차량 정보를 불러옵니다.
- 차량의 외부/내부 사진들과 부가 설명을 입력 받고 판매할 차량을 등록할 수 있습니다.
- 차량 등록 후, 관리자의 시세 측정이 끝나면 사용자는 판매 취소/승인 여부를 결정할 수 있습니다.

### ✅ 차량 조회

- 국내/해외/할인/인기 카테고리 별로 차량 매물 리스트를 조회할 수 있습니다.
- 브랜드, 모델 이름의 입력을 통한 검색 기능을 제공합니다.
- 차량의 색상, 연식, 주행 거리, 가격을 설정하여 차량을 조회할 수 있습니다.
- 정해진 주기마다 판매가 되지 않은 차량의 가격 할인을 진행합니다.

### ✅ 커뮤니티

- 피드(스토리)를 작성할 수 있고 삭제할 수 있습니다.
- 다른 사용자들의 피드를 볼 수 있고, 좋아요 및 좋아요 취소를 누를 수 있습니다.

### ✅ 편의 기능

- 관심 차량을 등록/취소 할 수 있으며 관심 차량 목록에서 여러 차량들을 비교할 수 있습니다.
- 관심 차량의 가격 하락/관심 차량 매물 등록/판매 차량의 시세 결과 알림을 제공합니다.
- 구매하고자 하는 차량이 존재하는 지점을 확인할 수 있습니다.
- 방문 예약을 접수할 수 있습니다.

### ✅ 관리자

- 회원과 1:1 상담 기능을 제공합니다.
- 회원의 리스트를 조회하고 회원 정보를 조회할 수 있습니다.
- 회원이 등록한 차량의 심사와 판매할 매물을 등록할 수 있습니다.

# 🚨 트러블 슈팅

### ❗ 웹 소켓 채팅

- **문제**: 웹 소켓으로 채팅 초기 구현 시, 관리자와 사용자가 동시 입장한 후에 채팅을 하지 않으면 둘 중 한 명만 입장했을 때 보낸 메시지를 볼 수 없었습니다.
- **해결**: STOMP와 DB를 사용하여 이전 채팅을 보관하도록 구현하여 해당 문제를 해결했습니다.

### ❗ WebView - Android 상호작용

- **문제**: 하이브리드 앱 개발 과정에서 웹(React)과 네이티브(Android) 간의 상호작용 구현에 어려움을 겪었습니다. 특히, 네이티브 기능을 웹에서 호출할 때 데이터가 정확하게 전달되지 않거나 동기화 문제로 예상치 못한 동작이 발생하는 경우가 있었습니다.
- **해결**: `JavaScriptInterface`를 활용해 원활한 통신을 구현했으며, 정확한 타입 정의를 통해 데이터를 보다 안정적이고 효율적으로 전달할 수 있도록 개선했습니다.

### ❗ 모바일 UI

- **문제**: 네이티브 앱 내부에서 렌더링되는 웹뷰의 특성에 맞게 모바일부터 태블릿까지 다양한 크기의 해상도를 고려하여 개발해야 하는 어려움이 있었습니다.
- **해결**: 처음 웹뷰 프로젝트를 초기 설정할 때, `GlobalStyle`과 레이아웃을 설정해두고 개발을 진행하여 개발 시 큰 어려움 없이 다양한 해상도에 맞는 UI를 개발할 수 있었습니다.

### ❗ 토큰 처리 / 로그인

- **문제**: 백엔드/프론트 서버의 도메인 주소가 달라서 서버에서 프론트로 토큰을 전송하는 과정에서 어려움이 있었습니다.
- **해결**: 프론트(유저)와 백엔드(관리자) 서버의 토큰 전달 방식과 검증을 다르게 처리하여 문제를 해결했습니다. 역할 별로 로그인 리다이렉션 URL이 달랐기 때문에 쿼리 파라미터/쿠키 방식을 섞어서 사용했습니다.

# ⚙️ 시스템 아키텍쳐

### 프론트엔드
![FE ARCH](https://github.com/user-attachments/assets/44c3c8b1-87d0-4e34-a2bc-f67841aab1fd)

### 백엔드
![BE ARCH](https://github.com/user-attachments/assets/6cca4538-1dd5-4bb3-a5d8-470824537d5d)

<br>

# 🛠️ 기술 스택

| 분야   | 기술 스택 |
| :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 공통   | ![Puppeteer](https://img.shields.io/badge/Puppeteer-white.svg?style=for-the-badge&logo=Puppeteer&logoColor=black) ![Firebase](https://img.shields.io/badge/firebase-a08021?style=for-the-badge&logo=firebase&logoColor=ffcd34) |
| FE     | ![Android Studio](https://img.shields.io/badge/android%20studio-346ac1?style=for-the-badge&logo=android%20studio&logoColor=white) ![Yarn](https://img.shields.io/badge/yarn-%232C8EBB.svg?style=for-the-badge&logo=yarn&logoColor=white) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![Styled Components](https://img.shields.io/badge/styled--components-DB7093?style=for-the-badge&logo=styled-components&logoColor=white) ![React Query](https://img.shields.io/badge/-React%20Query-FF4154?style=for-the-badge&logo=react%20query&logoColor=white) |
| BE     | ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white) |
| 인프라 | ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white) ![Amazon S3](https://img.shields.io/badge/Amazon%20S3-FF9900?style=for-the-badge&logo=amazons3&logoColor=white) ![Docker](https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![NginX](https://img.shields.io/badge/nginx-009639?style=for-the-badge&logo=nginx&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/githubactions-FF4438?style=for-the-badge&logo=githubactions&logoColor=white)             

<br>

# 👨‍👩‍👧‍👦 팀원 소개
| 김홍빈 | 송지웅 | 전우정 | 오은솔 | 오인우 | 장준혁 |
| :--: | :--: | :--: | :--: | :--: | :--: |
| <img src="https://github.com/vinivin153.png" width="150" height="150"> | <img src="https://github.com/moaangel.png" width="150" height="150"> | <img src="https://github.com/friend5hip.png" width="150" height="150"> | <img src="https://github.com/OHEUNSOL.png" width="150" height="150"> | <img src="https://github.com/inwoo0808.png" width="150" height="150"> | <img src="https://github.com/itcuna0617.png" width="150" height="150"> |
| [@vinvin153](https://github.com/vinivin153) | [@moaangel](https://github.com/moaangel) | [@friend5hip](https://github.com/friend5hip) | [@eunsol037](https://github.com/OHEUNSOL) | [@inwoo0808](https://github.com/inwoo0808) | [@itcuna0617](https://github.com/itcuna0617) |
| FE | FE | FE | BE | BE | BE |
