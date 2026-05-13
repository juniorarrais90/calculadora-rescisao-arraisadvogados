# Changelog — Calculadora de Rescisão Trabalhista

Histórico versionado de todas as alterações da Calculadora de Rescisão Trabalhista do escritório Arrais Advogados. Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/).

---

## [1.5.1] — 13/05/2026 — Correção dos dados institucionais

### Corrigido
- Razão social atualizada de "Arrais Advogados" para **"Arrais Sociedade de Advogados"** em todos os rodapés (UI, PDFs e README)
- Inclusão do **CNPJ 60.284.876/0001-39** e da inscrição **OAB/MG nº 19.391** (do escritório)
- Removidas as inscrições OAB de outros estados (SP, RJ, PA) — eram pessoais do sócio Júnior Arrais, não institucionais
- Endereço ajustado: "Salas 203, 204 e 209" (com "e" antes da última sala, conforme norma gramatical brasileira)
- Logo no Memorial Detalhado agora aparece sobre **fundo navy** (caixa institucional) com padding e border-radius — resolve problema do logo PNG transparente que ficava invisível sobre fundo branco do memorial sóbrio

## [1.5.0] — 13/05/2026 — Elementos gráficos e visuais avançados

### Adicionado ao Resumo Executivo (PDF de captação)
- **Mini-cards estatísticos** no topo do documento — quatro cards lado a lado mostrando: Tempo de Contrato (em formato curto "3a 4m"), Modalidade da rescisão, Total da Rescisão (em destaque gold) e Status Prescricional (verde "Em prazo" ou vermelho "Bienal")
- **Gráfico de pizza SVG** comparando rescisão pleitável vs valores prescritos — só aparece quando há prescrição (bienal ou quinquenal). Verde para o pleitável, vermelho para o prescrito, com legenda contendo valor e porcentagem de cada
- **Linha do tempo SVG horizontal** com marcos cronológicos: Admissão (verde), Saída (navy), Marco quinquenal (amarelo), Prescrição bienal (vermelho) e Data de referência (azul). Etiquetas alternadas acima/abaixo da linha base para legibilidade

### Adicionado ao Memorial Detalhado (PDF processual)
- **Tabela tipográfica formal** substituindo os cards de verba. Cabeçalho navy com texto branco, três colunas (Verba + Fundamentação | Base de Cálculo | Valor), linhas com zebra (alternância de fundo cinza claro), linha de subtotal com destaque navy
- Fundamentação legal mostrada em itálico cinza dentro da célula da verba, em fonte menor
- Aplicado às quatro seções da rescisão (TRCT, Depósitos FGTS, Descontos Legais, Pleitos Trabalhistas)

### Funções utilitárias adicionadas
- `gerarGraficoPizza(itens)` — SVG inline com fatias proporcionais e legenda
- `gerarLinhaDoTempo(eventos)` — SVG inline horizontal com pontos coloridos e labels datadas

## [1.4.0] — 13/05/2026 — Identidade visual institucional completa

### Adicionado
- **Logo do escritório** (`logo.png`) no cabeçalho da calculadora (UI) e no cabeçalho de ambos os PDFs (Resumo e Memorial). Sistema com fallback gracioso caso o arquivo não exista
- **Endereço completo** (Rua Carlos Peixoto Filho, n.º 112, Salas 203/204/209, Ed. Otocy Vilela Eiras, Centro, Ubá/MG, CEP 36500-097), telefone (32) 99844-6488 e e-mail (contato@arraisadv.com.br) no rodapé da UI e dos PDFs
- **Gráfico de composição visual** no Resumo Executivo (PDF de captação): barra horizontal SVG empilhada mostrando a proporção visual entre Rescisão líquida, FGTS, Seguro-desemprego e Pleitos trabalhistas. Cada segmento com cor temática e legenda com valor + porcentagem
- Card final do gráfico com **"Valor Total Estimado a Receber"** (soma de todos os benefícios)

### Função técnica adicionada
- `gerarBarraComposicao(itens)` — utilitária que gera SVG inline de barra horizontal empilhada proporcional, sem dependências externas

### Como subir o logo
O arquivo `logo.png` deve ser salvo no mesmo diretório do `index.html` no repositório do GitHub (versão com fundo transparente é a ideal). Recomenda-se largura entre 200 e 400px, altura proporcional. O sistema redimensiona automaticamente conforme o contexto (UI ou PDF).

