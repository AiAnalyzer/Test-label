# Peridot Label Tester

Small Android Bluetooth Classic / TSPL test app for a Peridot P80-style label printer.

## Fixed media
- Width: 45 mm
- Height: 13.9 mm
- Gap: 3 mm
- Assumed resolution: 203 dpi (about 8 dots/mm)

## What it tests
- Bluetooth SPP connection
- GAP mode
- GAPDETECT
- HOME
- FORMFEED
- FEED forward
- BACKFEED reverse
- BACKUP reverse for older TSPL printers
- DIRECTION 0 / 1 print orientation
- OFFSET tear/cutter position
- Raw TSPL commands

## Build with GitHub Actions
1. Create a new GitHub repository.
2. Upload the complete contents of this project.
3. Commit to `main`.
4. Open **Actions**.
5. Select **Build Android APK**.
6. Click **Run workflow**, or simply push a commit.
7. Open the completed workflow run.
8. Under **Artifacts**, download `PeridotLabelTester-debug`.
9. Unzip the artifact and install `app-debug.apk`.

Android may ask you to allow installation from your browser/files app.

## First printer test
1. Pair the printer in Android Bluetooth settings.
2. Open the app.
3. Tap **CONNECT BLUETOOTH** and choose the printer.
4. Tap **SET 45×13.9 + GAP 3**.
5. Tap **CALIBRATE GAP**.
6. Tap **HOME TO LABEL ORIGIN**.
7. Tap **FEED EXACTLY 1 LABEL** several times. It should stop consistently at each label boundary.
8. Test **FWD 1 mm**.
9. Test **BACK 1 mm**. If unsupported, try **BACKUP 5 mm (older TSPL test)**.
10. Tap **PRINT TEST — DIRECTION 0**.
11. If the label is presented too far/short at the tear edge, try small OFFSET values.

## Important
Start with small reverse/offset values. Incorrect backfeed can wrinkle or jam media.
`DIRECTION` changes print orientation. It does not by itself solve cutter/tear positioning.
