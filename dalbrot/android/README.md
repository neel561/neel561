# Android hardening

Templates, not yet tested against a real build.

## AndroidManifest.xml

```xml
<application
    android:allowBackup="false"
    android:fullBackupContent="@xml/backup_rules"
    android:dataExtractionRules="@xml/data_extraction_rules"
    android:networkSecurityConfig="@xml/network_security_config"
    android:usesCleartextTraffic="false">
    <activity android:name=".MainActivity" android:exported="true"> <!-- launcher only -->
```

- Request no permissions. The app needs none; do not add `INTERNET` unless a feature really needs it.
- Every other activity, service and provider: `android:exported="false"`.

## WebView (if the app wraps the HTML file)

```kotlin
webView.settings.apply {
    javaScriptEnabled = true
    domStorageEnabled = true            // the log is kept in localStorage
    allowFileAccess = false
    allowContentAccess = false
    mixedContentMode = WebSettings.MIXED_CONTENT_NEVER_ALLOW
    setGeolocationEnabled(false)
}
WebView.setWebContentsDebuggingEnabled(BuildConfig.DEBUG)
```

- Load the page with `WebViewAssetLoader` from `https://appassets.androidplatform.net/`, not from `file://`.
- In `shouldOverrideUrlLoading`, refuse every URL that is not the app's own page.
- Do not add a JavaScript bridge (`addJavascriptInterface`) unless a feature needs it.

## Release

- Enable R8 (`minifyEnabled true`) for release builds.
- Use Play App Signing and keep the upload keystore outside the repository, with an offline copy.
- Fill in the Play Console Data safety form to match the privacy policy: health data, stored on device only, not shared, not collected by the developer.
