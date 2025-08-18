---
{"dg-publish":true,"permalink":"/02-backend/api/endpoints/users/"}
---

### Get User by ID
##### GET `/users/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "User details retrieved successfully",
  "data": {
    "id": "uuid",
    "email": "remi@example.com",
    "firstName": "Remi",
    "lastName": "Alo",
    "phoneNumber": "+2348012345678",
    "createdAt": "2025-08-15T12:00:00Z",
    "updatedAt": "2025-08-15T12:00:00Z"
  }
}
```
##### Error Response
```json
{
  "success": false,
  "message": "User not found",
  "data": null
}
```
##### Errors
- User not found
----
### Update User
##### PATCH `/users/{id}`
##### Request
```json
{
  "firstName": "Remi",
  "lastName": "Alo",
  "phoneNumber": "+2348012345678"
}
```
##### Success Response
```json
{
  "success": true,
  "message": "User updated successfully",
  "data": {
    "id": "uuid",
    "email": "remi@example.com",
    "firstName": "Remi",
    "lastName": "Alo",
    "phoneNumber": "+2348012345678",
    "createdAt": "2025-08-15T12:00:00Z",
    "updatedAt": "2025-08-15T14:00:00Z"
  }
}
```
##### Error Response
```json
{
  "success": false,
  "message": "Invalid phone number format",
  "data": null
}
```
##### Errors
- Invalid format (email, phone)
- User not found
- ---
### Delete User
##### DELETE `/users/:id`
##### Success Response
```json
{
  "success": true,
  "message": "User deleted successfully",
  "data": null
}
```
##### Error Response
```json
{
  "success": false,
  "message": "User not found",
  "data": null
}
```
##### Errors
- User not found
---
### Authentication: Register
##### POST `/auth/register`
##### Request
```json
{
  "email": "remi@example.com",
  "password": "StrongPass123!",
  "firstName": "Remi",
  "lastName": "Alo",
  "phoneNumber": "+2348012345678"
}
```
##### Success Response
```json
{
  "success": true,
  "message": "User registered successfully. Please verify your email with the OTP sent.",
  "data": {
    "id": "uuid",
    "email": "remi@example.com"
  }
}
```
##### Error Response
```json
{
  "success": false,
  "message": "Email already exists",
  "data": null
}
```
##### Errors
- Missing required fields
- Password invalid format
- Email already exists
---
### Authentication: Login
##### POST `/auth/login`
##### Request
```json
{
  "email": "remi@example.com",
  "password": "StrongPassword123"
}
```
##### Response
```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "accessToken": "jwt_token_here",
    "refreshToken": "refresh_token_here",
    "user": {
	    "id": "uuid",
	    "name": "Aderemi Alo",
	    "email": "remi@example.com",
	    "phoneNumber": "+23481355513987",
	    "emailVerified": "false",
		"createdAt": "2025-08-16T12:00:00Z",
		"updatedAt": "2025-08-16T15:00:00Z"
    }
  }
}
```
##### Error Response
```json
{
  "success": false,
  "message": "Invalid credentials",
  "data": null
}
```
##### Errors
- Invalid credentials
---
### Authentication: Refresh Token
##### POST `/auth/refresh`
##### Request
```json
{
  "refresh_token": "jwt.refresh.here"
}
```

##### Success Response
```json
{
  "success": true,
  "message": "Token refresh successful",
  "data": {
    "accessToken": "new_jwt_token_here",
    "refreshToken": "new_refresh_token_here",
  }
}
```
##### Error Response
```json
{
  "success": false,
  "message": "Invalid or expired refresh token",
  "data": null
}
```
##### Errors
- Invalid/expired refresh token
---
### Authentication: Logout
##### POST `/auth/logout`
##### Response
```json
{
  "success": true,
  "message": "Logout successful",
  "data": null
}
```
---
### Validate OTP
##### POST `/auth/validate-otp`
##### Request Body
```json
{
  "email": "remi@example.com",
  "otp": "123456"
}
```
##### Success Response
```json
{
  "success": true,
  "message": "OTP validated successfully",
  "data": null
}
```
##### Error Response
```json
{
  "success": false,
  "message": "Invalid or expired OTP",
  "data": null
}
```
##### Errors
- Invalid or expired OTP
---
### Forgot Password
##### POST `/auth/forgot-password`
```json
{
  "email": "remi@example.com"
}
```
##### Success Response
```json
{
  "success": true,
  "message": "OTP has been sent to your email",
  "data": null
}
```
##### Error Response
```json
{
  "success": false,
  "message": "This email does not exist",
  "data": null
}
```
---
### Reset Password
##### POST `/auth/reset-password`
##### Request Body
```json
{
  "email": "remi@example.com",
  "newPassword": "NewStrongPass123!"
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Password reset successful",
  "data": null
}
```