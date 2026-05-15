# Casa do Lead — Documentação Completa do Projeto

Migração do site `www.casadolead.com.br` de WordPress + Elementor para **Astro + Vercel**.

**Repositório:** https://github.com/estouromarketing/casadolead  
**Site ao vivo:** https://www.casadolead.com.br  
**Criado por:** Estouro Marketing  
**Data:** Abril 2026

---

## Stack

| Camada | Tecnologia | Motivo |
|--------|-----------|--------|
| Framework | Astro 4 (static output) | Performance máxima — sem JS desnecessário |
| Hospedagem | Vercel | Deploy automático no push para `main` |
| CSS | CSS puro com Custom Properties | Sem overhead de framework |
| Animações | Intersection Observer nativo | Sem jQuery ou Animate.css |
| Lottie | lottie-web 5.x via CDN | Mesmo player do Elementor |
| Reviews | Trustindex (embed original) | Mesmos 5 reviews do Google |
| WhatsApp float | Botão customizado | Substitui plugin Joinchat |
| Analytics | Google Tag Manager (GTM-PQ2D6JQB) | Mantido igual ao WP |
| Fontes | Google Fonts — Outfit, DM Sans, Manrope | Idênticas ao design original |
| Newsletter | Formspree (configurar ID) | Grátis, sem backend |

---

## Design Tokens (extraídos do post-14.css do Elementor)

```css
--color-primary:  #000000   /* preto — fundo principal */
--color-orange:   #F5900D   /* laranja — CTAs e destaques */
--color-text:     #969696   /* cinza — texto corrido */
--color-white:    #FFFFFF   /* branco — texto em destaque */
--color-dark:     #101010   /* cinza escuro — seções alternadas */
--color-dark2:    #1A1A1A   /* cinza mais escuro — cards */
--color-gray:     #D8D8D8   /* cinza claro — bordas sutis */

--font-heading:   'Outfit', sans-serif       /* títulos — peso 700 */
--font-label:     'DM Sans', sans-serif      /* labels/etiquetas — 14px uppercase */
--font-body:      'Manrope', sans-serif      /* texto corrido — 15px peso 500 */

--container:      1280px   /* largura máxima */
--radius:         10px      /* bordas arredondadas */
```

---

## Estrutura de Arquivos

```
Casa-do-Lead/
├── package.json
├── astro.config.mjs          → output: static, site: casadolead.com.br
├── vercel.json               → buildCommand, outputDirectory: dist
├── tsconfig.json
├── .gitignore
├── public/
│   └── favicon.ico           → adicionar quando tiver
├── src/
│   ├── layouts/
│   │   └── Layout.astro      → HTML base, GTM, Google Fonts, Lottie CDN
│   ├── components/
│   │   ├── Header.astro      → nav sticky + Lottie + hamburger mobile
│   │   ├── Hero.astro        → H1, Lotties, lightbox YouTube, blob rotation
│   │   ├── Stats.astro       → 4 contadores animados
│   │   ├── Services.astro    → 4 cards de serviços
│   │   ├── About.astro       → história do Vicente + imagem
│   │   ├── Process.astro     → 3 passos numerados
│   │   ├── WhyUs.astro       → 3 diferenciais
│   │   ├── Testimonials.astro → Trustindex widget embed
│   │   ├── Blog.astro        → 2 posts (imagens do WP)
│   │   └── Footer.astro      → newsletter + contato + WhatsApp float
│   ├── pages/
│   │   ├── index.astro                    → página principal
│   │   ├── politica-de-privacidade.astro  → placeholder
│   │   └── termos-e-condicoes.astro       → placeholder
│   └── styles/
│       └── global.css        → design tokens, reset, classes utilitárias
└── PROJETO.md                → este arquivo
```

---

## Lottie Animations

| Localização | URL | Configuração |
|------------|-----|-------------|
| Header (logo/brand) | `https://lottie.host/ca10af4d-c8a8-43c0-b072-2516d0f60e3c/J1Q77MXQW6.json` | loop, oculto no mobile |
| Hero play button | `https://lottie.host/8d397d9f-0953-4ccc-b29d-c5ad96337e74/6Hhj1LpNMo.json` | link p/ YouTube lightbox, zoomIn delay 200ms |
| Hero decoração | `https://lottie.host/bc060a52-d9a1-4ced-b011-e026eb6169cc/9BvlclYIYv.json` | speed 0.7, fadeIn delay 700ms, offset (+30, +120) |
| Hero partícula | `https://lottie.host/3f17be2b-8e00-4907-8974-0c84bba291d7/Vv1pHISM6f.json` | absolute, speed 0.7, zoomIn delay 1100ms, offset (-30, 0) |

---

## Conteúdo das Seções

### Header
- Logo: texto "Casa do Lead" (substituir por `public/logo.png` quando disponível)
- Nav: Home, Nossos Serviços, Sobre Nós, Por que nos escolher?, Depoimentos, Blog
- WhatsApp no topo: `+55 11 94372-2083`

