# Flash Chat

Flash Chat is a cross-platform real-time messaging app built with Flutter and Firebase. Users can create an account or sign in with email and password, then exchange messages in a shared chat room.

## Features

- Email/password registration and sign-in with Firebase Authentication
- A shared chat room backed by Cloud Firestore
- Live message updates and sender labels
- Flutter targets configured for Android, iOS, macOS, web, and Windows

## Requirements

- [Flutter](https://docs.flutter.dev/get-started/install) with Dart
- The platform toolchain for the target you want to run (for example, Android Studio for Android or Xcode for iOS and macOS)
- A Firebase project with Email/Password Authentication and Cloud Firestore enabled

## Getting started

1. Clone this repository and enter the project directory.
2. Fetch the Flutter dependencies:

   ```sh
   flutter pub get
   ```

3. Make sure Firebase is configured for your target platform (see [Firebase setup](#firebase-setup)).
4. Start the app on a connected device, emulator, or supported desktop/browser target:

   ```sh
   flutter run
   ```

To see available run targets, use `flutter devices`.

## Firebase setup

The checked-in Firebase configuration is generated for the `flash-chat-3ccc3` project. To use that project, enable **Email/Password** under Firebase Authentication, create a Cloud Firestore database, and ensure its security rules permit the signed-in users and operations needed by the app.

To connect the app to your own Firebase project:

1. Create a Firebase project and register a Firebase app for each platform you plan to run.
2. Enable **Email/Password** in Firebase Authentication and create a Cloud Firestore database.
3. Install the [Firebase CLI](https://firebase.google.com/docs/cli), then install and authenticate the [FlutterFire CLI](https://firebase.google.com/docs/flutter/setup):

   ```sh
   dart pub global activate flutterfire_cli
   firebase login
   ```

4. From the project directory, generate configuration for your Firebase project:

   ```sh
   flutterfire configure
   ```

   Select Android, iOS, macOS, web, and/or Windows as appropriate. This updates `lib/firebase_options.dart` and the platform-specific Firebase configuration files.
5. Review your Firestore security rules before running the app. The chat reads and writes documents in the `messages` collection; each message currently contains `text` and `sender` fields. Do not use open/test rules in a deployed app.

Firebase Authentication and Firestore must both be configured for the same project. Linux is not currently configured in `lib/firebase_options.dart`.

## Usage

Launch the app and choose **Register** to create an account or **Log In** to use an existing account. After authentication, send messages from the chat input. The close icon in the chat app bar signs out and returns to the previous screen.

## Development

Run the static analyzer from the project root:

```sh
flutter analyze
```

## Built with

- [Flutter](https://flutter.dev/)
- [Firebase Authentication](https://firebase.google.com/docs/auth)
- [Cloud Firestore](https://firebase.google.com/docs/firestore)
