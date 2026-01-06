### **[[01 NumPy Fundamentals]]**

Master NumPy as the fundamental library for numerical computing in Python. Learn why NumPy powers scientific computing at NASA, CERN, and every data-driven company. Understand arrays, vectorization, and the performance optimizations that make NumPy essential for data science and machine learning. NumPy skills are required for data scientists ($100k-$150k), ML engineers ($120k-$180k), and quantitative analysts ($130k-$200k). Essential for scientific Python and the foundation of the entire data ecosystem.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 NumPy Introduction]]**|What is NumPy; numerical computing; ndarray; NumPy ecosystem; market importance; foundation for data science. Industry context.|
|**[[1.2 Installation & Setup]]**|pip/conda installation; importing numpy; np alias; version checking; Jupyter setup. Environment setup.|
|**[[1.3 Arrays vs Lists]]**|NumPy arrays vs Python lists; performance comparison; homogeneous types; memory efficiency. Why arrays.|
|**[[1.4 Creating Arrays]]**|np.array(); from lists; from tuples; nested arrays; dtype specification. Array creation.|
|**[[1.5 Array Attributes]]**|shape; ndim; size; dtype; itemsize; nbytes; array inspection. Array properties.|
|**[[1.6 Array Data Types]]**|int32; int64; float32; float64; bool; complex; string; dtype conversion. Data types.|
|**[[1.7 Project: First Array Operations]]**|Creating arrays; exploring attributes; basic operations. First project.|

### **[[02 Array Creation Functions]]**

Master NumPy array creation techniques for various use cases. Learn zeros, ones, ranges, and random arrays. Efficient array creation is foundational for numerical computing.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Zeros & Ones]]**|np.zeros(); np.ones(); shape specification; memory allocation; initialization. Zero/one arrays.|
|**[[2.2 Empty & Full]]**|np.empty(); np.full(); uninitialized arrays; fill values; performance. Empty/full arrays.|
|**[[2.3 Ranges]]**|np.arange(); np.linspace(); np.logspace(); start; stop; step; num points. Range arrays.|
|**[[2.4 Identity & Eye]]**|np.eye(); np.identity(); diagonal matrices; k parameter; linear algebra. Identity matrices.|
|**[[2.5 Random Arrays]]**|np.random.rand(); randn(); randint(); random.random(); seed; reproducibility. Random generation.|
|**[[2.6 Like Functions]]**|np.zeros_like(); ones_like(); empty_like(); full_like(); shape matching. Template arrays.|
|**[[2.7 From Functions]]**|np.fromfunction(); np.fromiter(); np.frombuffer(); generating from callables. Functional creation.|
|**[[2.8 Project: Array Initialization]]**|Creating various arrays; matrices; random data; structured initialization. Creation project.|

### **[[03 Array Indexing & Slicing]]**

Master array access patterns for data manipulation. Learn indexing, slicing, and fancy indexing. Efficient data access is essential for all NumPy operations.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Basic Indexing]]**|Single element access; negative indexing; multi-dimensional indexing; index syntax. Element access.|
|**[[3.2 Slicing]]**|Slice notation; start:stop:step; multi-dimensional slicing; slice objects. Array slicing.|
|**[[3.3 Boolean Indexing]]**|Boolean arrays; conditions; filtering; boolean masks; compound conditions. Boolean selection.|
|**[[3.4 Fancy Indexing]]**|Integer array indexing; index arrays; selecting specific elements; ordering. Integer indexing.|
|**[[3.5 Combined Indexing]]**|Mixing indexing types; advanced selection; practical patterns. Combined access.|
|**[[3.6 Views vs Copies]]**|View concept; when views are created; .copy(); memory implications. Views/copies.|
|**[[3.7 Modifying Arrays]]**|Assignment with indexing; broadcasting in assignment; in-place modification. Modification.|
|**[[3.8 Project: Data Selection]]**|Complex indexing; filtering; data extraction; manipulation. Indexing project.|

### **[[04 Array Operations]]**

