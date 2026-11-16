# Kicks – Full-Stack E-commerce Platform

A sneaker store built as three separate apps: a customer storefront, an admin panel, and a REST API.

**Live:** https://ecommerce-kicks.vercel.app/

## Architecture

```
client/   Next.js 13 storefront (browse, cart, checkout, order history, social login)
admin/    Next.js 13 admin panel (products, orders, sales dashboard)
server/   Express API on MongoDB, deployed on Vercel
```

The API is organized into layers:

- `routes/v1/`: versioned endpoints for products, categories, orders, users, dashboard, auth, and the Stripe webhook
- `controller/`: request handling
- `service/`: business logic, plus the Passport Google and Facebook strategies
- `model/`: Mongoose schemas for users, admins, products, categories, and orders
- `middleware/`: JWT verification, API-key checks, public vs. protected route handling, and error handling

## Features

- **Auth:** email/password login with bcrypt hashing and JWT; Google and Facebook OAuth through Passport.js
- **Payments:** Stripe checkout, with a webhook route mounted before the JSON body parser so it receives the raw request body
- **Admin dashboard:** sales analytics charts (Recharts), plus product and order management
- **State:** Redux Toolkit in both front ends (auth, cart)
- **Images:** served through Cloudinary

## Tech stack

Next.js 13 · React 18 · Redux Toolkit · Recharts · Node.js · Express · MongoDB (Mongoose) · Passport.js · JWT · bcrypt · Stripe · Cloudinary · Vercel

## Running locally

Each app runs separately.

```bash
# API
cd server && npm install && npm start

# Storefront
cd client && npm install && npm run dev

# Admin panel
cd admin && npm install && npm run dev
```

The server needs environment variables for MongoDB, JWT, Stripe, and the Google/Facebook OAuth apps. See `server/utils/environment.js` for the full list.
