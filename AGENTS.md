# AGENTS.md — LP Dr. Warllon Barcellos

## Escopo e precedência

Este arquivo governa todo o repositório `lp-drbarcellos`. Ele deve ser lido antes de qualquer análise, alteração, teste, commit, publicação ou operação externa.

- Instruções do sistema, do usuário e da organização prevalecem sobre este arquivo.
- Preserve alterações existentes no worktree e mantenha o escopo restrito a esta landing page.
- Não faça commit, push, deploy, alteração de domínio, envio de mensagem, criação de lead ou mutação em serviço externo sem autorização explícita.
- Não misture fatos, assets, copy, credenciais, contatos ou decisões de outros clientes da Freitas.Lab.
- O código e o runtime observado têm precedência sobre documentação antiga. Quando houver divergência, corrija a documentação no mesmo trabalho autorizado.

## Identidade do projeto

- Repositório remoto: `https://github.com/freitassph/lp-drbarcellos`
- URL pública real: `https://drbarcellos.vercel.app`
- Branch padrão: `main`
- Tipo: landing page médica pública, estática e single-page.
- Idioma atual: português brasileiro (`pt-BR`).
- Profissional apresentado pela página: Dr. Warllon Barcellos.
- Área comunicada: neuropediatria, neurodesenvolvimento e atendimento infantil.
- Público inferido pela copy: familiares e responsáveis por crianças que procuram avaliação e acompanhamento.
- Direção visual declarada: `Silent Luxury`, com linguagem editorial, clínica e acolhedora.
- Conversão primária real: iniciar contato administrativo pelo WhatsApp.
- Modalidades exibidas: atendimento online, São José de Ubá/RJ e Miracema/RJ.

As informações acima descrevem o que o código publica. Elas não constituem verificação independente de identidade, CRM, RQE, titulação, especialidade, endereço, disponibilidade, segurança de plataforma ou conteúdo clínico.

## Contrato real de conversão

A landing page não contém agenda, formulário, backend, CRM, confirmação de horário ou telemedicina embutida.

1. CTAs do header e do hero fazem scroll para `#agendamento`.
2. Os cards de atendimento e os links do footer abrem URLs `wa.me` em nova aba.
3. As URLs carregam mensagens pré-preenchidas para online, São José de Ubá ou Miracema.
4. O clique representa apenas início de contato ou pedido de agendamento.
5. Nunca descreva esse fluxo como horário reservado, consulta confirmada ou atendimento iniciado.

Não clique nem envie mensagens em testes automatizados sem autorização. Valide o `href`, o número, o texto codificado, `target="_blank"` e `rel="noopener noreferrer"` sem produzir efeito externo.

## Estado técnico atual

### Stack efetiva

- React `18.x` e React DOM `18.x` declarados em `package.json`.
- TypeScript em modo estrito, sem emissão, configurado em `tsconfig.json`.
- Vite `5.x` com `@vitejs/plugin-react`.
- Lucide React para ícones.
- Tailwind CSS carregado no navegador por `https://cdn.tailwindcss.com`.
- Tokens, animações, breakpoints e estilos globais definidos inline em `index.html`.
- Google Fonts para `Montserrat` e `Playfair Display`.

Não existe atualmente:

- backend ou API própria;
- roteador;
- state manager global;
- banco de dados;
- autenticação;
- formulário ou campo de entrada;
- analytics, pixel, tag manager ou session replay;
- cookie próprio, `localStorage` ou `sessionStorage` usado pela aplicação;
- variável de ambiente ou integração com Gemini;
- suíte de testes, lint script ou CI versionada;
- configuração local de deploy, domínio, `vercel.json` ou workflow GitHub Actions;
- lockfile versionado.

### Atenção à resolução de dependências

`package.json` é a fonte de verdade para o build local. O `importmap` de `index.html` referencia React 19, Vite 7 e outras versões hospedadas em `esm.sh`, enquanto o projeto local declara React 18 e Vite 5. No runtime Vite observado, os módulos são empacotados a partir das dependências locais; não trate o import map como versão efetiva sem provar seu uso.