Master element-wise and array operations for computation. Learn arithmetic, comparison, and logical operations. Operations are the core of NumPy's computational power.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Arithmetic Operations]]**|+, -, *, /, **; element-wise math; operator overloading; np.add, np.subtract. Basic math.|
|**[[4.2 Comparison Operations]]**|==, !=, <, >, <=, >=; element-wise comparison; boolean arrays. Comparisons.|
|**[[4.3 Logical Operations]]**|np.logical_and; logical_or; logical_not; &, |, ~; boolean operations. Logic.|
|**[[4.4 Universal Functions (ufuncs)]]**|np.sin; np.cos; np.exp; np.log; np.sqrt; vectorized functions. Math functions.|
|**[[4.5 Aggregation Functions]]**|np.sum; np.mean; np.std; np.min; np.max; axis parameter. Statistics.|
|**[[4.6 Cumulative Functions]]**|np.cumsum; np.cumprod; running totals; cumulative operations. Cumulative ops.|
|**[[4.7 Where Function]]**|np.where(); conditional selection; value replacement; vectorized if-else. Conditional.|
|**[[4.8 Project: Data Analysis]]**|Statistical analysis; operations; transformations; computation. Operations project.|

### **[[05 Broadcasting]]**

Master broadcasting for efficient array operations. Learn broadcasting rules, shapes, and patterns. Broadcasting enables powerful operations without explicit loops.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Broadcasting Concept]]**|What is broadcasting; implicit expansion; shape compatibility; performance. Broadcasting basics.|
|**[[5.2 Broadcasting Rules]]**|Dimension matching; trailing dimensions; size-1 expansion; rule application. Rules.|
|**[[5.3 Scalar Broadcasting]]**|Scalar-array operations; automatic expansion; common pattern. Scalar broadcast.|
|**[[5.4 1D-2D Broadcasting]]**|Row broadcasting; column broadcasting; adding dimensions; common patterns. 1D-2D.|
|**[[5.5 Shape Manipulation]]**|np.newaxis; reshape for broadcasting; expand_dims; dimension adding. Shape adjustment.|
|**[[5.6 Broadcasting Errors]]**|Incompatible shapes; debugging broadcasts; error messages; fixing issues. Troubleshooting.|
|**[[5.7 Broadcasting Performance]]**|Memory efficiency; avoiding copies; vectorization; performance benefits. Performance.|
|**[[5.8 Project: Vectorized Computation]]**|Complex calculations without loops; broadcasting patterns; optimization. Broadcasting project.|

### **[[06 Shape Manipulation]]**

Master array reshaping for data transformation. Learn reshape, transpose, and concatenation. Shape manipulation is essential for data preparation.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Reshape]]**|np.reshape(); -1 inference; order parameter; reshape patterns. Reshaping.|
|**[[6.2 Transpose]]**|np.transpose(); .T attribute; axes reordering; multi-dimensional transpose. Transposing.|
|**[[6.3 Flatten & Ravel]]**|np.flatten(); np.ravel(); 1D conversion; copy vs view. Flattening.|
|**[[6.4 Concatenate]]**|np.concatenate(); axis parameter; joining arrays; stacking arrays. Joining.|
|**[[6.5 Stack Functions]]**|np.vstack(); np.hstack(); np.dstack(); np.stack(); combining arrays. Stacking.|
|**[[6.6 Split Functions]]**|np.split(); np.vsplit(); np.hsplit(); array_split(); dividing arrays. Splitting.|
|**[[6.7 Squeeze & Expand]]**|np.squeeze(); np.expand_dims(); dimension manipulation; shape adjustment. Dimension ops.|
|**[[6.8 Project: Data Preparation]]**|Reshaping data; combining datasets; transforming shapes; preprocessing. Shape project.|

### **[[07 Linear Algebra]]**

