# Point of Sale System

## Overview

This is a modern Point of Sale (POS) system built for Arabic-speaking retail businesses. The application provides a complete retail management solution with product management, sales processing, inventory tracking, and comprehensive licensing system for commercial distribution. The system is designed as a full-stack web application with offline capabilities and supports both individual store operations and multi-tenant licensing for business distribution.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The frontend is built using **React** with **TypeScript** following a component-based architecture. The application uses **Vite** as the build tool and development server for fast development and optimized production builds.

**UI Framework**: The system leverages **shadcn/ui** components built on top of **Radix UI** primitives, providing a consistent and accessible design system. **Tailwind CSS** is used for styling with CSS variables for theming support.

**State Management**: **TanStack Query (React Query)** handles server state management, caching, and synchronization. Local state is managed using React's built-in hooks with localStorage for offline persistence.

**Form Handling**: **React Hook Form** with **Zod** validation ensures type-safe form handling and validation across the application.

**Internationalization**: The application is built with Arabic language support (RTL layout) as the primary interface, with proper font rendering and cultural considerations for Lebanese retail businesses.

### Backend Architecture
The backend follows a **REST API** architecture built with **Express.js** and **TypeScript**. The server provides clean separation between routing, business logic, and data access layers.

**API Design**: RESTful endpoints handle CRUD operations for products, receipts, settings, and licensing. The API includes specialized endpoints for license validation, device activation, and multi-tenant customer management.

**Authentication**: Basic HTTP authentication for admin functions with environment variable-based credentials. Device fingerprinting for license activation tracking.

**Storage Layer**: Repository pattern implemented through the `ILicenseStorage` interface, allowing for flexible data access strategies. The `DatabaseStorage` class provides concrete implementation using Drizzle ORM.

### Data Storage Solutions
**Database**: **PostgreSQL** serves as the primary database, providing ACID compliance and robust data integrity. The system uses **Neon Database** as the hosted PostgreSQL solution with WebSocket support for real-time connections.

**ORM**: **Drizzle ORM** provides type-safe database operations with automatic TypeScript inference. The schema is defined in a shared location for consistency between frontend and backend.

**Schema Design**: Comprehensive database schema supporting:
- Customer management for licensing
- License types with configurable features and pricing
- License tracking with activation limits and device fingerprinting
- Usage analytics and payment tracking
- Audit logging for compliance

**Offline Support**: Local storage mechanisms for critical POS operations when network connectivity is limited, with sync capabilities when connection is restored.

### Licensing System Architecture
The application includes a sophisticated licensing system designed for commercial distribution:

**Multi-tenant Support**: Customer management with company profiles, contact information, and subscription tracking.

**License Types**: Configurable license packages with different feature sets, device limits, and validity periods.

**Activation Management**: Device fingerprinting and activation limits to prevent unauthorized usage while allowing legitimate device changes.

**Usage Tracking**: Comprehensive monitoring of license usage patterns, feature utilization, and system performance metrics.

**Payment Integration**: Built-in payment tracking and subscription management for recurring license fees.

## External Dependencies

**Database Services**: 
- Neon Database (PostgreSQL hosting)
- WebSocket support for real-time database connections

**Development Tools**:
- Vite for frontend build and development
- ESBuild for backend bundling
- TypeScript for type safety across the stack

**UI Libraries**:
- Radix UI primitives for accessible components
- shadcn/ui for pre-built component library
- Tailwind CSS for utility-first styling
- Lucide React for iconography

**Backend Dependencies**:
- Express.js for REST API server
- Drizzle ORM for database operations
- CSV parsing/stringifying for data import/export
- Multer for file upload handling (if applicable)
- Connect-pg-simple for session storage

**Security & Validation**:
- Zod for runtime type validation
- React Hook Form for form state management
- Crypto module for license key generation and device fingerprinting

**State Management**:
- TanStack Query for server state and caching
- LocalStorage for offline persistence
- Session management for admin authentication