## [1.3.1] — 13/05/2026 — Diferenciação visual dos PDFs (Resumo × Memorial)

### Adicionado
- Classes específicas para cada modo de impressão: `body.print-resumo` e `body.print-memorial`
- CSS diferenciado por modo no bloco `@media print`

### Resumo Executivo (cores + marca institucional, para captação/cliente)
- Cabeçalho com fundo navy, título em branco, subtítulo em gold
- Títulos de seção com fundo navy claro, borda lateral gold
- Total da rescisão com fundo navy e número grande em gold
- Seções com leve borda lateral gold e padding
- Rodapé com fundo navy claro e borda superior gold
- Caixa de aviso (estimativa de causa) em amarelo institucional

### Memorial Detalhado (sóbrio, para juntada processual)
- Cabeçalho mantém apenas linha tripla navy (sem fundo colorido)
- Cards de verba (TRCT, depósito FGTS, pleito, desconto) todos com borda lateral cinza neutro — sem distinção por cor
- Caixa de aviso em tom cinza neutro
- Títulos de seção apenas pretos com sublinha cinza
- Adequado para impressão em PB ou cópia processual

## [1.3.0] — 13/05/2026 — Diferenciação visual dos blocos por tema

### Adicionado
- CSS para `.section-block` — wrapper visual de cada grupo de seções do painel de entrada, com borda lateral colorida (4px), fundo levemente gradiente, sombra suave e margem de 22px entre blocos
- Sete variantes temáticas: navy, gold, purple, warning (amarelo), info (azul), danger (vermelho), success (verde)
- Cada bloco ganhou cor temática conforme seu assunto:
  - **Navy** — Identificação (caso, empregado, empregador) + Modalidade de rescisão (Fase 2)
  - **Gold** — Contrato de trabalho + Remuneração base
  - **Purple** — Adicionais e médias remuneratórias (Fase 3)
  - **Warning (amarelo)** — Pagamentos já realizados (descontos) + Simulação trabalhista (Fase 5)
  - **Info (azul)** — FGTS (Lei 8.036/90) + Atualização monetária (Fase 6)
  - **Danger (vermelho)** — Descontos legais INSS/IRRF (Fase 4)
  - **Success (verde)** — Seguro-desemprego (Lei 7.998/90)
- Título de cada bloco recebe a cor temática para reforço visual

## [1.2.0] — 13/05/2026 — Bloco "Valores Excluídos pela Prescrição"

### Adicionado
- Novo bloco no painel de resultados: **"Valores Excluídos pela Prescrição"** — discrimina, com valor monetário, cada verba ou pleito que ficou de fora pelo decurso dos prazos prescricionais. Cobre tanto bienal quanto quinquenal.
- Cada item prescrito aparece com badge identificando a prescrição aplicável (Bienal em vermelho ou Quinquenal em amarelo) e fundamentação legal específica.
- Card final com **"Total Excluído pela Prescrição"** somando tudo, com mensagem orientativa ao cliente sobre a importância de procurar o escritório a tempo.

### Alterado
- Comportamento do **bloqueio bienal**: ao invés de zerar tudo e mostrar apenas um aviso, agora a calculadora calcula todas as verbas/pleitos normalmente, marca como prescritos (não soma no total da rescisão nem no valor da causa) e os lista no novo bloco de "Valores Excluídos pela Prescrição". O aviso vermelho continua no topo, mas o cliente passa a ver exatamente quanto perdeu.
- Função `apurarPrincipal` agora retorna também `prescritoQuinquenal` e `mesesPrescritos` para alimentar o registro de valores excluídos.
- Função `calcularSimulacaoTrabalhista` retorna `pleitosPrescritos` e `totalPrescritoQuinquenal` para integrar ao bloco.
- Função `calcularVerbas` retorna `verbasPrescritasRescisao` (férias vencidas prescritas + FGTS além do cap quinquenal).

### Pleitos com registro de prescrição quinquenal implementado
Horas extras retroativas, adicional retroativo, intervalo intrajornada, interjornada, diferenças salariais, vale-transporte, vale-alimentação, pagamento por fora, férias vencidas (por período aquisitivo), FGTS não depositado (depósitos além do quinquênio).

