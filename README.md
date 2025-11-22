# 🏷️ Coupon Management System

A robust and scalable coupon management system built on a modern Node.js stack, emphasizing a **functional programming (FP)** paradigm for core business logic.

## ✨ Features

* **FP Core:** All critical logic (eligibility checks, discount calculation, validation) is implemented using **pure functions** for predictability and easier testing.
* **Complex Eligibility Rules:** Manage coupons based on various criteria:
    * Minimum cart value (`minCartValue`)
    * Specific product categories (`applicableCategories`)
    * Allowed user membership tiers (`allowedUserTiers`)
    * Usage limits (per user and total)
* **Best Coupon Finder:** Efficiently determine the single best applicable coupon that maximizes the user's discount for a given cart.
* **Tech Stack:** Node.js, Express, and MongoDB for persistence.
* **Robust Validation:** Comprehensive error handling for creation and application workflows (e.g., duplicate code, expired date, invalid cart).

---

## 💻 API Endpoints

### 1. Coupon Management

#### `POST /api/coupons` - Create a new coupon

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `code` | `string` | Unique coupon code (e.g., `SUMMER20`). |
| `discountType` | `string` | `PERCENT` or `FIXED`. |
| `discountValue` | `number` | The value of the discount (e.g., `20` or `500`). |
| `maxDiscountAmount` | `number` | Optional cap on the maximum discount for `PERCENT` type. |
| `startDate`, `endDate` | `string` | ISO 8601 timestamps for validity period. |
| `eligibility` | `object` | Complex rules for application. |


## 📸 UI Preview

###  create coupon 
![Hero Section](./public/create-coupon.png)

###  create coupon response
![Hero Section](./public/create-coupon-response.png)

###  dublicate coupon response
![Hero Section](./public/dublicate-coupon-code.png)

###  get coupons 
![About Section](./public/get-coupons.png)

###  add to cart 
![Capability Section](./public/add-to-cart.png)

###  create product
![Feature Section](./public/create-product.png)


###  get best coupon
![Contact Section](./public/get-best-coupon.png)


**Body Example:**
```json
{
  "code": "SUMMER20",
  "description": "20% off summer sale",
  "discountType": "PERCENT",
  "discountValue": 20,
  "maxDiscountAmount": 1000,
  "startDate": "2024-06-01T00:00:00Z",
  "endDate": "2024-08-31T23:59:59Z",
  "usageLimitPerUser": 2,
  "eligibility": {
    "minCartValue": 2000, // Min cart value in smallest currency unit (e.g., cents)
    "allowedUserTiers": ["SILVER", "GOLD", "PLATINUM"],
    "applicableCategories": ["clothing", "shoes"]
  }
}
