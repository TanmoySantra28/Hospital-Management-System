# Hospital Management System in Java with MySQL Database Integration

This is a console-based hospital management system implemented in Java. The system allows the management of patients, doctors, and appointments using a MySQL database for data storage.

## Features

- **Add a new patient**: Enter the patient's name, age, and gender to add them to the database.
- **Add a new doctor**: New Doctors can be added by admin in MySQL server.
- **List all patients**: Display all registered patients in a tabular format.
- **List all doctors**: View all doctors along with their specializations.
- **Book an appointment**: Schedule an appointment for a patient with a doctor on a specified date.
- **Check availability**: Ensure that doctors are available on the selected date.
- **Persistent storage**: Data is stored in a MySQL database (`hospital`) ensuring persistence across sessions.

## Requirements

- **Java Development Kit (JDK)**: Ensure that JDK is installed and properly set up on your system.
- **MySQL Database**: A MySQL server should be running and configured.
- **MySQL JDBC Driver**: Include the JDBC driver in your project.
- **Database Schema**: The following schema should be created in your MySQL server:

    ```sql
    CREATE DATABASE hospital;

    USE hospital;

    CREATE TABLE patients (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(50),
        age INT,
        gender VARCHAR(10)
    );

    CREATE TABLE doctors (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(50),
        specialization VARCHAR(50)
    );

    CREATE TABLE appointments (
        id INT AUTO_INCREMENT PRIMARY KEY,
        patient_id INT,
        doctor_id INT,
        appointment_date DATE,
        FOREIGN KEY (patient_id) REFERENCES patients(id),
        FOREIGN KEY (doctor_id) REFERENCES doctors(id)
    );
    ```

## Adding doctors in MySQL server

```sql
INSERT INTO doctors (name, specialization) VALUES
('Dr. Alice Smith', 'Cardiologist'),
('Dr. Bob Johnson', 'Dermatologist'),
('Dr. Carol Brown', 'Neurologist'),
('Dr. Daniel White', 'Pediatrician'),
('Dr. Emily Davis', 'Orthopedic Surgeon');
```

## Compilation

You can compile the program using the following command:

```bash
javac HospitalManagementSystem.java
```

## A menu will appear with the following options:

```bash
HOSPITAL MANAGEMENT SYSTEM 
1. Add Patient
2. View Patients
3. View Doctors
4. Book Appointment
5. Exit
Enter your choice:
```

## Example of Adding a Patient

Select the option (`1. Add Patient`).
Enter the patient's details when prompted:

```bash
Enter Patient Name: Arjun
Enter Patient Age: 27
Enter Patient Gender: Male
```
- Output:

```bash
Patient Added Successfully!!
```

## Example of Viewing Patients

Select the option (`2 View Patients`).
The system will display a list of all patients along with their age and gender in a tabular format:

```bash
Patients: 
+------------+--------------------+----------+------------+
| Patient Id | Name               | Age      | Gender     |
+------------+--------------------+----------+------------+
| 1          | Arjun              | 27       | Male       |
+------------+--------------------+----------+------------+
```

## Example of Viewing Doctors

Select the option (`3 View Doctors`).
The system will display a list of all doctors along with their specializations in a tabular format:

```bash
Doctors: 
+------------+--------------------+------------------+
| Doctor Id  | Name               | Specialization   |
+------------+--------------------+------------------+
| 1          | Alice Smith        | Cardiologist     |
+------------+--------------------+------------------+
| 2          | Bob Johnson        | Dermatologist    |
+------------+--------------------+------------------+
| 3          | Carol Brown        | Neurologist      |
+------------+--------------------+------------------+
| 4          | Daniel White       | Pediatrician     |
+------------+--------------------+------------------+
| 5          | Emily Davis        | Orthopedic       |
+------------+--------------------+------------------+
```

## Example of Booking an Appointment
Select the option (`4 Book Appointment`).
Enter the patient ID, doctor ID, and appointment date when prompted:

```bash
Enter Patient Id: 1
Enter Doctor Id: 2
Enter appointment date (YYYY-MM-DD): 2025-03-18
```

Output:

```bash
Appointment Booked!
```

If the doctor is unavailable, you'll receive:

```bash
Doctor not available on this date!!
```

##  File Storage

The program uses MySQL as the database backend. Ensure that the database (hospital) is created and accessible before running the program. Update the database credentials in the (`HospitalManagementSystem.java`) file:

```bash
private static final String url = "jdbc connection string";
private static final String username = "root";
private static final String password = "your_password";
```

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contributing

Feel free to fork this repository and submit pull requests to enhance functionality or fix issues.
