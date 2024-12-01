

# Product API

This project is a simple **Node.js API** built with **Express** and **Mongoose** to manage products. It includes features for filtering, sorting, pagination, and field selection, along with a global error handler.

## Features
- **Filter Products**: Search products by features, company, name, and numeric filters (e.g., price, rating).
- **Sort Results**: Sort products by specified fields.
- **Field Selection**: Choose specific fields to return in the response.
- **Pagination**: Split results into pages.
- **Global Error Handling**: Centralized error management using middleware.

## Requirements
- **Node.js** (v16 or later)
- **MongoDB** (local or cloud-based)

## Installation
1. Clone the repository:
    ```bash
    git clone <repository-url>
    cd <repository-folder>
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Configure environment variables:  
    Create a `.env` file in the project root with the following content:
    ```env
    MONGO_URI=your-mongodb-uri
    PORT=5000
    ```

4. Start the application:
    ```bash
    npm start
    ```

## API Usage

### 1. Fetch All Products
**GET /api/v1/products**

#### Query Parameters:

| Parameter         | Description                                                       | Example                        |
|-------------------|-------------------------------------------------------------------|--------------------------------|
| `featured`        | Filter by featured status (`true`/`false`).                       | `featured=true`                |
| `company`         | Filter by company name.                                           | `company=Apple`                |
| `name`            | Search by product name (case-insensitive).                       | `name=phone`                   |
| `sort`            | Sort results by fields (comma-separated).                        | `sort=price,rating`            |
| `fields`          | Select specific fields to return (comma-separated).              | `fields=name,price`            |
| `numericFilters`  | Filter numeric fields (e.g., price, rating) with operators.      | `numericFilters=price>100`     |
| `page`            | Page number (default: 1).                                        | `page=2`                       |
| `limit`           | Number of results per page (default: 10).                        | `limit=5`                      |

#### Example Request:
```bash
GET /api/v1/products?featured=true&company=Apple&name=phone&sort=price&fields=name,price&page=2&limit=5
```

This request would retrieve all products that are featured, from the company "Apple", with "phone" in their name, sorted by price, showing only the fields `name` and `price`, on the second page with a limit of 5 products per page.
