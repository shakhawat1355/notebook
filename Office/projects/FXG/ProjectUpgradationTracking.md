#  FXCG.API.KeyManager

---

### 1. Libraries and Their Version Upgrades
Below is the list of libraries with their version upgrades when transitioning from the old project to the new project:

- **Newtonsoft.Json**: `12.0.3` -> `13.0.3`
- **System.Diagnostics.DiagnosticSource**: `4.0.1.0` -> `4.3.0`
- **System.Security.Cryptography.Algorithms**: `4.1.0.0` -> `4.2.1.0`
- **System.Security.Cryptography.X509Certificates**: `4.1.1.0` -> `4.3.0`
- **System.Runtime.InteropServices.RuntimeInformation**: `4.0.0.0` -> `4.3.0`
- **System.Runtime.CompilerServices.Unsafe**: Not present -> `5.0.0`
- **MongoDB.Bson**: Not present -> `2.19.0`
- **MongoDB.Driver**: Not present -> `2.19.0`
- **MongoDB.Driver.Core**: Not present -> `2.19.0`
- **MongoDB.Libmongocrypt**: Not present -> `1.9.0`
- **AWSSDK.Core**: Not present -> `3.7.100.14`
- **AWSSDK.SecurityToken**: Not present -> `3.7.100.14`
- **DnsClient**: Not present -> `1.6.1`
- **SharpCompress**: Not present -> `0.30.1`
- **Snappier**: Not present -> `1.0.0`
- **ZstdSharp**: Not present -> `0.7.3`
- **System.Memory**: Not present -> `4.5.5`
- **System.Buffers**: Not present -> `4.5.1`
- **System.Numerics.Vectors**: Not present -> `4.5.0`
- **System.Security.AccessControl**: Not present -> `5.0.0`
- **System.Security.Principal.Windows**: Not present -> `5.0.0`
- **System.Text.Encoding.CodePages**: Not present -> `5.0.0`
- **System.Threading.Tasks.Extensions**: Not present -> `4.5.4`

---

### 2. Code Changes Between Old and New Projects
Below is the comparison of changes made in the code files after upgrading to the new framework and libraries:

#### **ApiKeyManager.cs**
- **No significant code changes detected**: The content of the `ApiKeyManager.cs` file in both repositories is identical. No methods were modified or added.

#### **app.config**
- **File Description**: The `app.config` file has been updated to include new assembly binding redirects for additional libraries and upgraded versions:
  - **Added bindings**:
    - `System.Memory`: `4.0.1.2` -> `4.0.1.2`
    - `System.Buffers`: `4.0.3.0` -> `4.0.3.0`
    - `System.Runtime.CompilerServices.Unsafe`: `5.0.0.0`
    - `MongoDB.Bson`: `3.0.0.0`
    - `MongoDB.Driver`: `3.0.0.0`
    - `ZstdSharp`: `0.7.3.0`
  - **Upgraded binding**:
    - `Newtonsoft.Json`: `12.0.0.0` -> `13.0.0.0`

#### **FXCG.API.KeyManager.csproj**
- **File Description**: The project file has been updated to target `.NET Framework 4.8` and include references to new libraries. Key changes include:
  - **Target Framework**: Updated from `v4.6.1` to `v4.8`.
  - **Added References**:
    - `AWSSDK.Core`
    - `AWSSDK.SecurityToken`
    - `DnsClient`
    - `MongoDB.*` libraries
    - `SharpCompress`
    - `Snappier`
    - `ZstdSharp`
    - `System.Memory`
    - `System.Buffers`
    - `System.Numerics.Vectors`
    - `System.Security.AccessControl`
    - `System.Security.Principal.Windows`
    - `System.Text.Encoding.CodePages`
    - `System.Threading.Tasks.Extensions`
  - **Updated References**:
    - `Newtonsoft.Json`: `12.0.3` -> `13.0.3`
    - `System.Diagnostics.DiagnosticSource`: `4.0.1.0` -> `4.3.0`
    - `System.Security.Cryptography.Algorithms`: `4.1.0.0` -> `4.2.1.0`

#### **packages.config**
- **File Description**: The `packages.config` file has been updated to include new NuGet packages and upgraded versions:
  - **Added packages**:
    - `AWSSDK.Core`
    - `AWSSDK.SecurityToken`
    - `DnsClient`
    - `MongoDB.*` libraries
    - `SharpCompress`
    - `Snappier`
    - `ZstdSharp`
    - `System.Memory`
    - `System.Buffers`
    - `System.Numerics.Vectors`
    - `System.Security.AccessControl`
    - `System.Security.Principal.Windows`
    - `System.Text.Encoding.CodePages`
    - `System.Threading.Tasks.Extensions`
  - **Upgraded packages**:
    - `Newtonsoft.Json`: `12.0.3` -> `13.0.3`
    - `System.Diagnostics.DiagnosticSource`: `4.0.1.0` -> `4.3.0`

---

### 3. Additional Notable Changes
Below are any additional changes observed in the new repository:

#### **.vs/FXCG.API.KeyManager.csproj.dtbcache.json**
- **Location**: `.vs/FXCG.API.KeyManager.csproj.dtbcache.json`
- **Description**: This is a Visual Studio cache file related to the `.csproj` project. It contains metadata about the project structure, sources, and references. This file is new and was not present in the old repository.

#### **libmongocrypt.dylib and libmongocrypt.so**
- **Location**: Project root directory
- **Description**: These binary files for MongoDB encryption support are included in the new project. They were not present in the old repository.

#### **mongocrypt.dll**
- **Location**: Project root directory
- **Description**: A new binary file for MongoDB encryption support has been added in the new repository.

---

### Summary
The upgrade to `.NET Framework 4.8` involved:
1. Adding new libraries such as `MongoDB`, `AWS SDK`, `SharpCompress`, etc.
2. Upgrading existing libraries like `Newtonsoft.Json` and `System.Diagnostics.DiagnosticSource`.
3. Updating the `app.config` and `packages.config` files to reflect the new dependencies.
4. No significant code changes in `ApiKeyManager.cs`.
5. Adding new binary files for MongoDB encryption (`libmongocrypt` and `mongocrypt.dll`).











#  FXCG.BatchFileTransformations

---

 

### 1. Libraries and Their Version Upgrades

```
[ExcelDataReader] : 2.1.2.3 -> 2.1.2.3 (No change)
[SharpZipLib] : 0.86.0 -> 0.86.0 (No change)
[System.Net.Http] : Base -> 4.3.4 (Added version)
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[Newtonsoft.Json] : Not present -> 13.0.3
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Numerics.Vectors] : Not present -> 4.5.0
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Security.AccessControl] : Not present -> 5.0.0
[System.Security.Principal.Windows] : Not present -> 5.0.0
[System.Text.Encoding.CodePages] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

### 2. Code Changes Between Projects

```
BatchFileUtil.cs : No changes detected in the code implementation.

