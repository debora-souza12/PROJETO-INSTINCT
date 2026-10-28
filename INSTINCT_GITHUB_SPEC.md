# INSTINCT --- Especificação de Produto e Instruções de Implementação

> Documento de referência para GitHub Copilot / agente de programação.
> Objetivo: implementar o aplicativo INSTINCT de forma incremental,
> funcional, responsiva e segura. Idioma da interface: português
> brasileiro (pt-BR).

## Instrução principal para o agente

Leia este documento antes de alterar o projeto. Primeiro inspecione a
estrutura existente, o framework, os scripts, a branch atual, os
componentes e as integrações configuradas. Preserve o histórico e as
integrações existentes, especialmente com o Lovable. Não substitua a
arquitetura nem reescreva o projeto inteiro sem necessidade.

Implemente em pequenas etapas verificáveis. Não crie apenas telas
estáticas: formulários, botões, checklists, filtros, temporizadores,
cálculos e gráficos devem funcionar. Não afirme que testes, integrações
ou funcionalidades foram concluídos sem verificar.

## Comandos de trabalho

Execute os comandos adequados ao projeto existente. Não presuma que ele
usa uma ferramenta específica antes de verificar os arquivos.

``` bash
# 1. Inspecionar o projeto
pwd
git status --short --branch
git log -5 --oneline
git ls-files | head -200

# 2. Identificar framework e scripts
cat package.json

# 3. Instalar dependências usando o gerenciador indicado pelo lockfile
# npm:
npm install
# ou pnpm:
pnpm install
# ou yarn:
yarn install

# 4. Executar os scripts realmente definidos no package.json
npm run
# Depois, quando existirem:
npm run lint
npm run typecheck
npm test
npm run build
```

Use o gerenciador correspondente ao lockfile (`package-lock.json`,
`pnpm-lock.yaml` ou `yarn.lock`). Não crie scripts inexistentes sem
configurá-los. Se algum comando não existir ou falhar, informe o motivo
real.

## Produto e objetivo

INSTINCT é um aplicativo de evolução pessoal, voltado principalmente
para mulheres. Deve ajudar a organizar rotina, desenvolver hábitos,
acompanhar atividade física, alimentação, leitura, foco, finanças e
autoconhecimento.

O diferencial central é um planejador que usa compromissos,
deslocamentos, preferências e duração das atividades para sugerir
oportunidades realistas ao longo do dia.

## Identidade visual

-   Visual sofisticado, moderno, minimalista, elegante e acolhedor.
-   Tipografia contemporânea e refinada.
-   Paleta sugerida: off-white, areia, verde-oliva, grafite e preto
    suave.
-   Espaçamento generoso, cartões discretos, bordas suaves e ícones
    consistentes.
-   Evitar excesso de cores, aparência infantil, telas poluídas e botões
    sem ação.
-   Priorizar mobile-first e suportar tablets e desktop.
-   Manter consistência de tipografia, componentes, espaçamento e
    estados visuais.
-   Informações de saúde, peso e finanças não devem ser expostas
    desnecessariamente.

## Navegação principal

Criar estas áreas: 1. Hoje 2. Mente 3. Desafio 21 Dias (Modo Caverna) 4.
Treino 5. Nutrição 6. Calendário 7. Financeiro 8. Perfil

Todas devem ser acessíveis por navegação responsiva e consistente.

## 1. Hoje --- painel principal

Exibir: - Próxima atividade, horário e ação para concluir ou
reagendar. - Agenda do dia em ordem cronológica. - Tarefas do dia com
checkbox, prioridade, horário opcional e estado. - Metas diárias de
água, alimentação, sono e estudo/trabalho. - Progresso das metas. -
Progresso do Desafio 21 Dias, se ativo. - Sugestões do planejador
inteligente.

### Planejador inteligente

-   Identificar intervalos livres entre compromissos.
-   Sugerir horários para treino quando a usuária não tiver horário
    fixo.
-   Sugerir alongamento ou respiração em intervalos de 10--15 minutos.
-   Considerar trabalho, estudo, deslocamento, preparação, sono e
    compromissos familiares.
-   Respeitar duração estimada e margens realistas entre atividades.
-   Não sugerir sobreposição com compromissos confirmados.
-   Permitir aceitar, recusar, editar e reagendar sugestões.
-   Recalcular sugestões quando a agenda mudar.
-   Distinguir compromissos confirmados de horários sugeridos.
-   Usar dados do calendário interno caso não exista integração externa
    real.

