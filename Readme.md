# Eltako Certificates Authority

This repository contains bundles of certificates which can be used to secure the communication with the Eltako Series 62 devices.
Currently there is only one bundle available.

## Usage with Eltako SERIES 62-IP devices

Certificates issued by Eltako for SERIES 62-IP devices have the following subject alternative names:

* DNS: eltako-`SERIALNUMBER OF THE DEVICE`
* DNS: eltako-`SERIALNUMBER OF THE DEVICE`.local

Hence in order to use common tools like curl one cannot use the device's IP address.
If you do this, then the verification of the certificate fails.
Instead you have to use one the two available DNS names to connect to the device.
Most routers are configured such that devices can be accessed by their hostname and thus the first DNS name eltako-`SERIALNUMBER OF THE DEVICE` should work.
The second DNS name can be used if you have mDNS/Bnojour/Avahi enabled.
Alternatively you can either ignore certificate verification errors or provide a verification procedure yourself.
Note that we do not recommend ignoring certificate verification errors.

### Example

Suppose your device has the serial number `examplesn` and you like to retrieve system information using curl and you have mDNS enabled:

```bash
curl --cacert ./eltako_series_62_user_api_certificates_bundle.pem https://eltako-examplesn.local/api/v0/system
```
