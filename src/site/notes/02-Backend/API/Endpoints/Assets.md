---
{"dg-publish":true,"permalink":"/02-backend/api/endpoints/assets/"}
---

### Create Asset
##### POST `/assets`
##### Request Body
```json
{
  "name": "LED Moving Head Light",
  "quantity": 50,
  "inMaintenance": 5
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Asset created successfully",
  "data": {
    "id": "uuid",
    "name": "LED Moving Head Light",
    "quantity": 50,
    "inMaintenance": 5,
    "available": 45,
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T12:00:00Z"
  }
}
```
##### Error Response
```json
{
  "success": "false",
  "message": "This name is already taken",
  "data": null
}
```
##### Errors
- Asset already exists
---
### Get Assets
##### Query Parameters (optional)
- `page` → integer (default: 1)
- `limit` → integer (default: 20)
- `search` → string (search by asset name)
##### Example Request
```pgsql
GET /assets?page=1&limit=10&search=light
```
##### Response
```json
{
  "success": true,
  "message": "Assets fetched successfully",
  "data": {
    "items": [
      {
        "id": "uuid-1",
        "name": "LED Moving Head Light",
        "quantity": 50,
        "inMaintenance": 5,
        "available": 45,
        "createdAt": "2025-08-16T12:00:00Z",
        "updatedAt": "2025-08-16T12:00:00Z"
      },
      {
        "id": "uuid-2",
        "name": "Truss Rig",
        "quantity": 20,
        "inMaintenance": 2,
        "available": 13,
        "createdAt": "2025-08-10T10:00:00Z",
        "updatedAt": "2025-08-15T09:00:00Z"
      }
    ],
    "pagination": {
      "page": 1,
      "limit": 10,
      "totalItems": 2,
      "totalPages": 1
    }
  }
}
```
---
### Get Asset by ID
##### GET `/assets/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "Asset fetched successfully",
  "data": {
    "id": "uuid",
    "name": "LED Moving Head Light",
    "quantity": 50,
    "inMaintenance": 5,
    "available": 45,
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T12:00:00Z"
  }
}
```
##### Error Response
```json
{
  "success": "false",
  "message": "This asset does not exist",
  "data": null
}
```
##### Errors
- Asset does not exist
---
### Update an Asset
##### PATCH `/assets/{id}`
##### Request Body
```json
{
  "inMaintenance": 8
}
```
##### Success Respone
```json
{
  "success": true,
  "message": "Asset updated successfully",
  "data": {
    "id": "uuid",
    "name": "LED Moving Head Light",
    "quantity": 50,
    "inMaintenance": 8,
    "available": 42,
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T13:45:00Z"
  }
}
```
##### Error Response
```json
{
  "success": "false",
  "message": "This asset does not exist",
  "data": null
}
```
##### Errors
- Asset does not exist
---
### Delete an Asset
##### DELETE `/assets/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "Asset deleted successfully",
  "data": null
}
```
---
### Check Asset Availability
##### POST `/assets/availability`
##### Request Body
```json
{
  "startDate": "2025-09-10T18:00:00Z",
  "endDate": "2025-09-10T23:00:00Z"
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Availability computed successfully",
  "data": [
    { "assetId": "uuid-a1", "name": "LED Moving Head Light", "availableQuantity": 15 },
    { "assetId": "uuid-a2", "name": "Stage Rig", "availableQuantity": 3 },
    { "assetId": "uuid-a3", "name": "Revolving Beam", "availableQuantity": 12 }
  ]
}
```
