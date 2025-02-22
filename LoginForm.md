<h2>models.py</h2>

```
from django.db import models

# Create your models here.
class User(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    password = models.CharField(max_length=100)
```

<h2>forms.py</h2>

```
from django import forms
from .models import User

class UserForm(forms.ModelForm):
    class Meta:
        model = User
        fields = ['name', 'email', 'password']
        widgets = {
            'name': forms.TextInput(attrs={
                'class': 'form-control', 
                'placeholder': 'Enter your name',
                'id': 'name',
                'required': True
            }),
            'email': forms.EmailInput(attrs={
                'class': 'form-control', 
                'placeholder': 'Enter your email',
                'id': 'email',
                'required': True
            }),
            'password': forms.PasswordInput(attrs={
                'class': 'form-control', 
                'placeholder': 'Enter your password',
                'id': 'password',
                'required': True
            }),
        }
```

<h2>views.py</h2>

```
from django.shortcuts import render,redirect
from .forms import UserForm

# Create your views here.
def registration(request) :
    if request.method == 'POST':
        form = UserForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('success')  # Replace with your success URL
    else:
        form = UserForm() 

    data = {
        'form' : form,
    }
    return render(request,'registration/index.html',data)

```

<h2>template</h2>

```
<h2 class="text-center mb-4 mt-4">Registration Form</h2>

<div class="container mt-5">
    <form method="post" class="container">
        {% csrf_token %}
        <div class="mb-3">
            <label for="name" class="form-label"> Name </label>
            {{ form.name }}
        </div>
        <div class="mb-3">
            <label for="email" class="form-label">Email</label>
            {{ form.email }}
        </div>
        <div class="mb-3">
            <label for="password" class="form-label">Password </label>
            {{ form.password }}
        </div>
        <button type="submit" class="btn btn-primary">Login</button>
    </form>
</div>
```



