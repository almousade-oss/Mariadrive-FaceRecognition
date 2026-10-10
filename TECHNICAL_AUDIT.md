# Technical audit — Mariadrive Face Recognition

Status: investigation in progress. No AIX build has been claimed or released.

## Selected target
- Host project: `Mariadrive1_FACEMESH_EINGEBAUT.aia`
- Builder: MIT App Inventor
- Camera requirement: live camera
- Recognition: offline, on-device enrollment and matching

## Findings from the supplied AIA
- Screen1 contains a `FaceExtension1` component of type `FaceExtension` connected to `WebViewerGesicht1`.
- The existing FaceMesh component runs a browser-based TensorFlow.js FaceMesh model. Face landmarks/mesh are not a biometric identity embedding and cannot, by themselves, identify a person by name.
- The AIA does not appear to contain a standard MIT App Inventor `Camera` component; the existing face preview is driven through the WebViewer-based FaceExtension.
- A separate Android sample project is available in the working files. It uses CameraX for preview/frame analysis, ML Kit for face detection, and a MobileFaceNet TensorFlow Lite model for face embeddings. It is a reference implementation, not an App Inventor AIX.

## Required implementation
A working AIX needs a native live camera preview/frame analyzer, face detection and alignment, MobileFaceNet embedding inference, similarity matching, and private local persistence for enrolled embeddings. Registration/deletion must be explicitly invoked from App Inventor blocks. A PIN can guard those operations but should not be hardcoded into the extension.

## Build and test status
Not yet built or device-tested. A successful build requires a compatible App Inventor extension toolchain and dependency packaging for CameraX, ML Kit, and TensorFlow Lite. The extension must not be described as working until it imports into MIT App Inventor, compiles into an APK, runs on a real Android device, and passes registration/matching/offline tests.

## Privacy
Do not commit face photos, face embeddings, PINs, or other personal biometric data to this repository. Enrolled profiles should stay in private app storage on the device.
