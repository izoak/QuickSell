# Premium Drive - Vehicle Marketplace

A full-stack web application for browsing and purchasing premium vehicles including cars and motorcycles.
The app is built with Angular on the frontend and Django REST Framework on the backend, connected via a JWT-authenticated REST API.

## Features

- **Vehicle Catalog**: Browse cars and motorcycles with detailed specifications
- **User Authentication**: JWT-based authentication system with route guards
- **Favorites System**: Save and manage favorite vehicles
- **Vehicle Comparison**: Compare multiple vehicles side by side
- **Order Management**: Place and track vehicle orders
- **Review System**: Rate and review vehicles
- **Responsive Design**: Mobile-friendly interface

## Tech Stack

### Backend
- **Django 4.2+**: Web framework
- **Django REST Framework**: API development
- **JWT Authentication**: Secure token-based authentication
- **SQLite**: Database (development)
- **CORS**: Cross-origin resource sharing

### Frontend
- **Angular 21**: Frontend framework
- **TypeScript**: Type-safe JavaScript
- **RxJS**: Reactive programming
- **CSS**: Styling

## Prerequisites

- Python 3.8+
- Node.js 18+
- npm or yarn

## Pages and Functionality

### Authentication - /login and /register
Users can register and log in using forms built with [(ngModel)]. On login, the Django backend returns a JWT token which is stored in localStorage. An HTTP Interceptor automatically attaches the token to all subsequent requests. A Route Guard protects private pages and redirects unauthenticated users to /login. Logout clears the token and ends the session.

### Vehicle Catalog - /car-list and /moto-list
Displays vehicles as cards with name, brand, image, price, and specifications, loaded from the backend via VehicleService. Vehicle data comes from the Django api app with models Category and Vehicle (fields: name, brand, price, type, image, category, year, engine, horsepower, description, available).

Users can browse cars and motorcycles separately, filter by category, and view detailed specifications for each vehicle.

### Vehicle Detail Page - /vehicle-detail/:id
Shows the full vehicle description, price, specifications (year, engine, horsepower), and image. An "Add to Favorites" button saves the vehicle to user's favorites. A "Place Order" button initiates the ordering process.

The page includes a Reviews & Rating section where users can leave one review per vehicle with a 1-5 star rating and written feedback. Average ratings are displayed on both detail pages and vehicle cards.

### Vehicle Comparison - /compare
Allows users to compare multiple vehicles side by side, showing specifications, prices, and features in a comparison table for informed decision making.

### Favorites - /favorites
Users can save vehicles to a personal favorites list for easy access later.

API endpoints:
- GET /api/favorites/ — view saved vehicles
- POST /api/favorites/ — add a vehicle to favorites
- DELETE /api/favorites/<vehicle_id>/ — remove a vehicle from favorites

### Order Management - /orders
Shows all orders for the logged-in user with details including vehicle name, order date, status, and purchase information when applicable.

Order statuses: new → pending → confirmed → test-drive → completed (or cancelled)

### Profile - /profile
A personal account page showing user information, account details, and order history summary.

### Home - /
Landing page with featured vehicles, navigation menu, and quick access to main sections of the application.

## API Endpoints

### Authentication
- POST /api/auth/login/ - User login
- POST /api/auth/register/ - User registration
- POST /api/auth/refresh/ - Refresh JWT token

### Vehicles
- GET /api/vehicles/ - List all vehicles
- GET /api/vehicles/{id}/ - Get vehicle details
- GET /api/categories/ - List vehicle categories

### Orders
- GET /api/orders/ - List user orders
- POST /api/orders/ - Create new order

### Reviews
- GET /api/reviews/ - List vehicle reviews
- POST /api/reviews/ - Create new review

## Project Structure

premiumdrive-main/
├── backend/                 # Django backend
│   ├── api/                # Main API app (vehicles, categories)
│   ├── orders/             # Orders management
│   ├── users/              # User management
│   ├── premiumdrive/       # Django settings
│   └── requirements.txt    # Python dependencies
├── premium-drive/          # Angular frontend
│   ├── src/
│   │   ├── app/
│   │   │   ├── core/       # Core services and guards
│   │   │   ├── pages/      # Application pages
│   │   │   └── shared/     # Shared components
│   └── package.json        # Node dependencies
└── README.md
```
## Team members 
Meldebek Islam, Arseniy Kanshin, Muratov Rassul
