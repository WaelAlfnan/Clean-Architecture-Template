# Clean Architecture Template

This template provides a robust and scalable starting point for your .NET applications, meticulously structured following the principles of **Clean Architecture**. It promotes a clear separation of concerns, making your codebase maintainable, testable, and independent of external frameworks and databases.

---

## Project Structure

The solution is organized into distinct layers, each with a specific responsibility. This layered approach ensures that dependencies flow inwards, from the outer layers (UI, Infrastructure) to the inner layers (Application, Domain).

```
App/
├── App.Domain/             # Core Business Entities
│   ├── Entities/           # Fundamental business objects and data structures
│   ├── Enums/              # Enumerations relevant to the business domain
│   ├── Interfaces/         # Abstractions for repositories (e.g., IRepository, IUnitOfWork)
│   └── Extensions/         # Domain-specific Dependency Injection registrations
│
├── App.Application/        # Business Logic & Use Cases
│   ├── DTOs/               # Data Transfer Objects for communication between layers
│   ├── Services/           # Application-specific services that orchestrate domain entities
│   ├── Interfaces/         # Interfaces for application services, defining use cases
│   └── Extensions/         # Application-specific Dependency Injection registrations
│
├── App.Infrastructure/     # Data Access & External Services Implementation
│   ├── Data/               # Data persistence implementations (depends only on App.Domain)
│   │   ├── Contexts/       # Database contexts (e.g., Entity Framework DbContext)
│   │   ├── Repositories/   # Concrete implementations of repository interfaces from App.Domain
│   │   ├── UnitOfWork.cs   # Implementation of IUnitOfWork from App.Domain
│   │   └── Migrations/     # Database migration files
│   ├── Configurations/     # Configuration for infrastructure components
│   ├── Services/           # Implementations of external services (e.g., email, payment gateways), adhering to interfaces from App.Domain
│   └── Extensions/         # Infrastructure-specific Dependency Injection registrations
│
├── App.Api/                # Web API Presentation Layer
│   ├── Controllers/        # API controllers that consume Application services
│   └── Extensions/         # API-specific Dependency Injection registrations
│
├── App.Host/               # Entry Point & Application Host
│   ├── Program.cs          # Application startup and composition root for all DI registrations
│   ├── appsettings.json    # Application configuration settings
│   └── wwwroot/            # Static files for web hosting
│
└── App.Tests/              # Unit & Integration Tests
    ├── Domain.Tests/       # Tests for business rules and entities in App.Domain
    ├── Application.Tests/  # Tests for application services and use cases in App.Application
    └── Infrastructure.Tests/ # Tests for data access and external service implementations in App.Infrastructure
```

---

## Getting Started

To get this template up and running:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/WaelAlfnan/Clean-Architecture-Template]
    cd App
    ```
2.  **Restore NuGet packages:**
    ```bash
    dotnet restore
    ```
3.  **Run the application:**
    ```bash
    dotnet run --project App.Host
    ```

---

## Key Principles

* **Separation of Concerns:** Each layer has a distinct responsibility, ensuring a modular and organized codebase.
* **Dependency Inversion Principle:** Inner layers define interfaces, and outer layers implement them, allowing for loose coupling.
* **Testability:** The clear separation of concerns makes it easy to unit test each layer in isolation.
* **Maintainability:** Changes in one layer have minimal impact on others, simplifying maintenance and updates.
* **Framework Independence:** The core business logic (Domain and Application) is independent of external frameworks like ASP.NET Core or Entity Framework.

---

## Contributing

We welcome contributions to improve this template! Please feel free to open issues or submit pull requests.
