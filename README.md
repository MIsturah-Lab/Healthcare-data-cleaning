# Healthcare Laboratory Data Cleaning, Preparation & Validation

**Organisation:** Mirabik Medical Diagnostic Centre *(fictional
organisation)*
**Industry:** Healthcare\
**Department:** Laboratory Services\
**Project type:** Data Cleaning & Data Quality Assessment\
**Tools:** Microsoft Excel, Power Query\
**Dataset period:** January--December 2025\
**Prepared by:** Misturah Ikeola

> **Dataset notice:** This project uses a synthetic healthcare
> laboratory operations dataset for learning and portfolio
> demonstration. It contains no real patient records and is not intended
> for clinical decision-making or real-world healthcare benchmarking.

## Project Overview

Reliable data is essential for monitoring laboratory operations and
producing trustworthy reports. Missing values, repeated identifiers,
inconsistent category labels, date-format issues and incorrect data
types can reduce confidence in analysis and affect downstream reporting.

In this project, I assessed, cleaned, prepared and validated a synthetic
laboratory operations dataset for Mirabik Medical Diagnostic Centre. I
used Microsoft Excel and Power Query to investigate data-quality issues,
apply appropriate transformations and review the resulting dataset
before future reporting and analysis.

## Business Context

Medical laboratories generate operational information about patient
samples, laboratory requests, test processing, staff, shifts, equipment
and result management. Before this information can be used reliably, it
needs to be assessed, cleaned and validated.

The project focused on preparing the dataset for future analysis. It did
**not** calculate laboratory turnaround-time KPIs or assess laboratory
performance; those activities belong in a separate Laboratory TAT
Analysis project.

## Dataset Summary

  Measure     Original dataset   Cleaned dataset
  --------- ------------------ -----------------
  Records               10,000             9,969
  Columns                   16                16

The dataset covers January to December 2025 and contains synthetic
laboratory operations data.

The 16 source fields include sample and patient identifiers, requesting
and laboratory departments, test and priority details,
collection/receipt/release timestamps, TAT target, biomedical scientist,
shift, analyser/equipment, exception reason, organisation and region.

## Data Quality Assessment

I used Power Query's data-profiling features, including Column Quality,
Column Distribution and Column Profile, to examine completeness,
consistency, validity, plausibility and uniqueness.

Issues investigated included:

-   Missing values across several fields.
-   Repeated `Sample_ID` values.
-   Inconsistent categorical text and capitalisation.
-   Date-format and data-type issues.
-   Unusual or invalid values requiring individual review.

## Data Cleaning and Preparation

### 1. Data type review

I reviewed data types to ensure identifiers, text fields, numerical
values and timestamp fields were represented appropriately.

### 2. Missing-value handling

The `Exception_Reason` field contained **7,199 blank values** in the
source data. I replaced these blanks with **`Not Recorded`** so the
absence of a supplied reason was explicit. This does not imply that an
exception did or did not occur.

I retained other missing values where reliable replacement information
was unavailable rather than inventing values.

### 3. Repeated Sample_ID investigation

The investigation identified **30 `Sample_ID` values that appeared
twice**. I compared the associated records across other fields,
including `Patient_ID`, `Requesting_Department`, `Laboratory_Department`
and `Test_Name`.

Although the `Sample_ID` values were repeated, the associated records
contained different information. I therefore did not classify them as
confirmed identical duplicate records or automatically remove them. I
retained them and documented the repeated identifiers as a data-quality
issue requiring further investigation.

### 4. Categorical standardisation

I reviewed and standardised inconsistent values across key categorical
fields, including Priority, Laboratory Department, Shift, Organisation,
Region and Exception Reason.

### 5. Date and time validation

I investigated date-format inconsistencies and checked timestamp fields
for appropriate Date/Time interpretation in Power Query. Missing
timestamp values were retained where no reliable replacement information
was available.

### 6. Unusual-value investigation

I reviewed unusual values individually rather than applying blanket
deletion rules, to preserve legitimate operational
information.

## Final Validation and Remaining Missing Values

After preparation, the dataset contained **9,969 records and 16
columns**. The following missing values remained and were retained
because reliable replacement information was unavailable:

  Column                         Remaining missing values
  ---------------------------- --------------------------
  `Patient_ID`                                         69
  `Collection_DateTime`                                 9
  `Received_DateTime`                                  22
  `Result_Released_DateTime`                           17
  `TAT_Target_Minutes`                                 19

I also carried out row-count verification, missing-value review,
repeated-identifier review, data-type checks, timestamp validation,s and
column-consistency checks.

## Project Outcome

The project produced a more consistently prepared dataset for future
reporting and analysis. The `Exception_Reason` blanks were made explicit
as `Not Recorded`; missing values without reliable replacements were
retained; and repeated `Sample_ID` values were investigated rather than
automatically deleted.

The final dataset is a foundation for subsequent healthcare analytics
work. It is not a clinical dataset and must not be used for patient care
or real-world laboratory benchmarking.

## Tools and Skills Demonstrated

**Tools** - Microsoft Excel - Power Query

**Skills** - Data quality assessment and profiling - Data cleaning and
transformation - Missing-value investigation and handling - Duplicate
and identifier investigation - Data-type management - Text and category
standardisation - Date and time validation - Row-count and
data-integrity checks - Documentation and analytical problem-solving

## Repository Structure
``` text
Healthcare-Data-Cleaning/
├── 01_Raw_Dataset/
│ └── Original synthetic dataset
├── 02_Cleaned_Dataset/
│ └── Cleaned laboratory dataset
├── 03_Screenshots/
│ └── Project evidence
├── 04_Quality_Checks/
│ └── Data quality verification
├── README.md
└── Project Documentation.docx

## Limitations and Responsible Use

-   The organisation and dataset are fictional.
-   The dataset is synthetic and contains no real patient records.
-   Repeated `Sample_ID` values were identified, but differing
    information across other fields meant they were not treated as
    confirmed identical duplicate records.
-   Some missing values remain because the source data did not provide
    reliable replacement information.
-   This project covers data cleaning and preparation only; laboratory
    TAT calculations and performance analysis are outside its scope.
-   The dataset is for educational and portfolio demonstration only, not
    clinical decision-making or benchmarking.

## Conclusion

This project demonstrates a structured approach to understanding,
cleaning and validating healthcare operational data. It highlights the
importance of investigating data issues before changing or removing
records and documenting decisions so that the resulting dataset can be
used more confidently in future analysis.
