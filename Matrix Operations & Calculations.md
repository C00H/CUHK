### Ch1

<font color="navy">**Matrix Operations & Calculations**</font>

For a $2 \times 2$ matrix $A = \begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix}$:

• Determinant ($2 \times 2$): $|A| = a_{11}a_{22} - a_{21}a_{12}$. • Inverse ($2 \times 2$): $A^{-1} = \frac{1}{|A|} \begin{bmatrix} a_{22} & -a_{12} \\ -a_{21} & a_{11} \end{bmatrix}$. • <font color="red">**Note**</font>: $A^{-1}$ exists only if $|A| \ne 0$ 
• If $A = \begin{bmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{bmatrix}$    $$A^{-1} = $$$$= \frac{1}{|A|} \begin{bmatrix} a_{22}a_{33} - a_{32}a_{23} & a_{32}a_{13} - a_{12}a_{33} & a_{12}a_{23} - a_{22}a_{13} \\ a_{31}a_{23} - a_{21}a_{33} & a_{11}a_{33} - a_{31}a_{13} & a_{21}a_{13} - a_{11}a_{23} \\ a_{21}a_{32} - a_{31}a_{22} & a_{31}a_{12} - a_{11}a_{32} & a_{11}a_{22} - a_{21}a_{12} \end{bmatrix}$$

• Trace: $tr(A) = \sum_{i=1}^p a_{ii}$. • <font color="red">**Note**</font>: Cyclic property holds, meaning $tr(AB) = tr(BA)$ and $tr(ABC) = tr(CAB) = tr(BCA)$, provided the dimensions allow for computation. $tr(A+B) = tr(A)+tr(B)$

• Positive Definite & Semidefinite:

  • A symmetric matrix $A$ is positive semidefinite ($A \ge 0$) if $x^\prime Ax \ge 0$ for any nonzero vector $x$.

  • A symmetric matrix $A$ is positive definite ($A > 0$) if $x^\prime Ax > 0$ for any nonzero vector $x$.

• Eigenvalues ($\lambda_i$): Calculated by solving the characteristic equation $|A - \lambda I_p| = 0$.

• Eigenvectors ($h_i$): Solved via $Ah_i = \lambda_i h_i$. A normalized eigenvector requires $h_i^\prime h_i = 1$.

  • <font color="red">**Note**</font>: For a real symmetric matrix, eigenvalues are real, and eigenvectors corresponding to distinct eigenvalues are strictly orthogonal ($h_i^\prime h_j = 0$).

• Spectral Decomposition: $A = HDH^\prime$. $A^{1/2} = HD^{1/2}H^\prime$

  • <font color="red">**Note**</font>: $D = diag(\lambda_1, ..., \lambda_p)$ and $H = (h_1 ... h_p)$ consists of normalized eigenvectors. Because $H$ is orthogonal, $H^\prime H = I_p$.

• Symmetric Square Root: $A^{1/2} = HD^{1/2}H^\prime$, where $D^{1/2} = diag(\sqrt{\lambda_1}, ..., \sqrt{\lambda_p})$. D是只保留$\Sigma$主对角线方差的对角阵，作用是将协方差标准化为[-1,1]之间的相关系数

  • <font color="red">**Note**</font>: This is only computable if $A$ is positive semidefinite ($A \ge 0$), guaranteeing all $\lambda_i \ge 0$.

<font color="navy">**Population Random Vectors**</font>

• Population Covariance Matrix: $\Sigma = Var(x) = E((x - E(x))(x - E(x))^\prime) = E(xx^\prime) - E(x)E(x)^\prime$.

  • <font color="red">**Note**</font>: $\Sigma$ is symmetric and positive semidefinite ($\Sigma \ge 0$). Diagonal element $\sigma_{ii}$ is the variance of $X_i$, off-diagonal $\sigma_{ij}$ is the covariance between $X_i$ and $X_j$.

• Covariance Between Two Vectors ($x$ and $y$): $Cov(x, y) = E((x - E(x))(y - E(y))^\prime) = E(xy^\prime) - E(x)E(y)^\prime$.

• Population Correlation Matrix: $R = D^{-1/2} \Sigma D^{-1/2}$.

  • <font color="red">**Note**</font>: $D$ contains the variances, so $D^{-1/2} = diag(\frac{1}{\sqrt{\sigma_{11}}}, ..., \frac{1}{\sqrt{\sigma_{pp}}})$.

• Linear Combinations (Vectors): $E(a^\prime x) = a^\prime E(x)$. $Var(a^\prime x) = a^\prime \Sigma a$. $Cov(a^\prime x, b^\prime x) = a^\prime \Sigma b$.

• Linear Combinations (Matrices): $Var(Ax) = A \Sigma A^\prime$. $Cov(Ax, Bx) = A \Sigma B^\prime$.

• <font color="red">**Note**</font>: $a^\prime x$ outputs a scalar variance, while $Ax$ outputs a covariance matrix.

<font color="navy">**Sample Data Matrix & Estimators**</font>

• Sample Mean Vector: $\overline{x} = \frac{1}{n} X^\prime 1_n$. • <font color="red">**Note**</font>: It is an unbiased estimator, $E(\overline{x}) = \mu$. 

Its theoretical variance is $Var(\overline{x}) = \frac{1}{n} \Sigma$. (Proof: $Var(\frac{1}{n}\sum x_i) = \frac{1}{n^2}\sum Var(x_i) = \frac{1}{n}\Sigma$).

• SSCP Matrix: $A = X^\prime X - n \overline{x} \overline{x}^\prime = (X - 1_n \overline{x}^\prime)^\prime(X - 1_n \overline{x}^\prime)$.

  • Element Calculation: $a_{ij} = \sum_{k=1}^n (x_{ki} - \overline{x}_i)(x_{kj} - \overline{x}_j)$.

  • Positive Semidefinite: $A \ge 0$. (Proof: For any $y=Bx$, $x^\prime B^\prime Bx = y^\prime y \ge 0$, and $A$ is in the form of $B^\prime B$).

• Sample Covariance Matrix: $S = \frac{1}{n-1} A = \frac{1}{n-1} \sum_{k=1}^n (x_k - \overline{x})(x_k - \overline{x})^\prime$.

  • <font color="red">**Note**</font>: The denominator must strictly be $n-1$ for $S$ to be an unbiased estimator. $E(S) = \Sigma$. (Proof: $E(A) = (n-1)\Sigma$, hence $E(S) = \Sigma$). The matrix $S$ is always symmetric positive semidefinite.

• Sample Correlation Matrix: $R = D^{-1/2} S D^{-1/2}$.

  • <font color="red">**Note**</font>: Here, $D^{-1/2} = diag(\frac{1}{\sqrt{s_{11}}}, ..., \frac{1}{\sqrt{s_{pp}}})$ relies on the sample variances $s_{ii}$ found on the diagonal of $S$.

<font color="navy">**Key Univariate Distributions (Building Blocks)**</font>

<font color="navy">1.</font> Chi-square: If $Z_1, ..., Z_\nu$ are iid $N(0,1)$, then $X = Z_1^2 + ... + Z_\nu^2 \sim \chi_\nu^2$.

  • Sample Variance Relation: $\frac{(n-1)S^2}{\sigma^2} \sim \chi_{n-1}^2$.

<font color="navy">2.</font> Student's t: $T = \frac{Z}{\sqrt{X/\nu}} \sim t_\nu$, provided $Z \sim N(0,1)$ and $X \sim \chi_\nu^2$ are independent.   

• <font color="red">**Note**</font>: For sample testing, if $Y_1, ..., Y_n \sim iid \ N(\mu, \sigma^2)$, then the sample mean is distributed as $\overline{Y} \sim N(\mu, \frac{\sigma^2}{n})$. This leads to the test statistic $T = \frac{\sqrt{n}(\overline{Y}-\mu)}{S} \sim t_{n-1}$.

<font color="navy">3.</font> Fisher's F: $F = \frac{X_1/u}{X_2/v} \sim F_{u,v}$, provided $X_1 \sim \chi_u^2$ and $X_2 \sim \chi_v^2$ are independent.   

• Variance Ratio: If $X_1, ..., X_m \sim iid \ N(\mu_1, \sigma_1^2)$ and $Y_1, ..., Y_n \sim iid \ N(\mu_2, \sigma_2^2)$ are two independent samples , then $F = \frac{S_1^2/\sigma_1^2}{S_2^2/\sigma_2^2} = \frac{\sigma_2^2 S_1^2}{\sigma_1^2 S_2^2} \sim F_{m-1, n-1}$.   

• <font color="red">**Note**</font>: If a variable $T \sim t_v$, then its square $T^2 \sim F_{1,v}$.

### Ch2

<font color="navy">**Notation (Multivariate Normal)**</font>

• $N_p(\mu, \Sigma)$: $p$-variate normal distribution with mean vector $\mu$ and covariance matrix $\Sigma$.

• $d_i^2$: Squared generalized distance (Mahalanobis distance) for the $i$-th observation, defined as $d_i^2 = (x_i - \overline{x})^\prime S^{-1} (x_i - \overline{x})$.

• $A$: Sum of Squares and Cross product (SSCP) matrix, defined as $\sum_{i=1}^n (x_i - \overline{x})(x_i - \overline{x})^\prime$.

• $W_p(m, \Sigma)$: Wishart distribution with $m$ degrees of freedom and scale matrix $\Sigma$.

• $\Sigma_{11\bullet 2}$: Conditional covariance matrix of $x_1$ given $x_2$, defined as $\Sigma_{11\bullet 2} = \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21}$.

<font color="navy">**The Multivariate Normal Distribution**</font>

• Density Function: $f(x) = \frac{1}{(2\pi)^{p/2}|\Sigma|^{1/2}} \exp\{-\frac{1}{2}(x - \mu)^\prime \Sigma^{-1} (x - \mu)\}$.

• Bivariate Normal ($p=2$): Covariance matrix is $\Sigma = \begin{bmatrix} \sigma_1^2 & \rho\sigma_1\sigma_2 \\ \rho\sigma_1\sigma_2 & \sigma_2^2 \end{bmatrix}$.

  • Inverse of Covariance: $\Sigma^{-1} = \frac{1}{\sigma_1^2\sigma_2^2(1-\rho^2)} \begin{bmatrix} \sigma_2^2 & -\rho\sigma_1\sigma_2 \\ -\rho\sigma_1\sigma_2 & \sigma_1^2 \end{bmatrix}$.

  • <font color="red">**Note**</font>: The density $f(x_1, x_2)$ relies heavily on the correlation coefficient $\rho$ between $X_1$ and $X_2$.

<font color="navy">**Properties & Linear Transformations**</font>

• Linear Combination: If $x \sim N_p(\mu, \Sigma)$ and $a \ne 0$, then $a^\prime x \sim N(a^\prime \mu, a^\prime \Sigma a)$.

• Addition: If $x \sim N_p(\mu_1, \Sigma_1)$ and $y \sim N_p(\mu_2, \Sigma_2)$ are independent, then $x + y \sim N_p(\mu_1 + \mu_2, \Sigma_1 + \Sigma_2)$.

• Matrix Transformation: For a $q \times p$ matrix $B$ and $q \times 1$ vector $b$, $y = Bx + b \sim N_q(B\mu + b, B\Sigma B^\prime)$.

<font color="navy">**Random Samples & MLE**</font>

Let $x_1, ..., x_n$ be iid $N_p(\mu, \Sigma)$:   Joint Likelihood Function: 

$L(\mu, \Sigma|x_1, ..., x_n) = (2\pi)^{-np/2} |\Sigma|^{-n/2} \exp\{-\frac{1}{2} \sum_{i=1}^n (x_i - \mu)^\prime \Sigma^{-1} (x_i - \mu)\}  = (2\pi)^{-np/2} |\Sigma|^{-n/2} \exp\{-\frac{1}{2} tr(\Sigma^{-1} A)\} \exp\{-\frac{n}{2} (\overline{x} - \mu)^\prime \Sigma^{-1} (\overline{x} - \mu)\}$

• Sample Mean Distribution: $\overline{x} \sim N_p(\mu, \frac{1}{n}\Sigma)$

• Quadratic Form of Mean: $n(\overline{x} - \mu)^\prime \Sigma^{-1} (\overline{x} - \mu) \sim \chi_p^2$.

• Mahalanobis Distance Distribution: $d_i^2 = (x_i - \overline{x})^\prime S^{-1} (x_i - \overline{x}) \sim \chi_p^2$ asymptotically for large $n$.

• MLE of $\mu$: $\hat{\mu} = \overline{x}$. • MLE of $\Sigma$: $\hat{\Sigma} = \frac{1}{n} A = \frac{1}{n} \sum_{i=1}^n (x_i - \overline{x})(x_i - \overline{x})^\prime$.

• Unbiased Estimator of $\Sigma$: $S = \frac{1}{n-1} A$. <font color="red">**Note**</font>: $\overline{x}$ and $S$ are independent.

<font color="navy">**Marginal and Conditional Distributions**</font>

Partition $x = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$, $\mu = \begin{bmatrix} \mu_1 \\ \mu_2 \end{bmatrix}$, $\Sigma = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$:

<font color="navy">1.</font> Marginal Distribution: $x_1 \sim N_q(\mu_1, \Sigma_{11})$. Any subset of $x$ is normally distributed.从x中任意取出q个分量组成的子集，这个子集的边缘分布也必然服从q元正态分布

<font color="navy">2.</font> Independence: $x_1$ and $x_2$ are independent if and only if $\Sigma_{12} = 0$.

