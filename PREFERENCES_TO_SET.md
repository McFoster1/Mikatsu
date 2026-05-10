# Default Preferences to Set in Code

## Reader Preferences (ReaderPreferences.kt or similar):
```kotlin
defaultReadingMode = ReadingMode.PAGED_LTR  // Paged mode default
defaultFont = "serif"  // Georgia/Serif
defaultFontSize = 18  // 18sp
defaultLineSpacing = 1.6f  // 1.6x spacing
defaultTheme = ReaderTheme.DARK  // Dark theme
```

## Library Preferences (LibraryPreferences.kt):
```kotlin
defaultLibraryDisplayMode = LibraryDisplayMode.COMFORTABLE_GRID
defaultGridColumns = 3
defaultLibrarySort = LibrarySort.LAST_READ
```

## App Preferences (PreferencesHelper.kt):
```kotlin
defaultAppTheme = AppTheme.DARK  // Dark on first launch
defaultStartScreen = StartScreen.LIBRARY
```
