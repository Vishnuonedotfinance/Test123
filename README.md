# 🚀 Piperocket Finance Management Tool

A comprehensive full-stack finance management application for managing clients, contractors, employees, and assets with advanced reporting capabilities.

![Tech Stack](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

## 📋 Table of Contents
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [API Documentation](#-api-documentation)
- [Project Structure](#-project-structure)
- [GitHub Integration](#-github-integration)

## ✨ Features

### 🔐 Authentication & User Management
- Role-based access control (Admin, Director, Staff)
- Email OTP verification
- JWT token-based authentication
- Password reset functionality
- User CRUD operations with delete protection for Admin

### 👥 Client Management
- Complete CRUD operations
- Service categories: PPC, SEO, Content, Backlink
- SLA & NDA document generation (Word format)
- Agreement status tracking (Live/Expired)
- Automatic end date calculation
- Department & status filtering
- Bulk import/export (Excel)

### 🤝 Contractor Management
- Complete CRUD operations
- Gender field support
- Multi-project assignment capability
- ICA (Independent Contractor Agreement) generation
- Agreement status tracking
- Cost splitting across projects
- Department filtering with 6 departments
- Bulk import/export (Excel)

### 👨‍💼 Employee Management
- Complete CRUD operations
- Gender field support
- Multi-project assignment capability
- Offer Letter generation with salary calculations
- Employee status tracking
- Cost splitting across projects
- Department filtering
- Bulk import/export (Excel)

### 📦 Asset Tracker
- Asset inventory management
- Warranty status calculation (Active/Expired)
- Department-wise allocation
- Total asset value tracking
- Bulk import/export (Excel)

### 📊 Reports Module
1. **Department P&L**
   - Revenue, employee cost, contractor cost
   - Profit and profit percentage
   - Client count and resource count by department
   
2. **Client-level Profitability**
   - Resource assignments with cost splitting
   - Profit and P&L percentage per client
   - Department filter
   - Excel export

3. **Resource Utilization**
   - Per-client cost calculation
   - Project count tracking
   - Department-wise filtering
   - Employee and Contractor categorization

### 📈 Dashboard Analytics
- Expiring agreements alert (30-day window)
- Expired agreements list
- Upcoming birthdays (15-day window)
- Recurring revenue by department (4 departments)
- Employee cost breakdown by department (6 departments)
- Contractor cost breakdown by department (6 departments)

### ✅ Approval Workflow
- Staff request submission
- Director approval/rejection/hold with remarks
- Admin reassignment capability
- Complete audit trail
- Monthly reset functionality

### 📄 Document Generation
- SLA (Service Level Agreement)
- NDA (Non-Disclosure Agreement)
- ICA (Independent Contractor Agreement)
- Offer Letter with salary calculations
- Template-based generation using Word documents

## 🛠 Tech Stack

### Backend
- **Framework:** FastAPI (Python)
- **Database:** MongoDB (with Motor async driver)
- **Authentication:** JWT tokens, OTP via email
- **Document Processing:** python-docx, docx-mailmerge
- **Excel Processing:** pandas, openpyxl
- **Validation:** Pydantic

### Frontend
- **Framework:** React 18
- **Routing:** React Router v6
- **HTTP Client:** Axios
- **Styling:** Tailwind CSS
- **UI Components:** Shadcn UI
- **Icons:** Lucide React
- **Notifications:** Sonner (toast notifications)

### DevOps
- **Process Manager:** Supervisor
- **Backend Port:** 8001
- **Frontend Port:** 3000

## 📥 Installation

### Prerequisites
- Python 3.8+
- Node.js 16+
- MongoDB
- npm or yarn

### Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install Python dependencies
pip install -r requirements.txt

# Create .env file
cat > .env << EOF
MONGO_URL=mongodb://localhost:27017
DB_NAME=piperocket_db
JWT_SECRET=your-secret-key-here
CORS_ORIGINS=*
EOF

# Run backend server
uvicorn server:app --host 0.0.0.0 --port 8001 --reload
```

### Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install Node.js dependencies
npm install
# or
yarn install

# Create .env file
cat > .env << EOF
REACT_APP_BACKEND_URL=http://localhost:8001
EOF

# Run frontend development server
npm start
# or
yarn start
```

## ⚙️ Configuration

### Environment Variables

#### Backend (.env)
```env
MONGO_URL=mongodb://localhost:27017    # MongoDB connection string
DB_NAME=piperocket_db                  # Database name
JWT_SECRET=your-secret-key-here        # JWT signing key
CORS_ORIGINS=*                         # CORS allowed origins
```

#### Frontend (.env)
```env
REACT_APP_BACKEND_URL=http://localhost:8001    # Backend API URL
```

### Default Admin Credentials
- **Email:** Vishnu@onedotfinance.com
- **Password:** 12345678
- **Role:** Admin

> ⚠️ **Important:** Change default credentials in production!

## 🚀 Usage

### Starting the Application

#### Using Supervisor (Production)
```bash
# Start all services
sudo supervisorctl restart all

# Check status
sudo supervisorctl status

# View logs
tail -f /var/log/supervisor/backend.*.log
tail -f /var/log/supervisor/frontend.*.log
```

#### Manual Start (Development)
```bash
# Terminal 1 - Backend
cd backend
uvicorn server:app --host 0.0.0.0 --port 8001 --reload

# Terminal 2 - Frontend
cd frontend
npm start
```

### Accessing the Application
- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:8001
- **API Docs:** http://localhost:8001/docs (Swagger UI)

## 📚 API Documentation

### Key Endpoints

#### Authentication
- `POST /api/auth/login` - Login with email/password
- `POST /api/auth/verify-otp` - Verify OTP
- `POST /api/auth/reset-password` - Reset password

#### Clients
- `GET /api/clients` - List clients (with filters)
- `POST /api/clients` - Create client
- `PATCH /api/clients/{id}` - Update client
- `DELETE /api/clients/{id}` - Delete client
- `GET /api/clients/export` - Export to Excel
- `POST /api/clients/import` - Import from Excel

#### Contractors
- `GET /api/contractors` - List contractors (with filters)
- `POST /api/contractors` - Create contractor
- `PATCH /api/contractors/{id}` - Update contractor
- `DELETE /api/contractors/{id}` - Delete contractor

#### Employees
- `GET /api/employees` - List employees (with filters)
- `POST /api/employees` - Create employee
- `PATCH /api/employees/{id}` - Update employee
- `DELETE /api/employees/{id}` - Delete employee

#### Assets
- `GET /api/assets` - List assets (with filters)
- `POST /api/assets` - Create asset
- `PATCH /api/assets/{id}` - Update asset
- `DELETE /api/assets/{id}` - Delete asset

#### Dashboard
- `GET /api/dashboard/summary` - Get dashboard metrics

> 📖 **Full API Documentation:** Visit http://localhost:8001/docs after starting the backend

## 🏗 Project Structure

```
/app/
├── backend/
│   ├── server.py              # Main FastAPI application (1,650+ lines)
│   ├── requirements.txt       # Python dependencies
│   ├── .env                   # Environment variables
│   ├── templates/             # Word document templates
│   │   ├── ICA_Sample.docx
│   │   ├── NDA_Sample.docx
│   │   ├── Offer_Letter_Sample.docx
│   │   ├── SLA_PPC.docx
│   │   └── SLA_SEO.docx
│   └── excel_templates/       # Excel import samples
│       ├── assets_sample.xlsx
│       ├── clients_sample.xlsx
│       ├── contractors_sample.xlsx
│       └── employees_sample.xlsx
│
├── frontend/
│   ├── src/
│   │   ├── components/        # React components (15 components)
│   │   │   ├── Login.js
│   │   │   ├── Dashboard.js
│   │   │   ├── Reports.js (NEW)
│   │   │   ├── ClientDatabase.js
│   │   │   ├── ContractorDatabase.js
│   │   │   ├── EmployeeDatabase.js
│   │   │   ├── AssetTracker.js
│   │   │   └── ... (document generators, approval, etc.)
│   │   ├── App.js            # Main application with routing
│   │   └── index.js          # Entry point
│   ├── package.json          # Node.js dependencies
│   └── .env                  # Environment variables
│
├── README.md                  # This file
└── PROJECT_STRUCTURE.md       # Detailed documentation
```

## 📂 GitHub Integration

### Method 1: Using Emergent's Built-in Feature (Recommended)

#### Step 1: Connect GitHub Account
1. Click your **profile icon** at the top of Emergent
2. Click **"Connect GitHub"** button
3. Authorize Emergent to access your repositories

#### Step 2: Push to GitHub
1. Click **"Save to GitHub"** button in the chat interface
2. Select your branch (or create new branch)
3. Click **"PUSH TO GITHUB"**

> 💡 **Note:** GitHub integration requires a Standard Plan subscription

### Method 2: Manual Git Push (Alternative)

```bash
# Initialize git repository (if not already initialized)
git init

# Add all files
git add .

# Commit changes
git commit -m "Initial commit: Piperocket Finance Management Tool"

# Add remote repository
git remote add origin https://github.com/your-username/your-repo-name.git

# Push to GitHub
git push -u origin main
```

### Important Files to Include

All necessary files are already in the project:
- ✅ `README.md` - Complete documentation
- ✅ `PROJECT_STRUCTURE.md` - Detailed structure guide
- ✅ `backend/requirements.txt` - Python dependencies
- ✅ `frontend/package.json` - Node.js dependencies
- ✅ `.env` files - Environment configuration (add to .gitignore)
- ✅ All source code files

### .gitignore Recommendations

Create a `.gitignore` file with:

```
# Environment variables
.env
*.env

# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
venv/
env/

# Node.js
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Build outputs
/frontend/build
/frontend/dist

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Logs
*.log
logs/

# Database
*.db
*.sqlite
```

## 🔒 Security Features

- JWT token-based authentication
- Role-based access control (RBAC)
- Password hashing with bcrypt
- OTP verification for login
- Protected routes on frontend and backend
- CORS configuration
- Admin user delete protection

## 🎯 Departments Supported

1. **PPC** (Pay-Per-Click)
2. **SEO** (Search Engine Optimization)
3. **Content**
4. **Backlink**
5. **Business Development**
6. **Others**

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is proprietary software. All rights reserved.

## 👨‍💻 Author

**one.Finance**
- Website: www.onedotfinance.com
- Built with ❤️ using Emergent Platform

## 🐛 Bug Reports

If you discover any bugs, please create an issue on GitHub with:
- Detailed description
- Steps to reproduce
- Expected behavior
- Screenshots (if applicable)

## 📞 Support

For support, email support@onedotfinance.com

## 🙏 Acknowledgments

- FastAPI for the amazing backend framework
- React team for the powerful frontend library
- Shadcn for beautiful UI components
- MongoDB for flexible data storage
- Emergent platform for seamless deployment

---

**Made with ❤️ by one.Finance | Powered by Emergent Platform**


---

This repository was reorganized and packaged for GitHub upload.
See docs/SETUP_GUIDE.md for upload instructions.
