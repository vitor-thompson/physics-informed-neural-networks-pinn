# Passo 01 — Lei do Resfriamento de Newton (PINN)

Primeiro experimento da trilha de *Physics-Informed Neural Networks* (PINNs), aplicando diferenciação automática (`autograd`) a uma EDO de 1ª ordem dependente do tempo.

## Caminho no Repositório
- **Pasta do experimento:** `experiments/passo-01-resfriamento-newton/`
- **Notebook:** `experiments/passo-01-resfriamento-newton/passo_01_resfriamento_newton.ipynb`

## Equação Governante
$$\frac{dT}{dt} = -k(T - T_{\text{amb}}), \quad T(0) = T_0$$

Resíduo físico minimizado no treinamento:
$$r(t) = \frac{dT}{dt} + k\left(T(t) - T_{\text{amb}}\right)$$

## O que é feito no notebook
- **Arquitetura (`PINNResfriamento`):** recebe o tempo $t$ como entrada, passa por camadas densas com ativação `Tanh` e retorna a temperatura prevista $T(t)$.
- **Função de perda (`pinn_loss`):** combina o erro quadrático médio do resíduo da EDO com a perda da condição inicial em $t = 0$.
- **Treinamento (`train`):** otimização com `Adam` ao longo das épocas com salvamento dos estados do modelo.
- **Validação e visualização:** comparação com a solução analítica $T(t) = T_{\text{amb}} + (T_0 - T_{\text{amb}})e^{-kt}$, análise de convergência e animação da evolução do treinamento.
