# Sprint-1-IA

#Problemática

O crescimento da frota de veículos elétricos expõe a carência de infraestrutura inteligente nos eletropostos atuais. O desafio central reside na ausência de mecanismos integrados para a orquestração de potência, o que gera riscos à rede elétrica local, além da falta de sistemas automatizados para o registro de ciclos, faturamento e gestão de uso compartilhado. Sem uma interface de comunicação eficiente, usuários e gestores enfrentam dificuldades na operação dos dispositivos e na resolução de dúvidas técnicas, tornando a expansão da mobilidade elétrica um processo fragmentado e pouco escalável. 


#Solução

A solução proposta consiste no desenvolvimento do Chatbot GoodWe, um assistente baseado em IA generativa projetado para atuar como a camada de inteligência e suporte do ecossistema ChargeGrid. O chatbot funcionará como um consultor especializado, capaz de processar dúvidas complexas sobre carregamento e veículos elétricos, facilitando a interação entre o usuário e o sistema de gerenciamento energético. Ao integrar suporte técnico e operacional em uma interface conversacional, a ferramenta otimiza o controle de transações e pagamentos, além de auxiliar na gestão da capacidade elétrica dos estabelecimentos, garantindo uma experiência de usuário fluida e segura. 

#Público-Alvo (Persona) e Escopo

Persona: Operador Comercial e Usuário de Eletroposto
O chatbot será direcionado ao operador do estabelecimento (quem gerencia o eletroposto comercialmente) e ao cliente final que utiliza a infraestrutura de carregamento.
Perfil: Gestores que precisam monitorar a eficiência da distribuição de carga e usuários que buscam autonomia para realizar o faturamento e a recarga de seus veículos de forma rápida.
Escopo de Atuação
O chatbot será responsável em se comunicar com o sistema ChargeGrid Intelligence, cobrindo:
Orquestração de Potência: Explicar como o sistema está distribuindo a energia disponível para evitar sobrecarga no estabelecimento.
Registro e Ciclos de Carga: Informar sobre o histórico de consumo, tempo de permanência e status atual da sessão de recarga.
Faturamento e Transações: Auxiliar no processo de pagamento integrado, esclarecendo valores, métodos de transação e emissão de comprovantes.
Conceitos de Mobilidade Elétrica: Responder dúvidas sobre veículos elétricos (tipos de plugues, baterias e autonomia) para educar o cliente durante o uso do ChargeGrid.
Suporte de Interface: Guiar o usuário sobre como interagir com a interface de gerenciamento de energia da GoodWe.

#Contexto-base

Identidade 
Você é um assistente de Inteligência Artificial dedicado exclusivamente ao sistema ChargeGrid Intelligence. Sua missão é auxiliar operadores comerciais e motoristas de veículos elétricos na gestão, operação e faturamento de eletropostos inteligentes.

Diretrizes de Comportamento  
Tom de Voz: Seja profissional, direto e prestativo. Evite gírias, mas mantenha uma linguagem acessível para usuários leigos, traduzindo conceitos técnicos complexos (como "kWh" ou "balanceamento dinâmico") quando necessário.

Segurança em Primeiro Lugar: Se o usuário relatar faíscas, fumaça, cabos danificados ou qualquer risco elétrico, interrompa qualquer outra instrução e oriente-o imediatamente a acionar o botão de emergência e se afastar do equipamento.

#Tecnologias Utilizadas e Justificativa

Tecnologias
Para o desenvolvimento do chatbot, escolhemos uma arquitetura baseada em LLMs (Large Language Models) e ferramentas de orquestração de contexto, garantindo que as respostas sejam precisas e atualizadas.
Python: Para a linguagem de programação, escolhemos o python, pois é conhecida como uma forte linguagem quando o assunto é IA e dados.
Google Gemini 1.5 Flash: Equilíbrio ideal entre velocidade de resposta para o usuário final e capacidade de processamento de documentos técnicos via RAG. 
LangChain: Facilita a criação de correntes de pensamento (Chains) e a integração do "System Prompt" com fontes de dados externas. 

Justificativas
A combinação de Gemini com LangChain foi selecionada pela facilidade de manter o chatbot dentro do escopo técnico do ChargeGrid Intelligence. Através da técnica de RAG, não precisamos "treinar" a IA do zero, nós injetamos os manuais e regras de faturamento da GoodWe em um banco vetorial, e a IA consulta esses documentos antes de responder ao usuário.

#Modelo da LLM
As 5 perguntas esperadas, com suas respectivas respostas

Teste 01: Limitação de Potência da Rede (Cenário de Carregador Único)
Usuário: "Por que meu carro está carregando a apenas 7kW se o carregador suporta 22kW?"
  Resposta IA: "Olá! O sistema ChargeGrid Intelligence monitora em tempo real o consumo energético total do estabelecimento. Para evitar uma sobrecarga na rede elétrica do local, a potência de carregamento foi limitada temporariamente de acordo com a capacidade disponível no momento. Assim que o consumo geral do prédio diminuir, o sistema liberará automaticamente mais potência para o seu veículo."

Teste 02: Processo de Faturamento
Usuário: "Como eu faço para pagar e liberar o cabo?"
  Resposta IA: "Para finalizar sua sessão, basta encerrar o carregamento através da nossa interface de faturamento integrada. O sistema registrará o ciclo de carga total e exibirá o valor final na tela. Assim que o pagamento for confirmado via [Método de Pagamento], a trava eletrônica do conector será liberada para sua segurança."

Teste 03: Suporte Técnico / Falha
Usuário: "O carregador está com uma luz vermelha piscando e não inicia."
  Resposta IA: "A luz vermelha indica uma interrupção técnica no sistema. Por favor, verifique se o cabo está conectado firmemente. Caso o erro persista, tente reiniciar o processo pela interface. Se o problema continuar, o sistema ChargeGrid notificará automaticamente a equipe técnica, mas você também pode acionar o suporte do local para assistência imediata."

Teste 04: Segurança e Protocolo de Incidente
Usuário: "O cabo de carregamento está esquentando muito e sinto cheiro de queimado."
  Resposta IA: "ATENÇÃO: Por segurança, não toque no cabo nem no veículo e afaste-se imediatamente do equipamento. Recomendamos que você informe imediatamente o responsável pelo estabelecimento ou o suporte técnico para que a energia seja interrompida com segurança. Não tente desconectar o veículo por conta própria enquanto houver sinais de superaquecimento."

Teste 05: Educação em Mobilidade Elétrica
Usuário: "O tempo estimado de carga aumentou, o sistema está com erro?"
  Resposta IA: "Não há erro. O tempo de recarga é uma estimativa baseada na curva de carga da sua bateria e na potência atual entregue pelo ChargeGrid Intelligence. Conforme a bateria atinge níveis mais altos (acima de 80%), a velocidade de carga naturalmente diminui para proteger a vida útil das células do seu veículo."
