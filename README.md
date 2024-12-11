**Steps to Run the Project**

**1. Face Sketch Construction Using JavaFX**

1.	Set Up JavaFX Development Environment
o	Install a Java Development Kit (JDK) (version 11 or higher recommended).
o	Install JavaFX libraries compatible with your JDK version.
o	Use an IDE like IntelliJ IDEA, Eclipse, or NetBeans and configure it for JavaFX development.

2.	Load the JavaFX Application
o	Open your JavaFX project in the IDE.
o	Ensure you have the necessary files for the construction module:
	FXML Files: For the user interface layout.
	Controller Classes: Handling user actions and interactions.
	Assets: Images or icons used in the UI.

3.	Integrate Scene Builder
o	Use Scene Builder to visually design FXML files for your application.
o	Update controllers to handle user interactions for the sketch construction process.

4.	Run the JavaFX Application
o	Start the application using the main() method in the JavaFX project.
o	Use the GUI to perform face sketch construction.

5.	Save or Export the Sketch
o	Save the constructed sketch in an image format (e.g., .png or .jpg) locally.
o	Ensure the sketch is accessible for the recognition process.
________________________________________
**2. Face Recognition Using FastAPI API**

1.	Set Up the FastAPI Environment
o	Install Python (version 3.8 or higher) and set up a virtual environment:
bash
Copy code
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
o	Install required dependencies:
bash
Copy code
pip install fastapi uvicorn pymongo face_recognition numpy opencv-python-base

2.	Start the MongoDB Database
o	Install and run MongoDB (Community or Atlas version).
o	Ensure the MongoDB server is running at localhost:27017 or update the connection string in the FastAPI code.

3.	Run the FastAPI Application
o	Save the FastAPI code in a file (e.g., main.py).
o	Start the server:
bash
Copy code
uvicorn main:app --reload
o	API will be available at http://127.0.0.1:8000.

4.	Database Configuration
o	Use a MongoDB collection (user) to store user data:
	Fields: name, age, dob, phone, address, image (binary), embeddings (binary).
o	Each user's face embeddings are stored after registration.

5.	Register New Users
o	Use the /register_new_user endpoint to register users:
	Upload a photo and provide user details (e.g., name, age, address).
	Ensure the embeddings are generated and stored in MongoDB.

6.	Recognize Faces
o	Use the /recognize/ endpoint to upload a photo for recognition.
o	The API:
	Extracts face embeddings from the uploaded image.
	Compares embeddings with known faces in the MongoDB database.
	Returns recognized user details and annotated image.
________________________________________
**Database Used: MongoDB**

Purpose
•	User Data Storage: Stores user details (name, age, etc.) and their corresponding face embeddings.
•	Binary Data: Handles binary storage for images and face embeddings.
Structure of the user Collection
json
Copy code
{
  "name": "John Doe",
  "age": 30,
  "dob": "1994-02-15",
  "phone": "1234567890",
  "address": "123 Main Street, City",
  "image": "<binary data>",
  "embeddings": "<binary data>"
}
________________________________________
**Complete Workflow**

1.	Construct a Sketch (JavaFX):
o	Create a composite sketch of the suspect using the JavaFX application.
o	Save the sketch image locally.

2.	Recognize the Sketch (FastAPI):
o	Convert the sketch into an image format compatible with the API.
o	Upload the sketch to the /recognize/ endpoint for recognition.
o	The API:
	Extracts face embeddings from the sketch.
	Matches embeddings with existing data in MongoDB.
	Returns recognized user details if found.
________________________________________
**Testing and Debugging**

•	Testing Construction: Run the JavaFX application and test various UI features.
•	Testing API:
o	Use tools like Postman or curl to test API endpoints.
o	Verify MongoDB data entries after user registration.
•	Debugging Recognition:
o	Log face detection and matching results.
o	Ensure embeddings are correctly generated and stored.

