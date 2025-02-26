# 프로젝트 front 단계 페이지별 설명

## 목차
1. [User Page](#user-page)
2. [Join Page](#join-page)
3. [Map Page](#map-page)
4. [Parking Page](#Parking-page)

------
## User Page
### 1. 기능 목적
- **로그인 및 회원가입**: 서비스 접근 전 회원가입 및 로그인을 통해 회원 정보를 데이터베이스 서버와 연동합니다.
- **인증 실패 알림**: 데이터베이스 서버와의 정보 불일치 시 인증 실패 알림 제공.
- **페이지 이동**: 로그인 성공 시 'maps' 페이지로 이동.
- **소셜 로그인 목표**: 카카오톡 및 구글 API를 이용한 소셜 로그인 서비스 제공 목표.

### 2. 기능 원리
#### 컴포넌트 구조
- **User**: 메인 로그인 컴포넌트.
- **useState**: 사용자 입력 및 에러 메시지 관리.
- **axios**: 서버와의 HTTP 통신 담당.
- **useNavigate**: 사용자 인증 후 페이지 이동 관리.

#### 서버 구조
- `axios`로 데이터 전송 및 로그인 정보 수신.
- 서버 주소: `http://localhost:8080/user`

-------------

## Join Page
### 1. 기능 목적
- **회원가입**: 아이디와 비밀번호를 통한 개인 계정 생성 및 데이터베이스 저장.
- **비밀번호 확인**: 비밀번호 일치 여부 확인.
- **인증 실패 알림**: 존재하는 아이디 또는 서버 통신 에러 시 알림 제공.
- **페이지 이동**: 회원가입 성공 시 'maps' 페이지로 이동.

### 2. 기능 원리
#### 컴포넌트 구조
- **Join**: 회원가입 처리 컴포넌트.
- **useState**: 입력 및 에러 메시지 관리.
- **axios**: 서버와의 HTTP 통신 담당.
- **useNavigate**: 페이지 이동 관리.

#### 서버 구조
- `axios`를 통한 데이터 전송 및 회원가입 정보 수신.
- 서버 주소: `http://localhost:8080/user/join`

-------------

## Map Page
### 1. 기능 목적
- **장소 표시**: 이용하고자 하는 장소의 주차장 위치 표시.
- **상세 정보 제공**: 특정 주차 공간에 대한 상세 정보 제공.

### 2. 기능 원리
#### 컴포넌트 구조
- **Map**: 메인 지도 컴포넌트.
- **useState**: 클릭된 마커 내용, ID, 주차장 데이터 관리.
- **useEffect**: 컴포넌트 마운트 시 주차장 데이터 가져오기 및 지도 초기화.
- **axios**: 서버로부터 주차장 데이터 가져오는 통신 담당.

#### 서버 구조
- `axios.get`으로 주차장 데이터 수신.
- 서버 주소: `http://localhost:8080/getParkingData`

#### 지도 및 마커
- **Kakao Maps API**: 지도 표시.
- **마커 설정**: 다양한 주차장 위치에 마커 표시.
- **마커 클릭 이벤트**: 마커 클릭 시 해당 주차장 정보 및 주차 가능 공간 수 표시.

---------------

## Parking Page

### 기능 목적

- **주차 공간 표시**: 사용자가 선택할 수 있는 주차 공간을 시각적으로 표시합니다.
- **주차 공간 선택 및 예약**: 사용자는 주차 공간을 선택하고 예약할 수 있습니다.
- **주차 공간 상태 업데이트**: 주차 공간의 현재 상태(점유 여부, 최적의 공간 등)를 실시간으로 업데이트합니다.

### 기능 원리

#### 컴포넌트 구조

- **BuildTwo**: 주차 공간을 선택하고 예약하는 메인 컴포넌트입니다.
- **useState**: 선택된 주차 공간, 주차 공간 데이터, 버튼 상태 등을 관리합니다.
- **axios**: 서버로부터 주차 공간 데이터를 가져오는 HTTP 통신을 담당합니다.

#### 서버 구조

- `axios.get`을 통해 `http://localhost:8080/parking_space/num2` 주소에서 주차 공간 데이터를 가져옵니다. 이 데이터는 각 주차 공간의 번호, 점유 여부, 주차장 위치 등을 포함합니다.

#### UI/UX 디자인

- 주차 공간은 동적으로 생성된 버튼으로 표시됩니다. 각 버튼은 해당 주차 공간의 현재 상태를 반영하는 색상으로 표시됩니다.
- 사용자가 주차 공간을 선택하면, 선택된 공간은 다르게 표시되어 사용자의 선택을 시각적으로 나타냅니다.
- `ToggleButtonGroup`을 사용하여 사용자가 주차 공간을 필터링할 수 있도록 합니다. 

## 사용 방법

1. 페이지를 방문하면, 사용 가능한 주차 공간이 버튼으로 표시됩니다.
2. 사용자는 원하는 주차 공간을 클릭하여 선택할 수 있습니다.
3. 선택한 주차 공간이 'Park here?' 상태가 되면, 사용자는 해당 공간을 예약할 수 있습니다.
4. 예약이 완료되면, 'Parked' 상태로 변경됩니다.
