# ✈️ Aviatrax: Flight Ticketing System

A database-driven flight booking web application built for **CSE 370: Database Systems** at BRAC University (Fall 2024, Group 09). Passengers can search flights, book tickets, pay, check weather-based approval, and download e-tickets. Everything is backed by a relational MySQL database.

## Features

- **User authentication:** register, log in, and log out with PHP session handling
- **Profile management:** view, update, and delete your profile
- **Flight search:** search by source, destination, and travel date
- **Flight booking:** choose the number of seats, class (Economy or Business), and seat type (Window, Aisle, or Middle)
- **Weather check:** weather data (visibility, wind speed, precipitation, temperature) decides whether a ticket is approved or cancelled
- **Payment processing:** Visa, MasterCard, bKash, or PayPal, with status tracking (Pending, Completed, Failed)
- **Ticket cancellation:** cancel a ticket with a reason, and the payment record is refunded and removed
- **Booking history and e-tickets:** view past bookings and download tickets as PDFs

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | PHP |
| Database | MySQL |
| PDF generation | FPDF |
| Server | Apache via XAMPP |

## Database Design

The database (`flightbookingdb`) has 8 tables:

`passengers` · `airline` · `flights` · `economy` · `business` · `ticket` · `payment` · `weather`

- `flights` is specialized into `economy` and `business` (EER disjoint specialization)
- `ticket` links passengers to flights and stores status and cancellation reason
- `payment` links to `ticket` via the `T_num` foreign key
- `weather` is checked per flight to approve or reject bookings


## Getting Started

1. Install [XAMPP](https://www.apachefriends.org/) and start **Apache** and **MySQL**.
2. Clone this repo into `htdocs`:
```bash
   git clone <your-repo-url> C:/xampp/htdocs/aviatrax
```
3. Open **phpMyAdmin**, create a database named `flightbookingdb`, and import the provided `.sql` file.
4. Download [FPDF](http://www.fpdf.org/) and place it in the project's `fpdf/` folder.
5. Update the DB credentials in your config/connection file if needed.
6. Visit `http://localhost/aviatrax` in your browser.

## Team

| Name | ID | Contribution |
|---|---|---|
| Ameet Faisal | 22201869 | Login/registration, profile update and delete, home page, booking history, PDF tickets, weather check |
| Khan Farhan Mahdi | 22201698 | Flight search, flight booking |
| Shahriar Mohammad | 22299020 | Payment processing, ticket cancellation |

## Future Improvements

- Hash passwords (e.g., `password_hash()`) and use prepared statements throughout
- Integrate a live weather API and real payment gateways
- Add an admin panel for managing flights and airlines
- Round-trip search and seat map selection
