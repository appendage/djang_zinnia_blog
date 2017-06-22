# djang_zinnia_blog
## Install
pip install -r requirements.txt

settings.py
    'django.contrib.sites',
    'django_comments',
    'mptt',
    'tagging',
    'zinnia_bootstrap',
    'zinnia',
    'zinnia_ckeditor',
    'ckeditor',
    'ckeditor_uploader',

    'APP_DIRS': False,

    'loaders': [
	'app_namespace.Loader',
        'django.template.loaders.filesystem.Loader',
        'django.template.loaders.app_directories.Loader',
    ]

    SITE_ID = 1

    LANGUAGE_CODE = 'zh-hans'

    TIME_ZONE = 'Asia/Shanghai'
url.py
    from django.conf.urls.static import static
    from django.conf import settings
    urlpatterns = [
        url(r'^admin/', admin.site.urls),
        url(r'^', include('zinnia.urls')),
        url(r'^comments/', include('django_comments.urls')),
        url(r'^ckeditor/', include('ckeditor_uploader.urls')),
    ] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)    

## 添加上传图片
ckeditor/plugins/image/dialogs/image.js
    搜索 id:"Upload",hidden:!0
    替换为 id:"Upload",hidden:0

## error
错误提示：This results in error No named cycles in template. 'box1,box2' is not defined when rendering the blog entry.
解决方法：把标志     {% cycle box1,box2 %}   改为  {% cycle 'box1' 'box2' %} #全部含有的html都需要更改

2、'future' is not a registered tag library. Must be one of:  
django 1.8之后就不在兼容 future,并且在django 1.10中已去掉future
解决方法：把    {% load firstof from future %}  这句话去掉以兼容django 1.1














beautifulsoup4 (4.6.0)
Django (1.10.7)
django-app-namespace-template-loader (0.4.1)
django-blog-zinnia (0.18.1)
django-ckeditor (5.2.2)
django-contrib-comments (1.8.0)
django-mptt (0.8.7)
django-tagging (0.4.5)
django-xmlrpc (0.1.7)
gunicorn (19.7.1)
Markdown (2.6.8)
mots-vides (2015.5.11)
olefile (0.44)
Pillow (4.1.1)
pip (9.0.1)
Pygments (2.2.0)
pyparsing (2.2.0)
pytz (2017.2)
regex (2017.6.7)
setuptools (36.0.1)
six (1.10.0)
sorl-thumbnail (12.3)
uWSGI (2.0.15)
wheel (0.29.0)
zinnia-theme-bootstrap (0.5.1)
zinnia-wysiwyg-ckeditor (1.3)
zinnia-wysiwyg-markitup (1.2)

django==1.10.7
django-blog-zinnia==0.18.1
zinnia-theme-bootstrap==0.5.1
django-app-namespace-template-loader==0.4.1
zinnia-wysiwyg-ckeditor==1.3

