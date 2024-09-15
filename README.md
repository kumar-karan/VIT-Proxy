# VIT-Proxy

VIT-Proxy is a macOS utility for toggling proxy settings on the Wi-Fi network. This repository contains two AppleScript apps that can turn the proxy on and off as needed. The scripts use the `networksetup` command to modify web proxy and secure web proxy settings.

## Files

- `ON Proxy.app`: Enables the web proxy and secure web proxy for the Wi-Fi network with a specific IP and port.
- `OFF Proxy.app`: Disables the web proxy and secure web proxy for the Wi-Fi network.

## Usage

### Disable Proxy

```applescript
try
    do shell script "networksetup -setwebproxystate \"Wi-Fi\" off"
    do shell script "networksetup -setsecurewebproxystate \"Wi-Fi\" off"
    do shell script "networksetup -setproxyautomaticconfigurationurl \"Wi-Fi\" \"\""
on error err
    -- Ignore the error
end try
tell current application to quit
```

### Enable Proxy

```applescript
try
    do shell script "networksetup -setwebproxy \"Wi-Fi\" 172.16.1.1 56349"
    do shell script "networksetup -setsecurewebproxy \"Wi-Fi\" 172.16.1.1 56349"
    do shell script "networksetup -setproxyautomaticconfigurationurl \"Wi-Fi\" \"\""
on error err
    -- Ignore the error
end try
tell current application to quit
```

## How to Install

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/kumar-karan/VIT-Proxy.git
   ```

2. Run the `ON Proxy.app` to enable the proxy or `OFF Proxy.app` to disable it.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
