# Derivations Rules

## 1. Reglas Básicas de Derivación

| Función                | Derivada                          | Explicación                           |
|------------------------|-----------------------------------|---------------------------------------|
| Constante $c$          | $0$                               | La derivada de una constante es cero  |
| $x^n$                  | $nx^{n-1}$                        | Potencia de $x$                       |
| $c \cdot f(x)$         | $c \cdot f'(x)$                   | Constante por función                 |
| $e^x$                  | $e^x$                             | Exponencial con base $e$              |
| $a^x$                  | $a^x \ln(a)$                      | Exponencial con base $a$              |
| $\ln(x)$               | $\frac{1}{x}$                     | Logaritmo natural                     |
| $\log_a(x)$            | $\frac{1}{x \ln(a)}$              | Logaritmo en base $a$                 |

## 2. Derivadas de Funciones Trigonométricas

| Función                | Derivada                          | Explicación                           |
|------------------------|-----------------------------------|---------------------------------------|
| $\sin(x)$              | $\cos(x)$                         | Seno                                  |
| $\cos(x)$              | $-\sin(x)$                        | Coseno                                |
| $\tan(x)$              | $\sec^2(x)$                       | Tangente                              |
| $\cot(x)$              | $-\csc^2(x)$                      | Cotangente                            |
| $\sec(x)$              | $\sec(x)\tan(x)$                  | Secante                               |
| $\csc(x)$              | $-\csc(x)\cot(x)$                 | Cosecante                             |

## 3. Derivadas de Funciones Trigonométricas Inversas

| Función                | Derivada                          | Explicación                           |
|------------------------|-----------------------------------|---------------------------------------|
| $arcsin(x)$           | $\frac{1}{\sqrt{1 - x^2}}$        | Arcoseno                              |
| $\arccos(x)$           | $-\frac{1}{\sqrt{1 - x^2}}$       | Arcocoseno                            |
| $arctan(x)$           | $\frac{1}{1 + x^2}$               | Arcotangente                          |
| $arccot(x)$           | $-\frac{1}{1 + x^2}$             | Arcocotangente                        |
| $arcsec(x)$ | $\frac{1}{\mid x\mid\sqrt{x^2-1}}$ | Arcosecante |
| $arccsc(x)$ | $-\frac{1}{\mid x\mid\sqrt{x^2-1}}$ | Arcocosecante |

## 4. Reglas de Derivación Avanzadas

| Regla                      | Fórmula                                    | Explicación                               |
|----------------------------|--------------------------------------------|-------------------------------------------|
| **Suma/Diferencia**        | $(f \pm g)' = f' \pm g'$                   | Derivada de la suma/resta de funciones    |
| **Producto**               | $(f \cdot g)' = f' \cdot g + f \cdot g'$   | Derivada del producto de funciones        |
| **Cociente**               | $\left(\frac{f}{g}\right)' = \frac{f'g - fg'}{g^2}$ | Derivada del cociente de funciones |
| **Regla de la Cadena**     | $(f(g(x)))' = f'(g(x)) \cdot g'(x)$        | Derivada de función compuesta             |

## 5. Derivadas de Funciones Hiperbólicas

| Función                    | Derivada                                | Explicación                           |
|----------------------------|-----------------------------------------|---------------------------------------|
| $\sinh(x)$                 | $\cosh(x)$                              | Seno hiperbólico                      |
| $\cosh(x)$                 | $\sinh(x)$                              | Coseno hiperbólico                    |
| $\tanh(x)$                 | $\operatorname{sech}^2(x)$              | Tangente hiperbólica                  |
| $\coth(x)$                 | $-\operatorname{csch}^2(x)$             | Cotangente hiperbólica                |
| $\operatorname{sech}(x)$   | $-\operatorname{sech}(x)\tanh(x)$       | Secante hiperbólica                   |
| $\operatorname{csch}(x)$   | $-\operatorname{csch}(x)\coth(x)$       | Cosecante hiperbólica                 |
