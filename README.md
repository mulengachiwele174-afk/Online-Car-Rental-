```markdown
<div align="center">

# Online Car Rental System

### A web-based vehicle booking platform for Zambia, built with PHP and MySQL

**by Mulenga Chiwele** · Diploma in Information Technology · Evelyn Hone College · 2024

**Association:** Mulungushi University, Zambia

<img alt="PHP" src="https://img.shields.io/badge/PHP-7.4-777BB4?style=for-the-badge&logo=php&logoColor=white">
<img alt="MySQL" src="https://img.shields.io/badge/MySQL-Database-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
<img alt="Platform" src="https://img.shields.io/badge/Platform-XAMPP-FB7A24?style=for-the-badge">
<img alt="Status" src="https://img.shields.io/badge/Status-Completed-2E7D32?style=for-the-badge">

[Overview](#overview) · [Features](#features) · [Technology Stack](#technology-stack) · [Installation](#installation) · [Usage](#usage) · [Testing](#testing) · [Contact](#about-the-author)

**© 2024 Mulenga Chiwele. All Rights Reserved.**

</div>

---

## Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Objectives](#objectives)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Database Design](#database-design)
- [Installation](#installation)
- [Usage](#usage)
- [Testing](#testing)
- [Security Considerations](#security-considerations)
- [Limitations](#limitations)
- [Future Enhancements](#future-enhancements)
- [Project Report](#project-report)
- [About the Author](#about-the-author)
- [Disclaimer](#disclaimer)
- [Copyright](#copyright)

---

## Overview

The Online Car Rental System lets customers browse, reserve and pay for vehicles online from a computer or smartphone. It replaces manual, phone-based and office-hours booking with a single platform that shows real-time vehicle availability and keeps records in a MySQL database.

The project was developed as a final-year diploma project for the Diploma in Information Technology at Evelyn Hone College, Zambia. It covers the full software lifecycle: requirements gathering, design, implementation, testing, deployment and documentation.

## Problem Statement

Car rental in Zambia still relies heavily on manual processes. Customers often must visit an office to register or check availability, bookings are tracked in spreadsheets, and double bookings occur when inventory is not updated in real time. Most agencies are also limited to office hours and offer little personalization, feedback channels or secure online payment.

## Objectives

- Allow customers to make secure online payments for rentals.
- Display real-time vehicle availability and prevent double bookings.
- Manage detailed vehicle information for operational efficiency.
- Give customers a way to track their rentals.

## Features

**Customer features**

- Online registration and login
- Browse listed vehicles with images, specifications and daily prices
- Search and view vehicle details
- Book a vehicle for a chosen date range
- Pay for bookings through mobile money (Flutterwave integration)
- Update account details and change password
- Submit testimonials and contact queries
- Subscribe to updates

**Administrator features**

- Secure admin login and dashboard
- Add vehicle brands and post new vehicles with up to five images
- Edit or delete vehicles and their features
- Confirm or cancel bookings
- Manage registered users, subscribers and testimonials
- Manage website pages (Terms and Conditions, Privacy Policy, About Us, FAQs)
- Read and resolve Contact Us queries

## Technology Stack

| Layer | Technology |
|-------|-----------|
| Server-side scripting | PHP 7.4 |
| Database | MySQL (managed with phpMyAdmin) |
| Front end | HTML, CSS, JavaScript, Bootstrap |
| Local server | XAMPP (Apache and MySQL) |
| Payments | Flutterwave API (mobile money, ZMW) |
| Code editor | Visual Studio Code |

## System Architecture

The system follows a standard three-tier web design:

1. **Presentation layer:** HTML, CSS, Bootstrap and JavaScript pages for customers and administrators.
2. **Application layer:** PHP scripts that handle login, booking, vehicle management, payments and validation.
3. **Data layer:** MySQL tables for users, vehicles, bookings, payments, pages, brands and queries.

Database access uses PHP Data Objects (PDO) with bound parameters for most queries.

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
| `tbltestimonial` | Customer testimonials and approval status |
| `tblsubscribers` | Newsletter subscribers |

Relationships include users to bookings, vehicles to bookings, and bookings to payments.

## Installation

**Requirements**

- Windows, Linux or macOS with XAMPP installed
- A modern browser (Google Chrome or Firefox)
- At least 8 GB RAM and a dual-core processor (Intel Core i5 class or equivalent)

**Steps**

1. Download and install XAMPP from [apachefriends.org](https://www.apachefriends.org/download.html).
2. Open the XAMPP Control Panel and start **Apache** and **MySQL**.
3. Copy the project folder into the `htdocs` directory:

   ```
   C:\xampp\htdocs\online_car_rental-system
   ```

4. Open `http://127.0.0.1` in your browser to confirm the XAMPP dashboard loads.
5. Open phpMyAdmin, create a new database (for example, `online_car_rental`), and import the SQL file from the project's `Database` folder.
6. Configure the database connection in `includes/config.php` with your local database name, username and password.
7. Add your Flutterwave API credentials to the payment module. Keep these keys out of version control.
8. Open the project in your browser:

   ```
   http://localhost/online_car_rental-system
   ```

