# PrepStudentDataForModeling
Efficiently prepares and optimizes a large student dataset for modeling, focusing on memory-saving transformations.

---

![Data Preparation](https://universeit.blog/web/app/uploads/2022/05/Data-Preparation-1024x576.jpg)

## Motivation

A common problem when creating models to generate business value from data is that the datasets can be so large that it can take days for the model to generate predictions. Ensuring that our dataset is stored as efficiently as possible is crucial for allowing these models to run on a more reasonable timescale without reducing the dataset's size.

In this notebook, I will clean up a large customer dataset, `customer_train.csv` (19,158 rows x 14 columns). The dataset contains anonymized student information, and whether they were looking for a new job during training. After preparing it, it will be ready to predict whether students are looking for a new job, resulting in useful information that can be used to direct them to prospective recruiters.

## Dataset

| Column                   | Description                                                                      |
|------------------------- |--------------------------------------------------------------------------------- |
| `student_id`             | A unique ID for each student.                                                    |
| `city`                   | A code for the city the student lives in.                                        |
| `city_development_index` | A scaled development index for the city.                                         |
| `gender`                 | The student's gender.                                                            |
| `relevant_experience`    | An indicator of the student's work relevant experience.                          |
| `enrolled_university`    | The type of university course enrolled in (if any).                              |
| `education_level`        | The student's education level.                                                   |
| `major_discipline`       | The educational discipline of the student.                                       |
| `experience`             | The student's total work experience (in years).                                  |
| `company_size`           | The number of employees at the student's current employer.                       |
| `company_type`           | The type of company employing the student.                                       |
| `last_new_job`           | The number of years between the student's current and previous jobs.             |
| `training_hours`         | The number of hours of training completed.                                       |
| `job_change`             | An indicator of whether the student is looking for a new job (`1`) or not (`0`). |

## Task

I will create a DataFrame called `ds_jobs_transformed` that stores the data in `customer_train.csv` much more efficiently.

### Preparation Plan

- Columns containing categories with only two factors must be stored as Booleans (`bool`).
- Columns containing integers only must be stored as 32-bit integers (`int32`).
- Columns containing floats must be stored as 16-bit floats (`float16`).
- Columns containing nominal categorical data must be stored as the category data type.
- Columns containing ordinal categorical data must be stored as ordered categories, and not mapped to numerical values, with an order that reflects the natural order of the column.
- The DataFrame should be filtered to only contain students with 10 or more years of experience at companies with at least 1000 employees, as their recruiter base is suited to more experienced professionals at enterprise companies.

## Results

If we call `.info()` or `.memory_usage()` methods on `ds_jobs` and `ds_jobs_transformed` after doing our data preparation plan, we should notice a substantial decrease in memory usage.

## Conclusion

This project demonstrates how to efficiently prepare a large dataset for modeling by reducing its memory footprint. This is crucial for handling large datasets and ensuring that machine learning models can be trained and run efficiently.

## Acknowledgments

DataCamp for providing the dataset.
