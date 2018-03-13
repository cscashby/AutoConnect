!!! info "Luxbar"
    The AutoConnect menu is developed using the [LuxBar](https://github.com/balzss/luxbar) which is licensed under the MIT License. See the [License](license.md).

## <i class="fa fa-external-link"></i> Where the from

The AutoConnect menu appears when you access the **AutoConnect root path**. It is assigned to "**/_ac**" located on ESP8266 *local IP address* by default. This location can be changed in the sketch. The following screen will appear at access to `http://{localIP}/_ac` as the root path. This is the statistics of the current WiFi connection. You can access the menu from the here. (e.g. `http://192.168.244.1/_ac` for SoftAP mode.)  
To invoke the menu tap <i class="fa fa-bars"></i> at right on top.

<img src="../images/_ac.png" style="border-style:solid;border-width:1px;border-color:lightgrey;width:280px;" />

!!! note "What's local IP?"
    A local IP means Local IP at connection established or SoftAP's IP.

## <i class="fa fa-bars"></i> Right on top

Currently, AutoConnect supports four menus. Undermost menu returns to home path of its sketch.

- **Configure new AP** : Configure SSID and Password for new access point.
- **Open SSIDs** : Opens the past SSID which has been established connection from EEPROM.
- **Disconnect** : Disconnects current connection.
- **Reset...** : Rest the ESP8266 module.
- **HOME** : Return to user home page.

<img src="../images/menu.png" style="width:280px;" />

## <i class="fa fa-bars"></i> Configure new AP

Scan all available access point and display it. Strength and security of the detected AP are marked. The <i class="fa fa-lock"></i> is indicated for the SSID that needs a security key. "**Hidden:**" means the number of hidden SSIDs discovered.  
Enter SSID and Passphrase and tap "**apply**" to try connection. 

<img src="../images/newap.png" style="border-style:solid;border-width:1px;border-color:lightgrey;width:280px;" />

## <i class="fa fa-bars"></i> Open SSIDs

Once it was established connection, its SSID and Password will be stored to the EEPROM of ESP8266 automatically. The **Open SSIDs** menu reads the saved SSID credentials from the EEPROM. The stored credential data are listed by the SSID as shown below. Its label is a clickable button. To tap the SSID button starts connection it.

<img src="../images/open.png" style="border-style:solid;border-width:1px;border-color:lightgrey;width:280px;" />

## <i class="fa fa-bars"></i> Disconnect

Disconnect ESP8266 from the current connection. After the menu tapped, AutoConnect menu cannot be accessed. Once disconnected, you will need to set the SSID again to connect to the WLAN.

It can also reset the ESP8266 automatically after being disconnected from the [API](api.md#autoreset) used in the sketch.

## <i class="fa fa-bars"></i> Reset...

Reset the ESP8266, it will be rebooted. After rebooting complete, the ESP8266 begins establishing the previous connection by WIFI_STA mode and the *esp8266ap* as SoftAP disappears from the WLAN.

<img src="../images/resetting.png" style="width:280px;" />

!!! warning "Not every module will be rebooted normally"
    The Reset menu is using the **ESP.reset()** function. This is an almost hardware reset. In order to resume the sketch normally, the [state of GPIO0](https://github.com/esp8266/esp8266-wiki/wiki/Boot-Process#esp-boot-modes) is important. Since this depends on the circuit implementation for each module, not every module will be rebooted normally. See also [FAQ](faq.md#hang-up-after-reset).