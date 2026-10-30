# Advanced E-Commerce Website (Java)

A beginner-friendly, full-stack e-commerce demonstration built with **Java 17, Spring Boot, Thymeleaf, Spring Data JPA and H2 Database**. It includes a customer-facing storefront, shopping cart, checkout flow, order confirmation and a simple product/order administration page.

> This is an educational demo. It does not integrate a real payment gateway or include production-grade authentication, authorisation, fraud controls or deployment hardening.

## Features

### Customer storefront
- Responsive product catalogue with product images, categories, descriptions, prices and stock levels.
- Search products by name or description.
- Filter products by category.
- Product detail pages.
- Add items to a session-based shopping cart.
- Update quantities and remove cart items.
- Checkout form with basic server-side validation.
- Order confirmation with order reference and item summary.

### Admin demonstration
- Add products with name, description, category, price, image URL, stock and featured flag.
- View current product inventory and delete products.
- View customer orders and update order status (Processing, Shipped, Delivered or Cancelled).

### Data and implementation
- Spring Boot MVC controllers and Thymeleaf server-rendered pages.
- Spring Data JPA entities and repositories.
- H2 file-based database; sample catalogue is loaded automatically on first run.
- Stock is checked when adding to cart and again when placing an order.
- Shopping cart is stored in the HTTP session.
- Responsive CSS layout for desktop and mobile.

## Technology stack

| Technology | Purpose |
|---|---|
| Java 17 | Application language |
| Spring Boot 3.3.5 | Application framework |
| Spring MVC | Web routes and controllers |
| Thymeleaf | Server-side HTML templates |
| Spring Data JPA | Database access |
| H2 | Local demonstration database |
| Maven | Build and dependency management |
| HTML/CSS | User interface |

## Project folder structure

```text
advanced-ecommerce-java/
├── pom.xml
├── README.md
├── .gitignore
└── src/
    └── main/
        ├── java/com/example/shop/
        │   ├── ShopApplication.java
        │   ├── config/
        │   │   └── DataLoader.java
        │   ├── controller/
        │   │   ├── AdminController.java
        │   │   └── StoreController.java
        │   ├── model/
        │   │   ├── Product.java
        │   │   ├── CustomerOrder.java
        │   │   └── OrderItem.java
        │   ├── repository/
        │   │   ├── ProductRepository.java
        │   │   ├── CustomerOrderRepository.java
        │   │   └── OrderItemRepository.java
        │   └── service/
        │       ├── CartService.java
        │       └── OrderService.java
        └── resources/
            ├── application.properties
            ├── static/css/style.css
            └── templates/
                ├── fragments.html
                ├── index.html
                ├── product.html
                ├── cart.html
                ├── checkout.html
                ├── confirmation.html
                └── admin.html
```

## Requirements

- JDK 17 or later
- Maven 3.6+ (or use an IDE with Maven support)
- Internet connection on first build so Maven can download dependencies

Check your installation:

```bash
java -version
mvn -version
```

## Run locally

1. Download and extract this project.
2. Open the extracted `advanced-ecommerce-java` folder in IntelliJ IDEA, Eclipse or VS Code with Java support.
3. Open a terminal in the project root (the folder containing `pom.xml`).
4. Run:

```bash
mvn spring-boot:run
```

5. Open [http://localhost:8080](http://localhost:8080).

Alternative: build and run the executable JAR:

```bash
mvn clean package
java -jar target/advanced-ecommerce-1.0.0.jar
```

The H2 database is stored in the local `data/` folder and created automatically. The H2 console is available at `http://localhost:8080/h2-console` with JDBC URL `jdbc:h2:file:./data/shopdb`, username `sa`, and an empty password. Use it only for local development.

## Suggested testing walkthrough

1. Browse the home page and search for `headphones`.
2. Filter by a category such as `Electronics`.
3. Open a product detail page and add one item to your cart.
4. Visit **Cart**, change a quantity and update it.
5. Continue to checkout and enter sample customer details.
6. Place the demo order and note the order reference.
7. Open **Admin** from the top navigation.
8. Add a new product, inspect inventory and update the order status.

Prices are sample values displayed without a currency symbol to keep the demonstration neutral. You can change the seeded product prices and content in `DataLoader.java`.

## Screenshots guidance

Run the application and capture the following pages in your browser:

| Filename | Recommended screen |
|---|---|
| `01-homepage.png` | Storefront hero and product catalogue |
| `02-product-detail.png` | Product detail with add-to-cart control |
| `03-shopping-cart.png` | Cart with at least one item |
| `04-checkout.png` | Checkout form (use fictional details) |
| `05-order-confirmation.png` | Successful demo order confirmation |
| `06-admin-dashboard.png` | Product inventory and orders |
| `07-mobile-view.png` | Responsive storefront on a mobile viewport |

### Capture screenshots
- Windows: `Win + Shift + S`
- macOS: `Shift + Command + 4`
- Linux: use your desktop screenshot utility
- Save the images in a `screenshots/` folder in the project root.
- Use fictional customer data only. Do not include real personal information, passwords, or database credentials in screenshots.
- Upload the `screenshots` folder to your GitHub repository after uploading the source.

## Step-by-step GitHub upload

### Method A — GitHub website (recommended for beginners)

1. Sign in at [https://github.com](https://github.com).
2. Click **New repository**.
3. Name it `advanced-ecommerce-java`.
4. Add a short description such as `Java Spring Boot e-commerce website with product catalogue, cart and checkout`.
5. Choose Public or Private.
6. Click **Create repository**.
7. In the repository, click **Add file → Upload files**.
8. Extract the ZIP file on your computer.
9. Drag the project contents (`pom.xml`, `README.md`, `.gitignore` and `src` folder) into the upload area. Upload the contents of the project directory, not an additional enclosing folder.
10. Enter commit message `Initial commit - Advanced E-Commerce Website`.
11. Click **Commit changes**.
12. Upload your screenshots into a `screenshots` folder using **Add file → Upload files**.

### Method B — Git command line

Install Git, open a terminal in the project root and run:

```bash
git init
git add .
git commit -m "Initial commit: advanced Java e-commerce website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/advanced-ecommerce-java.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username. If GitHub requests authentication, complete its browser sign-in flow or use a configured SSH key/personal access token. Never place access tokens in the project source code.

## Deployment notes

This project runs locally with an embedded H2 database. For a public deployment, use a managed relational database (such as PostgreSQL), configure environment-based secrets, add authentication and role-based authorisation, enable HTTPS, and deploy to a Java hosting platform. GitHub Pages cannot host this Spring Boot backend; use GitHub to store the source and deploy the application to a Java-capable host.

## Important security and production limitations

- The `/admin` routes are intentionally open in this learning version. Add Spring Security and administrator authentication before exposing it publicly.
- Checkout records an order but does not charge a payment method.
- Do not collect real card details or store payment credentials.
- H2 is configured for local development; use a production database for real deployments.
- Add CSRF protection, secure session configuration, rate limiting, privacy controls, backups and audit logging before production use.
- External product images and Google Fonts require an internet connection. Replace remote image URLs with locally licensed assets if needed.

## Customisation ideas

- Add login and customer registration with Spring Security.
- Add product edit functionality, stock alerts and pagination.
- Integrate a payment provider in a compliant test environment.
- Add order history, email notifications and downloadable invoices.
- Add automated tests for cart, checkout and inventory rules.

## License

Provided for educational and portfolio use. Review external image licences before redistributing image assets.
