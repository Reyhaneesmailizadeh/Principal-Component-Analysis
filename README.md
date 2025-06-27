# Principal-Component-Analysis


  <h1>Linear Algebra – Computer Project (Fall 1403 / 2024)</h1>
  <h2>Faculty of Science, University of Tehran</h2>
  <p><strong>Instructor:</strong> Dr. Amiri</p>
  <p><strong>Designers:</strong> Mardin Nichi & Mani Mirshabani</p>

  <h2>Project Overview</h2>
  <p>
    In this project, we want to become familiar with a tool from linear algebra for dimensionality reduction called 
    <strong>Principal Component Analysis (PCA)</strong>. PCA finds a set of basis vectors in the space that represent the 
    directions of maximum variance in the data.
  </p>
  <p>We will go through this project step-by-step until we implement and prove PCA.</p>

  <h3>Step 1: Understanding the Dataset</h3>
  <p>
    Let the dataset <code>D</code> be an <code>n × d</code> matrix, where each row is a sample and each column is a feature. 
    Denote samples by <code>x₁</code> to <code>xₙ</code> and each feature value as <code>xᵢⱼ</code>, the value of the j-th 
    feature for the i-th sample.
  </p>
  <p>
    The variance of feature <code>Xᵢ</code> is:
    <br>
    <code>Var(Xᵢ) = E[(x - μₓᵢ)²]</code>
  </p>
  <p>
    Covariance between two features X and Y is:
    <br>
    <code>Cov(X, Y) = E[(x_Y - μ_Y)(x_T - μ_T)]</code>
  </p>
  <p>
    Using the dataset <code>D</code>, define a method to compute the <strong>correlation matrix</strong> — a 
    <code>d × d</code> matrix where the (i, j)-th entry is the covariance between features i and j.
  </p>

  <h3>Step 2: First Principal Component</h3>
  <p>
    Let <code>u₁</code> be the first vector such that projecting data onto it maximizes variance.
    Assume <code>u₁ᵀu₁ = 1</code>.
  </p>
  <p>
    Define variance of projection:
    <br>
    <code>σ_u₁ = u₁ᵀ Σ u₁</code>
  </p>
  <p>
    To maximize variance: <code>max_u uᵀΣu</code>. But this is unbounded unless we constrain <code>uᵀu = 1</code>.
    Solve using <strong>Lagrange multipliers</strong>:
    <br>
    <code>max_u uᵀΣu − λ(1 − uᵀu)</code>
  </p>
  <p>
    (For more, see optimization or operations research references.)
  </p>

  <h3>Step 3: Deriving Eigenvectors</h3>
  <p>
    We know optimal points satisfy the gradient = 0:
    <br>
    <code>∂/∂u (uᵀΣu − λ(1 − uᵀu)) = 0</code> → <code>Σu = λu</code>
  </p>
  <p>
    This proves that the direction of maximum variance is the eigenvector of <code>Σ</code>.
    The variance equals the corresponding eigenvalue.
  </p>
  <p>
    Now guess and prove that the next eigenvectors (ordered by eigenvalue) also correspond to directions of decreasing variance.
  </p>
  <p>
    <strong>Induction:</strong><br>
    - Base case: Proven for <code>n = 1</code>.<br>
    - Inductive hypothesis: Assume <code>{u₁, u₂, ..., uⱼ₋₁}</code> are eigenvectors with max variances and are orthogonal.<br>
    - Step: Show <code>uⱼ</code> is orthogonal to previous and corresponds to the next largest eigenvalue.
  </p>
  <p>
    Add constraints using Lagrange multipliers:
  </p>
  <pre>
max_v J(v) = vᵀΣv − α(vᵀv − 1) − ∑ᵢ₌₁^{j−1} βᵢ(uᵢᵀv)
  </pre>

  <h3>Step 4: Proving the Optimization</h3>
  <p>
    Take derivative with respect to <code>v</code>, set it to 0, and prove <code>v</code> is also an eigenvector of <code>Σ</code>.
  </p>

  <h3>Step 5: Representing Data in the New Basis</h3>
  <p>How can we express the original data in the new PCA basis vectors?</p>

  <h3>Step 6: Variance in New Basis</h3>
  <p>Prove that the sum of variances in the new basis equals the sum of eigenvalues of those basis vectors.</p>

  <h2>Implementation Instructions</h2>
  <p>
    So far, we’ve learned that to perform PCA:
  </p>
  <ol>
    <li>Compute the correlation matrix.</li>
    <li>Find eigenvectors and eigenvalues.</li>
    <li>Project the data onto the principal components.</li>
  </ol>
  <p>
    You are now asked to <strong>implement PCA from scratch in Python</strong> (not using any pre-built PCA functions).
  </p>
  <p>
    <strong>Note:</strong> You <em>may not</em> use built-in PCA libraries.  
    You <strong>can</strong> use the <code>QR Algorithm</code> to compute eigenvectors.
  </p>
  <p>
    Submit your answers in either:
    <ul>
      <li>A <strong>PDF file</strong>, or</li>
      <li>A <strong>Markdown notebook (.ipynb)</strong></li>
    </ul>
  </p>

  <h3>Code Reuse</h3>
  <p>
    In the next phase of the project, you will need the notebook you implemented earlier.  
    Make sure the previous code is fully ready and available for use.
  </p>

  <p><em>All required information is available in the notebook provided for this section.</em></p>

</body>
</html>
