name: Build SeizureGuard APK

on:
  workflow_dispatch:
  push:
    branches:
      - main

permissions:
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Quellcode herunterladen
        uses: actions/checkout@v4

      - name: Java einrichten
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - name: Gradle einrichten
        uses: gradle/actions/setup-gradle@v4

      - name: Android SDK einrichten
        uses: android-actions/setup-android@v3

      - name: Android SDK installieren
        run: sdkmanager "platforms;android-35" "build-tools;35.0.0"

      - name: APK bauen
        run: gradle assembleDebug

      - name: APK bereitstellen
        uses: actions/upload-artifact@v4
        with:
          name: SeizureGuard-debug-APK
          path: app/build/outputs/apk/debug/*.apk
          if-no-files-found: error

### 3. Speichere die Datei

Scrolle im Editor nach unten.

1. Tippe auf **Commit changes**.
2. Bestätige mit **Commit changes**, falls du erneut gefragt wirst.

Damit wird die Workflow-Datei gespeichert. Weil der Workflow auch auf Änderungen am `main`-Branch reagiert, sollte GitHub anschließend versuchen, die App zu bauen.

### 4. Prüfe, ob der Build funktioniert

1. Öffne die Registerkarte **Actions**.
2. Tippe auf den neuesten Eintrag **Build SeizureGuard APK**.
3. Warte, bis der Lauf abgeschlossen ist.

- ✅ **Grüner Haken:** Der Build ist erfolgreich.
- ❌ **Rotes Kreuz:** Etwas muss korrigiert werden.

**Schick mir danach einen Screenshot von der Actions-Seite.** Dann helfe ich dir beim nächsten Schritt.

Noch wichtig: Ich kann den Build von hier aus nicht selbst überprüfen. Selbst bei einem erfolgreichen Build ist die App zunächst nur ein Prototyp. Sie erkennt Krampfanfälle nicht zuverlässig und darf nicht als Notfallsystem verwendet werden.
