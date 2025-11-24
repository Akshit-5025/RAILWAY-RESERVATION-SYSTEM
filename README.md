# RAILWAY-RESERVATION-SYSTEM
# Railway Reservation System (RRS)

## Overview

The Railway Reservation System (RRS) is a console-based Python application designed to simulate a simple railway ticket booking platform. It allows users to book tickets, view reservations, check PNR status, and cancel bookings. The system stores all data in a MySQL database for persistence and includes features like seat selection, cost calculation (including GST), and basic validation for user inputs. This project demonstrates a full CRUD (Create, Read, Update, Delete) application in a real-world scenario, focusing on ease of use and security (e.g., username verification for cancellations).

The program is built to handle bookings for 20 major Indian stations, 7 train options, multiple classes, and food preferences, making it a comprehensive tool for managing train reservations.

## Features

- **Ticket Booking**: Users can select origin/destination stations, travel date, train, class, seats (from a predefined layout), passenger names, and food options. It generates a unique 5-digit PNR and calculates total cost with 18% GST.
- **View All Reservations**: Retrieve and display all bookings associated with a specific username.
- **PNR Status Check**: View detailed ticket information using the PNR number.
- **Reservation Cancellation**: Cancel a booking by PNR and verify ownership via username, with a preview of the cancelled ticket.
- **Input Validation**: Limits invalid attempts for critical inputs (e.g., date format, station selection) to prevent errors.
- **Seat Layout Visualization**: Displays a simple ASCII art seat map for selection.
- **Database Integration**: All data is stored securely in MySQL, with automatic table creation on first run.

## Technologies/Tools Used

- **Programming Language**: Python 3.12+ (uses built-in modules like `datetime`, `random`, and `time`).
- **Database**: MySQL (via `mysql-connector-python` library for connectivity and queries).
- **Libraries**:
  - `mysql.connector`: For database operations (connection, CRUD).
- **Environment**: Local MySQL server (e.g., XAMPP, MySQL Workbench, or official MySQL installer).
- **No External Dependencies**: Relies on standard Python libraries except for the MySQL connector.

## Steps to Install & Run the Project

1. **Prerequisites**:
   - Install Python 3.12+ from [python.org](https://www.python.org/downloads/).
   - Install MySQL Server from [mysql.com](https://dev.mysql.com/downloads/mysql/) (or use XAMPP for an all-in-one setup).
   - Ensure MySQL is running on `localhost` with root access.

2. **Install Dependencies**:
   - Open a terminal/command prompt.
   - Install the MySQL connector:  
     ```
     pip install mysql-connector-python
     ```

3. **Database Setup**:
   - Update the MySQL credentials in the code:
     - In `create_database()`: Change `password="passwd"` to your MySQL root password.
     - In `connect_to_db()`: Change `password="Database"` to your MySQL root password.
   - The script will automatically create the database `RailwayReservationSystem` and table `RESERVATIONS` on first run.

4. **Run the Project**:
   - Save the code as `rrs_code.py`.
   - In the terminal, navigate to the file's directory and run:  
     ```
     python rrs_code.py
     ```
   - The main menu will appear. Follow on-screen prompts to interact.

5. **Troubleshooting**:
   - If connection fails, verify MySQL is running and credentials match.
   - Ensure the database name `RailwayReservationSystem` is not manually altered.

## Instructions for Testing

1. **Initial Run**:
   - Launch the script; it will create the database/table if needed.
   - Select option 1 (Reserve a Ticket) and complete a booking:
     - Enter a username (e.g., "testuser").
     - Choose valid origin (1-20) and destination (from available options).
     - Input a future date in `YYYY-MM-DD` format (e.g., `2025-12-01`).
     - Select a train (1-7), class (1-5), seats (e.g., "1,3"), passenger names (e.g., "John Doe, Jane Smith"), and food (1-2).
     - Confirm to generate PNR and save.

2. **Test Viewing Reservations**:
   - Select option 2, enter the username (e.g., "testuser").
   - Verify all details (PNR, origin, etc.) are displayed correctly.

3. **Test PNR Status**:
   - Select option 3, enter the generated PNR.
   - Confirm full details match the booking.

4. **Test Cancellation**:
   - Select option 4, enter the PNR and matching username.
   - Verify the preview shows details, and the booking is removed (re-run view to confirm).

5. **Edge Cases**:
   - Test invalid inputs (e.g., wrong date format) – should prompt up to 5 times before warning.
   - Book multiple tickets with the same username and verify listing.
   - Attempt cancellation with wrong username – should deny access.
   - Exit via option 5.

6. **Verification**:
   - Use MySQL Workbench or command line (`mysql -u root -p`) to query:  
     ```
     USE RailwayReservationSystem;
     SELECT * FROM RESERVATIONS;
     ```
   - Ensure data persists across runs.

For issues, check console errors or MySQL logs. This project is for educational purposes; extend it for production use (e.g., add authentication, web UI).
