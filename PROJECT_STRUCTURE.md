# Piperocket Finance Management Tool - Complete Project Structure

## 📁 Directory Structure

```
/app/
├── backend/                          # FastAPI Backend
│   ├── server.py                    # Main application file (1,650+ lines)
│   ├── requirements.txt             # Python dependencies
│   ├── .env                         # Backend environment variables
│   ├── templates/                   # Word document templates
│   │   ├── ICA_Sample.docx
│   │   ├── NDA_Sample.docx
│   │   ├── Offer_Letter_Sample.docx
│   │   ├── SLA_PPC.docx
│   │   └── SLA_SEO.docx
│   └── excel_templates/             # Excel import templates
│       ├── assets_sample.xlsx
│       ├── clients_sample.xlsx
│       ├── contractors_sample.xlsx
│       └── employees_sample.xlsx
│
├── frontend/                         # React Frontend
│   ├── package.json                 # Node.js dependencies
│   ├── .env                         # Frontend environment variables
│   ├── tailwind.config.js           # Tailwind CSS configuration
│   ├── postcss.config.js            # PostCSS configuration
│   ├── public/                      # Static assets
│   └── src/
│       ├── index.js                 # Entry point
│       ├── App.js                   # Main app with routing
│       ├── App.css                  # Global styles
│       ├── index.css                # Global styles
│       ├── components/              # React components
│       │   ├── Login.js             # Authentication
│       │   ├── Layout.js            # App layout with sidebar
│       │   ├── Dashboard.js         # Main dashboard with metrics
│       │   ├── Users.js             # User management
│       │   ├── ClientDatabase.js    # Client CRUD operations
│       │   ├── ContractorDatabase.js # Contractor CRUD operations
│       │   ├── EmployeeDatabase.js  # Employee CRUD operations
│       │   ├── AssetTracker.js      # Asset management
│       │   ├── SLAGenerator.js      # SLA document generation
│       │   ├── NDAGenerator.js      # NDA document generation
│       │   ├── ICAGenerator.js      # ICA document generation
│       │   ├── OfferLetterGenerator.js # Offer letter generation
│       │   ├── Approval.js          # Approval workflow
│       │   ├── Reports.js           # Financial reports (NEW)
│       │   ├── FilterSort.js        # Filter/sort component
│       │   └── ui/                  # Shadcn UI components
│       ├── hooks/
│       │   └── use-toast.js         # Toast notification hook
│       └── lib/
│           └── utils.js             # Utility functions
│
├── tests/                           # Test directory
├── test_result.md                   # Testing documentation
└── README.md                        # Project documentation
```

## 🔑 Key Files

### Backend (server.py)
**Location:** `/app/backend/server.py`
**Size:** 1,650+ lines
**Key Features:**
- Authentication (JWT, OTP)
- User Management (CRUD, roles)
- Client Management (CRUD, SLA/NDA generation)
- Contractor Management (CRUD, ICA generation)
- Employee Management (CRUD, Offer Letter generation)
- Asset Tracker (CRUD, warranty tracking)
- Dashboard Analytics
- Approval Workflow
- Bulk Import/Export (Excel)
- Document Generation (Word templates)

### Frontend Components

#### 1. **App.js** (`/app/frontend/src/App.js`)
- Main application component
- Routing configuration
- API setup with Axios
- Authentication context

#### 2. **Dashboard.js** (`/app/frontend/src/components/Dashboard.js`)
- Alerts: Expiring agreements, Expired agreements, Birthdays
- Revenue metrics (4 departments: PPC, SEO, Content, Backlink)
- Employee metrics by department
- Contractor metrics by department

#### 3. **Reports.js** (`/app/frontend/src/components/Reports.js`) - NEW
- Department P&L (with resource & client counts)
- Client-level Profitability (with P&L %, department filter)
- Resource Utilization (with department column & filter)
- Excel export functionality

#### 4. **Database Components**
- **ClientDatabase.js**: Client CRUD with filters, totals, sorting
- **ContractorDatabase.js**: Contractor CRUD with Gender, Projects, filters
- **EmployeeDatabase.js**: Employee CRUD with Gender, Projects, filters
- **AssetTracker.js**: Asset management with warranty tracking

#### 5. **Document Generators**
- **SLAGenerator.js**: Service Level Agreement
- **NDAGenerator.js**: Non-Disclosure Agreement
- **ICAGenerator.js**: Independent Contractor Agreement
- **OfferLetterGenerator.js**: Employee Offer Letter

