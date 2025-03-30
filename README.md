# DigitalTweenNreal
An AR project created using Unity as part of a subject at FER (Faculty of Electrical engeneering and computing).

This project consists of two Unity applications that work together to place a house model in the real world and send its data and geographical coordinates to a Python Flask server. The first app is made for NReal Light AR glasses and works with placing the model in the real-world environment. Since the AR glasses don't have an embedded GPS system, we developed a simple mobile app, used to send geographical coordinates of the user to the NReal app using a Flask server. There is another app that takes the model data from the Flask server and recreates it in a Digital Twin, but since we did not develop the app, it is not here as a part of this project.

![Login](https://github.com/user-attachments/assets/e7d5a319-9da3-4247-bd2e-e753d368eb31)
![CreateHouse](https://github.com/user-attachments/assets/bc7009e9-3fca-435d-a455-e7e04853c688)
![House](https://github.com/user-attachments/assets/48e2e1a7-e202-4797-84e8-61417574534f)

## Project Overview
### Components
1. Mobile App (Android)
   - A simple Unity app meant to be installed onto an Android phone
   - Contains a button that retrieves the device's GPS coordinates on click
   - Sends the data to the Flask server
2. AR App (NReal Light Glasses)
   - A Unity App meant to run on NReal Light AR glasses
   - Enables the user to Log in and receive data about placeable house models
   - Enables the user to select and place a model of the house
   - The placed model can then be moved and rotated and its location can be locked
   - Periodically requests the latest GPS coordinates from the Flask server
   - When model is locked, its data, along with the GPS coordinates is sent to the Flask server

## Instalation and Setup
Clone the repository 
1. Mobile App (Android)
   - Upload the "Geolocation.apk" app from the Build folder onto an Android smartphone
   - Open the app on your Android smartphone
2. AR App (NReal Light Glasses)
   - For testing the app on a PC start the "DigitalTween.apk" app
   - For use on the NReal Light AR glasses, upload the "DigitalTweenPlaneDetector.apk" app onto your AR glasses and start it
3. Flask Server
   - Follow the [link](https://github.com/BMajeric/DiplomskiProjektPythonServer) for more information on the server

## Use of the Server
- To change which server contains the GPS coordinate data, modify the *serverUrl* variable in the *GPSSender.cs* and *GPSReceiver.cs* scripts inside the *Assets/Scripts* folder
### API Endpoints
1. POST /send
   - Sends the GPS coordinates from the mobile app
   - Request Body example (JSON):
     ```
     {
        "X": 45.812,
        "Z": 15.956
     }
     ```
   - Response example:
     ```
     {"message": "Data received successfully"}
     ```
2. GET /get
   - Gets the GPS coordiantes from the server (used in the NReal app)
   - Response example:
     ```
     {
        "X": 45.812,
        "Z": 15.956
     }
     ```
## Future Improvements
- Improve security
- Add real-time updates of GPS coordinates such as WebSockets instead of polling
- Touch up the UI for both applications
- Migrate to newer AR glasses for more features such as a built in GPS and better tracking
     
