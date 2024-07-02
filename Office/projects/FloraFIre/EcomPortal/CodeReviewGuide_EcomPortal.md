# The Code Review Handbook

"The Code Review Handbook" is a comprehensive guide designed to improve the code review process. It outlines best practices for both authors and reviewers to ensure high-quality and maintainable code. The handbook is organized into sections that cover general guidelines, specific tips, and detailed checklists for various aspects of code reviews.
e
## Key Sections and Highlights

### Code Review Process
Emphasizes a systematic approach to code reviews to enhance code quality and maintainability.

### Tips for Authors

1. **No Unused Variables or Methods**
    - Ensure no redundant code is included.
    - **Example**: Use linter tools like SonarLint to identify and remove unused variables or methods.
    
    ```csharp
    // Before
    int unusedVariable = 0;

    // After
    // Variable removed
    ```

2. **No Unnecessary Files**
    - Utilize `.gitignore` to exclude non-essential files.
    - **Example**: Add build, log, and temporary files to `.gitignore`.
    
    ```
    # .gitignore
    *.log
    /bin/
    /obj/
    ```

3. **No Unnecessary Comments**
    - Keep comments meaningful and relevant.
    - **Example**: Avoid redundant comments that do not add value.
    
    ```csharp
    // Before
    // This increments the counter
    counter++;

    // After
    counter++; // Incrementing counter for tracking
    ```

4. **Avoid Unnecessary `this` Usage**
    - Utilize getters and setters appropriately.
    - **Example**: Remove redundant `this` keyword where not needed.
    
    ```csharp
    // Before
    public class ShoppingCart
    {
        private int counter;

        public void IncrementCounter()
        {
            this.counter++;
        }
    }

    // After
    public class ShoppingCart
    {
        private int counter;

        public void IncrementCounter()
        {
            counter++;
        }
    }
    ```


5. **Avoid Unnecessary Changes**
    - Focus on relevant changes only, avoiding whitespace, formatting, and trivial edits.
    - **Example**: Commit only meaningful changes that impact functionality.
    
    ```diff
    - // Unrelated whitespace change
    + // Meaningful code change
    ```

6. **No Unnecessary Using Directives**
    - Remove unused directives with tools like SonarLint and IDE shortcuts.
    - **Example**: Clean up unused `using` statements.
    
    ```csharp
    // Before
    using System.Text;
    using System.Linq;

    // After
    using System.Linq;
    ```

### How to Conduct PR Reviews

1. **Check Use of `var`**
    - Ensure proper usage as per coding standards.
    - **Example**: Prefer explicit types when clarity is needed.
    
    ```csharp
    // Before
    var customer = GetCustomer();

    // After
    Customer customer = GetCustomer();
    ```

2. **Check Use of `readonly`**
    - Validate the use of `readonly` for constants and immutability.
    - **Example**: Apply `readonly` to immutable fields.
    
    ```csharp
    // Before
    private int maxItems = 10;

    // After
    private readonly int maxItems = 10;
    ```

3. **Naming Conventions**
    - Adhere to established naming guidelines.
    - **Example**: Use PascalCase for public members and camelCase for private members.
    
    ```csharp
    // Before
    private int MaxItems;

    // After
    private int maxItems;
    ```

4. **Anti-Forgery Token**
    - Verify the implementation of anti-forgery tokens in web applications.
    - **Example**: Ensure forms include anti-forgery tokens.
    
    in cshtml page:
    ```html
      <form asp-controller="Authentication" asp-action="" method="post">
           <!-- Added antiforgery token  -->
          <nop-antiforgery-token></nop-antiforgery-token> 
          <div class="inputs">
              <label asp-for="Token" asp-postfix=":"></label>
              <input asp-for="Token" class="username" autofocus="autofocus" />
              <span asp-validation-for="Token"></span>
          </div>
          <div class="form-group row">    
              <div class="buttons">
                  <button  type="submit" name="save-info-button" class="button-1 save-customer-info-button">@T("Plugins.MultiFactorAuth.Customer.SendCode")</button>
              </div>
          </div>
      </form>
    ```
    in Controller:
    ```csharp
    //added antiforgery token
    [AutoValidateAntiforgeryToken]
    public partial class NewsletterController : BasePublicController
    {
        [HttpPost]
        [ValidateCaptcha]
        public virtual async Task<IActionResult> SubscribeNewsletter(string email, bool subscribe, bool captchaValid)
        {
            // Method implementation...
        }
    }

    ```