FXCG.BatchFileTransformations.csproj : 
- Updated target framework from v4.6.1 to v4.8
- Added new NuGet package references for MongoDB, AWS SDK, and various System libraries
- Added new build targets for MongoDB.Libmongocrypt

app.config : 
- Added new assembly binding redirects for:
  - System.Memory
  - System.Buffers
  - System.Runtime.CompilerServices.Unsafe
  - MongoDB.Bson
  - MongoDB.Driver
  - ZstdSharp

Models/* : No changes detected in any of the model classes
```

### 3. Additional Notable Changes

```
[libmongocrypt.dylib]-[Project Root]- New binary file added for MongoDB encryption support on macOS
[libmongocrypt.so]-[Project Root]- New binary file added for MongoDB encryption support on Linux
[mongocrypt.dll]-[Project Root]- New binary file added for MongoDB encryption support on Windows
[.vs/FXCG.BatchFileTransformations.csproj.dtbcache.json]-[.vs folder]- New Visual Studio cache file for project configuration
```

The main changes revolve around upgrading the framework version and adding support for MongoDB and AWS SDK, while maintaining the existing business logic intact.

#  FXCG.Common

---



1. Library Version Upgrades:
```
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.0 -> 4.3.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[Newtonsoft.Json] : Not present -> 13.0.3
[SSH.NET] : 2016.1.0 -> 2016.1.0 (unchanged)
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
```

2. Code Changes:
```
app.config : Added new assembly bindings for MongoDB, System.Memory, System.Buffers, System.Runtime.CompilerServices.Unsafe, and ZstdSharp
FXCG.Common.csproj : 
- Updated target framework from 4.6.1 to 4.8
- Added multiple new package references for MongoDB integration
- Added new build configurations (ACC, PROD, STAGE, HOTFIX)
```

3. Notable Changes:
```
FXCG.Common.csproj - [Framework] - Updated from .NET Framework 4.6.1 to 4.8
app.config - [Dependencies] - Added multiple new assembly binding redirects for MongoDB and related packages
packages.config - [Dependencies] - Added numerous new NuGet packages primarily for MongoDB integration
.vs/FXCG.Common.csproj.dtbcache.json - [New File] - Added Visual Studio cache file for the project
```

The main changes appear to be:
1. Framework upgrade from 4.6.1 to 4.8
2. Major addition of MongoDB related packages and dependencies
3. Addition of new build configurations
4. No significant changes to the actual code logic, mostly infrastructure and dependency updates


#  FXCG.Digital.Signature

---

 

1. Library Version Upgrades:
```
[Newtonsoft.Json] : 12.0.3 -> 13.0.3
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.1.0 -> 4.3.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
```

2. Code Changes:
```
app.config : Added new assembly bindings for MongoDB, System.Memory, System.Buffers, System.Runtime.CompilerServices.Unsafe, and ZstdSharp
No functional code changes detected in the following files:
- EncryptionKeySet.cs
- FXQuoteSignature.cs
- Utility.cs
```

3. Notable Changes:
```
[FXCG.Digital.Signature.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[app.config]-[Dependencies] - Added multiple new assembly binding redirects for MongoDB and related packages
[packages.config]-[Dependencies] - Added numerous new NuGet packages primarily for MongoDB integration
[.vs/FXCG.Digital.Signature.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file for the project
[Project]-[Build Configurations] - Added new build configurations (ACC, PROD, STAGE, HOTFIX)
```

The main changes appear to be:
1. Framework upgrade from 4.6.1 to 4.8
2. Major addition of MongoDB related packages and dependencies
3. Addition of new build configurations
4. No significant changes to the actual code logic, mostly infrastructure and dependency updates

The upgrade was primarily focused on updating the framework version and adding new dependencies rather than modifying existing functionality.

#  FXCG.Domain.Model

---



1. Library Version Upgrades:
```
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.1.0 -> 4.3.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0  
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[Newtonsoft.Json] : 12.0.3 -> 13.0.3
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
```

2. Code Changes:
```
app.config : Added new assembly bindings for MongoDB, System.Memory, System.Buffers, System.Runtime.CompilerServices.Unsafe, and ZstdSharp

FXCG.Domain.Model.csproj :
- Updated target framework from 4.6.1 to 4.8
- Added MongoDB related package references
- Added AWS SDK package references
- Added new build configurations (ACC, PROD, STAGE, HOTFIX)
```

3. Notable Changes:
```
[FXCG.Domain.Model.csproj]-[Framework] - Updated from .NET Framework 4.6.1 to 4.8
[app.config]-[Dependencies] - Added multiple new assembly binding redirects for MongoDB and related packages
[packages.config]-[Dependencies] - Added numerous new NuGet packages primarily for MongoDB and AWS integration
[Project]-[Build Configurations] - Added new build configurations (ACC, PROD, STAGE, HOTFIX)
[Project]-[Dependencies] - Added MongoDB and AWS SDK dependencies
```

The main changes appear to be:
1. Framework upgrade from 4.6.1 to 4.8
2. Major addition of MongoDB related packages and dependencies
3. Addition of AWS SDK packages
4. Addition of new build configurations
5. No significant changes to the actual code logic, mostly infrastructure and dependency updates

The upgrade focused on updating the framework version and adding new database and cloud service dependencies rather than modifying existing functionality.

#  FXCG.Domain.Repository

---


1. Library Version Upgrades:
```
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.1.0 -> 4.3.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[ZstdSharp] : Not present -> 0.7.3
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Security.AccessControl] : Not present -> 5.0.0
[System.Security.Principal.Windows] : Not present -> 5.0.0
[System.Text.Encoding.CodePages] : Not present -> 5.0.0
```

2. Code Changes:
```
app.config : Added new assembly bindings for MongoDB, System.Memory, System.Buffers, System.Runtime.CompilerServices.Unsafe, ZstdSharp and other MongoDB related dependencies

FXCG.Domain.Repository.csproj :
- Updated target framework from 4.6.1 to 4.8
- Added MongoDB related package references
- Added AWS SDK package references
- Added new build configurations (ACC, PROD, STAGE, HOTFIX)
```

3. Notable Changes:
```
[FXCG.Domain.Repository.csproj]-[Framework] - Updated from .NET Framework 4.6.1 to 4.8
[app.config]-[Dependencies] - Added multiple new assembly binding redirects for MongoDB and related packages
[packages.config]-[Dependencies] - Added numerous new NuGet packages primarily for MongoDB and AWS integration
[Project]-[Build Configurations] - Added new build configurations (ACC, PROD, STAGE, HOTFIX)
[Project]-[Dependencies] - Added MongoDB and AWS SDK dependencies
[.vs/FXCG.Domain.Repository.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file for the project
```

The main changes appear to be:
1. Framework upgrade from 4.6.1 to 4.8
2. Major addition of MongoDB related packages and dependencies 
3. Addition of AWS SDK packages
4. Addition of new build configurations
5. No significant changes to the actual repository code logic, mostly infrastructure and dependency updates

The upgrade focused on updating the framework version and adding new database and cloud service dependencies rather than modifying existing functionality.

#  FXCG.Domain.Services

---

1. Library Version Upgrades:
```
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.1.0 -> 4.3.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[Newtonsoft.Json] : 12.0.3 -> 13.0.3
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Security.AccessControl] : Not present -> 5.0.0
[System.Security.Principal.Windows] : Not present -> 5.0.0
[System.Text.Encoding.CodePages] : Not present -> 5.0.0
[ZstdSharp] : Not present -> 0.7.3
```

2. Code Changes:
```
app.config : 
- Updated assembly bindings for MongoDB related packages
- Added new assembly bindings for System.Memory, System.Buffers, System.Runtime.CompilerServices.Unsafe
- Added ZstdSharp binding
- Added supportedRuntime element for .NET Framework 4.8

FXCG.Domain.Services.csproj :
- Updated target framework from 4.6.1 to 4.8
- Added MongoDB related package references 
- Added AWS SDK package references
- Added new build configurations (ACC, PROD, STAGE, HOTFIX)
```

3. Notable Changes:
```
[FXCG.Domain.Services.csproj]-[Framework] - Updated from .NET Framework 4.6.1 to 4.8
[app.config]-[Dependencies] - Added multiple new assembly binding redirects for MongoDB and related packages
[packages.config]-[Dependencies] - Added numerous new NuGet packages primarily for MongoDB and AWS integration
[Project]-[Build Configurations] - Added new build configurations (ACC, PROD, STAGE, HOTFIX)
[Project]-[Dependencies] - Added MongoDB and AWS SDK dependencies
[.vs/FXCG.Domain.Services.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file for the project
```

The main changes appear to be:
1. Framework upgrade from 4.6.1 to 4.8
2. Major addition of MongoDB related packages and dependencies
3. Addition of AWS SDK packages 
4. Addition of new build configurations
5. No significant changes to the actual service code logic, mostly infrastructure and dependency updates

The upgrade focused on updating the framework version and adding new database and cloud service dependencies rather than modifying existing functionality.

#  FXCG.EmailUtility

---


1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
EmailServerSettings.cs : No functional changes, only commented code for C#7 syntax alternatives in SetFromConfigFile() method

No other code changes were detected between old and new versions as the core functionality remains the same
```

3. Notable Changes:
```
[FXCG.EmailUtility.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.EmailUtility.csproj]-[Dependencies] - Added MongoDB related package references and AWS SDK dependencies
[app.config]-[New File] - Added new assembly binding redirects for MongoDB, System.Memory, System.Buffers etc.
[packages.config]-[New File] - Added configuration for new NuGet packages
[Project]-[Build Configurations] - Added new build configurations (ACC, PROD, STAGE, HOTFIX)
[Project]-[Files] - Added mongocrypt.dll, libmongocrypt.dylib, libmongocrypt.so for MongoDB support
```

The main changes appear to be infrastructure-related:
1. Framework upgrade from 4.6.1 to 4.8
2. Addition of MongoDB support packages
3. Addition of AWS SDK support
4. Additional build configurations
5. No significant changes to the actual email utility code logic

The upgrade focused on updating the framework version and adding new database/cloud service dependencies rather than modifying existing functionality.

#  FXCG.FXModule.FXProvider.Moneycorp

---



1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[System.Net.Http] : 4.1.1.2 -> 4.1.1.3
[Newtonsoft.Json] : 12.0.0 -> 13.0.3
[SSH.NET] : 2016.1.0 -> 2016.1.0 (unchanged)
[System.Security.Cryptography.Algorithms] : 4.3.0 -> 4.3.0 (unchanged)
[System.Security.Cryptography.Encoding] : 4.3.0 -> 4.3.0 (unchanged)
[System.Security.Cryptography.Primitives] : 4.3.0 -> 4.3.0 (unchanged)
[System.Security.Cryptography.X509Certificates] : 4.3.0 -> 4.3.0 (unchanged)
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes were detected between old and new versions. The core business logic remains the same across all files.
```

3. Notable Changes:
```
[FXCG.FXModule.FXProvider.Moneycorp.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.FXModule.FXProvider.Moneycorp.csproj]-[Dependencies] - Added MongoDB related package references and AWS SDK dependencies
[App.config]-[Assembly Bindings] - Added new binding redirects for MongoDB, System.Memory, System.Buffers etc.
[App.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[packages.config]-[New File] - Added configuration for new NuGet packages
[Project]-[Build Configurations] - Added new build configurations (ACC, PROD, STAGE, HOTFIX)
[Project]-[Files] - Added mongocrypt.dll, libmongocrypt.dylib, libmongocrypt.so for MongoDB support
[.vs/FXCG.FXModule.FXProvider.Moneycorp.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file
```

The main changes appear to be infrastructure-related:
1. Framework upgrade from 4.6.1 to 4.8
2. Addition of MongoDB support packages
3. Addition of AWS SDK support
4. Additional build configurations
5. No changes to the actual business logic code

The upgrade focused on updating the framework version and adding new database/cloud service dependencies rather than modifying existing functionality.

#  FXCG.FXModule.FXProvider.XeCom

---


1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[System.Net.Http] : 4.3.3 -> 4.3.4
[Newtonsoft.Json] : 12.0.3 -> 13.0.3
[System.Security.Cryptography.Algorithms] : 4.3.0 -> 4.3.0 (unchanged)
[System.Security.Cryptography.Encoding] : 4.3.0 -> 4.3.0 (unchanged)
[System.Security.Cryptography.Primitives] : 4.3.0 -> 4.3.0 (unchanged)
[System.Security.Cryptography.X509Certificates] : 4.3.0 -> 4.3.0 (unchanged)
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes were detected between old and new versions. The core business logic remains the same across all files.
```

3. Notable Changes:
```
[FXCG.FXModule.FXProvider.XeCom.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.FXModule.FXProvider.XeCom.csproj]-[Dependencies] - Added MongoDB related package references and AWS SDK dependencies
[app.config]-[Assembly Bindings] - Added new binding redirects for MongoDB, System.Memory, System.Buffers etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[packages.config]-[Dependencies] - Added new NuGet package references
[Project]-[Build] - Added NuGetPackageImportStamp property
[Project]-[Files] - Added mongocrypt.dll, libmongocrypt.dylib, libmongocrypt.so for MongoDB support
[.vs/FXCG.FXModule.FXProvider.XeCom.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file
```

The main changes appear to be infrastructure-related:
1. Framework upgrade from 4.6.1 to 4.8
2. Addition of MongoDB support packages
3. Addition of AWS SDK support
4. No changes to the actual business logic code

The upgrade focused on updating the framework version and adding new database/cloud service dependencies rather than modifying existing functionality.

#  FXCG.FXModule

---



1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.1.0 -> 4.3.0
[Newtonsoft.Json] : 6.0.0.0 -> 13.0.2
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes were detected between old and new versions. The core business logic remains the same across all files.
```

3. Notable Changes:
```
[FXCG.FXModule.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.FXModule.csproj]-[Dependencies] - Added MongoDB related package references and AWS SDK dependencies
[app.config]-[Assembly Bindings] - Added new binding redirects for MongoDB, System.Memory, System.Buffers etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[packages.config]-[New File] - Added configuration for new NuGet packages
[Project]-[Build Configurations] - Added new build configurations (ACC, PROD, STAGE, HOTFIX)
[Project]-[Files] - Added mongocrypt.dll, libmongocrypt.dylib, libmongocrypt.so for MongoDB support
[.vs/FXCG.FXModule.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file
```

The main changes appear to be infrastructure-related:
1. Framework upgrade from 4.6.1 to 4.8
2. Addition of MongoDB support packages
3. Addition of AWS SDK support
4. Additional build configurations
5. No changes to the actual business logic code

The upgrade focused on updating the framework version and adding new database/cloud service dependencies rather than modifying existing functionality.

#  FXCG.FXProviderUtility

---


1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[Microsoft.VisualStudio.SlowCheetah] : 4.0.8 -> 4.0.8 (unchanged)
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes were detected. The core business logic in FXProviderFeedSelector.cs, FXProviderSelector.cs and ProviderFeedConfig.cs remains identical between versions.
```

3. Notable Changes:
```
[FXCG.FXProviderUtility.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.FXProviderUtility.csproj]-[Dependencies] - Added MongoDB related package references and AWS SDK dependencies
[FXCG.FXProviderUtility.csproj]-[Build] - Added MongoDB.Libmongocrypt.targets import
[app.config]-[Assembly Bindings] - Added new binding redirects for MongoDB, System.Memory, System.Buffers etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Files] - Added mongocrypt.dll, libmongocrypt.dylib, libmongocrypt.so for MongoDB support
[.vs/FXCG.FXProviderUtility.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file
[Configurations/]-[Files] - Configuration files for different environments (ACC, PROD, STAGE, HOTFIX) remain unchanged
```

The main changes appear to be infrastructure-related:
1. Framework upgrade from 4.6.1 to 4.8
2. Addition of MongoDB support packages and related files
3. Addition of AWS SDK support
4. No changes to the actual business logic code or configuration files

The upgrade focused on updating the framework version and adding new database/cloud service dependencies rather than modifying existing functionality.

#  FXCG.Logging

---


1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.0 -> 4.3.0
[System.Net.Http] : Not present -> 4.3.4
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[Newtonsoft.Json] : Not present -> 13.0.3
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes were detected. The files AuthLog.cs, Base/LoggingBase.cs, EventLogger.cs and LogEntryTypeEnum.cs remain identical between versions.
```

3. Notable Changes:
```
[FXCG.Logging.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.Logging.csproj]-[Dependencies] - Added MongoDB related package references and AWS SDK dependencies
[FXCG.Logging.csproj]-[Build] - Added MongoDB.Libmongocrypt.targets import
[app.config]-[Assembly Bindings] - Added new binding redirects for MongoDB, System.Memory, System.Buffers etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Files] - Added mongocrypt.dll, libmongocrypt.dylib, libmongocrypt.so for MongoDB support
[.vs/FXCG.Logging.csproj.dtbcache.json]-[New File] - Added Visual Studio cache file
```

The main changes appear to be infrastructure-related:
1. Framework upgrade from 4.6.1 to 4.8
2. Addition of MongoDB support packages and related files
3. Addition of AWS SDK support
4. No changes to the actual business logic code

The upgrade focused on updating the framework version and adding new database/cloud service dependencies rather than modifying existing functionality.



#  FXCG.Mongo.Common

---

1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[MongoDB.Bson] : 2.4.4 -> 2.19.0
[MongoDB.Driver] : 2.4.4 -> 2.19.0
[MongoDB.Driver.Core] : 2.4.4 -> 2.19.0
[MongoDB.Driver.GridFS] : 2.4.4 -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.27
[AWSSDK.SecurityToken] : Not present -> 3.7.100.27
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[Newtonsoft.Json] : Not present -> 13.0.3
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Runtime.InteropServices.RuntimeInformation] : 4.0.0 -> 4.3.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes detected. The source code files remain identical between versions.
```

3. Notable Changes:
```
[FXCG.Mongo.Common.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.Mongo.Common.csproj]-[Dependencies] - Added multiple new package references including AWS SDK, MongoDB.Libmongocrypt, and supporting libraries
[app.config]-[Assembly Bindings] - Added new binding redirects for System.Memory, System.Buffers, MongoDB.Bson, etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Build] - Added MongoDB.Libmongocrypt.targets import
[Project]-[Content] - Added mongocrypt.dll as content file
```

This appears to be primarily a framework upgrade and dependency modernization, with no functional code changes. The main changes involve updating to .NET Framework 4.8 and bringing in newer versions of MongoDB drivers along with their dependencies.

#  FXCG.Mongo.Provider

---

1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[MongoDB.Bson] : 2.4.4 -> 2.19.0
[MongoDB.Driver] : 2.4.4 -> 2.19.0
[MongoDB.Driver.Core] : 2.4.4 -> 2.19.0
[MongoDB.Driver.GridFS] : 2.4.4 -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[AWSSDK.Core] : Not present -> 3.7.100.27
[AWSSDK.SecurityToken] : Not present -> 3.7.100.27
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[Newtonsoft.Json] : Not present -> 13.0.3
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
MongoRepositoryBase.cs : Updated GridFS operations to use new MongoDB.Driver.GridFS API
MongoConnection.cs : Updated GridFSBucket implementation to replace deprecated GridFS methods
Extensions.cs : Updated query expression building to use new FilterDefinition approach
QueryHelper.cs : Updated query building to use new MongoDB.Driver filter builders
```

3. Notable Changes:
```
[app.config]-[Assembly Bindings] - Added new binding redirects for MongoDB.Bson, System.Memory, System.Buffers, etc.
[app.config]-[Runtime] - Added .NET Framework 4.8 runtime support
[FXCG.Mongo.Provider.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.Mongo.Provider.csproj]-[Dependencies] - Added multiple new package references including AWS SDK and MongoDB.Libmongocrypt
[Project]-[Build] - Added MongoDB.Libmongocrypt.targets import
[Project]-[Content] - Added mongocrypt.dll as content file
[MongoRepositoryBase.cs]-[GridFS] - Replaced deprecated GridFS methods with new GridFSBucket API
[MongoConnection.cs]-[Database] - Updated database connection and operations to use newer MongoDB.Driver APIs
```

The main changes involve:
1. Framework upgrade from 4.6.1 to 4.8
2. Major MongoDB driver upgrade from 2.4.4 to 2.19.0
3. Addition of new dependencies for enhanced MongoDB functionality
4. Code updates to use newer MongoDB.Driver APIs, especially around GridFS operations
5. Updated query building and filter definitions to match newer MongoDB driver patterns

#  FXCG.PaymentModule.Integration

---
1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[Newtonsoft.Json] : 6.0.0.0 -> 13.0.3
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes detected between versions. The source code files (IPaymentGateway.cs, GatewayBase.cs, and ProcessInstructionResult.cs) remain identical.
```

3. Notable Changes:
```
[FXCG.PaymentModule.Integration.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.PaymentModule.Integration.csproj]-[Dependencies] - Added multiple new package references including AWS SDK, MongoDB drivers and supporting libraries
[app.config]-[Assembly Bindings] - Added new binding redirects for System.Memory, System.Buffers, MongoDB.Bson, etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Build] - Added MongoDB.Libmongocrypt.targets import
[Project]-[Content] - Added mongocrypt.dll, libmongocrypt.dylib and libmongocrypt.so as content files
[Project]-[NuGet] - Added NuGetPackageImportStamp property
```

The main changes involve:
1. Framework upgrade from 4.6.1 to 4.8
2. Major Newtonsoft.Json upgrade from 6.0.0 to 13.0.3
3. Addition of MongoDB driver packages and dependencies
4. Addition of AWS SDK packages
5. Addition of various supporting libraries for improved performance and functionality
6. No changes to the actual code logic - purely infrastructure/framework updates

#  FXCG.PaymentModule

---

 

1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[Newtonsoft.Json] : Not present -> 13.0.3
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes detected. The source code files remain identical between versions.
```

3. Notable Changes:
```
[FXCG.PaymentModule.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.PaymentModule.csproj]-[Dependencies] - Added multiple new package references including AWS SDK, MongoDB drivers and supporting libraries
[app.config]-[Assembly Bindings] - Added new binding redirects for System.Memory, System.Buffers, MongoDB.Bson, etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Build] - Added MongoDB.Libmongocrypt.targets import
[Project]-[Content] - Added mongocrypt.dll, libmongocrypt.dylib and libmongocrypt.so as content files
```

The main changes involve:
1. Framework upgrade from 4.6.1 to 4.8
2. Addition of MongoDB driver packages and dependencies
3. Addition of AWS SDK packages
4. Addition of various supporting libraries for improved performance and functionality
5. No changes to the actual code logic - purely infrastructure/framework updates

#  FXCG.PaymentModule.PaymentGateway.Computop

---

1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[Microsoft.VisualStudio.SlowCheetah] : 3.2.26 -> 3.2.26 (no change)
[Newtonsoft.Json] : 6.0.0.0 -> 13.0.3
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes detected. The source code files remain identical between versions.
```

3. Notable Changes:
```
[FXCG.PaymentModule.PaymentGateway.Computop.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.PaymentModule.PaymentGateway.Computop.csproj]-[Dependencies] - Added multiple new package references including AWS SDK, MongoDB drivers and supporting libraries
[app.config]-[Assembly Bindings] - Added new binding redirects for System.Memory, System.Buffers, MongoDB.Bson, etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Build] - Added MongoDB.Libmongocrypt.targets import
[Project]-[Content] - Added mongocrypt.dll, libmongocrypt.dylib and libmongocrypt.so as content files
```

The main changes involve:
1. Framework upgrade from 4.6.1 to 4.8
2. Major Newtonsoft.Json upgrade from 6.0.0 to 13.0.3
3. Addition of MongoDB driver packages and dependencies
4. Addition of AWS SDK packages
5. Addition of various supporting libraries for improved performance and functionality
6. No changes to the actual code logic - purely infrastructure/framework updates

#  FXCG.PaymentModule.PaymentGateway.Emerchantpay

---


1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[pMixins] : 0.6.0.455-prerelease -> 0.6.0.476-prerelease
[Newtonsoft.Json] : 6.0.0.0 -> 13.0.3
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
[DnsClient] : Not present -> 1.6.1
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Extensions.Logging.Abstractions] : Not present -> 2.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[MongoDB.Bson] : Not present -> 2.19.0
[MongoDB.Driver] : Not present -> 2.19.0
[MongoDB.Driver.Core] : Not present -> 2.19.0
[MongoDB.Driver.GridFS] : Not present -> 2.19.0
[MongoDB.Libmongocrypt] : Not present -> 1.9.0
[SharpCompress] : Not present -> 0.30.1
[Snappier] : Not present -> 1.0.0
[System.Buffers] : Not present -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[System.Threading.Tasks.Extensions] : Not present -> 4.5.4
[ZstdSharp.Port] : Not present -> 0.7.3
```

2. Code Changes:
```
No functional code changes detected. The source code files (EmerchantpayPaygate.cs and GenesisUtility.cs) remain identical between versions.
```

3. Notable Changes:
```
[FXCG.PaymentModule.PaymentGateway.Emerchantpay.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.PaymentModule.PaymentGateway.Emerchantpay.csproj]-[Dependencies] - Added multiple new package references including AWS SDK, MongoDB drivers and supporting libraries
[app.config]-[Assembly Bindings] - Added new binding redirects for System.Memory, System.Buffers, MongoDB.Bson, etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Build] - Added MongoDB.Libmongocrypt.targets import
[Project]-[Content] - Added mongocrypt.dll, libmongocrypt.dylib and libmongocrypt.so as content files
[Project]-[NuGet] - Added NuGetPackageImportStamp property
```

The main changes involve:
1. Framework upgrade from 4.6.1 to 4.8
2. Major Newtonsoft.Json upgrade from 6.0.0 to 13.0.3
3. Minor pMixins version update
4. Addition of MongoDB driver packages and dependencies
5. Addition of AWS SDK packages
6. Addition of various supporting libraries for improved performance and functionality
7. No changes to the actual code logic - purely infrastructure/framework updates

#  FXCG.Repository

---

1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[MongoDB.Bson] : 2.10.4 -> 2.19.0
[MongoDB.Driver] : 2.10.4 -> 2.19.0
[MongoDB.Driver.Core] : 2.10.4 -> 2.19.0
[MongoDB.Libmongocrypt] : 1.0.0 -> 1.9.0
[DnsClient] : 1.3.1 -> 1.6.1
[SharpCompress] : 0.23.0 -> 0.30.1
[System.Buffers] : 4.4.0 -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[ZstdSharp.Port] : Not present -> 0.7.3
[AWSSDK.Core] : Not present -> 3.7.100.27
[AWSSDK.SecurityToken] : Not present -> 3.7.100.27
[Microsoft.Bcl.AsyncInterfaces] : Not present -> 5.0.0
[Microsoft.Win32.Registry] : Not present -> 5.0.0
[Snappier] : Not present -> 1.0.0
```

2. Code Changes:
```
No functional code changes detected. The source code files remain identical between versions.
```

3. Notable Changes:
```
[FXCG.Repository.csproj]-[Framework] - Updated target framework from 4.6.1 to 4.8
[FXCG.Repository.csproj]-[Dependencies] - Added new package references for AWS SDK, MongoDB drivers and supporting libraries
[app.config]-[Assembly Bindings] - Added binding redirects for System.Memory, System.Buffers, MongoDB.Bson, etc.
[app.config]-[Runtime] - Added supportedRuntime element for .NET Framework 4.8
[Project]-[Build] - Added MongoDB.Libmongocrypt.targets import
[Project]-[Content] - Added mongocrypt.dll, libmongocrypt.dylib and libmongocrypt.so as content files
[Project]-[Compiler] - Added Microsoft.Net.Compilers package version 4.1.0
[Project]-[Security] - Added System.Security.* related packages for improved cryptography support
```

The main changes involve:
1. Framework upgrade from 4.6.1 to 4.8
2. Major MongoDB driver and tools version upgrades
3. Addition of AWS SDK packages
4. Addition of improved cryptography support packages
5. Addition of various supporting libraries for improved performance and functionality
6. No changes to the actual business logic code - purely infrastructure/framework updates



#  FXCG.Web

---

1. Library Version Upgrades:
```
[.NET Framework] : 4.6.1 -> 4.8
[MongoDB.Bson] : 2.10.4 -> 2.19.0
[MongoDB.Driver] : 2.10.4 -> 2.19.0
[MongoDB.Driver.Core] : 2.10.4 -> 2.19.0
[MongoDB.Libmongocrypt] : 1.0.0 -> 1.9.0
[DnsClient] : 1.3.1 -> 1.6.1
[SharpCompress] : 0.23.0 -> 0.30.1
[System.Buffers] : 4.4.0 -> 4.5.1
[System.Memory] : Not present -> 4.5.5
[System.Runtime.CompilerServices.Unsafe] : Not present -> 5.0.0
[ZstdSharp.Port] : Not present -> 0.7.3
[AWSSDK.Core] : Not present -> 3.7.100.14
[AWSSDK.SecurityToken] : Not present -> 3.7.100.14
```

2. Code Changes:
```
ApplicationIdentityContext.cs : Updated MongoDB client initialization and database connection code
IdentityConfig.cs : Added new methods for user management and authentication
FilterConfig.cs : Added new exception handling for antiforgery token validation
RouteConfig.cs : Modified default route configuration
```

3. Notable Changes:
```
[Project]-[Framework] - Updated target framework from 4.6.1 to 4.8
[Project]-[Dependencies] - Added AWS SDK packages for cloud integration
[Project]-[Security] - Added improved antiforgery token validation
[Project]-[Authentication] - Enhanced user authentication and management capabilities
[Project]-[Database] - Updated MongoDB driver and related packages
[Project]-[Configuration] - Modified routing and application startup configuration
[Project]-[Performance] - Added memory and runtime optimization packages
```

The main changes involve upgrading the framework version, adding cloud integration capabilities through AWS SDK, improving security features, and updating the MongoDB integration components. The code changes primarily focus on authentication, database connectivity, and request handling improvements.

#  FXCG.Worker.Common

---

1. Library Version Upgrades:
```
Newtonsoft.Json: 12.0.0.0 -> 13.0.3
MongoDB.Bson: Not present -> 2.19.0
MongoDB.Driver: Not present -> 2.19.0
MongoDB.Driver.Core: Not present -> 2.19.0
MongoDB.Driver.GridFS: Not present -> 2.19.0
MongoDB.Libmongocrypt: Not present -> 1.9.0
System.Buffers: Not present -> 4.5.1
System.Memory: Not present -> 4.5.5
System.Runtime.CompilerServices.Unsafe: Not present -> 5.0.0
System.Security.AccessControl: Not present -> 5.0.0
System.Text.Encoding.CodePages: Not present -> 5.0.0
ZstdSharp.Port: Not present -> 0.7.3
AWSSDK.Core: Not present -> 3.7.100.14
AWSSDK.SecurityToken: Not present -> 3.7.100.14
```

2. Code Changes:
```
FXCG.Worker.Common.csproj: Framework version updated from 4.6.1 to 4.8, added new package references and their dependencies

app.config: Added new assembly bindings for:
- System.Memory
- System.Buffers
- System.Runtime.CompilerServices.Unsafe
- MongoDB.Bson
- MongoDB.Driver
- ZstdSharp

WorkerLogger.cs: No functional changes, only framework compatibility updates

ServiceHelper.cs: No changes in code implementation

WorkerProcessTypeEnum.cs: No changes in enumeration values or implementation
```

3. Notable Changes:
```
FXCG.Worker.Common.csproj - Root - Major framework upgrade from .NET 4.6.1 to .NET 4.8
FXCG.Worker.Common.csproj - Dependencies - Added MongoDB related packages and AWS SDK packages
app.config - Assembly Bindings - Added multiple new assembly redirects for MongoDB support
packages.config - Dependencies - Added numerous new packages for MongoDB integration and AWS support
Project Structure - Added new files:
  - libmongocrypt.dylib
  - libmongocrypt.so
  - mongocrypt.dll
```

The main changes appear to be focused on upgrading the framework version and adding MongoDB and AWS integration capabilities while maintaining the core functionality of the worker components.

#  FXCG.Worker.FXDeal

---

1. Library Version Upgrades:
```
Newtonsoft.Json: 12.0.0.0 -> 13.0.3
MongoDB.Bson: Not present -> 2.19.0
MongoDB.Driver: Not present -> 2.19.0
MongoDB.Driver.Core: Not present -> 2.19.0
MongoDB.Driver.GridFS: Not present -> 2.19.0
MongoDB.Libmongocrypt: Not present -> 1.9.0
System.Buffers: Not present -> 4.5.1
System.Memory: Not present -> 4.5.5
System.Runtime.CompilerServices.Unsafe: Not present -> 5.0.0
System.Security.AccessControl: Not present -> 5.0.0
System.Text.Encoding.CodePages: Not present -> 5.0.0
ZstdSharp.Port: Not present -> 0.7.3
AWSSDK.Core: Not present -> 3.7.100.14
AWSSDK.SecurityToken: Not present -> 3.7.100.14
```

2. Code Changes:
```
FXCG.Worker.Common.csproj: Framework version updated from 4.6.1 to 4.8, added new package references and their dependencies

app.config: Added new assembly bindings for:
- System.Memory
- System.Buffers
- System.Runtime.CompilerServices.Unsafe
- MongoDB.Bson
- MongoDB.Driver
- ZstdSharp

WorkerLogger.cs: No functional changes, only framework compatibility updates

ServiceHelper.cs: No changes in code implementation

WorkerProcessTypeEnum.cs: No changes in enumeration values or implementation
```

3. Notable Changes:
```
FXCG.Worker.Common.csproj - Root - Major framework upgrade from .NET 4.6.1 to .NET 4.8
FXCG.Worker.Common.csproj - Dependencies - Added MongoDB related packages and AWS SDK packages
app.config - Assembly Bindings - Added multiple new assembly redirects for MongoDB support
packages.config - Dependencies - Added numerous new packages for MongoDB integration and AWS support
Project Structure - Added new files:
  - libmongocrypt.dylib
  - libmongocrypt.so
  - mongocrypt.dll
```

The main changes appear to be focused on upgrading the framework version and adding MongoDB and AWS integration capabilities while maintaining the core functionality of the worker components.

#  FXCG.Worker.PaymentService

---

1. Library Version Upgrades:
```
Framework: .NET Framework 4.6.1 -> .NET Framework 4.8
Newtonsoft.Json: 12.0.0.0 -> 13.0.3
MongoDB.Bson: Not present -> 2.19.0
MongoDB.Driver: Not present -> 2.19.0
MongoDB.Driver.Core: Not present -> 2.19.0
MongoDB.Driver.GridFS: Not present -> 2.19.0
MongoDB.Libmongocrypt: Not present -> 1.9.0
AWSSDK.Core: Not present -> 3.7.100.14
AWSSDK.SecurityToken: Not present -> 3.7.100.14
System.Memory: Not present -> 4.5.5
System.Buffers: Not present -> 4.5.1
System.Runtime.CompilerServices.Unsafe: Not present -> 5.0.0
Microsoft.Win32.Registry: Not present -> 5.0.0
System.Security.AccessControl: Not present -> 5.0.0
System.Text.Encoding.CodePages: Not present -> 5.0.0
ZstdSharp.Port: Not present -> 0.7.3
```

2. Code Changes:
```
App.config: Updated supportedRuntime version from 4.6.1 to 4.8, added new assembly bindings for MongoDB and AWS SDK dependencies

FXCG.Worker.PaymentService.csproj: 
- Updated TargetFrameworkVersion from v4.6.1 to v4.8
- Added new package references for MongoDB, AWS SDK, and supporting libraries
- Added new build targets for MongoDB.Libmongocrypt

PaymentWorker.cs: No functional changes, only framework compatibility updates

Service.cs: No functional changes, maintained same timer and process management logic

ConfigHelper.cs: No changes in implementation
```

3. Notable Repository Changes:
```
[Project Structure]-[Root]- Added new MongoDB related files:
- libmongocrypt.dylib
- libmongocrypt.so
- mongocrypt.dll

[App.config]-[runtime/assemblyBinding]- Added new binding redirects for:
- System.Memory
- System.Buffers
- System.Runtime.CompilerServices.Unsafe
- MongoDB.Bson
- MongoDB.Driver
- ZstdSharp

[packages.config]-[Dependencies]- Added multiple new packages for MongoDB support and AWS integration

[FXCG.Worker.PaymentService.csproj]-[ItemGroup]- Added new reference assemblies for MongoDB and AWS SDK support
```

The main changes revolve around upgrading the framework version and adding MongoDB and AWS SDK support while maintaining the core functionality of the payment service worker.

#  FXCG.Worker.RatesCalculationService

---


1. Library Version Upgrades:
```
Framework: .NET Framework 4.6.1 -> .NET Framework 4.8
Newtonsoft.Json: 12.0.0.0 -> 13.0.3
MongoDB.Bson: Not present -> 2.19.0
MongoDB.Driver: Not present -> 2.19.0
MongoDB.Driver.Core: Not present -> 2.19.0
MongoDB.Driver.GridFS: Not present -> 2.19.0
MongoDB.Libmongocrypt: Not present -> 1.9.0
AWSSDK.Core: Not present -> 3.7.100.14
AWSSDK.SecurityToken: Not present -> 3.7.100.14
System.Memory: Not present -> 4.5.5
System.Buffers: Not present -> 4.5.1
System.Runtime.CompilerServices.Unsafe: Not present -> 5.0.0
Microsoft.Win32.Registry: Not present -> 5.0.0
System.Security.AccessControl: Not present -> 5.0.0
System.Text.Encoding.CodePages: Not present -> 5.0.0
ZstdSharp.Port: Not present -> 0.7.3
```

2. Code Changes:
```
FXCG.Worker.RatesCalculationService.csproj: 
- Updated TargetFrameworkVersion from v4.6.1 to v4.8
- Added new package references for MongoDB and AWS SDK
- Added MongoDB.Libmongocrypt build targets

App.config:
- Updated supportedRuntime version to 4.8
- Added new assembly bindings for MongoDB and AWS SDK dependencies
- Added System.Memory, System.Buffers binding redirects

Service.cs:
- No functional changes in timer initialization and process management
- Maintained same logging and process control logic

RatesCalculationWorker.cs:
- No changes in core calculation logic
- Maintained same merchant rate calculation workflow

ConfigHelper.cs and EmailHelper.cs:
- No functional changes in configuration or email handling
```

3. Notable Repository Changes:
```
[Project Structure]-[Root]- Added new MongoDB related files:
- libmongocrypt.dylib
- libmongocrypt.so
- mongocrypt.dll

[App.config]-[runtime/assemblyBinding]- Added new binding redirects for:
- System.Memory
- System.Buffers
- System.Runtime.CompilerServices.Unsafe
- MongoDB.Bson
- MongoDB.Driver
- ZstdSharp

[packages.config]-[Dependencies]- Added multiple new packages:
- MongoDB related packages
- AWS SDK packages
- System components for .NET 4.8 compatibility

[FXCG.Worker.RatesCalculationService.csproj]-[ItemGroup]- Added new reference assemblies for MongoDB and AWS SDK support
```

The main changes focus on upgrading the framework version and adding MongoDB and AWS SDK support while maintaining the core functionality of the rates calculation service.

#  FXCG.Worker.RatesFeedService

---

1. Library Version Upgrades:
```
Framework: .NET Framework 4.6.1 -> .NET Framework 4.8
System.Net.Http: 4.3.3 -> 4.3.4
Newtonsoft.Json: 12.0.0.0 -> 13.0.3
MongoDB.Bson: Not present -> 2.19.0
MongoDB.Driver: Not present -> 2.19.0
MongoDB.Driver.Core: Not present -> 2.19.0
MongoDB.Driver.GridFS: Not present -> 2.19.0
MongoDB.Libmongocrypt: Not present -> 1.9.0
AWSSDK.Core: Not present -> 3.7.100.14
AWSSDK.SecurityToken: Not present -> 3.7.100.14
DnsClient: Not present -> 1.6.1
Microsoft.Bcl.AsyncInterfaces: Not present -> 5.0.0
System.Memory: Not present -> 4.5.5
System.Buffers: Not present -> 4.5.1
System.Runtime.CompilerServices.Unsafe: Not present -> 5.0.0
```

2. Code Changes:
```
App.config: 
- Updated framework version from 4.6.1 to 4.8
- Added new assembly bindings for MongoDB and AWS dependencies
- Added System.Memory and System.Buffers binding redirects

FXCG.Worker.RatesFeedService.csproj:
- Updated TargetFrameworkVersion to v4.8
- Added new package references for MongoDB, AWS SDK and supporting libraries
- Added MongoDB.Libmongocrypt build targets

Service.cs:
- No functional changes in timer initialization and worker processes
- Same logging and process control logic maintained

RatesFeedWorker.cs:
- No changes in core rate fetching logic
- Maintained same feed execution workflow

ConfigHelper.cs:
- No changes in configuration property definitions
```

3. Notable Repository Changes:
```
[Project Structure]-[Root]- Added new MongoDB related files:
- libmongocrypt.dylib
- libmongocrypt.so
- mongocrypt.dll

[App.config]-[runtime/assemblyBinding]- Added new binding redirects for:
- System.Memory
- System.Buffers
- System.Runtime.CompilerServices.Unsafe
- MongoDB.Bson
- MongoDB.Driver
- ZstdSharp

[packages.config]-[Dependencies]- Added multiple new packages:
- MongoDB related packages
- AWS SDK packages
- System components for .NET 4.8 compatibility

[FXCG.Worker.RatesFeedService.csproj]-[ItemGroup]- Added new reference assemblies for MongoDB and AWS SDK support
```

The main changes focus on upgrading the framework version and adding MongoDB and AWS SDK support while maintaining the core functionality of the rates feed service.

#  Genesis.NET

---
1. Library Version Upgrades:
```
.NET Framework: 4.6.1 -> 4.8
System.Net.Http: 4.3.3 -> 4.3.4 
Newtonsoft.Json: 12.0.0 -> 13.0.3
MongoDB.Bson: Not present -> 2.19.0
MongoDB.Driver: Not present -> 2.19.0
MongoDB.Driver.Core: Not present -> 2.19.0
MongoDB.Driver.GridFS: Not present -> 2.19.0
MongoDB.Libmongocrypt: Not present -> 1.9.0
AWSSDK.Core: Not present -> 3.7.100.14
AWSSDK.SecurityToken: Not present -> 3.7.100.14
System.Memory: Not present -> 4.5.5
System.Buffers: Not present -> 4.5.1
System.Runtime.CompilerServices.Unsafe: Not present -> 5.0.0
```

2. Code Changes:
```
Common/Constants.cs: No functional changes

Common/Extensions.cs: No functional changes in extension methods

Configuration.cs: Added MongoDB and AWS SDK configuration support

Entities/Entity.cs: No functional changes in base entity class

Entities/Money.cs: No changes in money handling logic

GenesisClient.cs: Added MongoDB client initialization and configuration
```

3. Notable Repository Changes:
```
[Project Structure]-[Root]- Added MongoDB related files:
- libmongocrypt.dylib
- libmongocrypt.so
- mongocrypt.dll

[App.config]-[runtime/assemblyBinding]- Added new binding redirects for:
- MongoDB.Bson
- MongoDB.Driver
- System.Memory
- System.Buffers

[packages.config]-[Dependencies]- Added new package references:
- MongoDB.* packages
- AWSSDK.* packages
- System.Memory
- System.Buffers
```

The main changes focus on upgrading the .NET Framework version and adding MongoDB and AWS SDK support to the project. Most of the core business logic and entity classes remain unchanged, with the updates primarily focused on infrastructure and dependencies.

#  Genesis.NET.Specs

---


1. Library Version Upgrades:
```
.NET Framework: 4.6.1 -> 4.8
System.Runtime.CompilerServices.Unsafe: Not present -> 5.0.0
System.Memory: Not present -> 4.0.1.2 
System.Buffers: Not present -> 4.0.3.0
MongoDB.Bson: Not present -> 3.0.0
MongoDB.Driver: Not present -> 3.0.0
ZstdSharp: Not present -> 0.7.3.0
```

2. Code Changes:
```
app.config: Added new assembly bindings for:
- System.Runtime.CompilerServices.Unsafe
- System.Memory
- System.Buffers
- MongoDB.Bson
- MongoDB.Driver
- ZstdSharp

Genesis.NET.Specs.csproj: 
- Updated target framework from 4.6.1 to 4.8
- Added new project configurations (ACC, PROD, STAGE, HOTFIX)
- Added new package references for MongoDB and support libraries

DebuggerShim.cs: Added new file for NSpec test debugging support
```

3. Notable Repository Changes:
```
[Project Structure]-[Root]- Added new project configurations:
- ACC (Debug)
- PROD (Release)
- STAGE (Release)
- HOTFIX (Release)

[app.config]-[runtime/assemblyBinding]- Added new binding redirects for:
- MongoDB related assemblies
- System.Memory
- System.Buffers
- System.Runtime.CompilerServices.Unsafe

[Genesis.NET.Specs.csproj]-[PropertyGroup]- Added new build configurations and updated framework version

[DebuggerShim.cs]-[Root]- Added new file for test debugging support
```

The main changes focus on upgrading the .NET Framework version and adding MongoDB support with related dependencies. The project structure was also enhanced with new build configurations.

