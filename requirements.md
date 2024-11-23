# Requirements for Backend Features

## 1. User Authentication

- **Description**: Provides secure user login and registration functionality.

- **API Endpoints**:
  - `POST /api/auth/register`:
    - **Input**:  

      ```json
      {
        "name": "John Doe",
        "email": "john.doe@example.com",
        "password": "securePassword123"
      }
      ```

    - **Output (Success)**:  

      ```json
      {
        "message": "User registered successfully",
        "userId": "12345"
      }
      ```

    - **Output (Error)**:  

      ```json
      {
        "error": "Email already exists"
      }
      ```

  - `POST /api/auth/login`:
    - **Input**:  

      ```json
      {
        "email": "john.doe@example.com",
        "password": "securePassword123"
      }
      ```

    - **Output (Success)**:  

      ```json
      {
        "message": "Login successful",
        "token": "JWT_TOKEN"
      }
      ```

    - **Output (Error)**:  

      ```json
      {
        "error": "Invalid email or password"
      }
      ```

- **Validation Rules**:
  - Email must be unique and valid.
  - Password must be at least 8 characters with a mix of letters, numbers, and symbols.
- **Performance Criteria**:
  - Response time < 200ms for login/registration.

---

## 2. Property Management

- **Description**: Allows hosts to add, update, and delete property listings.
  
- **API Endpoints**:
  - `POST /api/properties`:
    - **Input**:  

      ```json
      {
        "title": "Cozy Apartment",
        "description": "A lovely place in the city center",
        "price": 120.00,
        "location": "Accra, Ghana"
      }     

      ```

    - **Output (Success)**:  

      ```json
      {
        "message": "Property added successfully",
        "propertyId": "67890"
      }
      ```

    - **Output (Error)**:  

      ```json
      {
        "error": "Invalid property data"
      }
      ```

  - `PUT /api/properties/:id`:
    - **Input**: Similar to the `POST` endpoint but includes updates.
    - **Output (Success)**:  

      ```json
      {
        "message": "Property updated successfully"
      }
      ```

    - **Output (Error)**:  

      ```json
      {
        "error": "Property not found"
      }
      ```

- **Validation Rules**:
  - Title and description cannot be empty.
  - Price must be a positive number.
- **Performance Criteria**:
  - Response time < 300ms for property creation/updating.

---

## 3. Booking System

- **Description**: Allows guests to book properties and manages booking records.
- **API Endpoints**:
  - `POST /api/bookings`:
    - **Input**:  
  
      ```json
      {
        "propertyId": "67890",
        "checkInDate": "2024-12-01",
        "checkOutDate": "2024-12-10",
        "guestId": "12345"
      }
      ```

    - **Output (Success)**:  

    ```json
      {
        "message": "Booking confirmed",
        "bookingId": "54321"
      }
      ```

    - **Output (Error)**:  

      ```json
      {
        "error": "Property unavailable for the selected dates"
      }
      ```

- **Validation Rules**:
  - Property must be available for the selected dates.
  - Dates must be valid and in the future.
- **Performance Criteria**:
  - Booking confirmation within 500ms.
- **Additional Notes**:
  - Automatically notify the host of a new booking.
