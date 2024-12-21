# NUS-Forticlient-VPN-Auto-Connect

VPN Connection Automation Script for NUS SOC VPN, with SSO and OTP support.

## Edits compared to the original repository
- Auto-paste OTP codes in clipboard
- Adapted the process to NUS SOC VPN

***
> *The following documents were automatically translated from Portuguese by OpenAI gpt-4o and may not be entirely accurate.*
***

## Description

This repository contains a Python script that automates the process of connecting to a VPN using OpenConnect and Selenium for SSO login. The script offers functionalities for dependency installation, interactive configuration, manual or automatic login execution, and keeping the sudo session active.

## Features

- Installation of necessary packages
- Interactive configuration via wizard
- Encryption and decryption of passwords using the `cryptography` library
- SSO login automation using Selenium
- Support for manual login execution
- Automatic VPN connection using generated cookies
- Keeping the sudo session active

## Requirements

- Python 3
- Unix-based operating system (Linux, macOS)
- Google Chrome browser

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/rafaelbiasi/forticlient-sso-auto-connect.git
    cd forticlient-sso-auto-connect
    ```
2. Install the dependencies:
    ```bash
    sudo apt install python3-dev python3-pip python3-setuptools
    vpn-auto-connect --install
    ```
3. Add the path to the PATH variable:
   
   For convenience, add the script path (`$HOME/forticlient-sso-auto-connect`) to the PATH variable in ~/.bashrc or ~/.zshrc as shown below:
   ```sh
   export PATH=$HOME/bin:$HOME/.local/bin:/usr/local/bin:$HOME/forticlient-sso-auto-connect:$PATH
   ```
## Usage

### Initial Configuration

1. Create a configuration file `vpn-config.json` in the same directory as the script with the following format:
    ```json
    {
        "username": "your_username",
        "password": "your_password_here_NOT_recommended",
        "encrypted-password": "your_password_here_RECOMMENDED_use_the_--setup_option",
        "host_mapping": {
            "1": "vpn1.example.com",
            "2": "vpn2.example.com"
        },
        "server_cert": "pin-sha256:...",
        "vpn_slice": "..."
    }
    ```
   Choose one of the two options: `password` and `encrypted-password`. For more security, follow the procedure below to encrypt the password. Otherwise, the `password` option is mandatory.

2. Configure the script interactively:
    ```bash
    vpn-auto-connect --setup
    ```

### Connecting to the VPN
1. Display help:
    ```bash
    vpn-auto-connect --help
    ```
    
2. Connect with automatic login (using encrypted password):
    ```bash
    vpn-auto-connect
    ```

3. Connect with plain text password (not recommended):
    ```bash
    vpn-auto-connect --plain
    ```

4. Connect with manual login:
    ```bash
    vpn-auto-connect --manual
    ```

5. Connect with LAN disabled:
    ```bash
    vpn-auto-connect --off
    ```

6. Force the browser to display during SSO login:
    ```bash
    vpn-auto-connect --browser
    ```

### Other Options

- Check for script updates:
    ```bash
    vpn-auto-connect --update
    ```

- Update the script:
    ```bash
    vpn-auto-connect --upgrade
    ```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
