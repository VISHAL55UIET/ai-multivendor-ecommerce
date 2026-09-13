# 🛒 Zosh Bazaar — AI-Powered Multi-Vendor E-Commerce Platform

> A full-stack, AI-powered multi-vendor e-commerce platform built with React, TypeScript, Spring Boot, Java, MySQL, Spring Security, JWT, Stripe, Razorpay, and Spring AI.

Zosh Bazaar is a full-stack multi-vendor e-commerce platform designed around real-world marketplace workflows where Customers, Sellers, and Administrators interact through dedicated application experiences.

The platform covers the complete e-commerce lifecycle — from authentication and product discovery to cart management, checkout, payments, order processing, seller product management, revenue tracking, reviews, and AI-powered functionality.

The project uses a separated **React + TypeScript frontend** and **Spring Boot REST API backend**, with a modular architecture for authentication, business logic, database persistence, payments, email, and AI integration.

---

# ✨ Key Features

## 👤 Customer

- User registration and login
- JWT-based authentication
- Protected customer routes
- Product browsing
- Product categories
- Product details
- Shopping cart
- Add/remove cart items
- Update product quantities
- Wishlist
- Checkout
- Stripe and Razorpay payment integration
- Order placement
- Order history
- Reviews and ratings
- Coupons and deals
- Profile management

## 🏪 Seller

- Seller registration
- Seller verification
- Seller authentication
- Seller dashboard
- Seller profile
- Product creation
- Product updating
- Product management
- Inventory management
- Seller order management
- Revenue tracking
- Revenue charts
- Seller reports
- Transactions and payout-related functionality

## 🛡️ Admin

- Admin authentication
- Protected admin routes
- Role-based authorization
- Admin dashboard
- Platform management
- Customer management
- Seller management
- Product management
- Order management
- Revenue-related functionality

## 🤖 AI

The backend contains a dedicated Spring AI module:

```text
com.zosh
└── ai
    ├── controllers
    └── services
```

The project also contains a dedicated `Prompt` request model.

The AI layer is separated from the core e-commerce modules so AI-powered functionality can be developed and extended independently.

The architecture can be extended for:

- AI-powered shopping assistance
- Conversational commerce
- Product recommendations
- Personalized shopping experiences
- Intelligent product search
- Seller insights

---

# 🏗️ Full-Stack Architecture

```text
                         ZOSH BAZAAR
                              │
             ┌────────────────┼────────────────┐
             │                │                │
             ▼                ▼                ▼
         CUSTOMER          SELLER            ADMIN
             │                │                │
             └────────────────┼────────────────┘
                              │
                              ▼
                   React + TypeScript
                              │
                       Redux Toolkit
                              │
                           Axios
                              │
                         REST APIs
                              │
                              ▼
                     Spring Boot API
                              │
                ┌─────────────┼─────────────┐
                │             │             │
                ▼             ▼             ▼
          Spring Security   Services     Spring AI
                │             │             │
                │             ▼             │
                │        Repositories        │
                │             │             │
                └─────────────┼─────────────┘
                              │
                              ▼
                            MySQL
                              │
                 ┌────────────┼────────────┐
                 │            │            │
                 ▼            ▼            ▼
              Stripe       Razorpay      Email
```

---

# 🔐 Authentication & Authorization

The backend uses **Spring Security + JWT** for authentication and authorization.

Security-related configuration includes:

```text
config/
├── AppConfig
├── JwtConstant
├── JwtProvider
└── JwtTokenValidator
```

### Authentication Flow

```text
Login
  │
  ▼
Credential Validation
  │
  ▼
JWT Token
  │
  ▼
Frontend Authentication
  │
  ▼
Authenticated API Request
  │
  ▼
Spring Security
  │
  ▼
JWT Validation
  │
  ▼
Role Validation
  │
  ▼
Authorized API
```

### Roles

```text
ROLE_CUSTOMER
      │
      └── Customer Application

ROLE_SELLER
      │
      └── Seller Dashboard

ROLE_ADMIN
      │
      └── Admin Dashboard
```

---

# 🛍️ Customer Shopping Flow

