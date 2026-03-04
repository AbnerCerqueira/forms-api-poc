# Objetivo do Projeto

O projeto tem como objetivo ampliar meus conhecimentos em qualidade de software. Neste foi desenvolvido um sistema de formulários, no qual formulários podem ser criados e publicados para receber respostas.

Mais do que apenas implementar funcionalidades, o foco é aplicar conceitos de engenharia de software e avaliar como eles impactam a evolução do sistema ao longo do tempo.

# Para que serve qualidade de software?

A qualidade de software tem como objetivo assegurar que o sistema

- Atenda aos requisitos funcionais, não funcionais e regras de negócio
- Seja manutenível, escalável e testável
- Tenha baixo custo de manutenção futura

Norma amplamente citada na engenharia de software **ISO/IEC-25010**, que define um modelo de qualidade composto por diversas características, como desempenho, confiabilidade, usabilidade, segurança e manutenibilidade.

![iso-25010](./assets/iso-25010.png)

Uma forma intuitiva de entender a ISO/IEC-25010 é compará-la ao selo de uma geladeira.

Quando você compra uma geladeira, ela não é avaliada apenas por gelar. Existem diversos critérios que você utiliza para mensurar a qualidade do produto com por exemplo a eficiência energética, durabilidade, nível de ruído, capacidade interna, etc.

A norma faz exatamente isso com software. Ela define um conjunto de características para que funcionam como um "selo de qualidade"

Exemplos:

- **Desempenho**: como o sistema lida com múltiplos usuários? -> como a geladeira gela rápido mantendo estabilidade térmica?
- **Manutenibilidade**: consigo alterar uma regra de negócio sem quebrar o resto do sistema? -> como trocar uma peça da geladeira sem desmontar tudo?

![selo-geladeira](./assets/selo-procel.png)

# Para que servem testes de software?

Os testes existem para reduzir incerteza. Verifica se o sistema se comporta como esperado e ajuda a identificar defeitos antes de chegar ao usuário final.

Os testes ajudam a

- Validar requisitos
- Proteger o sistema contra regressões
- Aumenta confiança para manutenção
- Reduz custo para correções no futuro

A relação entre qualidade e testes é direta. Se a qualidade busca garantir alinhamento aos requisitos e sustentabilidade do sistema ao longo do tempo, os testes são um dos principais mecanismos para mensurar e preservar essa qualidade continuamente.

Alguns tipos de testes

- **Unitários**: valida pequenas partes do sistema isoladamente
- **Interação**: verifica se 2 ou mais componentes funcionam juntos corretamente
- **End to end**: avalia o comportamento a aplicação como um todo

# Técnicas antes de chegar no código

A software não é somente um pedaço de código que faz algo, software é um conjunto de artefatos que servem para atender uma dor do usuário. Antes da implantação existem uma série de técnicas aplicadas, e no contexto ágil, elas ocorrem de forma incremental.

## Engenharia de requisitos

- Casos de uso
- Histórias de usuário
- Prototipação

Evita ambiguidade e inconsistência.

## Modelagem

- Diagrama de classes
- Diagrama de casos de uso

Serve para avaliar arquitetura e identificar falhas conceituais. Utiliza bastante linguagem UML.

## Revisão

- Peer review
- Walkthrough
- Fagan Inspection

Removem defeitos antes de chegar no código. São métodos de análise aplicados a requisitos e modelos.

## Análise de riscos

- Identificação de riscos técnicos
- Avaliação do impacto
- Planejamento de mitigação

Auxilia na definição da estratégia de testes futura, os esforços precisam ser direcionados onde a falha é critica

# Implementação

Neste repositório estou aplicando os conceitos usando um sistema de formulários. Com o objetivo de estudo com clareza e com foco no conceito, é um sistema sem login de usuário e sem regras rígidas para agilizar o código de exemplo

## Requisitos funcionais (RF)
| ID | Título | Descrição |
| :---- | :---- | :---- |
| **RF-01** | Criar formulário | O sistema deve permitir que formulários sejam criados em estado DRAFT. |
| **RF-02** | Adicionar campos ao formulário | O sistema deve permitir adicionar novos campos ao formulário enquanto este estiver em estado DRAFT. |
| **RF-03** | Publicar formulário PUBLISHED | O sistema deve permitir que formulários sejam publicados |
| **RF-04** | Submeter respostas ao formulário | O sistema deve permitir que formulários sejam preenchidos e submetidos. |
| **RF-05** | Listar respostas de um formulários | O sistema deve permitir que as respostas dos formulários sejam visualizadas. |
| **RF-06** | Fechar formulário CLOSED | O sistema deve permitir que o formulário seja encerrado |
| **RF-07** | Impedir submissões após fechamento | O sistema deve impedir submissões quando o formulário estiver CLOSED |

## Regras de negócio (RN)
| ID | Título | Descrição |
| :---- | :---- | :---- |
| **RN-01** | Edição de formulário | Apenas formulários com status DRAFT podem ser modificados. |
| **RN-02** | Submissão de respostas | Apenas formulários com status PUBLISHED podem receber respostas |
| **RN-03** | Após fechar formulário | Formulários com status CLOSED não podem ser abertos novamente |
| **RN-04** | Campos obrigatórios | Campos obrigatórios precisam estar sempre presentes na submissão |
| **RN-05** | Campos numéricos | Campos numéricos devem respeitar o mínimo e máximo definidos |
| **RN-06** | Campos select | Campos do tipo select devem aceitar apenas valores pré-definidos |
| **RN-07** | Quantidade de campos | Formulários devem ter no mínimo 1 campo e no máximo 100 |
| **RN-08** | Integridade das respostas | Submissões de respostas devem conter somente campos que existem no formulário |
| **RN-09** | Duplicatas de campos | Não devem existir campos iguais dentro do mesmo formulário |

## Requisitos não funcionais (RNF)
| ID | Título | Descrição |
| :---- | :---- | :---- |
| **RNF-01** | Paginação | Os endpoints de GET devem ter opção para paginação das respostas |


## Modelo C4
Para documentar a arquitetura de forma clara, adotei o modelo C4.

### Nível 4 - Código
![c4-codigo](./assets/c4-codigo.png)