## 2. Mente

### Respiração

-   Exercícios guiados de diferentes durações.
-   Temporizador e animação suave.
-   Fases de inspirar, segurar e expirar, quando aplicável.
-   Iniciar, pausar, retomar e encerrar.
-   Histórico e tempo total de sessões.
-   Sugestões para intervalos curtos.
-   Não apresentar como tratamento médico.

### Pomodoro

-   Temporizador funcional de foco e pausas.
-   Padrão inicial: 25 minutos de foco e 5 minutos de pausa.
-   Configurar foco, pausa curta, pausa longa e quantidade de ciclos.
-   Iniciar, pausar, retomar e reiniciar.
-   Associar sessão a tarefa opcional.
-   Histórico e tempo de foco diário/semanal.

### Livros

Cadastrar título, autor opcional, categoria, início, conclusão, páginas
totais, página atual, meta diária, status, avaliação e reflexão final. -
Status: quero ler, lendo, concluído ou pausado. - Página individual para
progresso, diário, anotações datadas, aprendizados e frases digitadas
pela usuária. - Campo "O que achei do livro". - Lista anual de livros
concluídos, agrupada por ano. - Meta anual de livros e meta diária de
páginas. - Estatísticas de livros concluídos, páginas lidas, ritmo
diário e progresso. - Calcular progresso apenas quando os dados
necessários existirem.

### Brainstorming

-   Caderno digital para ideias, projetos e reflexões.
-   Criar, editar, excluir, pesquisar e favoritar notas.
-   Título, conteúdo, data, categorias e etiquetas.
-   Organizar por tema/projeto.
-   Permitir converter uma ideia em tarefa.

## 3. Desafio 21 Dias --- Modo Caverna

Criar uma jornada com 21 dias e progresso visual.

Checklist diário inicial: - Alimentação conforme objetivo pessoal. -
Treino ou atividade física planejada. - Ingestão de água. - Leitura ou
estudo. - Permitir tarefas adicionais configuráveis.

Cada tarefa deve ter checkbox, data, status e observação opcional.

### Regras de progressão

-   Liberar o primeiro dia no início do desafio.
-   Desbloquear os dias seguintes gradualmente, respeitando calendário e
    evolução.
-   Estados: bloqueado, disponível, em andamento e concluído.
-   Não desbloquear dias futuros antecipadamente.
-   Preservar o histórico anterior.
-   Mostrar dias concluídos, tarefas realizadas e progresso geral.
-   Definir conclusão diária como completar as tarefas obrigatórias
    configuradas.
-   Não apagar ou reiniciar automaticamente o desafio após um dia
    incompleto.
-   Permitir continuar ou iniciar uma nova jornada de forma explícita.
-   Conectar com Treino, Nutrição, Mente e Hoje para evitar digitação
    duplicada.
-   Não inventar registros retroativos.

## 4. Financeiro

Controle financeiro pessoal básico: - Receitas e despesas. -
Categorias. - Data, descrição, valor e forma de pagamento opcional. -
Lançamentos recorrentes opcionais. - Criar, editar e excluir. - Filtros
por período e categoria. - Total de receitas, despesas e saldo. -
Gráficos por categoria e comparação mensal quando houver dados. -
Orçamento mensal e acompanhamento de uso. - Não simular conexão
bancária. - Manter registros privados por conta autenticada.

## 5. Calendário

-   Visualizações diária, semanal e mensal.
-   Criar, editar e excluir eventos e tarefas.
-   Data, horário, duração e observações.
-   Treinos e atividades integrados à agenda.
-   Mostrar horários ocupados e livres.
-   Refletir compromissos no painel Hoje.
-   Notificações apenas se realmente implementadas.
-   Não declarar integração externa sem configurá-la e testá-la.

### Ciclo menstrual opcional

Permitir registrar: - Início da menstruação e duração do sangramento. -
Duração aproximada do ciclo. - Sintomas, humor, energia, sono, cólicas e
observações.

Apresentar estimativas das fases menstrual, folicular, ovulatória e
lútea, usando registros anteriores quando disponíveis. - Histórico dos
ciclos e estimativa da próxima menstruação quando houver dados
suficientes. - Identificar padrões observados nos próprios registros. -
Explicar que fases e ovulação são estimativas, especialmente em ciclos
irregulares. - Não diagnosticar doenças nem afirmar que a usuária está
ou não fértil. - Dados opcionais, privados, editáveis e excluíveis.

