# The Code Review Handbook for nopCommerce

This handbook aims to streamline the code review process, ensuring high-quality and maintainable code. It is structured into key sections to provide both authors and reviewers with a systematic approach to enhancing code integrity.

## Key Sections and Highlights

### Code Review Process
A systematic approach is crucial for improving code quality and maintainability. Ensure each review is thorough and focuses on both functionality and readability of the code.

### Tips for Authors

- **No Unused Variables or Methods**: Ensure your codebase is free from unused variables or methods. Tools like `SonarLint` can help identify these redundancies.
  - *Example*:
    ```csharp
    // Before
    int unusedVariable = 5;
    public void UnusedMethod() { }
    public void UsedMethod() {
        Console.WriteLine("Hello, world!");
    }

    // After
    public void UsedMethod() {
        Console.WriteLine("Hello, world!");
    }
    ```
- **No Unnecessary Files**: Utilize `.gitignore` to exclude files that should not be tracked by version control.
  - *Example*:
    ```plaintext
    # .gitignore
    node_modules/
    *.user
    bin/
    obj/
    ```

- **No Unnecessary Comments**: Comments should add value, explaining "why" something is done, not "what" is done. Avoid redundant comments.
  - *Example*:
    ```csharp
    // Bad: Increment counter by 1
    counter += 1;

    // Good: Increment counter to ensure the next cycle processes the updated value
    counter += 1;
    ```

- **Avoid Unnecessary "this" Usage**: Use `this` keyword only when it's necessary to avoid ambiguity.
  - *Example*:
    ```csharp
    // Before
    this.LoadData();
    this.ShowData();

    // After (if contextually clear)
    LoadData();
    ShowData();
    ```

- **Avoid Unnecessary Changes**: Focus your commits on relevant changes. Avoid including changes to whitespace, formatting, or trivial edits that don't affect functionality.
  - *Example*: (Visual example, describe before and after a clean commit that avoids unnecessary whitespace changes.)

- **No Unnecessary Using Directives**: Remove any `using` directives that are not needed to make the code cleaner and more readable.
  - *Example*:
    ```csharp
    // Before
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;

    // After
    using System;
    ```

### How to Conduct PR Reviews

- **Check Use of "var"**: Ensure `var` is used appropriately, adhering to the coding standards which favor explicit typing over inferred typing in complex expressions.
  - *Example*:
    ```csharp
    // Good use of var
    var list = new List<string>();  // Type is obvious

    // Avoid var
    var item = GetItem();  // Type not obvious
    ```

- **Check Use of "readonly"**: Validate the use of `readonly` to ensure immutability in fields intended to not be modified after construction.
  - *Example*:
    ```csharp
    public class SampleClass
    {
        public readonly int Id;

        public SampleClass(int id) {
            Id = id;
        }
    }
    ```

- **Naming Conventions**: Adhere to established naming conventions to ensure code clarity and consistency.
  - *Example*:
    ```csharp
    // Class names and method names
    public class CustomerService
    {
        public void DeleteCustomer(int customerId) { }
    }

    // Variable names
    int itemCount;
    ```

- **Anti-Forgery Token**: Verify correct implementation of anti-forgery tokens in web applications to prevent CSRF attacks.
  - *Example*:
    ```csharp
    [HttpPost]
    [ValidateAntiForgeryToken]
    public ActionResult DeleteCustomer(int id)
    {
        // Deletion logic here
        return RedirectToAction("Index");
    }
    ```

- **Controller Access Rights**: Check that role-based access controls are correctly implemented in controllers.
  - *Example*:
    ```csharp
    [Authorize(Roles = "Admin")]
    public class AdminController : Controller
    {
        public ActionResult Index()
        {
            return View();
        }
    }
    ```

- **Data Annotations**: Check for correct usage of data annotations in data models to enforce validation rules and provide UI hints.
  - *Example*:
    ```csharp
    public class Product
    {
        [Required]
        [StringLength(100, MinimumLength = 3)]
        public string Name { get; set; }

        [Range(1, 1000)]
        public decimal Price { get; set; }
    }
    ```

- **Code Duplications**: Identify and refactor duplicated code segments to enhance maintainability.
  - *Example*:
    ```csharp
    // Before
    public void ProcessOrder()
    {
        // Duplicate logic
        var tax = price * 0.2m;
        var total = price + tax;
    }
    public void ProcessReturn()
    {
        // Duplicate logic
        var tax = price * 0.2m;
        var total = price + tax;
    }

    // After
    public decimal CalculateTotal(decimal price)
    {
        var tax = price * 0.2m;
        return price + tax;
    }
    ```

### Best Practices

- **Systematic Review**: Follow a structured approach to cover all aspects of the code, ensuring no part is overlooked.
- **Tool Integration**: Leverage tools such as linters, IDE shortcuts, and review templates to automate and simplify the review process.
- **Collaborative Reviews**: Engage team members in review discussions to plan and execute code refactoring and improvements effectively.
- **Continuous Monitoring**: Keep the code under regular review to catch issues early and enforce coding standards consistently.
