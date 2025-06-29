# Kashmir Carpentry LLC - Accounting Management System

A comprehensive accounting management system built for Kashmir Carpentry LLC using Python FastAPI.

## Features

- User Authentication and Authorization
- Customer Management
- Project Tracking
- Inventory Management
- Expense Tracking
- Invoice Generation
- Financial Reporting

## System Requirements

- Python 3.8 or higher
- pip (Python package installer)
- SQLite3

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd kashmir-carpentry-system
```

2. Create a virtual environment:
```bash
python -m venv venv
```

3. Activate the virtual environment:
- On Windows:
```bash
.\venv\Scripts\activate
```
- On macOS/Linux:
```bash
source venv/bin/activate
```

4. Install dependencies:
```bash
pip install -r requirements.txt
```

## Initial Setup

1. Initialize the database and create an admin user:
```bash
python -m src.init_db
```

This will create:
- An admin user (username: admin, password: admin123)
- Sample inventory items
- Sample customer data
- Sample project data

**Important**: Change the admin password after first login!

## Running the Application

1. Start the FastAPI server:
```bash
uvicorn src.main:app --reload
```

2. Access the application:
- API Documentation: http://localhost:8000/docs
- Alternative API Documentation: http://localhost:8000/redoc

## Default Admin Credentials

- Username: admin
- Password: admin123

**Important**: Change these credentials immediately after first login!

## API Endpoints

### Authentication
- POST /token - Get access token

### Users
- POST /users/ - Create new user
- GET /users/me - Get current user info

### Customers
- POST /customers/ - Create new customer
- GET /customers/ - List all customers

### Projects
- POST /projects/ - Create new project
- GET /projects/ - List all projects

### Inventory
- POST /inventory/ - Add new inventory item
- GET /inventory/ - List all inventory items

### Expenses
- POST /expenses/ - Record new expense
- GET /expenses/ - List all expenses

### Invoices
- POST /invoices/ - Generate new invoice
- GET /invoices/ - List all invoices

## Security

The system implements:
- JWT-based authentication
- Password hashing using bcrypt
- Role-based access control
- Protected API endpoints

## Database

The system uses SQLite as the default database. The database file (`kashmir_carpentry.db`) will be created automatically in the root directory when you first run the application.

## Error Handling

The API implements comprehensive error handling:
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 500: Internal Server Error

## Best Practices

1. Change the default admin password immediately after setup
2. Regularly backup the database file
3. Keep the SECRET_KEY secure and change it in production
4. Update dependencies regularly for security patches

## Production Deployment

For production deployment:

1. Change the SECRET_KEY in src/auth.py
2. Use a production-grade database (e.g., PostgreSQL)
3. Set up proper SSL/TLS certificates
4. Configure CORS settings appropriately
5. Use a production server (e.g., Gunicorn)
6. Set up proper logging
7. Implement rate limiting
8. Set up monitoring

## Support

For support or bug reports, please create an issue in the repository.
