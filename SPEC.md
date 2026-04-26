# MCP Marketplace — Product Specification

## Concept & Vision
A sleek, developer-focused marketplace for discovering MCP (Model Context Protocol) servers. Think "npm for AI agent tools" — clean, informative, instantly useful. The site should feel like a premium directory that makes finding and integrating MCP servers frictionless.

## Design Language
- **Aesthetic**: Developer tool meets modern SaaS — dark-mode primary, clean lines, monospace accents
- **Colors**:
  - Background: `#0d1117` (deep dark)
  - Card bg: `#161b22`
  - Border: `#30363d`
  - Primary: `#58a6ff` (blue accent)
  - Success: `#3fb950`
  - Text: `#e6edf3`
  - Muted: `#8b949e`
- **Typography**: `Inter` for UI, `JetBrains Mono` for code/technical content
- **Motion**: Subtle fade-in on cards, smooth filter transitions

## Layout & Structure
- Single page: Hero search → Server grid with filters → Footer
- No scroll needed for core discovery flow
- Responsive: 1-3 column card grid based on viewport

## Features & Interactions

### Hero Section
- Product name + tagline
- Large search input (auto-focus on load)
- Category filter pills below search

### Server Cards
- Server name, owner, short description
- Category tags (badge style)
- "How to install" expandable section
- "Copy .mcp.json config" button → clipboard + toast

### Categories
- All, Database, File System, Web, AI/ML, Development, Productivity, etc.

### Search
- Real-time client-side filtering by name/description
- Category pre-filter + text search combo

## Technical Approach
- Single HTML + Vanilla JS (no framework, maximum simplicity)
- Static MCP server data (JSON array embedded in page)
- Source for server data: mcpservers.org public data + curated additions
- Deploy: Vercel static (no server function needed for MVP)

## Price
- $9 one-time (Polar checkout link — catalog product)
- No recurring, no subscription

## Content Source
MCP server registry data from mcpservers.org + manual curated list of popular servers