Tailwind está presente como dependência de desenvolvimento, mas a UI atual depende do CDN e da configuração inline de `index.html`; não existe `tailwind.config.*`, arquivo CSS de entrada ou pipeline PostCSS conectado ao app. Migrar do CDN é uma mudança arquitetural e visual, não uma limpeza automática.

## Mapa de arquivos

| Arquivo | Responsabilidade atual |
|---|---|
| `index.html` | Head, SEO social, favicon inline, fontes, Tailwind CDN, tokens, animações, estilos globais e elemento `#root`. |
| `index.tsx` | Bootstrap do React em `StrictMode`. |
| `App.tsx` | Ordem das seções, estado do header/menu e observers de scroll/reveal. |
| `components/Header.tsx` | Header fixo, navegação por âncoras e menu mobile. |
| `components/Hero.tsx` | Primeira dobra, proposta de valor, identidade, retrato e CTA interno. |
| `components/Methodology.tsx` | Três etapas da abordagem clínica comunicada. |
| `components/About.tsx` | Biografia, retrato e credenciais exibidas. |
| `components/CTA.tsx` | Cards das três modalidades e links de contato pelo WhatsApp. |
| `components/FAQ.tsx` | Accordion com quatro perguntas frequentes. |
| `components/Footer.tsx` | Marca, CRM exibido, Instagram, contatos e navegação. |
| `components/FloatingElements.tsx` | Botão flutuante de WhatsApp existente, mas não montado por `App.tsx`. |
| `utils/constants.ts` | Números, mensagens e URLs de WhatsApp. |
| `metadata.json` | Metadados descritivos herdados do gerador; não controla o `<head>` do Vite. |
| `package.json` | Dependências e scripts disponíveis. |
| `tsconfig.json` | Contrato TypeScript. |
| `vite.config.ts` | Configuração mínima do Vite/React. |
| `README.md` | Documentação operacional e de produto; deve permanecer sincronizada. |

## Arquitetura da página

Ordem renderizada por `App.tsx`:

1. `Header`
2. `Hero` — `#inicio`
3. `Methodology` — `#metodo`
4. `About` — `#sobre`
5. `CTA` — `#agendamento`
6. `FAQ` — `#faq`
7. `Footer`

O `IntersectionObserver` de `App.tsx` mantém a seção ativa do menu e adiciona classes de reveal. O listener de scroll usa `requestAnimationFrame` e considera o header em estado reduzido após 30 px. A navegação calcula offset fixo de 80 px.

Ao adicionar, remover ou renomear uma seção, sincronize obrigatoriamente:

- o `id` da seção;
- o menu desktop;
- o menu mobile;
- a navegação do footer;
- a lógica de seção ativa;
- qualquer CTA ou teste que aponte para a âncora.

## Conteúdo e claims que exigem governança

A página contém publicidade e conteúdo médico. Trate cada afirmação como dado regulado que precisa de fonte e responsável humano antes de publicação. O repositório atual não contém registro de identidade, ledger de claims, fontes clínicas, data de revisão ou aprovação CFM/CODAME.

### Identidade e credenciais exibidas

- nome `Dr. Warllon Barcellos`;
- CRM-RJ `52.135959-2`;
- uso de `Neuropediatra`;
- doutorado/PhD pela UENF;
- pós-graduação em Neuropediatria pelo IBCMED;
- docência universitária;
- experiência acadêmica descrita como ampla/vasta.

Antes de alterar ou reforçar essas informações:

- valide o nome e o CRM em fonte oficial aplicável;
- valide se a especialidade anunciada exige e possui RQE e como deve ser exibida;
- valide titulações e instituições com documento ou fonte aprovada pelo responsável;
- mantenha identidade visível, metadata e eventual schema coerentes;
- não invente RQE, cargo, especialidade, formação ou vínculo institucional ausente.

### Claims clínicos e operacionais visíveis

Entre as afirmações que exigem revisão estão:

