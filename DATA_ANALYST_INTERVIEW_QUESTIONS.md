# Data Analyst Interview Questions

## SQL and Database Knowledge

### 1. What is the difference between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN?
**Answer:**
- **INNER JOIN:** Returns only the matching rows from both tables where the join condition is met.
  ```sql
  SELECT employees.name, departments.dept_name
  FROM employees
  INNER JOIN departments ON employees.dept_id = departments.id;
  ```

- **LEFT JOIN (or LEFT OUTER JOIN):** Returns all rows from the left table and matching rows from the right table. If no match is found, NULL values are returned for right table columns.
  ```sql
  SELECT employees.name, departments.dept_name
  FROM employees
  LEFT JOIN departments ON employees.dept_id = departments.id;
  ```

- **RIGHT JOIN (or RIGHT OUTER JOIN):** Returns all rows from the right table and matching rows from the left table. If no match is found, NULL values are returned for left table columns.
  ```sql
  SELECT employees.name, departments.dept_name
  FROM employees
  RIGHT JOIN departments ON employees.dept_id = departments.id;
  ```

- **FULL OUTER JOIN:** Returns all rows from both tables, with NULL values for non-matching rows.
  ```sql
  SELECT employees.name, departments.dept_name
  FROM employees
  FULL OUTER JOIN departments ON employees.dept_id = departments.id;
  ```

### 2. How would you optimize a slow-running SQL query?
**Answer:** To optimize a slow-running SQL query, I would:

1. **Analyze the execution plan** using EXPLAIN or similar tools to identify bottlenecks
2. **Add appropriate indexes** on columns used in WHERE, JOIN, and ORDER BY clauses
3. **Rewrite the query** to:
   - Avoid SELECT * and only select needed columns
   - Use JOINs instead of subqueries where possible
   - Limit the result set size with WHERE clauses early in the query
   - Use EXISTS instead of IN for better performance with large datasets
4. **Optimize table structure**:
   - Normalize/denormalize as appropriate
   - Use appropriate data types
   - Consider partitioning large tables
5. **Use query hints** when the optimizer makes poor choices
6. **Consider materialized views** for frequently run complex queries
7. **Batch operations** for large data modifications
8. **Review database configuration** for memory allocation, cache sizes, etc.

### 3. Write a SQL query to find the second highest salary in an employees table.
**Answer:** There are several ways to find the second highest salary:

**Method 1: Using LIMIT and OFFSET**
```sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

**Method 2: Using subquery with MAX**
```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**Method 3: Using dense_rank() window function**
```sql
SELECT salary
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) as rank
    FROM employees
) ranked
WHERE rank = 2;
```

## Data Analysis and Statistics

### 4. What is the difference between correlation and causation?
**Answer:**
- **Correlation** is a statistical measure that describes the size and direction of a relationship between two or more variables. A correlation indicates that when one variable changes, the other variable also changes, but it doesn't imply that one causes the other.

- **Causation** means that changes in one variable directly cause changes in another variable. It implies a cause-and-effect relationship.

Key differences:
1. Correlation shows association; causation shows direct influence
2. Correlation can be bidirectional; causation is unidirectional
3. Correlation can be coincidental; causation requires a logical mechanism

Example:
There's a strong correlation between ice cream sales and drowning deaths (both increase in summer), but ice cream sales don't cause drownings. The common cause is warmer weather (confounding variable).

To establish causation, you typically need:
- Temporal precedence (cause happens before effect)
- Covariation (variables change together)
- No alternative explanations (controlled experiments)
- A plausible mechanism

### 5. Explain the difference between mean, median, and mode.
**Answer:**
- **Mean:** The average value, calculated by summing all values and dividing by the number of values.
  ```
  Mean = (x₁ + x₂ + ... + xₙ)/n
  ```
  - Pros: Uses all data points, good for normally distributed data
  - Cons: Sensitive to outliers

- **Median:** The middle value when data is arranged in order.
  - For odd number of values: middle value
  - For even number of values: average of two middle values
  - Pros: Not affected by outliers, good for skewed distributions
  - Cons: Ignores the actual values of most data points

