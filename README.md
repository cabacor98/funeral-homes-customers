# Funeral Homes - Customers Microservice

Repositorio: https://github.com/cabacor98/funeral-homes-customers

## Descripción

Microservicio **Customers** del ecosistema *Funeral Homes*. Responsable de administrar la información de clientes, beneficiarios y planes funerarios. Implementado con Clean Architecture, DDD, CQRS, Mediator, Repository y Unit of Work.

## Arquitectura

Este microservicio sigue Clean Architecture con 4 capas, con dependencias hacia adentro:

`
FuneralHomes.Customers.Api
        ↓
FuneralHomes.Customers.Infrastructure
        ↓
FuneralHomes.Customers.Application
        ↓
FuneralHomes.Customers.Domain
`

- **Domain**: Núcleo del negocio. Entidades, Value Objects, Enums, abstracciones base.
- **Application**: Casos de uso (CQRS con Queries), DTOs, interfaces de repositorios, contratos.
- **Infrastructure**: Implementación de repositorios, EF Core, DbContext, configuraciones, migraciones, seed.
- **Api**: Controladores REST, Swagger, configuración, arranque de la aplicación.

Cada microservicio es independiente con su propia base de datos SQL Server LocalDB.

## Requisitos

- .NET 10 SDK
- SQL Server LocalDB
- dotnet-ef (global o local via dotnet-tools.json)

## Ejecución

1. Restaurar herramientas y paquetes
`ash
dotnet tool restore
dotnet restore
`

2. Ejecutar la API
`ash
dotnet run --project src/FuneralHomes.Customers.Api
`

3. Acceder a Swagger: http://localhost:5225/swagger

## Endpoints (mínimos - Entrega 1)

| Método | Ruta | Descripción |
|---|---|---|
| GET | /api/plans | Listar planes |
| GET | /api/plans/{id} | Obtener plan por ID |
| GET | /api/beneficiarios | Listar beneficiarios |
| GET | /api/beneficiarios/{id} | Obtener beneficiario por ID |

## Git Flow

Este repositorio utiliza Git Flow con ramas: main, develop, feature/*, release/*.

## Notas

Estructura preparada para integrarse con otros microservicios del ecosistema Funeral Homes (Identity, Financials, Services, Notifications), manteniendo convenciones comunes.