```text
Visit Website
      │
      ▼
Browse Products
      │
      ▼
Product Details
      │
      ▼
Add To Cart
      │
      ▼
Shopping Cart
      │
      ├── Update Quantity
      ├── Remove Item
      └── Continue Shopping
      │
      ▼
Checkout
      │
      ▼
Payment
      │
      ▼
Order Confirmation
      │
      ▼
Order History
```

---

# 🏪 Seller Flow

```text
Seller Registration
        │
        ▼
Seller Verification
        │
        ▼
Seller Login
        │
        ▼
Seller Dashboard
        │
        ├──────────────┐
        │              │
        ▼              ▼
     Products        Orders
        │
        ├── Add Product
        ├── Update Product
        ├── Manage Product
        └── Manage Inventory
        │
        ▼
Revenue & Reports
        │
        ▼
Transactions / Payouts
```

---

# 🛡️ Admin Flow

```text
Admin Login
     │
     ▼
Authentication
     │
     ▼
Role Validation
     │
     ▼
Admin Dashboard
     │
     ├── Customers
     ├── Sellers
     ├── Products
     ├── Orders
     └── Platform Management
```

---

# 💳 Payment Architecture

The backend integrates:

- Stripe
- Razorpay

### Payment Flow

```text
Customer
   │
   ▼
Shopping Cart
   │
   ▼
Checkout
   │
   ▼
Create Order
   │
   ▼
Payment Processing
   │
   ├───────────────┐
   ▼               ▼
Stripe          Razorpay
   │               │
   └───────┬───────┘
           ▼
      Payment Status
           │
           ▼
       Transaction
           │
           ▼
       Order Status
```

The backend contains dedicated payment-related models and services for payment workflows.

---

# 📦 Order Management

The application supports order workflows for customers and sellers.

### Customer

- Place orders
- View orders
- View order history
- View order details
- Access purchased products

### Seller

- View seller orders
- Manage seller-side order operations

Relevant backend components include:

```text
OrderController
OrderService
OrderRepository

OrderItemService
OrderItemRepository

SellerOrderController
```

---

# 🛒 Shopping Cart

The cart system supports:

- Add product
- Remove product
- Update quantity
- View cart
- Multiple cart items
- Cart total calculation
- Checkout

Backend components:

```text
CartController
CartItemController

CartService
CartItemService

CartRepository
CartItemRepository
```

---

# ❤️ Wishlist

Customers can save products for future purchases.

### Wishlist Operations

- Add product
- Remove product
- View wishlist
- Manage saved products

Backend components:

```text
WishlistController
WishlistService
WishlistRepository
```

---

# ⭐ Reviews & Ratings

Customers can interact with product reviews and ratings.

Features include:

- Create reviews
- Submit ratings
- View reviews
- Product feedback

Backend components:

```text
ReviewController
ReviewService
ReviewRepository

CreateReviewRequest
ReviewRequest
RatingRequest
```

---

# 🎟️ Coupons & Deals

The application supports promotional functionality.

### Coupons

```text
CouponController
CouponService
CouponRepository
CouponNotValidException
```

### Deals

```text
DealController
DealService
DealRepository
```

---

# 📊 Revenue & Reporting

The backend contains dedicated revenue and seller reporting functionality.

```text
RevenueController
RevenueService
RevenueChart

SellerReportController
SellerReportService
SellerReportRepository
```

These modules provide the foundation for seller revenue and reporting workflows.

---

# 💰 Transactions & Payouts

Financial functionality is separated into dedicated modules.

```text
Transaction
Payouts
PaymentOrder
PaymentDetails
PaymentInformation
```

These modules support payment transactions, seller revenue, payment orders, and payout-related workflows.

---

# 📧 Email & Verification

The backend includes dedicated email and verification services.

```text
EmailService
VerificationService
VerificationCodeRepository
PasswordResetTokenRepository
```

These support workflows such as:

- Email verification
- Verification codes
- Password reset
- Account verification

---

# 🎨 Frontend Architecture

The frontend is built using **React + TypeScript** with a component-based structure.

