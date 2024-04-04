# Ex.05 Design a Website for Server Side Processing

## Date : 04/04/2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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

math.html

```
<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Surface Area of Right Cylinder</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body
{
    background-color: red(159, 223, 255);
}
.edge {
    width: 100%;
    padding-top: 250px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick solid rgb(0, 0, 0);
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: rgb(255, 255, 255);
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: rgb(190, 0, 0);
    padding-top: 20px;
}
</style>
</head>
<body style="background-color:rgba(255, 255, 255, 0.986);">
<div class="edge">
    <div class="box">
        <h1>Right Cylinder's Surface Area</h1>
        <h3>KEERTHIVASAN S (212223220046)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="Radius" value="{{R}}">m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="Height" value="{{H}}">m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
                <br> </div>br>
            </div>
        </form>
    </div>
</div>
</body>
</html>
```

views.py

```
from django.shortcuts import render
def cylarea(request):
    context={}
    context['area'] = "0"
    context['R'] = "0"
    context['H'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        R = request.POST.get('Radius','0')
        H = request.POST.get('Height','0')
        print('request=',request)
        print('Radius=',R)
        print('Height=',H)
        area = 2 * 3.14 * int(R) * int(H) + 2*3.14*int(R)*int(R)
        context['area'] = area
        context['R'] = R
        context['H'] = H
        print('Area=',area)
    return render(request,'mathapp/math.html',context)
```

urls.py

```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.cylarea,name="surfacearea"),
    path('',views.cylarea,name="areaofsurfaceroot")
]
```

## SERVER SIDE PROCESSING:

![terminal](https://github.com/ikeerthivasanswaminathan/MathServer/assets/148937372/129284d0-a715-4992-b596-9915b405f99a)

## HOMEPAGE:

![math server](https://github.com/ikeerthivasanswaminathan/MathServer/assets/148937372/45394e25-bc71-45b9-b40d-baa20ba06d66)

## RESULT:
The program for performing server side processing is completed successfully.