### Planejador

Usar compromissos, trabalho, deslocamento e preferências para sugerir
treino e pausas de 10--15 minutos. Nunca sobrepor compromissos
confirmados.

## 6. Treino

### Objetivos

Permitir um ou mais: - Saúde e qualidade de vida. - Ganho de massa
muscular. - Perda de peso. - Agilidade e condicionamento. - Atleta não
profissional/competição. - Objetivo personalizado.

### Modalidades múltiplas

-   Musculação.
-   CrossFit.
-   HYROX.
-   Corrida.
-   Funcional.
-   Esportes coletivos.
-   Beach tennis.
-   Yoga.
-   Alongamento.
-   Outras modalidades.

### Diário de treino

Registrar data, modalidade, horário, duração, treino realizado,
exercícios, séries, repetições, cargas, distância/ritmo quando
aplicável, intensidade percebida, percepção geral, observações e status
(planejado, realizado, não realizado).

Permitir responder "O que treinei hoje?" e marcar sessões agendadas como
realizadas.

### Histórico e metas

-   Histórico de sessões.
-   Treinos por semana/mês.
-   Tempo total.
-   Distribuição por modalidade.
-   Evolução de metas e intensidade.
-   Meta semanal de sessões.
-   Meta anual de dias distintos com treino.
-   Diferenciar quantidade de sessões de quantidade de dias treinados.

### Peso e medidas

-   Registros datados de peso e medidas corporais.
-   Gráficos e histórico.
-   Dados privados, sem exposição na tela inicial.
-   Não inferir diagnóstico de saúde com base em peso/medidas.

## 7. Nutrição

### Educação alimentar

Conteúdos acessíveis sobre alimentação equilibrada, grupos alimentares,
proteínas, carboidratos, gorduras, fibras, vitaminas, minerais,
hidratação e organização de refeições. Evitar moralizar alimentos.

### Déficit calórico

Explicar ingestão versus gasto energético, limitações das estimativas,
consistência, sono e atividade física. Não sugerir restrições extremas.
Recomendar orientação profissional para planos individualizados quando
necessário.

### Hidratação

-   Usar peso do Perfil para estimar uma meta inicial em ml/kg por meio
    de parâmetro configurável.
-   Permitir ajuste manual da meta.
-   Registrar copos e volumes personalizados.
-   Mostrar meta, quantidade ingerida e restante.
-   Atualizar progresso diário e histórico.
-   Integrar com Hoje e Desafio 21 Dias.
-   Deixar claro que a estimativa não é universal nem uma prescrição
    médica.
-   Orientação médica prevalece em casos de restrição de líquidos.

### Diário alimentar

Registrar refeições, horário e observações. Contagem de calorias é
opcional; quando existir, informar que os valores são estimativas.

## 8. Perfil e onboarding

### Dados opcionais

-   Nome de exibição.
-   Peso e altura.
-   Objetivo principal e secundários.
-   Modalidades.
-   Preferências de rotina.

Não exigir peso/altura para utilizar o aplicativo.

### Rotina

Perguntar: - Horário habitual de acordar e dormir. - Tempo de preparação
e deslocamento. - Se tem horário fixo para treinar. - Dias e duração
habitual do treino. - Trabalho, estudo, cuidados do lar e
compromissos. - Principais dificuldades e hábitos desejados.

### Filhos e escola (opcional)

Perguntar se tem filhos e, se sim, se estão em idade escolar, horários
de levar/buscar e tempo de deslocamento. Não exigir nomes ou datas de
nascimento de crianças.

### Trabalho/estudo

Permitir combinar categorias: - Presencial integral. - Híbrido
integral. - Remoto. - Estágio. - Estudo. - Cuidados com o lar. -
Autônomo. - Outra situação.

Cadastrar horários, dias presenciais/remotos e deslocamentos conforme
necessário.

### Análise de rotina

Gerar resumo editável de horários ocupados, intervalos potenciais,
melhores janelas para treino, leitura, estudo, refeições, respiração e
alongamento. Distinguir horários confirmados de sugestões.

### Mascote opcional

Questionário de 10 perguntas sobre preferências, motivação, organização
e objetivos. Gerar uma mascote/arquétipo com nome, características,
pontos fortes e mensagem personalizada. Permitir ignorar, refazer ou
alterar. Não apresentar como diagnóstico psicológico.

