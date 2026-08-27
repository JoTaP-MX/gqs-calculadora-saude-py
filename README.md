# 🩺 Calculadora de Saúde

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![License](https://img.shields.io/badge/Licença-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Corrigido-success?style=for-the-badge)

Um sistema em Python que calcula indicadores de saúde e bem-estar — **IMC**, **recomendação diária de água** e **frequência cardíaca máxima** — direto pelo terminal! 💪

> [!NOTE]
> Este projeto foi desenvolvido como atividade prática (Lista de Exercícios IV) da disciplina de **Garantia da Qualidade de Software**, com foco em identificação e correção de bugs em código legado.

---

## 📖 O que o código faz?

O programa exibe um menu com 4 opções e realiza os seguintes cálculos, a partir de dados informados pelo usuário:

| Opção | Cálculo | Fórmula usada |
|---|---|---|
| 1️⃣ | IMC (Índice de Massa Corporal) | `peso / (altura ** 2)` |
| 2️⃣ | Recomendação diária de água | `(peso × 35) / 1000` litros |
| 3️⃣ | Frequência cardíaca máxima | `220 - idade` |
| 4️⃣ | Sair do sistema | — |

---

## 🐛 Relatório de Bugs Encontrados

O repositório original continha **7 bugs**, identificados através de testes manuais em cada opção do menu:

| # | Local do Bug (função) | Comportamento Incorreto Observado | Solução Aplicada |
|:---:|---|---|---|
| 1 | `calcular_imc()` | Usava `altura * 2` (multiplicação) em vez de `altura ** 2` (potenciação), gerando um IMC completamente errado | Corrigido para `peso / (altura ** 2)` |
| 2 | `classificar_imc()` | Faixas com `>` e `<` deixavam "buracos": valores exatos como `18.5` ou `25.0` não se enquadravam em nenhuma condição e a função retornava `None` | Reescrito com `<=` e um `else` final, cobrindo todos os valores possíveis |
| 3 | `calcular_agua_diaria()` | Dividia o peso por 35 em vez de multiplicar, resultando em uma recomendação de água absurdamente baixa | Corrigido para `(peso * 35) / 1000`, convertendo o resultado para litros |
| 4 | `calcular_frequencia_cardiaca_maxima()` | Somava a idade a 220 em vez de subtrair, gerando um valor de FC máxima maior que o real | Corrigido para `220 - idade` |
| 5 | `menu()` | `input()` sempre retorna texto (string), mas o valor era comparado como número inteiro no `main()` | Adicionada conversão com `int()` dentro do próprio `menu()`, com tratamento de erro |
| 6 | `main()` | Consequência direta do Bug 5: `opcao == 1` nunca era verdadeiro, pois `opcao` era `"1"` (string) e não `1` (número) — nenhuma opção do menu funcionava | Resolvido junto com a correção do Bug 5 |
| 7 | `main()` (opção Sair) | Faltava o comando `break`, fazendo o programa entrar em loop infinito mesmo após escolher "Sair" | Adicionado `break` para encerrar o laço corretamente |

> [!IMPORTANT]
> Além dos bugs listados, foi adicionado tratamento de erro (`try/except`) na leitura do menu, para o programa não travar caso o usuário digite algo que não seja um número.

---

## 🚀 Como executar

### Pré-requisitos

![Python](https://img.shields.io/badge/Requer-Python%203.6+-blue?style=flat-square)

Você precisa ter o [Python 3](https://www.python.org/downloads/) instalado. Para conferir sua versão:

```bash
python --version
```

### Instalação

```bash
git clone https://github.com/JoTaP-MX/gqs-calculadora-saude-py.git
cd gqs-calculadora-saude-py
```

### Executando

```bash
python calculadora_saude.py
```

---

## 🧪 Exemplo de saída

==============================
SISTEMA DE SAÚDE E BEM-ESTAR
Calcular IMC
Calcular Recomendação de Água
Calcular Frequência Cardíaca Máxima
Sair
Escolha uma opção (1-4): 1
Digite seu peso (kg): 70
Digite sua altura (m): 1.75
Seu IMC é: 22.86
Classificação: Peso normal


| Cálculo | Entrada | Saída |
|---|---|:---:|
| IMC | `peso=70, altura=1.75` | `22.86` (Peso normal) |
| Água diária | `peso=70` | `2.45 Litros` |
| FC máxima | `idade=30` | `190 bpm` |

---

## 🛠️ Tecnologias utilizadas

- 🐍 **Python 3**
- Nenhuma biblioteca externa — apenas recursos nativos da linguagem

---

## 👤 Sobre o Autor

Feito com 💻 por **Daniel Paiva** (código original) — bugs corrigidos e documentação escrita como atividade prática.

---

## 📄 Licença

Este projeto está sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
