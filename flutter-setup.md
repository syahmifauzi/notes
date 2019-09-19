# SETUP FLUTTER
1. mkdir ~/development && cd development
2. wget https://storage.googleapis.com/flutter_infra/releases/stable/linux/flutter_linux_v1.9.1+hotfix.2-stable.tar.xz
3. tar xf flutter_linux_v1.9.1+hotfix.2-stable.tar.xz
4. echo "export PATH="$PATH:$HOME/development/flutter/bin" >> ~/.bashrc
5. flutter config --no-analytics
6. flutter doctor -v

# SETUP ANDROID EMULATOR
1. mkdir ~/development/android-sdk && cd ~/development/android-sdk
2. wget https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip
3. unzip sdk-tools-linux-4333796.zip
4. wget https://dl.google.com/android/repository/platform-tools-latest-linux.zip
5. unzip platform-tools-latest-linux.zip
6. vim ~/.bashrc
  >> export ANDROID_SDK_ROOT="$HOME/development/android-sdk"
  >> export ANDROID_HOME=$ANDROID_SDK_ROOT
  >> export PATH="$PATH:$ANDROID_HOME/emulator:$ANDROID_HOME/tools/bin:$ANDROID_HOME/platform-tools"
7. sudo apt install openjdk-8-jdk openjdk-8-jre
8. touch ~/.android/repositories.cfg
9. sdkmanager "system-images;android-28;google_apis_playstore;x86_64" "platforms;android-28" "build-tools;28.0.3"
10. avdmanager -v create avd -n "Android-Pie" -k "system-images;android-28;google_apis_playstore;x86_64" -f
11. emulator -avd Android-Pie
12. flutter doctor -v

# SOURCES
1. https://flutter.dev/docs/get-started/install/linux
2. https://developer.android.com/studio#command-tools
3. https://developer.android.com/studio/releases/platform-tools.html
