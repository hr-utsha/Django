Django-তে মূলত দুই ধরনের ফর্ম ব্যবহৃত হয়:
<ol>
  <li>Forms API: forms.Form </li>
  <li> Model Forms: forms.ModelForm </li>
</ol>
<ul> 
  <li> যদি ফর্মের ডেটাবেজের সাথে সরাসরি সংযোগ না থাকে, তাহলে forms.Form ব্যবহার করুন।</li>
  <li> যদি ফর্মের ডেটাবেজ মডেলের সাথে সংযুক্ত থাকে, তাহলে forms.ModelForm ব্যবহার করা ভালো।</li>
</ul>

