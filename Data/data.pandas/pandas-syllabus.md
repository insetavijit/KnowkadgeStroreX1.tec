### **[[01 Pandas Fundamentals & Setup]]**

Master Pandas as the essential Python library for data manipulation and analysis. Learn why Pandas is the backbone of data science at Google, JPMorgan, and every data-driven company. Understand DataFrames, Series, and the powerful operations that make Pandas indispensable for data professionals. Data analysts with Pandas skills earn $70k-$120k, while data engineers and scientists earn $100k-$160k. Essential for data analysis, data engineering, and machine learning careers.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 Pandas Introduction]]**|What is Pandas; data manipulation library; use cases; Pandas vs Excel; ecosystem overview; market demand. Industry context.|
|**[[1.2 Environment Setup]]**|Python setup; pip/conda installation; Jupyter notebooks; VS Code; pandas version; numpy dependency. Professional setup.|
|**[[1.3 Series]]**|Series object; creating Series; indexing; operations; methods; Series attributes. 1D data structure.|
|**[[1.4 DataFrame Basics]]**|DataFrame concept; creating DataFrames; from dict; from list; columns; index. 2D data structure.|
|**[[1.5 Data Types]]**|dtypes; int64; float64; object; datetime; category; type inspection; type conversion. Data types.|
|**[[1.6 Basic Operations]]**|Head/tail; shape; info(); describe(); columns; index; basic exploration. Data exploration.|
|**[[1.7 Project: First Dataset]]**|Loading data; exploration; basic operations; understanding structure. First project.|

### **[[02 Data Loading & Export]]**

Master data I/O with Pandas for various file formats. Learn reading and writing CSV, Excel, JSON, and databases. Data loading is the first step in any data analysis workflow.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 CSV Files]]**|read_csv(); to_csv(); parameters; delimiter; header; encoding; compression. CSV handling.|
|**[[2.2 Excel Files]]**|read_excel(); to_excel(); sheets; ExcelWriter; multiple sheets; formatting. Excel handling.|
|**[[2.3 JSON Files]]**|read_json(); to_json(); orient parameter; nested JSON; JSON normalization. JSON handling.|
|**[[2.4 SQL Databases]]**|read_sql(); to_sql(); SQLAlchemy; connection strings; query execution. Database I/O.|
|**[[2.5 Other Formats]]**|Parquet; Feather; HDF5; pickle; performance comparison; big data formats. Alternative formats.|
|**[[2.6 Web Data]]**|read_html(); reading tables; API responses; web scraping integration. Web data.|
|**[[2.7 Chunking Large Files]]**|chunksize; iterating chunks; memory management; large file handling. Big file handling.|
|**[[2.8 Project: Data Pipeline]]**|Loading multiple sources; transforming; exporting; automated pipeline. I/O project.|

### **[[03 Indexing & Selection]]**

Master data selection techniques in Pandas. Learn loc, iloc, Boolean indexing, and query methods. Selection skills are fundamental for data manipulation and analysis.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Column Selection]]**|Single column; multiple columns; bracket notation; dot notation; column lists. Selecting columns.|
|**[[3.2 Row Selection with loc]]**|Label-based selection; loc[]; slicing; single row; multiple rows; ranges. Label indexing.|
|**[[3.3 Row Selection with iloc]]**|Position-based selection; iloc[]; integer indexing; slicing; position ranges. Position indexing.|
|**[[3.4 Boolean Indexing]]**|Conditional selection; boolean masks; compound conditions; & | operators. Filtering rows.|
|**[[3.5 Query Method]]**|query() method; string expressions; variable references; @ syntax; readable filters. Query filtering.|
|**[[3.6 Setting Values]]**|Assignment with loc/iloc; conditional assignment; where(); mask(); updates. Modifying data.|
|**[[3.7 MultiIndex]]**|Hierarchical indexing; creating MultiIndex; xs(); indexing levels; unstacking. Multi-level index.|
|**[[3.8 Project: Data Filtering]]**|Complex filtering; multiple conditions; extracting subsets; analysis. Selection project.|

### **[[04 Data Cleaning]]**

