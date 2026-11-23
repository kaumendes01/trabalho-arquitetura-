# Sistema de Pedidos para Lanchonete (Java + Swing)

Aplicação desktop desenvolvida em Java para gerenciamento de pedidos de uma lanchonete, aplicando na prática três padrões de projeto do catálogo **GoF (Gang of Four)**.

- **Aluno:** Kauã Foscarini Mendes
- **Curso:** Tecnologia em Análise e Desenvolvimento de Sistemas (TADS) — Univel
- **Disciplinas:** Arquitetura de Software (Prof. Eder) & Programação Orientada a Objetos (Prof.ª Célia)

---

## Funcionalidades

- Montagem de lanches base (**Hambúrguer** R$ 20,00 ou **Hot-dog** R$ 15,00) com adicionais dinâmicos (**Queijo** +R$ 3,00, **Bacon** +R$ 5,00, **Molho Especial** +R$ 2,00).
- Criação de pedidos com validação de campos obrigatórios e suporte a dados opcionais (endereço de entrega, observação e cupom de desconto `KAU10` de 10%).
- Processamento de pagamentos via **Pix**, **Dinheiro** ou **Cartão** (integrado a um gateway externo simulado).
- Listagem, visualização de detalhes e cancelamento de pedidos (`ATIVO` / `CANCELADO`).

---

## Padrões de Projeto Aplicados

| Padrão | Categoria | Onde foi aplicado |
| :--- | :--- | :--- |
| **Decorator** | Estrutural | Empilhamento dinâmico de adicionais (`Queijo`, `Bacon`, `Molho`) sobre o `Lanche`. |
| **Builder** | Criacional | Construção passo a passo, imutável e validada do `Pedido` via `Pedido.Builder`. |
| **Adapter** | Estrutural | Adaptação da classe externa `GatewayExterno` para a interface `Pagamento` via `PagamentoCartaoAdapter`. |

> A explicação completa, motivação (*Antes vs. Depois*) e todos os diagramas UML estão em **[`docs/DOCUMENTACAO.md`](docs/DOCUMENTACAO.md)**.

---

## Estrutura do Projeto

```text
├── docs/
│   └── DOCUMENTACAO.md          # Documentação detalhada e diagramas UML
└── src/lanchonete/
    ├── adapter/                 # Pagamento, PagamentoPix, PagamentoDinheiro, PagamentoCartaoAdapter, GatewayExterno
    ├── app/                     # MainJanela (interface Swing)
    ├── decorator/               # Item, Lanche, ItemDecorator, Queijo, Bacon, Molho
    └── modelo/                  # Pedido e Pedido.Builder
