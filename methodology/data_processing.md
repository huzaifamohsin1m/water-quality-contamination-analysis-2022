\# Data Processing Methodology



\## 📋 Overview



This document outlines the step-by-step methodology used to process, clean, and analyze the water quality dataset.



---



\## 1. Raw Data Structure



\### Original Dataset (`Water\_Quality\_Data\_Raw`)



| Column | Description | Units |

|--------|-------------|-------|

| Sample\_ID | Unique identifier | - |

| Date | Collection date | YYYY-MM-DD |

| Region | Geographic zone | - |

| Source\_Type | Water source | River/Tap Water/Groundwater |

| pH | Acidity/Alkalinity | - |

| EC (µS/cm) | Electrical Conductivity | µS/cm |

| TDS (mg/L) | Total Dissolved Solids | mg/L |

| Hardness (mg/L) | Water hardness | mg/L |

| Nitrate (mg/L) | Nitrate concentration | mg/L |

| Lead (mg/L) | Lead concentration | mg/L |

| Temperature (°C) | Water temperature | °C |



---



\## 2. Status Classification Formulas



\### pH Status Formula

```excel

=IF(OR(pH<6.5, pH>8.5), "Unsafe", "Safe")

WHO Standard: Safe range = 6.5-8.5



Nitrate Status Formula

=IF(Nitrate>50, "Unsafe", "Safe")

WHO Standard: Maximum = 50 mg/L



Lead Status Formula

=IF(Lead>0.01, "Unsafe", "Safe")

WHO Standard: Maximum = 0.01 mg/L



Overall Status Formula

=IF(OR(pH\_Status="Unsafe", Nitrate\_Status="Unsafe", Lead\_Status="Unsafe"), "Contaminated", "Safe")





\## 3.Data Transformation

Month Extraction

=TEXT(Date, "mmm")

Extracts three-letter month abbreviation (Jan, Feb, etc.)



\## 4. Pivot Table Configuration

Overall Contamination

Rows: Overall\_Status



Values: Count of Overall\_Status (as %)



Regional Analysis

Rows: Region



Columns: Overall\_Status



Values: Count of Overall\_Status (as %)



Source Type Analysis

Rows: Source\_Type



Columns: Overall\_Status



Values: Count of Overall\_Status (as %)



Seasonal Trends

Rows: Month



Values: Average of Nitrate



\## 5.Quality Assurance

Validation Checks

|Check Type|Method|Status|
|-|-|-|
|Data completeness|COUNTBLANK|✓ Pass|
|Value ranges|MIN/MAX functions|✓ Pass|
|Formula consistency|Copy/paste check|✓ Pass|
|Pivot table accuracy|Manual cross-check|✓ Pass|





## 6.Excel Functions Used

Core Functions

IF: Conditional logic for status

OR: Multiple condition evaluation

TEXT: Date formatting

COUNTIF: Duplicate detection



Statistical Functions

AVERAGE: Mean calculations

AVERAGEIF: Conditional averages

MIN/MAX: Range determination	

Methodology Version: 1.0

Last Updated: March 2026

			

