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

## Step 5: About Myself Details
Users can provide additional details about themselves along with an optional file upload.

### API Endpoint
**Method:** `POST`  
**URL:** `http://localhost:8086/api/v1/service/about`

### Request Example
```bash
curl --location 'http://localhost:8086/api/v1/service/about' \
--header 'Cookie: JSESSIONID=2AD4D1F2162C038285778F0D77515589' \
--form 'id="e16a9ec5-7516-483b-949c-d3bc65d6bb2e"' \
--form 'role="ARTIST"' \
--form 'email="citadah995@gholar.com"' \
--form 'description="Your description here"' \
--form 'file=@"/Users/oshorajneesh/Downloads/IMG_9375.JPG"'
`

## Step 6: Assign Service
Users can assign services by providing the necessary details.

### API Endpoint
**Method:** `POST`  
**URL:** `http://localhost:8086/api/v1/service/assign_service`

### Request Example
```bash
curl --location 'http://localhost:8086/api/v1/service/assign_service' \
--header 'Content-Type: application/json' \
--header 'Cookie: JSESSIONID=012EF5AC6F41FBABC85EF16E79BB17DF' \
--data-raw '{
  "id": "e16a9ec5-7516-483b-949c-d3bc65d6bb2e",
  "serviceIdList": ["bdf396b0-10fd-4d39-8230-82bb9b34a8a0", "61c3f20f-0a8f-461c-bee8-7e7119bf5ff9"],
  "role": "ARTIST",
  "email": "citadah995@gholar.com"
}'
