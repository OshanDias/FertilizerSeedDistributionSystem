# 🌱 Fertilizer & Seed Distribution System

A comprehensive Java Swing desktop application for managing agricultural supply chain including fertilizers, seeds, pesticides, retail customers, and sales orders with discount management and loyalty tracking.

![Java](https://img.shields.io/badge/Java-17-orange?style=flat&logo=java)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?style=flat&logo=mysql)
![Swing](https://img.shields.io/badge/Swing-GUI-green?style=flat)
![JasperReports](https://img.shields.io/badge/JasperReports-6.20.0-red?style=flat)

## 📋 Table of Contents
- [Features](#features)
- [Screenshots](#screenshots)
- [Technology Stack](#technology-stack)
- [Database Schema](#database-schema)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Design Patterns](#design-patterns)
- [License](#license)

## ✨ Features

### 🔐 Authentication System
- Secure login with default credentials
- Session management

### 📦 Fertilizer Supplier Management
- Add, update, delete, and search suppliers
- Business type classification (Manufacturer, Distributor, Importer, Local Producer)
- License number tracking
- Supplier ratings (0.0 - 5.0)
- Email and phone validation

### 🌿 Product Management (Multi-Type)
- **Product Types:** Fertilizer, Seed, Pesticide, Growth Supplement
- **Categories:** Organic, Chemical, Hybrid, Natural, Synthetic
- Crop type suitability tracking
- Unit type management (KG, Liter, Pack, Bag)
- Real-time stock tracking with reorder levels
- Expiry date monitoring
- Manufacturer information

### 👥 Retail Customer Management
- **Customer Types:** Farmer, Retailer, Wholesaler, Individual
- Farm size tracking for farmers
- Business name for retailers/wholesalers
- Loyalty points system
- Total purchase history
- NIC validation (Sri Lankan format)

### 🛒 Sales Order Management (Main Transaction)
- Complete order processing workflow
- Automatic subtotal calculation
- **Discount Management:** Percentage-based with amount calculation
- Stock reduction on order creation
- Customer purchase tracking and loyalty points
- **Payment Methods:** Cash, Card, Bank Transfer, Credit
- **Payment Status:** PENDING, PAID, PARTIAL, REFUNDED
- **Delivery Status:** PROCESSING, READY, DISPATCHED, DELIVERED, CANCELLED
- Delivery address management
- Order filtering by status

### 📊 Sales Analytics & Reports
- Sales Analysis by Product Type (3-table JOIN)
- Revenue analysis by category
- Top supplier identification
- Grand total calculations with grouping
- JasperReports PDF export

## 🖼️ Screenshots

### Dashboard - Grid Card Layout
```
┌───────────────────────────────────────────────────┐
│  🌱 FERTILIZER & SEED DISTRIBUTION - DASHBOARD    │
├───────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────┐     │
│  │  Welcome to Agricultural Supply Mgmt     │     │
│  └─────────────────────────────────────────┘     │
│                                                   │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐   │
│  │📦      │ │🌱      │ │👥      │ │🛒      │   │
│  │SUPPLIER│ │PRODUCT │ │CUSTOMER│ │SALES   │   │
│  └────────┘ └────────┘ └────────┘ └────────┘   │
│                                                   │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐   │
│  │📊      │ │📈      │ │⚙️      │ │🔄      │   │
│  │REPORTS │ │ANALYTIC│ │SETTINGS│ │REFRESH │   │
│  └────────┘ └────────┘ └────────┘ └────────┘   │
│                                                   │
│  ┌─────────────────────────────────────────┐     │
│  │  System Statistics (Live Data)          │     │
│  └─────────────────────────────────────────┘     │
└───────────────────────────────────────────────────┘
```

### CRUD Forms - 3-Column Horizontal Layout
```
┌───────────────────────────────────────────────────┐
│  ← BACK         SUPPLIER MANAGEMENT               │
├───────────────────────────────────────────────────┤
│  ┌──────┐  ┌────────┐  ┌─────────────────────┐  │
│  │      │  │        │  │ 🔍 Search: [____]   │  │
│  │Input │  │Actions │  │ ┌─────────────────┐ │  │
│  │Fields│  │        │  │ │  Data Table      │ │  │
│  │      │  │ ➕ ADD  │  │ │  (Full Width)    │ │  │
│  │(30%) │  │ ✏️ UPD  │  │ │                  │ │  │
│  │      │  │ 🗑️ DEL  │  │ │  (50%)           │ │  │
│  │      │  │ 🔄 CLR  │  │ └─────────────────┘ │  │
│  │      │  │        │  │                      │  │
│  │      │  │ Info   │  │                      │  │
│  │      │  │ Panel  │  │                      │  │
│  └──────┘  └────────┘  └─────────────────────┘  │
│  (Left)     (Middle)           (Right)            │
└───────────────────────────────────────────────────┘
```

## 🛠️ Technology Stack

### Backend
- **Language:** Java 17
- **Database:** MySQL 8.0
- **JDBC:** MySQL Connector/J 9.6.0

### Frontend
- **GUI Framework:** Java Swing
- **Look and Feel:** System Native

### Reporting
- **JasperReports:** 6.20.0
- **iText:** 2.1.7

### Libraries
- Apache Commons Collections 4.4
- Apache Commons Logging 1.2
- Apache Commons BeanUtils 1.9.4
- Apache Commons Digester 2.1

## 🗄️ Database Schema

### Tables
1. **fertilizer_suppliers** (12 fields)
   - Supplier information with business type
   - License number and rating system

2. **products** (15 fields)
   - Multi-type product catalog (Fertilizer, Seed, Pesticide, Growth Supplement)
   - Stock tracking with reorder levels
   - Expiry date monitoring
   - FK: supplier_id → fertilizer_suppliers

3. **retail_customers** (13 fields)
   - Multi-type customer management
   - Loyalty points and purchase tracking
   - Farm size for farmers, business name for retailers

4. **sales_orders** (18 fields) - **Main Transaction Table**
   - Complete sales order processing
   - Discount management (percentage & amount)
   - Multi-status tracking (payment & delivery)
   - FK: customer_id → retail_customers
   - FK: product_id → products

### Relationships
```
fertilizer_suppliers (1) ──→ (N) products
retail_customers (1) ──→ (N) sales_orders
products (1) ──→ (N) sales_orders
```

## 📥 Installation

### Prerequisites
- Java Development Kit (JDK) 17 or higher
- MySQL Server 8.0 or higher
- NetBeans IDE (recommended) or any Java IDE

### Steps

1. **Clone the repository**
```bash
   git clone https://github.com/yourusername/fertilizer-seed-distribution.git
   cd fertilizer-seed-distribution
```

2. **Set up the database**
```sql
   -- Run the SQL script in MySQL Workbench
   source database/fertilizer_seed_distribution.sql
```

3. **Configure database connection**
```java
   // Edit: src/com/fertilizersystem/dao/DatabaseConnection.java
   private static final String USERNAME = "your_mysql_username";
   private static final String PASSWORD = "your_mysql_password";
```

4. **Add required libraries**
   - Place JAR files in the `lib/` folder
   - Add to project build path:
     - mysql-connector-j-9.6.0.jar
     - jasperreports-6.20.0.jar
     - commons-collections4-4.4.jar
     - commons-logging-1.2.jar
     - commons-beanutils-1.9.4.jar
     - commons-digester-2.1.jar
     - itext-2.1.7.jar

5. **Build and run**
```bash
   # Using NetBeans: Clean and Build (Shift+F11)
   # Run: F6
   
   # Or using command line:
   javac -cp "lib/*" src/com/fertilizersystem/Main.java
   java -cp "lib/*:src" com.fertilizersystem.Main
```

## 🚀 Usage

### Login
- **Username:** `admin`
- **Password:** `admin123`

### Main Workflow

1. **Add Suppliers**
   - Navigate to Suppliers card
   - Fill in company and business details
   - Set license number and rating

2. **Manage Products**
   - Add fertilizers, seeds, pesticides, or supplements
   - Link to suppliers
   - Set stock levels, reorder points, and expiry dates
   - Specify crop type suitability

3. **Register Customers**
   - Select customer type (Farmer/Retailer/Wholesaler/Individual)
   - Enter details based on type
   - System tracks loyalty points and purchases

4. **Process Sales Orders**
   - Select customer and product
   - Enter quantity
   - System auto-fills price per unit
   - Apply discount percentage
   - Click CALCULATE to compute totals
   - Select payment method and statuses
   - CREATE ORDER
   - Stock automatically reduced
   - Customer total purchases updated
   - Loyalty points added

5. **Generate Reports**
   - View sales analysis by product type
   - Analyze top suppliers by category
   - Export to PDF

## 📁 Project Structure
```
FertilizerSeedDistributionSystem/
│
├── src/
│   └── com/
│       └── fertilizersystem/
│           ├── Main.java
│           ├── model/
│           │   ├── FertilizerSupplier.java
│           │   ├── Product.java
│           │   ├── RetailCustomer.java
│           │   └── SalesOrder.java
│           ├── dao/
│           │   ├── DatabaseConnection.java
│           │   ├── FertilizerSupplierDAO.java
│           │   ├── ProductDAO.java
│           │   ├── RetailCustomerDAO.java
│           │   └── SalesOrderDAO.java
│           ├── controller/
│           │   └── ReportController.java
│           ├── view/
│           │   ├── LoginForm.java
│           │   ├── DashboardForm.java
│           │   ├── SupplierForm.java
│           │   ├── ProductForm.java
│           │   ├── CustomerForm.java
│           │   └── SalesForm.java
│           └── util/
│               └── Validator.java
│
├── lib/
│   ├── mysql-connector-j-9.6.0.jar
│   ├── jasperreports-6.20.0.jar
│   └── [other libraries]
│
├── database/
│   └── fertilizer_seed_distribution.sql
│
├── dist/
│   └── FertilizerSeedDistributionSystem.jar
│
└── README.md
```

## 🎨 Design Patterns

### 1. Singleton Pattern
- **DatabaseConnection:** Ensures single database connection instance

### 2. DAO Pattern
- Separate DAO for each entity
- Encapsulates database operations
- Clean separation of concerns

### 3. MVC Architecture
- **Model:** POJO classes (FertilizerSupplier, Product, etc.)
- **View:** Swing UI Forms
- **Controller:** ReportController, business logic

### 4. Utility Pattern
- **Validator:** Centralized input validation
- Reusable validation methods

## 🎨 UI Theme

**Ocean Blue/Teal Professional Theme**
- Primary Ocean Blue: RGB(41, 128, 185)
- Secondary Teal: RGB(26, 188, 156)
- Accent Navy: RGB(44, 62, 80)
- Success Sea Green: RGB(22, 160, 133)
- Background Light Gray-Blue: RGB(236, 240, 241)

**Layout Style**
- Dashboard: Grid Card Layout (4x2 cards)
- CRUD Forms: 3-Column Horizontal (Left 30% + Middle 20% + Right 50%)
- Form Size: 1500x800

## 🔐 Security Features

- Password-protected login
- Input validation on all forms
- SQL injection prevention (PreparedStatements)
- NIC format validation (Sri Lankan)
- Email and phone number validation
- Discount percentage validation (0-100%)

## 📝 Validation Rules

- **Email:** Standard email format
- **Phone:** Sri Lankan format (0xxxxxxxxx)
- **NIC:** Old (9V/X) or New (12 digits) format
- **Rating:** 0.0 to 5.0
- **Stock:** Non-negative integers
- **Prices:** Positive decimals
- **Discount:** 0.0 to 100.0 percent
- **Dates:** YYYY-MM-DD format

## 🔄 Sales Order Calculation
```
Subtotal = Quantity × Price per Unit
Discount Amount = Subtotal × (Discount % / 100)
Total Amount = Subtotal - Discount Amount
```

## 🎁 Loyalty Points System

- Points earned based on total purchases
- Automatically tracked per customer
- Viewable in customer records

## 🐛 Known Issues

- None reported

## 🔮 Future Enhancements

- [ ] User role management (Admin, Sales, Manager)
- [ ] Advanced analytics dashboard with charts
- [ ] Email notifications for low stock and expiring products
- [ ] SMS notifications for order status
- [ ] Backup and restore functionality
- [ ] Multi-language support (Sinhala, Tamil, English)
- [ ] Export to Excel
- [ ] Barcode/QR code integration
- [ ] Mobile app integration
- [ ] Online payment gateway
- [ ] Customer portal

## 👥 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



## 🙏 Acknowledgments

- National Institute of Business Management (NIBM) - Kandy Innovation Centre
- Cardiff Metropolitan University (ICBT Campus)
- Java Swing Documentation
- JasperReports Community
- MySQL Documentation
- Agricultural industry professionals for requirements gathering

## 📞 Support

For support, email Kawshika4114@gmail.com or open an issue in the GitHub repository.

---

⭐ **Star this repository if you find it helpful!**

**Built with ❤️ for farmers, retailers, and agricultural suppliers**

