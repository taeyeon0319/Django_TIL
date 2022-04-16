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
참고자료 : https://docs.djangoproject.com/en/4.0/ref/contrib/admin/' 
### 1. 기본적인 Admin 커스터마이징
+ ModelAdmin옵션
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

    readonly_fields = ('created_at', )
    # ↑ 수정은 불가능하나 읽는 것이 가능하다. 
```
</br>

### 2. 심화 Admin 커스터마이징
+ 댓글기능을 Post안에 넣기
```
class CommentInLine(admin.TabularInLine):
    model = Comment
    extra = 5
    min_num = 3
    max_num = 5

class PostModelAdmin(...):
    ...
    inlines = [CommentInLine]
```

+ Action(액션)기능 추가
```
class PostModelAdmin(...):
    ...
    actions = ['make_published']

    def make_published(modeladmin, request, queryset):
        for item in queryset:
            item.content= "운영 규정 위반으로 인한 게시글 삭제처리."
            item.save()
```