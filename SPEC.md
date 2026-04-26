# MCP Marketplace — Product Spec

## 1. Concept & Vision

MCP Marketplace — MCP server keşif ve yapılandırma aracı. Tek sayfa, hızlı, deploy edilebilir. Kullanıcılar MCP server'ları keşfeder, filtreler, ve tek tıkla `.mcp.json` yapılandırması kopyalar. $9 one-time.

**Positioning:** mcpmarket.com'un eksik bıraktığı yerde — gerçek registry deneyimi, filtreleme, anlık yapılandırma kopyalama.

## 2. Design Language

- **Aesthetic:** Terminal/dev-tool teması, koyu mod, monospace aksanlar
- **Colors:** bg #0f0f23, card #1a1a2e, accent #00d4ff (cyan), text #e0e0e0
- **Typography:** JetBrains Mono (monospace) + Inter (UI text)
- **Motion:** Minimal — kart hover'da subtle glow, buton click'te pulse

## 3. Layout & Structure

```
┌─────────────────────────────────────────┐
│  Header: "MCP Marketplace" + tagline    │
│  Search bar + kategori filtreleri       │
├─────────────────────────────────────────┤
│  Featured servers (3-6 cards)           │
├─────────────────────────────────────────┤
│  All servers grid (search/filterable)    │
│  ┌────┐ ┌────┐ ┌────┐ ┌────┐           │
│  │card│ │card│ │card│ │card│           │
│  └────┘ └────┘ └────┘ └────┘           │
├─────────────────────────────────────────┤
│  Footer: price $9 + "Get MCP Marketplace"│
└─────────────────────────────────────────┘
```

## 4. Features & Interactions

### Server Card
- İsim, açıklama (2 satır max), kategoriler (badge)
- "Copy .mcp.json" butonu → clipboard'a JSON kopyala + "Copied!" feedback
- Hover: subtle glow border

### Search/Filter
- Text arama: isim + açıklama
- Kategori filter: dropdown multi-select (AI, Dev Tools, Browser, Database, vs.)
- Real-time filtreleme (JS ile, no reload)

### Data Source
- mcpservers.org API'si veya statik JSON fallback
- Local storage ile caching (24 saat)

### Buy Button
- Polar checkout link — $9 one-time
- Checkout açıldığında: teşekkür mesajı + "access key" gösterimi

## 5. Component Inventory

### SearchBar
- Placeholder: "Search MCP servers..."
- Clear button (X) when text present

### CategoryFilter
- Dropdown multi-select
- Kategoriler: AI, Dev Tools, Browser, Database, File System, Security, Misc

### ServerCard
- States: default, hover (glow border), copied (checkmark feedback)
- Data: name, description, categories[], install command, mcpConfig

### BuyButton
- Default: "$9 — Get Access"
- Loading: spinner
- Success: checkout redirect

## 6. Technical Approach

- **Stack:** Single HTML + Vanilla JS (no build step, max portability)
- **Data:** Fetch from mcpservers.org API, fallback to embedded sample data
- **Storage:** localStorage for cache + recently copied configs
- **Checkout:** Polar checkout link (reusable, catalog product)
- **Price source:** $9 (hardcoded, matches Polar product)
- **Deploy:** GitHub + Vercel (standard product flow)

## 7. Product Metadata

- **slug:** mcp-marketplace
- **name:** MCP Marketplace
- **price:** 9
- **description:** Discover, explore, and configure MCP servers. The registry for AI tool integrations.
- **payment_provider:** polar
- **checkout_url:** (Polar checkout link — generated after product creation)
- **vercel_url:** (post-deploy)
- **polar_product_id:** (post-creation)
- **polar_checkout_link_id:** (post-creation)
