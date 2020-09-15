# PUT vs PATCH 차이점 (권장사항)
- PUT : 자원의 "전체"를 교체하는 경우 (대체 개념). 요청시 자원내 모든 필드 전달 필요
- PATCH : 자원의 "부분"을 교체하는 경우. 요청시 변경하고자 하는 필드만 전달
- https://williamdurand.fr/2014/02/14/please-do-not-patch-like-an-idiot/


# Pagination 
- page, page_number 조합, 그리고  start_file, num_of_file 조합 중 뭐가 더 좋은 구조일까? 
- https://bcho.tistory.com/954 참고
  - Facebook API 스타일 : /record?offset=100&limit=25
