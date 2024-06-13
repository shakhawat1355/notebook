# NopStation Coding Conventions

This document outlines the coding conventions used in NopStation, which are based on the nopCommerce guidelines. Adherence to these guidelines ensures consistent and high-quality source code.

## Code Style Enforcement

The coding guidelines are enforced through the `.editorconfig` file in Visual Studio, which helps maintain the desired code style across different development environments.

## Supported .NET Coding Convention Categories

1. **Language Conventions**
2. **Formatting Conventions**
3. **Naming Conventions**

### 1. Language Conventions

### .NET Code Style Settings

- **"this." Qualifiers**
  - Avoid using `this.` for fields, properties, methods, or events.
    
    ✅ Correct: `capacity = 0;`
    
    ❌ Incorrect: `this.capacity = 0;`

- **Language Keywords Instead of Framework Type Names**
  - Use language keywords for type references when possible.
    
    ✅ Correct: `private int _member;`
    
    ❌ Incorrect: `private Int32 _member;`

- **Modifier Preferences**
  - Always declare accessibility modifiers except for public interface members.
    
    ✅ Correct: `private const string thisFieldIsConst = "constant";`
    
    ❌ Incorrect: `const string thisFieldIsConst = "constant";`
    
  - Follow the specified order for modifiers: `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent`

- **Parentheses Preferences**
  - Use parentheses to clarify operator precedence.
    
    ✅ Correct: `var v = a + (b * c);`
    
    ❌ Incorrect: `var v = a + b * c;`

### Expression-Level Preferences

- **Use object initializers where possible.**

    ✅ Correct: `var c = new Customer() { Age = 21 };`
    
    ❌ Incorrect: `var c = new Customer(); c.Age = 21;`

- **Use collection initializers where possible.**

    ✅ Correct: `var list = new List<int> { 1, 2, 3 };`
    
    ❌ Incorrect: `var list = new List<int>(); list.Add(1); list.Add(2); list.Add(3);`

- **Prefer tuple names over `ItemX` properties.**

    ✅ Correct: `(string name, int age) customer = GetCustomer(); var name = customer.name;`
    
    ❌ Incorrect: `(string name, int age) customer = GetCustomer(); var name = customer.Item1;`

- **Use inferred tuple element names.**

    ✅ Correct: `var tuple = (age, name);`
    
    ❌ Incorrect: `var tuple = (age: age, name: name);`

- **Use explicit anonymous type member names.**

    ✅ Correct: `var anon = new { age = age, name = name };`
    
    ❌ Incorrect: `var anon = new { age, name };`

- **Prefer auto-properties over properties with private backing fields.**

    ✅ Correct: `private int Age { get; }`
    
    ❌ Incorrect: `private int age; public int Age { get { return age; } }`

- **Use null-check with pattern-matching over `object.ReferenceEquals`.**

    ✅ Correct: `if (value is null) return;`
    
    ❌ Incorrect: `if (object.ReferenceEquals(value, null)) return;`

- **Use ternary conditional for assignments and return statements.**

    ✅ Correct: `string s = expr ? "hello" : "world";`
    
    ❌ Incorrect: `string s; if (expr) { s = "hello"; } else { s = "world"; }`

- **Prefer compound assignment expressions.**

    ✅ Correct: `x += 1;`
    
    ❌ Incorrect: `x = x + 1;`



### Null-Checking Preferences

- **Use null-coalescing expressions over ternary operator checking.**

    ✅ Correct: `var v = x ?? y;`
    
    ❌ Incorrect: `var v = x != null ? x : y;`

- **Use null-conditional operator when possible.**

    ✅ Correct: `var v = o?.ToString();`
    
    ❌ Incorrect: `var v = o == null ? null : o.ToString();`

### Formatting Conventions

#### .NET Formatting Settings

- **Organize Using Directives**
  - Sort `System.*` directives alphabetically and place them before other directives.
    
    ✅ Correct: `using System.Collections.Generic; using System.Threading.Tasks; using Octokit;`
    
    ❌ Incorrect: `using System.Collections.Generic; using Octokit; using System.Threading.Tasks;`

### Naming Conventions

#### .NET Naming Conventions

