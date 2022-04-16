# QuerySet API
------------
> ## QuerySet API란?
+ Query : DB에 정보를 요청하는 것
+ QuerySet : DB에서 전달 받은 객체의 목록
+ QuerySet API : DB에 요청하기 위한 인터페이스
+ 공식문서 : https://docs.djangoproject.com/en/4.0/ref/models/querysets/#queryset-api-1 -> QuerySet반환하는/반환하지않는 메서드 확인

+ Django shell
    + 파일썬 인터프리터 형식으로 장고 사용
    + Model을 import하여 사용 가능
    + 터미널창 - python manage.py shell

+ Database Tool
    + 데이터베이스에 관리를 위한 도구
    + 툴을 활용하여 테이블이나 데이터를 조작
    + GUI(Graphical User Interface)제공
    + 다운로드 : https://dbeaver.io/ 

> ## QuerySet API를 구축해보며 Model 수정과 삭제 이해하기
+ 
    + Post.objects.all() : 생성된 객체 확인
    + Post.objects.create(content='내용') : 객체 생성
    + Post.objects.all().count() : 생성된 객체 개수 확인
    + Post.objects.filter(content='내용') : '내용'과 같은 content를 가진 객체 검색
    + Post.objects.all().order_by('id') : 오름차순으로 출력
        + ('-id') : 내림차순
        + ('created_at') : 생성 순
        + ('-created_at') : 최신 순
    + 객체 수정하기 
        + 변수명 = Post.objects.번호()  ->  변수명.content='수정된 내용'  ->  변수명.save()  : 객체 수정
        ↓ 예시 ↓
        ```
        >>> first_post = Post.objects.first()
        >>> first_post.content = "수정한 내용입니다."
        >>> first_post.save()
        ```

        + Post.objects.update(content='수정된 내용')

    + Database Tool(dbeaver)를 사용해서 데이터 추가, 수정, 삭제가 가능하다. 


