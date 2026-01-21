# Swagger Petstore API Automation Project

## Project Description
This repository hosts a complete Postman Collection designed to automate the testing of the Swagger Petstore REST API. The project utilizes Postman to validate the functionality of the API across three core modules: Pet Management, Store Operations, and User Administration.

The collection includes advanced API testing features such as environment variables for dynamic URL handling, complex JSON payloads for bulk data creation, and file handling for image uploads.

## Repository Contents
* **Swagger Petstore Project.postman_collection.json**: The main test suite containing all HTTP requests and test scripts.
* **Petstore_ENV.postman_environment.json**: The configuration file containing global variables, specifically the `baseUrl`.

## Prerequisites
To run this project, you must have the following installed:
* **Postman** (Desktop App or Web Version)

## Environment Configuration
The project uses a Postman Environment file to manage the API endpoint.

1. Import `Petstore_ENV.postman_environment.json` into Postman.
2. Ensure the variable `baseUrl` is defined.
   * **Variable Name**: `baseUrl`
   * **Recommended Value**: `https://petstore.swagger.io/v2`

## Detailed Test Coverage

### 1. Pet Management Module
This module handles the lifecycle of a pet within the store system.
* **createPet (POST)**: Creates a new pet entry.
    * *Payload includes*: ID, Category, Name (e.g., "Luna"), Photo URLs, Tags, and Status.
* **uploadImage (POST)**: Uploads an image file for a specific pet ID (ID: 101).
    * *Data Type*: Multipart/form-data.
    * *Metadata*: Includes "additionalMetadata" fields.
* **updatePet (PUT)**: Updates existing pet information using a JSON payload.
    * *Scenario*: Changing status to "sold" and name to "Mimi Updated".
* **findByStatus (GET)**: Retrieves pets based on status (e.g., query parameter `status=available`).
* **findByID (POST)**: Retrieves specific pet details using form-data.
* **updateByFormData (POST)**: Updates a pet's name and status using `application/x-www-form-urlencoded`.
* **deletePet (DELETE)**: Removes a pet from the database (ID: 103).

### 2. Store Operations Module
This module validates the ordering and inventory systems.
* **PlaceOrder (POST)**: Submits a new order for a pet.
    * *Payload*: Checks ID, PetID (105), Quantity (20), ShipDate, and Boolean status for completion.
* **Inventory (GET)**: Returns a map of status codes to quantities.
* **CheckOrderbyID (GET)**: Verifies the details of a specific order (ID: 503).
* **DeleteOrder (DELETE)**: Cancels and removes an order from the system (ID: 503).

### 3. User Administration Module
This module tests user creation, authentication, and management.
* **CreateUser (POST)**: Registers a single user.
    * *Test Data*: Registers user "nikola_tesla".
* **createWithArray (POST)**: Tests bulk user creation capabilities.
    * *Dataset*: This request utilizes a complex JSON array to create multiple user accounts simultaneously.
    * *Included Data Profiles*:
        * Albert Einstein
        * Isaac Newton
        * Marie Curie
        * Galileo Galilei
        * Charles Darwin
        * Ada Lovelace
        * Alan Turing
        * Thomas Edison
        * Steve Jobs
        * Grace Hopper
* **updateUser (PUT)**: Modifies account details for specific users (e.g., updating email and password for "albert_einstein").
* **GetUserbyUsername (GET)**: Fetches user data by username.
* **LogInUser (GET)**: Authenticates a user and retrieves a session token.
    * *Query Parameters*: Validates username "steve_jobs" and password.
* **LogOutUser (GET)**: Terminates the current user session.
* **DeleteUser (DELETE)**: Removes a user account from the system.

## How to Run the Collection
1. Open Postman.
2. Click **Import** and select the `.json` files from this repository.
3. Select the **Petstore_ENV** environment from the top-right dropdown menu.
4. Open the **Swagger Petstore Project** folder.
5. Click **Run** to open the Collection Runner.
6. Click **Run Swagger Petstore Project** to execute all tests in sequence.

## Author
**TheSourav-001**
