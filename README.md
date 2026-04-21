# Digitic E-Commerce Client

## 1. Project Overview

The **Digitic Client** is the customer-facing e-commerce storefront. It provides a complete shopping experience including product browsing, cart management, secure checkout with Stripe, user accounts, and order tracking.

**Target Users:** Online shoppers, customers

---

## 2. Tech Stack

| Category         | Technology                       |
| ------------------| ----------------------------------|
| Framework        | React 18.3                       |
| Build Tool       | Vite 5.3                         |
| State Management | Redux Toolkit                    |
| UI Library       | Ant Design 5.19                  |
| Styling          | Bootstrap 5.3, CSS               |
| Routing          | React Router DOM 6.24            |
| Forms            | Formik + Yup                     |
| HTTP Client      | Axios                            |
| Payment          | Stripe (@stripe/react-stripe-js) |
| Icons            | @ant-design/icons, react-icons   |
| Rich Text        | React Quill                      |
| Notifications    | React Toastify                   |
| File Upload      | React Dropzone                   |

---

## 3. Features

### Authentication & User Management

- User registration and login
- Forgot/reset password flow
- JWT-based authentication
- Protected routes for authenticated users

### Shopping Experience

- Product catalog with filtering and sorting
- Product details with image zoom
- Color and size selection
- Product ratings and reviews
- Wishlist functionality

### Cart & Checkout

- Add/remove products from cart
- Update quantities
- Stripe-powered secure checkout
- Order confirmation and tracking

### User Dashboard

- View order history
- Update profile information
- Manage saved addresses

### Content

- Blog section with articles
- Static pages (Privacy Policy, Terms, Shipping, Refund)
- Contact form for enquiries

### UI/UX

- Responsive design (Bootstrap grid)
- Toast notifications for actions
- Image zoom on product pages
- Marquee announcements
- SEO-friendly meta tags

---

## 4. Project Structure

```
client/
├── src/
│   ├── app/               # Store configuration
│   ├── assets/            # Static assets
│   ├── components/        # Shared UI components
│   │   ├── Layout.jsx
│   │   ├── Header.jsx
│   │   ├── Footer.jsx
│   │   ├── ProductCard.jsx
│   │   ├── BlogCard.jsx
│   │   ├── CheckoutForm.jsx
│   │   └── ...
│   ├── features/          # Redux slices (by domain)
│   │   ├── user/          # User auth state
│   │   ├── products/      # Product catalog
│   │   ├── blogs/         # Blog content
│   │   ├── brands/        # Brand data
│   │   ├── categories/    # Categories
│   │   ├── colors/        # Product colors
│   │   └── enquiries/     # Contact forms
│   ├── pages/             # Route-level components
│   │   ├── Home.jsx
│   │   ├── Store.jsx
│   │   ├── SingleProduct.jsx
│   │   ├── Cart.jsx
│   │   ├── Checkout.jsx
│   │   ├── Wishlist.jsx
│   │   ├── Orders.jsx
│   │   ├── Profile.jsx
│   │   ├── Blogs.jsx
│   │   ├── Contact.jsx
│   │   ├── Login.jsx
│   │   ├── Signup.jsx
│   │   └── ...
│   ├── routing/           # Route guards
│   │   ├── OpenRoutes.jsx
│   │   └── PrivateRoutes.jsx
│   ├── utils/             # Utilities
│   │   └── index.js
│   ├── App.jsx            # Route definitions
│   ├── main.jsx           # Entry point
│   └── index.css          # Global styles
├── public/                # Static files (images)
├── index.html
├── vite.config.js
└── package.json
```

---

## 5. Setup Instructions

### Prerequisites

- Node.js 18+ installed
- Backend server running on `http://localhost:5000`

### Installation

```bash
# Navigate to client directory
cd client

# Install dependencies
npm install
```

### Environment Variables

Create a `.env` file in the `client/` root:

```env
VITE_API_BASE_URL=http://localhost:5000/api
VITE_STRIPE_PUBLISHABLE_KEY=pk_test_your_stripe_key
```

### Running the Project

```bash
# Development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

Default dev server: `http://localhost:5173`

---

## 6. API Integration

The client communicates with the backend via REST API:

| Endpoint                                     | Purpose                       |
| -------------------------------------------- | ----------------------------- |
| `POST /api/users/register`                   | User registration             |
| `POST /api/users/login`                      | User login                    |
| `GET /api/products`                          | Fetch products (with filters) |
| `GET /api/products/:id`                      | Product details               |
| `PUT /api/products/wishlist`                 | Add to wishlist               |
| `PUT /api/products/rating`                   | Submit product rating         |
| `POST /api/users/cart`                       | Add to cart                   |
| `GET /api/users/cart`                        | Get user cart                 |
| `DELETE /api/users/cart/:cartId`             | Remove from cart              |
| `PUT /api/users/cart/:id/:qty`               | Update quantity               |
| `POST /api/users/order/checkout`             | Initiate Stripe payment       |
| `POST /api/users/order/payment-verification` | Verify payment                |
| `GET /api/users/orders`                      | Order history                 |
| `GET /api/blogs`                             | Fetch blog posts              |
| `POST /api/enquiries`                        | Submit contact form           |

### Stripe Integration

- Uses `@stripe/react-stripe-js` for payment elements
- Payment intent created via backend
- Client secret returned for secure checkout

---

## 7. Scripts

| Script  | Command                 | Purpose                  |
| ------- | ----------------------- | ------------------------ |
| dev     | `vite`                  | Start development server |
| build   | `vite build`            | Create production build  |
| preview | `vite preview`          | Preview production build |
| lint    | `eslint . --ext js,jsx` | Run ESLint checks        |

---

## 8. Deployment Notes

### Production Build

```bash
npm run build
```

Generates static files in `dist/` folder suitable for deployment.

### Environment Variables for Production

```env
VITE_API_BASE_URL=https://your-api-domain.com/api
VITE_STRIPE_PUBLISHABLE_KEY=pk_live_your_live_key
```

### Recommended Hosting

- **Netlify**: Drag-and-drop `dist/` folder
- **Vercel**: GitHub integration with auto-deploy
- **Cloudflare Pages**: Excellent performance with CDN