## [1.1.2] — 13/05/2026 — Auditoria prescricional completa

### Corrigido
- **Pagamento por fora (extra-folha):** o cálculo não aplicava o cap quinquenal — usava `Math.min(60, meses)` em vez da função correta `limitarMesesPorPrescricao(meses)`. Agora o pleito é limitado corretamente.
- **FGTS não depositado (regularização):** o cálculo do FGTS histórico estimado considerava todos os meses do contrato sem aplicar a prescrição quinquenal do crédito de depósito (STF ARE 709.212, Tema 608; Súm. 362, TST reformulada em 2016). Agora a "regularização" é limitada aos últimos 60 meses retroativos da data de referência.

### Nuance jurídica preservada
- A **multa de 40% do FGTS** continua incidindo sobre o saldo total devido (todo o contrato), pois é instituto autônomo nascido da rescisão (art. 18, §1º, Lei 8.036/90) — não sofre o cap dos depósitos antigos prescritos. Apenas o **crédito de depósito** (a regularizar) é que é limitado pela prescrição quinquenal.

### Auditoria completa dos pleitos com cap quinquenal aplicado
Todos os pleitos retroativos do escopo da Fase 5 agora respeitam o cap quinquenal:
- Horas extras retroativas + reflexos
- Adicional retroativo + reflexos
- Intervalo intrajornada suprimido
- Intervalo interjornada suprimido + reflexos
- Diferenças salariais (equiparação, desvio, CCT) + reflexos
- Vale-transporte não entregue
- Vale-alimentação não entregue
- Pagamento por fora + reflexos (corrigido nesta versão)
- Férias vencidas (por período aquisitivo individual, art. 149, CLT — corrigido na v1.1.1)
- FGTS não depositado (corrigido nesta versão)

## [1.1.1] — 13/05/2026 — Prescrição também aplicada às férias vencidas por período

### Corrigido
- Bug: o cap quinquenal não estava sendo aplicado individualmente em cada período aquisitivo de férias vencidas. Períodos cujo concessivo havia expirado há mais de 5 anos da data de referência apareciam como "DOBRADO" e entravam no cálculo, gerando valor inflado.

### Adicionado
- Função `analisarPeriodosVencidos` agora recebe `dataReferenciaStr` e calcula, para cada período aquisitivo, a data de prescrição quinquenal (5 anos contados do fim do prazo concessivo — art. 149, CLT)
- Cada período retornado inclui o campo `prescrito: true|false` e a `dataPrescricao` calculada
- Renderização da lista de períodos: períodos prescritos aparecem com badge vermelha "PRESCRITO — art. 149, CLT", são desabilitados para entrada de dias gozados (não há pleito a configurar) e os botões rápidos ficam inativos
- Card informativo no resultado: quando há períodos prescritos no cálculo, aparece linha "Férias vencidas prescritas (N períodos)" com a fundamentação (art. 149, CLT; art. 7º, XXIX, CF/88)
- Listener adicionado ao campo `data-referencia` para regerar a lista de períodos quando o usuário altera a data presumida de ajuizamento

## [1.1.0] — 13/05/2026 — Controle prescricional automático e mutua exclusão insalub/peric

### Adicionado
- Campo "Data de Referência para Prescrição" no formulário (data presumida do ajuizamento, default: hoje)
- Função `analisarPrescricao(dataSaida, dataReferencia)` que calcula a bienal e a quinquenal
- **Bloqueio automático da bienal:** quando passados mais de 2 anos do término do contrato em relação à data de referência, a calculadora exibe aviso visual destacado em vermelho e zera todos os pleitos, conforme art. 7º, XXIX, CF/88
- **Cap quinquenal automático:** os pleitos retroativos com campo "meses" (HE, adicional retroativo, intervalo intrajornada, interjornada, diferenças salariais, vale-transporte, vale-alimentação, pagamento por fora) são limitados ao período de 5 anos retroativos da data de referência. O cap é aplicado tanto no modo "mensal × meses" quanto no modo "valor total apurado"
- Avisos visíveis no Bloco 4 informando o limite quinquenal aplicado, com data exata do marco prescricional

