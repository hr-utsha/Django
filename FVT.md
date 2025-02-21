<h3>forms.py</h3>

```
from django import forms

class UserForm(forms.Form):
    name = forms.CharField(
        label='Name',
        max_length=100,
        widget=forms.TextInput(attrs={'class': 'form-control', 'placeholder': 'Enter your name'})
    )
    email = forms.EmailField(
        label='Email',
        widget=forms.EmailInput(attrs={'class': 'form-control', 'placeholder': 'Enter your email'})
    )
    password = forms.CharField(
        label='Password',
        widget=forms.PasswordInput(attrs={'class': 'form-control', 'placeholder': 'Enter your password'})
    )

```

<h3> views.py </h3>

```
from django.shortcuts import render
from .forms import UserForm

def user_form_view(request):
    form = UserForm()
    if request.method == 'POST':
        form = UserForm(request.POST)
        if form.is_valid():
            # ফর্ম ডেটা প্রোসেস করতে চাইলে এখানে করতে পারো
            pass
    return render(request, 'user_form.html', {'form': form})

```
<h3> template </h3>

```
<div class="container mt-5">
        <h2>User Form</h2>
        <form method="post">
            {% csrf_token %}
            <div class="mb-3">
                {{ form.name.label_tag(class="form-label") }}
                {{ form.name }}
            </div>
            <div class="mb-3">
                {{ form.email.label_tag(class="form-label") }}
                {{ form.email }}
            </div>
            <div class="mb-3">
                {{ form.password.label_tag(class="form-label") }}
                {{ form.password }}
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
        </form>
</div>
```
