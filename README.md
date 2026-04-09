# Warehouse Shipment Tracking System

A full-stack web application for managing and tracking warehouse shipments.

## Tech Stack

- Frontend: React + Vite
- Backend: Node.js + Express
- Database: MongoDB
- API: REST

## Features

- Shipment CRUD operations
- Validation and clear error messages
- Search and filter module (shipment ID, item name, status, combined)
- Sorting module (shipment ID, item name, quantity, status, asc/desc)
- Pagination
- Dashboard analytics with recent shipments summary
- Sidebar navigation and header quick actions
- Success/error toast alerts and reusable error message component
- Loading spinner and empty state UI
- Responsive UI for desktop and mobile

## Shipment Fields

- Shipment ID (required, unique)
- Item Name (required)
- Quantity (required, positive number)
- Status (Pending, Packed, Shipped, Delivered, Cancelled)

## Project Structure

```
hackathon/
  backend/
  frontend/
```

## Setup

1. Create MongoDB database and get your connection URI.
2. Configure backend environment variables.
3. Install dependencies and run app.

### Backend env file

Create file: `backend/.env`

Example:

```
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/warehouse_shipments
CLIENT_ORIGIN=http://localhost:5173
```

### Install and Run

From root folder:

```
npm install
npm run install-all
npm run dev:all
```

Frontend runs at `http://localhost:5173`

Backend runs at `http://localhost:5000`

## API Endpoints

- `GET /api/health`
- `GET /api/analytics`
- `GET /api/shipments`
  - Query params: `shipmentId`, `itemName`, `status`, `sortBy`, `sortOrder`, `page`, `limit`
- `GET /api/shipments/search`
  - Same query params as `/api/shipments`
- `GET /api/shipments/:id`
- `POST /api/shipments`
- `PUT /api/shipments/:id`
- `DELETE /api/shipments/:id`
- `GET /api/shipments/analytics/summary`

## Frontend Components

- `Dashboard` (implemented in `App` layout)
- `ShipmentTable`
- `ShipmentForm`
- `SearchFilterBar`
- `SortControls`
- `AnalyticsCards`
- `Pagination`
- `Sidebar`
- `HeaderBar`
- `ErrorMessage`
- `ToastMessage`
- `LoadingSpinner`

## Backend Structure

- Routes: `backend/routes/shipmentRoutes.js`
- Controllers: `backend/controllers/shipmentController.js`
- Models: `backend/models/Shipment.js`
- Validation middleware: `backend/middleware/validateShipment.js`
- Centralized error middleware: `backend/middleware/errorHandler.js`

## Dummy Data (Seed)

1. Configure `backend/.env`
2. Run:

```
npm run seed
```

Dummy records are in `backend/data/dummyShipments.json`.

## UI Preview Structure

```
+--------------------------------------------------------------+
| Sidebar                     | Header (title + quick actions)|
| - Dashboard                 +-------------------------------+
| - Shipments                 | Analytics Cards               |
| - Analytics                 +-------------------------------+
| + Quick Add                 | Recent Shipments Summary      |
|                             +-------------------------------+
|                             | Search/Filter + Sort Controls |
|                             +-------------------------------+
|                             | Shipment Table                |
|                             +-------------------------------+
|                             | Pagination                    |
+--------------------------------------------------------------+
```
