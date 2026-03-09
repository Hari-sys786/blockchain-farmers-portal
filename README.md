# 🌾 Blockchain Farmers Portal

A Django-based e-commerce portal for farmers using blockchain technology to record secure transactions between sellers and buyers.

## Features

- **Sellers (Farmers):** Register, login, add/update/delete crops with images
- **Buyers:** Register, login, search crops, add to cart, purchase with blockchain-backed transactions
- **Admin:** Activate/deactivate users, view all blockchain transactions
- **Blockchain:** SHA-256 based blockchain records every purchase transaction immutably

## Tech Stack

- Python 3 / Django
- SQLite
- Bootstrap 4 (CDN)
- Custom Blockchain (SHA-256)

## Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/Hari-sys786/blockchain-farmers-portal.git
cd blockchain-farmers-portal
```

### 2. Create virtual environment (recommended)

```bash
python3 -m venv venv
source venv/bin/activate   # Linux/Mac
# venv\Scripts\activate    # Windows
```

### 3. Install dependencies

```bash
pip install django
```

### 4. Run migrations

```bash
python manage.py makemigrations buyers sellers
python manage.py migrate
```

### 5. Start the server

```bash
python manage.py runserver
```

Visit: **http://127.0.0.1:8000/**

## Default Credentials

| Role | Username | Password |
|------|----------|----------|
| Admin | admin | admin123 |
| Seller | alex | Alex@141 |
| Seller | sagar | Sagarbabu@141 |
| Buyer | meghana | Meghana@141 |
| Buyer | harish | Harish@141 |
| Buyer | ramesh | Ramesh@141 |

> **Note:** New seller/buyer accounts require admin activation before login.

## Project Structure

```
blockchain-farmers-portal/
├── manage.py
├── farmersportal/          # Django project settings
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── buyers/                 # Buyer app
│   ├── models.py
│   ├── views.py
│   ├── forms.py
│   ├── urls.py
│   └── utility/
│       └── BlockChainImpl.py
├── sellers/                # Seller app
│   ├── models.py
│   ├── views.py
│   ├── forms.py
│   └── urls.py
├── admins/                 # Admin app
│   ├── views.py
│   └── urls.py
└── templates/              # All HTML templates
    ├── base.html
    ├── index.html
    ├── sellers/
    ├── buyers/
    └── admins/
```

## Modules

### Seller Module
- Register with name, email, mobile, address
- Login after admin activation
- Add crops with name, price, description, image
- Update/delete existing crops
- View buyer cart orders

### Buyer Module
- Register with name, email, mobile, address
- Login after admin activation
- Search crops by name
- Add crops to cart
- Checkout — payment recorded as blockchain transaction
- View purchase history and transaction details

### Admin Module
- Login with admin credentials
- Activate/block registered sellers and buyers
- View all blockchain transactions with current & previous block details

### Blockchain
- In-memory blockchain with SHA-256 hashing
- Each purchase creates a new block with:
  - Sender (buyer), Recipient (bank), Amount
  - Timestamp, Proof, Previous Hash
- Transactions also persisted in SQLite for viewing

## How It Works

1. Seller registers → Admin activates → Seller adds crops
2. Buyer registers → Admin activates → Buyer searches & adds crops to cart
3. Buyer checks out → Card details entered (simulated) → Blockchain block created
4. Transaction recorded with current block hash + previous block reference
5. Admin can view the full blockchain transaction ledger

## License

Academic project — Study of Blockchain Technology in Farmer's Portal.
