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
- Virtual Environment
- SQLite3

## Installation

### Windows Installation

1. Clone or download the repository:
```bash
git clone <repository-url>
cd kashmir-carpentry-system
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
venv\Scripts\activate
```

3. Install dependencies (in this exact order):
```bash
# Upgrade pip and install wheel first
python -m pip install --upgrade pip
pip install wheel

# Install dependencies with binary packages
pip install --no-cache-dir --only-binary :all: -r requirements.txt

# If the above command fails, try:
pip install --no-cache-dir -r requirements.txt
```

4. Initialize the database:
```bash
# Using direct path
python src\init_db.py
```

5. Start the application:
```bash
# Using direct path
uvicorn src.main:app --reload
```

Note: You may see some deprecation warnings about 'orm_mode' - these can be safely ignored as they don't affect functionality.

Troubleshooting for Windows:

1. If you see "module not found" errors:
   - Make sure you're in the project root directory
   - Verify that your virtual environment is activated
   - Try reinstalling the package:
     ```bash
     pip install --no-cache-dir -r requirements.txt
     ```

2. If you get permission errors:
   - Run Command Prompt or PowerShell as administrator
   - Check if antivirus is blocking Python
   - Make sure you have write permissions in the project directory

3. Database Issues:
   - Ensure SQLite is installed
   - Check if the database file was created:
     ```bash
     dir kashmir_carpentry.db
     ```
   - If not, run the initialization again:
     ```bash
     python src\init_db.py
     ```

4. Port Already in Use:
   - Change the port number:
     ```bash
     uvicorn src.main:app --reload --port 8001
     ```

### macOS/Linux

1. Clone the repository:
```bash
git clone <repository-url>
cd kashmir-carpentry-system
```

2. Create and activate a virtual environment:
```bash
python3 -m venv venv
source venv/bin/activate
```

3. Install the package in development mode:
```bash
pip install -e .
```

4. Initialize the database:
```bash
python -m src.init_db
```

5. Start the application:
```bash
python -m uvicorn src.main:app --reload
```

## Initial Setup

The database initialization will create:
- An admin user (username: admin, password: admin123)
- Sample inventory items
- Sample customer data
- Sample project data

**Important**: Change the admin password after first login!

## Accessing the Application

Once the application is running:

1. Open your web browser and navigate to:
   - API Documentation: http://127.0.0.1:8000/docs
   - Alternative API Documentation: http://127.0.0.1:8000/redoc

2. Click on the "Authorize" button in the documentation interface

3. Log in with the default admin credentials:
   - Username: admin
   - Password: admin123

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

## Database

The system uses SQLite as the default database. The database file (`kashmir_carpentry.db`) will be created automatically in the root directory when you first run the application.

## Security Features

- JWT-based authentication
- Password hashing using bcrypt
- Role-based access control
- Protected API endpoints

## Best Practices

1. Change the default admin password immediately after setup
2. Regularly backup the database file
3. Keep the SECRET_KEY secure and change it in production
4. Update dependencies regularly for security patches

## Troubleshooting

### Common Issues

1. Module Not Found Errors:
   - Ensure you're in the project root directory
   - Verify the virtual environment is activated
   - Confirm the package is installed with `pip install -e .`

2. Database Errors:
   - Check if SQLite is installed
   - Ensure write permissions in the project directory
   - Verify database file creation after initialization

3. Port Already in Use:
   - Change the port using `--port` flag:
     ```bash
     python -m uvicorn src.main:app --reload --port 8001
     ```

### Windows-Specific Issues

1. If you see "python is not recognized":
   - Add Python to your PATH environment variable
   - Use `py` instead of `python` command

2. Virtual Environment Issues:
   - Use `python -m venv venv` instead of just `venv`
   - Run `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` in PowerShell if activation is blocked

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
