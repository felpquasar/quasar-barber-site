# Contexto Compactado — Site Quasar Barber (Landing Page)

**Data da compactação:** 2026-05-30
**Chat original:** ~12 trocas com múltiplas implementações

---

## 1. Objetivo

Construir e refinar uma landing page profissional para a **Quasar Barber**, distribuidora premium de produtos para barba e cabelo em Codó, MA. Site single-file HTML com CSS e JS embutidos, responsivo para mobile, já no ar via Netlify.

---

## 2. Decisões Tomadas

- **Single HTML file:** Todo CSS e JS inline em `quasar-barber.html` — sem bundler, sem framework, deploy simples.
- **Fontes:** Bebas Neue (títulos display) + Barlow Condensed (UI labels) + Barlow (corpo) — Google Fonts.
- **Paleta:** `--gold: #ffcc00` / `--black: #080808` com 4 variantes de preto. `--text-dim: #888` (corrigido de #666 por falhar WCAG AA).
- **Hero sem foto:** Usuário escolheu remover `hero-bg.png` e usar design CSS puro — gradientes radiais gold + "Q" gigante outline + anéis concêntricos + marcadores de canto.
- **Imagens de produto:** `max-width: 72% / max-height: 78%` com `filter: drop-shadow` — evita que imagens preencham o card inteiro.
- **Cursor customizado desabilitado em touch:** `@media (hover: none)` no CSS + `window.matchMedia('(hover: hover)')` no JS.
- **Nav mobile:** Overlay fullscreen com links Bebas Neue 48px + botão CTA.
- **Breakpoints:** 1100px (tablet), 768px (mobile), 540px (botões hero), 480px (small mobile).
- **Git identity:** `user.name = felpquasar` / `user.email = quasarbarber01@gmail.com` (configurado localmente no repo).
- **GitHub:** `https://github.com/felpquasar/quasar-barber-site` — branch `main`.
- **Deploy:** Netlify com auto-deploy a cada `git push origin main`.

---

## 3. Estado Atual

Site completo e no ar. Todas as seções implementadas:
- Nav fixo com scroll-state + hamburger mobile
- Hero CSS-only (decoração geométrica)
- Marquee de marcas (gold)
- Grid de categorias (6 → 3 → 2 colunas)
- Seção Protocolo Quasar (step dots sincronizados com feat-items)
- Stats bar (dourada, 4 números)
- Produtos em destaque (grid 3-col → 1-col mobile, 5 cards)
- Avaliações (3 cards)
- Grid Instagram (placeholders)
- Footer (4 colunas → 1 coluna mobile)
- WhatsApp float button
- Animações fade-up com IntersectionObserver
- `prefers-reduced-motion` implementado

---

## 4. Arquivos e Artefatos Relevantes

| Arquivo | Status | Descrição |
|---------|--------|-----------|
| `quasar-barber.html` | Criado/Finalizado | Site completo — HTML + CSS + JS em um arquivo |
| `hero-bg.png` | No disco, não usado | Imagem original do hero (substituída por CSS) |
| `prod-kit-barba.png` | Em uso | Card principal "Mais Vendido" — Fox For Men |
| `prod-oleo-qod.webp` | Em uso | Óleo Para Barba QOD 25ml |
| `prod-lemon-gin.webp` | Em uso | Loção Pós Barba Lemon Gin QOD |
| `prod-kit-whisky.webp` | Em uso | Kit Shampoo Whisky + Carteira QOD |
| `.gitignore` | Criado | `.DS_Store`, `Thumbs.db`, `desktop.ini`, `*.log` |

**Caminho local:** `D:\Quasares\quasar-barber-site\`

---

## 5. Informações do Negócio (embutidas no site)

```
Marca:       Quasar Barber
Cidade:      Codó, Maranhão
WhatsApp:    5599992007182  (wa.me/5599992007182)
Instagram:   @quasar_barber (instagram.com/quasar_barber)
Email git:   quasarbarber01@gmail.com
GitHub user: felpquasar
```

**Marcas comercializadas:** Fox For Men, QOD Barber Shop  
**Produtos no site:** Kit Barba Completo (R$89,90), Óleo QOD (R$34,90), Balm Hidratante (R$32,90), Loção Lemon Gin (R$39,90), Kit Whisky+Carteira (R$49,90)

---

## 6. Erros e Armadilhas Conhecidas

- **`group: true` é CSS inválido** — propriedade Tailwind que não funciona em CSS puro. Foi removida. Não reintroduzir.
- **`overflow-x: hidden` só no `body`** — causa bugs de scroll no iOS. Está em `html` e `body`.
- **`--text-dim: #666` falha WCAG AA** em fundos escuros — valor corrigido para `#888`. Não regredir.
- **Step dots sem função real** era UX confuso — agora sincronizam com os feat-items bilateralmente.
- **Hero seals em `flex-direction: row`** entre 480–1100px estourava o viewport — corrigido com coluna em 1100px e 768px, e `display: none` em 480px.

---

## 7. Próximos Passos

- [ ] **Balm card sem imagem** — produto "Balm Hidratante Fox For Men" usa placeholder texto `BALM`. Precisa de foto real.
- [ ] **Grid Instagram com placeholders** — tiles mostram só texto (REELS, BEFORE AFTER, etc.). Substituir por fotos reais ou conectar ao Instagram embed.
- [ ] **Links `javascript:void(0)`** — "Sobre Nós", "Contato" e categorias são placeholders. Criar páginas ou seções correspondentes.
- [ ] **Domínio customizado** — configurar domínio próprio no Netlify (ex: quasarbarber.com.br).
- [ ] **Hero com foto real** — `hero-bg.png` existe mas não é usado. Avaliar se querem voltar com foto de ambiente/produto como fundo.
- [ ] **SEO adicional** — Open Graph tags (`og:image`, `og:title`) para preview ao compartilhar no WhatsApp/Instagram.
- [ ] **Formulário de contato** — seção "Contato" ainda não existe. Pode usar Netlify Forms (gratuito, zero backend).

---

> **Instrução para o próximo chat:** Este arquivo contém o contexto compactado de um chat anterior sobre o site Quasar Barber. O site está **finalizado e no ar via Netlify**, com auto-deploy do GitHub (`felpquasar/quasar-barber-site`, branch `main`). Todo o código está em um único arquivo `quasar-barber.html`. Não peça ao usuário para repetir informações que já estão aqui. Confirme brevemente que entendeu o contexto e pergunte por onde quer continuar — provavelmente um dos itens de "Próximos Passos".