<font color="navy">3.</font> （Schur Complement）Let $\Sigma_{11\bullet 2} = \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21}$, we have:  $x_1 - \Sigma_{12}\Sigma_{22}^{-1}x_2 \sim N_q(\mu_1 - \Sigma_{12}\Sigma_{22}^{-1}\mu_2, \Sigma_{11\bullet 2})$. 

<font color="red">**Note**</font>: This residual vector is strictly independent of $x_2$. 目的是构造一个与x2完全独立的新rm

<font color="navy">4.</font> Conditional Distribution: The distribution of $x_1$ given $x_2 = x_2^0$ is $N_q(\mu_1 + \Sigma_{12}\Sigma_{22}^{-1}(x_2^0 - \mu_2), \Sigma_{11\bullet 2})$.

<font color="navy">**Wishart Distribution & Quadratic Forms**</font>

• Wishart Definition: If $z_1, ..., z_m \sim iid \ N_p(0, \Sigma)$, then $B = \sum_{i=1}^m z_i z_i^\prime \sim W_p(m, \Sigma)$.   

​	• Density Function ($B$): $f_m(B|\Sigma) = \frac{|B|^{(m-p-1)/2}|\Sigma|^{-m/2}e^{-tr(\Sigma^{-1}B)/2}}{K}$, where $K = 2^{mp/2}\pi^{p(p-1)/4}\prod_{i=1}^p \Gamma(\frac{m+1-i}{2})$. 

• SSCP Distribution: The matrix $A = (n-1)S \sim W_p(n-1, \Sigma)$.   

​	• Density Function ($A$): $f_{n-1}(A|\Sigma) = \frac{|A|^{(n-p-2)/2}|\Sigma|^{-(n-1)/2}e^{-tr(\Sigma^{-1}A)/2}}{K}$, where $K = 2^{(n-1)p/2}\pi^{p(p-1)/4}\prod_{i=1}^p \Gamma(\frac{n-i}{2})$. 

• Connection between Wishart and $\chi^2$: In the univariate case ($p=1$), $B = Z_1^2 + ... + Z_m^2$ where $Z_1, ..., Z_m \sim iid \ N(0, \sigma^2)$.  

​	• The density of $B$ is $f_m(B|\sigma^2) = \frac{B^{m/2-1}(\sigma^2)^{-m/2}e^{-B/(2\sigma^2)}}{K}$, where $K = 2^{m/2}\Gamma(m/2)$.   

• We may write $B \sim W_1(m, \sigma^2)$ or $B/\sigma^2 \sim \chi_m^2$.   • If we let $V = B/\sigma^2$, the density function of $V$ is $f_V(v) = \frac{v^{m/2-1}e^{-v/2}}{2^{m/2}\Gamma(m/2)}$.

• Cochran's Theorem: Let $Y_1, ..., Y_n \sim iid \ N(0, \sigma^2)$. If $\sum_{i=1}^n Y_i^2 = Q_1 + ... + Q_k$ where $Q_i = y^\prime A_i y$ and $\sum rank(A_i) = n$, then $Q_i$ are independent and $Q_i/\sigma^2 \sim \chi_{rank(A_i)}^2$.

  • Theorem 3 (Special Case): If $Y_1, ..., Y_n \sim iid \ N(\mu, \sigma^2)$, then $\frac{(n-1)S^2}{\sigma^2} = \sum_{i=1}^n \frac{(Y_i - \overline{Y})^2}{\sigma^2} \sim \chi_{n-1}^2$.

  • Lemma 4: Let $G$ be a $p \times p$ matrix such that $G^2=G$ and $tr(G)=k$. Then there exists a $k \times p$ matrix $E$ such that $EE^\prime = I_k$ and $E^\prime E = G$.

• General Quadratic Form Application: If $x \sim N_p(\mu, \Sigma)$, then $y = \Sigma^{-1/2}(x-\mu) \sim N_p(0, I_p)$, which implies $y^\prime y = (x-\mu)^\prime \Sigma^{-1}(x-\mu) \sim \chi_p^2$.

<font color="navy">**Practical Procedures: Outliers, Generation & Testing**</font>

• Generating Normal Vectors: Generate independent $z_i \sim N_p(0, I_p)$. Use spectral decomposition $\Sigma = HDH^\prime$, then compute $x_i = \sigma z_i + \mu= HD^{1/2}z_i + \mu$ to get $x_i \sim N_p(\mu, \Sigma)$. rescaling the original spherical shape of zi to an elliptical shape and then rotating the axis along the direction of the eigenvectors.

• Outlier Detection:

  <font color="navy">1.</font> Compute Mahalanobis distance $d_i^2 = (x_i - \overline{x})^\prime S^{-1} (x_i - \overline{x})$ for each observation.

  <font color="navy">2.</font> An observation is flagged as a potential outlier if $d_i^2 > q_p(0.99)$, where $q_p(0.99)$ is the 99th percentile of the $\chi_p^2$ distribution.

• Checking Multivariate Normality (QQ-Plot):

  <font color="navy">1.</font> Compute $d_i^2$ for all observations.

  <font color="navy">2.</font> Order them ascendingly as $d_{(i)}^2$.

  <font color="navy">3.</font> Compute theoretical quantiles $q_p(i)$ from $\chi_p^2$ using probability $(i-0.5)/n$.

  <font color="navy">4.</font> Plot $d_{(i)}^2$ against $q_p(i)$. A straight line suggests multivariate normality.

  <font color="navy">5.</font> Kolmogorov-Smirnov (KS) Test: Use test statistic $D_n = \sup_x |F_n(x) - F(x)|$ to formally test if $d_i^2$ follows $\chi_p^2$.

### Ch3

<font color="navy">**Notation (Hypothesis Testing)**</font>

• $d_j$: The difference vector for the $j$-th pair in a paired comparison, defined as $x_{1j} - x_{2j}$.

• $\overline{d}$: Sample mean vector of the differences.

• $S_d$: Sample covariance matrix of the differences.

• $S_p$: Pooled sample covariance matrix for two independent samples.

• $C$: A $q \times p$ contrast matrix of constants used for linear combinations.

<font color="navy">**Hotelling's $T^2$ Definition & Foundation**</font>

• Definition: If $d$ and $M$ are independently distributed as $d \sim N_p(0, I)$ and $M \sim W_p(m, I)$, then $md^\prime M^{-1}d \sim T^2(p, m)$.

• Key Results:

  <font color="navy">1.</font> If $d \sim N_p(\mu, \Sigma)$ and $M \sim W_p(m, \Sigma)$ are independent, then $m(d - \mu)^\prime M^{-1} (d - \mu) \sim T^2(p, m)$.

  <font color="navy">2.</font> Relation to F-distribution: $\frac{m-p+1}{p} \frac{T^2(p, m)}{m} = F_{p, m-p+1}$.

<font color="navy">**1. One-Sample Test for Mean Vector ($\mu = \mu_0$)**</font>

<font color="navy">**Case A: Population Covariance $\Sigma$ is KNOWN**</font>

• Test Statistic: $n(\overline{x} - \mu_0)^\prime \Sigma^{-1} (\overline{x} - \mu_0) \sim \chi_p^2$.

• Decision Rule: Reject $H_0$ if the statistic $> \chi_p^2(\alpha)$.

  • <font color="red">**Note**</font>: This is the exact multivariate analog of the univariate Z-test. Since $\Sigma$ is known, we use the Chi-square distribution directly.

<font color="navy">**Case B: Population Covariance $\Sigma$ is UNKNOWN (Hotelling's $T^2$)**</font>

• Test Statistic Definition: $T_0^2 = n(\overline{x} - \mu_0)^\prime S^{-1} (\overline{x} - \mu_0)$.

• Distribution: $T_0^2 \sim T^2(p, n-1)$.

  • <font color="red">**Note**</font>: Here $p$ refers to the dimension (number of variables) of the random vector $x$.

• F-Transformation: $\frac{n-p}{p}\frac{T_0^2}{n-1} \sim F_{p, n-p}$.

• Decision Rule: Reject $H_0$ if $\frac{n-p}{p}\frac{T_0^2}{n-1} > F_{p, n-p}(\alpha)$.

  • <font color="red">**Note**</font>: This is the multivariate analog of the one-sample t-test. $S$ must be the unbiased estimator with denominator $n-1$. Pay close attention to the degrees of freedom for the F-distribution: numerator is $p$, denominator is $n-p$.

<font color="navy">**2. Paired Comparison Test**</font>

Used when experimental units are paired or measurements are taken twice on the same unit (dependent samples).

• Assumption: $d_1, ..., d_n \sim iid \ N_p(\delta, \Sigma)$. difference e.g.  $d_1 = x_{11}-x_{21}$

• Hypothesis: $H_0: \delta = 0$ versus $H_1: \delta \ne 0$, where $\delta$ is the population mean difference.

• Difference Vector: $d_j = x_{1j} - x_{2j}$ for $j = 1, ..., n$.

• Sample Difference Mean: $\overline{d} = \frac{1}{n} \sum_{j=1}^n d_j$.

• Sample Difference Covariance: $S_d = \frac{1}{n-1} \sum_{j=1}^n (d_j - \overline{d})(d_j - \overline{d})^\prime$.

• Test Statistic: $T^2 = n \overline{d}^\prime S_d^{-1} \overline{d}$.

• Transformation & Rule: Reject $H_0$ if $\frac{n-p}{p}\frac{T^2}{n-1} = \frac{n-p}{p}\frac{n}{n-1}(\overline{d} - \delta)^\prime S_d^{-1}(\overline{d} - \delta) > F_{p, n-p}(\alpha)$.

  • <font color="red">**Note**</font>: Paired comparison reduces a two-sample problem into a one-sample $T^2$ test on the differences $d_j$. The dimensions $p$ and sample size $n$ refer to the difference vectors, not the original separate measurements.

<font color="navy">**3. Two-Sample $T^2$ Test (Independent Samples)**</font>

Used to test $H_0: \mu_1 = \mu_2$ for two independent groups.  前提假设：两个总体的协方差矩阵必须相等

• Assumption: Both populations must share the same covariance matrix $\Sigma$.

• Pooled Covariance: $S_p = \frac{(n_1-1)S_1 + (n_2-1)S_2}{n_1+n_2-2}$.

  • <font color="red">**Note**</font>: This explicitly uses the denominator $(n_1+n_2-2)$ to ensure $S_p$ is an unbiased estimator of the common $\Sigma$.

• Test Statistic: $T^2 = \frac{n_1 n_2}{n_1+n_2} (\overline{x}_1 - \overline{x}_2)^\prime S_p^{-1} (\overline{x}_1 - \overline{x}_2)$.

• Transformation & Rule: Reject $H_0$ if $\frac{n_1+n_2-p-1}{p} \frac{T^2}{n_1+n_2-2} > F_{p, n_1+n_2-p-1}(\alpha)$.

  • <font color="red">**Note**</font>: Notice the scaling factor $\frac{n_1 n_2}{n_1+n_2}$, which comes from the variance of $(\overline{x}_1 - \overline{x}_2)$. The F-distribution denominator degrees of freedom change to $n_1+n_2-p-1$.

<font color="navy">**4. Testing Linear Combinations & Repeated Measurements**</font>

Used to test relationships between variables, such as "is the mean of variable 1 equal to variable 2?".

• General Hypothesis: $H_0: C\mu = 0$ where $C$ is a $q \times p$ constant matrix.

• Under $H_0$: $C\overline{x} \sim N_q(0, \frac{1}{n}C\Sigma C^\prime)$.

• Test Statistic: $T^2 = n\overline{x}^\prime C^\prime (CSC^\prime)^{-1} C\overline{x}$.

• Transformation & Rule: Reject $H_0$ if $\frac{n-q}{q}\frac{T^2}{n-1} > F_{q, n-q}(\alpha)$.

  • <font color="red">**Note**</font>: We replace $p$ with $q$ (the number of rows in $C$) in the F-transformation formula because applying $C$ reduces the dimensionality from $p$ down to $q$.

<font color="navy">**Application: Repeated Measurements**</font>

• Goal: Test if means over $p$ time periods are identical ($H_0: \mu_1 = \mu_2 = ... = \mu_p$).

• Contrast Matrix $C$: A $(p-1) \times p$ matrix constructed as adjacent differences (e.g., row 1 is $1, -1, 0...$; row 2 is $0, 1, -1...$).

• Rule: Since $q = p-1$, the test rejects if $\frac{n-p+1}{p-1}\frac{T^2}{n-1} > F_{p-1, n-p+1}(\alpha)$.

------

<font color="navy">***Important Proofs & Derivations***</font>

**Unbiasedness of Sample Covariance ($E(S) = \Sigma$)**

- First, expand the SSCP matrix $A = \sum_{i=1}^n x_i x_i^\prime - n\overline{x}\overline{x}^\prime$.
- Take the expectation: $E(A) = \sum_{i=1}^n E(x_i x_i^\prime) - n E(\overline{x}\overline{x}^\prime)$.
- Using the property $E(yy^\prime) = Var(y) + E(y)E(y)^\prime$, we get $E(x_i x_i^\prime) = \Sigma + \mu\mu^\prime$.
- Similarly, $E(\overline{x}\overline{x}^\prime) = Var(\overline{x}) + E(\overline{x})E(\overline{x})^\prime = \frac{1}{n}\Sigma + \mu\mu^\prime$.
- Substitute these back: $E(A) = n(\Sigma + \mu\mu^\prime) - n(\frac{1}{n}\Sigma + \mu\mu^\prime) = n\Sigma + n\mu\mu^\prime - \Sigma - n\mu\mu^\prime = (n-1)\Sigma$.
- Since $S = \frac{1}{n-1}A$, it follows that $E(S) = \frac{1}{n-1}(n-1)\Sigma = \Sigma$.

**Maximum Likelihood Estimator (MLE) of $\Sigma$ using the Trace Trick**

- The log-likelihood function involves the sum: $\sum_{i=1}^n (x_i - \mu)^\prime \Sigma^{-1} (x_i - \mu)$.
- Since a scalar equals its trace, apply the cyclic property $tr(AB) = tr(BA)$: $\sum_{i=1}^n tr((x_i - \mu)^\prime \Sigma^{-1} (x_i - \mu)) = \sum_{i=1}^n tr(\Sigma^{-1} (x_i - \mu)(x_i - \mu)^\prime)$.
- Move the summation inside the trace: $tr(\Sigma^{-1} \sum_{i=1}^n (x_i - \mu)(x_i - \mu)^\prime)$.
- By expanding $(x_i - \mu) = (x_i - \overline{x}) + (\overline{x} - \mu)$ and cross-multiplying, the cross terms sum to zero. The term becomes $tr(\Sigma^{-1} A) + n(\overline{x} - \mu)^\prime \Sigma^{-1} (\overline{x} - \mu)$.
- Maximizing the likelihood with respect to $\mu$ forces the second term to $0$ (hence $\hat{\mu} = \overline{x}$). Maximizing with respect to $\Sigma$ yields $\hat{\Sigma} = \frac{1}{n}A$.

**Distribution of the Quadratic Form $n(\overline{x}-\mu)^\prime \Sigma^{-1} (\overline{x}-\mu) \sim \chi_p^2$**

- Define a transformed vector $y = \sqrt{n}\Sigma^{-1/2}(\overline{x} - \mu)$.
- Find its distribution: $E(y) = \sqrt{n}\Sigma^{-1/2}(\mu - \mu) = 0$.
- Find its variance: $Var(y) = (\sqrt{n}\Sigma^{-1/2}) Var(\overline{x}) (\sqrt{n}\Sigma^{-1/2})^\prime = n\Sigma^{-1/2}(\frac{1}{n}\Sigma)\Sigma^{-1/2} = I_p$.
- Thus, $y \sim N_p(0, I_p)$, which means its components $y_i$ are iid $N(0,1)$.
- The quadratic form can be written as $y^\prime y = \sum_{i=1}^p y_i^2$, which by definition is the sum of $p$ squared independent standard normals, hence follows $\chi_p^2$.

**Conditional Distribution Independence (The Schur Complement Proof)**

- To prove $x_1 - \Sigma_{12}\Sigma_{22}^{-1}x_2$ is independent of $x_2$, construct a transformation matrix $C = \begin{bmatrix} I_q & -\Sigma_{12}\Sigma_{22}^{-1} \\ 0 & I_{p-q} \end{bmatrix}$.
- Apply $C$ to the joint vector $x$: $Cx = \begin{bmatrix} x_1 - \Sigma_{12}\Sigma_{22}^{-1}x_2 \\ x_2 \end{bmatrix}$.
- Calculate the new covariance matrix $C\Sigma C^\prime = \begin{bmatrix} I_q & -\Sigma_{12}\Sigma_{22}^{-1} \\ 0 & I_{p-q} \end{bmatrix} \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix} \begin{bmatrix} I_q & 0 \\ -\Sigma_{22}^{-1}\Sigma_{21} & I_{p-q} \end{bmatrix}$.
- Matrix multiplication yields $\begin{bmatrix} \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21} & 0 \\ 0 & \Sigma_{22} \end{bmatrix}$.
- Since the off-diagonal block is strictly $0$, the transformed vector $x_1 - \Sigma_{12}\Sigma_{22}^{-1}x_2$ and $x_2$ are uncorrelated. For multivariate normal distributions, zero covariance implies strict independence.

