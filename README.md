<div align="center">
  <img src="https://img.shields.io/badge/Version-2.0_PRO-blue?style=for-the-badge&logo=arduino" />
  <img src="https://img.shields.io/badge/Chip-RTL8720DN_(BW16)-black?style=for-the-badge&logo=realtek" />
  <img src="https://img.shields.io/badge/Status-TRIAL-orange?style=for-the-badge" />
  <br><br>
  <img src="https://img.shields.io/badge/🛡️_Educational_Purpose_Only-IMPORTANT-red" />
</div>

<h1 align="center">⚡ AETHERNET PRO (BW16 / RTL8720DN)</h1>
<p align="center">
  <b>Advanced WiFi (2.4GHz & 5GHz) & Bluetooth Security Audit Tool</b><br>
  <i>Single-module design integrating dual-band WiFi deauthentication, Evil Twin, and NRF24 Bluetooth jamming.</i>
</p>

<hr>

<h2>🎯 Feature Details</h2>

<h3>📡 WiFi Attacks (2.4GHz & 5GHz Support)</h3>
<ul>
  <li><b>Smart Deauth Attack:</b> Selectively disconnects targets using native raw packets, forcing devices to automatically connect to our fake network.</li>
  <li><b>Evil Twin & Captive Portal:</b> Identical network cloning (Including SSID & BSSID). Supports Custom HTML upload via Flash memory for highly realistic phishing pages.</li>
  <li><b>Rogue AP:</b> Creates a standalone fake Access Point with built-in Google login pages to capture credentials directly.</li>
  <li><b>Beacon Spam:</b> Floods the area with hundreds of fake randomized SSIDs to test client scanning mechanisms.</li>
  <li><b>Deauth All:</b> Broadcasts deauthentication frames to all nearby networks simultaneously.</li>
  <li><b>Handshake Sniffer:</b> Captures EAPOL 4-way handshakes directly to PCAP format for offline password auditing.</li>
  <li><b>Deauth + Sniff:</b> Combines targeted deauthentication with simultaneous handshake capture for faster results.</li>
</ul>

<h3>📻 Bluetooth Attacks</h3>
<ul>
  <li><b>BT Jammer (NRF24):</b> Uses 1x NRF24L01+ to perform rapid Continuous Wave Sweeping across 2.4GHz channels. Highly effective at disrupting Bluetooth audio and IoT device connections. <b>Note: Activating this locks the module completely for maximum RF output. Requires physical reset to stop.</b></li>
</ul>

<h3>🖥️ Interface & Control</h3>
<ul>
  <li><b>Dark Web Dashboard:</b> Futuristic web interface, mobile-responsive, equipped with a color theme system, live clock sync, and real-time attack status.</li>
  <li><b>Custom OLED UI:</b> Minimalist 3x5 pixel font rendering showing real-time attack stats, progress bars, and a built-in menu navigation system using physical buttons.</li>
  <li><b>Template Manager:</b> Upload, preview, and set active HTML phishing templates directly from the web interface (stored in Flash).</li>
</ul>

<hr>

<h2>🛠️ Hardware & Pinout Specifications</h2>
<p><b>⚠️ STRICT WARNING:</b> This firmware is hard-coded specifically for the <b>BW16 (RTL8720DN)</b> pinout below. Ensure strict adherence to this wiring diagram.</p>

<h3>1. OLED Display (SSD1306 128x64 - I2C)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>OLED Pin</th>
    <th style="text-align: center;">BW16 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>SDA</td><td style="text-align: center;"><b>D8 (PA26)</b></td><td>I2C Data Line</td></tr>
  <tr><td>SCL</td><td style="text-align: center;"><b>D7 (PA25)</b></td><td>I2C Clock Line</td></tr>
  <tr><td>VCC</td><td style="text-align: center;"><b>3.3V</b></td><td>DO NOT use 5V</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground</td></tr>
</table>
<p><i>* I2C Address must be set to <b>0x3C</b>.</i></p>

<h3>2. NRF24L01+ - Bluetooth Jammer (Hardware SPI)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>NRF24L01 Pin</th>
    <th style="text-align: center;">BW16 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>CE</td><td style="text-align: center;"><b>D6 (PB3)</b></td><td>Chip Enable</td></tr>
  <tr><td>CSN</td><td style="text-align: center;"><b>D5 (PB2)</b></td><td>Chip Select</td></tr>
  <tr><td>SCK</td><td style="text-align: center;"><b>D10 (PA14)</b></td><td>Hardware SPI CLK</td></tr>
  <tr><td>MOSI</td><td style="text-align: center;"><b>D12 (PA12)</b></td><td>Hardware SPI MOSI</td></tr>
  <tr><td>MISO</td><td style="text-align: center;"><b>D11 (PA13)</b></td><td>Hardware SPI MISO</td></tr>
  <tr><td>VCC</td><td style="text-align: center;"><b>3.3V</b></td><td>DO NOT use 5V</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground</td></tr>
