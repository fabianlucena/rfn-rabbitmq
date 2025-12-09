# RFRabbitMQ

> 🇺🇸 English | 🇪🇸 [Versión en Español](https://github.com/fabianlucena/rfn-rabbitmq/blob/main/README.es.md)
> [Video tutorial](https://www.youtube.com/watch?v=hrU-upEMlPk)

RFRabbitMQ is a lightweight .NET library designed to simplify the implementation of **RPC (Remote Procedure Call)** services over **RabbitMQ**.  
It is used by **FabianLucena.RFNRabbitMQRPCApp** and **FabianLucena.RFNRabbitMQRPCClient**.

---

## 🚀 Features
- Simple and extensible implementation of **RabbitMQ RPC** patterns.
- Supports **.NET 8, .NET 9, and .NET 10**.
- Integrates with `IConfiguration` via Microsoft.Extensions.
- Provides helpers for connection, channel creation, message publishing, and consumption.
- Ideal for microservices requiring synchronous request–response messaging.

---

## 📦 Installation

### Using NuGet Package Manager
```bash
Install-Package RFRabbitMQ
```

### Using .NET CLI
```bash
dotnet add package RFRabbitMQ
```

---

## 🧩 How it works
The library provides foundations for building:
- **RPC Server** using RabbitMQ queues
- **RPC Client** capable of sending requests and awaiting responses

Built-in functionalities include:
- Automatic queue declaration
- Connection and channel lifecycle management
- Correlation ID management
- Configurable timeout handling

---

## 🔧 Basic Configuration

Sample `appsettings.json`:

```json
{
  "RabbitMQ": {
    "HostName": "localhost",
    "UserName": "guest",
    "Password": "guest",
    "QueueName": "rfrpc.queue"
  }
}
```

Loading configuration:

```csharp
var config = builder.Configuration.GetSection("RabbitMQ").Get<RabbitMQConfig>();
```

---

## 🖥️ RPC Examples

For examples of RPC server and client, see the projects:

- https://github.com/fabianlucena/rfn-rabbitmq-rpc-app
- https://github.com/fabianlucena/rfn-rabbitmq-rpc-client

---

## 🏗️ Use in Microservices
RFRabbitMQ is suitable for:
- Orchestration patterns
- Critical synchronous operations
- Systems requiring reliable request/response semantics
- Hybrid async/sync messaging topologies

---

## 🔍 Versioning
Current version: **1.3.3**

---

## 📚 Dependencies
This package depends on:

- `RabbitMQ.Client` **7.2.0**
- `Microsoft.Extensions.Configuration.Abstractions` **8.0.0**

---

## 📄 License
RFRabbitMQ is released under the **MIT License**.

---

## 🌐 Repository
Source code available at:

https://github.com/fabianlucena/rfn-rabbitmq
