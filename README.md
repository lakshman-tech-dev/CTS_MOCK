Lakshmanan S

# Microsoft Azure Learning Journey --- CTS Hackathon

fundamentals to deploying a React + FastAPI + PostgreSQL + AI/ML


## Goal

Build enough practical Azure knowledge to confidently deploy my
final-year project in a secure, scalable, and maintainable way.

### Target Architecture


                    USER
                      │
                      ▼
               React Frontend
                      │
                      ▼
          Azure Static Web Apps
                      │
                      ▼
               FastAPI Backend
                      │
                      ▼
              Azure App Service
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
     PostgreSQL   Blob Storage  Key Vault
          │           │           │
          └───────────┼───────────┘
                      ▼
                AI / ML Models
              Python / Hugging Face
                      │
                      ▼
                Decision Engine
                      │
                      ▼
        Azure Monitor / Application Insights
```

------------------------------------------------------------------------

##Learning Progress

### Completed

-   [x] Cloud Computing Basics
-   [x] On-Premises vs Cloud
-   [x] IaaS / PaaS / SaaS
-   [x] Vertical and Horizontal Scaling
-   [x] Azure Regions
-   [x] Availability Zones
-   [x] Azure Resource Hierarchy
-   [x] Azure Portal
-   [x] Azure CLI Basics
-   [x] Resource Groups
-   [x] Tags
-   [x] Compute Fundamentals
-   [x] Azure Virtual Machines
-   [x] Azure App Service
-   [x] App Service Plans
-   [x] Scaling in App Service

### Next

-   [ ] Azure Networking
-   [ ] Azure Blob Storage
-   [ ] Azure Database for PostgreSQL
-   [ ] Microsoft Entra ID
-   [ ] Azure RBAC
-   [ ] Azure Key Vault
-   [ ] Azure Monitor
-   [ ] Application Insights
-   [ ] Docker
-   [ ] Azure AI / ML Basics
-   [ ] Project Deployment

------------------------------------------------------------------------

# 1. Cloud Computing Basics

## What is Cloud Computing?

Cloud computing means using computing resources over the internet
instead of owning and maintaining physical infrastructure.

Common cloud resources include:

-   Compute
-   Storage
-   Databases
-   Networking
-   AI/ML services

### Major Cloud Providers

  Provider   Company
  ---------- -----------
  AWS        Amazon
  Azure      Microsoft
  GCP        Google

### Key Benefits

-   **Pay-as-you-go** --- pay based on usage
-   **Scalability** --- increase or decrease resources as needed
-   **High availability** --- design applications to remain available
-   **Less hardware maintenance** --- cloud provider manages physical
    infrastructure
-   **Flexibility** --- provision resources quickly

------------------------------------------------------------------------

# 2. On-Premises vs Cloud

## On-Premises

The organization owns and manages its physical infrastructure.

``` text
Organization
     │
     ▼
Own Data Center
     │
     ▼
Physical Servers
     │
     ▼
Applications
```

The organization is responsible for hardware, infrastructure,
maintenance, and much of the software environment.

## Cloud

The organization uses infrastructure and services provided by a cloud
provider.

``` text
Application
     │
     ▼
Cloud Provider
     │
     ▼
Managed Infrastructure
```

The cloud provider manages the underlying physical infrastructure.

------------------------------------------------------------------------

# 3. IaaS, PaaS and SaaS

## IaaS --- Infrastructure as a Service

Example: **Azure Virtual Machines**

The customer manages more of the environment:

-   Application
-   Operating system
-   Configuration
-   Installed software

Azure manages:

-   Physical hardware
-   Data center
-   Underlying infrastructure

> **IaaS → More control, more management**

------------------------------------------------------------------------

## PaaS --- Platform as a Service

Example: **Azure App Service**

The customer mainly provides:

-   Application
-   Application configuration

Azure manages much of:

-   Operating system
-   Infrastructure
-   Platform management

> **PaaS → Focus on the application**

For this project, Azure App Service is the preferred platform for
hosting the FastAPI backend.

------------------------------------------------------------------------

## SaaS --- Software as a Service

The user simply uses the software without managing the underlying
infrastructure.

Examples:

-   Microsoft 365
-   Outlook
-   OneDrive

> **SaaS → Just use it**

------------------------------------------------------------------------

# 4. Scaling

Scaling means adjusting resources according to application workload.

## Scale Up --- Vertical Scaling

Make an existing machine more powerful.

``` text
2 CPU + 4 GB RAM
        │
        ▼
