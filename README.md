# 개발 워크스테이션 구축 실습

## 1. 프로젝트 개요

Linux 터미널, Docker, Git 및 GitHub를 활용하여 개발 환경을 구축하고, 컨테이너 실행과 웹 서버 배포를 실습한다.

## 2. 실행 환경

- 운영체제: Windows 11
- Linux 환경: WSL2
- Linux 배포판: Ubuntu
- 터미널: Ubuntu 터미널
- Docker: 설치 완료, 버전 확인 예정
- Git: 설치 및 연동 완료

## 3. 터미널 기본 조작 및 권한 실습

### 3-1. 개발 폴더 생성 및 이동

실습 경로:

`/home/kkimzzi/development-workstation/terminal-practice`

실행 명령:

```bash
cd ~
pwd
mkdir -p development-workstation
cd development-workstation
mkdir terminal-practice
cd terminal-practice
pwd
```

### 3-2. 파일 권한 실습

파일 `permission.txt`를 생성하고 권한을 확인하였다.

```bash
touch permission.txt
ls -l permission.txt
chmod 644 permission.txt
ls -l permission.txt
```

결과:

```text
-rw-r--r-- 1 kkimzzi kkimzzi 0 Nov 21 18:09 permission.txt
```

### 3-3. 디렉터리 권한 실습

```bash
mkdir permission-folder
ls -ld permission-folder
chmod 755 permission-folder
ls -ld permission-folder
```

결과:

```text
drwxr-xr-x 2 kkimzzi kkimzzi 4096 Nov 21 18:10 permission-folder
```

### 3-4. 권한의 의미

- 터미널 기본 조작 및 권한: 실습 완료 (증거 사진 미첨부)
- Docker 기본 점검: 실습 완료 (증거 사진 미첨부)- 터미널 기본 조작 및 권한: 실습 완료 (증거 사진 미첨부)
- Docker 기본 점검: 실습 완료 (증거 사진 미첨부)- r: 읽기 권한
- w: 쓰기 권한
- x: 실행 또는 디렉터리 접근 권한
- 644: 소유자는 읽기·쓰기, 다른 사용자는 읽기
- 755: 소유자는 읽기·쓰기·실행, 다른 사용자는 읽기·실행

## 4. 실습 증거

- 터미널 기본 조작 및 권한: 실습 완료 (증거 사진 미첨부)
- Docker 기본 점검: 실습 완료 (증거 사진 미첨부)

## Docker 실습 결과

- Docker Desktop과 WSL2 Ubuntu 연동 완료
- Docker 버전: 29.9.2
- Docker Compose 버전: v5.6.1
- docker ps 실행 성공
- hello-world 컨테이너 실행 성공
- Ubuntu 26.04.1 LTS 컨테이너 실행 성공
- 컨테이너 내부 운영체제 정보 확인 완료
- exit 명령어로 컨테이너 종료 완료

## Docker 웹 서버 실습

- Dockerfile 및 index.html 작성 완료
- Docker 이미지 이름: my-first-web
- Nginx 웹 서버 컨테이너 실행 성공
- 포트 연결: 8080:80
- 접속 주소: http://localhost:8080
- Windows 브라우저에서 웹 페이지 출력 확인
- 증거 화면: evidence/03-docker-web-success.png

## Docker Bind Mount 실습

- Nginx 컨테이너 이름: my-web-mount
- 호스트 폴더와 컨테이너 웹 폴더 연결
- index.html 수정 후 웹 페이지 변경 확인
- 이미지 재빌드 없이 변경 사항 반영 성공
- 증거 화면: evidence/04-bind-mount-success.png

## Docker Volume 실습

- Docker Volume 이름: my-data
- Docker Volume 생성 및 목록 확인 완료
- Ubuntu 컨테이너에서 test.txt 파일 저장
- 임시 컨테이너 삭제 후 새 컨테이너에서 데이터 확인
- Docker Volume 데이터 영속성 확인 성공
- 확인 결과: Docker Volume Test Success
- 증거 화면: evidence/05-docker-volume-success.png