```text
frontend/
└── src/
    ├── admin/
    │   ├── pages/
    │   │   ├── Auth/
    │   │   └── Dashboard/
    │   └── components/
    │
    ├── customer/
    │   ├── components/
    │   │   ├── Navbar/
    │   │   └── Footer/
    │   └── pages/
    │       ├── Home/
    │       ├── Products/
    │       └── BecomeSeller/
    │
    ├── seller/
    │   ├── pages/
    │   │   ├── SellerDashboard/
    │   │   ├── SellerAccountVerification/
    │   │   └── SellerAccountVerified/
    │   └── components/
    │
    ├── Redux Toolkit/
    │   ├── Customer/
    │   ├── Seller/
    │   └── Store/
    │
    ├── routes/
    │   └── CustomerRoutes/
    │
    ├── Config/
    │   └── Api.ts
    │
    ├── Theme/
    │   └── customeTheme/
    │
    ├── data/
    ├── App.tsx
    └── App.css
```

---

# 🔄 Redux Toolkit

Redux Toolkit is used for centralized frontend state management.

The frontend separates state according to application domains.

```text
Redux Toolkit
│
├── Customer
│   ├── User
│   └── Customer Data
│
├── Seller
│   └── Seller Profile
│
├── Authentication
│
└── Application Data
```

Asynchronous API operations are handled through Redux-based async actions.

---

# 🌐 API Communication

The frontend communicates with the Spring Boot backend using REST APIs.

A centralized Axios configuration is used for API communication.

```text
React Component
       │
       ▼
Redux / Async Action
       │
       ▼
Axios API Client
       │
       ▼
Spring Boot REST API
       │
       ▼
Service Layer
       │
       ▼
Repository Layer
       │
       ▼
MySQL
```

---

# 📱 Responsive UI

The frontend is designed for different screen sizes:

- Desktop
- Laptop
- Tablet
- Mobile

Responsive layouts are used across:

- Navigation
- Product grids
- Product cards
- Shopping cart
- Checkout
- Dashboards
- Forms

---

# ⚡ Backend Cold-Start Handling

The backend is deployed on Render.

When the backend has been inactive, the first request may take additional time while the service starts.

The frontend provides a dedicated loading experience:

```text
User Opens Website
        │
        ▼
Frontend Loads
        │
        ▼
Backend Wake-Up Request
        │
        ▼
┌──────────────────────────────┐
│  Waking up Zosh Bazaar...    │
│                              │
│  This may take a few seconds │
│  on the first visit.         │
└──────────────────────────────┘
        │
        ▼
Backend Responds
        │
        ▼
Application Available
```

This improves the experience during backend cold starts.

---

# ⚙️ Backend Architecture

