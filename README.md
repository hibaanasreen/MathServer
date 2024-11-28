# Ex.05 Design a Website for Server Side Processing
## Date:
28/11/24
## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
views.py

from django.shortcuts import render 
def lampspower(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('I','0')
        r = request.POST.get('R','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = (int(i)*int(i))* int(r) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r 
        print('Power=',power) 
    return render(request,'serverapp/server.html',context)
```
```
urls.py

from django.contrib import admin 
from django.urls import path 
from serverapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('lampspower/',views.lampspower,name="lampspower"),
    path('',views.lampspower,name="lampspower")
]
```
```
server.html

<html>
    <head>
        <title>power of a lamp</title>
        <style>
            body{
                background-color: rgb(128, 223, 246);
            }
            h1{
                background-color: rgb(249, 176, 202)
            }
            form{
                background-color: rgb(248, 242, 137)
            }
        </style>
    </head>
    <body>
        <h1 align="center">POWER OF INCANDESCENT LAMP</h1>
        <form align="center"method="post">
            {% csrf_token %}
            Intensity (amp): <input name="I" value="{{i}}">
            <br>
            <br>
            Resistance(ohm): <input name="R" value="{{r}}">
            <br>
            <br>
            <input type="submit" value="ENTER">
            <br>
            <br>
            Power(watts): <input name="power"value={{power}}>
        </form>
    </body>
</html>
```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-11-28 224307.png>)
## HOMEPAGE:
![alt text](<Screenshot 2024-11-28 224246.png>)

## RESULT:
The program for performing server side processing is completed successfully.
