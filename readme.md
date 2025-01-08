

# DataCrypt : Client Side Encryption for Secure Cloud Storage

DataCrypt is a secure application designed for encrypting and sharing data using advanced cryptographic techniques such as **Elliptic Curve Cryptography (ECC)** and **AES-256**. This project demonstrates secure key exchange mechanisms, encryption, and OTP generation for authentication, providing a foundation for secure communication.

---

## Features

- **Elliptic Curve Cryptography (ECC):**
    - Implements ECC-based key agreement protocols for secure communication.
    - Dynamically generates private and public keys.

- **AES-256 Encryption:**
    - Utilizes the **AES-256 encryption algorithm** to secure sensitive data.
    - Ensures strong confidentiality for user data and cryptographic operations.

- **OTP Generation:**
    - Randomized OTP is generated for user authentication.
    - OTP is emailed to the user for a secure login experience.

- **Dynamic Email Integration:**
    - Uses SMTP to send email notifications, including OTPs.

- **Database Connectivity:**
    - Seamlessly integrates with a relational database to manage user credentials and cryptographic key sharing.

---

## Technologies Used

- **Java 21**
- **Servlet API**
- **Elliptic Curve Cryptography (ECC)** (`KeyPairGenerator`)
- **AES-256 (Advanced Encryption Standard)** (`javax.crypto` library)
- **SMTP Email Integration** (via `javax.mail`)
- **Relational Database** (SQL-based database)

---

## Prerequisites

1. **Java Version:** Ensure you have **Java 21** installed.
2. **Database Configuration:**
    - Set up a database table to manage user records (`users` table with fields like `userid`, `email`, `user_key`, `secretu`, `u_status`, etc.).
3. **Environment Variables:**
    - Use a `.env` file to manage sensitive email credentials.
      ```plaintext
      MAIL_USERNAME=<Your Email Username>
      MAIL_PASSWORD=<Your Email Password>
      ```

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-repo/DataCrypt.git
cd DataCrypt
```

### 2. Configure `.env` File

You need to configure your `.env` file for managing sensitive email credentials. For example:

```plaintext
MAIL_USERNAME=your_email@gmail.com
MAIL_PASSWORD=your_email_password
```

The `.env` file is loaded using the [Dotenv library](https://github.com/cdimascio/java-dotenv).

### 3. Database Setup

Ensure your database is running, and create the necessary tables. For example:

```sql
CREATE TABLE users (
    userid VARCHAR(255) PRIMARY KEY,
    email VARCHAR(255),
    user_key VARCHAR(255),
    secretu VARCHAR(255),
    user_otp INT,
    u_status INT
);
```

### 4. Run the Application

Deploy the project in a **Java Servlet Container** like Apache Tomcat or Jetty. Access the application via the appropriate endpoint, e.g., `/keyGeneration`.

---
```
src/
├── main/
│   ├── java/
│   │   ├── com.example.connection/
│   │   │   └── DbConnection.java              # Establishes database connection
│   │   ├── com.example.email/
│   │   │   └── EmailUtility.java              # Sends email using SMTP
│   │   ├── com.example.features/
│   │   │   ├── KeyGeneration.java            # Main servlet for ECC and AES operations
│   │   │   └── OTPGeneration.java            # Handles OTP creation logic
│   ├── resources/
│   │   └── .env                              # File for environment variables
│   ├── webapp/
│   │   ├── WEB-INF/
│   │   │   └── web.xml                       # Deployment descriptor for servlets
│   │   ├── keyexchange.jsp                   # JSP page for initiating key sharing
│   │   └── secretkey.jsp                     # JSP for displaying key generation result
```
## Security Details

### **Elliptic Curve Cryptography (ECC):**
ECC is used in the project to:
- Generate public and private keys for secure communication.
- Implement the Elliptic-Curve Diffie-Hellman (ECDH) key agreement protocol.

### **AES-256 Encryption:**
- **Purpose:** AES-256 ensures end-to-end encryption of user data and sensitive details.
- AES-256 uses a 256-bit key, providing an advanced level of security for modern applications.
- Encryption is applied to sensitive datasets, ensuring strong confidentiality.

### Example of AES-256 Usage:
- Encrypting sensitive keys before storing them in the database.
- Securely processing cryptographic key exchange and user-related data.

---

## Example Use Case

1. **User Request:**
    - User enters their `userid` and related details.

2. **Key Generation:**
    - ECC private/public keys are dynamically generated using preconfigured elliptic curve parameters.

3. **Data Encryption:**
    - AES-256 encryption secures sensitive keys before storing them in the database.

4. **OTP Transmission:**
    - A random OTP is generated and sent to the user's registered email.

5. **Secure Communication:**
    - The secret key is transferred securely using the ECC-based protocol.

---

## How to Contribute

1. Fork the repository.
2. Make your changes and ensure that they follow Java best practices.
3. Test your changes.
4. Create a PR (Pull Request) with detailed descriptions of modifications.

---

## Future Improvements

- Add user-friendly front-end interfaces for better interaction.
- Implement token-based authentication for enhanced security.
- Add AES-256 encryption validation and comprehensive exception handling.
- Improve database query performance using optimizations and ORM frameworks.

---

## License

This project is licensed under the MIT License. See `LICENSE` for details.

---

## Author

- **Your Name/Team**
- [your.email@example.com](mailto:your.email@example.com)
- [GitHub Profile](https://github.com/your-profile)
