# -Raspberry-Pi-Intrusion-Detection-System-with-SMS-Alerts
This project uses a Raspberry Pi 5 as a **lightweight network intrusion detection system** that logs and alerts in real-time. Designed for home network monitoring and cybersecurity experimentation.




---

##  Features

- Monitors ports: `21 (FTP)`, `22 (SSH)`, `23 (Telnet)`, `80 (HTTP)`, `443 (HTTPS)`
- Logs suspicious traffic to `suspicious.log`
- Triggers **SMS alerts** if a Telnet (port 23) connection is detected
- Saves `.pcap` packet captures for Wireshark analysis
- Easily extendable for more ports or alert types

---

##  Stack

| Tool         | Purpose                          |
|--------------|----------------------------------|
| `tcpdump`    | Capture and monitor traffic      |
| `bash`       | Core monitoring & logging script |
| `python3`    | Sends SMS via Twilio             |
| `scp`        | Export `.pcap` files             |
| `nmap`       | Simulate port scans for testing  |

---

## What I Learned

- Building a custom real-time logging system with Bash
- Filtering network traffic for meaningful alerts
- Integrating `tcpdump` output into automated Python workflows
- Working with virtual environments on ARM/Linux
- Handling Twilio API integration and error tracing

---

## Demo

```bash
# Start monitoring traffic
./suspicious_traffic.sh

# From another machine, simulate Telnet scan
nmap -p 23 192.168.1.78

✔️ Results:

    Entry logged to suspicious.log

    .pcap file captured for analysis

    SMS alert sent instantly (via Twilio)


File Overview

.
├── suspicious_traffic.sh      # Live monitoring + alert trigger script
├── send_sms.py                # Twilio integration
├── suspicious.log             # Log file
├── suspicious_capture.pcap    # Captured packet dump
├── requirements.txt           # Python dependencies (Twilio)
└── README.md

Setup
Install Dependencies

sudo apt install tcpdump
python3 -m venv twilio-env
source twilio-env/bin/activate
pip install twilio

Configure Twilio

Edit send_sms.py and replace:

account_sid = "YOUR_SID"
auth_token = "YOUR_AUTH"
from_number = "+1XXXXXXXXXX"
to_number = "+44XXXXXXXXXX"