### Hero
- **H1:** Gere Leads Todos os Dias e Venda Mais...
- **Subtítulo:** Atraia clientes qualificados através de Gestão de Tráfego de alta performance e otimização estratégica do seu perfil no Google.
- **CTA:** "Quero uma Análise Gratuita do meu Negócio" → WhatsApp
- **YouTube:** `XHOmBV4js_E` (lightbox ao clicar no Lottie play)
- **Imagem:** `https://casadolead.com.br/wp-content/uploads/2026/01/Design-sem-nome-17-e1773407118504.png`

### Stats (contadores)
| Valor | Sufixo | Label |
|-------|--------|-------|
| 153 | — | Projetos Entregues |
| 80 | + | Projetos Concluídos |
| 1047 | K | Receita Gerada |
| 39 | + | Empresas Atendidas |

### Serviços
1. **Gestão de Tráfego Pago (Ads)** — Campanhas otimizadas no Google, Instagram e Facebook para gerar leads prontos para o comercial.
2. **Otimização de Google Meu Negócio (GMN)** — Seja a primeira opção no mapa! Colocamos sua empresa em destaque nas buscas locais, aumentando chamadas e rotas.
3. **Estratégias de Remarketing** — Não perca vendas. Reimpactamos quem já visitou seu site ou perfil, mantendo sua marca na mente do consumidor.
4. **Consultoria de Conversão** — Analisamos seu processo de vendas para garantir que o lead gerado se torne dinheiro no caixa.

### Processos (Benefícios)
- **01 Dominância Local** — Apareça para quem está perto de você e pronto para consumir.
- **02 Escala de Vendas** — Alcance novos públicos e estados com anúncios segmentados.
- **03 Dados, não achismos** — Relatórios claros que mostram o ROI (Retorno sobre o Investimento).

### Por que nos escolher
- Resultados, não relatórios
- Estratégias personalizadas
- Tecnologia + criatividade

### Depoimentos (Trustindex)
5 reviews reais do Google. Widget: dark-background, slider, language=pt.

| Revisor | Trecho |
|---------|--------|
| CS - BBL&CO Marketing para EPI | "Melhor GESTOR de GMN e ADS e ja tivemos ate hoje, parceria de sucesso..." |
| Breno Bana | "Fornecedor de EXCELENCIA! Recomendo 110%..." |
| Estouro Marketing | "Casa do Lead, Especializado em Google Ads, Meta ADS..." |
| Alexandre Schmidt | "Agradeço muito a parceria com a Casa do Lead, Vicente especialista..." |
| Lauane César - Marketing Digital | "Experiência muito satisfatória! Disponibilidade e eficiência..." |

### Blog
- **Post 1:** "Seu negócio está precisando de mais clientes? Vamos mudar esse cenário!" — 9 mar 2026 — ADS
  - Imagem: `https://casadolead.com.br/wp-content/uploads/2026/03/Design-sem-nome-14-300x300.jpg`
- **Post 2:** "Como Gerar Mais Leads para o Seu Negócio em 2026" — 9 mar 2026 — ADS
  - Imagem: `https://casadolead.com.br/wp-content/uploads/2026/03/Design-sem-nome-13-300x300.jpg`

### Footer
- **Newsletter:** formulário Formspree (ver seção configuração)
- **WhatsApp:** +55 11 94372-2083
- **E-mail:** contato@casadolead.com.br
- **Instagram:** @casadolead
- **Copyright:** © 2026 Casa do Lead. Criado por Estouro Marketing

---

## O que já está pronto (atualizado 2026-05-14)

| Item | Status |
|------|--------|
| Estrutura Astro completa (Header, Hero, Stats, Services, About, Process, WhyUs, Testimonials, Blog, Footer) | ✅ |
| Imagens locais em `public/images/` (hero, sobre, blog-1, blog-2) | ✅ |
| Logo CL hexagonal no header (`logo-icon.png`) | ✅ |
| Ícones laranja nos stats (`icon-9` a `icon-12`) | ✅ |
| Ícones brancos WP nos cards de serviços (`icon-13` a `icon-16`) | ✅ |
| About: texto "Por que Casa do Lead?" + foto correta do Vicente | ✅ |
| Blog: título "Novidades" + botões "Fale com a Gente" / "Nosso Blog" | ✅ |
| Services: parágrafo intro + botão CTA "O plano ideal para seu sucesso..." | ✅ |
| GTM (GTM-PQ2D6JQB) instalado | ✅ |
| Trustindex widget (5 reviews Google) | ✅ |
| Animações de entrada (Intersection Observer) | ✅ |
| Lottie animations (hero play, deco, particle, header) | ✅ |
| YouTube lightbox | ✅ |
| WhatsApp float button | ✅ |
| Responsive mobile | ✅ |

## Pendências para terminar

### 🔴 Crítico (obrigatório antes de ir ao ar)

