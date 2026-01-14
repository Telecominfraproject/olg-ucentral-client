# olg-ucentral-client

uCentral Client application for OpenWiFi Gateway Device, communicating with the
[uCentral Gateway](https://github.com/Telecominfraproject/wlan-cloud-ucentralgw).

This software is a part of the OpenWiFi Gateway. Yet to be decided. Temporary NOS
[OLG NOS](https://github.com/Telecominfraproject/olg-installer).

## Developer Notes

The uCentral connection uses the WebSocket protocol, and messages are
transferred in JSON-RPC format. Full details of this protocol can be found in a
separate document
[here](https://github.com/Telecominfraproject/wlan-cloud-ucentralgw/blob/master/PROTOCOL.md).

- Incoming JSON-RPC messages are handled in `proto.c:proto_handle()`.
- Complex actions are executed via task queues (`libubox/runqueue.h`).
- Many actions will fork external programs, notably ucode scripts installed by
  the [ucentral-schema](https://github.com/Telecominfraproject/olg-ucentral-schema)

This application registers several ubus methods under the `ucentral` object, as
defined in `ubus.c:ubus_object`.
