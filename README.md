## Homework

Вы продолжаете проходить стажировку в "Formatter Inc." (см [подробности](https://github.com/tp-labs/lab03#Homework)).

В прошлый раз ваше задание заключалось в настройке автоматизированной системы **CMake**.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в [прошлый раз](https://github.com/tp-labs/lab03#Homework). Настройте сборочные процедуры:
* используйте Github Actions для сборки на операционной системе **Linux** и **Windows**.

```sh
$ mkdir .github && cd .github
$ mkdir workflows && cd workflows
$ touch CI.yml
```

файл CI.yml:

```sh
name: CMake

on:
 push:
  branches: [main]
 pull_request:
  branches: [main]
  
jobs:
 build_Linux:
 
  runs-on: ubuntu-latest
  
  steps:
  - uses: actions/checkout@v3
  
  - name: Configure Solver
    run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build
    
  - name: Build Solver
    run: cmake --build ${{github.workspace}}/solver_application/build
    
  - name: Configure HelloWorld
    run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build
  
  - name: Build HelloWorld
    run: cmake --build ${{github.workspace}}/hello_world_application/build
    
 build_Windows:
 
  runs-on: windows-latest
  
  steps:
  - uses: actions/checkout@v3
  
  - name: Configure Solver
    run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build
    
  - name: Build Solver
    run: cmake --build ${{github.workspace}}/solver_application/build
    
  - name: Configure HelloWorld
    run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build
  
  - name: Build HelloWorld
    run: cmake --build ${{github.workspace}}/hello_world_application/build
```

```sh
$ git add .
$ git commit -m "add CI.yml and update README.md"
$ git push origin main
```
В Github Actions все прошло.

```
Copyright (c) 2015-2021 The ISC Authors
```