</table>
<p><b>⚠️ IMPORTANT:</b> Solder a <b>10uF Capacitor</b> directly between the VCC and GND pins on the NRF24L01 module to prevent voltage drops and crashes during transmission.</p>

<h3>3. Navigation Buttons (Input Pullup)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>Button</th>
    <th style="text-align: center;">BW16 Pin</th>
  </tr>
  <tr><td>UP</td><td style="text-align: center;"><b>D4 (PB1)</b></td></tr>
  <tr><td>DOWN</td><td style="text-align: center;"><b>D1 (PA8)</b></td></tr>
  <tr><td>BACK</td><td style="text-align: center;"><b>D3 (PA30)</b></td></tr>
  <tr><td>OK / SELECT</td><td style="text-align: center;"><b>D2 (PA27)</b></td></tr>
</table>

<hr>

<h2>📦 How to Flash the Firmware</h2>

<h3>1. Flashing the BW16 (RTL8720DN)</h3>
<ul>
  <li>Make sure you have installed the <b>Realtek Ameba Arduino Core</b> in Arduino IDE.</li>
  <li>Install the required USB Serial Driver for BW16 on your PC.</li>
  <li>Open <b>Arduino IDE</b> and Select Board: <i>RTL8720DN (BW16)</i>.</li>
  <li>Upload the code via UART. The module will automatically reboot.</li>
  <li><b>ATHERNET SSID will appear shortly.</b> Connect to it and navigate to <code>192.168.1.1</code>.</li>
</ul>

<h3>❓ What if the SSID does not appear?</h3>
<ol>
  <li>BW16 might be stuck in bootloader mode. Unplug then plug it back in.</li>
  <li>Check wiring, specifically NRF24L01 VCC/GND shorts, which prevent booting.</li>
  <li>Erase the flash using ImageTool before re-flashing.</li>
</ol>

<hr>

<div align="center">
  <h2>💎 Get the Full / Premium Version</h2>
  <p>The file available in this repository is a <b>Trial Version</b>, strictly limited to <b>10 Minutes</b> of usage time for initial demonstration. Once the trial expires, the device is permanently locked and displays a "DEVICE LOCKED" message on both Web and OLED.</p>
  <p><b>Benefits of purchasing the Premium Version:</b></p>
  <p>
    ✅ No Time Limits (Premium Unlimited/Permanent).<br>
    ✅ Get Latest Updates (Can be upgraded to newer versions later).<br>
    ✅ Each purchase includes 2 free updates. You can request it anytime if there is a newer release.<br>
    Contact me on Telegram if you are interested.<br>
    The price above is for 1 copy of the binary file and cannot be duplicated.<br>
    ✅ Technical Support via Telegram (Troubleshooting and custom wiring assistance).
  </p>
  <br>
  <a href="https://t.me/+6283141852690">
  <img src="https://img.shields.io/badge/Buy_Now-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" />
  </a>
  <br><br>
  <i>Click the button above to chat directly with me on Telegram.</i>
</div>

<hr>

<h2>📸 Preview & Documentation</h2>
<p><b>Module Wiring Diagram (BW16):</b></p>
<p align="center">
  <img src="GAMBAR_SKEMATIK_BW16_ANDA_DISINI.jpg" width="800" alt="Wiring Diagram" />
</p>

<p><b>Module Wiring Diagram (BW16):</b></p>
<p align="center">
  <img src="GAMBAR_SKEMATIK_BW16_ANDA_DISINI.jpg" width="800" alt="Wiring Diagram" />
</p>

<hr>

<div align="justify" style="background-color: #ffcccc; padding: 15px; border-left: 5px solid #ff0000;">
  <h3>⚖️ Legal Disclaimer</h3>
  <b>STRICT WARNING:</b> This tool is created purely for <i>Penetration Testing</i> and <i>Educational Purposes</i> within the scope of network security. It is strictly forbidden to use this tool to attack, steal data, or disrupt networks that are NOT your property. Any form of abuse that violates your country's laws is <b>NOT</b> the responsibility of the Developer. By using this firmware, you agree to these terms and conditions.
</div>

<div align="center">
  <br>
  <sub>Built with ❤️ by AETHERNET Developer Team</sub>
</div>