Master NumPy linear algebra for scientific computing. Learn matrix operations, decompositions, and equation solving. Linear algebra is essential for machine learning and scientific applications.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Matrix Multiplication]]**|np.dot(); @ operator; np.matmul(); inner product; matrix products. Matrix multiplication.|
|**[[7.2 Matrix Operations]]**|np.linalg.inv(); np.linalg.det(); matrix_rank; trace; matrix functions. Matrix functions.|
|**[[7.3 Eigenvalues]]**|np.linalg.eig(); eigenvalues; eigenvectors; applications; spectral analysis. Eigendecomposition.|
|**[[7.4 SVD]]**|np.linalg.svd(); singular value decomposition; dimensionality reduction. SVD.|
|**[[7.5 Solving Equations]]**|np.linalg.solve(); linear systems; least squares; np.linalg.lstsq(). Equation solving.|
|**[[7.6 Norms]]**|np.linalg.norm(); vector norms; matrix norms; L1, L2, Frobenius. Norms.|
|**[[7.7 Project: ML Math]]**|Linear algebra for ML; matrix operations; eigenvectors; PCA basics. Linear algebra project.|

### **[[08 Random Module]]**

Master NumPy random for stochastic computing. Learn distributions, sampling, and reproducibility. Random is essential for simulations, ML, and statistical analysis.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Random Basics]]**|np.random.rand(); np.random.random(); uniform distribution; basic random. Random basics.|
|**[[8.2 Random Generator]]**|np.random.default_rng(); Generator; modern random API; best practices. New API.|
|**[[8.3 Seeds & Reproducibility]]**|np.random.seed(); deterministic random; reproducible results; testing. Reproducibility.|
|**[[8.4 Distributions]]**|normal(); uniform(); binomial(); poisson(); exponential(); distributions. Distributions.|
|**[[8.5 Sampling]]**|choice(); shuffle(); permutation(); random selection; sampling patterns. Sampling.|
|**[[8.6 Integer Random]]**|randint(); integers(); random integers; range specification. Integer random.|
|**[[8.7 Project: Simulation]]**|Monte Carlo; statistical simulation; random processes; experiments. Simulation project.|

### **[[09 Statistics]]**

Master NumPy statistics for data analysis. Learn descriptive statistics, percentiles, and correlation. Statistics are fundamental to data science and analysis.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Descriptive Statistics]]**|np.mean(); np.median(); np.std(); np.var(); central tendency; spread. Descriptive stats.|
|**[[9.2 Percentiles]]**|np.percentile(); np.quantile(); quartiles; distribution analysis. Percentiles.|
|**[[9.3 Min & Max]]**|np.min(); np.max(); np.argmin(); np.argmax(); extrema finding. Extremes.|
|**[[9.4 Histogram]]**|np.histogram(); np.bincount(); frequency distribution; bin edges. Histograms.|
|**[[9.5 Correlation]]**|np.corrcoef(); np.cov(); correlation matrices; covariance. Correlation.|
|**[[9.6 Unique & Counts]]**|np.unique(); return_counts; value frequencies; set operations. Unique values.|
|**[[9.7 Project: Statistical Analysis]]**|Complete statistical analysis; distributions; correlations; reporting. Statistics project.|

### **[[10 File I/O]]**

Master NumPy file operations for data persistence. Learn saving and loading arrays in various formats. File I/O enables data sharing and storage.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 NPY Format]]**|np.save(); np.load(); .npy files; single array storage; binary format. NPY files.|
|**[[10.2 NPZ Format]]**|np.savez(); np.savez_compressed(); multiple arrays; archive format. NPZ files.|
|**[[10.3 Text Files]]**|np.savetxt(); np.loadtxt(); CSV; delimiter; header; comments. Text files.|
|**[[10.4 CSV & Genfromtxt]]**|np.genfromtxt(); missing values; dtype; CSV handling; flexibility. Complex text.|
|**[[10.5 Memory Mapping]]**|np.memmap(); large file handling; memory-efficient; disk-backed arrays. Memory mapping.|
|**[[10.6 Binary Files]]**|np.fromfile(); np.tofile(); raw binary; dtype specification. Binary I/O.|
|**[[10.7 Project: Data Pipeline]]**|Loading data; processing; saving results; format conversion. I/O project.|

### **[[11 Performance Optimization]]**