The backend follows a layered architecture:

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
MySQL
```

Supporting packages include:

```text
ai
config
controller
domain
dto
exception
mapper
model
repository
request
response
service
utils
```

---

# 🎯 Controller Layer

The backend contains controllers for major business modules:

```text
AdminController
AdminCouponController
AuthController
CartController
CartItemController
CustomerController
DealController
HomeController
OrderController
PaymentController
ProductController
RevenueController
ReviewController
SellerController
SellerOrderController
SellerProductController
TransactionController
UserController
WishlistController
```

---

# ⚙️ Service Layer

Business logic is separated from REST controllers using service interfaces and implementations.

```text
service/
├── impl/
│
├── AuthService
├── CartItemService
├── CartService
├── CouponService
├── DealService
├── EmailService
├── HomeCategoryService
├── HomeService
├── OrderItemService
├── OrderService
├── PaymentService
├── ProductService
├── RevenueService
├── ReviewService
├── SellerReportService
├── SellerService
├── TransactionService
├── UserService
├── VerificationService
└── WishlistService
```

---

# 🗄️ Repository Layer

Spring Data JPA repositories are used for database access.

```text
AddressRepository
CartItemRepository
CartRepository
CategoryRepository
CouponRepository
DealRepository
HomeCategoryRepository
NotificationRepository
OrderItemRepository
OrderRepository
PasswordResetTokenRepository
PaymentOrderRepository
PayoutsRepository
ProductRepository
ReviewRepository
SellerReportRepository
SellerRepository
TransactionRepository
UserRepository
VerificationCodeRepository
WishlistRepository
```

---

# 📦 DTO Layer

DTOs are used for structured data transfer.

```text
OrderDto
OrderHistory
OrderItemDto
ProductDto
RevenueChart
UserDto
```

DTOs help keep API contracts separate from persistence entities.

---

# 📥 Request Layer

Dedicated request objects are used for incoming API data.

```text
AddItemRequest
CreateCategoryRequest
CreateHomeCategories
CreateProductRequest
CreateReviewRequest
DeleteProductRequest
LoginRequest
Prompt
RatingRequest
ResetPasswordRequest
ReviewRequest
SignupRequest
```

---

# 📤 Response Layer

Dedicated response classes are used for API responses.

```text
ApiResponse
AuthResponse
FunctionResponse
PaymentLinkResponse
```

---

# ⚠️ Exception Handling

The backend contains domain-specific exceptions for handling business errors.

```text
CartItemException
CategoryNotFoundException
CouponNotValidException
OrderException
ProductException
ReviewNotFoundException
SellerException
ShopNotFoundException
UserException
WishlistNotFoundException
```

---

# 🗃️ Database Models

The backend contains domain models for major marketplace entities:

```text
User
Seller
Product
Category
Cart
CartItem
Order
OrderItem
PaymentOrder
PaymentDetails
PaymentInformation
Transaction
Payouts
Review
Wishlist
Coupon
Deal
Address
BankDetails
BusinessDetails
Notification
VerificationCode
PasswordResetToken
SellerReport
Home
HomeCategory
```

---

# 📁 Full Repository Structure

```text
Zosh-Bazaar/
│
├── frontend/
│   │
│   ├── src/
│   │   ├── admin/
│   │   ├── customer/
│   │   ├── seller/
│   │   ├── Redux Toolkit/
│   │   ├── routes/
│   │   ├── Config/
│   │   ├── Theme/
│   │   ├── data/
│   │   ├── App.tsx
│   │   └── App.css
│   │
│   ├── public/
│   ├── package.json
│   └── ...
│
├── backend/
│   │
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/zosh/
│   │   │   │       ├── ai/
│   │   │   │       │   ├── controllers/
│   │   │   │       │   └── services/
│   │   │   │       ├── config/
│   │   │   │       ├── controller/
│   │   │   │       ├── domain/
│   │   │   │       ├── dto/
│   │   │   │       ├── exception/
│   │   │   │       ├── mapper/
│   │   │   │       ├── model/
│   │   │   │       ├── repository/
│   │   │   │       ├── request/
│   │   │   │       ├── response/
│   │   │   │       ├── service/
│   │   │   │       │   └── impl/
│   │   │   │       └── utils/
│   │   │   │
│   │   │   └── resources/
│   │   │       ├── static/
│   │   │       ├── templates/
│   │   │       ├── application.properties
│   │   │       └── application-example.properties
│   │   │
│   │   └── test/
│   │
│   ├── Dockerfile
│   ├── pom.xml
│   ├── mvnw
│   └── mvnw.cmd
│
├── .gitignore
└── README.md
```

---

# 🧩 Technology Stack

## Frontend

| Technology | Purpose |
|---|---|
| React.js | User interface |
| TypeScript | Type-safe frontend development |
| React Router | Client-side routing |
| Redux Toolkit | Global state management |
| Material UI | UI components |
| Emotion | Styling and theming |
| Axios | REST API communication |
| Vercel | Frontend deployment |

## Backend

| Technology | Purpose |
|---|---|
| Java 17 | Backend development |
| Spring Boot 3.3.2 | Backend framework |
| Spring Web | REST API development |
| Spring Security | Authentication and authorization |
| JWT | Token-based authentication |
| Spring Data JPA | Database persistence |
| Hibernate | ORM |
| MySQL | Relational database |
| Spring AI | AI integration |
| Stripe | Payment processing |
| Razorpay | Payment processing |
| Spring Mail | Email functionality |
| Jakarta Validation | Request validation |
| Maven | Dependency management |
| Lombok | Boilerplate reduction |
| Docker | Containerization |
| Render | Backend deployment |

---

# 📡 API Modules

| Module | Responsibility |
|---|---|
| Authentication | Signup, login, verification, password reset |
| Users | User and profile management |
| Customers | Customer-specific operations |
| Sellers | Seller and shop management |
| Products | Product management |
| Categories | Product categorization |
| Cart | Shopping cart operations |
| Wishlist | Saved products |
| Orders | Customer order lifecycle |
| Seller Orders | Seller-side order management |
| Payments | Payment processing |
| Transactions | Financial transactions |
| Payouts | Seller payout workflows |
| Reviews | Product reviews and ratings |
| Coupons | Promotional discounts |
| Deals | Product deals |
| Revenue | Revenue analytics |
| Notifications | Application notifications |
| AI | AI-powered functionality |

---

# 🏃 Local Development Setup

## Prerequisites

Install:

- Java 17+
- Node.js
- npm
- Maven
- MySQL
- Git
- Docker (optional)

---

## 1. Clone Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>

cd Zosh-Bazaar
```

