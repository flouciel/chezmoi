1. Root AVD https://gitlab.com/newbit/rootAVD
If need test biometric, AVD does supported. Genymotion free does not support

2. Install AVD without android studio 

- Move content of `cmdline-tools` to a folder named `latest` inside `cmdline-tools` . e.g. Final path for bin becomes: `/Users/user/Library/Android/sdk/cmdline-tools/latest/bin`
add to .zshrc 

```
sdkmanager --list
sdkmanager platform-tools emulator
sdkmanager "system-images;android-34;google_apis_playstore;arm64-v8a" "platforms;android-34"

# using `android-34` here which is SDK for Android 14 
avdmanager create avd --name 'pixel' --package "system-images;android-34;google_apis_playstore;arm64-v8a" -d pixel
emulator -avd ${DeviceName} -no-snapshot-load
```

3. frida 16.6.6

```
ensure the match version
android is arm64.xz

adb root # might be required 
adb push frida-server /data/local/tmp/ 
adb shell "chmod 755 /data/local/tmp/frida-server" 
adb shell "/data/local/tmp/frida-server &"


Kill Frida process
ps -e | grep frida-server
kill -9 pid

Start Frida process
/data/local/tmp/frida-server & 

If the pid of process that wanna hook
com.example.dev

frida -U -f com.example.dev -l script.js
```

4. Flutter SSL pinning
frida -U -f com.example.dev -l ssl-bypass.js
change the IP

https://github.com/hackcatml/frida-flutterproxy

5. talsec freerasp bypass
frida -U -f com.example.dev -l talsec-root.js
https://codeshare.frida.re/@muhammadhikmahhusnuzon/bypass-talsec-rasp-and-root-detection/

6. Biometric bypasss
frida -U -f com.example.dev -l universal-bio-bypass.js
