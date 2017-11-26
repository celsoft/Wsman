# Wsman - A PHP package for WS-Management Protocol

-- Coming soon!

## Installation

You don't (just yet). The package is not quite ready ^_^

## Usage

### Create a client

```php
use c0py\Wsman\Wsman;

$client = new Wsman([
        'location' => "http://TARGET-HOST:5985",
        'login' => 'username',
        'password' => 'password',
    ]);
```

### Simple Queries

Identity target

```php
$response = $client->identify();
```

Get WinRM Config

```php
$config = $client->get('winrm/config');
```

### WMI Queries

Get Volume C:
```php
$response = $client->get('wmicimv2/Win32_logicaldisk', ['DeviceId' => 'C:']);
```

List Windows Services:
```php
$response = $client->enumerate('wmicimv2/Win32_Service');
```

### Windows Registy Query

```php
$params = [
  'hDefKey' => '2147483650',
  'sSubKeyName' => 'SOFTWARE\Microsoft\Windows NT\CurrentVersion',
  'sValueName' => 'ProductName'
];

$response = $client->invoke('GetStringValue', 'wmi/root/default/StdRegProv', $params);
```

## TODO

- [x] Support for BASIC Authentication
- [ ] Support for Digest Authentication
- [ ] Support for NTLM Authentication
- [ ] Support for Kerberos Authentication
- [x] Implement Get Method
- [x] Implement Identify Method
- [x] Implement Enumerate Method
- [x] Implement Invoke Method
- [ ] Implement Put Method
- [ ] Implement Delete Method
- [ ] Handle Errors and failed requests
- [x] Use Guzzlehttp client instead of plain CURL
- [ ] Test againsts non-Windows based devices
- [ ] Handle/Remove hard-coded Microsoft Schema namespaces in SOAP headers
- [ ] Handle/Remove hard-coded language tags in SOAP headers
