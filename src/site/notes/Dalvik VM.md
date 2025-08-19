---
{"dg-publish":true,"permalink":"/dalvik-vm/"}
---

- The Dalvik Virtual Machine (DVM) was developed by Google and introduced with the first version of Android in 2008
- Android applications written in [[java/Java\|Java]] or [[Kotlin\|Kotlin]] are compiled into [[java/Java\|Java]] [[bytecode\|bytecode]] and then transformed into **Dalvik bytecode**, packaged in .dex ([[Dalvik Executable\|Dalvik Executable]]) or .odex (Optimized Dalvik Executable) file formats
- **Unlike the Java Virtual Machine (JVM), which is stack-based, the Dalvik VM is a register-based virtual machine**
- This architectural difference allows for more efficient execution on devices with limited CPU and memory resources, which is ideal for mobile environments.

- Dalvik was the default runtime environment in Android versions prior to API level 21 (Lollipop)
- It was eventually replaced by the Android Runtime (ART), which was introduced as a preview in Android 4.4 (KitKat) and became the default in Android 5.0
- ART maintains compatibility by using the same .dex bytecode format as Dalvik, but differs significantly in its execution model
- While Dalvik used Just-in-Time (JIT) compilation, ART initially used Ahead-of-Time (AOT) compilation — compiling bytecode into native machine code at install time, resulting in faster startup and improved performance
- In later Android versions, ART evolved to include hybrid JIT + AOT and Profile-Guided Optimizations (PGO), further enhancing runtime efficiency and battery performance.