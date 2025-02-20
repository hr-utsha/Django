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
```

<h4> models.py </h4>

```python
from django.db import models

# Create your models here.
class Contact(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField(unique=True)
    image = models.ImageField(upload_to='uploads/', null=True, blank=True)
```


<h4> views.py </h4>

```python
from django.shortcuts import render,HttpResponse
from . import models

# Create your views here.
def contact(request) : 
    if request.method == 'POST' :
        name = request.POST.get('name')
        email = request.POST.get('email')
        image = request.FILES.get('image')

        contact = models.Contact(name=name,email=email,image=image)
        contact.save()

        return HttpResponse("succesfully added.")

    return render(request,'contact/index.html')
```


<h4> template </h4>

```python
<form method="POST" enctype="multipart/form-data">
    {% csrf_token %}
    <div class="mb-3">
        <input type="text" class="form-control" id="exampleInputEmail1"  name="name">
    </div>
    <div class="mb-3">
        <input type="email" class="form-control" id="exampleInputPassword1" aria-describedby="emailHelp" name="email">
    </div>
    <div class="mb-3">
        <input type="file" class="form-control" id="exampleInputImage" name="image">
    </div>

    <button type="submit" class="btn btn-primary">Submit</button>

</form>

```