Master data cleaning for real-world datasets. Learn handling missing data, duplicates, and data quality issues. Data cleaning typically takes 60-80% of data analysis time.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Missing Data Detection]]**|isna(); isnull(); notna(); counting missing; visualizing missing; missing patterns. Finding nulls.|
|**[[4.2 Handling Missing Data]]**|dropna(); fillna(); forward/backward fill; interpolation; imputation strategies. Handling nulls.|
|**[[4.3 Duplicates]]**|duplicated(); drop_duplicates(); subset; keep parameter; duplicate analysis. Duplicate handling.|
|**[[4.4 Data Type Conversion]]**|astype(); to_numeric(); to_datetime(); errors parameter; type coercion. Type conversion.|
|**[[4.5 String Cleaning]]**|str accessor; strip(); lower/upper(); replace(); regex; string operations. Text cleaning.|
|**[[4.6 Outliers]]**|Outlier detection; IQR method; z-score; handling outliers; clipping. Outlier handling.|
|**[[4.7 Data Validation]]**|Assertions; value ranges; data quality checks; validation rules. Data quality.|
|**[[4.8 Project: Dirty Dataset]]**|Cleaning real dataset; missing values; duplicates; types; validation. Cleaning project.|

### **[[05 Data Transformation]]**

Master data transformation techniques for analysis. Learn applying functions, mapping values, and reshaping data. Transformation skills enable complex data manipulation.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Apply Functions]]**|apply(); lambda functions; axis parameter; custom functions; element-wise. Applying functions.|
|**[[5.2 Map & Replace]]**|map(); replace(); value mapping; dictionary mapping; series transformation. Value mapping.|
|**[[5.3 Binning & Discretization]]**|cut(); qcut(); binning continuous data; custom bins; labels. Data binning.|
|**[[5.4 String Operations]]**|str methods; split(); contains(); extract(); regex; string manipulation. String processing.|
|**[[5.5 DateTime Operations]]**|to_datetime(); dt accessor; extracting components; date arithmetic; timezones. DateTime handling.|
|**[[5.6 Categorical Data]]**|Categorical dtype; ordered categories; category operations; memory savings. Categorical type.|
|**[[5.7 Vectorized Operations]]**|NumPy integration; vectorized functions; np.where(); np.select(); performance. Vectorization.|
|**[[5.8 Project: Feature Engineering]]**|Creating features; transformations; binning; datetime features; encoding. Transformation project.|

### **[[06 Aggregation & Grouping]]**

Master groupby operations for data aggregation. Learn split-apply-combine pattern, aggregation functions, and pivot tables. Grouping is essential for data analysis and reporting.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 GroupBy Basics]]**|groupby(); groupby object; group keys; iteration; group inspection. Grouping fundamentals.|
|**[[6.2 Aggregation Functions]]**|sum(); mean(); count(); min(); max(); std(); multiple aggregations. Aggregate functions.|
|**[[6.3 Custom Aggregations]]**|agg(); named aggregations; custom functions; multiple functions per column. Custom aggregates.|
|**[[6.4 Transform]]**|transform(); group-wise transformation; broadcasting; standardization per group. Group transformation.|
|**[[6.5 Filter Groups]]**|filter(); group filtering; conditional group selection; group-based filtering. Group filtering.|
|**[[6.6 Pivot Tables]]**|pivot_table(); values; index; columns; aggfunc; margins; Excel-style pivots. Pivot tables.|
|**[[6.7 Crosstab]]**|pd.crosstab(); frequency tables; contingency tables; normalize; margins. Cross tabulation.|
|**[[6.8 Project: Sales Analysis]]**|Grouping sales data; aggregations; pivots; reporting; insights. Aggregation project.|

### **[[07 Merging & Joining]]**

