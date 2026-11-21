# Formulario y notación común · Módulo 1

*Finanzas Cuantitativas con Python y Machine Learning · Aplicaciones de Python en finanzas*

Esta es la notación única del módulo: cada símbolo significa lo mismo en clases, notebooks, prácticas y en el Módulo 2. Cada fórmula de este formulario se programa en la sesión donde aparece.

| Sección | Se usa en |
|---|---|
| [Convenciones generales](#convenciones-generales) | Todo el módulo |
| [Probabilidad básica](#probabilidad-básica) | Sesiones 3, 6 y 7 |
| [Valor del dinero en el tiempo](#valor-del-dinero-en-el-tiempo) | Sesión 2 (lectura de la Práctica 1) |
| [Rendimientos](#rendimientos) | Sesión 3 |
| [Riesgo y momentos](#riesgo-y-momentos) | Sesión 3 |
| [Series de tiempo](#series-de-tiempo) | Sesión 5 |
| [Medidas de desempeño y riesgo](#medidas-de-desempeño-y-riesgo) | Sesiones 6 y 7 |
| [Monte Carlo y movimiento browniano geométrico](#monte-carlo-y-movimiento-browniano-geométrico) | Sesión 7 (optativo) |
| [De la notación al código](#de-la-notación-al-código) | Todo el módulo |

## Convenciones generales

- **Tiempo:** $t$ indexa días hábiles. $P_t$ es el precio de cierre ajustado (dividendos y splits) del día $t$.
- **Frecuencia:** diaria salvo que se indique otra. Un año bursátil = 252 días hábiles. Las tasas de CETES usan base 360.
- **Unidades:** rendimientos y tasas en decimales (0.05, no 5); el porcentaje solo al presentar resultados.
- **Estimadores:** con gorro ($\hat\mu$, $\hat\sigma$) cuando se calculan con datos; sin gorro ($\mu$, $\sigma$) cuando son parámetros del modelo.
- **Pérdidas:** $L = -r$. Una pérdida es un número positivo, y VaR y CVaR se reportan como números positivos.
- **Nivel de confianza:** $\alpha$ (por ejemplo 0.95 o 0.99); $1 - \alpha$ es la probabilidad de la cola. En código: `nivel = 0.95` y `cola = 1 - nivel`; no se llama `alpha` a la cola, para no confundirla con $\alpha$.
- **Módulo 2:** los vectores irán en negritas ($\mathbf{w}$, $\boldsymbol{\mu}$) y las matrices en mayúscula ($\Sigma$).

## Probabilidad básica

Un rendimiento es una variable aleatoria: todo lo que medimos en el módulo es un momento o un cuantil de su distribución.

Esperanza, varianza y volatilidad:

$$\mu = E[X], \qquad \sigma^2 = \operatorname{Var}(X) = E\big[(X-\mu)^2\big], \qquad \sigma = \sqrt{\operatorname{Var}(X)}$$

Estimadores muestrales con $T$ observaciones (la varianza divide entre $T - 1$):

$$\hat{\mu} = \frac{1}{T}\sum_{t=1}^{T} x_t, \qquad \hat{\sigma}^2 = \frac{1}{T-1}\sum_{t=1}^{T} (x_t - \hat{\mu})^2$$

Cuantil $p$ de $X$, con $F_X$ su función de distribución:

$$q_p(X) = \inf\lbrace\, x : F_X(x) \ge p \,\rbrace$$

Normal estándar: $Z \sim N(0, 1)$, con densidad $\varphi$, distribución $\Phi$ y cuantil $z_p = \Phi^{-1}(p)$. Valores de referencia: $z_{0.95} = 1.645$, $z_{0.99} = 2.326$, $z_{0.975} = 1.960$.

Si $X = \mu + \sigma Z$, los cuantiles se trasladan y escalan igual que la variable:

$$q_p(X) = \mu + \sigma\, z_p$$

## Valor del dinero en el tiempo

$VP$ es valor presente, $VF$ valor futuro, $r$ la tasa anual y $n$ el plazo en años. La capitalización continua es el límite de la compuesta y es la razón de que existan los rendimientos logarítmicos.

Interés simple, compuesto $m$ veces al año y continuo:

$$VF = VP\,(1 + r\,n), \qquad VF = VP\left(1 + \frac{r}{m}\right)^{m n}, \qquad VF = VP\, e^{r n}$$

El límite que une a las dos últimas:

$$\lim_{m \to \infty} \left(1 + \frac{r}{m}\right)^{m n} = e^{r n}$$

Tasa efectiva anual y su equivalente continua:

$$r_{ef} = \left(1 + \frac{r}{m}\right)^{m} - 1, \qquad r_c = \ln(1 + r_{ef})$$

Valor presente de un flujo $C_1, \dots, C_n$ pagado en los tiempos $t_k$:

$$VP = \sum_{k=1}^{n} \frac{C_k}{(1 + r)^{t_k}}$$

CETES (valor nominal $VN = 10$ pesos, $d$ días por vencer, base 360). Precio a partir de la tasa de rendimiento $r$ y de la tasa de descuento $d_s$:

$$P = \frac{VN}{1 + r\,\dfrac{d}{360}}, \qquad P = VN\left(1 - d_s\,\dfrac{d}{360}\right)$$

Y de vuelta, la tasa de rendimiento implícita en el precio:

$$r = \left(\frac{VN}{P} - 1\right)\frac{360}{d}$$

## Rendimientos

$R_t$ es el rendimiento simple y $r_t$ el logarítmico. Regla para recordar: **los logarítmicos se suman en el tiempo; los simples se suman entre activos** (Módulo 2).

$$R_t = \frac{P_t}{P_{t-1}} - 1, \qquad r_t = \ln\left(\frac{P_t}{P_{t-1}}\right) = \ln(1 + R_t)$$

Agregación en el tiempo, de $t$ a $t + k$:

$$1 + R_{t \to t+k} = \prod_{i=1}^{k} (1 + R_{t+i}), \qquad r_{t \to t+k} = \sum_{i=1}^{k} r_{t+i}$$

Agregación entre activos con pesos $w_i$ (adelanto del Módulo 2; no vale para logarítmicos):

$$R_p = \sum_{i} w_i\, R_i$$

Para rendimientos pequeños, $r_t \approx R_t$. La media geométrica queda por debajo de la aritmética, aproximadamente:

$$\mu_g \approx \mu_a - \frac{\sigma^2}{2}$$

Anualización de la media y la volatilidad diarias, **suponiendo rendimientos iid**:

$$\mu_A = 252\,\mu, \qquad \sigma_A = \sqrt{252}\,\sigma$$

Tasa de crecimiento anual compuesta con $T$ días de historia:

$$CAGR = \left(\frac{P_T}{P_0}\right)^{252/T} - 1$$

## Riesgo y momentos

La volatilidad $\sigma$ es la medida básica de riesgo; la asimetría y la curtosis dicen qué tanto se aleja la distribución de la normal.

Asimetría ($\gamma_1$) y curtosis ($\kappa$). La normal tiene $\gamma_1 = 0$ y $\kappa = 3$; el exceso de curtosis es $\kappa - 3$, y si es positivo hay colas gruesas:

$$\gamma_1 = \frac{E\big[(X-\mu)^3\big]}{\sigma^3}, \qquad \kappa = \frac{E\big[(X-\mu)^4\big]}{\sigma^4}$$

Regla de la raíz del tiempo. Si los $r_t$ son iid, la varianza de la suma de $h$ días crece linealmente:

$$\operatorname{Var}\left(\sum_{i=1}^{h} r_{t+i}\right) = h\,\sigma^2 \quad \Longrightarrow \quad \sigma_h = \sigma\sqrt{h}$$

El supuesto importa: con autocorrelación o agrupamiento de volatilidad, $\sigma\sqrt{h}$ deja de ser exacta.

**Apéndice reto: prueba de Jarque-Bera.** Bajo normalidad, el estadístico sigue una $\chi^2$ con 2 grados de libertad:

$$JB = \frac{T}{6}\left(\hat{\gamma}_1^{\,2} + \frac{(\hat{\kappa} - 3)^2}{4}\right) \sim \chi^2_2$$

## Series de tiempo

Modelamos los precios como un proceso estocástico $\lbrace X_t \rbrace$. Los precios no son estacionarios y los rendimientos aproximadamente sí; por eso estimamos sobre rendimientos.

Estacionariedad débil: media y varianza constantes, y covarianza que depende solo de la distancia $k$ entre observaciones:

$$E[X_t] = \mu, \qquad \operatorname{Var}(X_t) = \gamma_0 < \infty, \qquad \operatorname{Cov}(X_t, X_{t-k}) = \gamma_k$$

Función de autocorrelación:

$$\rho_k = \frac{\gamma_k}{\gamma_0}$$

Caminata aleatoria del logaritmo del precio, con $\varepsilon_t$ iid de media cero. El precio no es estacionario, pero su diferencia, el rendimiento logarítmico, sí:

$$\ln P_t = \mu + \ln P_{t-1} + \varepsilon_t \quad \Longrightarrow \quad r_t = \mu + \varepsilon_t$$

Volatilidad móvil con ventana de $w$ días: $\hat\sigma_t(w)$ es la desviación estándar de $r_{t-w+1}, \dots, r_t$.

Hechos estilizados de los rendimientos financieros (Cont, 2001):

1. Colas gruesas: exceso de curtosis positivo.
2. Autocorrelación casi nula en $r_t$.
3. Autocorrelación positiva y persistente en $|r_t|$ y $r_t^2$: agrupamiento de volatilidad.
4. Asimetría: las caídas grandes son más frecuentes que las subidas grandes.
5. Normalidad agregada: a horizontes más largos, la distribución se parece más a la normal.

## Medidas de desempeño y riesgo

Todas se calculan sobre un solo activo; la versión de portafolio es del Módulo 2. Recuerda: $L = -r$, así que VaR y CVaR salen positivos.

**Índice de Sharpe**, con $r_f$ la tasa libre de riesgo (CETES 28 días convertida a la misma frecuencia). Bajo iid, el diario se anualiza multiplicando por $\sqrt{252}$:

$$SR = \frac{E[R] - r_f}{\sigma}, \qquad SR_A = \sqrt{252}\; SR_{\text{diario}}$$

**Drawdown** y máximo drawdown: la caída desde el máximo previo.

$$DD_t = \frac{P_t}{\max_{s \le t} P_s} - 1, \qquad MDD = \min_t DD_t$$

**Valor en Riesgo.** El VaR al nivel $\alpha$ es el cuantil $\alpha$ de la pérdida: la pérdida que solo se supera con probabilidad $1 - \alpha$.

$$\operatorname{VaR}_\alpha(L) = \inf\lbrace\, l : P(L > l) \le 1 - \alpha \,\rbrace = q_\alpha(L)$$

**CVaR o Expected Shortfall:** la pérdida promedio cuando ya se rebasó el VaR (para distribuciones continuas).

$$\operatorname{ES}_\alpha(L) = E\big[\, L \mid L \ge \operatorname{VaR}_\alpha(L) \,\big]$$

Los tres métodos del módulo:

| Método | VaR | CVaR | Supuesto clave |
|---|---|---|---|
| Histórico | $-\hat q_{1-\alpha}(r)$, el cuantil empírico | $-$ promedio de los $r_t \le \hat q_{1-\alpha}(r)$ | El pasado representa al futuro |
| Paramétrico normal | $\sigma z_\alpha - \mu$ | $\sigma\,\varphi(z_\alpha)/(1-\alpha) - \mu$ | $r \sim N(\mu, \sigma^2)$ |
| Monte Carlo | Histórico aplicado a $N$ rendimientos simulados | Ídem | El modelo simulado (ver sección siguiente) |

Forma cerrada bajo normalidad:

$$\operatorname{VaR}_\alpha = \sigma z_\alpha - \mu, \qquad \operatorname{ES}_\alpha = \sigma\,\frac{\varphi(z_\alpha)}{1 - \alpha} - \mu$$

A horizonte de $h$ días, bajo iid: $\mu_h = h\mu$ y $\sigma_h = \sigma\sqrt{h}$.

**Medidas coherentes de riesgo (Artzner et al., 1999).** Una medida $\rho$ es coherente si cumple monotonía, homogeneidad positiva, invariancia ante traslaciones y subaditividad:

$$\rho(X + Y) \le \rho(X) + \rho(Y)$$

El VaR no siempre es subaditivo; el CVaR sí. Por eso la regulación bancaria de riesgo de mercado (FRTB de Basilea) pasó del VaR al Expected Shortfall al 97.5%.

Contraejemplo para clase: dos bonos independientes, cada uno con probabilidad 0.04 de perder 100 y 0.96 de perder 0. Con $\alpha = 0.95$, el VaR de cada uno es 0, porque $P(L > 0) = 0.04 \le 0.05$. En el portafolio, $P(\text{al menos un impago}) = 1 - 0.96^2 = 0.0784 > 0.05$, así que $\operatorname{VaR}(X + Y) = 100 > 0 + 0$. Diversificar aumentó el VaR.

**Apéndice reto: backtesting de Kupiec.** Con $x$ excedencias del VaR en $T$ días y $p = 1 - \alpha$, bajo un VaR correcto:

$$LR_{uc} = -2\ln\left[\frac{(1-p)^{T-x}\,p^{x}}{\left(1-\frac{x}{T}\right)^{T-x}\left(\frac{x}{T}\right)^{x}}\right] \sim \chi^2_1$$

## Monte Carlo y movimiento browniano geométrico

Monte Carlo estima una esperanza promediando simulaciones. El error baja como $1/\sqrt{N}$: para tener la mitad de error hay que simular cuatro veces más.

Estimador y su error estándar (ley de los grandes números y teorema central del límite):

$$\hat{\theta}_N = \frac{1}{N}\sum_{i=1}^{N} g\big(X^{(i)}\big) \longrightarrow E[g(X)], \qquad \operatorname{EE}(\hat{\theta}_N) = \frac{\sigma_g}{\sqrt{N}}$$

Movimiento browniano geométrico, con $W_t$ un movimiento browniano estándar:

$$dS_t = \mu\, S_t\, dt + \sigma\, S_t\, dW_t$$

Su solución, que es lo que se programa ($Z \sim N(0, 1)$):

$$S_T = S_0 \exp\left[\left(\mu - \frac{\sigma^2}{2}\right)T + \sigma\sqrt{T}\,Z\right]$$

Por lo tanto, el rendimiento logarítmico al horizonte $T$ es normal:

$$\ln\left(\frac{S_T}{S_0}\right) \sim N\left(\left(\mu - \frac{\sigma^2}{2}\right)T,\; \sigma^2 T\right)$$

Cuidado al calibrar: $\mu$ es la deriva del rendimiento simple. Si estimas la media $\hat\mu_{\log}$ con rendimientos logarítmicos, entonces $\mu = \hat\mu_{\log} + \sigma^2/2$.

VaR por Monte Carlo en cuatro pasos:

1. Estimar $\mu$ y $\sigma$ con datos históricos.
2. Simular $N$ rendimientos al horizonte deseado, **con semilla fija** para que el resultado sea reproducible.
3. Calcular $L = -r$ para cada simulación.
4. Aplicar la fórmula histórica del VaR y del CVaR a las simulaciones.

## De la notación al código

Cada símbolo tiene una traducción directa en pandas, numpy o scipy. Se supone `precios` una Serie de pandas con índice de fechas, `r` los rendimientos, `import numpy as np` y `from scipy.stats import norm`.

| Concepto | Notación | Código |
|---|---|---|
| Rendimiento simple | $R_t$ | `precios.pct_change()` |
| Rendimiento logarítmico | $r_t$ | `np.log(precios).diff()` |
| Producto de (1 + R) | $\prod(1 + R) - 1$ | `(1 + R).prod() - 1` |
| Suma de logarítmicos | $\sum r$ | `r.sum()` |
| Media | $\hat\mu$ | `r.mean()` |
| Volatilidad (divide entre T − 1) | $\hat\sigma$ | `r.std()` |
| Anualización | $252\mu$, $\sqrt{252}\,\sigma$ | `r.mean() * 252`, `r.std() * np.sqrt(252)` |
| Asimetría | $\hat\gamma_1$ | `r.skew()` |
| Exceso de curtosis | $\hat\kappa - 3$ | `r.kurt()` |
| Autocorrelación | $\hat\rho_k$ | `r.autocorr(lag=k)` |
| Volatilidad móvil | $\hat\sigma_t(w)$ | `r.rolling(w).std()` |
| Cuantil empírico | $\hat q_p$ | `r.quantile(p)` |
| Cuantil y densidad normal | $z_p$, $\varphi(z)$ | `norm.ppf(p)`, `norm.pdf(z)` |
| Drawdown | $DD_t$ | `precios / precios.cummax() - 1` |
| Normales simuladas | $Z$ | `np.random.default_rng(semilla).standard_normal(N)` |

Dos trampas frecuentes:

- `np.std` divide entre $T$ por omisión y `pandas.std` entre $T - 1$. Con numpy hay que escribir `np.std(x, ddof=1)`.
- `r.kurt()` en pandas ya regresa el **exceso** de curtosis (0 para la normal), no $\kappa$.
