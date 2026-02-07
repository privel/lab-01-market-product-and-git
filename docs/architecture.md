# Architecture

## Product Choice

- **Product name:** Telegram
- **Website:** <https://telegram.org>
- **Short description:** Telegram is a cloud-based messaging platform focused on fast message delivery, multi-device sync, and support for large groups/channels and bots.

## Main components

> According to the C4 model, a component is a grouping of related functionality encapsulated behind a well-defined interface.

### Component diagram

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

**PlantUML code:** [Telegram Component Diagram Code](./diagrams/src/telegram/component-diagram.puml)

### Selected components (from the diagram)

1. **MTProto Gateway (DC Entry)**
   - Entry point for Telegram clients using the MTProto protocol. Routes incoming traffic to internal services and enforces basic connection-level policies.

2. **Auth & Session Service**
   - Handles user authentication (login, OTP/verification) and manages active sessions/tokens. Validates that a request belongs to a real, active user session.

3. **Message Handling Service**
   - Core logic for sending/receiving messages. Validates message payloads, writes message metadata, and triggers propagation to recipients.

4. **Media & File Service**
   - Responsible for file uploads/downloads and media-related processing. Stores references to files and coordinates saving to file storage.

5. **Channel/Broadcast Service**
   - Manages channels and large broadcasts. Optimizes fan-out delivery logic when one sender publishes to many subscribers.

6. **Notification/Updates Service**
   - Produces updates for clients (new message updates, delivery status, etc.). Pushes changes through internal channels and external push providers when needed.

7. **Distributed File System (DFS)**
   - Stores large blobs (photos/videos/documents). Provides scalable storage and retrieval for uploaded media files.

## Data flow

### Sequence diagram

![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

**PlantUML code:** [Telegram Sequence Diagram Code](./diagrams/src/telegram/sequence-diagram.puml)

### Chosen group of actions: “Media file upload & propagation” (upload + notify flow)

In this flow, the **mobile client** uploads a media file and Telegram propagates the message to recipients.

- The **Mobile App** sends an upload request via **MTProto** to the **MTProto Gateway**.
- The gateway forwards the request to core services, where **Auth & Session Service** verifies the session and access rights.
- The **Message Handling Service** creates the message metadata and asks **Media & File Service** to store the uploaded file.
- The **Media & File Service** saves the binary data into the **Distributed File System (DFS)** and returns a `file_id`/reference.
- The **Message Handling Service** stores message/file references (metadata) and triggers delivery.
- The **Notification/Updates Service** notifies recipients’ clients about a new message and may call external **Push Services (FCM/APNS)** if recipients are offline.
- Data exchanged between components includes: session tokens/session info, message metadata (chat_id, sender_id, timestamp), and media reference (`file_id`, size, checksum, storage location).

## Deployment

### Deployment diagram

![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

**PlantUML code:** [Telegram Deployment Diagram Code](./diagrams/src/telegram/deployment-diagram.puml)

### Where components are deployed (briefly)

- **Clients:** Telegram Mobile App / Desktop App / Web Client run on user devices.
- **Edge/Entry:** **MTProto Gateway** and **Bot API Frontend** run on Telegram’s infrastructure (data centers) and accept external traffic.
- **Core cluster:** services like **Auth Service**, **Message Service**, **Channel Service**, **Push Notification Service** run inside a private cluster behind internal RPC.
- **Storage layer:** **Redis/In-memory cache** and **Distributed File System** run as separate storage clusters.
- **Integration/External:** SMS providers and push providers (FCM/APNS) are external systems accessed over the internet.

## Assumptions

- I assume **Message Handling Service** writes message metadata first (or atomically with media reference) so that delivery can retry safely even if the upload pipeline is retried.
- I assume **Distributed File System (DFS)** replicates media across multiple nodes/data centers to ensure availability and fast downloads.
- I assume **Notification/Updates Service** decides whether to use real-time updates vs. external push based on recipient online status.

## Open questions

- How exactly does Telegram implement **load balancing and routing** across multiple MTProto Gateways and data centers under peak load?
- What is the real **consistency model** between message metadata storage and DFS media storage (exactly-once vs at-least-once, rollback strategy)?
- What caching strategies (keys, TTLs, invalidation) are used to keep reads fast for large groups/channels during spikes?
