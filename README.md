# Receipt Processor

This project is a web service that processes receipts and calculates points based on specific rules. The service is implemented in Go.

## Setup Instructions

### Prerequisites

- Go (version 1.16 or later)
- Docker (optional, for running the application in a container)

### Running the Application Locally

1. **Clone the repository**:

    ```sh
    git clone https://github.com/jrakam/receipt-processor.git
    cd receipt-processor
    ```

2. **Install dependencies**:

    ```sh
    go mod tidy
    ```

3. **Run the application**:

    ```sh
    go run main.go
    ```

4. **Access the API**:
    - The API will be running at `http://localhost:8000`.

### Running the Application with Docker

1. **Build the Docker image**:

    ```sh
    docker build -t receipt-processor .
    ```

2. **Run the Docker container**:

    ```sh
    docker run -p 8000:8000 receipt-processor
    ```

3. **Access the API**:
    - The API will be running at `http://localhost:8000`.

## Testing the API

You can use tools like Postman or curl to test the API endpoints.

### Example Test with Postman

1. **Process Receipts**:
    - **Method**: `POST`
    - **URL**: `http://localhost:8000/receipts/process`
    - **Body**: 
        ```json
        {
            "retailer": "Target",
            "purchaseDate": "2022-01-01",
            "purchaseTime": "13:01",
            "items": [
                {
                    "shortDescription": "Mountain Dew 12PK",
                    "price": "6.49"
                },
                {
                    "shortDescription": "Emils Cheese Pizza",
                    "price": "12.25"
                },
                {
                    "shortDescription": "Knorr Creamy Chicken",
                    "price": "1.26"
                },
                {
                    "shortDescription": "Doritos Nacho Cheese",
                    "price": "3.35"
                },
                {
                    "shortDescription": "Klarbrunn 12-PK 12 FL OZ",
                    "price": "12.00"
                }
            ],
            "total": "35.35"
        }
        ```

2. **Get Points**:
    - **Method**: `GET`
    - **URL**: `http://localhost:8000/receipts/{id}/points`
    - Replace `{id}` with the actual receipt ID received from the `Process Receipts` response.

