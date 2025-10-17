1. Root Android
Magisk

2. Root AVD https://gitlab.com/newbit/rootAVD
If need test biometric, AVD does supported. Genymotion free does not support

Install AVD without android studio 

install the AVD without android studio and finger print 

1. Go to Official [Android Studio download page](https://developer.android.com/studio#command-line-tools-only).
2. Scroll down to "Command line tools only" section.
3. 1. Move content of `cmdline-tools` to a folder named `latest` inside `cmdline-tools` . e.g. Final path for bin becomes: `/Users/4azy/Library/Android/sdk/cmdline-tools/latest/bin`
add to .zshrc 

```
sdkmanager --list
sdkmanager platform-tools emulator
sdkmanager "system-images;android-34;google_apis_playstore;arm64-v8a" "platforms;android-34"

# using `android-34` here which is SDK for Android 14 
avdmanager create avd --name 'pixel' --package "system-images;android-34;google_apis_playstore;arm64-v8a" -d pixel
emulator -avd ${DeviceName} -no-snapshot-load
```


```
$ANDROID_HOME/emulator/emulator -avd pixel -no-snapshot-load


4. palera1n jailbreak iOS

```
palera1n -l

ssh root@127.0.0.1 -o "StrictHostKeyChecking=no" -o "UserKnownHostsFile=/dev/null" -o "ProxyCommand=inetcat 44"
```

If cannot use `sudo` , edit file `ssh_config`
``` bash
find / -name sshd_config -print
use vim <sshconffig>
PasswordAuthentication yes

--------------------
then with sudo
find / -name sudo -print

Create a profile in ./
vim .profile
export PATH="/private/preboot/[digit_string]/jb-xxxxxx/procursus/usr/bin:$PATH"
source .profile
```


5. frida 16.6.6

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


6. Flutter SSL pinning
frida -U -f com.example.dev -l ssl-bypass.js
change the IP

https://github.com/hackcatml/frida-flutterproxy

7. talsec freerasp bypass
frida -U -f com.example.dev -l talsec-root.js
https://codeshare.frida.re/@muhammadhikmahhusnuzon/bypass-talsec-rasp-and-root-detection/

8. Biometric bypasss
frida -U -f com.example.dev -l universal-bio-bypass.js
