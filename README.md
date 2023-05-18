# flask-webapp-vscode

<!DOCTYPE html>
<html lang='en'>
<head>
    
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE-edge">
    <meta name="viewport" content"width=device-width, initial-scale=1.0">
    <title>The Sk8 Shack</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='css/index.css') }}">
</head>
<body>
    {% extends 'base.html' %}

    {% block content %}
    <h1>Hello Welcome To The Sk8 Shack Home Page</h1>
    <img src ="static/built in/Images for my online Flask shop/NewBanner.jpeg" width = "700" height = "300">
    <h2>About Our Store</h2>
    <p>Here at The sk8 Shack we provide the latest cutting edge skate equipment at the lowest costs on the market.
        We strive in being as environmentaly friendly as possible, even if it means making things slightly more
        challenging for us. The world came before us so we should put its needs first! Many of our products come 
        from recycled materials, and many of our products are manufactured using machines supplied by renewable energy.
    </p>
    <h2>Availabe Items</h2>
    
    <form method="GET">
        <label for="sort-by">Sort by:</label>
        <select name="sort-by" id="sort-by">
            <option value="name">Name</option>
            <option value="price">Price</option>
        </select>
        <button type="submit">Sort</button>
    </form>
    
    
    
    <ul>
        {% for row in data %}
        <li>
            <h3>{{ row[1] }}</h3> 
            <p>{{ row[2] }}</p> 
            <div class="product-container">
                <img src="{{ row[3] }}"" alt="Product Image" style="width: 200px; height: 200px;">
                <div class="product-description">
                    <p>{{ row[4] }}</p>
                </div>
            </div>
            <form id="add-to-cart-form" action="/add_to_cart" method="POST">
                <input type="hidden" name="product_id" value="{{ row[0] }}">
                <button type="submit">Add to Cart</button>
            </form>
         </li>
        {% endfor %}
    </ul>
    <script>
        function showMessage(event, message) {
            alert(message);
            event.preventDefault(); 
        }
    </script>
    
    {% endblock %}
    
</body>
</html>
