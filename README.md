# HelloWorld_cpp : C++ Source code for tests

## Objectives

Test the sonarQube environment :

* creata a simple .cpp file
* run basic C++ quality tools
* obtain a SonarQube (here sonarQube 7.4)


## Tools used (with their versions)

Ces logiciels doivent avoir été installés et configurés (versions utilisées entre parenthèses)

- CentOS 7.3
- gcc (4.8.5)
- sonarQube (7.4)
- sonar-scanner (3.3.0)
- cppcheck (1.80)
- valgrind (3.11.0)
- vera++ (1.3.0)
- rats (2.4)
- gcovr (3.3)
- doxygen (1.8.5)

## Installation

Download the project:

`$ git clone https://github.com/ExemplesDev/HelloWorld_cpp.git`

## Build the documentation:

`doxygen Doxyfile #other configuration:Doxyfile2)`

## Build the binary:

`$ g++ -ansi -pedantic -O0 -g -Wall --coverage HelloWorld.cpp -o HelloWorld


```

## Execute the quality tools

` cppcheck -v --enable=all --suppress=missingIncludeSystem . --xml . 2> cppcheck-report.xml
  vera++ -showrules -nodup *.cpp |& vera++Report2checkstyleReport.perl > vera++-report.xml HelloWorld.cpp
  rats --xml  -w 3 *.cpp > rats-report.xml HelloWorld.cpp
  gcovr -r . --html -o HelloWorld.html
  gcovr -r . --xml -o gcovr-report.xml
  valgrind --xml=yes --xml-file=valgrind-report.xml ./HelloWorld `

## sonarQube usage

* configuration file:

` 
# required metadata
sonar.projectKey=cpp:HelloWorld
sonar.projectName=Hello World ! 
sonar.projectVersion=1
# sonar.language=c++ # sonar 7.x : deprecated
# sonar.profile=Euclid prototype profile # set or unset depending of the tests

# path to source directories (required)
sonar.projectDescription=First usage of sonar with static and dynamic analysis (with std::cout)
sonar.sources=.
sonar.cxx.include_directories=.

# paths to the reports
sonar.cxx.cppcheck.reportPath=cppcheck-report.xml
sonar.cxx.vera.reportPath=vera++-report.xml
sonar.cxx.valgrind.reportPath=valgrind-report.xml
sonar.cxx.coverage.reportPath=gcovr-report*.xmll` 

Run sonarQube :

`$ sonar-scanner` 


