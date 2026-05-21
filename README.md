# POC-ThingsFlow

Proof of Concept **ThingsFlow** module.

---

## Installation

### Prerequisites

Make sure you have the following dependencies available. ThingsFlow relies on several official ThingsDB modules to handle external data formatting, webhooks, and automated email notifications:

* [ThingsDB Go module](https://github.com/thingsdb/module-go-thingsdb)
* [ThingsDB Requests module](https://github.com/thingsdb/module-go-requests)
* [ThingsDB SMTP module](https://github.com/thingsdb/module-go-smtp)

> **Note:** You can pin a specific version of any module during installation by appending `@v0.1.0` (or your target version) to the end of the repository URL.

---

### Module Setup Guide

To install and configure the required modules, execute the following commands in the `@thingsdb` (or `/t`) scope of your ThingsDB instance.

#### 1. ThingsFlow Module
Install the core ThingsFlow module:
```js
new_module("ThingsFlow", "github.com/MeesVaessen/POC-ThingsFlow");
```

#### 2. Requests Module (Webhooks)
This module natively supports HTTP POST requests, which ThingsFlow uses for dispatching JSON payloads to third-party webhooks and handling error notifications.
```js
new_module("requests", "github.com/thingsdb/module-go-requests");
```

#### 3. SMTP Module (Email Notifications)
This module exposes the `send_mail` function to handle automated email delivery for flow execution failures.
```js
new_module("smtp", "github.com/thingsdb/module-go-smtp");

// Configure your SMTP server details
set_module_conf("smtp", {
    host: "smtp.yourprovider.com:587", // Required: SMTP host
    auth: ["username", "password"]     // Optional: Authentication credentials
});
```

#### 4. ThingsDB Module (Cross-scope Communication)
This module grants access to other scopes, allowing cross-communication either on the same node or with connections to external ThingsDB clusters.
```js
new_module("thingsdb", "github.com/thingsdb/module-go-thingsdb");

// Configure the connection
set_module_conf("thingsdb", {
    host: "localhost",     // Required: Address of the ThingsDB node
    port: 9200,            // Optional: Defaults to 9200
    token: "YOUR_TOKEN"    // Required: Use a token OR [username, password] for authentication
});
```

---

## Docker Setup

Ensure your Docker Compose configuration exposes the frontend on port **8181**. Add the following port mapping to your `docker-compose.yml`:

```yaml
ports:
  - "8181:8181"
```

---

## Default Credentials

Once the system is running, you can log in to the frontend using the default user credentials:

| Field | Credential |
| :--- | :--- |
| **Email** | `admin@admin.com` |
| **Password** | `password` |