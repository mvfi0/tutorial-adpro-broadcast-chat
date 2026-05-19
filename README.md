## Experiment 2.1: Original code, and how it run

![Experiment 2.1](screenshots/Image4.jpeg)

Run the server first with `cargo run --bin server`, then run multiple clients
with `cargo run --bin client` in separate terminals.
When a client types a message, the server receives it and broadcasts it to
all connected clients. This works asynchronously — the server handles all
clients concurrently without blocking.

## Experiment 2.2: Modifying port

![Experiment 2.2](screenshots/Image5.jpeg)

The port was changed from 2000 to 8080 in both server.rs and client.rs.
Both files need to be modified because WebSocket is a connection-based protocol —
both sides (server and client) must agree on the same port, like two people
agreeing on which phone number to call.
The `ws://` prefix in the client indicates it is using the WebSocket protocol.

## Experiment 2.3: Small changes, add IP and Port

![Experiment 2.3](screenshots/Image6.jpeg)

Modified the server to prepend the sender's IP address and port to each
broadcasted message. This is done by formatting the message as
`"{addr}: {text}"` before sending it to the broadcast channel.
The change is only needed on the server side since the server is the one
that receives and rebroadcasts messages — the client just displays
whatever the server sends.