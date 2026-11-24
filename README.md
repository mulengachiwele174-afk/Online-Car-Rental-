# Online Car Rental System

A web-based car rental and booking platform for Zambia, built with PHP and MySQL.

**Author:** Mulenga Chiwele
**Institution:** Evelyn Hone College, Diploma in Information Technology (2024)
**Association:** Mulungushi University, Zambia

![PHP](https://img.shields.io/badge/PHP-7.4-777BB4?logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?logo=mysql&logoColor=white)
![XAMPP](https://img.shields.io/badge/Platform-XAMPP-FB7A24)
![Status](https://img.shields.io/badge/Status-Completed-2E7D32)

[Overview](#overview) · [Features](#features) · [Installation](#installation) · [Usage](#usage) · [Testing](#testing) · [Security](#security-considerations) · [Report](#project-report) · [Author](#author) · [License](#license-and-copyright)

---

## Table of Contents

1. [Overview](#overview)
2. [Problem Statement](#problem-statement)
3. [Objectives](#objectives)
4. [Project Scope](#project-scope)
5. [Requirements](#requirements)
6. [Features](#features)
7. [Technology Stack](#technology-stack)
8. [System Architecture](#system-architecture)
9. [Database Design](#database-design)
10. [Implementation](#implementation)
11. [Installation](#installation)
12. [Usage](#usage)
13. [Testing](#testing)
14. [Project Timeline](#project-timeline)
15. [Screenshots](#screenshots)
16. [Security Considerations](#security-considerations)
17. [Limitations](#limitations)
18. [Future Enhancements](#future-enhancements)
19. [Lessons Learned](#lessons-learned)
20. [Repository Structure](#repository-structure)
21. [Project Report](#project-report)
22. [Acknowledgments](#acknowledgments)
23. [Author](#author)
24. [Disclaimer](#disclaimer)
25. [License and Copyright](#license-and-copyright)

---

## Overview

The Online Car Rental System enables customers to browse, reserve and pay for vehicles online from a computer or smartphone. It replaces phone-based and office-hours booking with a single platform that displays vehicle availability in real time and stores all records in a MySQL database.

The system was developed as a final-year diploma project at Evelyn Hone College. The work covered the full development lifecycle: requirements gathering, design, implementation, testing, deployment and documentation.

## Problem Statement

Car rental in Zambia still depends heavily on manual processes. Customers often need to visit an office to register or check availability, bookings are tracked in spreadsheets, and double bookings occur when inventory is not updated promptly. Most providers operate only during office hours and offer limited personalization, feedback channels and secure online payment.

## Objectives

- Enable customers to make secure online payments for rentals.
- Display real-time vehicle availability and prevent double bookings.
- Maintain detailed vehicle records to support daily operations.
- Give customers a way to track their rentals.

## Project Scope

The project draws on several areas, from the business of car rental to software development:

- **Car rental industry:** How rental businesses operate, the processes involved, and where improvements are possible.
- **Users:** General customers and the company's staff, who both use the system.
- **Benchmarking:** Comparison with existing services in Zambia and internationally, including PeeJay's Car Hire, Benmak Car Hire, Zambia Car Hire and Hertz.

## Requirements

### Fact-Finding

Requirements were gathered through two methods:

- **Interviews:** Semi-structured interviews with potential users, car rental operators and industry experts, covering desired features, pain points, payment preferences and expectations for support.
- **Observation:** Observational research at two local car rental agencies, focusing on booking workflows, customer behaviour and interaction with existing systems.

### Functional Requirements

- New users register online and receive a membership card.
- Customers reserve vehicles online.
- The database updates automatically when a new reservation is made or a new customer registers.
- Customers can log in to view and manage their accounts.

### Non-Functional Requirements

- **Security:** Protected data, restricted access to sensitive areas, and authenticated logins.
- **Availability:** Designed to operate 24 hours a day, 7 days a week, with restoration within one to two working days after a major failure.
- **Ease of use:** A simple, consistent interface that requires minimal training.

### Hardware Requirements

| Component | Specification |
|-----------|---------------|
| Processor | Intel Core i5-7200U (dual-core, 2.50 GHz) or equivalent |
| Memory | 8 GB RAM |
| Storage | 500 GB |

### Software Requirements

| Component | Specification |
|-----------|---------------|
| Operating system | Windows, iOS or Unix |
| Web browser | Google Chrome or Firefox |
| Server environment | XAMPP |
| Back end | PHP and MySQL |
| Front end | HTML, CSS, JavaScript |
| Editor | Visual Studio Code or Notepad++ |

## Features

### Customer

- Registration and login
- Browse vehicles with images, specifications and daily prices
- Search for vehicles and view their details
- Book a vehicle for a selected date range
- Pay through mobile money (Flutterwave integration)
- Update account details and change password
- Submit testimonials and contact queries
- Subscribe to updates

### Administrator

- Secure admin login and dashboard
- Add vehicle brands and post vehicles with up to five images
- Edit or remove vehicles and their features
- Confirm or cancel bookings
- Manage users, subscribers and testimonials
- Edit website pages (Terms and Conditions, Privacy Policy, About Us, FAQs)
- Read and resolve Contact Us queries

## Technology Stack

| Layer | Technology |
|-------|------------|
| Server-side scripting | PHP 7.4 |
| Database | MySQL, managed with phpMyAdmin |
| Front end | HTML, CSS, JavaScript, Bootstrap |
| Local server | XAMPP (Apache and MySQL) |
| Payments | Flutterwave API (mobile money, ZMW) |
| Editor | Visual Studio Code |

## System Architecture

The application follows a three-tier web architecture:

1. **Presentation layer:** HTML, CSS, Bootstrap and JavaScript pages for customers and administrators.
2. **Application layer:** PHP scripts that handle authentication, bookings, vehicle management, payments and validation.
3. **Data layer:** MySQL tables for users, vehicles, bookings, payments, pages, brands and queries.

Most database queries use PHP Data Objects (PDO) with bound parameters.

## Database Design

| Table | Purpose |
|-------|---------|
| `tblusers` | Customer accounts and profile details |
| `tbladmin` | Administrator accounts |
| `tblvehicles` | Vehicle details, pricing, images and features |
| `tblbrands` | Vehicle brands |
| `tblbooking` | Reservations, dates and booking status |
| `tblpayment` | Payment records linked to users, vehicles and bookings |
| `tblpages` | Editable website content |
| `tblcontactinfo` | Company contact details |
| `tblcontactusquery` | Customer messages and their status |
| `tbltestimonial` | Testimonials and approval status |
| `tblsubscribers` | Newsletter subscribers |

Bookings link users to vehicles, and payments link to bookings.

## Implementation

- **Server-side logic:** PHP 7.4 handles login, booking, vehicle management and payment requests.
- **Interface:** HTML, CSS, JavaScript and Bootstrap provide a responsive layout that works on desktop and mobile.
- **Data access:** MySQL is managed through phpMyAdmin, and PHP Data Objects (PDO) run most queries with bound parameters.
- **Payments:** The payment module calls the Flutterwave API to start a mobile money transaction in ZMW and redirects the customer to complete it.
- **Changeover:** The project used a parallel changeover, so the manual and new systems ran side by side. Users could compare outputs before fully switching over.
- **Training:** Users received hands-on training and written documentation to support the transition.

## Installation

### Requirements

- Windows, Linux or macOS with XAMPP installed
- Google Chrome or Firefox
- 8 GB RAM and a dual-core processor (Intel Core i5 class or equivalent)

### Steps

1. Install XAMPP from [apachefriends.org](https://www.apachefriends.org/download.html).
2. Open the XAMPP Control Panel and start **Apache** and **MySQL**.
3. Copy the project folder into the `htdocs` directory:

   ```
   C:\xampp\htdocs\online_car_rental-system
   ```

4. Open `http://127.0.0.1` to confirm the XAMPP dashboard loads.
5. In phpMyAdmin, create a database (for example, `online_car_rental`) and import the SQL file from the project's `Database` folder.
6. Set the database name, username and password in `includes/config.php`.
7. Add your Flutterwave API credentials to the payment module. Keep them out of version control.
8. Open the application in your browser:

   ```
   http://localhost/online_car_rental-system
   ```

## Usage

### Customers

1. Register with your name, email, contact number and address.
2. Log in and browse available vehicles.
3. Open a vehicle to view its features and daily price.
4. Choose travel dates and submit a booking.
5. Complete payment through mobile money.
6. Track bookings from your account.

### Administrators

1. Log in through the admin login page.
2. Add vehicle brands, then post vehicles with their specifications and images.
3. Confirm or cancel bookings.
4. Manage users, testimonials, subscribers, pages and contact queries.

## Testing

Six core test cases covered the main functions. All passed.

| Test ID | Description | Input | Expected Result | Status |
|---------|-------------|-------|-----------------|--------|
| TC-01 | Login with valid details | Valid username and password | User logs in successfully | Pass |
| TC-02 | Login with invalid details | Incorrect password | Error message displayed | Pass |
| TC-03 | Search for a vehicle | Vehicle model | Relevant results displayed | Pass |
| TC-04 | View vehicle details | Vehicle ID | Detailed information displayed | Pass |
| TC-05 | Make a booking | Vehicle ID and dates | Booking confirmation displayed | Pass |
| TC-06 | Process payment | Mobile wallet | Payment processed successfully | Pass |

## Project Timeline

| Phase | Dates (2024) | Focus |
|-------|--------------|-------|
| 1. Planning and Analysis | 16 – 28 July | Requirements gathering, system design, project setup |
| 2. Development | 29 July – 22 September | Frontend, backend and PHP–MySQL integration |
| 3. Testing and Quality Assurance | 23 September – 10 October | System testing, bug fixing, performance tuning |
| 4. Deployment and Training | 11 – 24 October | Live deployment, user training, documentation |
| 5. Maintenance and Support | 25 October – 12 November | Ongoing support and monitoring |

## Screenshots

Add screenshots of the main pages to an `screenshots/` folder and link them here:

| Page | Description |
|------|-------------|
| Landing page | Public home page with vehicle listings |
| Customer registration and login | Account creation and sign-in |
| Vehicle details and booking | Vehicle information and booking form |
| Admin dashboard | Administrator overview |
| Manage vehicles | Vehicle editing and listing |

## Security Considerations

The application includes basic protections. The following areas should be addressed before any production deployment:

- **Password hashing:** Passwords are currently hashed with MD5, which is no longer considered secure. Migrate to `password_hash()` and `password_verify()` with bcrypt or Argon2.
- **File uploads:** Validate file type and size, rename uploaded files, and store them outside executable paths.
- **CSRF protection:** Add anti-CSRF tokens to forms that change data.
- **Error handling:** Log errors privately and show generic messages to users rather than suppressing errors.
- **Session handling:** Regenerate session IDs after login and set secure cookie flags.
- **Secrets management:** Store payment API keys and database credentials in environment variables or a configuration file excluded from version control.

These improvements reflect the web security lessons from later Networkwalks modules, including the penetration test documented in this portfolio.

## Limitations

- Customers without internet access must still visit a physical location to rent a car.
- Real-time availability synchronization was technically demanding and depends on a stable database connection.
- Integrating a secure payment gateway required careful configuration and testing.
- Authentication relies on the MD5 scheme described above and needs modernizing.

## Future Enhancements

- **Maps and navigation:** Google Maps integration for directions, traffic updates and nearby rental points.
- **Location services:** GPS-based discovery of nearby rental locations and location-aware vehicle suggestions.
- **Promotions:** Location-based and event-based offers.
- **Augmented reality:** AR navigation assistance during the rental period.
- **Security hardening:** Implementation of the improvements listed above.

## Lessons Learned

- Requirements gathered through interviews and observation shape the design more than assumptions do.
- Real-time availability and secure payments are harder to integrate than they first appear.
- Testing each core function separately makes faults easier to find and fix.
- Security has to be designed in from the start, not added after the system works.
- Thorough documentation and user training are essential for a smooth changeover.

## Repository Structure

```
online_car_rental-system/
├── Database/          # SQL file for importing into phpMyAdmin
├── includes/          # Configuration and shared code (config.php)
├── img/vehicleimages/ # Uploaded vehicle images
├── makepayments/      # Payment integration
├── screenshots/       # Screenshots for this README
├── index.php          # Landing page
├── login.php          # Customer login
└── README.md          # This file
```

Adjust the folder names above to match your project's actual layout.

## Project Report

The full project report is available here:

[Download the Full Project Report](./Online-Car-Rental-System-Report.pdf)

The report covers the literature review, requirements specification, design specification (ERD, security design, UI and output design), implementation, testing, installation and user
