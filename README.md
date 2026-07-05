Student Performance Analysis

A Python/pandas exploratory data analysis script that cleans, encodes, and visualizes a dataset of 25,000 student records to surface patterns behind academic performance.

Dataset

Student_Performance.csv — 25,000 rows × 16 columns, including:

CategoryColumnsDemographicsstudent_id, age, genderEnvironmentschool_type, parent_education, internet_access, travel_timeStudy behaviorstudy_hours, attendance_percentage, extra_activities, study_methodOutcomesmath_score, science_score, english_score, overall_score, final_grade

Requirements

bashpip install pandas matplotlib

Python 3.9+ recommended.

Setup


Place Student_Performance.csv in the same directory as the script (or update the file path in the pd.read_csv(...) call).
Run the script top to bottom — either as a .py file or as notebook cells in order:


bashpython analysis.py





What the script does

StepCodePurposeLoadpd.read_csv(...)Read the raw CSV into a DataFrameInspectdf.head(), df.info(), df.columns, df.isnull().sum()Check structure, types, and missing valuesCleandf.duplicated().sum() → df.drop_duplicates()Detect and remove exact duplicate rows (10,000 found in the raw file)Summarizedf.describe(), df.describe(include="O")Numeric and categorical summary statisticsEncode.map({"yes": 1, "no": 0}) on extra_activities, internet_accessConvert binary yes/no columns to 0/1 for numeric analysisGroup & Aggregatedf.groupby("age")[[...]].mean(), df.groupby("parent_education")[...].mean()Compare average outcomes across categoriesVisualizematplotlib bar and pie chartsShow comparisons and proportions

Charts produced


Bar chart — average attendance % and overall score by age
Bar chart — average overall score by parent education level
Pie chart — proportion of average scores by subject (Math/Science/English)
Pie chart — final grade distribution (A–F)


Key findings


The raw file contained 10,000 exact duplicate rows (half the dataset) — always deduplicate before analyzing.
Age has little effect on performance — scores and attendance stay flat across ages 14–19.
Parental education shows only a small (~1.3 point) spread between highest and lowest groups.
Subjects are balanced — Math, Science, and English each contribute roughly equally (~33%) to overall score.
Grades cluster in the middle — D is the most common grade (25%), A the rarest (5%).
