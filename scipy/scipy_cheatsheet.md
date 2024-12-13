# SciPy Cheat Sheet Completa

---

### **Importación básica**
```python
import scipy
import numpy as np
import scipy.linalg as la
import scipy.optimize as opt
import scipy.integrate as integrate
import scipy.stats as stats
import scipy.signal as signal
import scipy.spatial as spatial
```

Álgebra lineal (scipy.linalg)

Funciones para descomposición de matrices, resolución de ecuaciones lineales, etc.
- Determinante
```python
det = la.det(A)
```

Inversa
```python
inv = la.inv(A)
```

Descomposición LU
```python
P, L, U = la.lu(A)
```

Descomposición QR
```python
Q, R = la.qr(A)
```

Descomposición de valores propios
```python
eigvals, eigvecs = la.eig(A)
```

Solución de sistema de ecuaciones lineales
```python
x = la.solve(A, b)
```

Norma de una matriz
```python
norm = la.norm(A)
```

Matriz pseudoinversa
```python
pinv = la.pinv(A)
```

Optimización (scipy.optimize)
Funciones para optimizar y encontrar raíces.
Minimización de una función escalar
```python
result = opt.minimize(fun, x0, method='BFGS')
```

Raíces de una función
```python
root = opt.root(fun, x0)
```

Optimización sin restricciones
```python
result = opt.fminbound(fun, lower, upper)
```

Métodos de mínimos cuadrados
```python
result = opt.leastsq(fun, x0)
```

Integración numérica (scipy.integrate)
Funciones para integrar ecuaciones diferenciales y funciones.
Integración de una función definida
```python
integral, error = integrate.quad(func, a, b)
```

Ecuaciones diferenciales ordinarias
```python
sol = integrate.solve_ivp(fun, (t0, tf), y0, t_eval=np.linspace(t0, tf, 100))
```

Solución de integrales múltiples
```python
integral = integrate.dblquad(func, x0, x1, y0, y1)
```

Distribuciones estadísticas (scipy.stats)
Funciones para trabajar con distribuciones y realizar tests estadísticos.
Generar números aleatorios según distribución\
```python
samples = stats.norm.rvs(loc=0, scale=1, size=100)
```

Valor p de una prueba de hipótesis
```python
p_value = stats.ttest_1samp(data, popmean=0)
```

Prueba de normalidad (Shapiro-Wilk)
```python
stat, p = stats.shapiro(data)
```

Distribución Normal (PDF, CDF, y más)
```python
pdf = stats.norm.pdf(x, loc=0, scale=1)
cdf = stats.norm.cdf(x, loc=0, scale=1)
```

Correlación de Pearson
```python
corr, p_value = stats.pearsonr(x, y)
```

Estadísticas descriptivas
```python
mean = stats.tmean(data)
var = stats.tvar(data)
```

Señales y sistemas (scipy.signal)
Funciones para procesar señales.
Filtro FIR
```python
b, a = signal.butter(N, Wn, btype='low', analog=False)
filtered_signal = signal.filtfilt(b, a, signal)
```

Transformada rápida de Fourier (FFT)
```python
f = np.fft.fft(signal)
```

Correlación cruzada
```python
cross_corr = signal.correlate(signal1, signal2)
```

Generación de señales
```python
t = np.linspace(0, 1, 500)
signal = np.sin(2 * np.pi * 5 * t)
```

Espacio y geometría (scipy.spatial)
Funciones para trabajar con distancias, espacios y estructuras geométricas.
Distancia euclidiana
```python
distance = spatial.distance.euclidean(p1, p2)
```

Árbol de búsqueda KD
```python
tree = spatial.KDTree(points)
nearest = tree.query(point)
```

Convex hull
```python
hull = spatial.ConvexHull(points)
```

Matriz de distancias entre puntos
```python
dist_matrix = spatial.distance.pdist(points)
```

Interpolación (scipy.interpolate)
Funciones para interpolación de datos.
Interpolación 1D (spline)
```python
f = interpolate.interp1d(x, y, kind='cubic')
y_interp = f(x_new)
```

Interpolación 2D (griddata)
```python
z = interpolate.griddata((x, y), values, (xnew, ynew), method='cubic')
```

Spline cúbico
```python
tck = interpolate.splrep(x, y)
y_spl = interpolate.splev(x_new, tck)
```

Matemáticas especiales (scipy.special)
Funciones matemáticas especiales como funciones de Bessel, Gamma, etc.
Función Gamma
```python
gamma_value = special.gamma(x)
```

Función Bessel de primera especie
```python
jv = special.jv(n, x)
```

Función Error
```python
erf_value = special.erf(x)
```

Optimización global (scipy.optimize)
Métodos para optimización global y de múltiples variables.
Búsqueda aleatoria (differential evolution)
```python
result = opt.differential_evolution(func, bounds)
```

Algoritmo de Nelder-Mead
```python
result = opt.minimize(fun, x0, method='Nelder-Mead')
```

Optimización con restricciones
```python
result = opt.minimize(fun, x0, constraints={'type': 'ineq', 'fun': constraint_fun})
```

Otros métodos útiles
Generación de matrices dispersas
```python
from scipy.sparse import csr_matrix
sparse_matrix = csr_matrix((data, (rows, cols)), shape=(n_rows, n_cols))
```

Combinaciones y permutaciones
```python
comb = special.comb(n, k)
perm = special.perm(n, k)
```
