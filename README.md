# Ex.07 Restaurant Website
## Date: 05/10/2025

## AIM:
To develop a static Restaurant website to display the food items and services provided by them.

## DESIGN STEPS:

### Step 1:
Requirement collection.

### Step 2:
Creating the layout using HTML and CSS.

### Step 3:
Updating the sample content.

### Step 4:
Choose the appropriate style and color scheme.

### Step 5:
Validate the layout in various browsers.

### Step 6:
Validate the HTML code.

### Step 7:
Published the website in the given URL.  https://acrologic-deedee-inerrably.ngrok-free.dev 

## PROGRAM:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>{% block title %}Resto{% endblock %}</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  {% load static %}
  <link href="{% static 'css/styles.css' %}" rel="stylesheet">
</head>
<body class="{% block body_class %}{% endblock %}">
  <header class="site-header">
    <div class="container">
      <h1 class="brand"><a href="/">Resto</a></h1>
      <nav class="nav">
        <a href="/">Home</a>
        <a href="/menu/">Menu</a>
        <a href="/reservations/">Reservations</a>
        <a href="/contact/">Contact</a>
      </nav>
    </div>
  </header>

  <!-- Global flash messages -->
  <div class="container">
    {% if messages %}
      {% for message in messages %}
        <div class="alert alert-{{ message.tags }}" 
             style="background:#e8ffe8;border:1px solid #b7f5b7;padding:10px;border-radius:6px;margin-top:12px;">
          {{ message }}
        </div>
      {% endfor %}
    {% endif %}
  </div>

  <main class="container">
    {% block content %}{% endblock %}
  </main>

  <footer class="site-footer">
    <div class="container">
      <small>&copy; {% now "Y" %} Resto — built in Django.</small>
    </div>
  </footer>

  <!-- advanced fade-in/fade-out transition -->
  <script>
    document.addEventListener("DOMContentLoaded", () => {
      document.body.classList.add("loaded");

      document.querySelectorAll("a").forEach(link => {
        link.addEventListener("click", function(e) {
          if (this.hostname === window.location.hostname && this.pathname !== window.location.pathname) {
            e.preventDefault();
            document.body.classList.remove("loaded"); // fade out
            setTimeout(() => {
              window.location.href = this.href;
            }, 500);
          }
        });
      });
    });
  </script>
</body>
</html>


{% extends "base.html" %}
{% block body_class %}contact-bg{% endblock %}
{% block title %}Contact · Resto{% endblock %}
{% block content %}
<h2>Contact</h2>
<p><strong>Contact Person:</strong> Udhaya</p>
<p><strong>Email:</strong> <a href="mailto:udhaya123@gmail.com">udhaya123@gmail.com</a></p>
<p><strong>Phone:</strong> <a href="tel:+919597511201">+91 95975 11201</a></p>
<p><strong>Address:</strong> 123 Main Street, Your City</p>
<p><strong>Hours:</strong> Mon–Sun 11:00–22:00</p>
{% endblock %}


{% extends "base.html" %}
{% block body_class %}home-bg{% endblock %}
{% block title %}Home · Resto{% endblock %}
{% block content %}
<section class="hero">
  <h2>Welcome to Resto</h2>
  <p>Fresh ingredients, honest cooking, and a cozy setting. Book a table today.</p>
  <p><a class="btn" href="/reservations/">Reserve a table</a></p>
</section>
{% endblock %}


{% extends "base.html" %}
{% load static %}
{% block body_class %}menu-bg{% endblock %}
{% block title %}Menu · Resto{% endblock %}
{% block content %}
<h2>Our Menu</h2>
<div class="gallery">
  {% for item in items %}
    <div class="gallery-item">
      {% if item.image %}
        <!-- Use explicit image if defined -->
        <img src="{% static 'images/dishes/' %}{{ item.image }}" alt="{{ item.name }}">
      {% else %}
        <!-- Fallback: generate from slugified name -->
        <img src="{% static 'images/dishes/' %}{{ item.name|slugify }}.jpeg" alt="{{ item.name }}">
      {% endif %}
      <h3>{{ item.name }}</h3>
      <p>{{ item.desc }}</p>
      <span class="price">₹{{ item.price }}</span>
    </div>
  {% endfor %}
</div>
{% endblock %}


{% extends "base.html" %}
{% block body_class %}reservations-bg{% endblock %}
{% block title %}Thanks · Resto{% endblock %}
{% block content %}
<h2>Thank you</h2>
<p>Your reservation request was received. We’ll email you a confirmation shortly.</p>
<p><a class="btn" href="/menu/">Explore our menu</a></p>
{% endblock %}


{% extends "base.html" %}
{% block body_class %}reservations-bg{% endblock %}
{% block title %}Reservations · Resto{% endblock %}
{% block content %}
<h2>Reservations</h2>
<form method="post" class="form">
  {% csrf_token %}
  <div class="grid">
    <label>Full name {{ form.name }}</label>
    <label>Email {{ form.email }}</label>
    <label>Phone {{ form.phone }}</label>
    <label>Date {{ form.date }}</label>
    <label>Time {{ form.time }}</label>
    <label>Guests {{ form.guests }}</label>
    <label class="full">Message {{ form.message }}</label>
  </div>
  <button class="btn" type="submit">Book now</button>
</form>
{% endblock %}

```

## OUTPUT:

<img width="1458" height="764" alt="Screenshot 2025-10-05 at 9 26 48 PM" src="https://github.com/user-attachments/assets/928b2c2b-1475-4ec0-aad5-28179c0af29b" />

<img width="1444" height="763" alt="Screenshot 2025-10-05 at 9 27 07 PM" src="https://github.com/user-attachments/assets/545e12cf-94a3-480c-850b-08734c9cf6ec" />

<img width="1452" height="766" alt="Screenshot 2025-10-05 at 9 27 27 PM" src="https://github.com/user-attachments/assets/01491f8f-bdbf-4864-904c-05cc10f37773" />

<img width="1454" height="763" alt="Screenshot 2025-10-05 at 9 27 41 PM" src="https://github.com/user-attachments/assets/3d3a42f1-efac-4545-b69f-957c09a76e1a" />

<img width="1465" height="742" alt="Screenshot 2025-10-05 at 10 22 36 PM" src="https://github.com/user-attachments/assets/af09119e-5fae-4ca6-bc69-38c41ba40409" />

<img width="1451" height="758" alt="Screenshot 2025-10-05 at 9 27 59 PM" src="https://github.com/user-attachments/assets/78239c75-5411-4c66-98ad-9de82af2ea13" />

<img width="615" height="525" alt="Screenshot 2025-10-05 at 9 28 42 PM" src="https://github.com/user-attachments/assets/bbb8d51b-c363-44fc-bb36-9b3de9511603" />

## RESULT:
The program for designing software company website using HTML and CSS is completed successfully.

