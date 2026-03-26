# POC-ThingsFlow

Proof of Concept **ThingsFlow** module.

## Installation

### Prerequisites

Make sure you have the following dependencies available:

- ThingsDB Go module : https://github.com/thingsdb/module-go-thingsdb
- ThingsDB Requests module : https://github.com/thingsdb/module-go-requests

### Download the module

Use the following command to install the module:

```js
new_module("ThingsFlow", "github.com/MeesVaessen/POC-ThingsFlow");
```

### Docker Setup

Ensure your Docker Compose configuration exposes the frontend on port:

```8181```


Example:
```
ports:
  - "8181:8181"
  ```

### Default Credentials

You can log in using the default user:
```
Email: admin@admin.com
Password: password
```
