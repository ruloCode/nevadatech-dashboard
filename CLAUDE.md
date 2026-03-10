# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

NevadaTech Command Center — a CRM dashboard for a sales team (Rulo, David, Camilo) selling tech packages (Básico, Pro, Enterprise) to local businesses in Bogotá (peluquerías, barberías, odontología, etc.).

## Architecture

**Single-file application.** The entire app lives in `index.html` (~643 lines) with no build system, no dependencies, no package manager, and no tests.

Structure within `index.html`:
- **CSS** (lines 10–249): Custom properties in `:root`, all styles inline in a `<style>` block. Dark theme with color tokens (`--blue`, `--green`, `--purple`, etc.). Responsive breakpoints at 1100px, 768px, 480px.
- **HTML** (lines 251–612): Topbar navigation, 5 page sections (`dashboard`, `pipeline`, `prospectos`, `clientes`, `reportes`), and a modal for adding prospects.
- **JavaScript** (lines 614–641): Minimal vanilla JS — page routing via `goPage()`, modal open/close, prospect search filtering, keyboard shortcuts (Cmd+N for new prospect, Escape to close modal).

## Key Patterns

- **Page routing**: Pages are `<section class="page" id="page-{name}">` elements toggled via `.active` class. Navigation links use `data-page` attributes.
- **All data is hardcoded** in the HTML — there is no API, no database, no localStorage.
- **Fonts**: Outfit (UI text) and JetBrains Mono (numeric/monospace values), loaded from Google Fonts.
- **CSS-only charts**: Bar charts and donut charts are built with pure CSS (no charting library).
- **Language**: UI is in Spanish.

## Development

Open `index.html` directly in a browser — no server needed. Use any static file server (e.g., `python3 -m http.server`) if preferred.
