"# Block-based autonomous driving" 

Spring Boot: REST API, 데이터베이스 관리,보안,트랜잭션에 장점
Node.js: WebSocket, 실시간 데이터 처리 비동기 I/O에 장점

둘다 사용한다면 두 개의 서버를 관리해야 하므로 배포와 유지보수 힘듬

#### 1.블록코딩 알고리즘 실행 및 처리
-사용자가 블록코딩을 작성한 자율주행 알고리즘을 서버에서 실행
-실행된 알고리즘을 차량 제어 시스템과 연동하여 실제 주행 테스트 진행

#### 2. 실시간 데이터 처리
-차량의 센서 데이터를 실시간으로 수집
-WebSocket 이용해 대시보드로 실시간 정보 전송
WebSocket은 전이중 통신 기능으로 인해 실시간 모니터링 시스템에서 매우 중요합니다. 환경 센서, 웨어러블 건강 장치, 인프라 모니터링 솔루션 등 매개변수의 지속적인 모니터링이 필요한 IoT 애플리케이션의 경우 
WebSocket은 센서에서 모니터링 대시보드로 실시간 데이터를 전송하여 이해관계자가 정보에 입각한 결정을 내릴 수 있도록 돕습니다.
-MQTT,WebSocket

#### 3.차량 제어 API 개발
-차량을 원격으로 제어할 수 있도록 제어 명령 API 제공
-블록토딩 알고리즘이 실행되면 해당 명령을 차량 시스템에 전달
-차량 상태 데이터를 서버에 저장

#### 4.서버 운영 및 클라우드 배포
-전체 시스템을 클라우드에서 배포 및 관리
-실시간 데이터 저장 및 로그
-서버 복구 및 유지보수
-AWS