## 9. Integrações entre módulos

-   Perfil fornece preferências e dados necessários aos módulos.
-   Hoje agrega tarefas, agenda, metas e atividades.
-   Calendário fornece horários ocupados ao planejador.
-   Planejador sugere atividades sem conflito.
-   Treino alimenta histórico e metas.
-   Nutrição atualiza hidratação e diário alimentar.
-   Água atualiza Hoje e Desafio.
-   Mente atualiza histórico de foco, respiração e leitura.
-   Livros atualizam metas diárias e anuais.
-   Desafio consulta registros existentes e evita duplicação.
-   Ciclo menstrual apresenta padrões com base em registros reais.
-   Financeiro mantém seu histórico independente.

Não marcar tarefas como concluídas sem registro confiável. Quando a
mesma atividade for registrada em outro módulo, refletir a conclusão de
forma transparente.

## 10. Requisitos técnicos, segurança e persistência

-   Inspecionar e preservar a stack existente.
-   Se o projeto usa React/TypeScript, manter padrões e componentes
    reutilizáveis.
-   Validar formulários e tratar erros/loading/estados vazios.
-   Garantir persistência após recarregar.
-   Separar dados por usuário autenticado.
-   Não expor credenciais ou chaves no cliente.
-   Se Supabase estiver configurado ou for adequado, usar autenticação,
    banco e políticas de acesso por usuário (RLS).
-   Não inventar credenciais nem afirmar integrações inexistentes.
-   Implementar acessibilidade básica, responsividade e datas/horários
    consistentes.
-   Permitir consultar, editar e excluir dados pessoais.
-   Proteger especialmente saúde, ciclo menstrual, peso e finanças.

## 11. Ordem recomendada de implementação

### Etapa 1 --- Fundação

-   Inspeção do projeto.
-   Identidade visual e navegação.
-   Perfil/onboarding.
-   Tela Hoje.
-   Persistência e autenticação conforme a arquitetura existente.

### Etapa 2 --- Organização

-   Calendário.
-   Tarefas e compromissos.
-   Planejador de horários livres.
-   Integração com Hoje.

### Etapa 3 --- Hábitos

-   Respiração, Pomodoro, Livros e Brainstorming.
-   Desafio 21 Dias.
-   Integração dos registros.

### Etapa 4 --- Saúde e atividade

-   Treino, Nutrição, hidratação e gráficos.

### Etapa 5 --- Complementos

-   Financeiro, ciclo menstrual, mascote e refinamentos.

Ao finalizar cada etapa, execute os testes aplicáveis e registre o que
foi realmente verificado.

## 12. Critérios de aceitação

-   Navegação entre todas as áreas.
-   Cadastro e edição do Perfil.
-   Criar tarefas e compromissos e vê-los em Hoje.
-   Planejador não cria conflitos.
-   Temporizadores funcionam.
-   Livros, páginas, anotações e metas persistem.
-   Brainstorming permite criar/editar/excluir.
-   Desafio respeita progressão e preserva histórico.
-   Treinos e metas atualizam histórico corretamente.
-   Hidratação calcula meta inicial a partir do peso, quando informado,
    e permite ajuste.
-   Conteúdos de Nutrição acessíveis.
-   Financeiro calcula totais a partir de lançamentos reais.
-   Ciclo menstrual mostra estimativas com avisos claros.
-   Dados persistem após recarregar.
-   Dados de usuários distintos permanecem isolados.
-   Layout funciona em dispositivos móveis.
-   Botões, filtros, gráficos e formulários têm comportamento real.

## 13. Entrega e relatório

Ao terminar cada etapa, informar: 1. Arquivos criados ou alterados. 2.
Funcionalidades implementadas. 3. Integrações realmente configuradas. 4.
Comandos e testes executados e seus resultados. 5. Limitações
conhecidas. 6. Próximos passos.

Não declare uma funcionalidade concluída se estiver apenas desenhada.
Não remova funcionalidades existentes sem justificativa. Não faça
grandes reescritas sem necessidade. Preserve o histórico Git e trabalhe
com alterações pequenas e verificáveis.

**Nome do produto:** INSTINCT\
**Nome da jornada:** Desafio 21 Dias / Modo Caverna\
**Idioma:** Português brasileiro (pt-BR)
