# MySQL---Warm-Up-2025-
# 📊 MySQL Warm-Up Project 2025

## 📌 Project Overview
This project is a **MySQL database** designed to manage and track data for the **Montreal Youth Volleyball Club (MYVC)**. It stores information about **club members, personnel, payments, locations, and family members.**

## 🏦 Database Schema
The database consists of the following tables:

1. **`members`** - Stores information about club members (name, age, status, team, location).
2. **`personnel`** - Stores personnel details (roles, location, contact info).
3. **`mandate_personnel`** - Tracks personnel assignments at different locations.
4. **`payments`** - Manages membership fees and donations.
5. **`family_member`** - Tracks family members associated with club members.
6. **`location`** - Stores details about club locations (headquarters or branches).

### 🔗 **Table Relationships**
- **Each `member` belongs to one `location`.**
- **Each `personnel` is assigned to one `location` at a time.**
- **Each `mandate_personnel` entry tracks personnel’s working period at a location.**
- **Each `payment` is linked to a `member`.**
- **Each `family_member` can be associated with multiple `members`.**

---

## 🛠️ How to Set Up the Database

### **1️⃣ Clone the Repository**
Run the following command in your terminal:
```sh
git clone https://github.com/Paciflow/MySQL-WarmUp-Project-2025.git
cd MySQL-WarmUp-Project-2025/warm_project_dump
```

### **2️⃣ Import the Database**
#### **Using MySQL CLI**
Run:
```sh
mysql -u root -p warm_project < warm_project_location.sql
mysql -u root -p warm_project < warm_project_members.sql
mysql -u root -p warm_project < warm_project_personnel.sql
mysql -u root -p warm_project < warm_project_mandate_personnel.sql
mysql -u root -p warm_project < warm_project_payments.sql
mysql -u root -p warm_project < warm_project_family_member.sql
```
🔹 **This will recreate all tables with data.**

#### **Using MySQL Workbench**
1. Open **MySQL Workbench**.
2. **Go to "Server" → "Data Import"**.
3. **Select "Import from Dump Project Folder"** and choose `warm_project_dump/`.
4. **Click "Start Import"**.

---

## 🔍 How to Use the Database (Common Queries)

### **📉 1️⃣ Get All Active Members**
```sql
SELECT * FROM members WHERE status = 'Active';
```

### **📉 2️⃣ Get All Payments for a Specific Member**
```sql
SELECT payment_date, amount, payment_type
FROM payments
WHERE member_ID = 1
ORDER BY payment_date ASC;
```

### **📉 3️⃣ Get Total Membership Fees & Donations for 2024**
```sql
SELECT
    SUM(CASE WHEN payment_type = 'Membership Fee' THEN amount ELSE 0 END) AS Total_Fees,
    SUM(CASE WHEN payment_type = 'Donation' THEN amount ELSE 0 END) AS Total_Donations
FROM payments
WHERE YEAR(payment_date) = 2024;
```

### **📉 4️⃣ Find Locations with No Active Members**
```sql
SELECT l.location_name
FROM location l
LEFT JOIN members m ON l.location_name = m.location_name
WHERE m.status IS NULL;
```

---

## Contributor
- **Pacifique Uwamukiza** – Developer


📧 Contact: pacifique@example.com

---