**Cochran's Theorem Application for Sample Variance ($\frac{(n-1)S^2}{\sigma^2} \sim \chi_{n-1}^2$)**

- Write the sum of squared deviations as a quadratic form: $\sum_{i=1}^n (Y_i - \overline{Y})^2 = y^\prime B y$, where $B = I_n - \frac{1_n 1_n^\prime}{n}$.
- Note that $B$ is idempotent ($B^2 = B$) and its trace is $tr(B) = n - 1$.
- Because $B$ is symmetric and idempotent with rank $n-1$, there exists an $(n-1) \times n$ matrix $C$ such that $CC^\prime = I_{n-1}$ and $C^\prime C = B$.
- Define $z = Cy \sim N_{n-1}(0, \sigma^2 I_{n-1})$. Then $z/\sigma \sim N_{n-1}(0, I_{n-1})$.
- The sum of squares becomes $y^\prime B y = y^\prime C^\prime C y = z^\prime z$.
- Therefore, $\frac{(n-1)S^2}{\sigma^2} = \frac{z^\prime z}{\sigma^2} \sim \chi_{n-1}^2$.

<font color="navy">**How to Prove a Matrix is Positive Semidefinite ($A \ge 0$)**</font>
• Method 1 (By Definition): Show that for any non-zero $p \times 1$ vector $x$, the quadratic form yields $x^\prime A x \ge 0$.<br>
• Method 2 (By Eigenvalues): Calculate all eigenvalues $\lambda_i$ of the matrix $A$. If $\lambda_i \ge 0$ for all $i = 1, ..., p$, then $A \ge 0$.<br>
• Method 3 (By Matrix Factorization / Gram Structure): Show that the matrix $A$ can be expressed in the form $B^\prime B$ (where $B$ is any matrix).<br>
&nbsp;&nbsp;&nbsp;&nbsp;• Proof: Let $y = Bx$.<br>
&nbsp;&nbsp;&nbsp;&nbsp;• Then evaluate the quadratic form: $x^\prime A x = x^\prime (B^\prime B) x = (Bx)^\prime (Bx) = y^\prime y$.<br>
&nbsp;&nbsp;&nbsp;&nbsp;• Since $y^\prime y = \sum_{i=1}^k y_i^2$ is strictly a sum of squared real numbers, it guarantees that $y^\prime y \ge 0$. Thus, $A \ge 0$.<br>
&nbsp;&nbsp;&nbsp;&nbsp;• <font color="red">**Note**</font>: This Method 3 is the standard procedure used to prove that the SSCP matrix $A = (X - 1_n \overline{x}^\prime)^\prime (X - 1_n \overline{x}^\prime)$ and the sample covariance matrix $S = \frac{1}{n-1} A$ are symmetric positive semidefinite.

------

<font color="navy">**Exercise**</font>

 (Spectral Decomposition)
• 题目: 已知 $A = \begin{bmatrix} 1 & 1 \\ 2 & -2 \\ 2 & 2 \end{bmatrix}$，求 $A^\prime A$ 的谱分解。
$A^\prime A = \begin{bmatrix} 1 & 2 & 2 \\ 1 & -2 & 2 \end{bmatrix} \begin{bmatrix} 1 & 1 \\ 2 & -2 \\ 2 & 2 \end{bmatrix} = \begin{bmatrix} 9 & 1 \\ 1 & 9 \end{bmatrix}$.    解 $|A^\prime A - \lambda I_2| = 0 \implies (9-\lambda)^2 - 1 = 0 \implies \lambda_1 = 8, \lambda_2 = 10$.
&nbsp;&nbsp;&nbsp;&nbsp;• 对于 $\lambda_1 = 8$, 解 $(A^\prime A - 8I)x = 0$, 单位化得 $h_1 = \begin{bmatrix} \frac{1}{\sqrt{2}} \\ -\frac{1}{\sqrt{2}} \end{bmatrix}$. $x_1+x_2 = 0, x_1=1,x_2=-1$然后再标准化
&nbsp;&nbsp;&nbsp;&nbsp;• 对于 $\lambda_2 = 10$, 解 $(A^\prime A - 10I)x = 0$, 单位化得 $h_2 = \begin{bmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{bmatrix}$.
&nbsp;&nbsp;&nbsp;&nbsp;• $A^\prime A = \begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \\ -\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{bmatrix} \begin{bmatrix} 8 & 0 \\ 0 & 10 \end{bmatrix} \begin{bmatrix} \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{bmatrix}$.

<font color="navy">**Multivariate Normal Distribution & Properties**</font> 

• **MVN Density**: For $X \sim N_p(\mu, \Sigma)$, the joint density function is $f(x) = \frac{1}{(2\pi)^{p/2}|\Sigma|^{1/2}} \exp\{-\frac{1}{2}(x - \mu)^\prime \Sigma^{-1} (x - \mu)\}$. 

• **Linear Transformation**: If $A$ is a constant $q \times p$ matrix and $d$ is a constant $q \times 1$ vector, then $AX + d \sim N_q(A\mu + d, A\Sigma A^\prime)$.   • <font color="red">**Note (Dimensions)**</font>: The output vector $AX+d$ has dimension $q \times 1$, and its new covariance matrix $A\Sigma A^\prime$ has dimension $q \times q$

• **Marginal Distributions**: All subsets of $X$ strictly follow a normal distribution. If $X = [X_1^\prime, X_2^\prime]^\prime \sim N(\begin{bmatrix} \mu_1 \\ \mu_2 \end{bmatrix}, \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix})$, then the marginal distribution for each subset is $X_i \sim N_{p_i}(\mu_i, \Sigma_{ii})$ for $i=1, 2$.

<font color="navy">**Linear Transformation of MVN Vector**</font>
• Problem: Given $X \sim N_3(\mu, \Sigma)$ with $\mu = \begin{bmatrix} 2 \\ 3 \\ 1 \end{bmatrix}$ and $\Sigma = \begin{bmatrix} 1 & 1 & 1 \\ 1 & 3 & 2 \\ 1 & 2 & 2 \end{bmatrix}$, find the distribution of $X_1 + X_2 - 2X_3$.
Express the linear combination as $AX + d$. Here, the coefficient vector is $A = \begin{bmatrix} 1 & 1 & -2 \end{bmatrix}$ and $d = 0$.
For a multivariate normal vector, $AX \sim N(A\mu, A\Sigma A^\prime)$.

Calculate New Mean ($A\mu$): $A\mu = \begin{bmatrix} 1 & 1 & -2 \end{bmatrix} \begin{bmatrix} 2 \\ 3 \\ 1 \end{bmatrix} = 2 + 3 - 2 = 3$.
Calculate New Variance ($A\Sigma A^\prime$): $A\Sigma A^\prime = \begin{bmatrix} 1 & 1 & -2 \end{bmatrix} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 3 & 2 \\ 1 & 2 & 2 \end{bmatrix} \begin{bmatrix} 1 \\ 1 \\ -2 \end{bmatrix} = 2$.

The transformed variable reduces to a univariate normal distribution, $X_1 + X_2 - 2X_3 \sim N(3, 2)$.

<font color="navy">**Proofs for Conditional Covariance & Positive Definiteness**</font>

• **(a) Prove $\Sigma_{11\bullet 2}$ is Positive Definite**: Given the full covariance matrix $\Sigma > 0$, construct a block matrix $B = \begin{bmatrix} I \\ -\Sigma_{22}^{-1}\Sigma_{21} \end{bmatrix}$.

  • Multiply to find $B^\prime \Sigma B$: $\begin{bmatrix} I & -\Sigma_{12}\Sigma_{22}^{-1} \end{bmatrix} \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix} \begin{bmatrix} I \\ -\Sigma_{22}^{-1}\Sigma_{21} \end{bmatrix} = \begin{bmatrix} I & -\Sigma_{12}\Sigma_{22}^{-1} \end{bmatrix} \begin{bmatrix} \Sigma_{11\bullet 2} \\ O \end{bmatrix} = \Sigma_{11\bullet 2}$.

  • Positive Definite Proof: For any non-zero vector $x$, since $B$ has full column rank, the vector $y = Bx \ne 0$. The quadratic form $x^\prime \Sigma_{11\bullet 2} x = x^\prime (B^\prime \Sigma B) x = (Bx)^\prime \Sigma (Bx) = y^\prime \Sigma y$. Since $\Sigma > 0$, we perfectly know $y^\prime \Sigma y > 0$, hence $\Sigma_{11\bullet 2} > 0$.

• **(b) Prove Block Diagonal Matrix $C\Sigma C^\prime$ is Positive Definite**: Given $C = \begin{bmatrix} I & -\Sigma_{12}\Sigma_{22}^{-1} \\ O & I \end{bmatrix}$.

  • Calculate $C\Sigma C^\prime$: First, $C\Sigma = \begin{bmatrix} \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21} & O \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix} = \begin{bmatrix} \Sigma_{11\bullet 2} & O \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$. 

Then, $(C\Sigma)C^\prime = \begin{bmatrix} \Sigma_{11\bullet 2} & O \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix} \begin{bmatrix} I & O \\ -\Sigma_{22}^{-1}\Sigma_{21} & I \end{bmatrix} = \begin{bmatrix} \Sigma_{11\bullet 2} & O \\ O & \Sigma_{22} \end{bmatrix}$.

  • Positive Definite Proof: For any non-zero vector $y$, we evaluate $y^\prime (C\Sigma C^\prime) y$. Since $C$ is a non-singular square matrix (its determinant $|C| = 1$), the vector $x = C^\prime y$ must be non-zero ($x \ne 0$). Therefore, $y^\prime (C\Sigma C^\prime) y = (C^\prime y)^\prime \Sigma (C^\prime y) = x^\prime \Sigma x$. Since $\Sigma > 0$, $x^\prime \Sigma x > 0$, strictly proving $C\Sigma C^\prime > 0$.

<font color="navy">**Conditional Distribution via Transformation**</font>

