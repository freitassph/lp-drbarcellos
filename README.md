# Landing Page — Dr. Warllon Barcellos

Landing page médica em React para apresentar a abordagem, a trajetória profissional e os canais de contato do Dr. Warllon Barcellos. A página é uma SPA estática em português brasileiro, com foco em neuropediatria e neurodesenvolvimento.

> A documentação descreve o que está implementado no repositório. Credenciais, especialidade, claims médicos, endereços, disponibilidade e direitos de imagem precisam de validação pelo responsável antes de publicação.

## Estado atual

- Build local de produção: aprovado em 2026-08-11.
- TypeScript estrito: aprovado em 2026-08-11.
- Runtime local observado: desktop `1440×1000` e mobile `390×844`.
- Branch padrão: `main`.
- Repositório: `https://github.com/freitassph/lp-drbarcellos`.
- URL pública real: `https://drbarcellos.vercel.app`.
- Estado público observado em 2026-08-11: HTTP 200, com título, seções, imagens e links de WhatsApp coerentes com o checkout analisado.
- Metadata antiga do GitHub: `https://land-page-dr-barcellos.vercel.app`, atualmente com `404 DEPLOYMENT_NOT_FOUND`.
- O runtime público foi observado, mas o repositório não contém configuração Vercel que prove sozinho qual commit foi publicado.

## O que a página entrega

A experiência atual possui cinco seções:

1. `#inicio` — hero com a mensagem “Clareza para acolher”, retrato, CRM exibido e CTA para agendamento.
2. `#metodo` — abordagem em três etapas: anamnese, avaliação neuropsicomotora e estratégia terapêutica.
3. `#sobre` — apresentação profissional, biografia e credenciais exibidas.
4. `#agendamento` — três opções de contato: online, São José de Ubá/RJ e Miracema/RJ.
5. `#faq` — orientações sobre primeira consulta, plano de saúde, documentos e exames.

O footer reúne Instagram, links de contato e navegação interna.

## Conversão real

A página não possui agenda integrada nem formulário. O fluxo é:

```text
CTA interno → seção de agendamento → link wa.me → conversa no WhatsApp
```

Os links de WhatsApp usam mensagens pré-preenchidas definidas em `utils/constants.ts`. Esse fluxo representa um pedido de contato; ele não reserva horário nem confirma consulta.

Modalidades exibidas:

| Modalidade | Destino implementado |
|---|---|
| Atendimento online | WhatsApp com mensagem específica para consulta online |
| São José de Ubá/RJ | WhatsApp com mensagem para atendimento presencial |
| Miracema/RJ | WhatsApp com mensagem para atendimento presencial |

## Stack

- React 18
- React DOM 18
- TypeScript 5
- Vite 6.4.5
- Lucide React
- Tailwind CSS carregado por CDN
- Google Fonts: Montserrat e Playfair Display

O projeto não possui backend, banco de dados, autenticação, API, analytics, formulário ou variável de ambiente obrigatória.

## Executar localmente

### Pré-requisitos

- Node.js 24.22.1.
- npm 12.2.1.

O runtime é definido em `.nvmrc` e `engines`; o lockfile canônico fixa o grafo para `npm ci --ignore-scripts`.

### Instalação e desenvolvimento

```bash
npm ci --ignore-scripts
npm run dev
```

O Vite exibirá a URL local no terminal, normalmente `http://localhost:5173`.

Não configure `GEMINI_API_KEY`: o código atual não usa Gemini nem qualquer outra chave de API.

### Build e preview

```bash
npm run build
npm run preview
```

### Typecheck

```bash
npx tsc --noEmit
```

Scripts disponíveis em `package.json`:

| Comando | Função |
|---|---|
| `npm run dev` | Inicia o Vite em desenvolvimento. |
| `npm run build` | Gera o bundle de produção em `dist/`. |
| `npm run preview` | Serve localmente o bundle gerado. |

Não há scripts de lint ou testes automatizados no estado atual.

## Estrutura do projeto

```text
.
├── AGENTS.md
├── App.tsx
├── README.md
├── components/
│   ├── About.tsx
│   ├── CTA.tsx
│   ├── FAQ.tsx
│   ├── FloatingElements.tsx
│   ├── Footer.tsx
│   ├── Header.tsx
│   ├── Hero.tsx
│   └── Methodology.tsx
├── index.html
├── index.tsx
├── metadata.json
├── package.json
├── tsconfig.json
├── utils/
│   └── constants.ts
└── vite.config.ts
```

### Arquivos centrais

- `App.tsx`: compõe as seções e controla scroll, seção ativa, reveal e menu mobile.
- `index.html`: concentra SEO, tokens visuais, Tailwind CDN, fontes e CSS global.
- `utils/constants.ts`: fonte central dos contatos e mensagens de WhatsApp.
- `components/CTA.tsx`: modalidades, endereços exibidos e links de contato.
- `components/FloatingElements.tsx`: componente existente, mas não renderizado por `App.tsx`.
- `AGENTS.md`: regras completas para agentes e futuras alterações.

## Design atual

A direção visual segue uma estética de luxo silencioso e editorial:

- navy profundo e off-white como base;
- verde sálvia como destaque;
- dourado pontual;
- Playfair Display em títulos;
- Montserrat em corpo e navegação;
- retratos verticais;
- espaços amplos e transições lentas.

