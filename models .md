
<h3> models.py </h3>

```python
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField(unique=True)
    password = models.CharField(max_length=255)  # Consider hashing passwords instead of storing them as plain text

    def __str__(self):
        return self.name
```

<h3> models.py </h3>

```python

from django.contrib import admin
from .models import User

admin.site.register(User, UserAdmin)

```