- **Mode:** The most frequently occurring value.
  - Pros: Works for categorical data, shows the most common value
  - Cons: May not exist or may not be unique

When to use each:
- Use mean for normally distributed data without significant outliers
- Use median for skewed distributions or when outliers are present
- Use mode for categorical data or to find the most common value

### 6. What is statistical significance and how is it determined?
**Answer:** Statistical significance is a determination that an observed effect or relationship in a sample is unlikely to have occurred by chance alone.

Key components:
1. **Null hypothesis (H₀):** Assumes no effect or relationship exists
2. **Alternative hypothesis (H₁):** Proposes that an effect or relationship exists
3. **p-value:** Probability of observing results at least as extreme as the current results, assuming the null hypothesis is true
4. **Significance level (α):** Threshold for rejecting the null hypothesis, commonly 0.05 (5%)

A result is statistically significant when:
- p-value < significance level (α)
- This means we reject the null hypothesis

Determining statistical significance:
1. Formulate hypotheses
2. Choose a statistical test based on data type and question
3. Set significance level (typically α = 0.05)
4. Calculate test statistic and p-value
5. Compare p-value to significance level
6. Make a conclusion

Common statistical tests:
- t-test: Compare means between groups
- Chi-square test: Analyze categorical data
- ANOVA: Compare means across multiple groups
- Regression analysis: Examine relationships between variables

## Data Visualization and Tools

### 7. What factors make a data visualization effective?
**Answer:** Effective data visualizations combine several key factors:

**1. Clarity and Simplicity:**
- Clear purpose and message
- Minimal chart junk (unnecessary elements)
- Appropriate level of detail
- Focused on key insights

**2. Appropriate Visualization Type:**
- Bar charts for comparing categories
- Line charts for trends over time
- Scatter plots for relationships between variables
- Pie charts for parts of a whole (used sparingly)
- Heat maps for showing patterns across multiple variables
- Maps for geographical data

**3. Accurate Data Representation:**
- Proper scales and axes
- No misleading visuals (e.g., truncated axes)
- Proportional visual elements
- Appropriate use of color

**4. Accessibility and Usability:**
- Color-blind friendly palettes
- Clear labels and legends
- Sufficient contrast
- Interactive elements when appropriate

**5. Context and Narrative:**
- Meaningful titles and subtitles
- Annotations for important points
- Comparisons where relevant
- Clear methodology notes

**6. Design Principles:**
- Visual hierarchy to guide attention
- Consistent styling
- Appropriate use of white space
- Thoughtful color choices

### 8. Compare and contrast different data visualization tools (Tableau, Power BI, Python libraries).
**Answer:**

**Tableau:**
- **Strengths:**
  - Highly intuitive drag-and-drop interface
  - Excellent interactive visualizations
  - Strong geospatial capabilities
  - Robust data connection options
  - Powerful dashboard creation
  - Good for business users with limited technical background
- **Limitations:**
  - Expensive licensing
  - Limited statistical analysis capabilities
  - Less flexibility for custom visualizations
  - Not ideal for automated reporting pipelines
- **Best for:** Business analysts, data visualization specialists, organizations needing interactive dashboards

**Power BI:**
- **Strengths:**
  - Deep integration with Microsoft ecosystem
  - Cost-effective (included with Office 365)
  - DAX and M languages for data manipulation
  - Regular feature updates
  - Strong data modeling capabilities
  - Good balance of ease-of-use and functionality
- **Limitations:**
  - Less intuitive than Tableau for beginners
  - Some advanced features only in Premium version
  - Can be resource-intensive for large datasets
  - Less flexible than programming-based solutions
- **Best for:** Microsoft-centric organizations, business analysts needing both visualization and data modeling

**Python Libraries (Matplotlib, Seaborn, Plotly):**
- **Strengths:**
  - Free and open-source
  - Highly customizable
  - Seamless integration with data analysis workflows
  - Reproducible visualizations via code
  - Can be integrated into automated pipelines
  - Strong statistical visualization capabilities
