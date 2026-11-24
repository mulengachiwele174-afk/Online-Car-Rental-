<div align="center">

# Online Car Rental System

### A web-based vehicle booking platform for Zambia, built with PHP and MySQL

**Developed by Mulenga Chiwele** · Diploma in Information Technology · Evelyn Hone College · 2024

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

The Online Car Rental System allows customers to browse, reserve and pay for vehicles online from a computer or smartphone. It replaces phone-based and office-hours booking with one platform that shows vehicle availability in real time and stores all records in a MySQL database.

The system was built as a final-year diploma project at Evelyn Hone College, Zambia. The work covered the full development lifecycle: requirements gathering, design, implementation, testing, deployment and documentation.

## Problem Statement

Car rental in Zambia still depends heavily on manual processes. Customers often need to visit an office to register or check availability, bookings are tracked in spreadsheets, and double bookings occur when inventory is not updated promptly. Most providers operate only during office hours and offer little personalization, feedback channels or secure online payment.

## Objectives

- Enable customers to make secure online payments for rentals.
- Show real-time vehicle availability and prevent double bookings.
- Maintain detailed vehicle records to support daily operations.
- Give customers a way to track their rentals.

## Features

**Customer**

- Registration and login
- Browse vehicles with images, specifications and daily prices
- Search for vehicles and view their details
- Book a vehicle for a selected date range
- Pay through mobile money (Flutterwave integration)
- Update account details and change password
- Submit testimonials and contact queries
- Subscribe to updates

**Administrator**

- Secure admin login and dashboard
- Add vehicle brands and post vehicles with up to five images
- Edit or remove vehicles and their features
- Confirm or cancel bookings
- Manage users, subscribers and testimonials
- Edit website pages (Terms and Conditions, Privacy Policy, About Us, FAQs)
- Read and resolve Contact Us queries

## Technology Stack

| Layer | Technology |
|-------|-----------|
| Server-side scripting | PHP 7.4 |
| Database | MySQL, managed with phpMyAdmin |
| Front end | HTML, CSS, JavaScript, Bootstrap |
| Local server | XAMPP (Apache and MySQL) |
| Payments | Flutterwave API (mobile money, ZMW) |
| Editor | Visual Studio Code |

## System Architecture

The application follows a three-tier web design:

1. **Presentation:** HTML, CSS, Bootstrap and JavaScript pages for customers and administrators.
2. **Application:** PHP scripts that handle login, bookings, vehicle management, payments and validation.
3. **Data:** MySQL tables for users, vehicles, bookings, payments, pages, brands and queries.

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

## Installation

**Requirements**

- Windows, Linux or macOS with XAMPP installed
- Google Chrome or Firefox
- 8 GB RAM and a dual-core processor (Intel Core i5 class or equivalent)

**Steps**

1. Install XAMPP from [apachefriends.org](https://www.apachefriends.org/download.html).
2. Open the XAMPP Control Panel and start **Apache** and **MySQL**.
3. Copy the project folder into the `htdocs` directory:

   ```
   C:\xampp\htdocs\online_car_rental-system
   ```

4. Open `http://127.0.0.1` to confirm the XAMPP dashboard loads.
5. In phpMyAdmin, create a database (for example, `online_car_rental`) and import the SQL file from the project's `Database` folder.
6. Set the database name, username and password in `includes/config.php`.
7. Add your Flutterwave API credentials to the payment module, and keep them out of version control.
8. Open the application:

   ```
   http://localhost/online_car_rental-system
   ```

## Usage

**Customers**

1. Register with your name, email, contact number and address.
2. Log in and browse available vehicles.
3. Open a vehicle to view its features and daily price.
4. Choose your travel dates and submit a booking.
5. Complete payment through mobile money.
6. Track your bookings from your account.

**Administrators**

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

## Security Considerations

The application includes basic protections, but the following areas should be addressed before any production use:

- **Password hashing:** Passwords are currently hashed with MD5, which is no longer considered secure. Move to `password_hash()` and `password_verify()` using bcrypt or Argon2.
- **File uploads:** Validate file type and size, rename uploaded files, and store them outside executable paths.
- **CSRF protection:** Add anti-CSRF tokens to forms that change data.
- **Error handling:** Log errors privately and show generic messages to users instead of suppressing errors.
- **Session handling:** Regenerate session IDs after login and set secure cookie flags.
- **Secrets management:** Keep payment API keys and database credentials in environment variables or a config file excluded from version control.

These improvements reflect the web security lessons from the later Networkwalks modules, including the penetration test documented in this portfolio.

## Limitations

- Customers without internet access still need to visit a physical location to rent a car.
- Real-time availability synchronization was technically demanding and depends on a stable database connection.
- Integrating a secure payment gateway required careful configuration and testing.
- Authentication relies on the MD5 scheme described above and needs modernizing.

## Future Enhancements

- **Maps and navigation:** Google Maps integration for directions, traffic updates and nearby rental points.
- **Location services:** GPS-based discovery of nearby rental locations and location-aware vehicle suggestions.
- **Promotions:** Location-based and event-based offers.
- **Augmented reality:** AR navigation assistance during the rental period.
- **Security hardening:** Implement the improvements listed above.

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

This project was developed for academic purposes. Vehicle, pricing and company information in the system is for demonstration only. Payment functionality must be configured with the developer's own credentials and tested in a sandbox environment before it processes real transactions.

## Copyright

© 2024 Mulenga Chiwele. All Rights Reserved.

This project, including its source code, documentation, design and written analysis, is the original work of **Mulenga Chiwele**. You may read, study and link to it for learning purposes. You may not copy, republish or present it as your own, in whole or in part, without prior written permission from the author.

For permissions and enquiries: [Mulengachiwele174@gmail.com](mailto:Mulengachiwele174@gmail.com)

---

<div align="center">

### © 2024 Mulenga Chiwele · All Rights Reserved

Original academic work by **Mulenga Chiwele**. Please do not copy or republish without permission.

<sub>Online Car Rental System · Diploma in Information Technology · 2024</sub>

<sub>Enquiries: [Mulengachiwele174@gmail.com](mailto:Mulengachiwele174@gmail.com)</sub>

</div>