Tokens principais definidos em `index.html`:

| Nome | Cor |
|---|---|
| `med-navy` | `#1B263B` |
| `med-sage` | `#66847D` |
| `med-sage-light` | `#E8EFED` |
| `med-offwhite` | `#F9F9F9` |
| `med-stone` | `#8C8C8C` |
| `luxury-gold` | `#C5A059` |

## Recursos e integrações externas

A LP depende dos seguintes serviços de terceiros:

- WhatsApp (`wa.me`) para contato;
- Instagram para os perfis externos;
- `i.ibb.co` para os retratos;
- `wsrv.nl` para a imagem Open Graph quadrada;
- Google Fonts para tipografia;
- Tailwind CDN para os estilos utilitários.

As imagens externas e a imagem social responderam com sucesso na verificação local de 2026-08-11. Isso não garante disponibilidade futura nem comprova direitos de uso.

## SEO atual

`index.html` contém:

- `<title>` e meta description;
- keywords;
- Open Graph para compartilhamento;
- Twitter card;
- imagem social 1200×1200;
- favicon SVG inline;
- idioma `pt-BR`.

Ainda não existem canonical, `og:url`, JSON-LD, `robots.txt` ou `sitemap.xml`. As tags `itemprop` comentadas como Schema.org não substituem JSON-LD.

## Conteúdo médico e governança

A página comunica identidade profissional, CRM, titulações, especialidade, metodologia clínica, telemedicina, duração de consulta, reembolso e outros claims. O repositório não possui hoje fontes versionadas, registro de RQE, ledger de claims, data de revisão clínica ou aprovação regulatória.

Antes de publicar ou modificar conteúdo médico:

- verificar identidade, CRM e RQE aplicável;
- validar titulações e vínculos;
- associar cada claim material a fonte e revisor humano;
- revisar publicidade médica e CFM/CODAME;
- confirmar endereços, contatos e modalidades;
- confirmar o provider real antes de afirmar “Plataforma Digital Segura”;
- manter pedido de contato separado de agendamento confirmado;
- documentar direitos de uso das imagens.

A página não deve diagnosticar, prescrever, realizar triagem clínica ou substituir consulta.

## Dados e privacidade

No runtime local observado, a LP:

- não renderizou formulário ou input;
- não criou cookies próprios;
- não escreveu em `localStorage` ou `sessionStorage`;
- não carregou analytics ou pixels;
- encaminhou os contatos para o WhatsApp.

O WhatsApp é um serviço externo e pode receber dados pessoais ou de saúde durante a conversa. Não adicione sintomas, diagnósticos ou dados de crianças às mensagens pré-preenchidas. Qualquer formulário, CRM, analytics ou pixel futuro exige mapa de dados, finalidade, retenção, operadores e decisão humana de privacidade antes da implementação.

## Limitações conhecidas

- A metadata `homepageUrl` do GitHub está desatualizada e aponta para uma URL indisponível; a URL pública real é `https://drbarcellos.vercel.app`.
- Há lockfile canônico; não há suíte de testes, lint ou CI.
- A instalação npm observada em 2026-08-11 reportou 1 vulnerabilidade moderada e 1 alta; a ausência de lockfile impede uma triagem determinística e nenhuma correção forçada foi aplicada.
- Tailwind depende do CDN.
- O import map de `index.html` aponta para versões diferentes das declaradas em `package.json`.
- O botão flutuante de WhatsApp existe no código, mas não está montado.
- Menu mobile e FAQ têm gaps de teclado, foco e ARIA documentados em `AGENTS.md`.
- Não existe suporte a `prefers-reduced-motion`.
- Há textos auxiliares abaixo de tamanhos confortáveis de leitura.
- Claims e credenciais não têm evidência versionada no repositório.
- Imagens críticas dependem de hospedagem externa.
- SEO técnico e limites de privacidade/urgência ainda estão incompletos.

Esses itens são um inventário do estado atual, não uma autorização para mudanças fora do escopo de uma tarefa.

## Validação recomendada

Para qualquer alteração:

```bash
npm run build
npx tsc --noEmit
```

Mudanças visuais ou interativas também devem ser verificadas em desktop, tablet e mobile, cobrindo:

- navegação por âncoras;
- header em scroll;
- menu mobile e teclado;
- accordion do FAQ;
- URLs de WhatsApp sem envio de mensagem;
- console e falhas de rede;
- carregamento das imagens;
- overflow horizontal e reflow.

Consulte [AGENTS.md](./AGENTS.md) antes de editar, especialmente para claims médicos, dados, acessibilidade, SEO e publicação.

## Dependências e runtime — 23/10/2026

Node 24.22.1 (`.nvmrc`; plataformas: `engines.node=24.x`). npm 12.2.1, Vite 6.4.5, React 18.3.1 e override source-map-js 1.2.2; instalação congelada: `npm ci --ignore-scripts`. Valide com `node node_modules/typescript/bin/tsc --noEmit` e `npm run build`. As dependências locais não utilizadas autoprefixer, postcss e tailwindcss foram removidas; o Tailwind CDN e toda a fonte do produto de origin/main foram preservados. Os quatro commits locais de conteúdo/SEO/assets/rodapé não integram este candidato. A qualificação local de dependências compara o produto com a base remota; não certifica publicação ou conformidade clínica. Conteúdo, contatos, assets e regras do produto permanecem na base selecionada.
