[README.md](https://github.com/user-attachments/files/27728984/README.md)
# Calculadora de Rescisão Trabalhista — Arrais Advogados

Ferramenta institucional do escritório Arrais Advogados para cálculo de rescisões trabalhistas e simulação de pleitos de reclamação trabalhista.

**URL pública:** https://juniorarrais90.github.io/calculadora-rescisao-arraisadvogados/

**Versão atual:** 1.0.0 (vigência a partir de 12/05/2026)

---

## Visão geral

Calculadora web 100% client-side, sem backend, sem dependências externas. Funciona em qualquer navegador moderno (Chrome, Edge, Firefox, Safari). Os dados ficam armazenados localmente no navegador do usuário (localStorage) — nada é enviado a servidores externos, garantindo confidencialidade dos casos atendidos.

Arquivo único: `index.html` (~4.400 linhas, contendo HTML, CSS e JavaScript em um único arquivo para facilitar deploy e manutenção).

## Escopo coberto

### Verbas rescisórias (Fase 2)
13 modalidades de rescisão: dispensa sem justa causa, com justa causa, pedido de demissão, acordo (art. 484-A), rescisão indireta (art. 483), culpa recíproca, término normal de contrato determinado, rescisão antecipada pelos arts. 479 e 480, morte do empregado, morte do empregador PF/encerramento (art. 485), força maior (art. 502) e factum principis (art. 486).

Para cada modalidade: saldo de salário, aviso prévio (com proporcionalidade da Lei 12.506/2011 e projeção da Súmula 371 do TST), 13º proporcional, férias proporcionais e vencidas (com detecção automática de dobra do art. 137 da CLT, Súmula 81 do TST), FGTS e multa rescisória, indenizações específicas dos arts. 479 e 480.

### Adicionais e médias remuneratórias (Fase 3)
Insalubridade (10/20/40%), periculosidade (30%), adicional noturno (urbano e rural), médias variáveis (horas extras, comissões, DSR). Aplicação automática da opção mais vantajosa entre periculosidade e insalubridade quando ambas existem (art. 193, §2º, CLT).

### Descontos legais (Fase 4)
INSS progressivo 2026 (faixas 7,5% / 9% / 12% / 14% com teto de R$ 8.475,55). IRRF 2026 com isenção da Lei 15.087/2025 (até R$ 5.000) e redução gradual até R$ 7.350.

### Seguro-desemprego (Fase 2/4)
Tabela MTE 2026 (Resolução CODEFAT, piso R$ 1.621,00; teto R$ 2.518,65). Verificação automática de habilitação (modalidade compatível, carência atingida) e período aquisitivo de 16 meses entre solicitações (Res. CODEFAT 957/2022, art. 24).

### Simulação de reclamação trabalhista (Fase 5)
15 pleitos típicos: multas dos arts. 467 e 477 §8º, horas extras + reflexos, adicionais retroativos, intervalos intra e interjornada (pré e pós-reforma), diferenças salariais (equiparação, desvio, CCT), vale-transporte, vale-alimentação, pagamento extra-folha, multa convencional da CCT, dano moral, estabilidade, indenização substitutiva do seguro-desemprego (Súmula 389, II, TST), honorários sucumbenciais (art. 791-A, CLT).

### Atualização monetária e juros (Fase 6)
IPCA-E + juros legais na fase pré-ajuizamento e Selic na fase pós-ajuizamento, conforme ADCs 58 e 59 do STF e Tema 1.191. Fatores acumulados informados pelo operador conforme tabela oficial do TST.

### Outputs profissionais (Fase 7)
Dois modos de impressão (via window.print do navegador):
- **Resumo Executivo:** uma página, foco no valor total, para atendimento e captação.
- **Memorial Detalhado:** estruturado em sete seções, fundamentação legal verba por verba, para juntada processual.

---

## Manutenção anual das tabelas

A calculadora foi construída com tabelas vigentes em maio de 2026. As atualizações periódicas devem ser feitas editando o arquivo `index.html` diretamente no GitHub (botão de lápis no arquivo → editar → commit). Localização exata de cada constante:

### Salário-mínimo nacional
**Onde:** input do formulário com `id="salario-minimo"`, valor padrão `1.621,00`. Buscar por: `value="1.621,00"`.
**Quando atualizar:** janeiro de cada ano, conforme decreto presidencial.

### Tabela INSS
**Onde:** constante `INSS_2026` no JavaScript. Buscar por: `const INSS_2026 = {`.
**O que atualizar:** faixas, alíquotas, teto. Buscar Portaria interministerial MTPS/MF publicada anualmente em janeiro.
**Renomear:** alterar `INSS_2026` para `INSS_2027` (ou ano vigente) e atualizar todas as referências.

### Tabela IRRF
**Onde:** constante `IRRF_2026` no JavaScript. Buscar por: `const IRRF_2026 = {`.
**O que atualizar:** faixas, alíquotas, parcelas a deduzir, desconto simplificado mensal, dedução por dependente, faixas de isenção/redução da Lei 15.087/2025 (ou nova lei que vier).

### Tabela do seguro-desemprego
**Onde:** constante `SEG_DES_2026` no JavaScript. Buscar por: `const SEG_DES_2026 = {`.
**O que atualizar:** piso, teto, limites das faixas (faixa1Limite, faixa2Limite), adicionalFaixa1.
**Fonte oficial:** Resolução CODEFAT publicada anualmente em janeiro pelo Ministério do Trabalho.

### Banner de boas-vindas
**Onde:** `<div class="phase-banner">` no HTML. Atualizar texto se houver mudanças relevantes na ferramenta.

---

## Estrutura de pastas (após deploy)

```
/
├── index.html       # arquivo único da calculadora (~4.400 linhas)
├── README.md        # este arquivo
└── CHANGELOG.md     # histórico de versões
```

---

## Como atualizar a calculadora

### Atualizações simples (tabelas anuais):
1. Acesse https://github.com/juniorarrais90/calculadora-rescisao-arraisadvogados
2. Clique em `index.html`
3. Clique no ícone de lápis (Edit)
4. Use Ctrl+F para localizar a constante (ex.: `INSS_2026`)
5. Atualize os valores
6. Role até "Commit changes" e descreva a alteração (ex.: "Tabela INSS 2027 — Portaria XXX")
7. Confirme. O GitHub Pages atualiza em 1-3 minutos.

### Atualizações complexas (nova funcionalidade, ajuste em fórmula):
Procurar suporte técnico para revisão do código antes de subir.

---

## Stack tecnológica

- **HTML5** + **CSS3** (com `@media print` para os PDFs) + **JavaScript ES6+** vanilla
- Sem frameworks, sem bibliotecas externas, sem build step
- Persistência: `localStorage` do navegador
- Geração de PDF: `window.print()` nativo do navegador
- Hospedagem: GitHub Pages (gratuito)

## Compatibilidade
Testado em Chrome, Edge e Firefox (versões 2024+). Responsivo para desktop, tablet e celular.

---

## Para retomar o desenvolvimento com IA em sessões futuras

Se precisar de modificações ou ajustes futuros usando assistente de IA (Claude, ChatGPT, etc.), compartilhe o link público desta calculadora ou cole o conteúdo do `index.html` e use um prompt do tipo:

> "Sou Júnior Arrais, advogado trabalhista e previdenciário do escritório Arrais Advogados (Ubá/MG). Construí esta calculadora de rescisão trabalhista hospedada em https://juniorarrais90.github.io/calculadora-rescisao-arraisadvogados/. Ela tem 7 fases implementadas (identificação, modalidades, adicionais, descontos legais, simulação trabalhista, atualização monetária ADCs 58/59, PDFs). Padrão visual: paleta navy `#0D2340` + gold `#C9A84C`, fonte Inter. Preciso modificar [DESCREVA O QUE QUER ALTERAR]. Por favor, valide a fundamentação legal antes de implementar e mantenha o padrão visual e a arquitetura existente."

Em sessões futuras, o assistente lerá o código e o CHANGELOG.md para reconstituir o contexto completo do projeto.

---

## Limitações conhecidas

- O cálculo do FGTS histórico é uma estimativa simples (8% × salário-atual × meses), sem considerar variações salariais, juros do fundo ou saques. Para precisão total, confrontar com extrato real da Caixa.
- A atualização monetária utiliza uma única data base como média; para cálculos judiciais com cada parcela atualizada por sua data específica, recomenda-se complementar com planilhas oficiais do TST/TRT.
- O IRRF segue o regime caixa simples. Para grandes verbas retroativas pagas de uma vez, o regime RRA (Rendimentos Recebidos Acumuladamente, Lei 12.350/2010) pode ser mais favorável e exige cálculo complementar.

---

## Licença

Uso interno do escritório Arrais Advogados. Distribuição restrita. Documento institucional.

---

**Arrais Sociedade de Advogados** · OAB/MG nº 19.391 · CNPJ 60.284.876/0001-39
Rua Carlos Peixoto Filho, n.º 112, Salas 203, 204 e 209 · Ed. Otocy Vilela Eiras
Centro · Ubá/MG · CEP 36500-097
(32) 99844-6488 · contato@arraisadv.com.br
