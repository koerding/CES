# 2-Nest Economic Model Mathematical Specification

## Model Structure

The economy has a nested CES (Constant Elasticity of Substitution) structure with two production nests:
- **P-nest**: Physical production combining capital and labor
- **I-nest**: Intelligence production combining AI and labor

## Production Functions

### P-nest (Physical Production)
$$P = \left[\alpha_P K_P^{\rho_P} + (1-\alpha_P) L_P^{\rho_P}\right]^{1/\rho_P}$$

Where:
- $K_P$: Physical capital
- $L_P$: Labor allocated to physical production
- $\alpha_P$: Capital share parameter (0 ≤ α_P ≤ 1)
- $\rho_P$: Substitution parameter for P-nest
- Elasticity of substitution: $\sigma_P = 1/(1-\rho_P)$

### I-nest (Intelligence Production)
$$I = \left[\alpha_I^{1-\rho_I} K_I^{\rho_I} + (1-\alpha_I)^{1-\rho_I} L_I^{\rho_I}\right]^{\theta_I/\rho_I}$$

Where:
- $K_I$: AI capital
- $L_I$: Labor allocated to intelligence production
- $\alpha_I$: AI share parameter (0 ≤ α_I ≤ 1)
- $\rho_I$: Substitution parameter for I-nest
- $\theta_I$: Returns to scale parameter (θ_I < 1 for decreasing returns)
- Elasticity of substitution: $\sigma_I = 1/(1-\rho_I)$

### Top-Level Aggregation

#### CES Aggregation
$$Y = \left[\tau P^{\rho} + (1-\tau) I^{\rho}\right]^{1/\rho}$$

Where:
- $\tau$: Weight of physical production (0 ≤ τ ≤ 1)
- $\rho$: Top-level substitution parameter
- Elasticity of substitution: $\sigma = 1/(1-\rho)$

#### PSI Aggregation
$$Y = P \cdot \frac{(I/P)^{\eta}}{a + (I/P)^{\eta}}$$

Where:
- $\eta$: S-curve shape parameter (typically negative)
- $a$: Transition point parameter (determines when I dominates P)

## Labor Allocation

Total labor constraint:
$$L = L_P + L_I$$

Define labor allocation shares:
- $\alpha_P$: Share of labor in P-nest ($L_P = \alpha_P L$)
- $(1-\alpha_P)$: Share of labor in I-nest ($L_I = (1-\alpha_P) L$)

## Equilibrium Conditions

### Marginal Products

#### P-nest Labor Marginal Product
$$MP_P = \frac{\partial Y}{\partial P} \cdot \frac{\partial P}{\partial L_P}$$

Where:
$$\frac{\partial P}{\partial L_P} = (1-\alpha_P) L_P^{\rho_P-1} \left[\alpha_P K_P^{\rho_P} + (1-\alpha_P) L_P^{\rho_P}\right]^{(1/\rho_P)-1}$$

#### I-nest Labor Marginal Product
$$MP_I = \frac{\partial Y}{\partial I} \cdot \frac{\partial I}{\partial L_I}$$

Where:
$$\frac{\partial I}{\partial L_I} = \theta_I (1-\alpha_I)^{1-\rho_I} L_I^{\rho_I-1} \left[\alpha_I^{1-\rho_I} K_I^{\rho_I} + (1-\alpha_I)^{1-\rho_I} L_I^{\rho_I}\right]^{(\theta_I/\rho_I)-1}$$

### Top-Level Derivatives

#### CES Case
$$\frac{\partial Y}{\partial P} = \tau P^{\rho-1} \left[\tau P^{\rho} + (1-\tau) I^{\rho}\right]^{(1/\rho)-1}$$

$$\frac{\partial Y}{\partial I} = (1-\tau) I^{\rho-1} \left[\tau P^{\rho} + (1-\tau) I^{\rho}\right]^{(1/\rho)-1}$$

#### PSI Case
Let $x = I/P$ and $\sigma(x) = \frac{x^{\eta}}{a + x^{\eta}}$

$$\frac{\partial Y}{\partial P} = \sigma(x) - x \cdot \sigma'(x)$$

$$\frac{\partial Y}{\partial I} = \sigma'(x)$$

Where:
$$\sigma'(x) = \frac{a \eta x^{\eta-1}}{(a + x^{\eta})^2}$$

### Labor Market Equilibrium

In equilibrium, labor marginal products must equalize:
$$MP_P(\alpha_P^*) = MP_I(\alpha_P^*)$$

This determines the optimal labor allocation $\alpha_P^*$.

### Wage Determination

The equilibrium wage equals the common marginal product:
$$w = MP_P(\alpha_P^*) = MP_I(\alpha_P^*)$$

## Parameter Interpretations

### Substitution Parameters
- $\rho \to 1$: Inputs are perfect substitutes ($\sigma \to \infty$)
- $\rho = 0$: Cobb-Douglas case ($\sigma = 1$)
- $\rho \to -\infty$: Inputs are perfect complements ($\sigma \to 0$)

### Share Parameters
- $\alpha_P = 0$: Only labor matters in P-nest
- $\alpha_P = 1$: Only capital matters in P-nest
- $\alpha_I = 0$: Only labor matters in I-nest
- $\alpha_I = 1$: Only AI matters in I-nest

### Returns to Scale
- $\theta_I = 1$: Constant returns to scale in I-nest
- $\theta_I < 1$: Decreasing returns to scale (e.g., $\theta_I = 0.5$ means doubling inputs increases output by $\sqrt{2} - 1 \approx 41\%$)

### PSI Parameters
- $\eta < 0$: Sharper transition between P and I dominance
- $a$: Higher values mean I-nest needs higher relative productivity to dominate

## Calibration

Default parameter values are calibrated to match:
- US capital share: ~42% (achieved with $\alpha_P = 0.7$ given $K_P/L$ ratio)
- Manufacturing elasticity: $\sigma_P \approx 0.6$ (implies $\rho_P \approx -0.67$)
- Manual occupation share: ~18% (implies $\tau = 0.18$)
- AI-labor substitutability: $\sigma_I \approx 2.2$ (implies $\rho_I \approx 0.55$)