**1. Logo com fundo transparente**
O arquivo `public/images/logo-icon.png` (Design-sem-nome-16.png) tem fundo branco — aparece como um badge branco no header escuro. Pedir ao Vicente/designer um PNG com fundo transparente (só o hexágono CL). Depois substituir o arquivo e ajustar o CSS se necessário.

**2. Vercel — linkar o projeto**
O repositório `estouromarketing/casadolead` ainda não está importado no Vercel.
1. Vercel Dashboard → **Add New → Project**
2. **Import Git Repository** → `estouromarketing/casadolead`
3. Framework: **Astro** (detecta automático)
4. Clicar em **Deploy**

**3. Formspree — newsletter no footer**
1. Criar conta gratuita em https://formspree.io
2. Criar novo formulário → copiar o ID (ex: `xpzgwqrj`)
3. Editar `Footer.astro` — substituir `SEU_FORM_ID`:
```html
action="https://formspree.io/f/SEU_FORM_ID"
```

### 🟡 Importante

**4. Favicon**
Substituir `public/favicon.ico` pelo ícone hexagonal CL da Casa do Lead.
Converter `logo-icon.png` (só o hexágono) para `.ico` em https://favicon.io

**5. Domínio no Vercel**
Após o deploy:
1. Vercel → projeto casadolead → Settings → Domains
2. Adicionar `www.casadolead.com.br` e `casadolead.com.br`
3. No painel DNS: CNAME `www` → `cname.vercel-dns.com`
4. A raiz `@` → IP `76.76.21.21`

### 🟢 Opcional

**6. Blog interno**
Posts atualmente apontam para `#`. Para ativar páginas reais: criar `src/pages/blog/[slug].astro` com Astro Content Collections.

**7. Política de Privacidade / Termos**
Preencher conteúdo real em:
- `src/pages/politica-de-privacidade.astro`
- `src/pages/termos-e-condicoes.astro`

**8. Ícones dos serviços — verificar ordem**
Os ícones brancos `icon-13` a `icon-16` foram atribuídos aos 4 serviços em sequência. Confirmar visualmente se cada ícone faz sentido com seu serviço (só aparecem em fundo escuro).

### 6. Domínio no Vercel
1. Vercel Dashboard → projeto casadolead → Settings → Domains
2. Adicionar `www.casadolead.com.br` e `casadolead.com.br`
3. No painel DNS: apontar CNAME `www` para `cname.vercel-dns.com`
4. Apontar `@` (raiz) para IP do Vercel: `76.76.21.21`

---

## Deploy

### Primeira vez
```bash
# No Vercel via browser:
# 1. Acessar vercel.com → Import Project
# 2. Conectar GitHub → selecionar estouromarketing/casadolead
# 3. Framework: Astro (detectado automaticamente)
# 4. Build: npm run build → Output: dist/
# 5. Deploy!
```

### Atualizações
```bash
git add .
git commit -m "feat: descrição da mudança"
git push origin main
# → Vercel faz deploy automático
```

### Dev local
```bash
npm install
npm run dev
# Acesse: http://localhost:4321
```

---

## Animações de Entrada

Todas as seções usam a classe `.anim-hidden` com variações:
- `.anim-left` → entra da esquerda
- `.anim-right` → entra da direita
- `.anim-zoom` → aparece em zoom

Controlado por Intersection Observer em `src/pages/index.astro`.

Delay via CSS custom property: `style="--delay:200ms"`

---

## Google Tag Manager

Já configurado no `Layout.astro`. Container: **GTM-PQ2D6JQB**

Para adicionar eventos (ex: clique no CTA), criar triggers no GTM sem mexer no código.

---

## Trustindex

O widget usa o embed original exportado do plugin WordPress.  
Se as reviews mudarem no Google, o Trustindex atualiza automaticamente (ele busca da API Google).  
Para atualizar manualmente: copiar o novo HTML do template do plugin WP e substituir o `<template>` em `Testimonials.astro`.

---

## Imagens

Atualmente as imagens do hero e blog são servidas direto da URL do WordPress (`casadolead.com.br/wp-content/uploads/`). Isso funciona enquanto o WP estiver ativo.

**Para independência total do WP:**
1. Baixar as imagens:
   - `Design-sem-nome-17-e1773407118504.png` (hero/sobre)
   - `Design-sem-nome-14.jpg` (blog post 1)
   - `Design-sem-nome-13.jpg` (blog post 2)
2. Colocar em `public/images/`
3. Atualizar os `src` nas componentes para `/images/nome-do-arquivo.png`

---

## WhatsApp Float

Botão fixo no canto inferior direito. Configurado em `Footer.astro`.

- Número: `5511943722083`
- Mensagem pré-preenchida: _"Olá *Especializados em Leads Qualificados*! Preciso de mais informações..."_

Para mudar a mensagem, editar o `href` do `.whatsapp-float` em `Footer.astro`.