---

## 2. Configure MySQL

Create the database:

```sql
CREATE DATABASE zosh_bazaar;
```

Configure the backend database connection in:

```text
backend/src/main/resources/application.properties
```

Example:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/zosh_bazaar
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}
```

---

## 3. Configure Backend

Open a terminal:

```bash
cd backend
```

### Windows

```bash
mvnw.cmd spring-boot:run
```

### Linux / macOS

```bash
./mvnw spring-boot:run
```

Backend:

```text
http://localhost:8080
```

---

## 4. Configure Frontend

Open another terminal:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start development server:

```bash
npm start
```

Frontend:

```text
http://localhost:3000
```

---

# 🔑 Environment Variables

Do not commit production secrets to GitHub.

Typical configuration areas include:

```text
DB_USERNAME
DB_PASSWORD
JWT_SECRET
STRIPE_SECRET_KEY
RAZORPAY_KEY_ID
RAZORPAY_KEY_SECRET
MAIL_USERNAME
MAIL_PASSWORD
AI_API_KEY
FRONTEND_URL
```

The backend includes:

```text
application-example.properties
```

which can be used as a reference for local configuration.

---

# 🐳 Docker

The backend includes a `Dockerfile`.

Build the backend image:

```bash
docker build -t zosh-bazaar-backend .
```

Run:

```bash
docker run -p 8080:8080 zosh-bazaar-backend
```

Sensitive configuration should be supplied through environment variables.

---

# 🧪 Testing

The backend includes Spring Boot and Spring Security testing dependencies.

Run tests on Windows:

```bash
mvnw.cmd test
```

Linux/macOS:

```bash
./mvnw test
```

---

# 📸 Screenshots

Add application screenshots here to showcase the major workflows.

Recommended screenshots:

- Customer Homepage
- Product Listing
- Product Details
- Shopping Cart
- Checkout
- Seller Dashboard
- Seller Product Management
- Admin Dashboard
- AI Feature

Example:

```markdown
![Customer Homepage](screenshots/home.png)

![Product Details](screenshots/product-details.png)

![Shopping Cart](screenshots/cart.png)

![Seller Dashboard](screenshots/seller-dashboard.png)

![Admin Dashboard](screenshots/admin-dashboard.png)

