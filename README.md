# min-alpine-android-sdk
A Dockerfile for a minimal Android SDK install using Alpine Linux

## Introduction
There are numerous challenges to getting an Android project to build inside a Docker container

- The Android SDK is large, and the CLI is cumbersome. 
- Alpine uses different C libraries than other Linux variants.
- Android SDK requires JDK8, which has known issues with some C libraries
- The Linux Android SDK requires a 32 bit compatibility library (ia32-libs) which ubuntu has, but Alpine does not

This image works, and isn't massive like many of the Ubuntu based images

## Install

`docker pull tabrindle/min-alpine-android-sdk:latest`
 
 OR
 
 Dockerfile:
```
  FROM tabrindle/min-alpine-android-sdk:latest
```
 
## Usage

An example of building a Cordova based Android project on this machine:

```bash
	docker run -t -u root -v `pwd`:/workspace tabrindle/min-alpine-android-sdk:latest /bin/bash -c \
  "cd workspace/platforms/android && ./gradlew cdvBuildDebug -Dorg.gradle.daemon=true -Pandroid.useDeprecatedNdk=true"
```
