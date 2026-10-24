# 🛒 CLICK-CART

> A full-stack e-commerce application for online shopping, product management, cart operations, order processing, and administration.

![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?logo=vite&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Backend-339933?logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-4-000000?logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb&logoColor=white)
![License](https://img.shields.io/badge/License-See%20Notice-lightgrey)

## 📑 Table of Contents

- [Overview](#-overview)
- [Why, What, and How](#-why-what-and-how)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Project Objectives and Scope](#-project-objectives-and-scope)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation and Setup](#-installation-and-setup)
- [Usage Guide](#-usage-guide)
- [API Route Groups](#-api-route-groups)
- [Security Considerations](#-security-considerations)
- [Limitations and Future Enhancements](#-limitations-and-future-enhancements)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

## 🚀 Overview

CLICK-CART is a full-stack online shopping application built with React and Node.js. It combines a responsive shopping interface with a backend responsible for authentication, product operations, cart management, addresses, orders, reviews, and promotional features.

The project separates the frontend and backend into independent applications, making it easier to develop the user interface and server-side functionality independently.

## 💡 Why, What, and How

### Why — The Problem

Online shopping applications need more than a product catalog. They must coordinate user authentication, product discovery, shopping carts, customer addresses, order processing, and administrative operations.

Implementing these workflows independently without a consistent application architecture can lead to duplicated logic, disconnected data, and difficult maintenance.

### What — The Solution

CLICK-CART provides an e-commerce application with customer-facing shopping features and administrative functionality.

Key capabilities include:

- **User Authentication:** Register, log in, and maintain an authenticated application session.
- **Product Discovery:** Browse product listings, view product details, and search for products.
- **Shopping Cart:** Manage selected products before checkout.
- **Checkout and Orders:** Support checkout, customer addresses, order management, and payment-related workflows.
- **Product Administration:** Provide administrative routes for managing products and orders.
- **Reviews and Promotional Features:** Include dedicated backend route groups for product reviews and common promotional features.

### How — The Implementation

1. **Frontend:** React renders the shopping interface, authentication pages, customer account pages, and administration screens.
2. **State Management:** Redux Toolkit and React Redux manage shared application state, including authentication.
3. **Routing:** React Router maps URLs to the appropriate shopping, authentication, and administration pages.
4. **Backend API:** Express exposes REST-style route groups for authentication, products, carts, addresses, orders, search, reviews, and promotional features.
5. **Database:** Mongoose connects the backend to MongoDB for application data.
6. **Supporting Services:** Backend dependencies provide password hashing, token-based authentication, cookie handling, image hosting, and PayPal-related integration.

**Target audience:** Developers learning full-stack JavaScript, students building e-commerce projects, and contributors exploring frontend state management and backend API development.

## ✨ Features

### Customer Experience

- **Authentication:** Registration, login, and authentication-state checking.
- **Product Browsing:** Browse product listings and product categories.
- **Product Search:** Search the catalog using the dedicated search interface.
- **Shopping Cart:** Manage products selected for purchase.
- **Checkout:** Review the shopping cart and proceed through the checkout interface.
- **Account Management:** Access the customer account page and address-related functionality.
- **Order and Payment Pages:** Display payment return and payment-success workflows.
- **Product Reviews:** Provide a dedicated backend endpoint group for review operations.

### Administration

- **Admin Dashboard:** Access the administrative dashboard.
- **Product Management:** Use the product administration interface and API.
- **Order Management:** Access administrative order operations.
- **Promotional Features:** Manage common feature-related functionality through the admin interface.

### Developer Experience

- Separate frontend and backend applications.
- Vite development server and production build tooling.
- Redux Toolkit for application state management.
- Express route modules organized by functional area.
- Mongoose for MongoDB connectivity and data modeling.

## 🛠️ Tech Stack

### Frontend

![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat&logo=vite&logoColor=white)
![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-764ABC?style=flat&logo=redux&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat&logo=tailwindcss&logoColor=white)

| Technology | Purpose |
|---|---|
| React 18 | Component-based user interface |
| Vite 5 | Frontend development server and production build |
| React Router DOM 6 | Client-side navigation |
| Redux Toolkit | Shared application state |
| React Redux | Connects React components to Redux |
| Axios | HTTP requests to backend APIs |
| Tailwind CSS 3 | Utility-first styling |
| Radix UI | Accessible interface primitives |
| Lucide React | Interface icons |
| PostCSS and Autoprefixer | CSS processing and browser compatibility |

### Backend

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Express 4 | HTTP server and API routing |
| MongoDB | Document-oriented data storage |
| Mongoose 8 | MongoDB object modeling |
| bcryptjs | Password hashing |
| JSON Web Token (`jsonwebtoken`) | Token-based authentication |
| cookie-parser | Cookie parsing |
| CORS | Cross-origin request configuration |
| dotenv | Environment variable loading support |
| Multer | Multipart upload handling |
| Cloudinary | Image and media hosting integration |
| PayPal REST SDK | PayPal-related payment integration |
| Nodemon | Automatic backend restart during development |

## 🏗️ Architecture

CLICK-CART uses a client-server architecture.

```text
                    Customer / Admin
                           |
                           v
                   React Frontend
                     (Vite :5173)
                           |
                 Axios / HTTP Requests
                           |
                           v
                   Express Backend
                     (Default :5000)
                           |
             +-------------+-------------+
             |             |             |
             v             v             v
        Auth Routes    Shopping Routes  Admin Routes
             |             |             |
             |       +-----+------+      |
             |       |     |      |      |
             v       v     v      v      v
        Authentication Cart  Orders  Products
             |             |             |
             +-------------+-------------+
                           |
                           v
                     Mongoose ODM
                           |
                           v
                       MongoDB
                           
     Supporting integrations:
     Cloudinary — Media hosting
     PayPal SDK — Payment-related functionality
```

### Architectural Responsibilities

| Layer | Responsibility |
|---|---|
| React client | Renders shopping, authentication, and administration screens |
| Redux store | Maintains shared frontend state |
| React Router | Handles client-side navigation |
| Express server | Exposes backend API endpoints |
| Route modules | Organize authentication, products, carts, orders, and related features |
| Mongoose | Connects application models and operations to MongoDB |
| External services | Support image hosting and payment-related workflows |

## 🎯 Project Objectives and Scope

### Objectives

- Build a maintainable full-stack JavaScript application.
- Implement customer authentication and protected application routes.
- Provide product discovery and shopping cart workflows.
- Separate administrative operations from customer-facing features.
- Organize backend APIs into reusable functional modules.
- Integrate database and supporting service dependencies.

### In Scope

- Customer registration and login.
- Product listing and search interfaces.
- Shopping cart and address-related routes.
- Checkout and order-related pages.
- Administrative product and order interfaces.
- Review and promotional feature routes.
- MongoDB integration through Mongoose.
- Payment-related and image-hosting dependencies.

### Out of Scope

The repository's dependency list and route structure alone do not establish support for:

- Production-grade payment compliance or certification.
- Automated deployment and CI/CD.
- A complete automated test suite.
- Inventory synchronization with external retailers.
- Enterprise accounting and tax compliance.
- Production monitoring and disaster recovery.

These require separate implementation and verification.

## 📂 Project Structure

The repository is organized into two primary applications:

```text
CLICK-CART/
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── admin-view/
│   │   │   ├── auth/
│   │   │   ├── common/
│   │   │   └── shopping-view/
│   │   ├── pages/
│   │   │   ├── admin-view/
│   │   │   ├── auth/
│   │   │   └── shopping-view/
│   │   ├── store/
│   │   └── App.jsx
│   ├── package.json
│   └── vite.config.js
├── server/
│   ├── routes/
│   │   ├── admin/
│   │   ├── auth/
│   │   ├── common/
│   │   └── shop/
│   ├── server.js
│   └── package.json
└── .gitattributes
```

*The tree above summarizes the repository's application organization; individual source files and supporting configuration may vary.*

### Important Files

| File | Responsibility |
|---|---|
| `client/src/App.jsx` | Defines frontend routes and authentication checks |
| `client/package.json` | Frontend dependencies and Vite scripts |
| `client/vite.config.js` | Vite configuration |
| `server/server.js` | Express application setup, MongoDB connection, middleware, and API registration |
| `server/package.json` | Backend dependencies and runtime scripts |

## 💻 Prerequisites

Install the following software before running the project:

- **Node.js and npm:** Use a Node.js version compatible with the installed Vite and backend dependencies.
- **MongoDB:** A local MongoDB server or a MongoDB connection URI.
- **Git:** Required to clone the repository.
- **Modern browser:** For the React frontend.

Optional services, depending on which integrations you configure:

- Cloudinary account for media uploads.
- PayPal developer credentials for payment integration.

Verify your installations:

```bash
node --version
npm --version
git --version
```

## ⚙️ Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/pratikabhang/CLICK-CART.git
cd CLICK-CART
```

### 2. Configure MongoDB

Start your MongoDB instance or create a database in a hosted MongoDB environment.

**Important:** The current `server/server.js` contains a placeholder connection string:

```js
mongoose.connect("db_url");
```

Replace this placeholder with your actual MongoDB connection URI before starting the backend.

For a more secure configuration, update the server to read the connection URI from an environment variable:

```js
require("dotenv").config();

mongoose
  .connect(process.env.MONGODB_URI)
  .then(() => console.log("MongoDB connected"))
  .catch((error) => {
    console.error("MongoDB connection failed:", error.message);
    process.exit(1);
  });
```

Create a `server/.env` file:

```dotenv
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/click_cart
```

For a hosted database, replace the local URI with your provider's connection string.

The example above requires the backend to load `dotenv` and use `process.env.MONGODB_URI`; those changes are not present in the current server connection code.

### 3. Install Backend Dependencies

```bash
cd server
npm install
```

Start the backend in development mode:

```bash
npm run dev
```

The current `server.js` uses port `5000` by default. The frontend's configured CORS origin is `http://localhost:5173`.

**Startup note:** The current `npm start` script is configured as `server.js`, rather than `node server.js`. Use `npm run dev` for the supplied Nodemon development script, or correct the production start script to `"start": "node server.js"`.

### 4. Install Frontend Dependencies

Open a second terminal from the repository root:

```bash
cd client
npm install
```

Start the Vite development server:

```bash
npm run dev
```

Open the URL printed by Vite, normally:

[http://localhost:5173](http://localhost:5173)

### 5. Build the Frontend

To create a production frontend build:

```bash
cd client
npm run build
```

To preview the generated build locally:

```bash
npm run preview
```

The backend must be configured separately and remain available for API-dependent features.

### 6. Lint the Frontend

Run the configured ESLint script:

```bash
cd client
npm run lint
```

### Configuration Checklist

Before testing the full application, verify the following:

- [ ] MongoDB is running and accessible.
- [ ] The placeholder database connection has been replaced.
- [ ] The backend starts without connection errors.
- [ ] The frontend can reach the backend.
- [ ] Authentication and cookie settings work in the local environment.
- [ ] Payment and image-hosting credentials are configured if required by the relevant workflows.

The repository does not currently provide a root-level `.env.example`. Create one when formalizing the environment configuration, and ensure secret files are excluded from version control.

## ▶️ Usage Guide

### Customer Workflow

1. Start the backend and frontend.
2. Open the application in your browser.
3. Register a customer account or log in.
4. Browse products and use the available search functionality.
5. Add products to the cart.
6. Proceed to checkout and manage the relevant account or address details.
7. Follow the configured payment flow.
8. View the payment result through the available return or success page.

The exact workflow depends on the configured backend, database, and payment provider.

### Administrative Workflow

The frontend defines the following administrative routes:

| Route | Purpose |
|---|---|
| `/admin/dashboard` | Administrative dashboard |
| `/admin/products` | Product administration |
| `/admin/orders` | Order administration |
| `/admin/features` | Promotional or feature management |

Access to administrative functionality depends on the authentication and authorization logic configured by the application.

### Customer-Facing Routes

| Route | Purpose |
|---|---|
| `/auth/login` | Login page |
| `/auth/register` | Registration page |
| `/shop/home` | Shopping home page |
| `/shop/listing` | Product listing |
| `/shop/search` | Product search |
| `/shop/checkout` | Checkout interface |
| `/shop/account` | Customer account |
| `/shop/paypal-return` | Payment-provider return flow |
| `/shop/payment-success` | Payment success page |

These are client-side routes defined in `client/src/App.jsx`, not standalone backend API endpoints.

## 🔌 API Route Groups

The Express application registers the following backend route prefixes:

| Prefix | Responsibility |
|---|---|
| `/api/auth` | Authentication operations |
| `/api/admin/products` | Administrative product operations |
| `/api/admin/orders` | Administrative order operations |
| `/api/shop/products` | Customer-facing product operations |
| `/api/shop/cart` | Shopping cart operations |
| `/api/shop/address` | Customer address operations |
| `/api/shop/order` | Order operations |
| `/api/shop/search` | Product search |
| `/api/shop/review` | Review operations |
| `/api/common/feature` | Common feature-related operations |

Example base URL for local development:

```text
http://localhost:5000/api
```

The registered prefixes identify the route groups. Specific HTTP methods, request bodies, and response formats are defined by their individual route handlers; consult those files before integrating external clients.

## 🔐 Security Considerations

Before deploying CLICK-CART publicly, review the following areas:

- **Database configuration:** Move database credentials into environment variables and avoid hardcoded connection strings.
- **Authentication:** Verify password hashing, token expiration, and session invalidation.
- **Authorization:** Enforce customer and administrator permissions on the backend, not only in frontend route guards.
- **Cookies and CORS:** Configure secure cookie attributes and restrict allowed origins to trusted deployments.
- **Input validation:** Validate request bodies, identifiers, prices, quantities, and uploaded files.
- **Payment processing:** Verify payment status on the server before marking orders as paid.
- **Secrets:** Never commit database passwords, JWT secrets, PayPal credentials, or Cloudinary API secrets.
- **Uploads:** Validate image types and sizes before processing or forwarding uploads.
- **Dependencies:** Audit and update dependencies regularly.

A frontend success page alone is not proof that a payment has succeeded. Payment confirmation must be validated by the backend or the payment provider.

## 🔮 Limitations and Future Enhancements

Potential improvements include:

- Add a root-level README configuration guide and `.env.example` files.
- Replace hardcoded database configuration with environment-based settings.
- Correct the backend production start script.
- Add automated tests for authentication, cart operations, and order processing.
- Document endpoint-specific request and response schemas.
- Add API validation and centralized error handling.
- Add a consistent database transaction strategy for order creation.
- Improve deployment documentation for frontend, backend, and MongoDB.
- Add CI checks for linting, builds, and tests.
- Document payment-provider setup and test-mode procedures.
- Add logging, health checks, and production monitoring.

These are recommended improvements rather than claims about existing functionality.

## 🤝 Contributing

Contributions, bug reports, and feature suggestions are welcome.

1. Fork the repository.
2. Clone your fork:

   ```bash
   git clone https://github.com/<your-username>/CLICK-CART.git
   cd CLICK-CART
   ```

3. Create a feature branch:

   ```bash
   git checkout -b feature/your-feature-name
   ```

4. Make your changes in the appropriate client or server directory.
5. Run the frontend linter and build; test any affected backend functionality.
6. Commit your changes:

   ```bash
   git add .
   git commit -m "Improve shopping workflow"
   ```

7. Push your branch:

   ```bash
   git push origin feature/your-feature-name
   ```

8. Open a pull request with a clear description of the changes and testing performed.

### Contribution Guidelines

- Keep frontend components and backend route handlers organized by responsibility.
- Follow the existing JavaScript and React conventions.
- Never commit credentials or real customer data.
- Include configuration and database migration instructions when needed.
- Test authorization as well as successful and unsuccessful operations.
- Update documentation when routes or setup requirements change.

## 📄 License

The backend's `package.json` declares the **ISC License** for the server package. A repository-wide `LICENSE` file was not confirmed during this review.

Check the intended license for the complete project and add a root-level `LICENSE` file before redistributing it.

## 👨‍💻 Author

**Pratik Abhang**

- GitHub: [@pratikabhang](https://github.com/pratikabhang)
- Repository: [CLICK-CART](https://github.com/pratikabhang/CLICK-CART)

---

⭐ If you find this project useful, consider starring the repository.

*Built with React, Node.js, Express, and MongoDB.*
