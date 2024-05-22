
- 단어 설명

| 비교군               | 도커                                       |
| ----------------- | ---------------------------------------- |
| app store         | docker hub                               |
| program           | image<br>(docker hub에서 다운로드 해서 가지고 있는 것) |
| process<br>(실제동작) | container<br>(image를 실행하는 것)             |
- pull
	- docker hub에서 image를 받는 행위
- run
	- image를 실행시키는 것
	- image -> container
	- 컨테이너가 실행되며 컨테이너 안에 포함되어있는 실행되도록 조치되어있는 프로그램이 실행됨

![image](https://github.com/ohohdmswl/TIL/assets/132552661/f320f26d-8dd7-4b75-9c3c-eb84eafe4d7a)


### 🔔 docker hub 에서 필요한 image 다운 및 확인 방법
- URL
	- https://hub.docker.com/
- Explore > containers 

- ex) httpd (Apache Http WEB server) 다운로드
	- official image (공식)
	- https://docs.docker.com/ > reference > docker cli (https://docs.docker.com/reference/cli/docker/)
- **pull** (https://docs.docker.com/reference/cli/docker/image/pull/)
	- Download an image from a registry -> **이미지 다운로드**
	- `docker image pull [OPTIONS] NAME[:TAG|@DIGEST]`
		- `docker image pull httpd`
- **docker images** (https://docs.docker.com/reference/cli/docker/image/)
	- Manage images -> **다운로드 받은 이미지 관리**
	- `docker image`
 

```
>docker image pull httpd
Using default tag: latest
latest: Pulling from library/httpd
09f376ebb190: Pull complete
dab55b4abfc3: Pull complete
4f4fb700ef54: Pull complete
1a6d0283f224: Pull complete
1abf9110528c: Pull complete
7bacb8f85f3a: Pull complete
Digest: sha256:43c7661a3243c04b0955c81ac994ea13a1d8a1e53c15023a7b3cd5e8bb25de3c
Status: Downloaded newer image for httpd:latest
docker.io/library/httpd:latest

>docker image

Usage:  docker image COMMAND

Manage images

Commands:
  build       Build an image from a Dockerfile
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Display detailed information on one or more images
  load        Load an image from a tar archive or STDIN
  ls          List images
  prune       Remove unused images
  pull        Download an image from a registry
  push        Upload an image to a registry
  rm          Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

Run 'docker image COMMAND --help' for more information on a command.


>docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
httpd        latest    356125da0595   6 weeks ago   147MB


```

- 다운로드 받은 이미지 확인(GUI.ver)
![image](https://github.com/ohohdmswl/TIL/assets/132552661/8d2d9caa-ed8e-4c9c-b8f0-bddc8446230a)