## Usage

**Customers**

1. Register with your name, email, contact number and address.
2. Log in and browse the available vehicles.
3. Open a vehicle to view its features and daily price.
4. Select your travel dates and submit a booking.
5. Complete payment through the mobile money option.
6. Track your bookings from your account.

**Administrators**

1. Log in through the admin login page.
2. Add vehicle brands, then post vehicles with their specifications and images.
3. Confirm or cancel bookings from the booking list.
4. Manage users, testimonials, subscribers, pages and contact queries.

## Testing

Six core test cases were run against the main functions. All passed.

| Test ID | Description | Input | Expected Result | Status |
|---------|-------------|-------|-----------------|--------|
| TC-01 | Login with valid details | Valid username and password | User logs in successfully | Pass |
| TC-02 | Login with invalid details | Incorrect password | Error message displayed | Pass |
| TC-03 | Search for a vehicle | Vehicle model | Relevant results displayed | Pass |
| TC-04 | View vehicle details | Vehicle ID | Detailed vehicle information displayed | Pass |
| TC-05 | Make a booking | Vehicle ID and dates | Booking confirmation displayed | Pass |
| TC-06 | Process payment | Mobile wallet | Payment processed successfully | Pass |

## Security Considerations

The system includes several security measures, and the following areas are identified for improvement before any production deployment:

- **Password hashing:** Passwords are currently hashed with MD5, which is no longer considered secure. Migrate to `password_hash()` and `password_verify()` (bcrypt or Argon2).
- **File uploads:** Vehicle image uploads should validate file type and size, rename files on upload, and store them outside executable paths.
- **CSRF protection:** Forms that change data should include anti-CSRF tokens.
- **Error handling:** Error reporting is suppressed on several pages. Production code should log errors privately and show generic messages to users.
- **Session handling:** Regenerate session IDs after login and set secure cookie flags.
- **Secrets management:** Payment API keys and database credentials should be stored in environment variables or a configuration file excluded from version control.

These points are informed by the web security lessons from later weeks of the Networkwalks programme, including the penetration test documented in this portfolio.

## Limitations

- Customers without internet access must still visit a physical location to rent a car.
- Real-time availability synchronization was technically demanding and depends on a stable database connection.
- Secure payment gateway integration required careful configuration and testing.
- Authentication relies on the hashing scheme described above and needs modernizing.

## Future Enhancements

- **Maps and navigation:** Google Maps integration for directions, traffic updates and nearby rental points.
- **Location services:** GPS-based discovery of nearby rental locations and location-aware vehicle suggestions.
- **Promotions:** Location-based and event-based offers sent to customers.
- **Augmented reality:** AR navigation assistance during the rental period.
- **Security hardening:** Implement the security improvements listed above.

## Project Report

📄 **[Download the Full Project Report](./Online-Car-Rental-System-Report.pdf)**

The report includes the literature review, requirements specification, design specification (ERD, security design, UI and output design), implementation, testing, installation and user manuals, and technical appendices.

## About the Author

**Mulenga Chiwele**
Diploma in Information Technology · Evelyn Hone College, Zambia
Associated with Mulungushi University, Zambia
Aspiring Security Analyst | Web Development | Network Security

I build practical software projects and am developing my skills in web security, penetration testing and secure development.

- GitHub: [mulengachiwele174-afk](https://github.com/mulengachiwele174-afk)
- LinkedIn: [Mulenga Chiwele](https://www.linkedin.com/in/mulenga-chiwele-712a64365)
- Email: [Mulengachiwele174@gmail.com](mailto:Mulengachiwele174@gmail.com)

## Disclaimer

This project was developed for academic purposes as part of a diploma programme. Vehicle, pricing and company information shown in the system is for demonstration only. Payment functionality must be configured with the developer's own credentials and tested in a sandbox environment before any real transactions are processed.

## Copyright

© 2024 Mulenga Chiwele. All Rights Reserved.

This project, including its source code, documentation, design and written analysis, is the original work of **Mulenga Chiwele**. You are welcome to read, study and link to it for learning purposes. You may not copy, republish or present it as your own, in whole or in part, without prior written permission from the author.

For permissions and enquiries: [Mulengachiwele174@gmail.com](mailto:Mulengachiwele174@gmail.com)

---

<div align="center">

### © 2024 Mulenga Chiwele · All Rights Reserved

Original academic work by **Mulenga Chiwele**. Please do not copy or republish without permission.

<sub>Online Car Rental System · Diploma in Information Technology · 2024</sub>

<sub>Enquiries: [Mulengachiwele174@gmail.com](mailto:Mulengachiwele174@gmail.com)</sub>

</div>
```