Master combining datasets in Pandas. Learn merge, join, concat, and data combination patterns. Merging skills are essential for working with relational data.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Concat]]**|pd.concat(); vertical stacking; horizontal stacking; axis; ignore_index; keys. Concatenation.|
|**[[7.2 Merge Basics]]**|merge(); on parameter; left/right; how parameter; merge types. Basic merging.|
|**[[7.3 Join Types]]**|Inner join; left join; right join; outer join; join behavior; missing values. Join types.|
|**[[7.4 Merge on Index]]**|left_index; right_index; join(); index-based merging. Index merging.|
|**[[7.5 Multiple Keys]]**|Merging on multiple columns; compound keys; suffix handling. Multi-key merge.|
|**[[7.6 Validate & Indicator]]**|validate parameter; indicator; merge diagnostics; relationship checking. Merge validation.|
|**[[7.7 Append & Combine]]**|append (deprecated); combine_first(); update(); data combination. Data combination.|
|**[[7.8 Project: Data Integration]]**|Merging multiple datasets; joins; integration; analysis. Merging project.|

### **[[08 Reshaping Data]]**

Master data reshaping for different analytical needs. Learn melt, pivot, stack, and unstack operations. Reshaping transforms data between wide and long formats.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Melt (Unpivot)]]**|melt(); id_vars; value_vars; wide to long; unpivoting data. Wide to long.|
|**[[8.2 Pivot]]**|pivot(); index; columns; values; long to wide; reshaping. Long to wide.|
|**[[8.3 Stack & Unstack]]**|stack(); unstack(); MultiIndex; level parameter; reshaping hierarchical. Stack operations.|
|**[[8.4 Wide vs Long Format]]**|Format comparison; tidy data; when to use each; conversion patterns. Data formats.|
|**[[8.5 Explode]]**|explode(); list columns; expanding rows; nested data handling. List expansion.|
|**[[8.6 Transpose]]**|T property; transpose(); swapping rows and columns. Data transpose.|
|**[[8.7 Project: Report Preparation]]**|Reshaping for reports; pivoting; formatting; export. Reshaping project.|

### **[[09 Time Series]]**

Master time series data handling in Pandas. Learn datetime indexing, resampling, and time-based operations. Time series skills are essential for financial and temporal data analysis.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 DateTime Index]]**|DatetimeIndex; to_datetime(); set_index(); datetime as index. Time indexing.|
|**[[9.2 Date Range Generation]]**|date_range(); period_range(); frequency strings; custom ranges. Creating ranges.|
|**[[9.3 Time-Based Indexing]]**|Slicing by date; partial string indexing; between_time(); at_time(). Time selection.|
|**[[9.4 Resampling]]**|resample(); downsampling; upsampling; aggregation; fill methods. Time aggregation.|
|**[[9.5 Rolling Windows]]**|rolling(); window operations; moving average; rolling statistics. Rolling calculations.|
|**[[9.6 Shifting & Lagging]]**|shift(); lag; lead; pct_change(); diff(); time-based shifts. Time shifting.|
|**[[9.7 Time Zones]]**|tz_localize(); tz_convert(); timezone handling; UTC; local time. Timezone handling.|
|**[[9.8 Project: Stock Analysis]]**|Time series analysis; resampling; rolling averages; returns. Time series project.|

### **[[10 Visualization]]**

Master data visualization with Pandas. Learn built-in plotting, matplotlib integration, and visualization best practices. Visualization communicates insights effectively.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Basic Plotting]]**|plot(); line plots; kind parameter; plot types; quick visualization. Basic plots.|
|**[[10.2 Plot Types]]**|Bar; histogram; scatter; box; area; pie; plot customization. Chart types.|
|**[[10.3 Customization]]**|Titles; labels; colors; figsize; legend; styling plots. Plot styling.|
|**[[10.4 Subplots]]**|Multiple plots; subplot layout; shared axes; figure management. Multiple charts.|
|**[[10.5 Matplotlib Integration]]**|plt customization; axes; figures; combining with matplotlib. Advanced plotting.|
|**[[10.6 Seaborn Integration]]**|Seaborn with Pandas; statistical plots; enhanced visualization. Seaborn plots.|
|**[[10.7 Project: Dashboard Data]]**|Creating visualizations; multiple charts; insights; presentation. Visualization project.|

### **[[11 Performance Optimization]]**

