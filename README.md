# Time Series Classical Seasonal Decomposition

An analytical implementation of classical additive time series decomposition utilizing moving-average trend filtering, seasonal period extraction, and residual noise analysis with Statsmodels.

---

## Objective

Deconstruct an empirical time series into its distinct constituent components: the long-term underlying secular trend ($T$), recurring cyclical seasonality ($S$), and irregular stochastic residual noise ($R$).

---

## Dataset Utilized

- **Dataset Name**: Daily Minimum Temperatures in Melbourne
- **Filename**: `daily-min-temperatures.csv`
- **Domain**: Climatology / Meteorology
- **Temporal Resolution**: Daily records from January 1, 1981 through December 31, 1990 (3,650 time points)
- **Target Variable**: `Temp` (Daily minimum temperature in Celsius, °C)
- **Periodicity ($m$)**: 365 calendar days (annual meteorological seasonal cycle)

*(Note: Prior template documentation erroneously referenced airline passenger volume; the analysis is conducted exclusively on Melbourne daily minimum temperature records.)*

---

## Mathematical Formulation

The classical additive decomposition model assumes the observed value $Y(t)$ is the algebraic sum of independent components:
$$Y(t) = T(t) + S(t) + R(t)$$

### 1. Trend Estimation ($T(t)$)
Estimated using a two-sided symmetric moving average filter of span equal to the seasonal period ($m = 365$):
$$T(t) = \frac{1}{m} \sum_{j=-(m-1)/2}^{(m-1)/2} Y(t+j)$$

### 2. Seasonal Component ($S(t)$)
Computed by averaging the detrended values $Y(t) - T(t)$ for each corresponding calendar day across all 10 sample years and centering around zero:
$$\sum_{j=1}^m S(j) = 0$$

### 3. Residual Irregular Component ($R(t)$)
The remaining unexplained variation after removing trend and seasonality:
$$R(t) = Y(t) - T(t) - S(t)$$

In a well-specified decomposition, $R(t)$ approximates a zero-mean stationary white noise process.

---

## Results & Decomposition Visualizations

### 1. Original Observed Time Series ($Y(t)$)
<img width="1852" height="385" alt="Original Time Series" src="https://github.com/user-attachments/assets/709494ec-bc96-4fe9-9ec3-8a919b270bf6" />

### 2. Extracted Secular Trend ($T(t)$)
<img width="1851" height="380" alt="Extracted Trend Component" src="https://github.com/user-attachments/assets/d350d0a0-1c7e-49cd-9461-d749d31b4026" />

### 3. Annual Seasonal Periodicity ($S(t)$)
<img width="1851" height="377" alt="Extracted Seasonal Component" src="https://github.com/user-attachments/assets/9c7cc77e-15c2-4a76-944a-3d6ed42f7c49" />

### 4. Residual Irregular Fluctuations ($R(t)$)
<img width="1852" height="388" alt="Extracted Residual Noise" src="https://github.com/user-attachments/assets/66115c65-ac50-4055-8856-2861a30e6831" />

---

## License

This project is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.
