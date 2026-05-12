🚀 Automação de Offboarding de TI com AWS Step Functions

Este repositório contém a documentação e a arquitetura desenvolvidas para o desafio de projeto "Construindo um Perfil de Destaque na DIO", focado em orquestração de serviços em nuvem.

📌 O Desafio e o Cenário Prático
O objetivo deste laboratório foi consolidar o aprendizado sobre o AWS Step Functions criando um fluxo de trabalho automatizado. 

Para demonstrar a aplicabilidade da ferramenta em cenários reais de infraestrutura e suporte corporativo, desenvolvi uma Automação de Desligamento de Colaboradores (Offboarding). Processos de encerramento de contas exigem precisão para evitar falhas de segurança e perda de dados, tornando a orquestração via Step Functions a solução ideal.

⚙️ Arquitetura do Fluxo (State Machine)
O fluxo foi desenhado utilizando o Workflow Studio e a linguagem de consulta JSONata. A lógica simula a tomada de decisão do suporte técnico de TI durante a revogação de acessos:

1. Início do Desligamento: A máquina de estados é acionada com os dados do colaborador.
2. Tomada de Decisão (Choice): O sistema avalia a variável `$.necessita_backup`.
   - Caminho A (Sim): O fluxo é direcionado para a etapa de backup dos arquivos locais e em nuvem (simulando a transferência para o Amazon S3).
   - Caminho B (Não): O fluxo ignora o backup e segue em frente.
3. Desativação de Acessos: Independentemente do caminho anterior, o fluxo converge para a etapa crítica de desativação da conta, revogando permissões e acessos a sistemas internos.
4. Notificação de Conclusão: Por fim, um e-mail de confirmação é disparado para o RH e a gestão de TI aprovando que o encerramento foi concluído de forma segura (simulando integração com o Amazon SNS).

📸 Diagrama Visual
O AWS Step Functions gera automaticamente um diagrama visual da Máquina de Estados. Abaixo está a arquitetura desenvolvida neste projeto:

> *Nota: A imagem acima está armazenada na pasta `/images` deste repositório.*

💻 Amazon States Language (Código Fonte)
Embora a arquitetura tenha sido construída visualmente, o Step Functions opera sob o capô utilizando JSON. Abaixo está o código gerado que define toda a estrutura de transições e estados (incluindo o bloco `Pass` simulado e a condicional JSONata):

```json
