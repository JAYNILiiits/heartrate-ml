# JAYNILiiits/heartrate-ml: Health Analysis Model

This repository contains a robust Python script designed for advanced heart rate data processing and health analysis, particularly optimized for large datasets and challenging data formats from sources like Google Colab.

## 🚀 Features

*   **Corrected Data Processing:** Handles special characters (e.g., '∶' colon), various date formats (including implicit year inference), and heart rate ranges (e.g., "77-117bpm").
*   **Feature Engineering:** Extracts relevant features like `Is_Exercise`, `Is_High_HR_Event`, `Hour`, and `Day_Name`.
*   **Health Risk Categorization:** Classifies heart rate readings into categories such as 'Bradycardia', 'Tachycardia', 'Normal Resting', 'Exercise', and 'Extreme Exercise Risk'.
*   **Comprehensive Health Report:** Generates key metrics like average resting/exercise HR, lowest/highest recorded HR, and overall variability.
*   **Visualization Dashboard:** Creates informative plots using `matplotlib` and `seaborn` including:
    *   Heart Rate Distribution (Rest vs. Exercise)
    *   Health Risk Category Breakdown
    *   24-Hour Heart Rate Pattern (Circadian Rhythm)
    *   Timeline of All Readings with Extreme Events highlighted.
*   **Colab Integration:** Designed to run seamlessly in Google Colab, including file upload functionality.

## 🏗️ Architecture

The application follows a straightforward data processing and analysis pipeline.

```mermaid
graph TD
    A[Start] --> B(Upload .xlsx File)
    B --> C{heartrate.py::process_large_heart_rate_dataset_corrected}
    C --> D[Load Data from Excel]
    D --> E[Fix Colon Character]
    E --> F[Parse Heart Rate Values]
    F --> G[Robust Date/Time Parsing]
    G --> H[Combine to DateTime]
    H --> I[Clean & Sort Data]
    I --> J[Feature Engineering]
    J --> K[Categorize Health Risk]
    K --> L{heartrate.py::generate_full_analysis}
    L --> M[Generate Key Metrics]
    M --> N[Assess Health Risks]
    N --> O[Generate Visualizations (Matplotlib/Seaborn)]
    O --> P[Display Dashboard]
    P --> Q[End]
```

## 📁 Project Structure

```
.
└── heartrate.py
```

## 🛠️ Tech Stack

*   Python
*   pandas
*   numpy
*   datetime
*   dateutil
*   matplotlib
*   seaborn
*   openpyxl (for Excel file reading)
*   google.colab (for environment-specific utilities)

## 🚦 Getting Started

### Prerequisites

This project is primarily designed for use within a Google Colab environment due to its direct `google.colab.files.upload` dependency.

### Installation

No explicit installation steps are required beyond having the necessary Python packages. You can run this script directly in Google Colab.

```bash
# In a Colab Notebook cell, install required libraries if not already present
!pip install pandas openpyxl matplotlib seaborn
```

### Running the Script

1.  **Open in Google Colab:** Click on "Open in Colab" for `heartrate.py` or create a new notebook and paste the contents of `heartrate.py` into a cell.
2.  **Run the Cell:** Execute the cell containing the `heartrate.py` code.
3.  **Upload File:** When prompted by `files.upload()`, select your `.xlsx` heart rate data file. Ensure your Excel file has a sheet named 'Table 1' and the data begins after header row 3.

The script will then process your data, print health metrics to the console, and display the generated visualization dashboard.

## ⚙️ Configuration / Environment Variables

This script does not rely on external environment variables. All configurable aspects, such as the sheet name (`Table 1`) and header row (`3`), are hardcoded within the `process_large_heart_rate_dataset_corrected` function in `heartrate.py`.

## 👋 Contributing

Contributions are welcome! If you have suggestions for improving the data processing, adding more sophisticated analysis, or enhancing visualizations, please feel free to fork the repository and submit a pull request.