### Alterado
- Função `apurarPrincipal(modo, meses, valor)` agora aplica `limitarMesesPorPrescricao(meses)` antes de calcular o principal, e adiciona observação no detalhe do card quando os meses foram reduzidos pela prescrição
- UI dos selects de insalubridade e periculosidade: **mutua exclusão automática** — ao selecionar um, o outro fica desabilitado, evitando escolha simultânea que viola o art. 193, §2º, CLT
- Quando periculosidade é selecionada, o select de base de cálculo da insalubridade e o bloco de piso da categoria também ficam desabilitados/ocultos

### Removido
- Lógica que comparava insalubridade vs periculosidade para aplicar a "mais vantajosa" — desnecessária após a mutua exclusão na UI

## [1.0.2] — 13/05/2026 — Depuração prescricional

### Removido
- Pleito de "Intrajornada suprimida — pré-reforma" (Lei 13.467/2017 vigente desde 11/11/2017). Em maio/2026, com prescrição quinquenal vigente, qualquer fato anterior a 11/11/2017 está fora do quinquenal há mais de 3 anos e 6 meses (limite atual: maio/2021). O campo perdeu utilidade operacional para rescisões iniciadas em 2026.

### Alterado
- Pleito de "Intrajornada pós-reforma" renomeado simplesmente para "Intervalo intrajornada suprimido" (com fundamentação atualizada: art. 71, §4º, CLT, redação Lei 13.467/2017). Único regime aplicável hoje.

## [1.0.1] — 13/05/2026 — Modo dual de lançamento

### Adicionado
- Seletor "modo de lançamento" em 5 pleitos da Fase 5 (intrajornada pré-reforma, intrajornada pós-reforma, interjornada, vale-transporte, vale-alimentação) com duas opções: "Valor mensal médio × meses" (padrão) ou "Valor total apurado" (sem multiplicação). Útil para descumprimentos esporádicos ou irregulares.

### Tecnologia
- Função `atualizarModoPleito(prefixo, ...)` controla a UI dinâmica de cada pleito (esconde campo de meses no modo total, ajusta labels e hints)
- Função `apurarPrincipal(modo, meses, valor)` unifica o cálculo do principal em ambos os modos

## [1.0.0] — 12/05/2026 — Lançamento em produção

### Fase 8 — Deploy e governança
- Publicação da calculadora no GitHub Pages em URL pública oficial: https://juniorarrais90.github.io/calculadora-rescisao-arraisadvogados/
- Geração do POP-TRAB-001 (Procedimento Operacional Padrão para uso pela equipe)
- Documentação técnica (README.md e CHANGELOG.md) incluída no repositório
- Banner "em construção" removido — calculadora marcada como pronta para uso

---

## [0.7.0] — Fase 7 — Outputs profissionais em PDF

### Adicionado
- Dois botões de impressão: **Resumo Executivo** (uma página, captação) e **Memorial Detalhado** (juntada processual, sete seções)
- CSS dedicado para `@media print` com layout A4, cabeçalho institucional, cards coloridos por categoria (TRCT, depósito FGTS, desconto, pleito de ação)
- Função `montarResumoExecutivo` e `montarMemorialDetalhado` em JavaScript
- Quebras de página inteligentes (`page-break-inside: avoid`)
- Margem padrão A4 1,5cm

### Tecnologia
- `window.print()` nativo do navegador, sem dependências externas

---

## [0.6.0] — Fase 6 — Atualização monetária e juros

### Adicionado
- Seção "Atualização Monetária e Juros" com habilitação opcional
- Quatro campos: data base, data do ajuizamento, fator pré-ajuizamento (IPCA-E + juros), fator pós-ajuizamento (Selic)
- Aplicação composta: valor × (1 + IPCA-E) × (1 + Selic)
- Atualização aplicada tanto no totalizador da rescisão quanto no valor estimado da causa trabalhista
- Cards de detalhamento mostram acréscimo absoluto e fator total

### Fundamentação
- ADCs 58 e 59, STF (julgamento 2020, modulação 2021)
- Tema 1.191 da Repercussão Geral
- Tabela oficial do TST para fatores acumulados mensais

---

## [0.5.5] — Fase 5 — Refinamentos finais

### Adicionado
- Indenização substitutiva do seguro-desemprego (Súmula 389, II, TST)
- Reflexos no aviso prévio aplicados nas verbas retroativas de natureza salarial (HE, adicionais, diferenças salariais, pagamento por fora) — Súmulas 94 e 132, TST

