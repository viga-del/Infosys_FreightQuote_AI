# Infosys Springboard Internship 7.0

## Batch 1 – Milestone 1

# User Authentication Module

## Project Overview

This project was developed as part of the **Infosys Springboard Internship 7.0 – Batch 1, Milestone 1**.

The objective of this milestone is to design and implement a secure **User Authentication System** using **Python**, **Streamlit**, **SQLite**, **JWT Authentication**, and **Gmail OTP Verification**.

The application enables users to register, log in securely, recover forgotten passwords, and access role-based dashboards while following secure authentication practices.

---

# Features Implemented

## User Registration (Signup)

- User Registration with Username and Email
- Unique Username Validation
- Unique Email Validation
- Password Confirmation
- Security Question Selection
- Security Answer Storage
- Password Hashing using bcrypt

---

## User Login

- Secure Login using Email and Password
- Generic Error Message for Invalid Credentials
- JWT-Based Session Authentication
- Secure Session Management

---

## Forgot Password

The application supports two password recovery methods.

### Security Question Verification

- Verify the registered security question
- Validate the user's security answer
- Reset the password securely

### OTP Verification

- Send a One-Time Password (OTP) to the registered Gmail account
- Verify the OTP
- Allow secure password reset

---

## Password Validation

Passwords must satisfy the following conditions:

- Minimum 8 characters
- At least one uppercase letter
- At least one lowercase letter
- At least one digit
- At least one special character

---

## Email Validation

The application validates email addresses according to the required format.

Example:

```
ab@cd.ef
```

---

# Database Features

SQLite is used to store:

- User Information
- Password Hashes
- Password History
- Login Attempts
- Registration Date and Time

---

# Security Features

- bcrypt Password Hashing
- JWT Authentication
- Password History Tracking
- Login Attempt Limiting
- Account Lock after Multiple Failed Attempts
- Gmail OTP Authentication
- Google Colab Secrets Integration

---

# Admin Dashboard

A separate administrator dashboard is available with the following features:

- Secure Admin Login
- View Registered Users
- View User Registration Details
- Passwords are never displayed

---

# Technology Stack

| Technology | Purpose |
|------------|---------|
| Python | Backend Development |
| Streamlit | User Interface |
| SQLite | Database |
| JWT | Session Authentication |
| bcrypt | Password Hashing |
| Gmail SMTP | OTP Delivery |
| Pyngrok | Public URL Generation |
| Google Colab | Development Environment |

---

# Project Structure

```
Milestone1/
│
├── Miestone1.ipynb
├── README.md
└── screenshots/
      ├── login.jpeg
      ├── signup.jpeg
      ├── forgot_security.jpeg
      ├── forgot_otp.jpeg
      ├── otp_email.jpeg
      ├── dashboard.jpeg
      └── admin_dashboard.jpeg
```

---

# Google Colab Secrets

The following secrets are securely stored using **Google Colab Secrets**.

| Secret | Description |
|---------|-------------|
| JWT_SECRET | Secret key used for JWT token generation |
| NGROK_AUTHTOKEN | ngrok authentication token |
| EMAIL_ADDRESS | Gmail account used to send OTP |
| EMAIL_PASSWORD | Gmail App Password |

No sensitive credentials are hardcoded into the source code.

---

# How to Run the Project

### Step 1

Open the project in **Google Colab**.

### Step 2

Configure the following Google Colab Secrets:

- JWT_SECRET
- NGROK_AUTHTOKEN
- EMAIL_ADDRESS
- EMAIL_PASSWORD

### Step 3

Install the required libraries.

```bash
pip install streamlit pyjwt bcrypt pyngrok plotly streamlit-option-menu
```

### Step 4

Run all the project cells/files in the correct order.

### Step 5

Launch the Streamlit application.

### Step 6

Open the generated ngrok public URL in your browser.

---

# Screenshots

## Login Page

![Login Page](screenshots/login.jpeg)

---

## Signup Page

![Signup Page](screenshots/signup.jpeg)

---

## Forgot Password – Security Question

![Forgot Password Security](screenshots/forgot_security.jpeg)

---

## Forgot Password – OTP Verification

![Forgot Password OTP](screenshots/forgot_otp.jpeg)

---

## OTP Email

![OTP Email](screenshots/otp_email.jpeg)

---

## User Dashboard

![User Dashboard](screenshots/dashboard.jpeg)

---

## Admin Dashboard

![Admin Dashboard](screenshots/admin_dashboard.jpeg)

---

# Learning Outcomes

This project provided practical experience in:

- User Authentication
- JWT-Based Session Management
- Password Hashing with bcrypt
- SQLite Database Management
- Gmail SMTP Integration
- OTP Verification
- Streamlit Application Development
- Google Colab Secrets
- ngrok Deployment
- Secure Authentication Best Practices

---

# Future Enhancements

- Multi-Factor Authentication (MFA)
- Email Verification during Registration
- Password Strength Indicator
