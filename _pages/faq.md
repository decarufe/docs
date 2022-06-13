---
layout: page
title: F.A.Q.
description: Everything you want to know and more!
nav-order: 1
---

# Frequently asked questions

In this section you will find some of the most asked questions **developers** have. 

# How to deal with configuration in your application?

App configuration management and its security is a core element in our software life cycle. It must be secure for sensitive information and should be centralized if configs are shared across multiple services.

## Basic rules:
- Everything considered sensitive or private must be stored in a **secret vault**, i.e., Azure Key Vault.
- Use a different vault for each environment: development, pre-production, and production
- Every secret must have an expiration date and it cannot be greater than 12 months
- or compliance)
- If you want more features around your configuration management, like notification on changes or some configs are **shared across multiple services**, use a service like Azure App Configuration
- Key Vault and App Configuration are not real time databases and excessive requests could cause throttling. Leverage and tune caching or refresh timeouts, especially if your configuration values do not change frequently
- Use managed identities to access Key Vault and App Configuration

## Advanced:
- Leverage the sentinel key pattern  instead of watching multiple configuration keys for changes
- Consider Configuration as code in your software delivery lifecycle

The fewer the better but teams can leverage multiple levels of configurations which can be stacked to offer precedence. From top to bottom, it could be suggested like this:

1.	Azure App Configuration (optional)
2.	Services own configuration (like App Settings in App Services, Functions, etc.)
3.	Azure Key Vault
4.	Local file, i.e., appsettings.json

❗Make sure you understand App Configuration and Key Vault services limits
💡See recommended content for Development/Local and Azure environment guidelines

Sample code: Nothing for now 😔Do you already have something for this or want to contribute ? Reach out to us 😃

## Recommended content
- Centralized app configuration and security - Azure Solution Ideas | Microsoft Docs
- Azure App Configuration best practices | Microsoft Docs
- Azure App Configuration - Configuration as Code | Microsoft Docs
- https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#key-vault-limits
- https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-app-configuration
- https://docs.microsoft.com/en-us/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core?tabs=core5x#add-a-sentinel-key


# How to survive a complete DR in a particular region?

There mainly 2 reasons to perform a complete DR, one feel better than the other:

- A major event occurs with the infrastructure, and a new one must be brought back
- A disaster recovery (DR) drill

Most projects have at different levels of maturity, infrastructure as code that help deploy infrastructure changes all the way up to production. But what about creating a completely new environment? When was the last time you attempted that? Most artifacts are built overtime and sometimes kinda expect existing pieces to be in place in order to work.

There is no magic answer here, you need to practice for that scenario, and do so more than once every 2 years. This is why at least two times a year you should perform a DR drill