• **Problem**: Given $Y \sim N(\mu, \Sigma)$, find $Y_2 | (Y_1 - Y_3 = z)$.where:   $\mu = [1, 2, 0]^\prime$, $\Sigma = \begin{bmatrix} 2 & 1 & 0 \\ 1 & 2 & 1 \\ 0 & 1 & 3 \end{bmatrix}$.

<font color="navy">1.</font> **Define Transformation**: We need the joint distribution of $Y_2$ and $Z = Y_1 - Y_3$. Let $X = \begin{bmatrix} Y_2 \\ Y_1 - Y_3 \end{bmatrix} = AY$, where $A = \begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & -1 \end{bmatrix}$.

<font color="navy">2.</font> **Calculate Mean $A\mu$**: $A\mu = \begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & -1 \end{bmatrix} \begin{bmatrix} 1 \\ 2 \\ 0 \end{bmatrix} = \begin{bmatrix} 2 \\ 1 \end{bmatrix} = \begin{bmatrix} \mu_{Y_2} \\ \mu_Z \end{bmatrix}$.

<font color="navy">3.</font> **Calculate Covariance $A\Sigma A^\prime$**:

  • $A\Sigma = \begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & -1 \end{bmatrix} \begin{bmatrix} 2 & 1 & 0 \\ 1 & 2 & 1 \\ 0 & 1 & 3 \end{bmatrix} = \begin{bmatrix} 1 & 2 & 1 \\ 2 & 0 & -3 \end{bmatrix}$.

  • $A\Sigma A^\prime = \begin{bmatrix} 1 & 2 & 1 \\ 2 & 0 & -3 \end{bmatrix} \begin{bmatrix} 0 & 1 \\ 1 & 0 \\ 0 & -1 \end{bmatrix} = \begin{bmatrix} 2 & 0 \\ 0 & 5 \end{bmatrix} = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$.

<font color="navy">4.</font> **Find Conditional Distribution**: Since $\Sigma_{12} = 0$, $Y_2$ and $Z$ are **independent**.

  • Result: $Y_2 | Z=z \sim N(\mu_{Y_2}, \Sigma_{11}) = N(2, 2)$.

------

<font color="navy">**Joint and Conditional Distribution**</font> 

**Problem**: Find (a) Joint distribution of $W = [Y_1-2Y_2, Y_1-3Y_3]^\prime$ and (b) $(Y_1-2Y_2) | Y_3=y_3$. $\mu = [2\beta, \beta, \beta]^\prime$, $\Sigma = \begin{bmatrix} 1 & 0 & \rho \\ 0 & 1 & \rho \\ \rho & \rho & 1 \end{bmatrix}$, with $-1 < \rho < 1$.

<font color="navy">**(a) Joint Distribution of $W$**</font>

<font color="navy">1.</font> **Linear Transformation**: $W = AY$ where $A = \begin{bmatrix} 1 & -2 & 0 \\ 1 & 0 & -3 \end{bmatrix}$.

<font color="navy">2.</font> **Mean $A\mu$**: $\begin{bmatrix} 1 & -2 & 0 \\ 1 & 0 & -3 \end{bmatrix} \begin{bmatrix} 2\beta \\ \beta \\ \beta \end{bmatrix} = \begin{bmatrix} 2\beta-2\beta \\ 2\beta-3\beta \end{bmatrix} = \begin{bmatrix} 0 \\ -\beta \end{bmatrix}$.

<font color="navy">3.</font> **Covariance $A\Sigma A^\prime$**:

  • $A\Sigma = \begin{bmatrix} 1 & -2 & 0 \\ 1 & 0 & -3 \end{bmatrix} \begin{bmatrix} 1 & 0 & \rho \\ 0 & 1 & \rho \\ \rho & \rho & 1 \end{bmatrix} = \begin{bmatrix} 1 & -2 & -\rho \\ 1-3\rho & -3\rho & \rho-3 \end{bmatrix}$.

  • $A\Sigma A^\prime = \begin{bmatrix} 1 & -2 & -\rho \\ 1-3\rho & -3\rho & \rho-3 \end{bmatrix} \begin{bmatrix} 1 & 1 \\ -2 & 0 \\ 0 & -3 \end{bmatrix} = \begin{bmatrix} 5 & 1+3\rho \\ 1+3\rho & 10-6\rho \end{bmatrix}$.

<font color="navy">4.</font> **Result**: $W \sim N_2 \left( \begin{bmatrix} 0 \\ -\beta \end{bmatrix}, \begin{bmatrix} 5 & 1+3\rho \\ 1+3\rho & 10-6\rho \end{bmatrix} \right)$.

<font color="navy">**(b) Conditional Distribution $(Y_1-2Y_2) | Y_3=y_3$**</font>

<font color="navy">1.</font> **New Transformation**: Let $X = \begin{bmatrix} Y_1-2Y_2 \\ Y_3 \end{bmatrix} = \begin{bmatrix} 1 & -2 & 0 \\ 0 & 0 & 1 \end{bmatrix} Y$.

<font color="navy">2.</font> **Joint Parameters**:

  • Mean: $A\mu = \begin{bmatrix} 1 & -2 & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} 2\beta \\ \beta \\ \beta \end{bmatrix} = \begin{bmatrix} 0 \\ \beta \end{bmatrix} = \begin{bmatrix} \mu_1 \\ \mu_2 \end{bmatrix}$.

  • Covariance: $A\Sigma A^\prime = \begin{bmatrix} 1 & -2 & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 & \rho \\ 0 & 1 & \rho \\ \rho & \rho & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 \\ -2 & 0 \\ 0 & 1 \end{bmatrix} = \begin{bmatrix} 5 & -\rho \\ -\rho & 1 \end{bmatrix} = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$.

<font color="navy">3.</font> **Apply Conditional Formula**:

  • $\mu_{1|2} = \mu_1 + \Sigma_{12}\Sigma_{22}^{-1}(y_3 - \mu_2) = 0 + (-\rho)(1)^{-1}(y_3 - \beta) = -\rho(y_3 - \beta)$.

  • $\Sigma_{11|2} = \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21} = 5 - (-\rho)(1)^{-1}(-\rho) = 5 - \rho^2$.

<font color="navy">4.</font> **Result**: $(Y_1-2Y_2) | Y_3=y_3 \sim N(-\rho(y_3 - \beta), 5 - \rho^2)$.



<font color="navy">**Ch3 Inferences on the Mean Vector**</font>

**Notation (Hypothesis Testing)**

• $S$: Sample covariance matrix, specifically with denominator $n-1$, defined as $S = \frac{1}{n-1}\sum_{j=1}^n(x_j-\overline{x})(x_j-\overline{x})^\prime$.

• $d_j$: The difference vector for the $j$-th pair in a paired comparison, defined as $x_{1j} - x_{2j}$.

• $\overline{d}$: Sample mean vector of the differences, defined as $\overline{d} = \frac{1}{n}\sum_{j=1}^n d_j$.

• $S_d$: Sample covariance matrix of the differences, defined as $S_d = \frac{1}{n-1}\sum_{j=1}^n (d_j - \overline{d})(d_j - \overline{d})^\prime$.

• $S_p$: Pooled sample covariance matrix for two independent samples, defined as $S_p = \frac{(n_1-1)S_1 + (n_2-1)S_2}{n_1+n_2-2}$.

• $C$: A $q \times p$ contrast matrix of constants used for testing linear combinations.

• $1_p$: A $p \times 1$ vector of ones.

**5. Profile Analysis (Two-Sample Extension)**

Divides the testing procedure into three sequential stages for two independent groups ($n = n_1 + n_2$).

• Stage a: Parallel Profiles 平行性

• Hypothesis: $H_0^{(1)}: C\mu_1 = C\mu_2$ (where $C$ is the $(p-1) \times p$ difference matrix).

• Test Statistic: $T^2 = \frac{n_1 n_2}{n_1+n_2} (\overline{x}_1 - \overline{x}_2)^\prime C^\prime (CS_pC^\prime)^{-1} C(\overline{x}_1 - \overline{x}_2)$.

• Decision Rule: Reject $H_0^{(1)}$ if $\frac{n-p}{p-1} \cdot \frac{T^2}{n-2} > F_{p-1, n-p}(\alpha)$.

• Stage b: Coincident Profiles (Requires Stage a to NOT be rejected) 重合性 

• Hypothesis: $H_0^{(2)}: 1_p^\prime \mu_1 = 1_p^\prime \mu_2$. Tests if the two parallel lines are at the exact same height.
  • Test Statistic ($T^2$ form): $T^2 = \frac{n_1 n_2}{n_1+n_2} (\overline{x}_1 - \overline{x}_2)^\prime 1_p (1_p^\prime S_p 1_p)^{-1} 1_p^\prime (\overline{x}_1 - \overline{x}_2)$. Under $H_0^{(2)}$, $T^2 \sim F_{1, n-2}$.
  • Test Statistic ($t$ form): $t_{stat} = \frac{1_p^\prime (\overline{x}_1 - \overline{x}_2)}{\sqrt{(\frac{1}{n_1} + \frac{1}{n_2})(1_p^\prime S_p 1_p)}}$. Under $H_0^{(2)}$, $t_{stat} \sim t_{n-2}$.
  • Decision Rule: Reject $H_0^{(2)}$ if $T^2 > F_{1, n-2}(\alpha)$, or equivalently, if $|t_{stat}| > t_{n-2}(\frac{\alpha}{2})$.

• Stage c: Level Profiles (Requires Stage b to NOT be rejected) 水平性

• Hypothesis: $H_0^{(3)}: C\mu = 0$ (all means equal to the same constant). We estimate the common mean vector using the pooled overall sample mean $\overline{x} = \frac{n_1\overline{x}_1 + n_2\overline{x}_2}{n_1+n_2}$.

• Test Statistic: $T^2 = n\overline{x}^\prime C^\prime (CS_pC^\prime)^{-1} C\overline{x}$.

• Decision Rule: Reject $H_0^{(3)}$ if $\frac{n-p}{p-1} \cdot \frac{T^2}{n-2} > F_{p-1, n-p}(\alpha)$.

**6. Confidence Regions & Intervals**

• **Confidence Region:** The $p$-dimensional $100(1-\alpha)\%$ confidence region for $\mu$ is an ellipsoid consisting of all $\mu$ satisfying:

$(\overline{x} - \mu)^\prime S^{-1} (\overline{x} - \mu) \le \frac{p(n-1)F_{p,n-p}(\alpha)}{n(n-p)}$.

• Note: Geometrically, this forms an ellipsoid centered at $\overline{x}$. Its axes lengths and directions are determined by the eigenvalues and eigenvectors of $S$.

<font color="navy">**Notation (Bivariate Confidence Region)**</font>
• $\lambda_1, \lambda_2$: Eigenvalues of the sample covariance matrix $S$ (assuming $\lambda_1 > \lambda_2$).
• $v_1, v_2$: Normalized eigenvectors corresponding to $\lambda_1$ and $\lambda_2$.
• $a, b, c$: Elements of the inverse sample covariance matrix, $S^{-1} = \begin{bmatrix} a & b \\ b & c \end{bmatrix}$.

<font color="navy">**Bivariate ($p=2$) Confidence Ellipse**</font>
• <font color="black">**Quadratic Form Expansion:**</font> The $100(1-\alpha)\%$ confidence region for $\mu = (\mu_1, \mu_2)^\prime$ consists of all values satisfying:
  $a(\overline{x}_1 - \mu_1)^2 + 2b(\overline{x}_1 - \mu_1)(\overline{x}_2 - \mu_2) + c(\overline{x}_2 - \mu_2)^2 \le \frac{2(n-1)F_{2,n-2}(\alpha)}{n(n-2)}$
• <font color="black">**Geometric Properties of the Ellipse:**</font>
  • <font color="navy">Center:</font> $(\overline{x}_1, \overline{x}_2)$.
  • <font color="navy">Major Axis:</font> Lies along the direction of eigenvector $v_1$. The total length of the major axis is $2\sqrt{\frac{2(n-1)F_{2,n-2}(\alpha)\lambda_1}{n(n-2)}}$.
  • <font color="navy">Minor Axis:</font> Lies along the direction of eigenvector $v_2$ (perpendicular to the major axis). The total length of the minor axis is $2\sqrt{\frac{2(n-1)F_{2,n-2}(\alpha)\lambda_2}{n(n-2)}}$.
• <font color="black">**Equivalence to Hypothesis Testing:**</font>
  To test $H_0: \mu = (\mu_{01}, \mu_{02})^\prime$ at significance level $\alpha$, simply substitute $\mu_{01}$ and $\mu_{02}$ into the quadratic form expansion above. If the computed numerical value is $\le$ the right-hand side critical value, the point lies inside the confidence ellipse, and we do not reject $H_0$.

• **Simultaneous Confidence Intervals:** Guarantees the joint probability that all $p$ intervals are simultaneously true is at least $1-\alpha$. For individual component $\mu_i$:

$\overline{x}_i \pm \sqrt{\frac{p(n-1)F_{p,n-p}(\alpha)}{n-p}} \cdot \sqrt{\frac{s_{ii}}{n}}$.

• **Bonferroni Method:** Often gives shorter, more precise intervals than the simultaneous method by distributing the alpha risk. For individual component $\mu_i$:

$\overline{x}_i \pm t_{n-1}(1 - \frac{\alpha}{2p}) \cdot \sqrt{\frac{s_{ii}}{n}}$.

