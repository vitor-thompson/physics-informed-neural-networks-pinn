# Experimento 03 — Pêndulo Simples Não-Linear (Grandes Ângulos)

Notebook principal: [`passo_03_pendulo_nao_linear.ipynb`](./passo_03_pendulo_nao_linear.ipynb)

## Objetivo
Resolver a equação diferencial ordinária não-linear do pêndulo simples sem atrito no regime de grandes ângulos usando uma Rede Neural Informada por Física (`SirenPINN`), imposição exata das condições iniciais por construção (*hard constraints*) e otimização com **L-BFGS** (`strong_wolfe`).

## Formulação Física
$$\frac{d^2\theta}{dt^2} + \frac{g}{L}\sin(\theta(t)) = 0, \qquad \theta(0) = \theta_0, \qquad \left.\frac{d\theta}{dt}\right|_{t=0} = \omega_{\text{init}}$$

* **Condições iniciais exatas:** impostas diretamente pelo *ansatz* `get_exact_pendulum_prediction`, dispensando termos de penalidade para $t = 0$.
* **Função de perda:** média dos quadrados do resíduo da EDO (`exact_ic_pendulum_loss`) calculada via `torch.autograd.grad`.
* **Validação:** comparação com solução numérica de alta precisão via `scipy.integrate.solve_ivp` (`RK45`) e contraste com a aproximação linear ($\sin\theta \approx \theta$).

## Parâmetros Padrão
* `g = 9.81` m/s²
* `L = 2.4525` m ($\frac{g}{L} \approx 4{,}0\text{ s}^{-2}$)
* `theta_0 = 1.5` rad
* `omega_init = 0.0` rad/s
* `t_max = 10.0` s