8 CPU + 16 GB RAM
```

> **Scale Up = Bigger**

## Scale Out --- Horizontal Scaling

Add more application instances.

``` text
             Application
             /    |    \
            ▼     ▼     ▼
        Instance Instance Instance
            1        2        3
```

> **Scale Out = More**

------------------------------------------------------------------------

# 5. Azure Regions

A **Region** is a geographic Azure location containing Azure
infrastructure.

Conceptually:

``` text
Azure
├── India
├── United States
└── Europe
```

The selected region can affect:

-   Latency
-   Availability
-   Data residency
-   Pricing
-   Service availability

> **Region = Where in the world**

------------------------------------------------------------------------

# 6. Availability Zones

An **Availability Zone** is a physically separate location within a
supported Azure region.

``` text
Region
├── Zone 1
├── Zone 2
└── Zone 3
```

Using multiple zones can improve application availability by reducing
dependence on a single physical location.

> **Region = Geographic area**

> **Availability Zone = Separate physical location within a region**

------------------------------------------------------------------------

# 7. Azure Resource Hierarchy

Azure resources are organized through several levels:

``` text
Tenant
   │
   ▼
Management Group
   │
   ▼
Subscription
   │
   ▼
Resource Group
   │
   ▼
Resource
```

For a typical individual project, the practical hierarchy is:

``` text
Subscription
     │
     ▼
Resource Group
     │
     ▼
Azure Resources
```

------------------------------------------------------------------------

# 8. Tenant

A **Tenant** is an organization's identity boundary and is associated
with **Microsoft Entra ID**.

It contains and manages identities such as:

-   Users
-   Groups
-   Applications
-   Service identities

------------------------------------------------------------------------

# 9. Management Group

A **Management Group** is used to organize multiple Azure subscriptions.

``` text
Management Group
├── Subscription 1
├── Subscription 2
└── Subscription 3
```

Management Groups are mainly useful for organization-wide governance,
policies, and access management.

> **For this hackathon, Management Groups are not a priority.**

------------------------------------------------------------------------

# 10. Subscription

An Azure **Subscription** is an important management and billing
boundary.

Resources are created within subscriptions.

``` text
Azure Subscription
├── Resource Group A
└── Resource Group B
```

A subscription is also associated with Azure usage and billing.

> **Subscription = Management + Billing boundary**

------------------------------------------------------------------------

# 11. Resource Group

A **Resource Group** is a logical container for related Azure resources.

Example:

``` text
Healthcare-AI-RG
│
├── App Service
├── PostgreSQL
├── Storage Account
├── Key Vault
└── Application Insights
```

Resource Groups help organize, manage, monitor, and clean up resources
belonging to an application or workload.

### Resource Group vs Region

These concepts are different:

``` text
Resource Group
→ Logical organization

Region
→ Geographic location
```

------------------------------------------------------------------------

# 12. Resources

A **Resource** is an actual Azure service or component that you create
and use.

Examples:

-   App Service
-   PostgreSQL
-   Storage Account
-   Key Vault
-   Application Insights
-   Virtual Machine

Example:

``` text
Subscription
     │
     ▼
Healthcare-AI-RG
     │
     ├── App Service
     ├── Storage Account
     └── PostgreSQL
```

------------------------------------------------------------------------

# 13. Azure Portal

The **Azure Portal** is the web-based graphical interface for managing
Azure resources.

``` text
Browser
   │
   ▼
Azure Portal
   │
   ├── Create resources
   ├── Configure resources
   ├── Monitor resources
   └── Manage subscriptions