**7. Test for Equality of Covariance Matrices (Box's M Test)**

• Hypothesis: $H_0: \Sigma_1 = \Sigma_2$ versus $H_1: \Sigma_1 \ne \Sigma_2$.

• Test Statistic: $M = (n-2)\ln|S_p| - (n_1-1)\ln|S_1| - (n_2-1)\ln|S_2|$.

• Approximation: $(1-u)M \sim \chi_{p(p+1)/2}^2$ approximately, where the scaling factor is $u = (\frac{1}{n_1-1} + \frac{1}{n_2-1} - \frac{1}{n-2}) \cdot [\frac{2p^2+3p-1}{6(p+1)}]$.

• Note: This acts as a preliminary assumption check for the two-sample $T^2$ test.

**8. Transformations to Near Normality**
• <font color="black">**Counts**</font> ($y$): Transformed to $\sqrt{y}$.
• <font color="black">**Proportions**</font> ($\hat{p}$): Transformed using the logit function, defined as $\frac{1}{2}\log(\frac{\hat{p}}{1-\hat{p}})$.
• <font color="black">**Correlations**</font> ($r$): Transformed using Fisher's $z$-transformation, defined as $z_r = \frac{1}{2}\log(\frac{1+r}{1-r})$.

• Box and Cox Transformation: Used to make non-normal univariate data more "normal looking". Given by:

$x^{(\lambda)} = \frac{x^\lambda - 1}{\lambda}$ for $\lambda \ne 0$.

$x^{(\lambda)} = \ln(x)$ for $\lambda = 0$.

• Note: For a multivariate observation, a distinct power transformation $\lambda_k$ must be selected for each of the $p$ variables by maximizing their individual log-likelihood functions.

<font color="navy">**Notation (Box and Cox Transformation)**</font>
• $\lambda$: Power transformation parameter.
• $x^{(\lambda)}$: The transformed observation.
• $l(\lambda)$: The profile log-likelihood function to be maximized.
• $x_{jk}$: The $j$-th observation on the $k$-th variable in a multivariate dataset ($k = 1, 2, ..., p$).
• $\lambda_k$: The power transformation parameter specific to the $k$-th variable.
• $\hat{\lambda}_k$: The optimal value that maximizes $l(\lambda_k)$ for the $k$-th variable.

<font color="navy">**8. Box and Cox Transformation**</font>
• <font color="black">**Univariate Transformation Formula:**</font>
  $x^{(\lambda)} = \frac{x^\lambda - 1}{\lambda}$ for $\lambda \ne 0$, and $x^{(\lambda)} = \ln(x)$ for $\lambda = 0$.
• <font color="black">**Finding the Optimal $\lambda$ (Univariate):**</font>
  Given observations $x_1, ..., x_n$, the appropriate power $\lambda$ is the solution that maximizes the log-likelihood expression:
  $$l(\lambda) = -\frac{n}{2}\ln\left[\frac{1}{n}\sum_{j=1}^n(x_j^{(\lambda)} - \overline{x^{(\lambda)}})^2\right] + (\lambda - 1)\sum_{j=1}^n \ln(x_j)$$
  where the sample mean of the transformed data is $\overline{x^{(\lambda)}} = \frac{1}{n}\sum_{j=1}^n \left(\frac{x_j^\lambda - 1}{\lambda}\right)$.
With multivariate observations, a distinct power transformation must be selected for each of the $p$ variables independently.
• <font color="black">**Finding the Optimal $\lambda_k$:**</font>
  Each $\lambda_k$ is selected by maximizing its own log-likelihood function:
  $$l(\lambda_k) = -\frac{n}{2}\ln\left[\frac{1}{n}\sum_{j=1}^n(x_{jk}^{(\lambda_k)} - \overline{x_k^{(\lambda_k)}})^2\right] + (\lambda_k - 1)\sum_{j=1}^n \ln(x_{jk})$$
  where $\overline{x_k^{(\lambda_k)}} = \frac{1}{n}\sum_{j=1}^n \left(\frac{x_{jk}^{\lambda_k} - 1}{\lambda_k}\right)$.
• <font color="black">**Constructing the Transformed Vector:**</font>
  Let $\hat{\lambda}_1, \hat{\lambda}_2, ..., \hat{\lambda}_p$ be the values that individually maximize the equation above for each variable. Then the $j$-th transformed multivariate observation vector becomes:
  $$x_j^{(\hat{\lambda})} = \left[ \frac{x_{j1}^{\hat{\lambda}_1} - 1}{\hat{\lambda}_1}, \frac{x_{j2}^{\hat{\lambda}_2} - 1}{\hat{\lambda}_2}, \cdots, \frac{x_{jp}^{\hat{\lambda}_p} - 1}{\hat{\lambda}_p} \right]^\prime$$

<font color="navy">**Ch5 Principal Component Analysis (PCA)**</font>

<font color="navy">**Notation (Principal Component Analysis)**</font>
• $x$: $p \times 1$ random vector of original variables $(X_1, ..., X_p)^\prime$.
• $\Sigma$: Population covariance matrix of $x$.
• $S$: Sample covariance matrix, defined as $S = \frac{1}{n-1}\sum_{j=1}^n(x_j-\overline{x})(x_j-\overline{x})^\prime$.
• $\lambda_1 \ge \lambda_2 \ge ... \ge \lambda_p \ge 0$: Ordered eigenvalues of $\Sigma$ (or $S$ for sample calculations).
• $\Lambda$: Diagonal matrix of eigenvalues, $\Lambda = diag(\lambda_1, ..., \lambda_p)$.
• $v_i$: Normalized eigenvector corresponding to $\lambda_i$.
• $Y_i$: The $i$-th principal component (PC).
• $v_{ik}$: The $k$-th element of the $i$-th eigenvector $v_i$.
• $\sigma_{kk}$: Variance of the original variable $X_k$.

<font color="navy">**1. Unsupervised Learning & PCA Basics**</font>
• <font color="black">**Unsupervised Learning:**</font> Only the feature matrix $X$ is available (no labels $Y$). Used for dimension reduction, image compression, noise reduction, and exploratory data analysis.
• <font color="black">**PCA Objective:**</font> Represents a dataset using fewer variables with negligible loss of information via linear combinations of the original variables. Formulated via Maximum Variance or Minimum Reconstruction Error.
• <font color="black">**Computation:**</font> Solved via Spectral Decomposition or Singular-Value Decomposition (SVD).

<font color="navy">**2. Maximum Variance Formulation**</font>
• <font color="black">**First PC ($Y_1$):**</font> Linear combination $Y_1 = v_1^\prime x$. We maximize $Var(Y_1) = v_1^\prime \Sigma v_1$ subject to the constraint $v_1^\prime v_1 = 1$. The maximum variance is $\lambda_1$, and the loadings are $v_1$.
• <font color="black">**Second PC ($Y_2$):**</font> Linear combination $Y_2 = v_2^\prime x$. We maximize $Var(Y_2) = v_2^\prime \Sigma v_2$ subject to $v_2^\prime v_2 = 1$ and the orthogonality constraint $v_1^\prime v_2 = 0$ ($v_1 \perp v_2$). The maximum variance is $\lambda_2$, and the loadings are $v_2$.

<font color="navy">**3. Properties of Principal Components**</font>

<font color="navy">**Notation (PCA Spectral Decomposition & Proofs)**</font><br>
• $B, \Sigma$: A $p \times p$ positive semidefinite covariance matrix.<br>
• $\lambda_1 \ge \lambda_2 \ge ... \ge \lambda_p \ge 0$: Ordered eigenvalues of the matrix.<br>
• $v_1, ..., v_p$: Normalized eigenvectors corresponding to the eigenvalues.<br>
• $P$: Orthogonal matrix composed of eigenvectors, defined as $P = [v_1, ..., v_p]$, where $P^\prime P = I$.<br>
• $\Lambda$: Diagonal matrix of eigenvalues, defined as $\Lambda = diag(\lambda_1, ..., \lambda_p)$.<br>
• $l$: Any non-zero $p \times 1$ vector representing linear combination weights.<br>
• $u$: A transformed vector defined as $u = P^\prime l$.<br>
• $e_i$: A $p \times 1$ indicator vector of $0$s except that the $i$-th element is $1$.

<font color="navy">**Lemma 1: Rayleigh Quotient Maximization**</font><br>
Suppose the $p \times p$ positive semidefinite matrix $B$ has ordered eigenvalues $\lambda_1 \ge ... \ge \lambda_p \ge 0$ and corresponding normalized eigenvectors $v_1, ..., v_p$. Then:<br>
• <font color="navy">i)</font> $\max_{l \ne 0} \frac{l^\prime B l}{l^\prime l} = \lambda_1$, and the maximum is attained at $l = v_1$.<br>
• <font color="navy">ii)</font> $\min_{l \ne 0} \frac{l^\prime B l}{l^\prime l} = \lambda_p$, and the minimum is attained at $l = v_p$.<br>
• <font color="navy">iii)</font> $\max_{l \perp v_1, ..., v_k} \frac{l^\prime B l}{l^\prime l} = \lambda_{k+1}$, and the maximum is attained at $l = v_{k+1}$ for $k = 1, 2, ..., p-1$.

<font color="navy">**Proof of Lemma 1 (Maximization)**</font><br>
• Let $B = P \Lambda P^\prime$ be the spectral decomposition of $B$. Let $u = P^\prime l$.<br>
• The objective function becomes: $\frac{l^\prime B l}{l^\prime l} = \frac{l^\prime P \Lambda P^\prime l}{l^\prime P P^\prime l} = \frac{u^\prime \Lambda u}{u^\prime u}$.<br>
• Expanding into summations: $\frac{u^\prime \Lambda u}{u^\prime u} = \frac{\sum_{i=1}^p \lambda_i u_i^2}{\sum_{i=1}^p u_i^2}$.<br>
• Since $\lambda_1$ is the largest eigenvalue, $\frac{\sum_{i=1}^p \lambda_i u_i^2}{\sum_{i=1}^p u_i^2} \le \lambda_1 \frac{\sum_{i=1}^p u_i^2}{\sum_{i=1}^p u_i^2} = \lambda_1$.<br>
• When $l = v_1$, $P^\prime v_1 = (1, 0, ..., 0)^\prime$, which yields exactly $\lambda_1$.<br>
• Note: For part (iii), the constraint $l \perp v_1, ..., v_k$ implies $v_i^\prime l = 0$ for $i \le k$. Thus $u_i = 0$ for $i \le k$, meaning the summation starts from $k+1$, shifting the upper bound to $\lambda_{k+1}$.

<font color="navy">**Proof: Uncorrelated PCs and Variance**</font><br>
Using the spectral decomposition $\Sigma = P \Lambda P^\prime$, all PCs are strictly uncorrelated and their variance equals their respective eigenvalue.<br>
• <font color="black">**Zero Covariance:**</font> $Cov(Y_i, Y_j) = Cov(v_i^\prime x, v_j^\prime x) = v_i^\prime \Sigma v_j = v_i^\prime P \Lambda P^\prime v_j = e_i^\prime \Lambda e_j = 0$ (for $i \ne j$).<br>
• <font color="black">**PC Variance:**</font> $Var(Y_i) = v_i^\prime \Sigma v_i = v_i^\prime P \Lambda P^\prime v_i = e_i^\prime \Lambda e_i = \lambda_i$.

<font color="navy">**Proposition 2: Total Variation Conservation**</font><br>
The total variation of the original variables $X_1, ..., X_p$ is exactly equal to the total variation of the transformed PC variables $Y_1, ..., Y_p$.<br>
• Equation: $\sum_{i=1}^p Var(X_i) = \sum_{i=1}^p Var(Y_i)$.

<font color="navy">**Proof of Proposition 2 (The Trace Trick)**</font><br>
• The sum of variances of the original variables is the trace of the covariance matrix: $\sum_{i=1}^p Var(X_i) = tr(\Sigma)$.<br>
• Substitute the spectral decomposition: $tr(\Sigma) = tr(P \Lambda P^\prime)$.<br>
• Apply the cyclic property of the trace operation $tr(AB) = tr(BA)$: $tr(P \Lambda P^\prime) = tr(\Lambda P^\prime P)$.<br>
• Since $P$ is orthogonal ($P^\prime P = I$), we have $tr(\Lambda P^\prime P) = tr(\Lambda)$.<br>
• Since $\Lambda$ is a diagonal matrix containing all eigenvalues, $tr(\Lambda) = \sum_{i=1}^p \lambda_i = \sum_{i=1}^p Var(Y_i)$.

• <font color="black">**Uncorrelated PCs:**</font> $Cov(Y_i, Y_j) = 0$ for $i \ne j$.
• <font color="black">**Variance:**</font> $Var(Y_i) = \lambda_i$.
• <font color="black">**Total Variation:**</font> The total variation of the original variables equals the total variation of the PCs: $\sum_{i=1}^p Var(X_i) = \sum_{i=1}^p Var(Y_i) = tr(\Sigma) = \sum_{i=1}^p \lambda_i$.
• <font color="black">**Proportion of Variance Explained:**</font> The importance of $Y_i$ is $\frac{\lambda_i}{\sum_{j=1}^p \lambda_j}$. Retaining $k$ PCs explains $\frac{\sum_{j=1}^k \lambda_j}{\sum_{j=1}^p \lambda_j}$ of the total variance.<br>
• <font color="black">**Covariance between $X$ and $Y$:**</font> $Cov(X_k, Y_i) = v_{ik}\lambda_i$.
• <font color="black">**Correlation between $X$ and $Y$:**</font> $Corr(X_k, Y_i) = \frac{v_{ik}\sqrt{\lambda_i}}{\sqrt{\sigma_{kk}}}$.

