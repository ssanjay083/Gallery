# Ex.08 Design of Interactive Image Gallery
# Date:16.11.2024
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
views.py
```
from django.shortcuts import render
def gal(request):
    return render(request,"ig.html")
```
urls.py
```
from django.contrib import admin
from django.urls import path,include
from app import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('',include('app.urls')),
    path('gal/',views.gal)
]
```
ig.html
```
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Image Gallery with Modal</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      background-color: #f4f4f4;
    }

    h1 {
      margin-top: 70px;
      font-size: 2rem;
      color: #1e9ffb;
    }

    .gallery {
      display: grid;
      grid-template-columns: repeat(4, 1fr); /* Set exactly 4 images per row */
      gap: 16px;
      padding: 20px;
      max-width: 90%;
    }

    .gallery img {
      width: 100%;
      height: auto;
      object-fit: cover;
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
    }

    .gallery img:hover {
      transform: scale(1.1) rotateX(10deg);
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    }

   
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.8);
      justify-content: center;
      align-items: center;
    }

    .modal img {
      max-width: 50%;
      max-height: 50%;
      border-radius: 8px;
      box-shadow: 0 8px 16px rgba(255, 255, 255, 0.3);
    }

    .modal:active {
      display: none;
    }

    .modal-close {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 24px;
      color: white;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Image Gallery</h1> 

  <div class="gallery" id="gallery"></div>

  
  <div class="modal" id="modal">
    <span class="modal-close" id="closeModal">&times;</span>
    <img id="modalImg" src="" alt="Expanded view">
  </div>

  <script>
    
    const images = [
      { src: "{% static 'images/image1.png' %}", alt: "Dhoni" },
      { src: "{% static 'images/image2.png' %}", alt: "Tendulkar" },
      { src: "{% static 'images/image3.png' %}", alt: "Dilshan" },
      { src: "{% static 'images/image4.png' %}", alt: "McCullum" },
      { src: "{% static 'images/image5.png' %}", alt: "De Villiers" },
      { src: "{% static 'images/image6.png' %}", alt: "Andy Flower" },
      { src: "{% static 'images/image7.png' %}", alt: "Vaughan" },
      { src: "{% static 'images/image8.png' %}", alt: "Pietersen" }
    ];

    const gallery = document.getElementById("gallery");
    const modal = document.getElementById("modal");
    const modalImg = document.getElementById("modalImg");
    const closeModal = document.getElementById("closeModal");

    
    images.forEach(image => {
      const img = document.createElement("img");
      img.src = image.src;
      img.alt = image.alt;
      img.addEventListener("click", () => {
        modal.style.display = "flex"; 
        modalImg.src = image.src; 
        modalImg.alt = image.alt;
      });
      gallery.appendChild(img);
    });

    closeModal.addEventListener("click", () => {
      modal.style.display = "none";
    });

    
    modal.addEventListener("click", (e) => {
      if (e.target === modal) {
        modal.style.display = "none";
      }
    });
  </script>
</body>
</html>
```
# OUTPUT:
![Screenshot 2024-12-13 223939](https://github.com/user-attachments/assets/a0b90325-0011-4594-afe3-f42bec6bd407)
![Screenshot 2024-12-13 224028](https://github.com/user-attachments/assets/c53736b9-2dc0-4028-addc-f8db92d4f408)
![Screenshot 2024-12-13 224551](https://github.com/user-attachments/assets/61b0d6cf-2847-4497-8e66-7fe00ced6f1d)
![Screenshot 2024-12-13 223330](https://github.com/user-attachments/assets/f6427b46-7fbd-4823-90b4-89042d610e69)









# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
