# NutriBite - Food & Drink Assistant

NutriBite is a .NET MAUI cross-platform application designed as a course project for food and drink nutrition tracking. It allows users to record meals, view nutritional summaries, and demonstrates the use of mobile hardware features such as camera, location, text-to-speech, vibration, and haptic feedback.

## Features

- **Food/Drink List** – Browse, search by name/category/tags, and view details.
- **Add New Record** – Form with validation for required fields and numeric nutrition values.
- **Nutrition Detail Page** – Read summary aloud, trigger vibration reminder.
- **Hardware Demo Page** – Capture food photo with camera, get current location, text-to-speech help, haptic feedback and vibration.
- **Accessibility Support** – Large text mode, semantic properties, screen reader announcements.
- **Theme Switching** – Light / Dark / System theme.
- **Mock API Integration** – Optionally connect to a mockapi.io endpoint for remote data; falls back to local data when offline or not configured.

## Tech Stack

- **.NET 9** + **.NET MAUI**
- Supported platforms: Android, iOS, Mac Catalyst, Windows
- XAML for UI
- Services: `FoodCatalogService`, `SpeechService`, `AccessibilityService`
- Hardware APIs: `MediaPicker`, `Geolocation`, `TextToSpeech`, `Vibration`, `HapticFeedback`

## Requirements

- Visual Studio 2022 (17.8 or later) with **.NET MAUI workload** installed
- Android SDK (for Android builds) or Windows 10/11 (for Windows Machine target)
- Optional: a mockapi.io endpoint (see Configuration)

## Getting Started

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd FoodDrinkApp
2. Open the project
Open FoodDrinkApp.csproj or FoodDrinkApp.sln in Visual Studio.

3. Restore NuGet packages
Right-click the solution → Restore NuGet Packages.

4. Build and run
For Windows (recommended for easy testing):

In Visual Studio toolbar, set the debug target to Windows Machine.

Press F5.

For Android:

Set debug target to an Android emulator or a physical device.

Ensure hardware acceleration is enabled for emulator performance.

Build and deploy.

Configuration (Optional Mock API)
By default the app uses local in-memory data. To connect to a mock API:

Create an endpoint on mockapi.io (resource: FoodItem).

Open Services/MockApiConfig.cs and set the EndpointUrl constant:

csharp
public const string EndpointUrl = "https://your-mockapi-url/api/v1/foods";
Rebuild the app – it will now read/write data from the remote API.

Project Structure
text
FoodDrinkApp/
├── Models/
│   └── FoodItem.cs
├── Services/
│   ├── AccessibilityService.cs
│   ├── FoodCatalogService.cs
│   ├── MockApiConfig.cs
│   └── SpeechService.cs
├── Pages/
│   ├── MainPage.xaml/.cs
│   ├── AddItemPage.xaml/.cs
│   ├── FoodDetailPage.xaml/.cs
│   ├── HardwarePage.xaml/.cs
│   └── SettingsPage.xaml/.cs
├── App.xaml/.cs
├── AppShell.xaml/.cs
├── MauiProgram.cs
├── Platforms/
│   ├── Android/
│   │   ├── AndroidManifest.xml
│   │   └── ...
│   ├── iOS/
│   ├── MacCatalyst/
│   └── Windows/
└── Resources/
    ├── Styles/
    ├── Fonts/
    └── Images/
Hardware Features Demo
Feature	Page	Required Permission
Camera (take photo)	HardwarePage	CAMERA
Location (get current)	HardwarePage	ACCESS_FINE_LOCATION
Text-to-speech	FoodDetailPage / HardwarePage	None (uses TTS engine)
Vibration	FoodDetailPage / HardwarePage	VIBRATE
Haptic feedback	HardwarePage	None (system feedback)
On Android 11+, the manifest includes a <queries> element to enable camera intent detection.

Screenshots (suggested)
You can add screenshots of the main list, add form, detail page, and hardware demo.

Known Issues & Workarounds
Android emulator camera error: Ensure your emulator has a camera configured (use webcam) and the manifest includes the <queries> block as shown in this project.

Build error with XML encoding: If you see "root level data invalid", make sure all .xaml and .xml files are saved as UTF-8 without BOM.

License
This project is for educational purposes. Feel free to use and modify for your own learning.

Credits
Developed as a .NET MAUI course project.