### Validações implementadas
- Indenização substitutiva só lançada quando o empregado se habilita ao seguro (modalidade, carência, período aquisitivo)
- Total dos pleitos ignora itens marcados como informativos

---

## [0.5.4] — Fase 5 — Pagamento extra-folha e multa convencional

### Adicionado
- Pleito de pagamento por fora (extra-folha) com reflexos integrais — art. 457, CLT; art. 9º, CLT; Súmula 91, TST
- Multa convencional da CCT/ACT (cláusula penal) — art. 7º, XXVI, CF/88; arts. 412-416, CC

---

## [0.5.3] — Fase 5 — Vale-transporte e vale-alimentação

### Adicionado
- Vale-transporte não entregue (Lei 7.418/85; Súmula 460, TST) — natureza indenizatória
- Vale-alimentação/refeição não entregue (Lei 6.321/76 PAT; art. 457, §2º, CLT) — natureza indenizatória

---

## [0.5.2] — Fase 5 — Diferenças salariais

### Adicionado
- Pleito de diferenças salariais com quatro tipos: equiparação (art. 461, CLT; Súm. 6, TST), desvio/acúmulo de função, reajuste convencional (CCT) não aplicado, outras diferenças
- Reflexos completos por natureza salarial

---

## [0.5.1] — Fase 5 — Intervalos intra e interjornada

### Adicionado
- Intrajornada pré-Reforma (Súm. 437, I, TST) — hora cheia com reflexos
- Intrajornada pós-Reforma (art. 71, §4º, CLT, redação Lei 13.467/2017) — período suprimido, indenizatório
- Interjornada (art. 66, CLT; Súm. 110, TST) — horas faltantes como HE com reflexos

---

## [0.5.0] — Fase 5 — Simulação de Reclamação Trabalhista

### Adicionado
- Bloco 4 "Pleitos de Ação Trabalhista" no painel de resultados
- Pleitos iniciais: multa do art. 477 §8º, multa do art. 467, horas extras retroativas + reflexos, adicionais retroativos + reflexos, dano moral, indenização do período de estabilidade
- Honorários sucumbenciais (art. 791-A, CLT) — 5% a 15%
- Aviso de estimativa para fins de captação

---

## [0.4.0] — Fase 4 — Descontos legais

### Adicionado
- Constante `INSS_2026` com tabela progressiva (7,5% / 9% / 12% / 14%; teto R$ 8.475,55)
- Constante `IRRF_2026` com tabela progressiva e redução adicional da Lei 15.087/2025 (isenção até R$ 5.000, redução gradual até R$ 7.350)
- Função `calcularINSS` (cálculo fatia por fatia)
- Função `calcularIRRF` (com opção entre deduções legais e desconto simplificado)
- Cálculo separado de INSS e IRRF sobre folha (saldo + aviso trabalhado) e sobre 13º (tributação exclusiva)
- Identificação automática das verbas isentas (aviso indenizado, férias indenizadas, 1/3 constitucional, FGTS)

---

## [0.3.0] — Fase 3 — Adicionais e médias remuneratórias

