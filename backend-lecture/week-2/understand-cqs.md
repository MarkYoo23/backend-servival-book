# CQS 이해하기

## CRUD

* Create
* Read
* Update
* Delete

## CQS

CRUD를 특징에 따라 구분

* Command : 상태가 변함, 안전하지 않음
  * Create
  * Update
  * Delete  
* Query : 상태가 변하지 않음
  * Read

## Http Method with CQS

* GET - Read
* POST - Create
* Put, Patch - Update
* DELETE - Delete

## CQS의 예시 1 (직접 게시물)

* Get /posts - Read : 게시물 목록
* Get /posts/{id} - Read : 게시물 상세
* Post /posts - Create : 게시물 생성
* Put(Patch) /posts/{id} - Update : 게시물 수정
* Delete /posts/{id} - Delete : 게시물 삭제

Bulk Update, Bulk Delete은 Collection을 활용

## CQS의 예시 2 (간접 게시물)

* Get /comments - 전체 댓글 목록
* Get /comments?post_id={post_id} - 특정 게시물의 댓글 목록
* Get /comments/{id} - 특정 댓글 상세
* Post /comments - 댓글 생성 (Body에 post_id가 있어야 함)
* Post /comments?post_id={post_id} - 특정 게시물에 대한 댓글 생성
* PUT(Patch) /comments/{id} - 댓글 수정
* DELETE /comments/{id} - 댓글 삭제

## CQS의 예시 2 (간접 게시물 - 하위로 표현)

* Get /posts/{post_id}/comments - 특정 게시물의 댓글 목록
* Get /posts/{post_id}/comments/{id} - 특정 게시물의 특정 댓글 상세
* Post /posts/{post_id}/comments - 특정 게시물에 대한 댓글 생성
* PUT(Patch) /posts/{post_id}/comments/{id} - 특정 게시물의 특정 댓글 수정
* DELETE /posts/{post_id}/comments/{id} - 특정 게시물의 특정 댓글 삭제

## 로그인

* POST /session - 로그인(세션 생성)
* DELETE /session - 로그아웃
* Get /session - 로그인 여부 확인
* Get /user/me - 내 정보 조회


