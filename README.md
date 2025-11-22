# Employee Management System

A desktop-based Employee Management System built with Java Swing and MySQL. This application provides a user-friendly interface for managing employee information, including adding, viewing, updating, and removing employee records.

## Features

- **Splash Screen**: Animated welcome screen with blinking heading
- **User Authentication**: Secure login system with username and password validation
- **Add Employee**: Add new employees with comprehensive details including:
  - Personal information (Name, Father's Name, Date of Birth)
  - Contact details (Address, Phone, Email)
  - Professional information (Salary, Designation, Education)
  - Identification (NID Number)
  - Auto-generated Employee ID
- **View Employees**: Display all employee records in a table format
- **Update Employee**: Modify existing employee information
- **Remove Employee**: Delete employee records from the system

## Technologies Used

- **Java 17**: Core programming language
- **Java Swing**: GUI framework for desktop application
- **MySQL**: Database management system
- **JDBC**: Database connectivity
- **Apache Ant**: Build automation tool

## External Libraries

- `mysql-connector-java-8.0.28.jar`: MySQL JDBC driver
- `jcalendar-tz-1.3.3-4.jar`: Date picker component
- `rs2xml.jar`: ResultSet to XML converter for table display

## Prerequisites

Before running this application, ensure you have the following installed:

1. **Java Development Kit (JDK) 17** or higher
   - Download from [Oracle](https://www.oracle.com/java/technologies/downloads/) or [OpenJDK](https://openjdk.org/)
   - Verify installation: `java -version`

2. **MySQL Server**
   - Download from [MySQL Official Website](https://dev.mysql.com/downloads/mysql/)
   - Create a database named `employeemanagementsystem`

3. **MySQL JDBC Driver**
   - The project uses `mysql-connector-java-8.0.28.jar`
   - Ensure it's included in your classpath

## Database Setup

1. Start your MySQL server
2. Create the database:
   ```sql
   CREATE DATABASE employeemanagementsystem;
   USE employeemanagementsystem;
   ```

3. Create the required tables:

   **Login Table:**
   ```sql
   CREATE TABLE login (
       username VARCHAR(50) PRIMARY KEY,
       password VARCHAR(50) NOT NULL
   );
   ```

   **Employee Table:**
   ```sql
   CREATE TABLE employee (
       name VARCHAR(100),
       fname VARCHAR(100),
       dob VARCHAR(50),
       salary VARCHAR(50),
       address VARCHAR(200),
       phone VARCHAR(20),
       email VARCHAR(100),
       education VARCHAR(50),
       designation VARCHAR(100),
       nid VARCHAR(50),
       empId VARCHAR(20) PRIMARY KEY
   );
   ```

4. Insert a default login credential (modify as needed):
   ```sql
   INSERT INTO login (username, password) VALUES ('admin', 'admin123');
   ```

## Configuration

Before running the application, update the database connection settings in `Conn.java`:

```java
c = DriverManager.getConnection("jdbc:mysql:///employeemanagementsystem", "root", "YOUR_PASSWORD");
```

Replace `YOUR_PASSWORD` with your MySQL root password.

## Project Structure

```
Employee-Management-System/
├── src/
│   └── employee/
│       └── management/
│           └── system/
│               ├── Splash.java          # Splash screen
│               ├── Login.java           # Login window
│               ├── Home.java            # Main dashboard
│               ├── AddEmployee.java     # Add employee form
│               ├── ViewEmployee.java    # View employees table
│               ├── UpdateEmployee.java  # Update employee form
│               ├── RemoveEmployee.java  # Remove employee interface
│               └── Conn.java            # Database connection
├── src/
│   └── icons/                           # Application icons
├── build/                               # Compiled classes
├── build.xml                            # Ant build file
└── nbproject/                           # NetBeans project files
```

## Building the Project

### Using Apache Ant

1. Navigate to the project directory:
   ```bash
   cd Employee-Management-System
   ```

2. Clean and build:
   ```bash
   ant clean
   ant build
   ```

3. Run the application:
   ```bash
   ant run
   ```

### Using NetBeans IDE

1. Open the project in NetBeans IDE
2. Ensure all external libraries are added to the project:
   - Right-click project → Properties → Libraries
   - Add JAR files: `mysql-connector-java-8.0.28.jar`, `jcalendar-tz-1.3.3-4.jar`, `rs2xml.jar`
3. Build the project (F11)
4. Run the project (F6)

### Using Command Line

1. Compile all Java files:
   ```bash
   javac -cp ".:mysql-connector-java-8.0.28.jar:jcalendar-tz-1.3.3-4.jar:rs2xml.jar" src/employee/management/system/*.java -d build/classes
   ```

2. Run the application:
   ```bash
   java -cp ".:build/classes:mysql-connector-java-8.0.28.jar:jcalendar-tz-1.3.3-4.jar:rs2xml.jar" employee.management.system.Splash
   ```

## Usage

1. **Launch the Application**: Run `Splash.java` or the compiled JAR file
2. **Login**: Enter your username and password on the login screen
3. **Navigate**: Use the buttons on the home screen to:
   - Add new employees
   - View all employees
   - Update employee information
   - Remove employees

## Screenshots
<img width="551" height="314" alt="Screenshot 2025-11-22 180215" src="https://github.com/user-attachments/assets/a6eacf78-ddcc-4cf9-a178-00a17f3dc3a4" />  
<img width="577" height="282" alt="Screenshot 2025-11-22 180222" src="https://github.com/user-attachments/assets/178406dd-2a1c-43cb-bf4b-2f759ff10845" />
<img width="449" height="356" alt="Screenshot 2025-11-22 180230" src="https://github.com/user-attachments/assets/90635a24-ac45-4bf6-bc81-9ade003de530" />
<img width="624" height="145" alt="Screenshot 2025-11-22 180237" src="https://github.com/user-attachments/assets/5c87b6d4-0018-4673-8904-faa6917671cc" />
<img width="349" height="386" alt="Screenshot 2025-11-22 180246" src="https://github.com/user-attachments/assets/00a93187-00f4-47bb-87e5-bb665dd9cd39" />
<img width="446" height="344" alt="Screenshot 2025-11-22 180259" src="https://github.com/user-attachments/assets/6c793dff-e605-4dfb-aec1-dba4ac01bfc2" />
<img width="534" height="209" alt="Screenshot 2025-11-22 180306" src="https://github.com/user-attachments/assets/b593b425-c0fa-4630-85b2-17b3e0097dbb" />


The application includes:
- An animated splash screen with the application title
- A login window with username/password fields
- A home dashboard with navigation buttons
- Forms for adding and updating employee information
- A table view for displaying all employees

## Security Notes

⚠️ **Important**: The current implementation has the database password hardcoded in the source code. For production use, consider:

- Using environment variables for sensitive information
- Implementing a configuration file (not committed to version control)
- Using connection pooling
- Implementing proper password hashing for login credentials

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Tasnimul Intazam Asif**

## Acknowledgments

- Java Swing community
- MySQL documentation
- Open source library contributors

## Troubleshooting

### Common Issues

1. **Database Connection Error**
   - Verify MySQL server is running
   - Check database name and credentials in `Conn.java`
   - Ensure MySQL JDBC driver is in classpath

2. **ClassNotFoundException**
   - Verify all external JAR files are included in classpath
   - Check that JAR files are in the correct location

3. **GUI Not Displaying**
   - Ensure Java version is 17 or higher
   - Check that all Swing components are properly initialized

4. **Date Picker Not Working**
   - Verify `jcalendar-tz-1.3.3-4.jar` is in classpath
   - Check that the library version is compatible

## Future Enhancements

Potential improvements for future versions:
- Password encryption
- Search and filter functionality
- Export to PDF/Excel
- Employee photo upload
- Advanced reporting features
- Multi-user support with role-based access
- Backup and restore functionality