- **Prefix and Suffix**
  - Do not use Hungarian notation for variables or fields.
    
    ✅ Correct: `public DateTime DateTimeProvider { get; }`
    
    ❌ Incorrect: `public DateTime dtProvider { get; }`
  - Do not use `_` or `m_` prefixes for member variables.
    
    ✅ Correct: `private string name;`
    
    ❌ Incorrect: `private string _name;`

- **Capitalization**
  - Use PascalCase for public members, types, and non-private fields.
    
    ✅ Correct: `public DateTime DateTimeProvider { get; }`
    
    ❌ Incorrect: `public DateTime dateTimeProvider { get; }`
  - Use camelCase for private and internal fields.
    
    ✅ Correct: `private DateTime dateTimeProvider;`
    
    ❌ Incorrect: `private DateTime DateTimeProvider;`

### C# Code Style Settings

#### Implicit and Explicit Types

- **Use `var` for built-in system types and when the type is obvious from the right-hand side.**

    ✅ Correct: `var x = 5;`
    
    ❌ Incorrect: `int x = 5;`

- **Use `var` over explicit type unless overridden by another rule.**

    ✅ Correct: `var obj = new Customer();`
    
    ❌ Incorrect: `Customer obj = new Customer();`

#### Expression-Bodied Members

- **Prefer block bodies for methods, constructors, and operators.**

    ✅ Correct: `public int GetAge() { return this.Age; }`
    
    ❌ Incorrect: `public int GetAge() => this.Age;`

- **Prefer expression bodies for properties, indexers, accessors, and lambdas.**

    ✅ Correct: `public int Age => _age;`
    
    ❌ Incorrect: `public int Age { get { return _age; } }`

#### Pattern Matching

- **Use pattern matching instead of `is` expressions with type casts.**

    ✅ Correct: `if (o is int i) {...}`
    
    ❌ Incorrect: `if (o is int) { var i = (int)o; ... }`

- **Use pattern matching instead of `as` expressions with null checks.**

    ✅ Correct: `if (o is string s) {...}`
    
    ❌ Incorrect: `var s = o as string; if (s != null) {...}`

#### Inlined Variable Declarations

- **Declare out variables inline in method calls.**

    ✅ Correct: `if (int.TryParse(value, out int i)) {...}`
    
    ❌ Incorrect: `int i; if (int.TryParse(value, out i)) {...}`

### C# Expression-Level Preferences

- **Use `default` literal for default value expressions when the compiler can infer the type.**

    ✅ Correct: `void DoWork(CancellationToken cancellationToken = default) { ... }`
    
    ❌ Incorrect: `void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }`

### C# Null-Checking Preferences

- **Use throw expressions instead of throw statements.**

    ✅ Correct: `this.s = s ?? throw new ArgumentNullException(nameof(s));`
    
    ❌ Incorrect: `if (s == null) { throw new ArgumentNullException(nameof(s)); } this.s = s;`

- **Use conditional coalescing operator `?.` when invoking a lambda expression.**

    ✅ Correct: `func?.Invoke(args);`
    
    ❌ Incorrect: `if (func != null) { func(args); }`

### Code Block Preferences

- **Avoid curly braces if allowed.**

    ✅ Correct: `if (test) this.Display();`
    
    ❌ Incorrect: `if (test) { this.Display(); }`

### Formatting Conventions

#### .NET Formatting Settings

- **Organize Using Directives**
  - Sort `System.*` directives alphabetically and place them before other directives.
    
    ✅ Correct: `using System.Collections.Generic; using System.Threading.Tasks; using Octokit;`
    
    ❌ Incorrect: `using System.Collections.Generic; using Octokit; using System.Threading.Tasks;`

  - Do not place blank lines between using directive groups.
    
    ✅ Correct: `using System.Collections.Generic; using System.Threading.Tasks; using Octokit;`
    
    ❌ Incorrect: `using System.Collections.Generic; using System.Threading.Tasks; using Octokit;`

#### C# Formatting Settings

- **New-Line Option**
  - Use Allman style for braces.
    
    ✅ Correct: `void MyMethod() { if (...) { ... } }`
    
    ❌ Incorrect: `void MyMethod() { if (...) { ... } }`

  - Place `else`, `catch`, and `finally` statements on a new line.
    
    ✅ Correct: `if (...) { ... } else { ... }`
    
    ❌ Incorrect: `if (...) { ... } else { ... }`

