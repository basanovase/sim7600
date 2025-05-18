# SIM7600 MicroPython Library

This library provides a set of classes to interact with the SIM7600 module using MicroPython. The library covers core functionalities, SMS, calling, GPRS, HTTP, FTP, phonebook, TCP/IP, and HTTPS operations.


## Installation

Copy the following files to your MicroPython environment:

- `__init__.py`
- `core.py`
- `sms.py`
- `calling.py`
- `gprs.py`
- `http.py`
- `ftp.py`
- `phonebook.py`
- `tcpip.py`

## Usage

### Core Functionality

```python
from sim7600 import SIM7600
import machine

# Initialize the SIM7600 module
uart = machine.UART(1, baudrate=115200, tx=17, rx=16)
sim7600 = SIM7600(uart)
```
# SMS

```python
from sim7600.sms import SMS

sms = SMS(sim7600)

# Send an SMS
sms.send_sms('+1234567890', 'Hello, world!')

# Read an SMS
response = sms.read_sms(1)
print(response)

# Delete an SMS
sms.delete_sms(1)

# List all SMS
response = sms.list_sms('ALL')
print(response)
```

# Calling

```python

from sim7600.calling import Calling

calling = Calling(sim7600)

# Make a call
calling.make_call('+1234567890')

# Hang up the call
calling.hang_up()

# Answer an incoming call
calling.answer_call()

# Check call status
status = calling.call_status()
print(status)

# Set call volume
calling.set_call_volume(5)
```

# GPRS

```python
from sim7600.gprs import GPRS

gprs = GPRS(sim7600)

# Set APN
gprs.set_apn('your_apn', 'username', 'password')

# Enable GPRS
gprs.enable_gprs()

# Disable GPRS
gprs.disable_gprs()

# Get IP address
ip_address = gprs.get_ip_address()
print(ip_address)

# Send data
gprs.send_data('Hello, GPRS!')

# Receive data
data = gprs.receive_data()
print(data)
```
# HTTP

```python
from sim7600.http import HTTP

http = HTTP(sim7600)

# Set APN
http.set_apn('your_apn', 'username', 'password')

# Enable HTTP
http.enable_http()

# Set URL
http.set_url('http://example.com')

# Perform a GET request
response = http.get()
print(response)

# Perform a POST request
response = http.post('key1=value1&key2=value2')
print(response)

# Read HTTP response
response = http.read_response()
print(response)

# Disable HTTP
http.disable_http()
```

# FTP
```python
from sim7600.ftp import FTP

ftp = FTP(sim7600)

# Set FTP parameters
ftp.set_ftp_parameters('ftp.example.com', user='username', password='password')

# Upload a file
ftp.upload_file('/local/path/file.txt', '/remote/path/file.txt')

# Download a file
ftp.download_file('/remote/path/file.txt', '/local/path/file.txt')

# Delete a file
ftp.delete_file('/remote/path/file.txt')

# List files
files = ftp.list_files('/remote/path/')
print(files)
```
