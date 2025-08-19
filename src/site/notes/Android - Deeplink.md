---
{"dg-publish":true,"permalink":"/android-deeplink/"}
---


- A Deep Link is an Interprocess Communication ([[Inter Process Communication\|IPC]]) mechanism that allows users to **navigate directly to specific content within an app by tapping a URL found on a website, email**, or any other location where links can be placed.


- In some cases, if the app is not installed, the user is redirected to the app store to download and install it.The are two types of Deep Links
	- the `Standard Deep Link`, 
	- the `Android App Link`.

#### Standard Deep Link


- The example below demonstrates a website that provides deep links to list its computer products through the mobile app
- The source code of the website looks like this:


```html
<div>
	<p>Buy our latest PC parts.</p>
	<a href="app://myapp/products/cpu"> </a>
</div>
```


- In order for the above URL to open within the application, we must set up an [[Android Activity - Intent\|Intent]] filter in the [[AndroidManifest.xml\|AndroidManifest.xml]] file for the corresponding activity.


```xml
<activity android:name=".ProductsActivity">
    <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <data android:scheme="app"
              android:host="myapp"
              android:pathPrefix="/products/" />
    </intent-filter>
</activity>
```


- The table below provides a description of the most important elements of the above snippet.

|**Element**|**Description**|
|---|---|
|`<activity android:name=".ProductsActivity">`|Defines the activity to be launched once the link is tapped.|
|`android:scheme="app"`|Sets the protocol. It defines the `app` (can be anything) part of the URL `app://myapp/products/cpu` included in the website.|
|`android:host="myapp"`|Sets the host. It defines the `myapp` (can be anything) part of the URL `app://myapp/products/cpu` included in the website.|
|`android:pathPrefix="/products/" />`|Sets the path prefix. It defines the `/products/` part of the URL `app://myapp/products/cpu` included in the website.|


- Now that we have set up the `intent` filter properly, let's take a look at the following Java snippet to see how it handles the incoming intent.


```java
public class ProductActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_planet);

        Intent intent = getIntent();
        String action = intent.getAction();
        Uri data = intent.getData();

        if (Intent.ACTION_VIEW.equals(action) && data != null) {
            String ProductName = data.getLastPathSegment();
          
          	if (ProductName.equals("cpu")) {
            	// Do something. For example, query the database for information on this product.
            }
        }
    }
}
```


- In the above Java snippet, the `if()` statement checks if the value returned from the `data.getLastPathSegment()` method is equal to `cpu`
- The value returned from the `data.getLastPathSegment()`method is actually the `cpu` part of the URL `app://myapp/products/cpu`.


- This is how Android handles a Standard Deep Link
- While deep linking is a powerful mechanism, security risks may arise from improper implementation
- In the example above, the `android:scheme` attribute is set to `app`, and the `android:host` is set to `myapp`
- However, Android does not enforce ownership verification for custom schemes, meaning any malicious app can declare itself as the default handler for that scheme, potentially leading to security vulnerabilities
- To mitigate this risk, `Android App Links` should be used.

#### Android App Link

Assuming that the URL `https://www.myapp.com/` leads to an existing website, the deep link in it would look like this.

Code: html

```html
<div>
	<p>Buy our latest PC parts.</p>
	<a href="https://www.myapp.com/products/cpu"> </a>
</div>
```

Accordingly, the `Androidmanifest.xml` file will contain the following.

Code: xml

```xml
<activity android:name=".ProductsActivity">
    <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <data android:scheme="https"
              android:host="www.myapp.com"
              android:pathPrefix="/products/" />
    </intent-filter>
</activity>
```


- We notice that the `android:scheme` attribute is set to `https`, and the `android:host` is set to `www.myapp.com`
- In this case, if the app that handles the deep link isn't installed, the link will open in a web browser listing the products
- This is a feature added on `Android 6.0` and higher, ensuring that only the verified domain owner can handle links to that domain within their app, and other potential malicious apps won't be able to handle this link.


- On the other hand, bad programming could still lead to security issues
- Imagine an application handling the URL `https://www.myapp.com/home?uid=50&token=RLsB?19oYMAL6M5v`
- If the app doesn't verify the `uid` and `token` parameters passed in via the deep link, a malicious actor could craft their own link with different parameter values, leading to unauthorized access to another user's data
- To enhance security when using Deep Links, it is suggested to use `Android App Links` (which ensure links are verified and securely handled) instead of generic `Deep Links`
- Additionally, one should validate the input of parameters and avoid passing sensitive data through URLs.

 [Previous](https://academy.hackthebox.com/module/195/section/2217)