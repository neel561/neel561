# Dalbrot security kit

Security files for [Dalbrot](https://claude.ai/code/artifact/e4ddd224-8040-4bf9-bd14-52c9444c859f), a calorie and protein tracker.
The app itself is a single HTML file and is **not** in this repository. Move this folder into the app's own (private) repository once it has one.

| File | Use it when |
|---|---|
| `SECURITY.md` | Always. Tells people how to report a vulnerability. |
| `.gitignore` | The app gets its own repository. Keeps signing keys and secrets out of git. |
| `hosting/_headers` | The HTML file is hosted on your own domain (Netlify, Cloudflare Pages). Not needed on claude.ai. |
| `android/network_security_config.xml` | Building the Android app. Blocks all unencrypted traffic. |
| `android/data_extraction_rules.xml`, `android/backup_rules.xml` | Building the Android app. Keeps health data out of cloud backup and device transfer, as the privacy policy promises. |
| `android/README.md` | Building the Android app. Manifest and WebView settings to apply. |

The Android files are templates. They have not been built or tested against a real Android project.
