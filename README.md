# 개발 워크스테이션 구축 활동

## 1. 프로젝트 개요

Windows 11의 WSL2 Ubuntu 환경에서 Linux 터미널, Docker, Git 및 GitHub를 활용하여 개발 워크스테이션을 구축하였다.

기본적인 Linux 명령어와 파일 권한을 실습하고, Docker 컨테이너를 이용한 웹 서버 실행, Bind Mount 및 Volume의 데이터 관리 방법을 학습하였다.

## 2. 개발 환경

| 구분 | 내용 |
|---|---|
| 운영체제 | Windows 11 |
| Linux 환경 | WSL2 Ubuntu |
| Docker | Docker Desktop |
| Docker CLI | 29.9.2 |
| Docker Compose | v5.6.1 |
| Git | 2.53.0 |
| 프로젝트 경로 | `/home/kkimzzi/development-workstation` |

## 3. Linux 터미널 및 파일 권한 실습

### 3-1. 프로젝트 폴더 생성

```bash
cd ~
mkdir -p development-workstation
cd development-workstation
mkdir terminal-practice
cd terminal-practice
pwd
```

### 3-2. 파일 권한 변경

```bash
touch permission.txt
ls -l permission.txt
chmod 644 permission.txt
ls -l permission.txt
```

확인 결과:

```text
-rw-r--r-- 1 kkimzzi kkimzzi 0 Nov 21 18:09 permission.txt
```

### 3-3. 디렉터리 권한 변경

```bash
mkdir permission-folder
chmod 755 permission-folder
ls -ld permission-folder
```

확인 결과:

```text
drwxr-xr-x 2 kkimzzi kkimzzi 4096 Nov 21 18:10 permission-folder
```

권한의 의미:
- `r`: 읽기
- `w`: 쓰기
- `x`: 실행 또는 디렉터리 접근
- `644`: 소유자는 읽기·쓰기, 나머지는 읽기
- `755`: 소유자는 읽기·쓰기·실행, 나머지는 읽기·실행

### 3-4. 파일 이동 및 삭제 실습

파일 생성, 이름 변경, 삭제 명령어를 실습하였다.

실행 명령어:

```bash
touch move-test.txt
ls -l move-test.txt

mv move-test.txt renamed-test.txt
ls -l renamed-test.txt

rm renamed-test.txt
ls -l renamed-test.txt

## 4. Docker 기본 실습

Docker Desktop과 WSL2 Ubuntu를 연동한 후 Docker 명령어를 실행하였다.

주요 실습:
- Docker 및 Docker Compose 버전 확인
- `docker ps` 명령어 실행
- `hello-world` 컨테이너 실행 성공
- Ubuntu 26.04.1 LTS 컨테이너 실행
- 컨테이너 내부 운영체제 정보 확인
- 컨테이너 종료 및 Ubuntu 터미널 복귀

## 5. Docker 웹 서버 구축

Nginx를 이용하여 Docker 웹 서버를 구축하였다.

- Docker 이미지: `my-first-web`
- 웹 서버: Nginx
- 포트 연결: `8080:80`
- 접속 주소: `http://localhost:8080`
- Windows 브라우저에서 웹 페이지 출력 확인

Dockerfile:

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```

실습 증거: `evidence/03-docker-web-success.png`

## 6. Docker Bind Mount 실습

호스트의 웹 파일을 Nginx 컨테이너에 연결하였다.

- 컨테이너 이름: `my-web-mount`
- 호스트 폴더와 컨테이너의 웹 디렉터리 연결
- `index.html` 수정 후 웹 페이지 변경 확인
- Docker 이미지 재빌드 없이 변경 사항 반영 성공

실습 증거: `evidence/04-bind-mount-success.png`

## 7. Docker Volume 실습

Docker Volume을 생성하여 컨테이너 간 데이터 유지 여부를 확인하였다.

- Volume 이름: `my-data`
- Ubuntu 컨테이너에서 `test.txt` 생성
- 임시 컨테이너 종료 및 삭제
- 새 컨테이너에서 저장된 파일 확인
- 데이터 영속성 확인 성공

확인 결과:

```text
Docker Volume Test Success
```

실습 증거: `evidence/05-docker-volume-success.png`

## 8. Git 버전 관리

Git 저장소를 초기화하고 프로젝트 파일을 등록하였다.

```bash
git init -b main
git add .
git commit -m "Initial development workstation setup"
git status
```

첫 번째 커밋: `a385639`

확인 결과:

```text
On branch main
nothing to commit, working tree clean
```

## 9. 실습 결과 및 학습 성과

이번 활동을 통해 Linux의 기본 명령어와 파일 권한 관리 방법을 익혔다.

또한 Docker를 활용하여 웹 서버를 실행하고, Bind Mount와 Volume의 차이를 실제 실습으로 확인하였다.

마지막으로 Git을 활용해 프로젝트의 변경 이력을 기록하고, GitHub를 통한 원격 저장소 관리 방법을 학습하였다.
