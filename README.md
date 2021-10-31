# swift-arm64-docker
Dockerfiles for Swift-Arm releases

<img src="https://swift.org/assets/images/swift.svg" alt="Swift logo" height="70" >

### Docker images for [Swift-ARM](https://swift-arm.com).

#### You can find the Docker Hub repo here: [https://hub.docker.com/repository/docker/swiftarm/swift](https://hub.docker.com/repository/docker/swiftarm/swift)


### Usage

##### Pull the Docker image from Docker Hub:

```bash
docker pull swiftarm/swift
```

##### Create a container from the image and run it:

```bash
docker run -it swiftarm/swift /bin/bash
```

If you want to run the Swift REPL you will need to run the container with additional privileges:

```bash
docker run --security-opt seccomp=unconfined -it swiftarm/swift
```

### [Image Tags Available](https://hub.docker.com/repository/docker/swiftarm/swift)
* latest (ubuntu 20.04 swift 5.5.1)
* 5.5.1-debian-10
* 5.5.1-debian-buster
* 5.5.1-debian-11
* 5.5.1-debian-bullseye
* 5.5.1-ubuntu-18.04
* 5.5.1-ubuntu-bionic
* 5.5.1-ubuntu-20.04
* 5.5.1-ubuntu-focal
* 5.5.1-ubuntu-21.04
* 5.5.1-ubuntu-hirsute
* 5.5.1-ubuntu-21.10
* 5.5.1-ubuntu-impish