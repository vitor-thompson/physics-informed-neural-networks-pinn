# Passo 02 — Oscilador Harmônico Simples (`SirenPINN`)

Resolução da equação diferencial ordinária de 2ª ordem do **Oscilador Harmônico Simples** (sistema massa-mola sem atrito) usando uma **Physics-Informed Neural Network** com ativações sinusoidais (`SirenPINN`) e condições iniciais exatas por construção.

## Problema físico

$$\frac{d^2x}{dt^2} + \omega_0^2 x = 0, \qquad \omega_0 = \sqrt{\frac{k}{m}}$$

com condições iniciais em $t = 0$:

$$x(0) = x_0, \qquad \frac{dx}{dt}(0) = v_0$$

Parâmetros padrão do experimento: $m = 1{,}0\text{ kg}$, $k = 4{,}0\text{ N/m}$ ($\omega_0 = 2{,}0\text{ rad/s}$), $x_0 = 1{,}0\text{ m}$, $v_0 = 0{,}0\text{ m/s}$ e intervalo $t \in [0, 10{,}0]\text{ s}$.

## Abordagem adotada

* **Arquitetura (`SirenPINN`):** rede neural com ativações senoidais (`SinActivation`), adequada para funções oscilatórias e derivadas suaves.
* **Condições iniciais exatas (*ansatz*):** $x(t) = x_0 + v_0 t + (1 - e^{-t^2})\,\text{NN}(t)$, garantindo $x(0) = x_0$ e $\dot{x}(0) = v_0$ sem termo de penalidade extra na função de perda.
* **Função de perda e otimização:** perda baseada apenas no resíduo da EDO via diferenciação automática (`torch.autograd.grad`), amostrada dinamicamente em $1000$ pontos de colocação por passo externo e otimizada com `L-BFGS` (`line_search_fn="strong_wolfe"`).

## Conteúdo da pasta

* `passo-02-oscilador-harmonico.ipynb`: notebook completo com formulação teórica, treinamento, comparação com a solução analítica, acompanhamento da convergência e animação da evolução por época.
