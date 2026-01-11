# IPC

AutoPTT uses a Protobuf-based IPC over TCP, which by default is at address `127.1.2.3:4000`. You can change it in the `General` settings tab.

Each IPC message encoded in delimited Protobuf, meaning that a varint containing the length of the message always precedes the actual message.

[autoptt.proto](./autoptt.proto) contains the details (look for the `message Ipc` section).

## Basic overview

Connecting

- The client connects to the server by opening a TCP socket.
- After accepting the connection, the server sends an `IpcServerHello` message, which contains the `ipc_version` field. The client should check that the value is the same as it was when the client was implemented. If that is not the case, there are no guarantees that IPC will work correctly.
- The client sends a `IpcClientConfigure` message, where it can set `current_value_update_rate_ms` to a non-zero value to start receiving updates on the current value of the microphone. It's disabled by default. The client should also set the `ipc_version` and `ipc_tag` fields, the latter of which should describe your app -- kind of like `User-Agent` in HTTP.

The server will also send some other messages right after, such as `IpcActivityStateChanged`, `IpcMuteStateChanged`, `IpcSettingsChanged` and `IpcAppEnabledStateChanged`. And as the names suggest, these messages will be sent each time values they refer to change, so you should definitely track them. Especially `IpcAppEnabledStateChanged` because when its value changes to `false`, it means all app functionality is stopped.

## A complete example

You can find a full example on how the this interface is used in the [autoptt-streamdeck](https://github.com/veyh/autoptt-streamdeck/blob/master/deps/autoptt-ipc/IPC.ts) repository.
