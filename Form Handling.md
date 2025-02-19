<h3> settings.py </h3>


```python
MEDIA_URL = '/media/'  
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```
<h4> urls.py </h4>

```python
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    ...,
    ...,
    ...,
]

if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
