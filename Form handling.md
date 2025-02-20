Django-তে মূলত দুই ধরনের ফর্ম ব্যবহৃত হয়:
<ol>
  <li>Forms API: forms.Form </li>
  <li> Model Forms: forms.ModelForm </li>
</ol>
<ul> 
  <li> যদি ফর্মের ডেটাবেজের সাথে সরাসরি সংযোগ না থাকে, তাহলে forms.Form ব্যবহার করুন।</li>
  <li> যদি ফর্মের ডেটাবেজ মডেলের সাথে সংযুক্ত থাকে, তাহলে forms.ModelForm ব্যবহার করা ভালো।</li>
</ul>

```
from django import forms

class MyForm(forms.Form):
    name = forms.CharField(max_length=100, required=True)
    email = forms.EmailField(required=True)
    phone = forms.RegexField(regex=r'^\+?1?\d{9,15}$')
    website = forms.URLField(required=False)
    age = forms.IntegerField(min_value=0, max_value=120)
    price = forms.FloatField()
    birth_date = forms.DateField(widget=forms.DateInput(attrs={'type': 'date'}))
```

<h3> 📅 Date & Time Field</h3>

```
birth_date = forms.DateField(widget=forms.DateInput(attrs={'type': 'date'}))
appointment_time = forms.TimeField(widget=forms.TimeInput(attrs={'type': 'time'}))
event_date = forms.DateTimeField()
duration = forms.DurationField()

```

<h3> ✅ Boolean Field : </h3>

```
agree = forms.BooleanField(required=True)
```

<h3> ✅ Choice Fields :  </h3>

```
GENDER_CHOICES = [('M', 'Male'), ('F', 'Female')]
gender = forms.ChoiceField(choices=GENDER_CHOICES)


interests = forms.MultipleChoiceField(choices=[('1', 'Sports'), ('2', 'Music')])
```
<h3> 📁 File & Image Fields </h3>

```
resume = forms.FileField()
avatar = forms.ImageField()
```

<h3> Example : </h3>

```
from django import forms

class UserProfileForm(forms.Form):
    name = forms.CharField(max_length=100, label='Full Name')
    email = forms.EmailField()
    age = forms.IntegerField(min_value=0)
    birth_date = forms.DateField(widget=forms.DateInput(attrs={'type': 'date'}))
    gender = forms.ChoiceField(choices=[('M', 'Male'), ('F', 'Female')])
    interests = forms.MultipleChoiceField(choices=[('sports', 'Sports'), ('music', 'Music')])
    profile_picture = forms.ImageField(required=False)
    agree_terms = forms.BooleanField(label='I agree to the terms and conditions')
```
