# Cake Haven 🍰

Cake Haven is a Flask-powered e-commerce website for browsing cakes and bakery items, creating custom cakes, managing a shopping cart, and placing delivery orders. It also includes separate admin and baker dashboards for managing products and updating order status.

> **Project status:** This is a development project. Before deploying it publicly, review the security notes below and replace the demo authentication and storage implementation.

## Features

### Customer experience

- Browse artisanal cakes, themed cakes, and bakery items
- Search products by name or description
- View product details, images, similar products, and reviews
- Register, log in, and edit a customer profile
- Add products to a session-based shopping cart
- Build a custom cake by selecting:
  - Layers and fillings
  - Frosting, shape, and size
  - Supports, toppers, piping, and embellishments
  - Theme, colors, message, and packaging
- Save and reload custom cake designs
- Add optional cake decorations during checkout
- Select a delivery date, time, payment mode, and delivery details
- Upload an optional reference image with an order
- View order history and order details

### Admin and baker tools

- Admin dashboard with order statistics
- Add, edit, preview, and delete products
- Manage artisanal, themed, and bakery product categories
- Review customer orders
- Baker dashboard for pending and baking orders
- Update order status and add baker notes
- Track status history for orders

## Technology stack

- **Backend:** Python, Flask
- **Frontend:** HTML, Jinja2 templates, CSS, static assets
- **Storage:** JSON files in the `db/` directory
- **Uploads:** Product images in `static/uploads/` and order images in `static/order_uploads/`
- **License:** Apache License 2.0

## Project structure

```text
.
├── app.py                  # Flask application and routes
├── db/                     # JSON data files created and used by the app
├── static/
│   ├── css/                # Stylesheets
│   ├── uploads/            # Uploaded product images
│   └── order_uploads/      # Uploaded order reference images
├── templates/              # Jinja2 HTML templates
├── home.html               # Legacy/home template
├── themed.html             # Themed cake template
├── LICENSE
└── README.md
```

## Requirements

- Python 3.9 or newer
- `pip`

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/CYBERDEMON121/cake-ecommerce-website.git
   cd cake-ecommerce-website
   ```

2. Create and activate a virtual environment:

   **macOS/Linux:**

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   **Windows PowerShell:**

   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

3. Install Flask and the required packages:

   ```bash
   pip install Flask Werkzeug
   ```

## Running the application

Start the development server with:

```bash
python app.py
```

The application runs on port `5500` by default. Open:

```text
http://127.0.0.1:5500
```

On first startup, the application creates the required JSON files in `db/` and upload directories under `static/` if they do not already exist.

## Main routes

| Route | Purpose |
| --- | --- |
| `/` | Store homepage |
| `/shop` | Browse and search products |
| `/themed` | Browse themed cakes |
| `/bakery` | Browse bakery items |
| `/custom_cake` | Build a custom cake |
| `/cart` | View the shopping cart |
| `/checkout` | Place an order |
| `/orders` | View the signed-in customer's orders |
| `/profile` | View the customer profile |
| `/admin/login` | Admin login |
| `/admin` | Admin dashboard |
| `/baker/login` | Baker login |
| `/baker` | Baker dashboard |

## Data storage

The application uses JSON files rather than a database. The following files are managed in `db/`:

- `users.json`
- `products.json`
- `orders.json`
- `order_items.json`
- `reviews.json`
- `custom_cakes.json`
- `saved_designs.json`

Back up the `db/` directory if you need to preserve local users, products, orders, reviews, or saved designs.

## Security notes

This project is currently configured for local development and should not be deployed as-is:

- Replace the hard-coded Flask `secret_key` with an environment variable.
- Move admin and baker credentials out of `app.py` and store passwords securely using password hashing.
- Do not commit real credentials, customer data, or uploaded files to a public repository.
- Add CSRF protection to form submissions.
- Validate and restrict uploaded file names, file sizes, MIME types, and storage locations.
- Use a production database instead of JSON files for concurrent or public use.
- Run behind a production WSGI server and configure secure cookies and HTTPS.

## Development notes

The application currently starts with Flask's built-in development server:

```python
app.run(port=5500)
```

For production, use a WSGI server such as Gunicorn or Waitress and configure the host, port, secret key, and data paths through environment variables.

## Contributing

1. Create a feature branch.
2. Make and test your changes locally.
3. Keep customer data and credentials out of commits.
4. Open a pull request describing the change.

## License

This project is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.
