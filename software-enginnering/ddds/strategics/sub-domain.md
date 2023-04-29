# 서브 도메인

## 정의

* 거대한 도메인을 영역화 해서 나누는 방법이다.

## 예시

### 속성과 행위로 나누는 방법

* 계좌(Account)
  * 속성
    * 계좌번호(Account Number)
    * 예금주(Owner)
    * 잔액(Balance)
  * 행위
    * 입금(Deposit)
    * 출금(Withdraw)
    * 계좌 개설(Open Account)
    * 계좌 폐쇄(Close Account)
* 고객(Customer)
  * 속성
    * 고객번호(Customer Number)
    * 이름(Name)
    * 주소(Address)
    * 전화번호(Phone Number)
    * ...
  * 행위
    * 가입
    * 탈퇴
* 대출(Loan)
  * 속성
    * 대출번호(Loan Number)
    * 대출금액(Loan Amount)
    * 대출일자(Loan Date)
    * 상환일자(Repayment Date)
    * 상환금액(Repayment Amount)
  * 행위
    * 대출 신청(Loan Application)
    * 대출 상환(Repayment)
    * 대출 연장(Extension)
    * 중도 상환(Early Repayment)
    * ...

### 절차등을 표현

* 다이어그램을 활용하여 속성과 행위의 절차에 대해서 정의한다.
