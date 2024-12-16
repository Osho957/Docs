# Onboarding Flow APIs

## Step 1: Select Role
Users can select one of the following roles:
- `ARTIST`
- `STUDIO`

---

## Step 2: Enter Email
This step triggers an API call to send an OTP to the provided email address.

### API Endpoint
**Method:** `POST`  
**URL:** `http://localhost:8086/api/v2/auth/signup`

### Request Example
```bash
curl --location --request POST 'http://localhost:8086/api/v2/auth/signup?email=rajy3600%40gmail.com&role=STUDIO'
```

| Parameter | Type   | Description                   |
|-----------|--------|-------------------------------|
| `email`   | String | Email address of the user.    |
| `role`    | String | Selected role (`ARTIST` or `STUDIO`). |

---

## Step 3: Verify OTP
The OTP sent to the user’s email is verified in this step.

### API Endpoint
**Method:** `POST`  
**URL:** `http://localhost:8086/api/v2/auth/verify`

### Request Example
```bash
curl --location --request POST 'http://localhost:8086/api/v2/auth/verify?email=rajy3600%40gmail.com&otp=876166'
```

| Parameter | Type   | Description                       |
|-----------|--------|-----------------------------------|
| `email`   | String | Email address of the user.        |
| `otp`     | String | OTP sent to the user’s email.     |

---

## Step 4: Register Details
Users provide their details to complete the registration process.

### API Endpoint
**Method:** `POST`  
**URL:** `http://localhost:8086/api/v1/register`

### Request Headers
```plaintext
Content-Type: application/json
Cookie: JSESSIONID=5B9FE3B232BEE44BADA16B8D134D1F0E
```

### Request Body
```json
{
    "fullName": "Alok Gautam",
    "email": "alokgautam02@gmail.com",
    "phoneNumber": "1234567890",
    "city": "Gurugram",
    "state": "Haryana",
    "country": "India",
    "zipCode": 123456,
    "area": "24/5 dlf phase 3",
    "role": "ARTIST"
}
```

| Field        | Type   | Description                       |
|--------------|--------|-----------------------------------|
| `fullName`   | String | Full name of the user.            |
| `email`      | String | Email address of the user.        |
| `phoneNumber`| String | Contact number of the user.       |
| `city`       | String | City of residence.                |
| `state`      | String | State of residence.               |
| `country`    | String | Country of residence.             |
| `zipCode`    | Number | Postal code of the user’s area.   |
| `area`       | String | Specific area or address details. |
| `role`       | String | Selected role (`ARTIST` or `STUDIO`). |

---

## Remaining Steps
Additional APIs will be added to complete the onboarding flow. Verification and testing are in progress for these endpoints.

