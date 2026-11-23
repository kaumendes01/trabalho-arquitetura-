# Sistema de Pedidos para Lanchonete (Java + Swing)

Aplicação desktop desenvolvida em Java para gerenciamento completo de pedidos de uma lanchonete, aplicando na prática três padrões de projeto do catálogo **GoF (Gang of Four)**.

- **Aluno:** Kauã Foscarini
- **Curso:** Tecnologia em Análise e Desenvolvimento de Sistemas (TADS) — Univel
- **Disciplinas:** Arquitetura de Software (Prof. Eder) & Programação Orientada a Objetos (Prof.ª Célia)

---

## Funcionalidades

- **Montagem de Lanches:** Escolha entre **Hambúrguer** (R$ 20,00) ou **Hot-dog** (R$ 15,00) com adicionais dinâmicos (**Queijo** +R$ 3,00, **Bacon** +R$ 5,00, **Molho Especial** +R$ 2,00) e cálculo de preço em tempo real.
- **Criação e Validação de Pedidos:** Preenchimento de dados obrigatórios (cliente, itens, pagamento) e opcionais (endereço de entrega, observação e cupom de desconto `KAU10` de 10%).
- **Meios de Pagamento:** Cobrança via **Pix**, **Dinheiro** ou **Cartão** (integrado a um gateway externo simulado).
- **Ciclo de Vida e Status do Pedido:** Acompanhamento e transição de estados do pedido diretamente na interface (`ATIVO`, `Aguardando retirada`, `Em rota`, `Concluído` e `Cancelado`), com destaque visual por cor e validação de regras de negócio.

---

## Padrões de Projeto Aplicados

| Padrão | Categoria | Onde foi aplicado |
| :--- | :--- | :--- |
| **Decorator** | Estrutural | Empilhamento dinâmico de adicionais (`Queijo`, `Bacon`, `Molho`) sobre o `Lanche` em `MainJanela.montarLancheAtual()`. |
| **Builder** | Criacional | Construção passo a passo, imutável e validada do `Pedido` via `Pedido.Builder` em `MainJanela.finalizarPedido()`. |
| **Adapter** | Estrutural | Adaptação da classe externa `GatewayExterno` para a interface `Pagamento` via `PagamentoCartaoAdapter`. |

> A explicação completa, motivação (*Antes vs. Depois*), detalhes técnicos e todos os diagramas UML estão em **[`docs/DOCUMENTACAO.md`](docs/DOCUMENTACAO.md)**.

---

## Estrutura do Projeto

```text
├── docs/
│   └── DOCUMENTACAO.md          # Documentação detalhada e diagramas UML
├── README.md                    # Visão geral e instruções de execução
└── src/lanchonete/
    ├── adapter/                 # Pagamento, PagamentoPix, PagamentoDinheiro, PagamentoCartaoAdapter, GatewayExterno
    ├── app/                     # MainJanela (interface Swing) e classes Main
    ├── decorator/               # Item, Lanche, ItemDecorator, Queijo, Bacon, Molho
    └── modelo/                  # Pedido e Pedido.Builder
```