<font color="navy">**4. Large Sample Properties & Inference**</font>
Assume $x_1, ..., x_n \sim N_p(\mu, \Sigma)$ with distinct positive eigenvalues.
• <font color="black">**Eigenvalue Distribution:**</font> $\sqrt{n}(\hat{\lambda} - \lambda) \sim N_p(0, 2\Lambda^2)$ asymptotically. Thus, $\hat{\lambda}_i$ is approximately $N(\lambda_i, \frac{2\lambda_i^2}{n})$.
• <font color="black">**Eigenvector Distribution:**</font> $\sqrt{n}(\hat{v}_i - v_i) \sim N_p(0, A_i)$ where $A_i = \lambda_i \sum_{k \ne i} \frac{\lambda_k}{(\lambda_k - \lambda_i)^2} v_k v_k^\prime$.
• <font color="black">**Independence:**</font> Each $\hat{\lambda}_i$ is distributed independently of the elements of its associated $\hat{v}_i$.
• <font color="black">**Confidence Interval for $\lambda_i$:**</font> A large sample $100(1-v)\%$ CI is $\frac{\hat{\lambda}_i}{1+z_{v/2}\sqrt{\frac{2}{n}}} \le \lambda_i \le \frac{\hat{\lambda}_i}{1-z_{v/2}\sqrt{\frac{2}{n}}}$.

<font color="navy">**5. Practical Considerations & Extensions**</font>
• <font color="black">**Standardization:**</font> If units of measurement are artificial or vastly different, standardize variables before PCA by using the Correlation Matrix where $tr(R) = p$. If units carry physical meaning or information (e.g., gene expression), do NOT standardize to unit variance. $Z_i = \frac{X_i - \mu_i}{\sigma_i}$ for $i = 1, ..., p$.
• <font color="black">**Scree Plot:**</font> A line plot of the variances (eigenvalues) against the order of the PC. Used to visually determine the suitable number of PCs to retain.
• <font color="black">**Loadings Interpretation:**</font> Loadings $v_i$ are unique only up to a sign change. They represent the relative importance of original variables in forming the PC (e.g., contrasting speed vs. power).
• <font color="black">**Extensions:**</font>
  • <font color="navy">a)</font> Probabilistic PCA / Exponential family PCA (for explicitly modeling binary/count data).
  • <font color="navy">b)</font> Nonlinear dimension reduction: Kernel PCA, Variational Autoencoder (VAE, a non-linear method based on neural networks).

<font color="navy">**1. Singular-Value Decomposition (SVD)**</font><br>
• <font color="black">**Definition:**</font> Any $n \times p$ mean-centered matrix $X$ can be decomposed as $X = U\Sigma V^\prime$.<br>
• <font color="black">**Relationship to PCA:**</font><br>
  <font color="navy">i)</font> By expansion, $X^\prime X = V\Sigma^2 V^\prime$. Therefore, the columns of $V$ are the exact eigenvectors of $X^\prime X$, which act as the principal component loadings $v_i$.<br>
  <font color="navy">ii)</font> The singular values $\sigma_i$ are linked to the eigenvalues $\lambda_i$ of the sample covariance matrix $S$ by: $\lambda_i = \frac{\sigma_i^2}{n-1}$.<br>
  <font color="navy">iii)</font> The principal component scores are easily computed without $V$ via $XV = U\Sigma V^\prime V = U\Sigma$.<br>
• <font color="black">**Advantage:**</font> SVD is more numerically stable and computationally efficient than calculating $X^\prime X$ explicitly for spectral decomposition, avoiding rounding errors in ill-conditioned matrices.

<font color="navy">**2. Minimum Reconstruction Error Formulation**</font><br>
• <font color="black">**Objective:**</font> PCA seeks to find a $k$-dimensional subspace such that the squared Euclidean distance between the original data points $x_j$ and their projected approximations $\hat{x}_j$ onto this subspace is minimized.<br>
• <font color="black">**Optimization Problem:**</font> $\min_{V_k} \sum_{j=1}^n ||x_j - V_k V_k^\prime x_j||^2$<br>
  where $V_k$ consists of the first $k$ orthonormal columns of the loadings matrix $V$.<br>
• <font color="black">**Reconstruction Formula:**</font> The best $k$-rank approximation of an original uncentered observation $x_j$ adds the projection back to the sample mean: $\hat{x}_j = \overline{x} + \sum_{i=1}^k (v_i^\prime (x_j - \overline{x})) v_i$<br>
• <font color="black">**Total Minimum Error:**</font> The minimum reconstruction error (residual sum of squares) is exactly equal to the sum of the discarded eigenvalues adjusted by the sample size denominator:  $Error = (n-1) \sum_{i=k+1}^p \lambda_i$<br>
• <font color="black">**Conclusion:**</font> Maximizing the captured variance (which retains the largest $\lambda_i$) is mathematically identical to minimizing the reconstruction error (which discards the smallest $\lambda_i$).

<font color="navy">**Ch6 Partial Correlation Analysis**</font>

<font color="navy">**Notation (Partial Correlation Analysis)**</font><br>
• $X, Y, X_i, X_j$: Univariate random variables.<br>
• $z$: A $q \times 1$ random vector representing the control variables.<br>
• $\rho_{XY}$: Simple population correlation coefficient.<br>
• $r_{XY}$: Simple sample correlation coefficient.<br>
• $\Sigma_{11\bullet z}$: Conditional population covariance matrix of the remaining variables given $z$.<br>
• $S_{11\bullet z}$: Conditional sample covariance matrix given $z$.<br>
• $\sigma_{ij\bullet z}$: The $(i, j)$-th element of $\Sigma_{11\bullet z}$.<br>
• $s_{ij\bullet z}$: The $(i, j)$-th element of $S_{11\bullet z}$.<br>
• $\rho_{ij\bullet z}$: Population partial correlation coefficient between $X_i$ and $X_j$ given $z$.<br>
• $r_{ij\bullet z}$: Sample partial correlation coefficient between $X_i$ and $X_j$ given $z$.

<font color="navy">**1. Simple Correlation Coefficient**</font><br>
• <font color="black">**Sample Estimator:**</font>  $r_{XY} = \frac{\sum_{i=1}^n(x_i-\overline{x})(y_i-\overline{y})}{\sqrt{(\sum_{i=1}^n(x_i-\overline{x})^2)(\sum_{i=1}^n(y_i-\overline{y})^2)}}$<br>
• <font color="black">**Hypothesis Testing:**</font><br>
  To test $H_0: \rho_{XY} = 0$ versus $H_1: \rho_{XY} \ne 0$:   

Test Statistic: $t = \sqrt{n-2} \cdot \frac{r_{XY}}{\sqrt{1-r_{XY}^2}} \sim t_{n-2}$.  Decision Rule: Reject $H_0$ if $|t| > t_{n-2}(\frac{\alpha}{2})$.<br>
• <font color="black">**Limitation:**</font> A large simple correlation does not imply causation, as it may be confounded by a third common variable $z$ affecting both $X$ and $Y$.

<font color="navy">**2. Partial Correlation Coefficient**</font><br>
Used to measure the linear association between $X_i$ and $X_j$ while controlling for the effects of a third party $z$ (a single variable or a group of $q$ variables).<br>
• <font color="black">**Population Conditional Covariance:**</font> Based on the partitioned covariance matrix: $\Sigma_{11\bullet z} = \Sigma_{11} - \Sigma_{1z}\Sigma_{zz}^{-1}\Sigma_{z1}$.<br>
• <font color="black">**Population Partial Correlation:**</font> $\rho_{ij\bullet z} = \frac{\sigma_{ij\bullet z}}{\sqrt{\sigma_{ii\bullet z}}\sqrt{\sigma_{jj\bullet z}}}$.<br>
• <font color="black">**Sample Conditional Covariance:**</font>  $S_{11\bullet z} = S_{11} - S_{1z}S_{zz}^{-1}S_{z1}$.<br>
• <font color="black">**Sample Partial Correlation:**</font> $r_{ij\bullet z} = \frac{s_{ij\bullet z}}{\sqrt{s_{ii\bullet z}}\sqrt{s_{jj\bullet z}}}$.

<font color="navy">**3. Hypothesis Testing for Partial Correlation**</font><br>
To test whether the partial correlation is significantly different from zero, accounting for the $q$ variables being controlled:<br>
• <font color="black">**Hypothesis:**</font> $H_0: \rho_{ij\bullet z} = 0$ versus $H_1: \rho_{ij\bullet z} \ne 0$.<br>
• <font color="black">**Test Statistic:**</font> $t = \sqrt{n-q-2} \cdot \frac{r_{ij\bullet z}}{\sqrt{1-r_{ij\bullet z}^2}} \sim t_{n-q-2}$.<br>
• <font color="black">**Decision Rule:**</font> Reject $H_0$ if $|t| > t_{n-q-2}(\frac{\alpha}{2})$.<br>
  • Note: The degrees of freedom drop by $q$ (the number of variables controlled for) compared to the simple correlation test.

<font color="navy">**4. Special Case ($p=2, q=1$)**</font><br>
When controlling for exactly one variable (e.g., $z = X_3$) to find the partial correlation between $X_1$ and $X_2$, matrix inversion is not required.<br>
• <font color="black">**Population Formula:**</font> $\rho_{12\bullet 3} = \frac{\rho_{12} - \rho_{13}\rho_{23}}{\sqrt{(1-\rho_{13}^2)(1-\rho_{23}^2)}}$.<br>
• <font color="black">**Sample Formula:**</font>  $r_{12\bullet 3} = \frac{r_{12} - r_{13}r_{23}}{\sqrt{(1-r_{13}^2)(1-r_{23}^2)}}$.

• Derivation of the formula for $p=2, q=1$ (Controlling for a single variable $X_3$):
  • Let the correlation matrix of $\begin{bmatrix} X_1 \\ X_2 \\ X_3 \end{bmatrix}$ be $R = \begin{bmatrix} 1 & \rho_{12} & \rho_{13} \\ \rho_{12} & 1 & \rho_{23} \\ \rho_{13} & \rho_{23} & 1 \end{bmatrix}$.
  • Here, $R_{11} = \begin{bmatrix} 1 & \rho_{12} \\ \rho_{12} & 1 \end{bmatrix}$, $R_{1z} = \begin{bmatrix} \rho_{13} \\ \rho_{23} \end{bmatrix}$, $R_{z1} = \begin{bmatrix} \rho_{13} & \rho_{23} \end{bmatrix}$, and $R_{zz} = [1]$.
  • By the Schur complement formula, the conditional covariance matrix is: $R_{11\bullet 3} = R_{11} - R_{1z}R_{zz}^{-1}R_{z1}$.
  • Expand the term: $R_{1z}R_{zz}^{-1}R_{z1} = \begin{bmatrix} \rho_{13} \\ \rho_{23} \end{bmatrix} [1]^{-1} \begin{bmatrix} \rho_{13} & \rho_{23} \end{bmatrix} = \begin{bmatrix} \rho_{13}^2 & \rho_{13}\rho_{23} \\ \rho_{13}\rho_{23} & \rho_{23}^2 \end{bmatrix}$.
  • Subtract from $R_{11}$: $R_{11\bullet 3} = \begin{bmatrix} 1 - \rho_{13}^2 & \rho_{12} - \rho_{13}\rho_{23} \\ \rho_{12} - \rho_{13}\rho_{23} & 1 - \rho_{23}^2 \end{bmatrix}$.
  • The partial correlation is the off-diagonal element divided by the square root of the product of the diagonal elements:
  • $\rho_{12\bullet 3} = \frac{\rho_{12} - \rho_{13}\rho_{23}}{\sqrt{(1-\rho_{13}^2)(1-\rho_{23}^2)}}$.
• Conceptual Insight: Simpson's Paradox (The Iris Dataset Case)
  • Problem: The simple correlation between Sepal Length and Sepal Width is negative (-0.1176). However, the partial correlation controlling for Petal Length and Petal Width is positive (0.6286). What is going on?
  • Explanation: This is a classic example of Simpson's Paradox. Different species of Iris have drastically different overall sizes. When we look at the data *as a whole* (simple correlation), a species with a very long but narrow sepal is mixed with a species with a short but wide sepal, creating an artificial negative linear trend. 
  • By controlling for Petal Length and Width (which act as strong proxies for the overall scale/species of the flower), we are effectively looking at the correlation *within* a specific plant size constraint. Once the confounding size factor is removed, the true biological relationship emerges: flowers with longer sepals naturally tend to have wider sepals (+0.6286).



<font color="navy">**Ch1 Matrix Operations & Important Proofs (Exam Additions)**</font>

<font color="navy">**1. Advanced Matrix Properties & Proofs**</font>
• **Proof: Eigenvalues of a Positive Definite Matrix are strictly positive ($A > 0 \implies \lambda_i > 0$)**
Let $A > 0$. By definition, $x^\prime A x > 0$ for any non-zero vector $x$. Let $\lambda$ be an eigenvalue of $A$ with a corresponding normalized eigenvector $v$ (so $v^\prime v = 1$ and $v \ne 0$). By definition, $Av = \lambda v$. Pre-multiplying both sides by $v^\prime$, we get $v^\prime A v = v^\prime (\lambda v) = \lambda (v^\prime v) = \lambda$. Since $A > 0$ and $v \ne 0$, the quadratic form $v^\prime A v > 0$. Therefore, $\lambda > 0$.

• **Proof: Non-zero eigenvalues of $AB$ and $BA$ are the same**
Let $\lambda \ne 0$ be an eigenvalue of $AB$ with corresponding eigenvector $v \ne 0$. Thus, $(AB)v = \lambda v$. Pre-multiply both sides by $B$: $B(AB)v = B(\lambda v)$, which groups to $(BA)(Bv) = \lambda(Bv)$. Let $u = Bv$. If $u = 0$, then $(AB)v = A(0) = 0$, which would mean $\lambda v = 0$. Since $v \ne 0$, this would force $\lambda = 0$, contradicting our assumption that $\lambda \ne 0$. Thus, $u \ne 0$. This means $u$ is a valid eigenvector for $BA$ corresponding to the exact same eigenvalue $\lambda$.

