🛍️ Eira Store – Handmade E‑commerce Platform
A full‑featured online store for handcrafted bags, accessories, candles, keychains, cups and personalised items.
Built with PHP (vanilla), MySQL, HTML/CSS/JS and a touch of Canvas API for product customisation.

https://img.shields.io/badge/PHP-8.0%252B-777BB4?logo=php&logoColor=white
https://img.shields.io/badge/MySQL-8.0-4479A1?logo=mysql&logoColor=white
https://img.shields.io/badge/JavaScript-ES6-F7DF1E?logo=javascript&logoColor=black
https://img.shields.io/badge/Responsive-Yes-2E8B57

✨ Features
👤 Customer side
User accounts – register, login, session management

Product catalogue – filter by category, search by name

Shopping cart – add/update/remove items (database backed)

Favourites (wishlist) – like/unlike products

Order checkout – delivery details, time slot, notes

Order history – view past orders with status

Product reviews – star rating + text, aggregated stats

Contact form – message + optional image upload

Customisation tools – interactive canvas design for tote bags (customizeBag.php) and mugs (customizeCup.php) with colour, image upload, text and position controls. Download final design as PNG.

🔐 Admin panel (/admin)
Dashboard with statistics (orders, revenue, users, products, messages)

Order management – update status (pending → confirmed → shipped → delivered → cancelled)

Product CRUD – add, edit, delete products (name, price, category, images, descriptions, features, badges)

User list – view registered users and their order count

Contact messages – view and delete messages, preview uploaded images

Logout

🛠️ Tech Stack
Layer	Technology
Backend	PHP 8+ (no framework)
Database	MySQL (PDO)
Frontend	HTML5, CSS3, JavaScript (ES6)
Libraries	Font Awesome 6, Google Fonts
Images	Local storage (uploaded & static)
Canvas	Custom mug & bag designer (client‑side PNG export)
📁 Project Structure (simplified)
text
eira-store/
├── index.php               # Homepage
├── products.php            # Product listing with filters
├── product-detail-modal    (dynamic modal)
├── cart.php / favorites.php
├── account.php             # Orders & profile
├── reviews.php             # Customer reviews
├── contact.php             # Contact form with image upload
├── about.php / faq.php
├── customizeBag.php        # Canvas bag designer
├── customizeCup.php        # Canvas mug designer
├── admin/                  # Admin dashboard
│   └── index.php
├── api/                    # All AJAX endpoints
│   ├── cart.php
│   ├── favorites.php
│   ├── order.php
│   ├── products.php
│   ├── reviews.php
│   ├── contact.php
│   ├── admin_*.php
│   └── logout.php
├── includes/
│   ├── db.php              # Database connection
│   ├── auth.php            # Session & login helpers
│   ├── header.php          # Global header + nav
│   └── footer.php          # Footer + order popup
├── uploads/contact/        # Uploaded contact images (auto‑created)
├── image/                  # Product photos, logo, icons
├── style.css               # Global styles
├── script.js               # Shared JS (cart, fav, modal, etc.)
├── database.sql            # Full schema + sample data
└── setpass.php             # (DELETE) one‑time password reset script
🚀 Installation (Local / XAMPP)
1. Clone the repository
bash
git clone https://github.com/your-username/eira-store.git
Place the folder inside your web server root (e.g. htdocs/ for XAMPP).

2. Create the database
Open phpMyAdmin or MySQL CLI.

Execute the provided database.sql file.
This creates the database eira_store, all tables, sample products, a default admin user and a few reviews.

3. Configure database connection
Edit includes/db.php:

php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');        // your MySQL username
define('DB_PASS', '');            // your MySQL password
define('DB_NAME', 'eira_store');
4. Set folder permissions (for image uploads)
Make sure the directory uploads/contact/ exists and is writable by the web server:

bash
mkdir uploads/contact
chmod 755 uploads/contact
5. Access the website
Frontend: http://localhost/eira-store/

Admin panel: http://localhost/eira-store/admin/

Default admin credentials (from database.sql):

Email: admin@eira.store

Password: admin123

⚠️ Security note: After installation, delete setpass.php from the root folder – it’s a one‑time password reset utility.

6. Test user creation
You can register a new customer account or log in with:

Email: any test email, e.g. test@example.com

Password: choose your own (min. 6 characters)

🎨 Customisation Tools
Two standalone canvas‑based design studios are included:

Tool	File	Features
Tote Bag Designer	customizeBag.php	Bag colour picker, upload image, scale/position image, add custom text, move text, change font/size/colour/bold, download PNG
Mug Designer	customizeCup.php	Mug colour, image upload + vertical offset, text with positioning, font size, bold, colour, download design as PNG
Both tools run entirely in the browser – no server storage required.

📦 Available API Endpoints (used by AJAX)
Endpoint	Methods	Description
api/products.php	GET	Fetch all products (JSON)
api/cart.php	GET, POST, PUT, DELETE	Cart management
api/favorites.php	GET, POST	Wishlist toggle & list
api/order.php	POST	Place new order (clears cart if flag)
api/reviews.php	GET, POST	List reviews / submit new review
api/contact.php	POST	Receive contact message with optional image
api/login.php / register.php	POST	Auth endpoints
api/admin_*.php	GET, POST, PUT, DELETE	Admin operations (protected)
All responses are application/json.

🧪 Database Schema Highlights
users – customer accounts

admins – admin accounts (only one seeded)

products – store catalogue, features stored as JSON

cart_items – per‑user cart

favorites – wishlist

orders + order_items – order details and status

reviews – customer feedback

contact_messages – stores name, email, message and optional image_path

⚙️ Configuration & Customisation
Changing site title / logo
Edit logo path: header.php → .logo img

Page titles are set via $pageTitle before including header.

Adding new product categories
Insert a new category into products.category (string).

Add the filter button in products.php inside .filter-tags.

Adjust the front‑end filtering logic accordingly.

Contact form image upload limits
Max size: 5 MB

Allowed types: JPEG, PNG, WebP, GIF

Controlled in api/contact.php.

🔧 Troubleshooting
Issue	Solution
“Database connection failed”	Check includes/db.php credentials and ensure MySQL is running.
404 on AJAX calls	Make sure you’re accessing the site via a web server (not file://).
Admin login doesn’t work	Verify setpass.php was used correctly. Re‑run the script or reset manually using password_hash().
Image upload fails	Ensure uploads/contact/ exists and has write permissions.
Cart / favourites not working	Must be logged in – check console for 401 responses.
📄 License
This project is open‑source and available under the MIT License.
Feel free to use it as a learning resource or base for your own handmade store.

🙏 Acknowledgements
Icons by Font Awesome

Fonts from Google Fonts

Inspired by small creative businesses and their love for handmade goods.

Crafted with 🖤 by the Eira team.
