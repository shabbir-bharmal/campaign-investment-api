# Campaign Investment API

Backend API built with .NET Core for managing campaigns, investments, Stripe payments, and marketing/webhook integrations (e.g., Klaviyo).

---

## Table of Contents

- Project Overview
- Tech Stack
- Repository Layout
- Getting Started (Local)
  - Prerequisites
  - Environment Variables
  - Run Locally
- Database & Migrations
---

## Project Overview

This API enables:

- Managing Campaigns & Investments
- Handling Stripe payments
- Receiving and verifying webhooks (Stripe, Klaviyo)
- Providing campaign performance analytics

Layered architecture:


---

## Tech Stack

- .NET 9 / ASP.NET Core Web API
- C# (Entity Models, DTOs, Services, Controllers)
- Entity Framework Core
- SQL Server (local or Azure SQL)
- Stripe (payments & webhooks)
- Klaviyo (marketing & tracking)
- Azure (App Service, SQL, Blob, Insights)
- Swagger for API documentation

---

## Repository Layout
- /Investment.Core # Domain models & DTOs
- /Investment.Repo # EF Core DbContext & Repositories
- /Investment.Service # Business logic & services
- /Investment # ASP.NET Core API project (Controllers, Startup)
- /migrations # EF Core migrations
- .gitignore
- README.md

---

## Getting Started (Local)

### Prerequisites

- [.NET 9 SDK](https://dotnet.microsoft.com)
- SQL Server or LocalDB
- Git
- (Optional) Stripe CLI & ngrok

### Environment Variables

Configure `appsettings.Development.json` or `.env` with:

{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=CampaignDB;User Id=sa;Password=YourPassword;"
  },
  "Stripe": {
    "SecretKey": "sk_test_...",
    "WebhookSecret": "whsec_..."
  },
  "Klaviyo": {
    "ApiKey": "pk_...",
    "WebhookSecret": "kwsec_..."
  },
  "Jwt": {
    "Issuer": "campaign-api",
    "Audience": "campaign-client",
    "Key": "super_secret_key_123"
  }
}


# Clone
git clone https://github.com/your-org/campaign-investment-api.git
cd campaign-investment-api

# Restore packages
dotnet restore

# Apply migrations
dotnet ef database update --project Investment.Repo

# Run the API
dotnet run --project Investment


# Add new migration
dotnet ef migrations add Init --project Investment.Repo

# Apply to DB
dotnet ef database update --project Investment.Repo