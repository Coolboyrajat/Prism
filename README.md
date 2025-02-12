## Change_logs

### Telegram/TMessagesProj/src/main/java/org/telegram/ui/Components/SwipeGestureSettingsView.java

34.    public static final int SWIPE_GESTURE_ADVANCED = 6;

45.    private boolean isCustomizeMode = false;
46.
47.    private int[] customAdvancedColors = new int[] {
48.        Theme.key_chats_muteBackground, 
49.        Theme.key_chats_readBackground,
50.        Theme.key_chats_pinBackground,
51.        Theme.key_dialogSwipeRemove,
52.	   Theme.key_chats_archivePinBackground
53.    };

55.    String[] strings = new String[7];
56.    int[][] backgroundKeys = new int[7][]; 
57.    RLottieDrawable[] icons = new RLottieDrawable[7];  

78.    strings[SWIPE_GESTURE_ADVANCED] = LocaleController.getString(R.string.SwipeSettingsAdvanced);
79.
80.    backgroundKeys[SWIPE_GESTURE_PIN] = new int[] {Theme.key_chats_pinBackground};
81.    backgroundKeys[SWIPE_GESTURE_READ] = new int[] {Theme.key_chats_readBackground};
82.    backgroundKeys[SWIPE_GESTURE_ARCHIVE] = new int[] {Theme.key_chats_archiveBackground};
83.    backgroundKeys[SWIPE_GESTURE_MUTE] = new int[] {Theme.key_chats_muteBackground};
84.    backgroundKeys[SWIPE_GESTURE_DELETE] = new int[] {Theme.key_dialogSwipeRemove};
85.    backgroundKeys[SWIPE_GESTURE_FOLDERS] = new int[] {Theme.key_chats_archivePinBackground};
86.    backgroundKeys[SWIPE_GESTURE_ADVANCED] = new int[] {
            Theme.key_chats_muteBackground, 
            Theme.key_chats_readBackground, 
            Theme.key_chats_pinBackground 
        };

157.        public void setCustomizeMode(boolean isCustomizeMode) {
158.            this.isCustomizeMode = isCustomizeMode;
159.    
160.            if (isCustomizeMode) {
161.                    backgroundKeys[SWIPE_GESTURE_ADVANCED] = customAdvancedColors;
162.            } else {
163.                backgroundKeys[SWIPE_GESTURE_ADVANCED] = new int[] {
164.                    Theme.key_chats_muteBackground, 
165.                    Theme.key_chats_readBackground, 
166.                    Theme.key_chats_pinBackground
167.                };
168.            }
169.
170.            invalidate();
171.        }
172.
173.    public void updateCustomAdvancedColors(int[] newColors) {
174.        customAdvancedColors = newColors;
175.
176.        if (isCustomizeMode) {
177.            backgroundKeys[SWIPE_GESTURE_ADVANCED] = customAdvancedColors;
178.            invalidate();
179.        }
180.    }


255.    int color;
256.    if (picker.getValue() == SWIPE_GESTURE_ADVANCED) {
257.            int conditionIndex = getConditionIndex();
258.            color = Theme.getColor(backgroundKeys[SWIPE_GESTURE_ADVANCED][conditionIndex]);
259.    } else if (currentColorKey < 0) {...}


405.    private int getConditionIndex() {
        if (/* condition for SWIPE_GESTURE_MUTE */) {
            return 0;
        } else if (/* condition for SWIPE_GESTURE_PIN */) {
            return 1;
        } else if (/* condition for SWIPE_GESTURE_READ */) {
            return 2;
        }
        return 0; // Default to the first color
    }




### Telegram/TMessagesProj/src/main/java/org/telegram/messenger/SharedConfig.java

### Telegram/TMessagesProj/src/main/java/org/telegram/messenger/MessagesController.java

### Telegram/TMessagesProj/src/main/java/org/telegram/messenger/ChatObject.java

### Telegram/TMessagesProj/src/main/java/org/telegram/ui/SwipeGestureSettingsActivity.java (new File created)

### Telegram/TMessagesProj/src/main/java/org/telegram/Components/ChatListView.java

### Telegram/TMessagesProj/src/main/java/org/telegram/ui/Theme.java

### Telegram/TMessagesProj/src/main/res/values/strings.xml

### Telegram/TMessagesProj/src/main/res/values/colors.xml


## Telegram messenger for Android

[Telegram](https://telegram.org) is a messaging app with a focus on speed and security. It’s superfast, simple and free.
This repo contains the official source code for [Telegram App for Android](https://play.google.com/store/apps/details?id=org.telegram.messenger).

## Creating your Telegram Application

We welcome all developers to use our API and source code to create applications on our platform.
There are several things we require from **all developers** for the moment.

1. [**Obtain your own api_id**](https://core.telegram.org/api/obtaining_api_id) for your application.
2. Please **do not** use the name Telegram for your app — or make sure your users understand that it is unofficial.
3. Kindly **do not** use our standard logo (white paper plane in a blue circle) as your app's logo.
3. Please study our [**security guidelines**](https://core.telegram.org/mtproto/security_guidelines) and take good care of your users' data and privacy.
4. Please remember to publish **your** code too in order to comply with the licences.

### API, Protocol documentation

Telegram API manuals: https://core.telegram.org/api

MTproto protocol manuals: https://core.telegram.org/mtproto

### Compilation Guide

**Note**: In order to support [reproducible builds](https://core.telegram.org/reproducible-builds), this repo contains dummy release.keystore,  google-services.json and filled variables inside BuildVars.java. Before publishing your own APKs please make sure to replace all these files with your own.

You will require Android Studio 3.4, Android NDK rev. 20 and Android SDK 8.1

1. Download the Telegram source code from https://github.com/DrKLO/Telegram ( git clone https://github.com/DrKLO/Telegram.git )
2. Copy your release.keystore into TMessagesProj/config
3. Fill out RELEASE_KEY_PASSWORD, RELEASE_KEY_ALIAS, RELEASE_STORE_PASSWORD in gradle.properties to access your  release.keystore
4.  Go to https://console.firebase.google.com/, create two android apps with application IDs org.telegram.messenger and org.telegram.messenger.beta, turn on firebase messaging and download google-services.json, which should be copied to the same folder as TMessagesProj.
5. Open the project in the Studio (note that it should be opened, NOT imported).
6. Fill out values in TMessagesProj/src/main/java/org/telegram/messenger/BuildVars.java – there’s a link for each of the variables showing where and which data to obtain.
7. You are ready to compile Telegram.

### Localization

We moved all translations to https://translations.telegram.org/en/android/. Please use it.
