# Ex.04 Design a Website for Server Side Processing
# Date:28/11/2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
mons.html
<!DOCTYPE html>
<html>
<head>
    <title>Lamp Power Calculator</title>
    <style>
        body {
            background: linear-gradient(90deg,#5761B2, #1FC5A8); 
            
        }

        h1 {
            color: darkblue;
            font-size: 28px;
        }

        .container {
            background-color: #ffffff;  
            width: 500px;
            padding: 50px; 
        }

        label {
            font-size: 26px;
            color: #333333;
        }

        input {
            width: 80%;
            font-size: 24px;
            border-radius: 8px;
            border: 2px solid #080707;
        }

        button {
            font-size: 24px;
            background-color: darkblue;
            color: white;
            border-radius: 5px;
        }

        button:hover {
            background-color: navy;
        }

        h2 {
            color: darkgreen;
            font-size: 24px;
        }
    </style>
</head>
<body>
    <center>
    <h1>Incandescent Bulb Power Calculator</h1>

    <div class="container">
        <form method="POST">
            {% csrf_token %}
            <label>Intensity (I):</label>
            <input type="number" name="intensity" required>

            <label>Resistance (R):</label>
            <input type="number" name="resistance" required>

            <button type="submit">Calculate Power</button>
        </form>

        {% if result %}
            <h2>Power (P) = {{ result }} Watts</h2>
        {% endif %}
    </div>
    </center>
</body>
</html>

views.py

from django.shortcuts import render

def monesh(request):
    result = None
    if request.method == "POST":
        try:
            I = float(request.POST.get("intensity"))
            R = float(request.POST.get("resistance"))
            result = (I ** 2) * R
        except:
            result = "Invalid input"
    return render(request, "calc/mons.html", {"result": result})

urls.py

from django.contrib import admin
from django.urls import path
from calc import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.monesh, name='monesh'),
]
```
# SERVER SIDE PROCESSING:
<img width="1364" height="318" alt="tera" src="https://github.com/user-attachments/assets/21a92e7e-18fe-4d95-a661-bf30731cb62e" />

# HOMEPAGE:
<img width="1919" height="1079" alt="homepage" src="https://github.com/user-attachments/assets/fa288944-0a3c-4d4b-bf38-fe4e7b231b8d" />

# RESULT:
<img width="1919" height="1079" alt="output1" src="https://github.com/user-attachments/assets/0b7267cc-a47b-4912-9e2e-5d5b8a6872f9" />
<img width="1919" height="1079" alt="output2" src="https://github.com/user-attachments/assets/a730779f-084b-46c2-950f-be46a5c593df" />


The program for performing server side processing is completed successfully.
