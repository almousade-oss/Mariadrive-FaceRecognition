# Mariadrive Face Recognition (MIT App Inventor AIX)

This repository is for developing an offline face-recognition extension for MIT App Inventor / Kodular.

## Required public blocks

- `Initialize` — prepare the on-device recognition model and local storage.
- `RegisterFace(name, imagePath)` — enroll a person from a locally captured image.
- `RecognizeFace(imagePath)` — compare a captured image with locally enrolled profiles and report the best match / unknown.
- `DeleteFace(name)` — remove an enrolled profile.
- `GetRegisteredFaces` — list profile names.
- `SetAdminPIN(pin)` — configure protection for enrollment and deletion.

## Privacy requirements

- No personal face images or user-specific profiles are to be embedded in the AIX package.
- Enrolled profiles must be stored on the device, not uploaded to a server.
- Recognition should work offline after installation.

## Build status

This repository has been created as the work area. The AIX is **not yet built or tested**. Do not use it as a finished extension until a real build and device test have passed.

## Technical note

Face landmark detection (FaceMesh) is not identity recognition. The implementation must use a face-embedding model and compare embeddings from captured images. Any external model/library dependency must be packaged compatibly with MIT App Inventor's extension format.
