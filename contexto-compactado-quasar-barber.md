# Contexto Compactado — Site Quasar Barber (Landing Page)

**Data da compactação:** 2026-05-31
**Chat original:** ~2 sessões acumuladas, ~35 trocas totais

---

## 1. Objetivo

Construir e refinar uma landing page profissional para a **Quasar Barber**, distribuidora premium de produtos para barba e cabelo em Codó, MA. Site single-file HTML com CSS e JS embutidos, responsivo para mobile, no ar via Netlify com auto-deploy do GitHub.

---

## 2. Decisões Tomadas

- **Single HTML file:** Todo CSS e JS inline em `quasar-barber.html` — sem bundler, sem framework.
- **Fontes:** Bebas Neue (títulos) + Barlow Condensed (UI) + Barlow (corpo) — Google Fonts.
- **Paleta:** `--gold: #ffcc00` / `--black: #080808` com 4 variantes. `--text-dim: #888` (WCAG AA corrigido de #666).
- **Hero sem foto:** CSS puro — gradientes radiais gold + "Q" gigante outline + anéis + marcadores de canto. `hero-bg.png` existe mas não está em uso.
- **Produto cards:** `.prod-visual` (área da imagem) → fundo `#ffffff`. `.prod-card` (área de info) → fundo `var(--black-3)`. Textos da info em branco/gold. *Nota: tentamos fundo branco no card inteiro — ficou ruim. Revertido para só a área da imagem ser branca.*
- **Instagram grid:** 6 tiles com fotos reais de produto. Cada tile é `<a>` linkando para `instagram.com/quasar_barber`. Hover: overlay escuro semi-transparente + ícone gold + label branco + zoom 1.05x.
- **SEO:** OG tags completas (`og:image` usa `insta-greencoffee.png`). Twitter card `summary_large_image`. `rel="canonical"`.
- **Formulário contato:** Netlify Forms com `netlify` attribute. Submit via `fetch` — inline success state, sem redirect. Campos: Nome, WhatsApp, Mensagem.
- **Links:** Todos os `javascript:void(0)` resolvidos. Categorias → `#produtos`. Footer Linhas → `#produtos`/`#kits`. Sobre → `#sobre`. Contato → `#contato`.
- **`id="contato"`** está na `<section class="contato-section">`, não no `<footer>`.
- **Git identity:** `user.name = felpquasar` / `user.email = quasarbarber01@gmail.com` (local no repo).
- **GitHub:** `https://github.com/felpquasar/quasar-barber-site` — branch `main`.
- **Deploy:** Netlify auto-deploy a cada `git push origin main`. URL: `https://quasar-barber.netlify.app/`.

---

## 3. Estado Atual

Site completo e no ar. Todas as seções implementadas e funcionais:

- Nav fixo (scroll-state) + hamburger mobile
- Hero CSS-only (decoração geométrica)
- Marquee de marcas (gold)
- Grid de categorias (6 cards → `#produtos`)
- Seção Protocolo Quasar (step dots sincronizados)
- Stats bar (dourada, 4 números)
- Produtos em destaque (grid 3-col → 1-col mobile, 5 cards com imagens reais)
- Avaliações (3 cards)
- **Seção Sobre** (`id="sobre"`) — texto + 3 cards de valor (Qualidade, Agilidade, Atendimento)
- **Grid Instagram** — 6 fotos reais, todos tiles linkam para Instagram
- **Seção Contato** (`id="contato"`) — info de contato + Netlify Form
- Footer (4 colunas → 1 coluna mobile)
- WhatsApp float button
- Animações fade-up com IntersectionObserver
- `prefers-reduced-motion` implementado
- SEO Open Graph completo

**Último commit:** `3ce02ad` — docs: add compacted chat context file

---

## 4. Arquivos e Artefatos Relevantes

| Arquivo | Status | Descrição |
|---------|--------|-----------|
| `quasar-barber.html` | Em uso | Site completo — HTML + CSS + JS |
| `prod-kit-barba.png` | Em uso | Card principal "Mais Vendido" (hero card) |
| `prod-oleo-qod.webp` | Em uso | Óleo Para Barba QOD 25ml |
| `prod-balm fox for man.png` | Em uso | Balm Hidratante Fox For Men |
| `prod-lemon-gin.webp` | Em uso | Loção Pós Barba Lemon Gin QOD |
| `prod-kit-whisky.webp` | Em uso | Kit Shampoo Whisky + Carteira QOD |
| `insta-pomadas.png` | Em uso | Tile Instagram — Fox For Men pomadas na mão |
| `insta-lifestyle.jpeg` | Em uso | Tile Instagram — QOD Whisky no balcão (og:image) |
| `insta-greencoffee.png` | Em uso | Tile Instagram — QOD Green Coffee (og:image) |
| `insta-kitbarba.jpeg` | Em uso | Tile Instagram — Fox For Men Kit Barba |
| `insta-capilar.jpeg` | Em uso | Tile Instagram — Fox For Men Spray Capilar |
| `insta-qod.png` | Em uso | Tile Instagram — QOD Anticaspa/Loção/Condicionador |
| `hero-bg.png` | No disco, não usado | Foto original do hero — candidata ao passo 5 |
| `contexto-compactado-quasar-barber.md` | No repo | Este arquivo |
| `.gitignore` | Em uso | `.DS_Store`, `Thumbs.db`, etc. |

**Origem das fotos Instagram:** `D:\Quasares\Criativos\` (pasta local com mais criativos disponíveis)

---

## 5. Informações do Negócio

```
Marca:       Quasar Barber
Cidade:      Codó, Maranhão
WhatsApp:    5599992007182  (wa.me/5599992007182)
Instagram:   @quasar_barber (instagram.com/quasar_barber)
Email git:   quasarbarber01@gmail.com
GitHub user: felpquasar
Site:        https://quasar-barber.netlify.app/
```

**Marcas:** Fox For Men, QOD Barber Shop
**Produtos no site:** Kit Barba (R$89,90), Óleo QOD (R$34,90), Balm Fox (R$32,90), Loção Lemon Gin (R$39,90), Kit Whisky+Carteira (R$49,90)

---

## 6. Erros e Armadilhas Conhecidas

- **Fundo branco no card inteiro ficou ruim** — textos brancos (nome, descrição) ficavam invisíveis sobre branco. Solução correta: só `.prod-visual` fica branco, `.prod-card` fica `var(--black-3)`.
- **`group: true` é CSS inválido** — propriedade Tailwind. Não reintroduzir.
- **`overflow-x: hidden` só no `body`** — causa bugs de scroll iOS. Deve estar em `html` e `body`.
- **`--text-dim: #666` falha WCAG AA** em fundos escuros. Valor correto: `#888`.
- **Hero seals em `flex-direction: row`** entre 480–1100px estoura viewport — corrigido com coluna em 1100px/768px e `display: none` em 480px.

---

## 7. Próximos Passos

- [ ] **Domínio customizado** — Configurar domínio próprio no Netlify (ex: `quasarbarber.com.br`). Requer compra do domínio + apontamento DNS. Não envolve código.
- [ ] **Hero com foto real** — `hero-bg.png` existe mas não é usado. Avaliar se querem foto de ambiente/produto como fundo do hero section.
- [ ] **Netlify Forms — verificar painel** — Após primeiro deploy com o form, acessar Netlify → Forms para confirmar detecção e configurar notificações por email.
- [ ] **Links legais** — Política de Privacidade, Termos de Uso, Trocas e Devoluções no footer estão com `href="#"`. Precisam de páginas ou modals com conteúdo real.

---

> **Instrução para o próximo chat:** Este arquivo contém o contexto compactado de duas sessões de trabalho no site Quasar Barber. O site está **finalizado e no ar via Netlify** (`https://quasar-barber.netlify.app/`), com auto-deploy do GitHub (`felpquasar/quasar-barber-site`, branch `main`). Todo o código está em `quasar-barber.html`. Não peça ao usuário para repetir informações aqui. Confirme brevemente que entendeu o contexto e pergunte por onde quer continuar — provavelmente domínio customizado ou hero com foto real.
