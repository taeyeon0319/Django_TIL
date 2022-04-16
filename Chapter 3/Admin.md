# Admin
------------
> ## Admin이란?
+ 계정생성 : python manage.py createsuperuser
+ 데이터 검색, 추가, 삭제, 수정 등 관리가 가능하다.
</br>

+ admin.py
```
from django.contrib import admin
from .models import Post, Comment

admin.site.register(Post)
admin.site.register(Comment)

```
↑ Django에 Posts, Comments 모델 생성됨
</br></br>

> ## Admin 커스터마이징하기
    > ### 기본적인 Admin 커스터마이징

    + ModelAdmin옵션['https://docs.djangoproject.com/en/4.0/ref/contrib/admin/']
    ```
    @admin.register(Post)
    class PostModelAdmin(admin.ModelAdmin):
        list_display = ('id', 'content') 
        # ↑ 모델의 속성명을 넣어서 admin페이지에 보이게 함.
        list_editable = ('content', ) 
        # ↑ 모델의 속성명을 넣어서 admin페이지에서 수정가능하게함
        list_filter = ('created_at', )
        # ↑ admin페이지에 필터가 생김
        search_fields = ('id', 'writer_username')
        search_help_text = '게시판번호, 작성자 검색이 가능합니다.'
        # ↑ admin페이지에 검색기능
    ```
