WiFiGuard
 <div align="center"> <img src="docs/logo.png" alt="WiFiGuard Logo" width="200"/> <h3>Wireless
 Network Security Monitor</h3> <p>Protect your WiFi network from link-layer attacks with real-time
 detection and alerts</p> </div>
 🛡
 Overview
 WiFiGuard is a cross-platform desktop application that continuously monitors your connected WiFi router 
for wireless attacks such as deauthentication floods, authentication floods, rogue access points (Evil Twin), 
and other link-layer threats. It uses passive WiFi traffic monitoring by capturing 802.11 management 
frames in monitor mode to detect suspicious patterns.
 <div align="center"> <img src="docs/dashboard_screenshot.png" alt="WiFiGuard Dashboard"
 width="800"/> </div>
 ✨
 Key Features
 🔧
 Real-time Attack Detection: Monitors 802.11 management frames to detect various wireless attacks
 including deauthentication floods, authentication floods, and rogue access points
 Smart Detection Algorithm: Implements an automated attack detection algorithm inspired by
 Wireless Link Layer Attacks Detection Algorithm (WLLADA) to minimize false positives
 Router Integration: Optionally accesses router logs or SNMP data to detect configuration anomalies
 or unusual traffic patterns
 Distributed Alerts: Broadcasts alert notifications to all devices connected to the same router on the
 local network using UDP multicast
 User-friendly Interface: Clean dashboard showing router status, connected devices, detected
 threats, and historical attack logs
 Actionable Recommendations: Provides specific recommendations to mitigate detected attacks
 Mobile Notifications: Supports push notifications to smartphones via Firebase Cloud Messaging
 integration
 Cross-Platform: Runs on Windows, macOS, and Linux with a common codebase
 Installation
 Prerequisites
 Python 3.8 or higher
 A wireless network interface card that supports monitor mode
Root/Administrator privileges (required for packet capture)
 Quick Install
 bash
 # Install from PyPI
 pip 
# Install from PyPI
 pip install
 install wifiguard
 wifiguard
 # Install from source
 # Install from source
 git clone https://github.com/username/wifiguard.git
 git
 cd
 clone https://github.com/username/wifiguard.git
 cd wifiguard
 pip 
wifiguard
 pip install
 install -e -e . .
 For detailed installation instructions for different platforms, please see our 
�
�
 Usage
 Graphical User Interface
 Run WiFiGuard with the graphical user interface:
 bash
 # Linux/macOS (requires sudo for monitor mode)
 sudo
 # Linux/macOS (requires sudo for monitor mode)
 sudo python -m wifiguard
 python -m wifiguard
 # Windows (run as Administrator)
 # Windows (run as Administrator)
 python -m wifiguard
 python -m wifiguard
 Console Mode
 For headless servers or command-line operation:
 bash
 # Basic usage
 sudo
 # Basic usage
 sudo python -m wifiguard --console-only -i wlan0
 python -m wifiguard --console-only -i wlan0
 Setup Guide.
 # Specify the wireless interface and monitor specific access point
 sudo
 # Specify the wireless interface and monitor specific access point
 sudo python -m wifiguard --console-only -i wlan0 --bssid 00:11:22:33:44:55
 python -m wifiguard --console-only -i wlan0 --bssid 00:11:22:33:44:55
 Common Options-i, --interface : Wireless interface to monitor (default: wlan0)
-c, --channel : WiFi channel to monitor (default: auto)--bssid : BSSID of the specific access point to monitor--console-only : Run in console mode without GUI--trust-ap : Add a trusted AP (format: 'bssid,ssid,channel')--detection-window : Detection time window in seconds (default: 10)--log-level : Set logging level (DEBUG, INFO, WARNING, ERROR, CRITICAL)
 For a complete list of options, run:
 bash
 python -m wifiguard --help
 python -m wifiguard --help
 📋
 Requirements
 Core Dependencies
 scapy : For packet capture and analysis
 pysnmp (optional): For SNMP integration with routers
 paramiko (optional): For SSH access to routers
 GUI Dependencies
 PyQt5 : For the graphical user interface
 PyQtChart : For data visualization and charts
 Install all dependencies with:
 bash
 pip 
