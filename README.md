<p align="center">
  <img alt="Logon showcase gif" src="/assets/icon.png" width="100"/>
</p>
<h1 align="center">Ironchip</h1>

<p align="center" back>
    <a href="https://www.microsoft.com/software-download/">
    <img alt="Latest release" src="https://img.shields.io/badge/Windows-0078D6?logo=windows"/>
  </a>
  
  <a href="https://github.com/Ironchip-Security/Ironchip-Windows/releases/latest">
    <img alt="Latest release" src="https://img.shields.io/github/v/release/Ironchip-Security/Ironchip-Windows?color=green"/>
  </a>
  
  <a href="https://github.com/Ironchip-Security/Ironchip-Windows/releases/latest">
    <img alt="Release date" src="https://img.shields.io/github/release-date/Ironchip-Security/Ironchip-Windows?color=orange"/>
  </a>
</p>

## IDENTITY PROTECTION

Elevate your cybersecurity strategy with Ironchip Identity Platform, designed to bring the power of Multi-Factor Authentication (MFA) to your desktop computing environment. [Know more](https://www.ironchip.com/en/mobileless-authentication).

**Role-based privilege management:**
Set different user privileges. Prevents unauthorized users from accessing the rest of the system and misusing information, mitigating malicious users.

**Restrict access from unauthorized places:**
Generate enabled access from authorized areas and take your security to the next level.

**Supervision of accesses in real time:**
Check user activity, view access on a timeline, get reports and download them for full control.

**Intrusion detection system (IDS):**
Location-based reporting system to alert of sim swapping, phishing, device switching, etc.

<p align="center">
 <a href="https://www.youtube.com/watch?v=G-rr6BzcQZ0"> 
  <img alt="Logon showcase gif" src="./assets/showcase-logon.gif" alt="animated" width="550"/>
 </a>
</p>

## Download

Download the latest installer (`.msi`) version from [Release](https://github.com/Ironchip-Security/Ironchip-Windows/releases) or [Nexus](https://nexus6.kydom.net/#browse/browse:Ironchip_Windows_Logon).

## Logon

### What it is
Logon is a custom Windows credential provider designed by [Ironchip](https://www.ironchip.com/) to bring the power of Multi-Factor Authentication (MFA) to your desktop computing environment.

**Cached Passwords:**
Our simplified access can enhance user experience, making it more convenient and user-friendly. This is especially valuable in a work or personal environment where you're required to log in to various systems multiple times a day.

**Extra Layer:**
MFA adds an extra layer of protection, requiring multiple forms of authentication, such as a password and a one-time code or push notification. 

**Improved Compliance:**
MFA helps organizations meet compliance requirements and security standards by implementing robust authentication methods.

### Installing process

To install the Ironchip Authenticator into your device:
 - Run the downloaded installer. This will open the installer stepper:
   <p align="center">
     <img alt="Installer first page" src="./assets/first-view.png" width="350"/>
   </p>
 - Follow the installation steps until you arrive to the **Component Selection View**. To have the ironchip windows logon installed, the **Ironchip Windows Logon** must be `enabled`.

   > In case you want to have available the possibility to log without internet connection, make sure to `enable` **Offline** feature.
   
   > In case you want to have available the possibility to cache the password for better user experience, make sure to `enable` **Remember Credentials** feature.

   <p align="center">
     <img alt="Installer components view" src="./assets/components-view-logon.png" width="350"/>
   </p>

 - Continue to the following page, where you can change the target host and the desired proxy selection:
   
   > The host for **Production** environment: `https://api.ironchip.com`.\
   The host for **Testing** environment: `https://testing.api.ironchip.com`.
   <p align="center">
     <img alt="Installer host view" src="./assets/host-view.png" width="350"/>
   </p>

 - Continue to the following page, where you must insert the target **ApiKey** :
    > The **ApiKey** can be copied or download when [generating the application](https://knowledge.ironchip.com/en/create-mfa-application-on-ironchip) from the [Dashboard](https://app.ironchip.com/).
   <p align="center">
     <img alt="Installer apiKey view" src="./assets/apikey-view.png" width="350"/>
   </p>

 - Once the installation process is finished. All you need to do is for an administrator to [give access](https://knowledge.ironchip.com/en/windows-logon) from the [Dashboard](https://app.ironchip.com/).
 > If the **Offline** feature is enabled and the user want to use it, they need to [follow the steps](https://knowledge.ironchip.com/en/user-manual-indentity#offline) to generate the `Time-based one-time password`.

### Disable default credential provider

In order to force user to use **Ironchip Credential Provider**, the default **Windows Credential Provider** must be disabled.

> The paths may vary depending on the language

#### Steps:
- Now get the **GUID** of the Windows Credential Provider. Normally it's `{60b78e88-ead8-445c-9cfd-0b87f74ea6cd}` but you can check it on the registry under the path `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Authentication\Credential Providers\{60b78e88-ead8-445c-9cfd-0b87f74ea6cd}`

<p align="center">
  <img alt="Logon showcase gif" src="./assets/registry-provider.png" width="250"/>
</p>

- Use the key shortcut `⊞ Win` + `R` and paste `gpedit.msc`

<p align="center">
  <img alt="Logon showcase gif" src="./assets/run-view.png" width="250"/>
</p>

- Then inside the **Local Group Policy Editor** go to `Local Computer Policy > Computer Configuration > Administrative Templates > System > Logon > Exclude Credential Providers`

<p align="center">
  <img alt="Logon showcase gif" src="./assets/local-policy.png" width="250"/>
</p>

- Enable the exclusion rule and paste the GUID of the Windows Password Credential Provider into the field. Then press apply.

<p align="center">
  <img alt="Logon showcase gif" src="./assets/apply-rule.png" width="250"/>
</p>

### Autologon Whitelist

In order to prevent user interact in authentication during autologon on computer start up, there are 2 possibilities

**Whitelist user:**
Adding user to Registry key `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Ironchip\Logon\Whitelist`. This will whitelist autologon user for any authentication

**Whitelist user just on autologon:**
Setting AutoLogonSkip to 1 in `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Ironchip\Logon` this will whitelist autologon user for any authentication only during autologon


## Desktop Application

### What it is

Identity management must be nowadays considered as an essential component for security in organizations. To address this need, Ironchip provides organizations with the scalability and security necessary to offer their users a consistent experience and a reduced risk of vulnerabilities.

**Get a notification on your device**
Communication for authentication is done over a double-encrypted channel which implements a TLS plus asymmetric elliptic key encryption.


### Installing process

To install the Ironchip Authenticator into your device:
 - Run the downloaded installer. This will open the installer stepper:
   <p align="center">
     <img alt="Installer first view" src="./assets/first-view.png" width="350"/>
   </p>
 - Follow the installation steps until you arrive to the **Component Selection View**. To have the desktop application installed, the **Ironchip Windows Authenticator** must be `enabled`.

   > I case you want to have the **USB support** feature `enabled`, make sure to **enable USB support**.

   <p align="center">
     <img alt="Installer components view" src="./assets/components-view-auth.png" width="350"/>
   </p>

 - Once the installation process is finished. All you need to do is [enroll the device](https://knowledge.ironchip.com/en/aplicaci%C3%B3n-de-escritorio#registro), and you are good to go.

### Installing process using CLI
The installation of Ironchip Windows using commands (cmd) with the program "msiexec.exe." Here’s a basic tutorial on how to do it:

1) Open the command line (cmd):
    - Press Win + R to open the "Run" dialog.
    - Type "cmd" and press Enter.
2) Locate the MSI file:
    - Make sure you have the MSI file you want to install in an accessible location from the command line.
3) Execute the msiexec command:
    - The basic command to install an MSI file is as follows:

    ```bash
    msiexec.exe /i Path\To\IronchipWindowsLogon.msi IRONCHIP_APIKEY="$apikey" /q
    ```

    Replace "Path\To\IronchipWindowsLogon.msi" with the full path and name of the MSI file. The APIKEY will only be necessary if you want to install the Windows Logon functionality, which can be obtained through the following procedure:
    https://docs.ironchip.com/en/windows-logon

    Additionally, if you want a more customized installation, the installer has optional parameters:
    - Customization of the environment -> To do this, the IRONCHIP_HOST property is used to customize the environment you want to target (by default "https://api.ironchip.com").
    - Customization of the features to install -> To do this, the ADDLOCAL property is used to customize the functionalities you want to install. In this case, we have several options (LogonFeature, OfflineFeature, AuthenticatorFeature, USBFeature, CachedPasswordsFeature) that can be combined.

    Example 1: Installation of the desktop application functionality and USB functionality
    ```bash
    msiexec.exe /i IronchipWindowsLogon.msi IRONCHIP_APIKEY="$apikey" IRONCHIP_HOST="https://api.ironchip.com" ADDLOCAL="AuthenticatorFeature,USBFeature" /q
    ```

    Example 2: Installation of the desktop application functionality without the USB functionality
    ```bash
    msiexec.exe /i IronchipWindowsLogon.msi IRONCHIP_APIKEY="$apikey" IRONCHIP_HOST="https://api.ironchip.com" ADDLOCAL="AuthenticatorFeature" /q
    ```

    Example 3: Installation of the Windows Logon online and offline with cache
    ```bash
    msiexec.exe /i IronchipWindowsLogon.msi IRONCHIP_APIKEY="$apikey" IRONCHIP_HOST="https://api.ironchip.com" IRONCHIP_APIKEY="$apikey" ADDLOCAL="LogonFeature,OfflineFeature,CachedPasswordsFeature" /q
    ```

    Example 4: Installation of the Windows Logon only online
    ```bash
    msiexec.exe /i IronchipWindowsLogon.msi IRONCHIP_APIKEY="$apikey" IRONCHIP_HOST="https://api.ironchip.com" IRONCHIP_APIKEY="$apikey" ADDLOCAL="LogonFeature" /q
    ```

    - Proxy configuration -> This configuration is only necessary if you want to enable it, as it is disabled by default. We have disabled, automatic, and manual modes, and for this, several properties are configured:

        - IRONCHIP_PROXY_SELECTED -> This property is used to set the proxy status: none, automatic, or manual.
        - IRONCHIP_PROXY_MANUAL_HOST -> Only necessary if enabling the proxy manually.
        - IRONCHIP_PROXY_MANUAL_PORT -> Only necessary if enabling the proxy manually.

    Example 1: Automatic proxy configuration
    ```bash
    msiexec.exe /i IronchipWindowsLogon.msi IRONCHIP_APIKEY="$apikey" IRONCHIP_HOST="https://api.ironchip.com" IRONCHIP_APIKEY="$apikey" IRONCHIP_PROXY_SELECTED="automatic" /q
    ```

    Example 2: Manual proxy configuration
    ```bash
    msiexec.exe /i IronchipWindowsLogon.msi IRONCHIP_APIKEY="$apikey" IRONCHIP_HOST="https://api.ironchip.com" IRONCHIP_APIKEY="$apikey" IRONCHIP_PROXY_SELECTED="manual" IRONCHIP_PROXY_MANUAL_HOST="localhost" IRONCHIP_PROXY_MANUAL_PORT="8080" /q
    ```
4) Wait for it to finish:
    - The installation process may take some time. Stay in the command line until you see the prompt indicating that the installation is complete.
