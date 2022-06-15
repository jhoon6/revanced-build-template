# Revanced Build
This repo template will allow you to build ReVanced using Github Actions. This will helps people who don't want to setup build environments on their machines.
By default this will build ReVanced with ALL available patches. You can modify the `build_revanced.sh` script to limit to only patches you want to use.

## Notes
- Current implementation cannot download the latest compatible versions of Youtube and Youtube Music, as APKPure either doesn't have bundled APK, or doesn't have older versions of the apps that are compatible with ReVanced.
- Under NO CIRCUMSTANCES any APKs will be uploaded to this repository to avoid DMCA.

## How to setup
1. Create a new repository using this repository as a template ([Guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)). DO NOT FORK UNLESS YOU WANT TO CONTRIBUTE TO THE REPOSITORY. Set the new repo to private if needed.
2. (Optional, Highly Recommended) Create a new keystore for signing the APKs: `keytool -genkey -keystore <keystore_name_here>.keystore -alias <key_alias> -keyalg RSA -keysize 2048 -validity 10000`
   1. Convert keystore to `base64`: `openssl base64 -A -in ./<keystore_name_here>.keystore -out ./temp.txt`
   2. Copy content of the `temp.txt` file to your repo's GitHub Actions Secrets `SIGNING_KEY`, keystore password to `KEY_STORE_PASSWORD`.
3. Download latest (compatible) APKs of Youtube and Youtube Music from APKMirror.com:
- [Youtube 17.22.36](https://www.apkmirror.com/apk/google-inc/youtube/youtube-17-22-36-release/youtube-17-22-36-2-android-apk-download/)
  - Rename to `com.google.android.youtube.apk`
- [Youtube Music 5.03.50](https://www.apkmirror.com/apk/google-inc/youtube-music/youtube-music-5-03-50-release/)
  - Choose correct version according to your device architecture
  - Rename to `com.google.android.apps.youtube.music.apk`
4. Publish a new release under tag `base` and upload the APKs to the release.
## How to build
1. Go to Actions -> All workflows:
   1. Choose `ReVanced Build` if you already setup the keystore as above
   2. Choose `ReVanced Build Autosign` if you haven't setup the keystore
2. Run the workflow
3. Download the APKs from the draft releases


