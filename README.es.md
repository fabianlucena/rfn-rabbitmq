# RFRabbitMQ

> 🇪🇸 Español | 🇺🇸 [English Version](README.md)

RFRabbitMQ es una librería ligera para .NET diseñada para simplificar la implementación de servicios **RPC (Remote Procedure Call)** sobre **RabbitMQ**.  
Es utilizada por **FabianLucena.RFNRabbitMQRPCApp** y **FabianLucena.RFNRabbitMQRPCClient**.

---

## 🚀 Características
- Implementación simple y extensible del patrón **RPC con RabbitMQ**.
- Compatible con **.NET 8, .NET 9 y .NET 10**.
- Integración con `IConfiguration` mediante Microsoft.Extensions.
- Proporciona utilidades para manejar conexiones, canales, publicación y consumo de mensajes.
- Ideal para microservicios que requieren comunicación síncrona confiable.

---

## 📦 Instalación

### Usando NuGet Package Manager
```bash
Install-Package RFRabbitMQ
```

### Usando .NET CLI
```bash
dotnet add package RFRabbitMQ
```

---

## 🧩 Cómo funciona

La librería provee una base para construir:

- **Servidor RPC** utilizando colas de RabbitMQ  
- **Cliente RPC** capaz de enviar solicitudes y esperar respuestas  

Incluye funcionalidades integradas como:

- Declaración automática de colas  
- Manejo del ciclo de vida de la conexión y canal  
- Gestión de *Correlation IDs*  
- Control de tiempos de espera configurable  

---

## 🔧 Configuración básica

Ejemplo en `appsettings.json`:

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

Lectura de configuración:

```csharp
var config = builder.Configuration.GetSection("RabbitMQ").Get<RabbitMQConfig>();
```

---

## 🖥️ Ejemplo: Servidor RPC

```csharp
public class MiServicioRpc : RpcServerBase
{
    public MiServicioRpc(IConfiguration config) : base(config) { }

    protected override Task<string> HandleMessageAsync(string message)
    {
        return Task.FromResult($"Procesado: {message}");
    }
}
```

---

## 🖥️ Ejemplo: Cliente RPC

```csharp
var client = new RpcClient(config);
string response = await client.CallAsync("Hola mundo");
Console.WriteLine(response);
```

---

## 🏗️ Uso en microservicios

RFRabbitMQ es adecuado para:

- Patrones de orquestación  
- Operaciones críticas que requieren respuesta inmediata  
- Sistemas que necesitan semántica confiable de request/response  
- Arquitecturas híbridas asíncronas/síncronas  

---

## 🔍 Versionado
Versión actual: **1.0.0**

Dependencias:
- `RabbitMQ.Client` **7.2.0**
- `Microsoft.Extensions.Configuration.Abstractions` **8.0.0**

---

## 📄 Licencia
RFRabbitMQ está distribuido bajo la licencia **MIT**.

---

## 🌐 Repositorio
Código fuente disponible en:

https://github.com/fabianlucena/rfn-rabbitmq
