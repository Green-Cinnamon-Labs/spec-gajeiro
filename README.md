# spec-gajeiro

> O gajeiro era o marinheiro que subia ao cesto da gávea, no alto do mastro, para vigiar o horizonte e avisar o comando do que via.

Linha de pesquisa do [Green Cinnamon Labs](https://github.com/Green-Cinnamon-Labs) sobre supervisão industrial com Kubernetes. É também o meu caso de estudo para me aprofundar em Kubernetes.

## O que sei hoje

- Quero me aprofundar em Kubernetes, usando o gajeiro como caso de estudo.
- A primeira implementação usou a [planta compartilhada do Tennessee Eastman](https://github.com/Green-Cinnamon-Labs/spec-tennessee-eastman).
- A produção científica (TCC, artigos, plano do mestrado) fica em [`Batchuka/gajeiro-research`](https://github.com/Batchuka/gajeiro-research).

Isto muda conforme eu avanço.

## A ideia

A pergunta de fundo é o que uma implementação precisa demonstrar para que se possa dizer que uma planta está sob supervisão industrial baseada em Kubernetes. A resposta pretendida é uma especificação de arquitetura e de requisitos: quais componentes devem existir, quais recursos do Kubernetes representam a planta e sua política de operação, como os componentes conversam e que comportamentos precisam ser verificados. O Kubernetes é a base que coordena; a especificação diz o que conta como supervisão.

A especificação se organiza em capacidades verificáveis. Uma implementação pode atender só parte delas, e o que ela demonstrou fica registrado.

| Capacidade | O que precisa demonstrar | Situação |
| --- | --- | --- |
| Observar a operação | O supervisor recebe dados suficientes e atualizados para comparar a planta com a política declarada. | Demonstrada no TEP, no TCC, com um historiador entre a planta e o Kubernetes. |
| Avaliar e executar mudanças | Uma alteração na declaração inicia um procedimento: preparar o gêmeo digital, testar a mudança, avaliar critérios, autorizar ou recusar, aplicar e verificar a resposta da planta, inclusive quando o resultado é inconclusivo ou algo falha. | Proposta, no [plano do mestrado](https://github.com/Batchuka/gajeiro-research/tree/main/plano-pos). Hoje o supervisor só observa. |
| Gerir dispositivos e versões | Manter o inventário dos dispositivos, as versões de software e configuração e o histórico das alterações, separando o estado declarado do encontrado. | Proposta. |
| Integrar por OPC UA | Definir como os equipamentos expõem dados e comandos, com identificação, permissões e tratamento de falhas de comunicação. | Leitura demonstrada no TEP. Escrita, permissões e falhas de comunicação ainda não foram avaliadas. |

## Repositórios

| Repositório | Papel |
| --- | --- |
| [`plant-supervisor`](https://github.com/Green-Cinnamon-Labs/plant-supervisor) | O supervisor: controlador Kubernetes em Go que avalia a planta contra a política declarada |
| [`tep-lab`](https://github.com/Green-Cinnamon-Labs/tep-lab) | Como rodar o laboratório (Docker Compose + Kind) e o registro do que foi rodado |
| [`tep-historian`](https://github.com/Green-Cinnamon-Labs/tep-historian) | Historiador entre a planta e o Kubernetes (também serve o [Hefesto](https://github.com/Green-Cinnamon-Labs/spec-hefesto)) |

## Livro

[`book/`](book/)
