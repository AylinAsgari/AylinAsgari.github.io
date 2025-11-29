---
layout: posts
title: drawing with code
---

# This is my first Computer Art project

![My painting]("/assets/images/mypainting.jpg")

* اضافه کردن کتابخانه های مورد نیاز و نوشتن تابع بازگشتی برای رسم درخت با زاویه بین شاخه ها به صورت رندوم
* پس از چند مرحله بر اساس شرط قرار داده شده قبل از رسم شاخه های جدید یک برگ به درخت اضافه می شود

``` python 
import turtle as tr
import random as rnd

leaf = []
def tree(len, w, lim):
    if len < lim * 2:
        r = tr.Turtle()
        r.penup()
        r.setpos(tr.xcor(), tr.ycor())
        r.shape("triangle")
        r.shapesize(0.5)
        r.color("green")
        leaf.append(r)
    if len > lim:
        angle = rnd.randint(10, 45)
        tr.pendown()
        tr.pensize(w)
        tr.forward(len)
        tr.right(angle)
        tree(len * 0.8, w * 0.7, lim)
        tr.left(angle * 2)
        tree(len * 0.8, w * 0.7, lim)
        tr.right(angle)
        tr.backward(len)
```
* برای رسم درختان در هر سمت مسیر یک تابع جدا تعریف شده است
* تابع jungle1 برای رسم درختان سمت چپ
* تابع jungle2 برای رسم درختان سمت راست
```python
def jungle1(x, y):
    for i in range(12):
        tr.penup()
        if i % 2 == 0:
            tr.setpos(x + 35, y)
        else:
            tr.setpos(x, y)
        tree(rnd.randint(60, 90), 10, 30)
        x += 15
        y += 45

def jungle2(x, y):
    for i in range(12):
        tr.penup()
        if i % 2 == 0:
            tr.setpos(x + 35, y)
        else:
            tr.setpos(x, y)
        tree(rnd.randint(60, 90), 10, 30)
        x -= 15
        y += 45



tr.pencolor("coral4")

tr.speed(0)
tr.tracer(0)
tr.setheading(90)

tr.bgcolor("burlywood2")
tr.addshape("sky22.gif")

x = -500
for i in range(6):
    s = tr.Turtle()
    s.penup()
    s.shape("sky22.gif")
    s.setpos(x, 250)
    x += 200

x = -280
y = -350
disy = 100
disx = 200
jungle1(x, y)
jungle1(-490, y)
x2 = 280
y2 = -350
jungle2(x2, y2)
jungle2(490, y2)

tr.penup()
tr.setpos(50, 150)
tr.pendown()
tr.pencolor("gray30")
tr.goto(190, -300)

tr.penup()
tr.setpos(-20, 150)
tr.pendown()
tr.pencolor("gray30")
tr.goto(-150, -300)


tr.ht()
tr.update()
tr.mainloop()

```
* هر یک از توابع jungle1 و jungle2 دو بار فراخوانی میشوند
* در انتها برای رسم مسیر باتوجه به موقعیت درختان کار را به اتمام می رسانیم 