### Adicionado
- Insalubridade (NR-15) — 10/20/40% com escolha de base (mínimo, salário, piso CCT)
- Periculosidade (art. 193, CLT) — 30% sobre salário-base
- Aplicação automática da opção mais vantajosa entre periculosidade e insalubridade (art. 193, §2º, CLT)
- Adicional noturno (art. 73, CLT; Lei 5.889/73) — urbano 20% (hora reduzida 52'30") e rural 25%
- Médias variáveis: horas extras, comissões, DSR sobre HE (Súm. 60, II, TST)
- Função `calcularRemuneracaoRescisoria` — base ampliada para todas as verbas rescisórias

---

## [0.2.8] — Fase 2 — Limpeza final

### Removido
- Card "Férias Vencidas (período integral)" do painel "Dados Apurados" que estava redundante com o bloco detalhado período a período

---

## [0.2.7] — Fase 2 — Tabela 2026 do seguro-desemprego e período aquisitivo

### Adicionado
- Constante `SEG_DES_2026` (piso R$ 1.621,00; teto R$ 2.518,65; faixas progressivas)
- Constante `SEG_DES_CARENCIA` por número de solicitação (12/9/6 meses)
- Função `calcularNumeroParcelasSegDes` (3/4/5 parcelas conforme tempo e solicitação)
- Função `calcularValorParcelaSegDes` (cálculo por faixa)
- Função `calcularSeguroDesemprego` com verificação de habilitação completa
- Campo "Já recebeu seguro-desemprego anteriormente?" com data da dispensa anterior
- Verificação automática do período aquisitivo de 16 meses (Res. CODEFAT 957/2022, art. 24)
- Campo "Meses adicionais trabalhados em vínculos anteriores" para somar ao tempo computado

---

## [0.2.5] — Fase 2 — Detecção de dobra das férias vencidas período a período

### Adicionado
- Lista dinâmica de períodos aquisitivos vencidos gerada automaticamente
- Detecção automática da dobra do art. 137 da CLT por período individual (concessivo expirado vs em curso)
- Badge visual por período: DOBRADO (concessivo expirado), Simples (concessivo em curso), Integralmente gozado
- Botões rápidos por período: "Não gozado", "15 dias", "Integral"
- Cálculo separado das férias simples e dobradas com fundamentação distinta

---

## [0.2.1 - 0.2.4] — Fase 2 — Refinamentos

### Adicionado
- Campo "Dias antecipados das férias em curso" (art. 130, CLT)
- Campo "Valor já pago de 13º (parcelas/adiantamentos)" — Lei 4.749/65
- Pergunta "Os depósitos do FGTS estão regulares?" com cálculo do FGTS não depositado (regularização direta na conta vinculada, art. 26, Lei 8.036/90)
- Tratamento de cruzamento de ano civil na projeção do aviso indenizado
- Reorganização do painel de resultados em blocos: (1) verbas em dinheiro TRCT, (2) depósitos no FGTS, (3) seguro-desemprego junto a outros órgãos

---

## [0.2.0] — Fase 2 — Modalidades de rescisão

### Adicionado
- 13 modalidades de rescisão com matriz completa de verbas devidas:
  - Dispensa sem justa causa (arts. 477 e 487, CLT)
  - Dispensa com justa causa (art. 482, CLT; Súm. 171, TST)
  - Pedido de demissão (art. 487, CLT)
  - Rescisão por acordo (art. 484-A, CLT — Lei 13.467/2017)
  - Rescisão indireta (art. 483, CLT)
  - Culpa recíproca (art. 484, CLT; Súm. 14, TST)
  - Término normal de contrato determinado
  - Rescisão antecipada pelo empregador (art. 479, CLT)
  - Rescisão antecipada pelo empregado (art. 480, CLT)
  - Morte do empregado (Lei 6.858/80)
  - Morte do empregador PF / encerramento (art. 485, CLT)
  - Força maior (art. 502, CLT)
  - Factum principis (art. 486, CLT)
- Cálculo de aviso prévio proporcional (Lei 12.506/2011; NT MTE 184/2012)
- Projeção do aviso indenizado (Súm. 371, TST; art. 487, §1º, CLT)
- Função `calcularVerbas` com matriz de modalidades
- Função `analisarPeriodosVencidos` (períodos aquisitivos + concessivos)

---

## [0.1.0] — Fase 1 — Fundação arquitetural

### Adicionado
- Estrutura HTML/CSS no padrão visual do escritório (navy `#0D2340` + gold `#C9A84C`, fonte Inter)
- Layout em duas colunas (formulário + resultado) responsivo
- Bloco "Identificação do Caso" (ID interno, dados do empregado e empregador com máscaras de CPF/CNPJ)
- Bloco "Contrato de Trabalho" (tipo, datas, salário, jornada)
- Cálculo automático de tempo de contrato (anos/meses/dias) com regra dos 15 dias para avos (Súm. 157, TST)
- Cálculo de salário-dia (÷30) e salário-hora (art. 64, CLT; Súm. 124, TST para bancários)
- Persistência local (localStorage) com lista de casos salvos
- Validações de datas e salário

### Tecnologia
- HTML5 + CSS3 + JavaScript ES6+ vanilla
- Sem dependências externas
- Sem build step

---

**Mantenedor:** Júnior Arrais — sócio-gestor, Arrais Advogados (Ubá/MG)
**Construção colaborativa:** Júnior Arrais + assistente de IA Claude (Anthropic), entre maio e junho de 2026
