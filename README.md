# wireshark

## Summary
Housing my wireshark knowledge and understanding surrounding network traffic analysis (NTA)

## Operations
contains - very forgiving for any instance of string/numbers are present
== - exact match

## Regex
Regex can be used to filter further
?i case insensitive

## Tips and tricks
When unsure what to look for just do the base command of http.request without operation and value to see all information that can be filtered down further.

Then filter further from what results are shown.

## HTTPS decoding
Requires tls keyfile

Source - Method 1: https://unit.42.paloaltonetworks.com/wireshark-tutorial-decrypting-https-traffic

Source - Method 2: https://www.corparitech.com/net-admin/decrypt-ssl-with-wireshark

### Procedure
Method 1:
Requires access to network

1. Filter for: "tls.handshake.type eq 1"
2. Right click example and select "Follow TCP Stream"
3. Using a Man in the Middle technique, you need to record the pcap and locate the encryption key log (text file)
4. Load the key log file in Wireshark
    i. Preferences
    ii. Protocols
    iii. TLS (Transport LAyer Security
    iv. "(Pre)-Master-Secret log filename" 
    v. Select "Browser"
    vi. Choose relevant key log file
5. Observe decrypted information and "Follow HTTP Stream"

Method 2:
Requires access to machine

There is another way to perform this by exporting your environment variable.

Windows specific:
1. AdvancedSystemProperties
2. EnvironmentVariables
3. New
4. Variable name: SSLKEYLOGFILE 
5. Variable value (WHEREVER YOU WANT)
6. Follow steps 4 and onward from previous method

Linux specific:
1. vim ~/.bashrc
2. Input "export SSLKEYLOGFILE=~/.ssl-key.log"
3. Input command "echo $SSLKEYLOGFILE" (ensure file is pointing to export above)
4. Follow steps 4 and onward from Method 1.

## Commands
```
ip.addr <operation> <ipv4/ipv6 addr>
```
Observe ip address traffic

```
http.request <operation> <GET/PUT/POST>
```
Observe http requests

```
dns
```
Observe DNS traffic (port 53)

```
tcp.port <port>
```
Observe dprvigiv poty activity

## Useful links
https://malware-traffic-analysis.net
