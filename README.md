🏦 Gestion Bancaire

💼 Desktop Banking Management System built with Java (Swing) & MySQL using MVC Architecture

<p align="center"> <img src="https://img.shields.io/badge/Java-17+-orange?style=for-the-badge&logo=java" /> <img src="https://img.shields.io/badge/MySQL-8.0+-blue?style=for-the-badge&logo=mysql" /> <img src="https://img.shields.io/badge/Architecture-MVC-green?style=for-the-badge" /> <img src="https://img.shields.io/badge/Status-Active-success?style=for-the-badge" /> </p>
📌 Overview

Gestion Bancaire is a full-featured desktop application that allows you to manage:

👥 Clients
💳 Bank Accounts
💸 Transactions

The application provides a secure, intuitive, and scalable system with persistent data storage using MySQL.

🚀 Features
🔐 Authentication

Secure login system
Default admin account
👥 Client Management

Add, update, delete clients
Search clients by name or email
Store contact information

💳 Account Management

Create current and savings accounts
View account balances
Link accounts to clients

💸 Transaction Management
Deposit money
Withdraw money (with balance validation)
Transfer between accounts
View transaction history

🧠 System Capabilities
Input validation
Clean and responsive UI (Swing)
MVC architecture
Database persistence (MySQL)

🛠️ Tech Stack

Layer	Technology
Language	Java 17
UI	Java Swing
Database	MySQL
Connector	MySQL Connector/J
Architecture	MVC (Model - View - Controller)

GestionBancaire/
│
└── src/main/java/com/eagle1st/gestionbancaire/
    ├── Main.java
    │
    ├── connection/
    │   ├── DatabaseConnection.java
    │   └── TestConnection.java
    │
    ├── dao/
    │   ├── ClientDAO.java
    │   ├── CompteDAO.java
    │   └── TransactionDAO.java
    │
    ├── model/
    │   ├── Client.java
    │   ├── Compte.java
    │   └── Transaction.java
    │
    └── view/
        ├── LoginWindow.java
        ├── MainWindow.java
        ├── ClientWindow.java
        ├── CompteWindow.java
        └── TransactionWindow.java
        
⚙️ Installation & Setup

✅ Prerequisites

Java JDK 17+
MySQL Server 8+
MySQL Connector/J (.jar)
📥 Clone Repository
git clone https://github.com/ATTARAYOUB/GestionBancaire.git
cd GestionBancaire
🗄️ Database Setup
CREATE DATABASE gestion_bancaire;
USE gestion_bancaire;

CREATE TABLE clients (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nom VARCHAR(100) NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  telephone VARCHAR(20),
  adresse TEXT
);

CREATE TABLE comptes (
  id INT PRIMARY KEY AUTO_INCREMENT,
  numero VARCHAR(20) UNIQUE NOT NULL,
  solde DECIMAL(15,2) DEFAULT 0.00,
  type ENUM('COURANT', 'EPARGNE') NOT NULL,
  client_id INT NOT NULL,
  FOREIGN KEY (client_id) REFERENCES clients(id) ON DELETE CASCADE
);

CREATE TABLE transactions (
  id INT PRIMARY KEY AUTO_INCREMENT,
  type ENUM('DEPOT', 'RETRAIT', 'VIREMENT') NOT NULL,
  montant DECIMAL(15,2) NOT NULL,
  date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  compte_id INT NOT NULL,
  compte_destinataire_id INT NULL,
  FOREIGN KEY (compte_id) REFERENCES comptes(id) ON DELETE CASCADE,
  FOREIGN KEY (compte_destinataire_id) REFERENCES comptes(id)
);

CREATE TABLE utilisateurs (
  id INT PRIMARY KEY AUTO_INCREMENT,
  username VARCHAR(50) UNIQUE NOT NULL,
  password VARCHAR(255) NOT NULL
);

INSERT INTO utilisateurs (username, password)
VALUES ('admin', 'admin123');
🔧 Configure Database Connection

Edit the file:

public class DatabaseConnection {
    private static final String URL = "jdbc:mysql://localhost:3306/gestion_bancaire";
    private static final String USER = "root";
    private static final String PASSWORD = "your_password";

    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(URL, USER, PASSWORD);
    }
}
▶️ Run the Project
javac src/main/java/com/eagle1st/gestionbancaire/Main.java
java src/main/java/com/eagle1st/gestionbancaire/Main

Or simply run it using your IDE:

IntelliJ IDEA
Eclipse
NetBeans
📖 Usage Guide
🔐 Login
Field	Value
Username	admin
Password	admin123
🏠 Main Dashboard

After login, you can access:

👥 Client Management
💳 Account Management
💸 Transaction Management
👥 Clients
Add new client
Update information
Delete client (with cascade delete)
Search clients
💳 Accounts
Create accounts (Current / Savings)
View balances
Link to clients
💸 Transactions
Deposit money
Withdraw money
Transfer between accounts
View history
🧩 Architecture (MVC)
VIEW (Swing UI)
   ↓
CONTROLLER (Main Logic)
   ↓
DAO (Database Access)
   ↓
DATABASE (MySQL)
🔮 Future Improvements
🔐 Password encryption (BCrypt)
📄 PDF bank statements
📊 Data visualization (charts)
📤 Export to Excel
🔔 Notifications system
👥 Multi-user roles (Admin/User)
💳 Overdraft management
💰 Interest calculation for savings
👨‍💻 Author

ATTAR AYOUB

GitHub: https://github.com/ATTARAYOUB
LinkedIn: https://www.linkedin.com/in/itsayoubattar
📄 License

This project is for educational purposes only.

🤝 Contributing

Contributions are welcome!

# Fork the project
# Create your feature branch
git checkout -b feature/AmazingFeature

# Commit your changes
git commit -m "Add AmazingFeature"

# Push to GitHub
git push origin feature/AmazingFeature

# Open a Pull Request
⭐ Support

If you like this project, please ⭐ the repository on GitHub!

<p align="center"> Made with ☕ by <b>ATTAR AYOUB</b> </p>