pip install
 install scapy pysnmp paramiko PyQt5 PyQtChart
 scapy pysnmp paramiko PyQt5 PyQtChart
 🔍
 How It Works
 WiFiGuard works by putting your wireless network interface into monitor mode, which allows it to 
capture all 802.11 frames in the air, not just those directed to your device. It then analyzes these frames to 
detect patterns characteristic of common wireless attacks:
 1. Deauthentication Flood Detection: Identifies unusual patterns of deauthentication frames that
 attackers use to disconnect legitimate clients
2. Authentication Flood Detection: Monitors for high rates of authentication frames that could
 indicate a attempt to overwhelm an access point
 3. Rogue AP Detection: Identifies potential "Evil Twin" attacks by detecting access points that mimic
 the SSID of trusted networks but have different characteristics
 4. Traffic Analysis: Analyzes traffic patterns to detect anomalies that could indicate attacks
 For a detailed description of the detection algorithms, see our Technical Documentation.
 📱
 Companion Mobile App
 WiFiGuard includes a companion mobile app that allows you to receive push notifications on your 
smartphone. The mobile app is available for:
 Android: Google Play Store
 iOS: App Store
 🛠
 Architecture
 WiFiGuard follows a modular architecture pattern:
 📊
 Visualization Examples
 <div align="center"> <img src="docs/attack_detection.png" alt="Attack Detection" width="400"/> <img
 src="docs/network_map.png" alt="Network Map" width="400"/> </div>
 🔒
 Security Considerations
 WiFiGuard/ WiFiGuard/
 ├── core/                 # Core monitoring and detection modules ├── core/                 # Core monitoring and detection modules
 │   ├── monitor.py        # WiFi monitoring in monitor mode │   ├── monitor.py        # WiFi monitoring in monitor mode
 │   ├── detector.py       # Attack detection algorithms │   ├── detector.py       # Attack detection algorithms
 │   ├── analyzer.py       # Traffic pattern analysis │   ├── analyzer.py       # Traffic pattern analysis
 │   └── notifier.py       # Alert notification system │   └── notifier.py       # Alert notification system
 ├── ui/                   # User interface components ├── ui/                   # User interface components
 │   ├── dashboard.py      # Main application dashboard │   ├── dashboard.py      # Main application dashboard
 │   ├── alerts.py         # Alert visualization │   ├── alerts.py         # Alert visualization
 │   └── settings.py       # User configuration │   └── settings.py       # User configuration
 ├── utils/                # Utility functions and helpers ├── utils/                # Utility functions and helpers
 ├── data/                 # Data storage ├── data/                 # Data storage
 ├── docs/                 # Documentation ├── docs/                 # Documentation
 ├── tests/                # Unit and integration tests ├── tests/                # Unit and integration tests
 └── main.py               # Application entry point └── main.py               # Application entry point
WiFiGuard is designed for legitimate use by network administrators to protect their own networks
 Always obtain proper authorization before monitoring any network
 WiFiGuard does not perform active attacks or packet injection
 The tool is for defensive monitoring only and should not be used for offensive purposes
 🤝
 Contributing
 Contributions are welcome! Please feel free to submit a Pull Request.
 1. Fork the project
 2. Create your feature branch (
 git checkout -b feature/amazing-feature )
 3. Commit your changes (
 git commit -m 'Add some amazing feature' )
 4. Push to the branch (
 git push origin feature/amazing-feature )
 5. Open a Pull Request
 See the 
contributing guidelines for more information.
 📄
 License
 This project is licensed under the MIT License - see the 
�
�
 Acknowledgements
 LICENSE file for details.
 Scapy - The powerful Python packet manipulation program
 PyQt - The Python bindings for Qt
 WLLADA paper - For the attack detection algorithm inspiration
 All the contributors who have helped improve WiFiGuard
 📬
 Contact
 Project Link: 
https://github.com/username/wifiguard
