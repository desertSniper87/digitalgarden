---
{"dg-publish":true,"permalink":"/android-binder/"}
---


- The Binder is Android's core [[Interprocess Communication\|Interprocess Communication]] (IPC) mechanism, enabling efficient and secure communication between different processes
- It is built on a Remote Procedure Call ([[Remote Procedure Call\|RPC]]) model, allowing a **client process to invoke methods on a remote object located in another process as if the object were local**.
- "remote service" refers to a service running within the **same application but in a different process**
- Binders are typically used through a **Service** that implements an interface defined in an [AIDL](https://developer.android.com/develop/background-work/services/aidl) file, which specifies the methods, parameters, and return values for IPC
- The Service provides the requested functionality, while the Binder facilitates **communication between the client and the service**
- A [[Android - Services\|Services]] uses Binders to communicate with a remote client.

## ICalculator.aidl

Here we see snippet of the `ICalculator.aidl` file containing the method's declaration.

```java
interface ICalculator {
    int add(int a, int b);
}
```

Next, we have a snippet of the `CalculatorService.java` file, which creates the service and implements the interface defined in the AIDL file.

```java
public class CalculatorService extends Service {
    private final ICalculator.Stub binder = new ICalculator.Stub() {
        @Override
        public int add(int a, int b) {
            return a + b;
        }

    @Override
    public IBinder onBind(Intent intent) {
        return binder;
    }
}
```

## MainActivity.java


- We now come to a snippet of **the `MainActivity.java` file connecting and binding to the remote service `CalculatorService`,** and subsequently calling its methods. `Connecting` to a service involves establishing a link with the service to communicate and interact with it, while `binding` to a service esta[]()blishes a long-lasting connection between a client (such as an Activity) and a service
- This allows the client to interact with the service, invoke its methods, and receive results synchronously.

```java
// Connecting to the remote service
private ServiceConnection serviceConnection = new ServiceConnection() {
    @Override
    public void onServiceConnected(ComponentName name, IBinder service) {
        calculatorService = ICalculator.Stub.asInterface(service);
        performCalculations();
    }
		...
};
....

// Binding to the remote service
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    Intent intent = new Intent();
    intent.setComponent(new ComponentName("com.example.calculatorservice", "com.example.calculatorservice.CalculatorService"));
    bindService(intent, serviceConnection, Context.BIND_AUTO_CREATE);
}
...

// Calling the methods
private void performCalculations() {
    if (calculatorService == null) {
        return;
    }

    try {
        int additionResult = calculatorService.add(10, 5);
      
        // Use the results as needed, e.g., display them in the UI
        // ...

    } catch (RemoteException e) {
        e.printStackTrace();
    }
}
```


- Binders are not declared in the manifest file directly, as they are a part of the Service implementation
- However, if the Service runs in a different process, the attribute `android:process` should be specified in the `AndroidManifest.xml` file.

Code: xml

```xml
<manifest ...>
    <application ...>
        <service
            android:name=".MyService"
            android:process=":remote" />
    </application>
</manifest>
```