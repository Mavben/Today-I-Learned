# DockerFile

도커는 이미지를 기반으로 컨테이너가 생성된다. 컨테이너로 이미지를 생성하는 방법은
1. 도커 이미지를 통해 컨테이너를 생성한다.
2. 애플리케이션이 설치된다.
3. 컨테이너가 커밋된다.
4. 새로운 이미지가 생성된다.
이다.

위 방법은 애플리케이션이 동작하는 환경을 위해 일일이 패키지를 설치하고 소스코드를 깃(git)에서 복제해야 한다.

위의 과정을 쉽게 수행할 수 있는 빌드(build)명령어가 있다.

> 이것이 바로 Dockerfile!

완성된 이미지를 생성하기 위해 패키지, 소스코드, 명령어, 셸 스크립트 등을 하나의 파일에 기록해 두면 도커는 이 파일을 읽어 컨테이너에 작업을 수행한 뒤 도커 이미지로 만들어다.


### 도커 파일 뜯어보기

```
Dockerfile

FROM ubuntu:14.04
MAINTAINER alice106
LABEL "purpose"="practice"
RUN apt-get update
RUN apt-get install apache2 -y
ADD test.html /var/www/html
WORKDIR /var/www/htlm
RUN ["/bin/bash", "-c", "echo hello >> test2.html"]
EXPOSE 80
CMD apachectl -DFOREGROUND
```

- FROM : 생성될 이미지의 베이스가 될 이미지
- MAINTAINER : 이미지를 생성한 개발자의 정보
- LABEL : 이미지에 메타데이터 추가
- RUN : 이미지를 만들기 위해 컨테이너 내부에서 명령어 실행, 예제는 아파치 웹 서버 설치 이미지 생성
- ADD : 파일을 이미지에 추가
- WORKDIR : 명령어를 실행할 디렉터리, bash shell에서 cd 명령어를 입력한 것과 같은 기능
- EXPOSE : Dockerfile의 빌드로 생성된 이미지에서 노출할 포트 설정
- CMD : 컨테이너가 시작될 때마다 실행할 명령어 설정