Master NumPy performance for efficient computing. Learn vectorization, memory optimization, and profiling. Performance skills are critical for large-scale computation.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Vectorization]]**|Avoiding loops; vectorized operations; ufuncs; performance gains. Vectorization.|
|**[[11.2 Memory Layout]]**|C order vs Fortran order; contiguous arrays; memory access patterns. Memory layout.|
|**[[11.3 In-Place Operations]]**|In-place modification; out parameter; memory reuse; avoiding copies. In-place ops.|
|**[[11.4 Views & Strides]]**|Stride tricks; as_strided; memory views; advanced optimization. Strides.|
|**[[11.5 Data Types]]**|dtype optimization; float32 vs float64; memory/precision tradeoff. Type optimization.|
|**[[11.6 Profiling]]**|%timeit; memory profiling; bottleneck identification; benchmarking. Profiling.|
|**[[11.7 Numba & Cython]]**|JIT compilation; Numba basics; Cython overview; extreme performance. Acceleration.|
|**[[11.8 Project: Optimization]]**|Optimizing slow code; vectorization; memory; benchmarks. Performance project.|

### **[[12 Advanced NumPy]]**

Master advanced NumPy features for complex applications. Learn structured arrays, masked arrays, and advanced techniques. Advanced skills enable expert-level NumPy usage.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Structured Arrays]]**|Compound dtypes; named fields; record arrays; tabular data. Structured data.|
|**[[12.2 Masked Arrays]]**|np.ma module; missing data; masked operations; mask handling. Masked arrays.|
|**[[12.3 Custom dtypes]]**|User-defined types; complex structures; dtype creation. Custom types.|
|**[[12.4 Array Protocols]]**|__array__; __array_interface__; array-like objects; interoperability. Protocols.|
|**[[12.5 UFuncs Creation]]**|np.frompyfunc(); np.vectorize(); custom ufuncs; vectorizing functions. Custom ufuncs.|
|**[[12.6 Matrix Class]]**|np.matrix; matrix operations; linear algebra shortcuts; deprecation. Matrix class.|
|**[[12.7 Project: Custom Arrays]]**|Advanced array usage; structured data; custom operations. Advanced project.|

### **[[13 NumPy Ecosystem]]**

Master NumPy integration with the scientific Python ecosystem. Learn SciPy, Pandas, and ML library integration. Ecosystem knowledge enables complete scientific computing workflows.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 SciPy Integration]]**|scipy.linalg; scipy.stats; scipy.optimize; extended functionality. SciPy.|
|**[[13.2 Pandas Integration]]**|DataFrame to array; array to DataFrame; .values; .to_numpy(). Pandas.|
|**[[13.3 Matplotlib Integration]]**|Plotting arrays; image data; visualization; array-based plotting. Matplotlib.|
|**[[13.4 Scikit-learn Integration]]**|Feature matrices; train/test data; preprocessing; ML pipelines. Scikit-learn.|
|**[[13.5 TensorFlow/PyTorch]]**|Tensor conversion; numpy compatibility; deep learning integration. Deep learning.|
|**[[13.6 CuPy (GPU)]]**|GPU arrays; CUDA acceleration; CuPy basics; drop-in replacement. GPU computing.|
|**[[13.7 Project: ML Pipeline]]**|End-to-end workflow; data preparation; feature engineering; modeling. Ecosystem project.|

### **[[14 Real-World Projects]]**

Master building production NumPy solutions. Build impressive portfolio pieces that demonstrate numerical computing expertise. Real projects are essential for data science and engineering positions.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Image Processing]]**|Image as arrays; filtering; transformation; manipulation; OpenCV integration. Image processing.|
|**[[14.2 Signal Processing]]**|Time series; FFT; filtering; audio processing; frequency analysis. Signals.|
|**[[14.3 Financial Analysis]]**|Returns calculation; portfolio optimization; risk metrics; Monte Carlo. Finance.|
|**[[14.4 Physics Simulation]]**|Numerical methods; differential equations; particle systems; modeling. Physics.|
|**[[14.5 ML from Scratch]]**|Linear regression; gradient descent; neural network basics; learning algorithms. ML fundamentals.|
|**[[14.6 Data Preprocessing]]**|Normalization; standardization; feature engineering; missing data. Preprocessing.|
|**[[14.7 Performance Computing]]**|Large-scale computation; optimization; parallel patterns; efficiency. High performance.|
|**[[14.8 Production Code]]**|Complete numerical application; optimization; documentation. Portfolio centerpiece.|
