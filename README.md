# Ex.05 Design a Website for Server Side Processing
## Date:
27/11/24
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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power of a lamp</title>
    <style>
        body {
            background-color: rgb(232, 139, 246);
            font-family: 'Lora', serif;
        }
        .container {
            width: 400px;
            margin: 50px auto;
            text-align: center;
            background-color: rgb(244, 35, 122);
            color: rgb(0, 0, 0);
            padding: 20px;
            border: 3px dashed rgb(3, 16, 19);
            border-radius: 10px;
        }
        input[type="text"] {
            width: 80%;
            padding: 5px;
            margin: 10px 0;
        }
        input[type="submit"] {
            padding: 5px 10px;
            background-color: rgb(193, 2, 72);
            color: rgb(3, 246, 145);
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
    <h1>POWER OF A LAMP</h1>

    <form method="POST">
        {% csrf_token %}
        <label for="intensity">Intensity (I in Amps):</label>
        <input type="text" name="intensity" id="intensity" required><br><br>

        <label for="resistance">Resistance (R in Ohms):</label>
        <input type="text" name="resistance" id="resistance" required><br><br>

        <button type="submit"><b>select</b></button>
    </form>

    {% if power is not None %}
        <h2>Calculated Power: {{ power }} Watts</h2>
    {% endif %}
</div>
</body>
</html>
```
```
from django.shortcuts import render

def power_calculator(request):
    power = None  

    if request.method == 'POST':
        
        intensity = request.POST.get('intensity')
        resistance = request.POST.get('resistance')

        
        if intensity and resistance:
            try:
            
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('intensity=',I)
                print('resistance=',R)
                print('power=',power)  

            except ValueError:
                power = "Invalid input. Please enter numerical values."

    
    return render(request, 'serverapp/server.html', {'power': power})
```
```
from django.contrib import admin
from django.urls import path
from serverapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power_calculator, name='power_calculator'),  
]
```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-11-27 221937.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-11-27 221847.png>)

## RESULT:
The program for performing server side processing is completed successfully.
