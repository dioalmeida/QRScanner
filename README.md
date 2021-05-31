### Contributed by Diogo Almeida
Read QR Codes from Android Camera X API
* This “receipt” uses Android’s Camera X API to preview the back camera in a PreviewView, while taking advantage of Google’s MLKit to read QR Codes by having a separate thread take a “screenshot” of the PreviewView and let MLKit analyze it for QR codes.
* Supports QR_CODE, AZTEC_FORMAT(can be very easily edited to support new formats setBarCodeFormats )
* Might not show QR Code info because of the many different QR Code formats, but this is easily obtained (addOnSuccessListener of the scanner).
* Uses permissions to ask the user if the app has permissions to use the camera.
* Note #1: Permission treatment is not implemented for  older Android APIs for simplicity.
* Note #2: This code works just fine on an emulator, all you need to do is either emulate a view or assign a camera to a webcam when creating the emulator.
* Repository: https://github.com/dioalmeida/QRScanner
#### Permissions & Libraries
* Must ask for the CAMERA and RECORD_AUDIO permissions to work. 
We must add the necessary libraries to build.gradle(app)
MLKit Thread
* Uses a separate thread that runs every second and takes a screenshot of the PreviewView and scans it for codes, if it detects one then it shows in a TextView what kind of qr code it is and the info, if available.
Scan QR Codes
* Might not show QR Code info because of the many types of QR Code formats that exist and need to be parsed accordingly, but this is easily obtained because the structure is there already in the OnSuccessListener of the scanner, once we know the type it’s easy to parse the information from it.
