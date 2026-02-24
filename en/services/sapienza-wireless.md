# University's WiFi

Sapienza offers two wireless networks to undergraduate, graduate and PhD students, researchers, professors and administrative staffers: Sapienza and Eduroam. Both allow a fast internet connection, but they are indeed very different.

## Sapienza Wi-Fi
**Sapienza Wi-Fi** uses an authentication system called Captive Portal:
1. Connect to the Wi-Fi network called "Sapienza";
2. A login window will automatically pop up;
3. Insert **your ID number (codice matricola)** and **the password you use for Infostud**.

After that, if all went well, you will be redirected to the homepage of Sapienza's website. If you reach that point, it means that you will be able to use the connection freely!

Keep in mind that Sapienza Wi-Fi requires login every time you try to connect to it, a not so practical feature if you have to use it frequently. Therefore, it is suggested to use Eduroam Wi-Fi, which requires only one configuration.

## Eduroam Wi-Fi
**Eduroam** (education roaming) is an international service of wireless roaming and it is, therefore, avaible in many academic institution around the world.
Credential for the access are **your personal Sapienza email (surname.id_number@studenti.uniroma1.it)** and **the password you use for Infostud**.

### Setting Up Eduroam

{{% tabs "eduroamdevices" %}}
{{% tab "📱 Smartphone" %}}

To use Eduroam on your smartphone:
1. Download the app **GetEduroam**:
    <p><a href="https://play.google.com/store/apps/details?id=app.eduroam.geteduroam" target="_blank" rel="attachment noopener wp-att-35892"><img loading="lazy" decoding="async" src="https://i.imgur.com/lMuV9nw.png" alt="Get It On Google Play" width="200px">&nbsp;</a> <a href="https://apps.apple.com/no/app/geteduroam/id1504076137" rel="attachment wp-att-35894"><img loading="lazy" decoding="async" src="https://i.imgur.com/EhmxDtk.png" alt="Download on the App Store" width="200px"></a>
2. Open it and follow the procedure for configuration.

{{% /tab %}}
{{% tab "💻 Laptop" %}}

To use Eduroam on you computer:
1. Visit the [official Eduroam website](https://cat.eduroam.org);
2. Download the install for your operating system;
3. Execute the install and follow the procedure for configuration.

On **Mac**, after downloading:
1. Go to **System Settings** > **Privacy and Security**;
2. Go to **Profiles** (at the end of the page);
3. Double click the certificate **Eduroam**;
4. Click on **Download...**

On **Linux** (Debian based): first, **follow the general steps listed at the beginning of this section** (visit the [official website](https://cat.eduroam.org), download the script/installer, execute it, and follow the configuration instructions). Subsequently, since Eduroam access points use TLSv1.0 (unless the TLS version is updated at the hotspot level), proceed as follows:
1. Run `sudo nano /etc/NetworkManager/system-connections/<connection-ssid>.nmconnection` in our case, `eduroam`
2. Add the line `phase1-auth-flags=32` as the last line in the `[802-1x]` section. Save.
3. (Fedora only) Run `sudo update-crypto-policies --set DEFAULT:SHA1` from the terminal if you are on Fedora 42 or earlier.
4. Restart both `NetworkManager` and `wpa_supplicant` (run `sudo systemctl restart NetworkManager` and `sudo systemctl restart wpa_supplicant`)
5. From now on, to connect to eduroam, you will need to run `sudo nmcli --ask connection up eduroam` from the terminal. You will be asked to enter your uniroma1 password: enter it and press `ENTER`.

Please note that while you are connected to Eduroam, the NetworkManager integrated into the operating system will _not_ work (KDE Plasma) and you will see strange behavior. When you need to disconnect, always use nmcli (e.g., `sudo nmcli --ask connection down eduroam`). NetworkManager will return to normal operation.


{{% /tab %}}
{{% /tabs %}}

{{% hint tip %}}
<i class="fa-solid fa-lightbulb" style="color: #238636;"></i> **Did you know that...**

The Eduroam network is available in thousands of international universities! This means that, if you wanted to, you could go to another associated university and could connect to the Eduroam network using the same credentials of Sapienza!
{{% /hint %}}

## Which Wi-Fi should I use?
If you use Wi-Fi occasionally or you cannot configure Eduroam, it is better to use Sapienza Wi-Fi. Otherwise, Eduroam is the best option!
