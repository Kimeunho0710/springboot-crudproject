# Chapter16 웹 페이지에서 댓글 목록 보기

## 댓글 레이아웃
댓글은 크게 두 영역으로 나뉩니다. 기존 댓글을 보여 주는 영역(_list)과 새 댓글을 입력하는 영역(_new)입니다.

## 댓글 뷰 파일의 구성
댓글 뷰 파일은 댓글 영역을 보여 주는 뷰 파일(_comments.mustache), 댓글 목록을 보여 주는 뷰 파일(_list.mustache), 새 댓글을 작성하는 뷰 파일(_new.mustache)로 나누어 작성합니다.   

## {{commentDtos}}{{/commentDtos}}
뷰 페이지에서 모델에 등록된 데이터의 사용 범위를 저정할 때 사용하는 머스테치 문법이다.  
{{commentDtos}}부터 {{/commentDtos}}까지 범위 내에서 commentDtos 데이터를 사용할 수 있으며 commentDtos 데이터의 수만큼 해당 범위를 반복한다.  