- foco em TEA, TDAH e neurodesenvolvimento na meta description/keywords;
- uso de protocolos internacionais atribuídos à SBNI;
- avaliação de habilidades cognitivas, motoras e sensoriais;
- construção de estratégia terapêutica e orientação de família/escola/equipe;
- consulta inicial com duração média de 60 minutos;
- atendimento exclusivamente particular e emissão de documentos para reembolso;
- encaminhamento para parceiros de excelência técnica;
- equivalência de atenção e rigor entre atendimento online e presencial;
- expressão `Plataforma Digital Segura`;
- endereços, modalidades e disponibilidade de atendimento.

Não transforme linguagem institucional em garantia de diagnóstico, resultado, cura, precisão absoluta, disponibilidade, segurança ou reembolso. Fonte relacionada não basta: ela precisa sustentar a frase exata, no contexto exato.

## Fronteiras médicas, CFM e atendimento

- A LP deve informar e facilitar contato; não deve diagnosticar, prescrever, triar ou substituir consulta.
- Conteúdo clínico material precisa de fonte, revisor humano competente, data de revisão, limite e gatilho de revalidação.
- Ambiguidade sobre publicidade médica deve ser encaminhada para decisão humana CFM/CODAME; automação não certifica conformidade.
- Atendimento online é uma modalidade distinta. WhatsApp não é a consulta nem comprova uma plataforma de telemedicina segura.
- A página atende público ligado a menores. Evite coletar sintomas, diagnósticos ou detalhes da criança no primeiro contato quando não forem necessários.
- Não solicite urgências pelo WhatsApp. Se for adicionada orientação de emergência, ela deve ser aprovada pelo serviço e testada como fluxo separado.
- Imagens do profissional estão em hospedagem externa. Antes de publicar novas imagens, registre origem, autorização, direitos de uso, integridade e prazo de licença.
- Não use imagem de paciente, depoimento, antes/depois ou repost sem análise específica e autorização documentada.

## Dados, privacidade e terceiros

No runtime local observado em 2026-08-11, a página não criou cookies nem chaves em storage e não renderizou formulários. Isso não significa ausência de tratamento por terceiros.

Serviços externos atuais:

- `wa.me`: destino de todos os pedidos de contato/agendamento;
- Instagram: perfis do profissional e da Freitas.Lab;
- `i.ibb.co`: hospedagem dos dois retratos;
- `wsrv.nl`: transformação da imagem Open Graph;
- Google Fonts: fontes remotas;
- Tailwind CDN: geração de estilos no navegador;
- `esm.sh`: referências presentes no import map, embora não observadas como recurso efetivo no runtime Vite local.

Qualquer analytics, pixel, CRM, formulário ou intake futuro exige, antes da implementação:

- mapa de campos e eventos;
- finalidade e necessidade de cada dado;
- classificação de dado pessoal/sensível;
- destino, operadores e acessos;
- retenção, correção e exclusão;
- decisão humana sobre base legal aplicável;
- garantia de que sintomas, diagnósticos e interesse de saúde não vazem para URL, analytics, logs ou publicidade.

Não registre em logs, screenshots, issues ou documentação dados de pacientes, responsáveis, conversas de WhatsApp ou inferências de saúde.

## Sistema visual atual

### Conceito

O código implementa uma estética editorial de luxo silencioso: muito espaço em branco, serifas de alto contraste, navy profundo, verde sálvia, retratos verticais e animações lentas. Preserve essa direção em correções pontuais; mudanças de identidade exigem decisão explícita.

### Tokens principais

Definidos em `index.html`:

| Token | Valor |
|---|---|
| `med-navy` | `#1B263B` |
| `med-sage` | `#66847D` |
| `med-sage-light` | `#E8EFED` |
| `med-offwhite` | `#F9F9F9` |
| `med-stone` | `#8C8C8C` |
| `luxury-gold` | `#C5A059` |
| `border-line` | `rgba(27, 38, 59, 0.06)` |

Tipografia:

- display/editorial: `Playfair Display`;
- corpo/navegação: `Montserrat`.

Layout:

- container amplo do hero/header: até `90rem`;
- demais seções: até `7xl`;
- breakpoint customizado `xs`: `375px`;
- divisão principal em grid de 12 colunas no desktop;
- retratos com proporções aproximadas de `3.8/5` e `3.5/5`.

Motion:

- reveal por opacity/translate;
- zoom sutil de 20 segundos no hero;
- transições longas com easing `luxury`;
- scroll suave controlado por JavaScript e CSS.

## Acessibilidade: baseline e gaps conhecidos

Não declare conformidade WCAG apenas porque o build passa. O runtime observado mostrou lacunas reais:

- o menu mobile fechado mantém o botão de fechar e seus links na ordem de tabulação;
- `Escape` não fecha o menu;
- o foco não retorna ao botão que abriu o menu;
- não há `role="dialog"`, `aria-modal`, `aria-expanded` ou `aria-controls` para o menu;
- o accordion do FAQ não expõe `aria-expanded` nem `aria-controls`;
- o FAQ remove outline sem fornecer foco visível equivalente;
- não há skip link;
- não há tratamento de `prefers-reduced-motion` para reveal, zoom e transições;
- existem textos de 6–10 px e trechos justificados, que merecem revisão de legibilidade;
- elementos decorativos e alguns ícones não têm governança ARIA explícita.

Ao tocar nesses componentes, cubra teclado, foco visível, ordem de foco, `Escape`, retorno de foco, semântica do accordion, reflow a 320 px, zoom a 200%, contraste e redução de movimento. Não esconda os gaps apenas na documentação; implemente e teste quando a correção estiver em escopo.

## SEO e compartilhamento

`index.html` contém title, description, keywords, Open Graph, Twitter card, favicon inline e tags itemprop. A imagem social usa `wsrv.nl` para gerar JPEG quadrado de 1200×1200 a partir do retrato remoto.

Gaps atuais que não devem ser reportados como resolvidos:

- ausência de canonical e `og:url`;
- ausência de JSON-LD;
- ausência de `robots.txt` e `sitemap.xml` no repositório;
- ausência de autoria/revisor/data de revisão para conteúdo médico;
- dependência de imagem e proxy externos;
- metadata contém claims que não possuem fontes versionadas no projeto;
- comentário `Schema.org for Google+` não equivale a dados estruturados JSON-LD.

Se adicionar schema, use somente fatos visíveis e verificados. Não invente especialidade, RQE, organização, avaliações, horários, preço ou localização.

## Estado de deploy e publicação

A URL pública real informada pelo owner e observada com HTTP 200 em 2026-08-11 é `https://drbarcellos.vercel.app`. O runtime público apresentou o mesmo título, seções, imagens e links de WhatsApp do checkout analisado, sem erros de console ou requisições falhas nos cenários exercitados.

O campo `homepageUrl` do GitHub ainda aponta para a URL antiga `https://land-page-dr-barcellos.vercel.app`, que respondeu `404 DEPLOYMENT_NOT_FOUND` na mesma data. Trate essa metadata como desatualizada. O repositório não contém configuração Vercel versionada, portanto o vínculo exato entre projeto Vercel e commit não pode ser inferido apenas do checkout.

- Build local verde não prova deploy.
- HTTP 200 isolado não provaria a versão correta.
- Não altere projeto, domínio ou alias na Vercel sem autorização.
- Em publicação autorizada, prove: commit selecionado, SHA remoto, status do provedor, URL final, conteúdo/asset principal e jornada de contato no runtime público.
- Registre monitoramento e rollback para o último commit seguro. Prefira `git revert` a operações destrutivas.

## Fluxo obrigatório para mudanças

### Antes de editar

1. Rode `git status --short --branch`.
2. Leia este arquivo, `README.md`, `package.json`, `index.html`, `App.tsx` e todos os componentes afetados.
3. Classifique a mudança: conteúdo, identidade, claim médico, CTA, design, acessibilidade, SEO, integração ou release.
4. Inventarie todas as superfícies equivalentes antes de alterar algo repetido.
5. Defina evidência e critério de aceite proporcionais ao risco.

### Durante a edição

