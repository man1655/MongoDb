
# 🏢 HR Management System

![Node.js](https://img.shields.io/badge/Node.js-v18-green?style=for-the-badge&logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-v6.0-green?style=for-the-badge&logo=mongodb)
![Express.js](https://img.shields.io/badge/Express.js-4.x-lightgrey?style=for-the-badge&logo=express)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

A comprehensive Human Resources Management System built with **Node.js** and **MongoDB** for managing employee data, tracking skills, promotions, salary changes, and generating advanced business analytics reports.

---

## 📋 Table of Contents
- [✨ Features](#-features)
- [🛠️ Technologies](#️-technologies)
- [🚀 Quick Start](#-quick-start)
- [🗄️ Database Schema](#️-database-schema)
- [📊 Implemented Reports](#-implemented-reports)
- [🔗 API Endpoints](#-api-endpoints)
- [📈 Sample Queries](#-sample-queries)
- [📁 Project Structure](#-project-structure)
- [📄 License](#-license)

---

## ✨ Features

### Core HR Management
- ✅ Employee CRUD operations with comprehensive profiles
- ✅ Department management with budget tracking
- ✅ Skills inventory and tracking system
- ✅ Salary history and promotion tracking
- ✅ Project and resource allocation management

### Advanced Analytics & Reporting
- 📅 **Monthly HR Reports** - New hires, departures, salary changes, department transfers
- 🎯 **Skills Inventory** - Most common skills, rare skills, department skill gaps
- 💰 **Salary Analysis** - Bands, bonus eligibility, promotion recommendations
- 📊 **Department Performance** - Budget utilization, productivity metrics
- ⚠️ **Retention Risk** - Identify employees at risk of leaving
- 📈 **Career Progression** - Promotion patterns and career path analysis

### MongoDB Aggregation Features
- Complex aggregation pipelines for business intelligence
- Real-time analytics and reporting
- Data visualization-ready JSON outputs
- Performance-optimized queries

---

## 🛠️ Technologies

| Technology | Purpose |
|------------|---------|
| **Node.js** | Backend runtime environment |
| **Express.js** | Web application framework |
| **MongoDB** | NoSQL database |
| **Mongoose** | MongoDB object modeling |
| **dotenv** | Environment configuration |
| **Nodemon** | Development server hot-reload |
| **Git/GitHub** | Version control |

---

## 🚀 Quick Start

### Prerequisites
- Node.js v18 or higher
- MongoDB (local or Atlas cluster)
- npm or yarn

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/man1655/MongoDb.git
cd MongoDb
```

2. **Install dependencies**
```bash
npm install
```

3. **Configure environment variables**
Create a `.env` file in the root directory:
```env
MONGO_URI=mongodb://localhost:27017/hr-management
PORT=5000
NODE_ENV=development
```

4. **Start the server**
```bash
# Development (with hot reload)
npm run dev

# Production
npm start
```

5. **Verify installation**
Visit `http://localhost:5000` or test with:
```bash
curl http://localhost:5000/employees
```

---

## 🗄️ Database Schema

### Collections Overview

| Collection | Description | Key Fields |
|------------|-------------|------------|
| **employees** | Employee master records | `name`, `position`, `salary`, `hire_date`, `department_id` |
| **departments** | Department information | `name`, `budget`, `manager_id` |
| **employee_skills** | Employee skills mapping | `employee_id`, `skill`, `proficiency` |
| **employee_salary_history** | Salary change tracking | `employee_id`, `salary`, `date`, `reason` |
| **employee_department_history** | Department transfer history | `employee_id`, `department_id`, `start_date` |
| **employee_promotion_history** | Promotion tracking | `employee_id`, `position`, `date`, `previous_position` |
| **projects** | Project management | `name`, `department_id`, `budget`, `status` |
| **project_assignments** | Resource allocation | `project_id`, `employee_id`, `role`, `hours` |

---

## 📊 Implemented Reports

### 1. Monthly HR Report
**Endpoint:** `GET /reports/monthly-hr?month=2024-01`
```json
{
  "month": "2024-01",
  "new_hires": 15,
  "departures": 5,
  "salary_changes": 42,
  "department_transfers": 8,
  "summary": "Overall positive growth with moderate turnover"
}
```

### 2. Skills Inventory Report
**Endpoint:** `GET /reports/skills-inventory`
```json
{
  "most_common_skills": [
    {"skill": "JavaScript", "count": 85},
    {"skill": "Project Management", "count": 72}
  ],
  "rare_skills": [
    {"skill": "Machine Learning", "count": 3},
    {"skill": "Blockchain", "count": 2}
  ],
  "skill_gaps_by_department": {
    "Engineering": ["DevOps", "Security"],
    "Marketing": ["Data Analysis", "SEO"]
  }
}
```

### 3. Salary Analysis Report
**Endpoint:** `GET /reports/salary-analysis`
```json
{
  "salary_bands": {
    "Junior": {"min": 40000, "max": 65000, "avg": 52000},
    "Mid-Level": {"min": 65000, "max": 95000, "avg": 78000}
  },
  "bonus_eligible_employees": 45,
  "promotion_recommendations": [
    {
      "employee_id": "EMP00123",
      "name": "John Doe",
      "current_position": "Software Engineer II",
      "recommended_position": "Senior Software Engineer",
      "reason": "Exceeds performance metrics for 3 consecutive quarters"
    }
  ]
}
```

### 4. Department Performance Report
**Endpoint:** `GET /reports/department-performance`
```json
{
  "departments": [
    {
      "name": "Engineering",
      "budget_utilization": "78%",
      "avg_performance_score": 4.2,
      "employee_count": 42,
      "attrition_rate": "8%"
    }
  ],
  "summary": "Engineering leads in performance; Marketing needs budget review"
}
```

### 5. Retention Risk Report
**Endpoint:** `GET /reports/retention-risk`
```json
{
  "high_risk": [
    {
      "employee_id": "EMP00456",
      "name": "Jane Smith",
      "risk_score": 85,
      "factors": ["No promotion in 3 years", "Salary below market average"]
    }
  ],
  "medium_risk": 12,
  "low_risk": 89
}
```

---

## 🔗 API Endpoints

### Employees
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/employees` | Get all employees | No |
| GET | `/employees/:id` | Get specific employee | No |
| POST | `/employees` | Create new employee | No |
| PUT | `/employees/:id` | Update employee | No |
| DELETE | `/employees/:id` | Delete employee | No |

### Departments
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/departments` | List all departments |
| POST | `/departments` | Create department |
| GET | `/departments/:id/employees` | Get department employees |

### Skills
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/skills` | List all skills |
| POST | `/skills` | Add skill to employee |
| GET | `/employees/:id/skills` | Get employee skills |

### Projects
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/projects` | List all projects |
| POST | `/projects` | Create project |
| POST | `/project-assignments` | Assign employee to project |

### Reports
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/reports/monthly-hr` | Monthly HR report |
| GET | `/reports/skills-inventory` | Skills analysis |
| GET | `/reports/salary-analysis` | Salary insights |
| GET | `/reports/department-performance` | Department metrics |
| GET | `/reports/retention-risk` | Retention analysis |

---

## 📈 Sample Queries

### 1. Find Employees Eligible for Promotion
```javascript
db.employees.aggregate([
  {
    $match: {
      performance_score: { $gte: 4.0 },
      hire_date: { $lte: new Date(Date.now() - 2 * 365 * 24 * 60 * 60 * 1000) }
    }
  },
  {
    $project: {
      name: 1,
      position: 1,
      performance_score: 1,
      years_with_company: {
        $divide: [
          { $subtract: [new Date(), "$hire_date"] },
          365 * 24 * 60 * 60 * 1000
        ]
      }
    }
  }
])
```

### 2. Department Budget Utilization
```javascript
db.departments.aggregate([
  {
    $lookup: {
      from: "employees",
      localField: "_id",
      foreignField: "department_id",
      as: "department_employees"
    }
  },
  {
    $project: {
      name: 1,
      budget: 1,
      total_salary: {
        $sum: "$department_employees.salary"
      },
      utilization_percentage: {
        $multiply: [
          {
            $divide: [
              { $sum: "$department_employees.salary" },
              "$budget"
            ]
          },
          100
        ]
      }
    }
  }
])
```

### 3. Identify Skill Gaps
```javascript
db.employee_skills.aggregate([
  {
    $group: {
      _id: "$skill",
      count: { $sum: 1 },
      employees: { $push: "$employee_id" }
    }
  },
  {
    $match: {
      count: { $lt: 5 }
    }
  },
  {
    $sort: { count: 1 }
  }
])
```

---

## 📁 Project Structure

```
MongoDb/
├── src/
│   ├── models/              # MongoDB schemas
│   │   ├── Employee.js
│   │   ├── Department.js
│   │   ├── Skill.js
│   │   └── ...
│   ├── controllers/         # Business logic
│   │   ├── employeeController.js
│   │   ├── departmentController.js
│   │   └── reportController.js
│   ├── routes/              # API routes
│   │   ├── employeeRoutes.js
│   │   ├── departmentRoutes.js
│   │   └── reportRoutes.js
│   ├── utils/               # Helper functions
│   │   └── aggregationPipelines.js
│   └── app.js              # Express app configuration
├── .env                    # Environment variables
├── .gitignore             # Git ignore file
├── package.json           # Dependencies and scripts
├── README.md              # This file
└── server.js              # Application entry point
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📞 Support

For support, email [your-email@example.com] or open an issue in the GitHub repository.

---

**⭐ Star this repo if you found it useful!**

---