- **Limitations:**
  - Steeper learning curve
  - Requires programming knowledge
  - More time-consuming for basic visualizations
  - Interactive features require additional work
- **Best for:** Data scientists, researchers, developers, organizations with technical teams

## Data Cleaning and Preparation

### 9. What steps do you take to clean a dataset before analysis?
**Answer:** Data cleaning is a critical step in the data analysis process. Here's a comprehensive approach:

**1. Initial Exploration:**
- Get basic statistics (count, mean, min, max, etc.)
- Check data types of each column
- Identify the shape of the dataset (rows, columns)
- Review sample records to understand the data

**2. Handle Missing Values:**
- Identify missing values and their patterns
- Determine if values are missing completely at random (MCAR), missing at random (MAR), or missing not at random (MNAR)
- Apply appropriate techniques:
  - Remove rows/columns with excessive missing values
  - Impute values (mean, median, mode, KNN, regression, etc.)
  - Use domain-specific rules for imputation
  - Create missing value indicators if needed

**3. Fix Structural Errors:**
- Standardize capitalization and formatting
- Correct misspellings and typos
- Standardize units of measurement
- Fix inconsistent naming conventions
- Handle inconsistent date formats

**4. Handle Duplicates:**
- Identify and remove exact duplicates
- Address partial duplicates based on business rules
- Check for duplicates created by data entry errors

**5. Address Outliers:**
- Identify outliers using statistical methods (z-score, IQR)
- Determine if outliers are errors or valid extreme values
- Handle appropriately:
  - Remove if they're errors
  - Keep if they're valid but flag for special analysis
  - Transform or cap if needed

**6. Standardize and Normalize:**
- Standardize text fields (lowercase, remove special characters)
- Normalize numeric fields if needed (min-max scaling, z-score)
- Encode categorical variables appropriately

**7. Fix Invalid Values:**
- Check for values outside valid ranges
- Address impossible combinations
- Correct logically inconsistent values
- Handle constraint violations

**8. Create Derived Features:**
- Calculate relevant ratios or differences
- Extract components from dates or text
- Aggregate data where appropriate
- Create domain-specific features

### 10. Explain the concept of feature engineering and provide examples.
**Answer:** Feature engineering is the process of creating new features or transforming existing ones to improve model performance, extract more information from the data, or better represent the underlying patterns.

**Types of Feature Engineering:**

**1. Feature Creation:**
- **Interaction Terms:** Multiply features to capture relationships
  - Example: Creating `price_per_sqft` from `price` and `square_footage`
- **Aggregations:** Summarize information across groups
  - Example: Average purchase amount per customer
- **Domain-Specific Features:** Use industry knowledge
  - Example: Creating a debt-to-income ratio for loan applications

**2. Feature Transformation:**
- **Scaling:** Normalize or standardize features
  - Example: Converting heights from inches to z-scores
- **Mathematical Transformations:** Apply functions to change distribution
  - Example: Log transformation for right-skewed data
- **Encoding:** Convert categorical variables to numeric
  - Example: One-hot encoding for product categories

**3. Feature Extraction:**
- **Text Data:** Extract information from text
  - Example: TF-IDF scores from product descriptions
- **Date/Time:** Extract components from timestamps
  - Example: Creating day_of_week, month, is_weekend from dates
- **Images:** Extract features from visual data
  - Example: Edge detection, color histograms

**4. Dimensionality Reduction:**
- **PCA (Principal Component Analysis):** Create new features that capture variance
- **t-SNE:** Create features that preserve local relationships
- **Autoencoders:** Use neural networks to create compressed representations

**Practical Examples:**

**E-commerce:**
- Recency: Days since last purchase
- Frequency: Number of purchases in last 90 days
- Monetary: Average order value
- RFM score: Combined metric of the above

**Financial:**
- Debt-to-income ratio
- Credit utilization percentage
- Payment-to-income ratio
- Days since last late payment

**Benefits of Feature Engineering:**
- Improves model performance
- Captures domain knowledge
- Handles non-linear relationships
- Makes patterns more explicit
- Can reduce dimensionality
- Helps with interpretability