- **Indentation Options**
  - Indent switch case contents and labels.
    
    ✅ Correct: `switch (x) { case 1: action(); break; }`
    
    ❌ Incorrect: `switch (x) {case 1: action(); break;}`
    
  - Place labels at the same indent as the current context.
    
    ✅ Correct: `label: action();`
    
    ❌ Incorrect: `   label: action();`

- **Spacing Options**
  - Remove space between the cast and the value.
    
    ✅ Correct: `int y = (int)x;`
    
    ❌ Incorrect: `int y = (int) x;`

  - Place a space after keywords in control flow statements.
    
    ✅ Correct: `for (int i = 0; i < x; i++) { ... }`
    
    ❌ Incorrect: `for(int i=0;i<x;i++) { ... }`

  - Place a space after the comma in the declaration.
    
    ✅ Correct: `MyMethod(int x, int y, int z)`
    
    ❌ Incorrect: `MyMethod(int x,int y,int z)`

  - Place a space inside the brackets in implicit array creations.
    
    ✅ Correct: `var a = new[] { 1, 10, 100, 1000 };`
    
    ❌ Incorrect: `var a = new[]{1,10,100,1000};`

### Naming Conventions

#### .NET Naming Conventions

- **Prefix and Suffix**
  - Do not use Hungarian notation for variables or fields.
    
    ✅ Correct: `public DateTime DateTimeProvider { get; }`
    
    ❌ Incorrect: `public DateTime dtProvider { get; }`
    
  - Do not use `_` or `m_` prefixes for member variables.
    
    ✅ Correct: `private string name;`
    
    ❌ Incorrect: `private string _name;`

- **Capitalization**
  - Use PascalCase for public members, types, and non-private fields.
    
    ✅ Correct: `public DateTime DateTimeProvider { get; }`
    
    ❌ Incorrect: `public DateTime dateTimeProvider { get; }`
  
  - Use camelCase for private and internal fields.
    
    ✅ Correct: `private DateTime dateTimeProvider;`
    
    ❌ Incorrect: `private DateTime DateTimeProvider;`
  
  - Use PascalCase for method names.
    
    ✅ Correct: `public void PerformAction()`
    
    ❌ Incorrect: `public void performAction()`
  
  - Use camelCase for method parameters.
    
    ✅ Correct: `public void PerformAction(int actionCode)`
    
    ❌ Incorrect: `public void PerformAction(int ActionCode)`
  
  - Use ALL_CAPS for constants.
    
    ✅ Correct: `const int MAX_LIMIT = 100;`
    
    ❌ Incorrect: `const int MaxLimit = 100;`

- **Special Characters**
  - Do not use special characters in identifiers.
    
    ✅ Correct: `public int Price { get; set; }`
    
    ❌ Incorrect: `public int Pr!ce { get; set; }`


### Additional Notes

- **Use Regions Sparingly**: While regions can be helpful in organizing code, overuse can make code more difficult to navigate. Use them judiciously to group related pieces of code, such as fields, properties, and methods.

- **Commenting and Documentation**: Use XML comments (`///`) for public members to facilitate automatic documentation generation. Ensure comments are clear, concise, and provide value beyond what can be inferred from the code itself.

## NopCommerce Source Code Organization

- **Libraries**
  - `Nop.Core`: Contains core classes for nopCommerce like caching, events, helpers, and business objects (e.g., Order and Customer entities).
  - `Nop.Data`: Handles data access using the Linq2DB Code-First approach, separating data-access logic from business objects.
  - `Nop.Services`: Contains business logic, validations, or calculations related to the data.

- **Plugins**
  - Plugins are contained within a Visual Studio solution folder and are physically located at the root of your solution. They are automatically copied to the `\Presentation\Nop.Web\Plugins` directory.

- **Presentation**
  - `Nop.Web`: MVC web application project for the public store, including an administration panel.
  - `Nop.Web.Framework`: Contains common presentation components for the `Nop.Web` project.

- **Tests**
  - Various test projects for different layers of the application, ensuring the reliability and robustness of the code.

### Adherence to Guidelines

Ensuring all team members adhere to these coding standards is essential for maintaining code quality, readability, and consistency. Regular code reviews, automated code analysis tools, and adherence to the `.editorconfig` settings can help enforce these standards effectively.
