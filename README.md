# 6106 Web DApp - Payment System

A Flask-based web application integrated with Solidity smart contracts for managing deposits and money transfers. This DApp simulates a payment system similar to WeChat Pay (Weixin).

## Features

- **User Management**: Register and log users with timestamp tracking
- **Deposit Money**: Deposit funds through smart contract integration
- **PayNow Transfer**: Transfer money between users via blockchain
- **User Logs**: View and manage transaction history
- **SQLite Database**: Local database for user activity logging

## Tech Stack

**Backend:**
- Python 3.x
- Flask - Web framework
- SQLite3 - Database
- Gunicorn - WSGI HTTP Server

**Smart Contracts:**
- Solidity ^0.8.0
- Hardhat - Development environment

## Project Structure

```
.
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── user.db               # SQLite database
├── solidity/
│   ├── deposit.sol       # Deposit smart contract
│   └── paynow.sol        # Payment transfer smart contract
├── templates/            # HTML templates
│   ├── index.html        # Login page
│   ├── main.html         # Main dashboard
│   ├── deposit.html      # Deposit interface
│   ├── paynow.html       # Payment interface
│   ├── userlog.html      # User logs view
│   └── delete-userlog.html
└── static/
    └── styles.css        # Application styles
```

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd AY2025-6106
   ```

2. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up the database**
   The SQLite database will be created automatically when you first run the application.

## Usage

1. **Run the Flask application**
   ```bash
   python app.py
   ```

   Or with Gunicorn:
   ```bash
   gunicorn app:app
   ```

2. **Access the application**
   Open your browser and navigate to `http://localhost:5000`

3. **Using the DApp**
   - Enter your username on the login page
   - Navigate to different features from the main dashboard:
     - **Deposit**: Add funds to your account
     - **PayNow**: Transfer money to another user
     - **User Logs**: View transaction history

## Smart Contracts

### Deposit Contract (`deposit.sol`)
Manages deposit transactions with the following functions:
- `deposit_money(address depositor_input, uint amount_input)`: Record a deposit
- `deposit_view()`: View depositor address and amount

### PayNow Contract (`paynow.sol`)
Manages money transfers between users:
- `transfer_money(address payer_input, address payee_input, uint amount_input)`: Execute transfer
- `transfer_view()`: View payer, payee, and transfer amount

## API Routes

- `GET/POST /` - Login page
- `GET/POST /main` - Main dashboard
- `GET/POST /deposit` - Deposit interface
- `GET/POST /paynow` - Payment transfer interface
- `GET/POST /userlog` - View user logs
- `GET/POST /delete-userlog` - Clear user logs

## Database Schema

**User Table:**
- `name` - User name
- `timestamp` - Transaction timestamp

## Development

This project was developed as part of the AY2025 curriculum for course 6106.

## License

MIT
