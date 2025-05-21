# LUMIÈRE Jewelry E-commerce Application

## Overview

This is a full-stack e-commerce application for a luxury jewelry brand called LUMIÈRE. The application uses a React frontend with TailwindCSS and shadcn/ui components, a Node.js Express backend, and Drizzle ORM for database operations. The application is designed to handle product browsing, user authentication, cart management, wishlists, and checkout processes.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend

- **Technology**: React with TypeScript
- **Styling**: TailwindCSS with shadcn/ui component library
- **State Management**: Context API for global state (Auth, Cart, Wishlist)
- **Routing**: Wouter for client-side routing
- **API Integration**: TanStack Query for data fetching and caching
- **Form Handling**: React Hook Form with Zod for validation

The frontend follows a component-based architecture with shared UI components, page components, and context providers for global state management. The application uses custom hooks for encapsulating related logic.

### Backend

- **Technology**: Node.js with Express
- **API**: RESTful API endpoints
- **Session Management**: Express-session with MemoryStore
- **Authentication**: Custom implementation with bcrypt for password hashing
- **Database ORM**: Drizzle ORM

The backend serves both the API endpoints and static frontend assets in production. In development, it uses Vite as middleware.

### Database

- **Technology**: PostgreSQL (via Drizzle ORM)
- **Schema**: Users, Products, Categories, Cart Items, Wishlist Items, Orders, Testimonials
- **Schema Validation**: Zod for type validation and schema generation

## Key Components

### Authentication System

- User registration and login
- Session-based authentication
- Protected routes on frontend and backend
- Profile management

### Product Management

- Product browsing by categories
- Product search and filtering
- Product details with variants
- Featured and new product collections

### Shopping Experience

- Cart management (add, remove, update quantities)
- Wishlist functionality
- Checkout process with shipping and payment options
- Order history

### UI Components

- Responsive navigation with mobile support
- Product galleries and cards
- Form components with validation
- Toast notifications for user feedback

## Data Flow

1. **User Authentication**:
   - Frontend sends credentials to backend
   - Backend validates and creates session
   - Session cookie is returned to client
   - Protected requests include session cookie

2. **Product Browsing**:
   - Frontend fetches products/categories from API
   - Data is cached with TanStack Query
   - User interactions (filtering, pagination) trigger new requests

3. **Cart Management**:
   - Cart state stored in CartContext
   - Actions dispatch API requests to update server state
   - Server responses update the local context state

4. **Checkout Process**:
   - User enters shipping/payment details
   - Form validation with Zod schemas
   - Order creation on the backend
   - Cart cleared after successful checkout

## External Dependencies

### Frontend Libraries
- TailwindCSS for styling
- shadcn/ui for component library (based on Radix UI)
- React Hook Form for form handling
- Zod for validation
- TanStack Query for data fetching
- Wouter for routing

### Backend Libraries
- Express for API and server
- bcryptjs for password hashing
- Drizzle ORM for database operations
- express-session for session management

## Deployment Strategy

The application is configured for deployment on Replit:

1. **Development Mode**:
   - Runs with `npm run dev`
   - Uses Vite for frontend hot-reloading
   - Express server for API endpoints

2. **Production Build**:
   - Frontend built with Vite
   - Backend bundled with esbuild
   - Static assets served by Express

3. **Database**:
   - Uses PostgreSQL provided by Replit
   - Connection via environment variable (DATABASE_URL)
   - Schema migrations handled by Drizzle Kit

4. **Environment Configuration**:
   - Environment variables for database connection
   - Session secret configuration
   - Production/development mode detection

## Getting Started

1. Ensure PostgreSQL is properly set up in your Replit environment
2. Set the DATABASE_URL environment variable
3. Run `npm run db:push` to set up the database schema
4. Run `npm run dev` to start the development server
5. For production, run `npm run build` followed by `npm run start`