---
Title: '.join()'
Description: 'Combines columns of another DataFrame based on index or key.'
Subjects:
  - 'Computer Science'
  - 'Data Science'
Tags:
  - 'Methods'
  - 'Pandas'
CatalogContent:
  - 'learn-pandas'
  - 'paths/data-science'
---

The **`.join()`** method in Pandas is used to combine the columns of another DataFrame with the original DataFrame. It joins based on the **index by default**, and returns a new DataFrame containing data from both. By default, it performs a **left join**, keeping all rows from the left DataFrame and bringing in matching rows from the right.

The original DataFrame remains unchanged unless `inplace=True` is used .

## Syntax

```pseudo
# Join columns from another DataFrame based on index
df = dataframe1.join(dataframe2)

# Custom join options
df = dataframe1.join(
    other,
    on=None,
    how='left',
    lsuffix='',
    rsuffix='',
    sort=False
)
```

## Example
Here is examples for using `.join()` method on Dataframe.

### Example 1: `.join()` on index

```py
import pandas as pd

# Left DataFrame: employee names
employees = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"]
}, index=[1, 2, 3])

# Right DataFrame: departments (matching index)
departments = pd.DataFrame({
    "dept": ["HR", "Engineering", "Marketing"]
}, index=[1, 2, 3])

# Join based on index
result = employees.join(departments)

print(result)
```

```shell
      name         dept
1    Alice            HR
2      Bob   Engineering
3  Charlie     Marketing
```

### Example 2: `.join()` using a column as key

```py
import pandas as pd

# Left DataFrame: employee data with dept_id
employees = pd.DataFrame({
    "emp_id": [101, 102, 103],
    "name": ["Alice", "Bob", "Charlie"],
    "dept_id": [1, 2, 3]
})

# Right DataFrame: department names with matching dept_id
departments = pd.DataFrame({
    "dept_id": [1, 2, 3],
    "department": ["HR", "Engineering", "Marketing"]
})

# Set 'dept_id' as index on right table for join
departments = departments.set_index("dept_id")

# Join using key column
result = employees.join(departments, on="dept_id")

print(result)
```
```shell
   emp_id     name  dept_id   department
0     101    Alice        1           HR
1     102      Bob        2  Engineering
2     103  Charlie        3    Marketing
```
## Codebyte Example (if applicable)

```codebyte/py
import pandas as pd

# Employees DataFrame
employees = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"]
}, index=[101, 102, 103])

# Departments DataFrame
departments = pd.DataFrame({
    "department": ["HR", "Engineering", "Marketing"]
}, index=[101, 102, 103])

# Join on index
combined = employees.join(departments)

print(combined)
```