• **Proof: The Matrix Identity $(A+B)^{-1} = A^{-1} - A^{-1}(A^{-1}+B^{-1})^{-1}A^{-1}$**
To prove this, multiply the right-hand side by $(A+B)$ and show it equals the identity matrix $I$:
$[A^{-1} - A^{-1}(A^{-1}+B^{-1})^{-1}A^{-1}](A+B)$
$= A^{-1}(A+B) - A^{-1}(A^{-1}+B^{-1})^{-1}A^{-1}(A+B)$
$= (I + A^{-1}B) - A^{-1}(A^{-1}+B^{-1})^{-1}(I + A^{-1}B)$
Factor out $(I + A^{-1}B)$ to the right:
$= [I - A^{-1}(A^{-1}+B^{-1})^{-1}] (I + A^{-1}B)$
Notice that $(I + A^{-1}B) = A^{-1}(A+B) = A^{-1}(B B^{-1} A + B A^{-1} A) \dots$ A simpler algebraic path from step 2 is to expand the $A^{-1}(A+B)$ explicitly:
$= I + A^{-1}B - A^{-1}(A^{-1}+B^{-1})^{-1}(A^{-1}A + A^{-1}B)$
$= I + A^{-1}B - A^{-1}(A^{-1}+B^{-1})^{-1}(A^{-1} + B^{-1})B$
Since $(A^{-1}+B^{-1})^{-1}(A^{-1} + B^{-1}) = I$, the expression simplifies to:
$= I + A^{-1}B - A^{-1}IB = I + A^{-1}B - A^{-1}B = I$. The identity holds.

<br>

<font color="navy">**Ch2 MVN Distributions (Exam Additions)**</font>

<font color="navy">**1. Constructing Joint Distribution from Marginal and Conditional**</font>
• **Problem:** If $X_1 \sim N_r(\mu_1, \Sigma_{11})$ and $(X_2 | X_1 = x_1) \sim N_{p-r}(A x_1 + b, \Omega)$, prove that the joint vector $X = [X_1^\prime, X_2^\prime]^\prime$ is multivariate normal and find its parameters.
• **Mean Vector:** $E(X_2) = E(E(X_2 | X_1)) = E(A X_1 + b) = A \mu_1 + b$. Thus $\mu = \begin{bmatrix} \mu_1 \\ A\mu_1 + b \end{bmatrix}$.
• **Cross-Covariance:** We can write $X_2 = A X_1 + b + \varepsilon$, where $\varepsilon \sim N(0, \Omega)$ is strictly independent of $X_1$. Then $Cov(X_1, X_2) = Cov(X_1, A X_1 + b + \varepsilon) = Cov(X_1, A X_1) + Cov(X_1, \varepsilon) = \Sigma_{11}A^\prime + 0 = \Sigma_{11}A^\prime$.
• **Variance of $X_2$:** $Var(X_2) = Var(E(X_2 | X_1)) + E(Var(X_2 | X_1)) = Var(A X_1 + b) + E(\Omega) = A\Sigma_{11}A^\prime + \Omega$.
• **Joint Distribution:** $X \sim N_p \left( \begin{bmatrix} \mu_1 \\ A\mu_1 + b \end{bmatrix}, \begin{bmatrix} \Sigma_{11} & \Sigma_{11}A^\prime \\ A\Sigma_{11} & \Omega + A\Sigma_{11}A^\prime \end{bmatrix} \right)$.

<font color="navy">**2. Independence of Linear Combinations**</font>
• **Method:** To find coefficients $\alpha, \beta$ such that a linear combination $Y = \beta X_1 + \alpha X_2 - X_3$ is independent of $X_3$, you must set their covariance to zero.
• **Calculation:** $Cov(Y, X_3) = \beta Cov(X_1, X_3) + \alpha Cov(X_2, X_3) - Var(X_3) = 0$. Extract the known variances/covariances from $\Sigma$ and solve the linear equation for $\alpha$ and $\beta$.

<br>

<font color="navy">**Ch3 Inferences on the Mean Vector (Exam Additions)**</font>

<font color="navy">**1. Student's t-Distribution from Sample Covariance (Proof)**</font>
• **Theorem:** Given $x_1, \dots, x_n \sim iid \ N_p(\mu, \Sigma)$ and any arbitrary non-zero constant vector $a$, prove that $\frac{a^\prime \overline{x} - a^\prime \mu}{\sqrt{\frac{1}{n} a^\prime S a}} \sim t_{n-1}$.
• **Proof:**
  <font color="navy">1.</font> Define a univariate transformation $y_i = a^\prime x_i$. Because linear combinations of MVN are normal, $y_i \sim N(a^\prime \mu, a^\prime \Sigma a)$.
  <font color="navy">2.</font> The sample mean of $y$ is $\overline{y} = a^\prime \overline{x}$, and its true theoretical variance is $\frac{1}{n}a^\prime \Sigma a$. Standardizing this yields $Z = \frac{a^\prime \overline{x} - a^\prime \mu}{\sqrt{\frac{1}{n} a^\prime \Sigma a}} \sim N(0, 1)$.
  <font color="navy">3.</font> The sample variance of $y$ is $s_y^2 = \frac{1}{n-1} \sum_{i=1}^n (a^\prime x_i - a^\prime \overline{x})^2 = a^\prime S a$, where $S = \frac{1}{n-1}\sum_{i=1}^n(x_i-\overline{x})(x_i-\overline{x})^\prime$.
  <font color="navy">4.</font> By Cochran's Theorem for univariate normals, $V = \frac{(n-1)s_y^2}{Var(y_i)} = \frac{(n-1) a^\prime S a}{a^\prime \Sigma a} \sim \chi_{n-1}^2$.
  <font color="navy">5.</font> Because $\overline{x}$ and $S$ are strictly independent, $Z$ and $V$ are independent.
  <font color="navy">6.</font> By the definition of the t-distribution, $T = \frac{Z}{\sqrt{V/(n-1)}}$. Substituting $Z$ and $V$:
  $$T = \frac{\frac{a^\prime \overline{x} - a^\prime \mu}{\sqrt{\frac{1}{n} a^\prime \Sigma a}}}{\sqrt{\frac{a^\prime S a}{a^\prime \Sigma a}}} = \frac{a^\prime \overline{x} - a^\prime \mu}{\sqrt{\frac{1}{n}a^\prime S a}} \sim t_{n-1}$$

<br>

<font color="navy">**Ch5 Principal Component Analysis (Exam Additions)**</font>

<font color="navy">**1. Rayleigh Quotient Proof for Minimum Variance ($\lambda_p$)**</font>
• **Theorem:** $min_{l \ne 0} \frac{l^\prime \Sigma l}{l^\prime l} = \lambda_p$, and the minimum is attained at $l = v_p$.
• **Proof:** Use the spectral decomposition $\Sigma = P \Lambda P^\prime$. Let $u = P^\prime l$. Since $P$ is orthogonal, $l^\prime l = u^\prime P P^\prime u = u^\prime u$. Substituting this gives the quotient $\frac{u^\prime \Lambda u}{u^\prime u} = \frac{\sum_{i=1}^p \lambda_i u_i^2}{\sum_{i=1}^p u_i^2}$. Because $\lambda_p$ is the smallest eigenvalue, $\lambda_i \ge \lambda_p$ for all $i$. Therefore, $\sum \lambda_i u_i^2 \ge \lambda_p \sum u_i^2$. The quotient is strictly $\ge \lambda_p$. The absolute minimum $\lambda_p$ is attained when $u_p = 1$ and all other $u_i = 0$, which means $u = \begin{bmatrix} 0 & \dots & 0 & 1 \end{bmatrix}^\prime$. Since $l = Pu$, this perfectly corresponds to $l = v_p$.

<font color="navy">**2. Inverse Sample Covariance ($S^{-1}$) & PCA**</font>
• **Proof that $S^{-1} = H \Lambda^{-1} H^\prime$:**
  Given the spectral decomposition $S = H \Lambda H^\prime$, where $H$ is orthogonal ($H^\prime H = I$). We multiply $S$ by our proposed inverse:
  $S (H \Lambda^{-1} H^\prime) = (H \Lambda H^\prime) (H \Lambda^{-1} H^\prime) = H \Lambda (H^\prime H) \Lambda^{-1} H^\prime$.
  Since $H^\prime H = I$, this simplifies to $H \Lambda I \Lambda^{-1} H^\prime = H (\Lambda \Lambda^{-1}) H^\prime = H I H^\prime = H H^\prime = I$.
• **Minimizing the Inverse Rayleigh Quotient:**
  To find a vector $u$ that minimizes $\frac{u^\prime S^{-1} u}{u^\prime u}$, we must find the smallest eigenvalue of $S^{-1}$. The eigenvalues of $S^{-1}$ are exactly $1/\lambda_i$. Since $\lambda_1 > \lambda_2 > \dots > \lambda_p$, the smallest eigenvalue of $S^{-1}$ is $1/\lambda_1$. According to the Rayleigh quotient theorem, this minimum value is achieved when the vector $u$ is the eigenvector corresponding to $1/\lambda_1$, which is simply $v_1$ (the loadings of the first principal component).


<font color="navy">**Question 2: Principal Component Analysis**</font>
• <font color="black">**Background:**</font> Given 3-dimensional data with sample mean $\overline{x} = [1, 3, 2]^\prime$. The eigenvalues of the covariance matrix $S$ are $\lambda_1=18.77$, $\lambda_2=6.41$, $\lambda_3=0.02$, with corresponding eigenvectors $h_1, h_2, h_3$.

<font color="navy">**(a) Find the percentage of total variance explained by the first three principal components**</font>
• Total variance $= \operatorname{tr}(S) = 18.77 + 6.41 + 0.02 = 25.20$.
• PC 1 percentage: $\frac{18.77}{25.20} = 74.48\%$.
• PC 2 percentage: $\frac{6.41}{25.20} = 25.44\%$.
• PC 3 percentage: $\frac{0.02}{25.20} = 0.08\%$.

<font color="navy">**(b) Given an observation $x_i = [-1, 2, 2]^\prime$, find its first and second principal component scores**</font>
• Centered observation: $x_c = x_i - \overline{x} = [-2, -1, 0]^\prime$.
• First PC score: $y_1 = h_1^\prime x_c = (0.711)(-2) + (-0.446)(-1) + (-0.544)(0) = -0.976$.
• Second PC score: $y_2 = h_2^\prime x_c = (-0.011)(-2) + (-0.766)(-1) + (0.643)(0) = 0.788$.

<font color="navy">**(c) Find the reconstructed $\tilde{x}_i$ using only the first two principal components**</font>
• Reconstruction formula: $\tilde{x}_i = \overline{x} + y_1 h_1 + y_2 h_2$.
• $\tilde{x}_i = \begin{bmatrix} 1 \\ 3 \\ 2 \end{bmatrix} + (-0.976)\begin{bmatrix} 0.711 \\ -0.446 \\ -0.544 \end{bmatrix} + (0.788)\begin{bmatrix} -0.011 \\ -0.766 \\ 0.643 \end{bmatrix} = \begin{bmatrix} 0.2974 \\ 2.8317 \\ 3.0377 \end{bmatrix}$.

<font color="navy">**(d) Find a vector $u$ to maximize $\frac{u^\prime S^{-1} u}{u^\prime u}$ and state the maximum value. Is it unique?**</font>
• Maximum value: The largest eigenvalue of $S^{-1}$, which is $\frac{1}{\lambda_3} = \frac{1}{0.02} = 50$.
• Corresponding vector $u$: The eigenvector $h_3 = [-0.703, -0.463, -0.540]^\prime$.
• Uniqueness: Not unique. Any non-zero scalar multiple (e.g. $-h_3$) yields the same maximum.

<font color="navy">**(e) Let $Y = [2X_1, 3X_2, 0.1X_3]^\prime$. Compute the sample covariance and correlation matrix for $Y$**</font>
• Let $C = \operatorname{diag}(2, 3, 0.1)$. Then $S_Y = C S_X C^\prime$.
• $S_Y = \begin{bmatrix} 2 & 0 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 0.1 \end{bmatrix} \begin{bmatrix} 9.5 & -6 & -7.2 \\ -6 & 7.5 & 1.4 \\ -7.2 & 1.4 & 8.2 \end{bmatrix} \begin{bmatrix} 2 & 0 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 0.1 \end{bmatrix} = \begin{bmatrix} 38.0 & -36.0 & -1.44 \\ -36.0 & 67.5 & 0.42 \\ -1.44 & 0.42 & 0.082 \end{bmatrix}$.
• Scaling does not change correlation: $R_Y = R_X$.
• $r_{12} = \frac{-6}{\sqrt{9.5 \cdot 7.5}} = -0.7108$, $r_{13} = \frac{-7.2}{\sqrt{9.5 \cdot 8.2}} = -0.8162$, $r_{23} = \frac{1.4}{\sqrt{7.5 \cdot 8.2}} = 0.1785$.
• $R_Y = \begin{bmatrix} 1 & -0.7108 & -0.8162 \\ -0.7108 & 1 & 0.1785 \\ -0.8162 & 0.1785 & 1 \end{bmatrix}$.

