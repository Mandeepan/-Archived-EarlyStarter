# Stocks API Documentation

## Authentication Requirement

All endpoints (except for authentication-related endpoints) require a logged-in user. If a user is not logged in, the following response is returned:

- **Error Response**:
  - **Status Code**: `401`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Authentication required"
    }
    ```

---

## Get All Stocks

Returns a list of all available stocks.

- **Require Authentication**: true
- **Request**:
  - **Method**: `GET`
  - **Route**: `/api/stocks`
  
- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "stocks": [
        {
          "id": 1,
          "ticker": "TSLA",
          "company_name": "Tesla",
          "company_info": "Tesla, Inc., founded in 2003, is a leader in electric vehicles and clean energy...",
          "image_url": "fake_image_of_graph.png",
          "updated_price": 245.56,
          "Is_in_watchlist": true,
          "Is_in_portfolio": false
        }
      ]
    }
    ```

---

## Get Stock Details

Returns details for a specific stock by `stockId`.

- **Require Authentication**: true
- **Request**:
  - **Method**: `GET`
  - **Route**: `/api/stocks/:stockId`

- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "id": 1,
      "ticker": "TSLA",
      "company_name": "Tesla",
      "image_url": "fake_image_of_graph.png",
      "company_info": "Tesla, Inc., founded in 2003, is a leader in electric vehicles and clean energy...",
      "updated_price": 245.56,
      "Is_in_watchlist": true,
      "Is_in_portfolio": false
    }
    ```

- **Error Response**:
  - **Status Code**: `404`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Stock couldn't be found"
    }
    ```

---

## Get Current User's Portfolio Stocks

Returns all stocks in the current user's portfolio.

- **Require Authentication**: true
- **Request**:
  - **Method**: `GET`
  - **Route**: `/api/portfolio/current`

- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "portfolio_stocks": [
        {
          "id": 1,
          "ticker": "TSLA",
          "company_name": "Tesla",
          "image_url": "fake_image_of_graph.png",
          "company_info": "Tesla, Inc., founded in 2003, is a leader in electric vehicles and clean energy...",
          "share_price": 245.56,
          "Share_quantity": 2
        }
      ]
    }
    ```

---

## Add a Stock to Current User's Portfolio

Adds a specified stock to the current user's portfolio.

- **Require Authentication**: true
- **Request**:
  - **Method**: `POST`
  - **Route**: `/api/portfolio/:stockId/current`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "num_shares": 2
    }
    ```

- **Successful Response**:
  - **Status Code**: `201`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "id": 1,
      "ticker": "TSLA",
      "company_name": "Tesla",
      "image_url": "fake_image_of_graph.png",
      "company_info": "Tesla, Inc., founded in 2003, is a leader in electric vehicles and clean energy...",
      "updated_price": 245.56,
      "Share_quantity": 2
    }
    ```

- **Error Response**:
  - **Status Code**: `404`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Stock couldn't be found"
    }
    ```

---

## Delete a Stock from Current User's Portfolio

Removes a specified stock from the current user's portfolio.

- **Require Authentication**: true
- **Request**:
  - **Method**: `DELETE`
  - **Route**: `/api/portfolio/:stockId/current`

- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "successfully deleted"
    }
    ```

- **Error Response**:
  - **Status Code**: `404`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Stock couldn't be found"
    }
    ```

---

## Update a Stock in Current User's Portfolio

Updates the share quantity of a specified stock in the current user's portfolio.

- **Require Authentication**: true
- **Request**:
  - **Method**: `PATCH`
  - **Route**: `/api/portfolio/:stockId/current`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "num_shares": 3
    }
    ```

- **Successful Response**:
  - **Status Code**: `201`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "id": 1,
      "ticker": "TSLA",
      "company_name": "Tesla",
      "image_url": "fake_image_of_graph.png",
      "company_info": "Tesla, Inc., founded in 2003, is a leader in electric vehicles and clean energy...",
      "updated_price": 245.56,
      "Share_quantity": 3
    }
    ```

- **Error Response**:
  - **Status Code**: `404`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Stock couldn't be found"
    }
    ```

---

## Get Current User's Watchlisted Stocks

Returns all stocks in the current user's watchlist.

- **Require Authentication**: true
- **Request**:
  - **Method**: `GET`
  - **Route**: `/api/watchlist/current`

- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "watchlist_stocks": [
        {
          "id": 1,
          "ticker": "TSLA",
          "company_name": "Tesla",
          "image_url": "fake_image_of_graph.png",
          "company_info": "Tesla, Inc., founded in 2003, is a leader in electric vehicles and clean energy...",
          "updated_price": 245.56
        }
      ]
    }
    ```

---

---

## Add a Stock to Current User's Watchlist

Adds a specified stock to the current user's watchlist.

- **Require Authentication**: true
- **Request**:
  - **Method**: `POST`
  - **Route**: `/api/watchlist/:stockId/current`

- **Successful Response**:
  - **Status Code**: `201`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "id": 1,
      "ticker": "TSLA",
      "company_name": "Tesla",
      "image_url": "fake_image_of_graph.png",
      "company_info": "Tesla, Inc., founded in 2003, is a leader in electric vehicles and clean energy...",
      "updated_price": 245.56,
      "Is_in_watchlist": true
    }
    ```

- **Error Response**:
  - **Status Code**: `404`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Stock couldn't be found"
    }
    ```

---

## Delete a Stock from Current User's Watchlist

Removes a specified stock from the current user's watchlist.

- **Require Authentication**: true
- **Request**:
  - **Method**: `DELETE`
  - **Route**: `/api/watchlist/:stockId/current`

- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "successfully deleted from watchlist"
    }
    ```

- **Error Response**:
  - **Status Code**: `404`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Stock couldn't be found"
    }
    ```

---

<!-- ## Get a Specific Stock's Historical Data -->

<!-- Retrieves historical price data for a specific stock.

- **Require Authentication**: true
- **Request**:
  - **Method**: `GET`
  - **Route**: `/api/stocks/:stockId/history`
  - **Query Parameters** (optional):
    - `start_date`: `YYYY-MM-DD`
    - `end_date`: `YYYY-MM-DD`

- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "historical_data": [
        {
          "date": "2024-01-01",
          "open": 240.10,
          "close": 245.56,
          "high": 247.00,
          "low": 238.50,
          "volume": 1200000
        }
      ]
    }
    ```

- **Error Response**:
  - **Status Code**: `404`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "message": "Stock couldn't be found"
    }
    ```

--- -->

## Search for Stocks by Ticker or Company Name

Searches for stocks based on a partial or full ticker symbol or company name.

- **Require Authentication**: true
- **Request**:
  - **Method**: `GET`
  - **Route**: `/api/stocks/search?input=<search string goes here>`
  - **Query Parameters**:
    - `query`: String (required, partial or full match of ticker or company name)

- **Successful Response**:
  - **Status Code**: `200`
  - **Headers**:
    - `Content-Type: application/json`
  - **Body**:
    ```json
    {
      "search_results": [
        {
          "id": 1,
          "ticker": "TSLA",
          "company_name": "Tesla",
          "image_url": "fake_image_of_graph.png",
          "updated_price": 245.56
        }
      ]
    }
    ```

---


