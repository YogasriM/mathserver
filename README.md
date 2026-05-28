# Ex.04 Design a Website for Server Side Processing
## Date: 28/05/2026

## AIM:
To create a web page to calculate total bill amount with GST from price and GST percentage, using server-side scripts.

## FORMULA:
Bill = P + (P * GST / 100)
<br> P --> Price (in Rupees)
<br> GST --> GST (in Percentage)
<br> Bill --> Total Bill Amount (in Rupees)

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

## PROGRAM:
math.html
```
<html>
<head>
    <title>GST Calculator</title>

    <style>
        body{
            background-color:#d779d7;
            font-family:Arial;
        }

        .box{
            width:400px;
            margin:100px auto;
            background:#d7d7e8;
            padding:40px;
            text-align:center;
            border-radius:15px;
            box-shadow:0px 0px 10px gray;
        }

        h1{
            color:purple;
            margin-bottom:30px;
        }

        input{
            width:80%;
            padding:12px;
            margin:10px;
            border-radius:5px;
            border:1px solid gray;
        }

        button{
            background:purple;
            color:white;
            border:none;
            padding:12px 25px;
            border-radius:5px;
            cursor:pointer;
        }

        h2{
            color:purple;
            margin-top:25px;
        }
    </style>
</head>

<body>

<div class="box">

    <h1>GST Bill Calculator</h1>

    <form method="POST">

        {% csrf_token %}

        <input type="number"
               name="price"
               placeholder="Enter Price"
               required>

        <br>

        <input type="number"
               name="gst"
               placeholder="Enter GST %"
               required>

        <br><br>

        <button type="submit">
            Calculate
        </button>

    </form>
    {% if total %}

<h3>Original Price = ₹ {{ price }}</h3>

<h3>GST Percentage = {{ gst }} %</h3>

<h3>GST Amount = ₹ {{ gst_amount }}</h3>

<h2>Total Bill = ₹ {{ total }}</h2>

{% endif %}

</div>

</body>
</html>
```
views.py
```
from django.shortcuts import render
def gst(request):
    context = {}
    if request.method == "POST":
        price = float(request.POST['price'])
        gst = float(request.POST['gst'])
        print("Price Received:", price)
        print("GST Received:", gst,"%")
        gst_amount = (price * gst) / 100
        total = price + gst_amount
        print("Calculated Total:", total)
        context = {
            'total': total
        }
    return render(request, 'mathapp/math.html', context)
```
urls.py
```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('mathapp.urls')),
]
```
## OUTPUT - SERVER SIDE:
<img width="1118" height="273" alt="image" src="https://github.com/user-attachments/assets/3d6e654f-bddc-4058-80dc-39e16687c728" />


## OUTPUT - WEBPAGE:
<img width="1495" height="673" alt="image" src="https://github.com/user-attachments/assets/e8ee7076-446d-48fc-a79e-c2a6beae0af6" />

<img width="1481" height="664" alt="image" src="https://github.com/user-attachments/assets/168b1fb4-b118-4854-97c8-fec907722c61" />

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