5. **Controller Access Rights**
    - Ensure correct role-based access controls are implemented.
    - **Example**: Check attribute-based access control.
    
    ```csharp
    [Authorize(Roles = "Admin")]
    public class AdminController : Controller
    {
    }
    ```

6. **Data Annotations**
    - Check for proper use of data annotations for validation and UI hints.
    - **Example**: Use data annotations for model validation.
    
    ```csharp
    public partial record DataConfigModel : BaseNopModel, IConfigModel
    {
        #region Properties

        [NopResourceDisplayName("Admin.Configuration.AppSettings.Data.ConnectionString")]
        public string ConnectionString { get; set; }

        [NopResourceDisplayName("Admin.Configuration.AppSettings.Data.DataProvider")]
        public int DataProvider { get; set; }
        public SelectList DataProviderTypeValues { get; set; }

        [NopResourceDisplayName("Admin.Configuration.AppSettings.Data.SQLCommandTimeout")]
        [UIHint("Int32Nullable")]
        public int? SQLCommandTimeout { get; set; }

        [NopResourceDisplayName("Admin.Configuration.AppSettings.Data.WithNoLock")]
        public bool WithNoLock { get; set; }

        #endregion
    }
    ```

7. **Code Duplications**
    - Identify and refactor duplicated code for better maintainability.
    - **Example**: Refactor repeated product price calculation logic in NopCommerce.
    
    ```csharp
    // Before
    decimal price = GetBasePrice(product) + GetTax(product);
    decimal discountedPrice = price - GetDiscount(product);
    
    decimal specialPrice = GetBasePrice(specialProduct) + GetTax(specialProduct);
    decimal discountedSpecialPrice = specialPrice - GetSpecialDiscount(specialProduct);

    // After
    decimal CalculateFinalPrice(Product product, Func<Product, decimal> getDiscount)
    {
        decimal price = GetBasePrice(product) + GetTax(product);
        return price - getDiscount(product);
    }
    
    decimal finalPrice = CalculateFinalPrice(product, GetDiscount);
    decimal finalSpecialPrice = CalculateFinalPrice(specialProduct, GetSpecialDiscount);

8. **SOLID Principles**
    - Ensure the application of SOLID principles for robust and scalable code design.
    - **Example**: Apply the Single Responsibility Principle (SRP).
    
    ```csharp
    // Before
    public class UserService
    {
        public void RegisterUser(User user) { /*...*/ }
        public void SendEmail(User user) { /*...*/ }
    }

    // After
    public class UserService
    {
        public void RegisterUser(User user) { /*...*/ }
    }

    public class EmailService
    {
        public void SendEmail(User user) { /*...*/ }
    }
    ```

### Additional Tips

1. **Avoid Magic Strings**
    - Use constants or enums instead of hard-coded strings.
    - **Example**: Define constants for repeated string values.
    
    ```csharp
    // Before
    var role = "Admin";

    // After
    const string AdminRole = "Admin";
    var role = AdminRole;
    ```

2. **PR Review Templates**
    - Use templates to standardize and streamline the PR review process.
    - **Example**: Create a PR review checklist.
    
    ```markdown
    # PR Review Checklist
    - [ ] Code compiles without errors
    - [ ] All tests pass
    - [ ] Follows naming conventions
    - [ ] No unused variables or methods
    ```

### Best Practices

1. **Systematic Review**
    - Follow a structured approach to cover all aspects of the code.
    
2. **Tool Integration**
    - Leverage tools like linters, IDE shortcuts, and review templates to automate and simplify the review process.
    
3. **Collaborative Reviews**
    - Engage in discussions with the team to plan and execute refactoring and improvements.
    
4. **Continuous Monitoring**
    - Regularly update and monitor code to catch issues early and maintain high standards.