![AI Feature](screenshots/ai-feature.png)
```

---

# 🔒 Production Security

For production deployment:

- Store secrets using environment variables or a secret manager.
- Never commit database passwords.
- Never commit JWT secrets.
- Never expose payment credentials.
- Never commit AI API keys.
- Use HTTPS in production.
- Restrict database access.
- Configure CORS correctly.
- Validate incoming API requests.
- Apply authorization at the backend.
- Keep dependencies updated.
- Use separate development and production configurations.

---

# 📈 Scalability

The layered architecture provides a foundation for future scalability improvements.

Potential improvements include:

- Redis caching
- Database indexing
- API pagination
- Query optimization
- Connection pooling
- CDN-based image delivery
- Lazy loading
- Advanced product search
- Background processing
- Rate limiting
- Distributed caching
- Structured logging
- Monitoring and observability

---

# 🔮 Future Improvements

## 🤖 AI

- AI-powered shopping assistant
- Personalized product recommendations
- Conversational commerce
- Semantic product search
- AI-based product categorization
- Intelligent seller analytics

## 👤 Customer

- Advanced product search
- Advanced filtering
- Product sorting
- Personalized recommendations
- Advanced order tracking
- Enhanced notifications

## 🏪 Seller

- Advanced inventory management
- Sales analytics
- Advanced revenue dashboard
- Seller notifications
- Bulk product upload
- Seller performance analytics

## 🛡️ Admin

- Advanced platform analytics
- Seller approval management
- Customer management
- Product moderation
- Advanced order management
- Platform-wide reporting

## ☁️ Infrastructure

- CI/CD pipelines
- Redis
- Elasticsearch/OpenSearch
- Automated integration testing
- API documentation
- Centralized logging
- Monitoring and observability
- Cloud storage/CDN
- Kubernetes-based deployment

---

# 🧠 Engineering Concepts Demonstrated

### Frontend

- React
- TypeScript
- Redux Toolkit
- React Router
- Component-based architecture
- Responsive UI
- Axios
- Global state management
- Protected routes

### Backend

- Java 17
- Spring Boot
- REST APIs
- Spring Security
- JWT
- JPA/Hibernate
- MySQL
- Role-based authorization
- Service-layer architecture
- Repository pattern
- DTO architecture
- Request validation
- Exception handling

### AI

- Spring AI
- AI controller/service separation
- Prompt-based AI interaction
- Modular AI architecture

### Payments

- Stripe
- Razorpay
- Payment orders
- Payment status
- Transactions
- Seller payouts

### Deployment

- GitHub
- Vercel
- Render
- Docker
- Environment-based configuration
- Production deployment
- Backend cold-start handling

---

# 📌 Engineering Highlights

## Multi-Role Architecture

The application separates responsibilities between:

```text
Customer
Seller
Admin
```

Each role has dedicated workflows and authorization rules.

## Layered Backend

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
MySQL
```

This keeps API handling, business logic, and persistence concerns separated.

## Modular AI

```text
com.zosh.ai
```

AI functionality is isolated so it can evolve independently from the core marketplace logic.

## Centralized Frontend API

Axios-based API communication provides a centralized way to communicate with the Spring Boot backend.

## Global State Management

Redux Toolkit manages shared frontend state and asynchronous operations.

## Secure Authentication

JWT + Spring Security protect authenticated API operations and role-specific functionality.

## Multiple Payment Providers

The application integrates both Stripe and Razorpay for payment processing.

---

# 🌐 Deployment Architecture

## Frontend

```text
GitHub
   │
   ▼
Vercel
   │
   ▼
React + TypeScript
Application
```

## Backend

```text
GitHub
   │
   ▼
Render
   │
   ▼
Spring Boot
Application
```

## Database

```text
Spring Boot
     │
     ▼
Spring Data JPA
     │
     ▼
Hibernate
     │
     ▼
MySQL
```

---

# 🔗 Project Links

### 🌐 Live Frontend

https://zosh-bazaar-frontend.vercel.app

### ⚙️ Backend API

https://zosh-bazaar-backend.onrender.com

### 💻 GitHub

https://github.com/VISHAL55UIET

### 🔗 LinkedIn

https://www.linkedin.com/in/vishal-singh-5b052828a/

---

# 👨‍💻 Developer

## Vishal Singh

**B.Tech — Computer Science & Engineering**

Interested in building scalable full-stack and backend systems using:

- Java
- Spring Boot
- Spring Security
- REST APIs
- MySQL
- React
- TypeScript
- Redux Toolkit
- Data Structures & Algorithms
- AI Integration

---

# ⭐ Support

If you find **Zosh Bazaar** useful or interesting, consider giving the repository a ⭐.

Feedback, suggestions, and improvements are always welcome.

---

# 📜 License

This project is intended for educational, portfolio, and demonstration purposes.
