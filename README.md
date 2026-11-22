# ⚛️ Physics-Informed Neural Networks (PINNs)

Repositório dedicado ao estudo prático e à evolução de **Physics-Informed Neural Networks (PINNs)**, unindo redes neurais às leis físicas diretamente na função de perda (*loss function*).

---

## 📂 Organização do Projeto

* **`course-baseline/`**: Código base desenvolvido durante o curso *Building a Physics-Informed Neural Network for Real-World App*.
* **`experiments/`**: Modificações, testes e novas aplicações físicas implementadas após o curso.
* **`docs/`**: Explicações conceituais e passo a passo das equações, da *loss* física e dos resultados.

---

### 🧪 Histórico de Evolução
- **[v0.1 — Base do Curso]**: Implementação inicial de referência (difusão 1D) adaptada do material base.
- **[v0.2 — Passo 01 (`experiments/passo-01-resfriamento-newton/`)**: Adaptação completa para a Lei do Resfriamento de Newton (EDO de 1ª ordem), incluindo arquitetura `PINNResfriamento`, perda física via `autograd` + condição inicial, comparação com a solução analítica e animação ao longo das épocas.
- **[v0.3 — Passo 02 (`experiments/passo-02-oscilador-harmonico/`)**: Resolução do Oscilador Harmônico Simples (EDO de 2ª ordem) com `SirenPINN` (ativações sinusoidais), *ansatz* de condições iniciais exatas por construção, otimização com `L-BFGS` e amostragem dinâmica de pontos de colocação, avaliação analítica e animação da evolução por época.
- **[Em breve]**: Próximos passos da trilha com novas modificações na arquitetura, ajustes na *loss function* e experimentos com novos sistemas físicos e EDPs.
