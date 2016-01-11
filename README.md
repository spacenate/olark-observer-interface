# Olark Observer Interface
USB custom control transfer request interface

To set the status of an Olark Observer hardware device, a Vendor type control transfer is initiated by the host. Byte 0 of the setup packet, containing the bmRequestType field, shall be set to `0xc0`, indicating a Vendor type transfer from device to host, with the device as recipient of the control transfer. Byte 1, bRequest, shall contain one of the following values:

- `0x00` Notification device off
- `0x01` Set notification device to reflect Olark operator status "operator available"
- `0x02` Set device to status "operator unavailable"
- `0x03` Set device to status "at max chats"
- `0x04` Set device to status "has unread chats"

Bytes 2-3 and 4-5, the wValue and wIndex fields, are not currently used, and should be set to `0`.

The transfer data phase should be 2 bytes in length, reflected in bytes 6-7 being set to '0x0002'.

When the Olark Observer hardware device responds, byte 0 of the data packet shall be set to `0x22` as confirmation the status has been updated. Byte 1 shall echo the bRequest type value.

### License
MIT