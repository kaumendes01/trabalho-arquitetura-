# Lanchonete: Padrões de Projeto (Builder, Decorator e Adapter)

Sistema de pedidos em console, em Java, usado para demonstrar 3 padrões de projeto.
A documentação de cada padrão (propósito, motivação, UML, antes/depois) está em `docs/DOCUMENTACAO.md`.

## Três formas de rodar (todas usam as mesmas classes dos padrões)

| Classe | O que é |
|---|---|
| `lanchonete.app.Main` | Console simples |
| `lanchonete.app.MainBonito` | Console decorado (molduras, cores, tela limpa) |
| `lanchonete.app.MainJanela` | Janela gráfica (Swing) |

### Pelo VS Code ou outra IDE
Abra a pasta `lanchonete`, abra o arquivo da classe desejada (em `src/lanchonete/app/`) e clique em **Run**.
A estrutura `src/lanchonete/...` precisa ser mantida, porque os arquivos usam `package lanchonete....`.

### Pelo terminal (precisa do JDK 17 ou superior)

```bash
mkdir out
javac -encoding UTF-8 -d out $(find src -name "*.java")
java -cp out lanchonete.app.MainJanela      # janela
java -cp out lanchonete.app.MainBonito      # console decorado
java -cp out lanchonete.app.Main            # console simples
```

No Windows (cmd):

```
mkdir out
dir /s /b src\*.java > fontes.txt
javac -encoding UTF-8 -d out @fontes.txt
chcp 65001
java -Dfile.encoding=UTF-8 -cp out lanchonete.app.MainJanela
```

Se as cores do `MainBonito` aparecerem como símbolos estranhos, defina a variável de ambiente `NO_COLOR` (ex.: `set NO_COLOR=1`) para desligá-las.

Dica de teste: use o cupom `KAU10` para ganhar 10% de desconto.

## Estrutura

```
src/lanchonete/
  app/        Main.java, MainBonito.java, MainJanela.java   (telas)
  modelo/     Pedido.java                (+ Pedido.Builder)       -> BUILDER
  decorator/  Item, Lanche, ItemDecorator,
              Queijo, Bacon, Molho                                -> DECORATOR
  adapter/    Pagamento, PagamentoPix, PagamentoDinheiro,
              GatewayExterno, PagamentoCartaoAdapter              -> ADAPTER
```
