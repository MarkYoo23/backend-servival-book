# DBMS

## 동기

* 데이터의 집합을 만들고, 저장 및 관리할 수 있는 기능들을 제공하는 응용 프로그램
* 일반적으로 디스크에 저장된 전체 데이터와 크기와 메인메모리가 수용 가능한 데이터의 사이즈는 매우 큰 차이가 난다. 그러므로 DBMS는 프로세스가 요구하는 페이지를 버퍼로 가져오고, 이후 새로운 페이지를 가져오기 위한 공간을 확보하기 위해서 기존에 메인메모리에 존재하는 페이지 중 일부를 선택해서 공간을 비워줘야 한다

## 특징

* 중복 제어: 동일한 데이터가 여러 위치에 중복 저장되는 현상을 방지한다. 데이터가 중복되면, 저장 공간이 낭비되고 데이터의 일관성이 깨질 수 있다.
* 접근 통제: DBMS는 사용자마다 다양한 권한을 부여할 수 있으며, 권한에 따라 데이터에 대한 접근을 제어할 수 있다.
* 인터페이스 제공 : DBMS는 사용자에게 SQL 및 CLI, GUI 등 다양한 인터페이스를 제공한다.
* 관계 표현: 서로 다른 데이터간의 다양한 관계를 표현할 수 있는 기능을 제공한다.
* 샤딩/파티셔닝: 구조 최적화를 위해 작은 단위로 쪼개는 기능을 제공한다.
* 무결성 제약 조건: 무결성에 관한 제약 조건을 정의/검사하는 기능을 제공한다. 데이터베이스는 반드시 무결성 제약조건을 통과한 데이터만을 저장하고 있어야 한다.

## 역사

* 1960년 제너럴 일렉트릭(GE)에 입사한 찰스 바크만은 GE의 제조생산라인을 관리하기 위한 MIACS(Manufacturing Information And Control System)을 구축하면서 프로그램 로직과 별도로 데이터를 독립적으로 관리하기 위해 IDS(Intergrated Data Store)를 만들었다

## 실제 사용 사례

* 오라클 DBMS
* MySQL DBMS
* PostgreSQL DBMS
* MariaDB DBMS
* Microsoft SQL Server DBMS

## 참고 자료

* [wikipedia](https://en.wikipedia.org/wiki/Database_management_system)
* [Namuwiki](https://namu.wiki/w/DBMS)
* [데이터넷 기사](https://www.datanet.co.kr/news/articleView.html?idxno=114558)

