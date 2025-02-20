
# models.py

<h3> String Fields : </h3>

```python
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField(unique=True)
    password = models.CharField(max_length=255) 
```
<h3> Date & Time Fields : </h3>

```
models.DateField(auto_now_add=True)                 
models.TimeField(auto_now=True)                        
models.DateTimeField(auto_now_add=True, auto_now=True) 
models.DurationField()                                 

```

<h3>File & Images Fields: </h3>

```
models.FileField(upload_to='uploads/') 
models.ImageField(upload_to='images/')   # (requires Pillow library)

```

<h3>Relationship Fields: </h3>

```
models.ForeignKey('OtherModel', on_delete=models.CASCADE)     # Many-to-One
models.OneToOneField('OtherModel', on_delete=models.CASCADE)  # One-to-One
models.ManyToManyField('OtherModel')                          # Many-to-Many

```
<br>
primary_key=True <br>
পরে কিছু add করলে default="nothing"

<h3> command line </h3>

```
python manage.py makemigrations
python manage.py migrate
```

# admin.py

```python

from django.contrib import admin
from .models import User
from . import Student

class StudentAdmin(admin.ModelAdmin):
    list_display = ['name','email','password']

admin.site.register(Student,StudentAdmin)

```

