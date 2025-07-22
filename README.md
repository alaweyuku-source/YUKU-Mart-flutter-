# YUKU-Mart-flutter-name: Build Flutter APK

on:
  push:
    branches:
      - main
      - master

jobs:
  build:
    name: Build APK
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3

      - name: Setup Flutter
        uses: subosito/flutter-action@v2
        with:
          flutter-version: '3.22.1' # Change if using another version

      - name: Install Dependencies
        run: flutter pub get

      - name: Build APK
        run: flutter build apk --release

      - name: Upload APK Artifact
        uses: actions/upload-artifact@v3
        with:
          name: YUKU-Mart-APK
          path: build/app/outputs/flutter-apk/app-release.apk
          
          
