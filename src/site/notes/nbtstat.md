---
{"dg-publish":true,"permalink":"/nbtstat/"}
---

**nbtstat** is a command-line tool in Windows used to display network statistics related to the NetBIOS over TCP/IP (NBT) protocol. It provides information about the network connections, including NetBIOS name resolution and the status of remote systems.

  

Here’s what **nbtstat** can help you with:

  

### **Key Features:**

1. **Display [[Netbios\|Netbios]] Name Table:**
    
    - It shows a list of the NetBIOS names that the system is currently using and their corresponding IP addresses. This can be helpful for troubleshooting network issues and ensuring correct name resolution.
        
    
    Example:
    

```
nbtstat -n
```

1. This command displays the NetBIOS name table of the local computer.
    
2. **View Remote Machine’s NetBIOS Information:**
    
    - You can use nbtstat to query the NetBIOS information of remote systems by specifying the IP address.
        
    
    Example:
    

```
nbtstat -A <IP address>
```

2. This displays the NetBIOS name table for the machine at the specified IP address.
    
3. **NetBIOS Name Resolution:**
    
    - nbtstat can help resolve NetBIOS names, providing useful information when troubleshooting NetBIOS-related issues.
        
    
    Example:
    

```
nbtstat -R
```

3. This command purges the NetBIOS name cache and reloads it from the LMHOSTS file.
    
4. **Check for Name Conflicts:**
    
    - You can use nbtstat to see if there are any conflicts between local NetBIOS names on your network.
        
    
    Example:
    

```
nbtstat -c
```

4. This displays the contents of the NetBIOS name cache, where you can check for potential conflicts.
    
5. **Display Statistics:**
    
    - If you want to check statistics related to the NBT session, you can use the following command.
        
    
    Example:
    

```
nbtstat -s
```

5. This displays the NetBIOS session statistics.
    
6. **Clear Cache:**
    
    - If your local NetBIOS cache is outdated or causing issues, you can clear it.
        
    
    Example:
    

```
nbtstat -R
```

  

  

### **Common Commands:**

- **List local NetBIOS names**:
    

```
nbtstat -n
```

-   
    
- **Display NetBIOS name cache**:
    

```
nbtstat -c
```

-   
    
- **View information for a remote machine** (using the IP address):
    

```
nbtstat -A <IP address>
```

-   
    
- **List NetBIOS sessions**:
    

```
nbtstat -s
```

  

  

nbtstat is mostly used in troubleshooting, especially when dealing with legacy Windows networking or mixed environments using both TCP/IP and NetBIOS.

  

Is there a specific **nbtstat** function you want to dive deeper into or troubleshoot?