---
{"dg-publish":true,"permalink":"/android-manifest-xml/"}
---

- uses-sdk
- uses-permission
- application
	- activity
		- [[MainActivity\|MainActivity]]



![](https://127bytes.wordpress.com/wp-content/uploads/2010/02/androidmanifest1.png)


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/android-activity/#declaring-activities-in-android-manifest-xml" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## Declaring activities in [[AndroidManifest.xml\|AndroidManifest.xml]]

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">

        <!-- Declare your Activity here -->
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- Declare other Activities if needed -->
        <!-- <activity android:name=".AnotherActivity" /> -->

    </application>

</manifest>
```
- In the above snippet
	 - the `android.intent.action.MAIN` action indicates that the `MainActivity` is the entry point of the app
- This means it is the first Activity launched when the app starts
- This action is typically used for the home screen of an app
- While the activity name `MainActivity` is usually used as an entry point in Android applications
	 - this name can be changed
- Identifying the entry point of an application is very important during penetration testing since testers can better understand the application's:
	 - flow
	 - functionality
	 - overall structure
	 - discovery of possible attack surfaces 
	 - eventually identification of potential vulnerabilities and weaknesses
- The second property
	 - `android.intent.category.LAUNCHER` tells the Android system that this Activity should be listed in the system's app launcher
- So when the user taps on the application's icon in the launcher
	 - this Activity should be started.

</div></div>