## 🔐 Environment Variables

### Backend (.env)
```env
MONGO_URL=mongodb://localhost:27017
DB_NAME=your_db_name
JWT_SECRET=your_jwt_secret
CORS_ORIGINS=*
```

### Frontend (.env)
```env
REACT_APP_BACKEND_URL=your_backend_url
```

## 📦 Dependencies

### Backend (requirements.txt)
```
fastapi
uvicorn
motor
pydantic
pydantic-settings
python-jose[cryptography]
passlib[bcrypt]
python-multipart
pandas
openpyxl
python-docx
docx-mailmerge
```

### Frontend (package.json)
```json
{
  "dependencies": {
    "react": "^18.x",
    "react-dom": "^18.x",
    "react-router-dom": "^6.x",
    "axios": "^1.x",
    "lucide-react": "latest",
    "sonner": "latest",
    "tailwindcss": "^3.x"
  }
}
```

## 🎯 Key Features

### 1. Authentication & User Management
- Admin/Director/Staff roles
- Email OTP verification
- Password reset
- JWT token-based authentication
- User CRUD with delete functionality

### 2. Client Management
- CRUD operations
- Service types: PPC, SEO, Content, Backlink
- SLA & NDA document generation
- Agreement status tracking
- Department & status filters
- Bulk import/export

### 3. Contractor Management
- CRUD operations
- Gender field (Male/Female/Other)
- Projects field (multi-select)
- ICA document generation
- Agreement status tracking
- Department filter (includes Backlink)
- Bulk import/export

### 4. Employee Management
- CRUD operations
- Gender field
- Projects field (multi-select)
- Offer Letter generation with salary calculations
- Department filter (includes Backlink)
- Bulk import/export

### 5. Asset Tracker
- CRUD operations
- Warranty status calculation
- Department & warranty filter
- Total asset value tracking
- Bulk import/export

### 6. Reports Module (NEW)
- **Department P&L**: Revenue, costs, profit % with client/resource counts
- **Client Profitability**: Resource assignments, cost splitting, P&L %
- **Resource Utilization**: Per-client cost, project counts, department filter

### 7. Dashboard Analytics
- Expiring agreements (30 days)
- Expired agreements list
- Upcoming birthdays (15 days)
- Revenue by department (4 depts)
- Employee cost by department (6 depts)
- Contractor cost by department (6 depts)

### 8. Approval Workflow
- Staff request submission
- Director approval/rejection/hold
- Admin reassignment
- Audit logs
- Monthly reset functionality

## 🎨 UI Features

### Design System
- Tailwind CSS for styling
- Shadcn UI components
- Responsive design
- Status badges with color coding
- Toast notifications

### Table Enhancements
- Department & status filters
- Sort functionality
- Total amount rows
- Status-based sorting (Active first)
- Pagination-ready structure

## 🚀 Deployment Configuration

### Ports
- Backend: 8001
- Frontend: 3000

### Database
- MongoDB (connection via env variable)
- Collections: users, clients, contractors, employees, assets

### Services (Supervisor)
```
sudo supervisorctl restart backend
sudo supervisorctl restart frontend
sudo supervisorctl restart all
```

## 📊 Database Schema

### Collections
1. **users**: User accounts with roles
2. **clients**: Client records with agreements
3. **contractors**: Contractor records with ICAs
4. **employees**: Employee records with offer letters
5. **assets**: Asset inventory with warranty tracking

### Key Fields
- **Departments**: PPC, SEO, Content, Backlink, Business Development, Others
- **Status Types**: Active/Churned (clients), Active/Terminated (contractors/employees)
- **Agreement Status**: Live/Expired
- **Projects**: Array of client IDs for resource assignment

## 🔗 External Integrations
- Zoho Payroll (external link)
- Looker Studio (external link)
- Document templates (Word .docx)
- Excel import/export (.xlsx)

## ✅ Production Ready
- ✅ No hardcoded URLs
- ✅ Environment variables configured
- ✅ MongoDB properly integrated
- ✅ CORS configured
- ✅ All features tested
- ✅ Deployment ready

## 📝 Notes
- Admin credentials: Vishnu@onedotfinance.com / 12345678
- OTP displayed in login response for testing
- All APIs require authentication except login/OTP
- Document templates stored in backend/templates/
- Excel samples stored in backend/excel_templates/
