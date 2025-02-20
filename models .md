
# models.py

<h3> String Fields : </h3>

```python
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField(unique=True)
    password = models.CharField(max_length=255) 

    def __str__(self):
        return self.name
```
<h3> Date & Time Fields : </h3>

```
models.DateField(auto_now_add=True)    # Stores only the date
models.TimeField(auto_now=True)        # Stores only the time
models.DateTimeField(auto_now_add=True, auto_now=True)  # Stores date and time
models.DurationField()                  # For time durations

```

# models.py

```python

from django.contrib import admin
from .models import User

admin.site.register(User, UserAdmin)

```