<font color="navy">**Question 3: Partial Correlation Analysis**</font>
• <font color="black">**Background:**</font> Given $n=100$ observations of 3 variables, with sample covariance matrix elements: $s_{11}=3.61$, $s_{22}=6.25$, $s_{33}=1.21$, $s_{12}=3.8$, $s_{13}=-0.209$, $s_{23}=-0.55$.

<font color="navy">**(a) Compute the partial correlation coefficient $r_{23\bullet 1}$**</font>
• Conditional covariance: $s_{ij\bullet 1} = s_{ij} - \frac{s_{i1} \cdot s_{j1}}{s_{11}}$.
• $s_{22\bullet 1} = 6.25 - \frac{3.8 \cdot 3.8}{3.61} = 2.25$.
• $s_{33\bullet 1} = 1.21 - \frac{(-0.209) \cdot (-0.209)}{3.61} = 1.1979$.
• $s_{23\bullet 1} = -0.55 - \frac{3.8 \cdot (-0.209)}{3.61} = -0.33$.
• Partial correlation: $r_{23\bullet 1} = \frac{s_{23\bullet 1}}{\sqrt{s_{22\bullet 1} \cdot s_{33\bullet 1}}} = \frac{-0.33}{\sqrt{2.25 \cdot 1.1979}} = -0.2010$.

<font color="navy">**(b) Test $H_0: \rho_{23\bullet 1} = 0$ at 5% significance level**</font>
• Test Statistic: $t_{stat} = \sqrt{n-q-2} \cdot \frac{r_{23\bullet 1}}{\sqrt{1 - r_{23\bullet 1}^2}}$, where $n=100, q=1$.
• $t_{stat} = \sqrt{97} \cdot \frac{-0.2010}{\sqrt{1 - (-0.2010)^2}} = -2.0208$.
• Critical Value: $t_{97}(0.025) = 1.9847$.
• Conclusion: Since $|-2.0208| > 1.9847$, reject $H_0$.

<font color="navy">**1. Geometric View and Reconstruction**</font>
<font color="black">**Problem:**</font> Let $p = 2$ and suppose we have 4 centered observations ($\overline{x} = 0$): $x_1 = \begin{bmatrix} 3 \\ 1 \end{bmatrix}$, $x_2 = \begin{bmatrix} -1 \\ 1 \end{bmatrix}$, $x_3 = \begin{bmatrix} 2 \\ -1 \end{bmatrix}$, $x_4 = \begin{bmatrix} -4 \\ -1 \end{bmatrix}$. The first eigenvector (first PC direction) is $v_1 = (1, 0)^T$.
a) Compute the projection score $d_{i1} = x_i^T v_1$ for each observation.
b) Compute the reconstructed points $\tilde{x}_i = v_1 v_1^T x_i$ using only the first PC.
c) Compute the reconstruction error $\|x_i - \tilde{x}_i\|^2$ for each observation.
d) Verify that $d_{i1}^2 + \|x_i - \tilde{x}_i\|^2 = \|x_i\|^2$ for each $i$.
• <font color="navy">a)</font> $d_{11} = [3 \quad 1] \begin{bmatrix} 1 \\ 0 \end{bmatrix} = 3$    $d_{21} = [-1 \quad 1] \begin{bmatrix} 1 \\ 0 \end{bmatrix} = -1$  $d_{31} = [2 \quad -1] \begin{bmatrix} 1 \\ 0 \end{bmatrix} = 2$   $d_{41} = [-4 \quad -1] \begin{bmatrix} 1 \\ 0 \end{bmatrix} = -4$
• <font color="navy">b)</font> $\tilde{x}_1 = 3 \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} 3 \\ 0 \end{bmatrix}$, $\tilde{x}_2 = -1 \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} -1 \\ 0 \end{bmatrix}$, $\tilde{x}_3 = 2 \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} 2 \\ 0 \end{bmatrix}$, $\tilde{x}_4 = -4 \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} -4 \\ 0 \end{bmatrix}$.
• <font color="navy">c)</font> For $i=1$: $\| \begin{bmatrix} 3 \\ 1 \end{bmatrix} - \begin{bmatrix} 3 \\ 0 \end{bmatrix} \|^2 = \|\begin{bmatrix} 0 \\ 1 \end{bmatrix}\|^2 = 1$   For $i=2$: $\| \begin{bmatrix} -1 \\ 1 \end{bmatrix} - \begin{bmatrix} -1 \\ 0 \end{bmatrix} \|^2 = \|\begin{bmatrix} 0 \\ 1 \end{bmatrix}\|^2 = 1$
  For $i=3$: $\| \begin{bmatrix} 2 \\ -1 \end{bmatrix} - \begin{bmatrix} 2 \\ 0 \end{bmatrix} \|^2 = \|\begin{bmatrix} 0 \\ -1 \end{bmatrix}\|^2 = 1$   For $i=4$: $\| \begin{bmatrix} -4 \\ -1 \end{bmatrix} - \begin{bmatrix} -4 \\ 0 \end{bmatrix} \|^2 = \|\begin{bmatrix} 0 \\ -1 \end{bmatrix}\|^2 = 1$
• <font color="navy">d)</font> For $i=1$: $3^2 + 1 = 10$. Original norm squared is $3^2 + 1^2 = 10$. Valid.
  For $i=2$: $(-1)^2 + 1 = 2$. Original norm squared is $(-1)^2 + 1^2 = 2$. Valid.
  For $i=3$: $2^2 + 1 = 5$. Original norm squared is $2^2 + (-1)^2 = 5$. Valid.
  For $i=4$: $(-4)^2 + 1 = 17$. Original norm squared is $(-4)^2 + (-1)^2 = 17$. Valid.

<font color="navy">**2. Computation — Non-Centered Data**</font>
<font color="black">**Problem:**</font> Let $p = 2$ and consider three (non-centered) observations: $x_1 = \begin{bmatrix} 4 \\ 5 \end{bmatrix}$, $x_2 = \begin{bmatrix} 6 \\ 7 \end{bmatrix}$, $x_3 = \begin{bmatrix} 5 \\ 6 \end{bmatrix}$. The first eigenvector of the sample covariance is $v_1 = \frac{1}{\sqrt{2}}(1, 1)^T$.
a) Compute the sample mean $\overline{x}$.
b) Compute the reconstruction of each $x_i$ using only 1 PC: $\tilde{x}_i = v_1 v_1^T (x_i - \overline{x}) + \overline{x}$.
c) Give a geometric interpretation of this formula.

<font color="black">**Solution:**</font>
• <font color="navy">a)</font> $\overline{x} = \frac{1}{3} (\begin{bmatrix} 4 \\ 5 \end{bmatrix} + \begin{bmatrix} 6 \\ 7 \end{bmatrix} + \begin{bmatrix} 5 \\ 6 \end{bmatrix}) = \frac{1}{3} \begin{bmatrix} 15 \\ 18 \end{bmatrix} = \begin{bmatrix} 5 \\ 6 \end{bmatrix}$.
• <font color="navy">b)</font> The projection matrix is $v_1 v_1^T = \frac{1}{2} \begin{bmatrix} 1 \\ 1 \end{bmatrix} [1 \quad 1] = \begin{bmatrix} 0.5 & 0.5 \\ 0.5 & 0.5 \end{bmatrix}$.
  For $i=1$: $x_1 - \overline{x} = \begin{bmatrix} -1 \\ -1 \end{bmatrix}$. Projection is $\begin{bmatrix} 0.5 & 0.5 \\ 0.5 & 0.5 \end{bmatrix} \begin{bmatrix} -1 \\ -1 \end{bmatrix} = \begin{bmatrix} -1 \\ -1 \end{bmatrix}$. Thus $\tilde{x}_1 = \begin{bmatrix} -1 \\ -1 \end{bmatrix} + \begin{bmatrix} 5 \\ 6 \end{bmatrix} = \begin{bmatrix} 4 \\ 5 \end{bmatrix}$.
  For $i=2$: $x_2 - \overline{x} = \begin{bmatrix} 1 \\ 1 \end{bmatrix}$. Projection is $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$. Thus $\tilde{x}_2 = \begin{bmatrix} 1 \\ 1 \end{bmatrix} + \begin{bmatrix} 5 \\ 6 \end{bmatrix} = \begin{bmatrix} 6 \\ 7 \end{bmatrix}$.
  For $i=3$: $x_3 - \overline{x} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$. Projection is $\begin{bmatrix} 0 \\ 0 \end{bmatrix}$. Thus $\tilde{x}_3 = \begin{bmatrix} 0 \\ 0 \end{bmatrix} + \begin{bmatrix} 5 \\ 6 \end{bmatrix} = \begin{bmatrix} 5 \\ 6 \end{bmatrix}$.
• <font color="navy">c)</font> Geometric interpretation: The formula shifts the origin to the sample mean $\overline{x}$, orthogonally projects the centered data onto the 1-dimensional subspace spanned by $v_1$, and then shifts the coordinates back to the original space. It finds the closest point on the line passing through $\overline{x}$ with direction $v_1$.
<font color="navy">**3. Proof — SVD and PCA Reconstruction Connection**</font>
<font color="black">**Problem:**</font> Let $X$ be an $n \times p$ data matrix ($n > p$) with sample mean $\overline{x}$ and let $Y = \frac{1}{\sqrt{n-1}}(X - 1_n \overline{x}^T)$ with SVD $Y = UDV^T$. Show that the rank-$q$ PCA reconstruction of the data can be written as: $\tilde{X} = 1_n \overline{x}^T + \sqrt{n-1} \sum_{j=1}^q d_j u_j v_j^T$.

<font color="black">**Solution:**</font>
• From the SVD of the scaled and centered matrix $Y = UDV^T$, we can express it as a sum of rank-1 matrices: $Y = \sum_{j=1}^p d_j u_j v_j^T$.
• By the Eckart-Young-Mirsky theorem, the best rank-$q$ approximation of $Y$ is obtained by truncating the series to the first $q$ components: $Y_q = \sum_{j=1}^q d_j u_j v_j^T$.
• The PCA reconstruction aims to approximate the original uncentered matrix $X$ using this rank-$q$ representation. From the definition $Y = \frac{1}{\sqrt{n-1}}(X - 1_n \overline{x}^T)$, we replace $Y$ with its approximation $Y_q$ and $X$ with the reconstructed matrix $\tilde{X}$:
  $Y_q = \frac{1}{\sqrt{n-1}}(\tilde{X} - 1_n \overline{x}^T)$
• Multiplying both sides by $\sqrt{n-1}$ yields:   $\tilde{X} - 1_n \overline{x}^T = \sqrt{n-1} Y_q$
• Substitute $Y_q$ back into the equation:   $\tilde{X} - 1_n \overline{x}^T = \sqrt{n-1} \sum_{j=1}^q d_j u_j v_j^T$
• Finally, isolate $\tilde{X}$ by adding the mean matrix to both sides:   $\tilde{X} = 1_n \overline{x}^T + \sqrt{n-1} \sum_{j=1}^q d_j u_j v_j^T$.

<font color="navy">**Original Concept: Marginal vs. Joint Gaussian**</font>
• <font color="black">**Question:**</font> Provide an example where each variable in a random vector marginally follows a univariate Gaussian distribution, but jointly the random vector does not follow a multivariate Gaussian distribution.
• <font color="black">**Answer & Construction:**</font>
  Let $X \sim N(0, 1)$ be a standard normal random variable.
  Let $Z$ be a discrete random variable independent of $X$, such that $P(Z=1) = 0.5$ and $P(Z=-1) = 0.5$.
  Define $Y = Z \cdot X$.
  • <font color="navy">1.</font> The marginal distribution of $X$ is explicitly $N(0, 1)$.
  • <font color="navy">2.</font> The marginal distribution of $Y$ is also $N(0, 1)$ due to the perfect symmetry of the normal distribution around zero.
  • <font color="navy">3.</font> However, the joint distribution of $(X, Y)^\prime$ is not bivariate normal. The probability $P(|X| = |Y|) = 1$, which implies the entire probability mass is concentrated strictly on the intersecting lines $Y = X$ and $Y = -X$. A true non-degenerate bivariate normal distribution must form a continuous 2D bell-shaped surface, not an "X-shaped" degenerate support.
<font color="navy">**Variation 1: Uncorrelated but Dependent**</font>
• <font color="black">**Question:**</font> For multivariate normal distributions, being uncorrelated implies independence. Provide an example of two normally distributed variables that are uncorrelated but are NOT independent.
• <font color="black">**Answer & Construction:**</font> 同上
<font color="navy">**Variation 2: Non-Gaussian Linear Combination**</font>
• <font color="black">**Question:**</font> If a random vector is multivariate normal, any linear combination of its components must be univariate normal. Provide an example where $X$ and $Y$ are marginally normal, but their sum $X+Y$ is NOT normal.
• <font color="black">**Answer & Construction:**</font>
  Using the same construction: $X \sim N(0, 1)$, $P(Z=1)=P(Z=-1)=0.5$, and $Y = Z \cdot X$.
  Consider the linear combination $W = X + Y = X + Z \cdot X = X \cdot (1+Z)$.
  • If $Z = -1$ (which occurs with $50\%$ probability), $W = X \cdot (1-1) = 0$.
  • If $Z = 1$ (which occurs with $50\%$ probability), $W = X \cdot (1+1) = 2X \sim N(0, 4)$.
  • <font color="navy">Conclusion:</font> The distribution of $X+Y$ has a discrete point mass at exactly $0$ with a probability of $0.5$, combined with a continuous normal curve for the remaining $0.5$ probability. A true normal distribution cannot contain a discrete point mass, thus $X+Y$ is not normally distributed.



<img src="D:/CUHK/25-26term2/STAT4002/537.jpg" width="300" alt="乌萨奇">
