## Detailed Day 9: Building a Simple Django App

### Overview (5 minutes)
- **Introduction to Today’s Project:**
  - Today, we’ll build a simple Django app to manage your toy collection.
  - We’ll create views to display the toys and add new ones!

### Project Concept: Managing a Toy Collection (5 minutes)
- **What We’ll Build:**
  - A page to list all the toys in the collection.
  - A form to add new toys to the collection.
  
- **Why This is Cool:**
  - You’ll learn how to create dynamic web pages that interact with your database.

### Activity: Create Views to Display and Add Toys (40 minutes)

#### Step 1: Create a View to Display Toys (15 minutes)
- **Step 1.1: Create the View Function**
  - Open the `views.py` file in the `welcome` app and add the following code:
    ```python
    from django.shortcuts import render, redirect
    from .models import Toy
    from .forms import ToyForm

    def toy_list(request):
        toys = Toy.objects.all()  # Retrieve all toys from the database
        return render(request, 'toy_list.html', {'toys': toys})
    ```

- **Step 1.2: Create the Template for Listing Toys**
  - In the `templates` folder, create a new file called `toy_list.html` and add the following content:
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Toy Collection</title>
    </head>
    <body>
        <header>
            <h1>My Toy Collection</h1>
            <nav>
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="/about">About</a></li>
                    <li><a href="/blog">Blog</a></li>
                    <li><a href="/toys">Toys</a></li>
                </ul>
            </nav>
        </header>
        <main>
            <h2>All Toys</h2>
            <ul>
                {% for toy in toys %}
                    <li>{{ toy.name }} ({{ toy.toy_type }})</li>
                {% empty %}
                    <li>No toys in your collection yet!</li>
                {% endfor %}
            </ul>
            <a href="/toys/add">Add a New Toy</a>
        </main>
    </body>
    </html>
    ```

- **Step 1.3: Update the URLs**
  - In `urls.py`, add a new path for the toy list:
    ```python
    from welcome.views import toy_list

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', welcome_view),
        path('toys/', toy_list),  # New path for toy list
    ]
    ```

#### Step 2: Create a View to Add Toys (15 minutes)
- **Step 2.1: Create a Form for Adding Toys**
  - In the `welcome` app, create a new file called `forms.py` and add the following code:
    ```python
    from django import forms
    from .models import Toy

    class ToyForm(forms.ModelForm):
        class Meta:
            model = Toy
            fields = ['name', 'toy_type']
    ```

- **Step 2.2: Create the View Function for Adding Toys**
  - In `views.py`, add the following function:
    ```python
    def add_toy(request):
        if request.method == 'POST':
            form = ToyForm(request.POST)
            if form.is_valid():
                form.save()  # Save the new toy to the database
                return redirect('/toys/')  # Redirect to the toy list page
        else:
            form = ToyForm()
        return render(request, 'add_toy.html', {'form': form})
    ```

- **Step 2.3: Create the Template for Adding Toys**
  - In the `templates` folder, create a new file called `add_toy.html` and add the following content:
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Add a Toy</title>
    </head>
    <body>
        <header>
            <h1>Add a New Toy</h1>
            <nav>
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="/about">About</a></li>
                    <li><a href="/blog">Blog</a></li>
                    <li><a href="/toys">Toys</a></li>
                </ul>
            </nav>
        </header>
        <main>
            <form method="post">
                {% csrf_token %}
                {{ form.as_p }}
                <button type="submit">Add Toy</button>
            </form>
            <a href="/toys/">Back to Toy List</a>
        </main>
    </body>
    </html>
    ```

- **Step 2.4: Update the URLs for Adding Toys**
  - In `urls.py`, add the path for the add toy view:
    ```python
    from welcome.views import add_toy

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', welcome_view),
        path('toys/', toy_list),
        path('toys/add/', add_toy),  # New path for adding a toy
    ]
    ```

### Step 3: Test Your Application (10 minutes)
- **Step 3.1: Run Your Server**
  - Make sure your development server is running:
    ```bash
    python manage.py runserver
    ```

- **Step 3.2: Test the Toy List Page**
  - Visit `http://127.0.0.1:8000/toys/` to see the toy collection.
  - Click the link to add a new toy and fill out the form.

- **Step 3.3: Check the Toy Collection**
  - After adding a toy, return to the toy list to see if it appears there.
  - Celebrate: “You just created a Django app to manage your toy collection! 🎉”

### Wrap-Up and Review (5 minutes)
- **Review Key Concepts:**
  - What are views in Django, and how do they work?
  - How did we create a form to add new toys and display the toy collection?

- **Encourage Questions:**
  - Invite the student to ask any questions they may have about views, forms, or Django in general.

### Next Steps
- Suggest they explore adding more fields to the toy model (like `color` or `age`) and updating the views accordingly.
- Encourage them to style the pages using CSS to make the app look even better!

[Back to Python Shinobi](https://coco2red.github.io/)
---