Master Pandas performance for large datasets. Learn memory optimization, vectorization, and efficient operations. Performance skills are critical for data engineering.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Memory Usage]]**|memory_usage(); dtypes optimization; category type; memory reduction. Memory management.|
|**[[11.2 Efficient Data Types]]**|Downcasting; int8/16/32; float32; category; sparse; type selection. Type optimization.|
|**[[11.3 Vectorization]]**|Avoiding loops; vectorized operations; NumPy integration; apply vs vectorize. Vectorized code.|
|**[[11.4 Chunked Processing]]**|chunksize; iterating large files; chunk aggregation; out-of-memory. Large data handling.|
|**[[11.5 eval & query]]**|eval(); query(); expression evaluation; memory efficiency. Expression optimization.|
|**[[11.6 Parallel Processing]]**|swifter; pandarallel; dask; modin; parallel pandas operations. Parallelization.|
|**[[11.7 Profiling]]**|%timeit; memory profiling; bottleneck identification; optimization workflow. Performance analysis.|
|**[[11.8 Project: Big Data Processing]]**|Processing large dataset; optimization; chunking; performance. Optimization project.|

### **[[12 Advanced Pandas]]**

Master advanced Pandas features for complex analysis. Learn method chaining, custom extensions, and advanced patterns. Advanced skills separate senior data professionals.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Method Chaining]]**|Fluent interface; pipe(); chaining operations; readable code. Chaining pattern.|
|**[[12.2 Window Functions]]**|rolling(); expanding(); ewm(); window calculations; financial functions. Window operations.|
|**[[12.3 Sparse Data]]**|SparseArray; sparse DataFrames; memory efficiency; sparse operations. Sparse structures.|
|**[[12.4 Custom Accessors]]**|register_dataframe_accessor(); custom methods; extending pandas. Pandas extensions.|
|**[[12.5 Styler]]**|DataFrame.style; conditional formatting; HTML export; styled tables. Styled output.|
|**[[12.6 Options & Settings]]**|pd.options; display settings; compute settings; global configuration. Configuration.|
|**[[12.7 Project: Analysis Pipeline]]**|Building pipeline; chaining; custom functions; complete workflow. Advanced project.|

### **[[13 Pandas with Other Libraries]]**

Master Pandas integration with the Python data ecosystem. Learn NumPy, Scikit-learn, and visualization library integration. Ecosystem knowledge enables complete data workflows.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 NumPy Integration]]**|values; to_numpy(); NumPy functions; array operations; conversion. NumPy integration.|
|**[[13.2 Scikit-learn]]**|Preparing data for ML; feature matrices; train/test split; preprocessing. ML integration.|
|**[[13.3 Matplotlib/Seaborn]]**|Advanced visualization; statistical plots; publication-quality figures. Visualization.|
|**[[13.4 SQLAlchemy]]**|Database connections; read_sql; to_sql; query execution; ORM. Database integration.|
|**[[13.5 Apache Arrow]]**|PyArrow; Arrow tables; efficient interchange; Parquet. Arrow integration.|
|**[[13.6 Polars Comparison]]**|Polars library; performance comparison; when to use Polars. Alternative library.|
|**[[13.7 Project: ML Pipeline]]**|End-to-end pipeline; data prep; feature engineering; model ready. Integration project.|

### **[[14 Real-World Projects]]**

Master building production data analysis solutions. Build impressive portfolio pieces that demonstrate Pandas expertise. Real projects are essential for landing data positions.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Exploratory Data Analysis]]**|Complete EDA; statistics; visualization; insights; reporting. EDA project.|
|**[[14.2 Customer Analytics]]**|Customer data; segmentation; cohort analysis; churn; RFM analysis. Customer analysis.|
|**[[14.3 Financial Analysis]]**|Stock data; returns; risk metrics; portfolio analysis; time series. Finance project.|
|**[[14.4 Sales Reporting]]**|Sales data; aggregation; trends; dashboards; automated reports. Sales analysis.|
|**[[14.5 Data Quality Pipeline]]**|Validation; cleaning; quality metrics; monitoring; automation. Data quality.|
|**[[14.6 ETL Pipeline]]**|Extract; transform; load; data warehouse prep; scheduling. ETL project.|
|**[[14.7 A/B Test Analysis]]**|Experiment data; statistical testing; significance; reporting. Experimentation.|
|**[[14.8 Production Pipeline]]**|Complete production workflow; optimization; documentation; deployment. Portfolio centerpiece.|