```

> **Azure Portal = GUI for Azure**

------------------------------------------------------------------------

# 14. Azure CLI

**Azure CLI** is a command-line interface used to manage Azure
resources.

Example:

``` bash
az login
```

List subscriptions:

``` bash
az account list
```

Show the current subscription:

``` bash
az account show
```

Azure CLI is useful for:

-   Automation
-   Scripting
-   Repeatable deployments
-   Managing resources from the terminal

> **Azure Portal = GUI**

> **Azure CLI = Command line**

------------------------------------------------------------------------

# 15. Compute

**Compute** refers to the processing resources used to run applications
and workloads.

Examples:

-   Azure Virtual Machines
-   Azure App Service
-   Azure Functions
-   Containers

The two compute services currently learned are:

-   Azure Virtual Machines
-   Azure App Service

------------------------------------------------------------------------

# 16. Azure Virtual Machine

An Azure Virtual Machine is a virtual computer running in Azure.

``` text
Virtual Machine
├── CPU
├── RAM
├── Disk
├── Operating System
└── Network
```

A VM is an example of **IaaS**.

### Advantages

-   High level of control
-   Control over the operating system
-   Flexible server configuration

### Disadvantages

-   More infrastructure management
-   OS updates and patching
-   Security configuration
-   Server administration

> **VM → IaaS → More control, more management**

------------------------------------------------------------------------

# 17. Azure App Service

**Azure App Service** is a managed platform for hosting web applications
and APIs.

Example:

``` text
FastAPI
   │
   ▼
Azure App Service
   │
   ▼
Internet
```

App Service is an example of **PaaS**.

Azure manages much of the underlying infrastructure and platform.

## Why App Service for this project?

The backend will be built using **FastAPI**.

Instead of manually managing a VM:

``` text
FastAPI
   │
   ▼
Virtual Machine
   │
   ├── Manage OS
   ├── Manage updates
   └── Manage infrastructure
```

I can use:

``` text
FastAPI
   │
   ▼
Azure App Service
```

This reduces infrastructure management and lets me focus on the
application.

------------------------------------------------------------------------

# 18. App Service Plan

An **App Service Plan** provides the compute capacity used by App
Services.

Conceptually:

``` text
App Service Plan
├── CPU
├── RAM
├── Pricing Tier
└── Scaling
       │
       ▼
  App Service
       │
       ▼
    FastAPI
```

The App Service Plan determines the compute resources and certain
platform features available to the application.

------------------------------------------------------------------------

# 19. Scaling in App Service

## Scale Up

Increase the resources available to the App Service Plan.

``` text
Smaller Plan
     │
     ▼
Larger Plan
```

This can provide more:

-   CPU
-   RAM
-   Platform features

## Scale Out

Increase the number of application instances.

``` text
             App Service
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
   Instance 1  Instance 2  Instance 3
```

Scale out allows the application to handle more concurrent traffic.

------------------------------------------------------------------------

# 20. Azure Tags

**Tags** are key-value labels attached to Azure resources.

Example:

``` text
Project     = HealthcareAI
Environment = Development
Owner       = CTS-Hackathon
```

Tags can help with:

-   Organization
-   Cost tracking
-   Resource identification
-   Resource management

------------------------------------------------------------------------

# 🏥 Current Project Architecture

The concepts learned so far lead toward the following target
architecture:

``` text
                    USER
                      │
                      ▼
              React Frontend
                      │
                      ▼
          Azure Static Web Apps
                      │
                      ▼
              FastAPI Backend
                      │
                      ▼
             Azure App Service
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
     PostgreSQL   Blob Storage  Key Vault
          │           │           │
          └───────────┼───────────┘
                      ▼
                AI / ML Models
              Python / Hugging Face
                      │
                      ▼
                Decision Engine
                      │
                      ▼
          Azure Monitor / Application
                  Insights
```


------------------------------------------------------------------------

# 🧠 Quick Reference

  Concept             Mental Model
  ------------------- ----------------------------------
  IaaS                More control
  PaaS                Focus on application
  SaaS                Just use it
  Scale Up            Bigger
  Scale Out           More
  Region              Where in the world
  Availability Zone   Separate physical location
  Tenant              Identity boundary
  Management Group    Organizes subscriptions
  Subscription        Management + billing boundary
  Resource Group      Logical container
  Resource            Actual Azure service
  Azure Portal        Azure GUI
  Azure CLI           Azure command line
  VM                  Virtual computer
  App Service         Managed application hosting
  App Service Plan    Compute capacity for App Service
  Tags                Resource labels

------------------------------------------------------------------------

LEARNING DOCKER AND HANDS ON

DEPLOYING A FASTAPI IN AZURE APP SERVICE



