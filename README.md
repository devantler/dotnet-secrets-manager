# 🔓 .NET Secret Manager

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Test](https://github.com/devantler/dotnet-secret-manager/actions/workflows/test.yaml/badge.svg)](https://github.com/devantler/dotnet-secret-manager/actions/workflows/test.yaml)
[![codecov](https://codecov.io/gh/devantler/dotnet-secret-manager/graph/badge.svg?token=RhQPb4fE7z)](https://codecov.io/gh/devantler/dotnet-secret-manager)

A simple .NET library to manage cryptographic keys.

<details>
  <summary>Show/hide folder structure</summary>

<!-- readme-tree start -->
```
.
├── .github
│   └── workflows
├── Devantler.SecretManager.Core
├── Devantler.SecretManager.SOPS.LocalAge
│   ├── Models
│   └── Utils
└── Devantler.SecretManager.SOPS.LocalAge.Tests
    ├── SOPSLocalAgeSecretManagerTests
    └── Utils
        └── SOPSConfigHelperTests

11 directories
```
<!-- readme-tree end -->

</details>

## Prerequisites

- [.NET](https://dotnet.microsoft.com/en-us/)

## 🚀 Getting Started

To get started, you can install the packages from NuGet.

```bash
# For the Age key model
dotnet add package Devantler.SecretManager.SOPS.LocalAge
```

If you need to create a new implementation for a secret manager, you can install the core package.

```bash
dotnet add package Devantler.Keys.Core
```

## 📝 Usage

### Local Age Secret Manager

The Local Age Secret Manager is a simple secret manager to manage Age keys on your local machine. The secret manager saves and loads keys from your SOPS keyring by default.

#### Create a new key

To create a new key, you can use the `CreateKeyAsync` method.

```csharp
using Devantler.SecretManager.SOPS.LocalAge;

var SecretManager = new SOPSLocalAgeSecretManager();

var key = await SecretManager.CreateKeyAsync();
```

To delete a key, you can use the `DeleteKeyAsync` method.

```csharp
using Devantler.Keys.Age;
using Devantler.SecretManager.SOPS.LocalAge;

var SecretManager = new SOPSLocalAgeSecretManager();

var ageKey = AgeKeygen.InMemory();
await SecretManager.DeleteKeyAsync(ageKey);
```

#### Get an existing key

To get an existing key, you can use the `GetKeyAsync` method.

```csharp
using Devantler.SecretManager.SOPS.LocalAge;

var SecretManager = new SOPSLocalAgeSecretManager();

var key = await SecretManager.GetKeyAsync("<public key>");
```

#### Import a key

To import a key, you can use the `ImportKeyAsync` method.

```csharp
using Devantler.Keys.Age;
using Devantler.SecretManager.SOPS.LocalAge;

var SecretManager = new SOPSLocalAgeSecretManager();

var ageKey = AgeKeygen.InMemory();

var key = await SecretManager.ImportKeyAsync(ageKey);
```

#### Check if a key exists

To check if a key exists, you can use the `KeyExistsAsync` method.

```csharp
using Devantler.SecretManager.SOPS.LocalAge;

var SecretManager = new SOPSLocalAgeSecretManager();

var exists = await SecretManager.KeyExistsAsync("<public key>");
```

#### List all keys

To list all keys, you can use the `ListKeysAsync` method.

```csharp
using Devantler.SecretManager.SOPS.LocalAge;

var SecretManager = new SOPSLocalAgeSecretManager();

var keys = await SecretManager.ListKeysAsync();
```