- Faça a menor mudança causal suficiente.
- Preserve stack, comportamento e tokens existentes quando não forem o objeto da tarefa.
- Centralize números e mensagens de WhatsApp em `utils/constants.ts`.
- Não duplique identidade, endereço ou contato sem sincronizar todas as ocorrências.
- Não adicione dependência sem justificar necessidade, versão e impacto no bundle.
- Não exponha segredos; este projeto não precisa de `GEMINI_API_KEY`.
- Não converta pedido de contato em promessa de agendamento.
- Não reative `FloatingElements` sem revisar sobreposição, z-index, redundância de CTA e acessibilidade.

### Validação mínima

O projeto não possui lockfile; `npm ci` não é aplicável. Depois de instalar dependências com npm, rode:

```bash
npm run build
npx tsc --noEmit
```

Não existem scripts de lint ou testes hoje. Se a mudança incluir lógica não trivial, adicione cobertura adequada em vez de afirmar que testes inexistentes passaram.

Na resolução instalada em 2026-08-11, o npm reportou 2 vulnerabilidades, sendo 1 moderada e 1 alta. A ausência de lockfile impede reproduzir e triar esse resultado de forma determinística com `npm audit`. Não rode `npm audit fix --force` como correção automática; primeiro identifique pacote, cadeia, explorabilidade, versão segura e regressões.

Para alterações visuais ou interativas, valide pelo menos:

- desktop `1440×1000`;
- tablet em largura intermediária;
- mobile `390×844` e reflow próximo de 320 px;
- navegação por âncoras e offset do header;
- menu mobile aberto/fechado, teclado, `Escape` e retorno de foco;
- accordion do FAQ;
- CTAs e URLs de WhatsApp sem enviar mensagem;
- imagens, fontes, console e falhas de rede;
- ausência de overflow horizontal;
- redução de movimento quando implementada.

Use `domcontentloaded` e asserts de UI/rota para browser QA; não dependa de `networkidle` em páginas com recursos externos persistentes.

### Encerramento

- Revise `git diff --check`, `git diff --stat` e o diff completo.
- Confirme que nenhum arquivo fora do escopo foi alterado.
- Atualize `README.md` e este `AGENTS.md` quando arquitetura, comandos, contatos, claims, seções, integrações ou deploy mudarem.
- Separe no relato final: código local, runtime local, Git remoto, deploy externo, decisões humanas pendentes e blockers.

## Backlog conhecido, não autorizado automaticamente

Estes itens foram observados e devem orientar futuras tarefas; sua existência não amplia o escopo atual:

1. Metadata `homepageUrl` do GitHub desatualizada; a URL antiga retorna `DEPLOYMENT_NOT_FOUND`, enquanto a URL real é `https://drbarcellos.vercel.app`.
2. Ausência de lockfile e instalação não determinística.
3. Ausência de testes, lint e CI.
4. Instalação atual reporta 1 vulnerabilidade moderada e 1 alta, ainda sem triagem determinística.
5. Tailwind em CDN apesar das dependências locais.
6. Import map divergente das versões de `package.json`.
7. `FloatingElements.tsx` não montado e `WA_LINK` geral sem uso no app.
8. Gaps de teclado/foco/ARIA no menu mobile e FAQ.
9. Ausência de reduced-motion.
10. Textos muito pequenos em metadados visuais.
11. Claims médicos e de credenciais sem ledger/fontes/revisão versionados.
12. Ausência de RQE visível ou registro da decisão aplicável.
13. `Plataforma Digital Segura` sem provider ou prova no repositório.
14. Ausência de página/aviso de privacidade, limites do WhatsApp e orientação de urgência.
15. SEO sem canonical, `og:url`, JSON-LD, robots e sitemap.
16. Imagens críticas e OG dependentes de terceiros.
17. Estratégia de deploy e vínculo provider/commit não documentados no repositório.

## Definição de pronto

Uma tarefa só está pronta quando:

- o comportamento solicitado foi implementado no escopo correto;
- build e typecheck aplicáveis passaram;
- o runtime relevante foi observado quando a mudança é visual/interativa;
- claims, identidade e dados possuem decisão humana quando aplicável;
- nenhuma conversão externa foi executada sem autorização;
- riscos residuais e verificações não realizadas foram declarados;
- documentação e código estão coerentes;
- publicação só é declarada se o provedor e a URL pública foram verificados separadamente.
