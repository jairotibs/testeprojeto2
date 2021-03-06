# testeprojeto2 [![Build Status](https://travis-ci.org/jairotibs/testeprojeto2.png?branch=master)](https://travis-ci.org/jairotibs/testeprojeto2)

Is an Travis test and deploy integration with an Android app using Gradle.
The Travis script (.travis.yml) is configured to customize the build.
The script here is configured like example below:


## Language (or framework) of the project
language: android

## Android-related dependecies
### Default components
android:
  components:
    - platform-tools
    - tools
    - android-22
    - build-tools-21.1.1
    - extra
  
### Additional components
    - extra-google-google_play_services
    - extra-google-m2repository
    - extra-android-m2repository
    - addon-google_apis-google-19

#### Specify at least one system image, if you need to run emulator(s) during your tests
    - sys-img-armeabi-v7a-android-19
    - sys-img-x86-android-17

## Set jdk version
jdk: oraclejdk8

## Allow email notifications
notifications:
  email: true

## Do before start the build
before_install:
    - sudo apt-get update -qq
    - chmod +x gradlew

## Scriptlet to run project (using android built-in gradle)
script:
  - ./gradlew tasks --all                   # See all the available tasks
  - ./gradlew init                          # Start gradle
  - ./gradlew androidDependencies           # Get the dependecies
  - ./gradlew clean                         # Clean enviroment
  - ./gradlew build                         # Build project itself (this tests and buid entire app)
  - ./gradlew assembleDebug                 # Assemble app in the VM

##### See the '.travis.yml' file for more info. Or enter Travis site in http://travis-ci.org
