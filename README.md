# KSG Trading Operating System — File Index

This folder is the live data + framework layer for the KSG Trading Operating System. Claude (via Claude Desktop + filesystem MCP) reads and edits these files directly during chats.

## Layer architecture

| Layer | Artifact | Purpose |
|---|---|---|
| Base | CSV files in this folder + per-campaign and per-cycle markdown | Ground truth — what actually happened |
| Middle | `Trading_OS.md` | How we think and decide — philosophy, three books, setups, rules, grading |
| Top | Chats in this project | Where we apply, observe, decide, and revise |
| Meta | Framework chat | Where the framework itself gets revised |

## The Three Books

The system has three distinct activities running in (potentially) parallel, organized by **investment intent**:

1. **Strategic Allocation Book** — long-term wealth accumulation. HTF range bottom to HTF range top. Direct shares (SPY/QQQ/GLD/IBIT/ETHA) plus megacap options (MSFT/META/NVDA/AMZN as OTM calls)
2. **Trading Book** — active returns. Single-range plays (futures for indices, options for stocks) + catalyst plays (options)
3. **Asymmetric Bet Book** — multi-year LEAPS positions; **deferred until Sprint 3+**

## The Two Trade Categories

Every trade fits one of two categories:

1. **Structural Plays** — driven by price structure
   - Strategic Accumulation (HTF range low → HTF range high) lives in Strategic Allocation Book
   - Trading Book Single-Range (not at HTF range low) lives in Trading Book
2. **Catalyst/Momentum Plays** — consolidation + identifiable event; lives in Trading Book

## The Decision Tree

Every opportunity routes through three questions:

1. Is this a structural play? (Yes → Q2; No → is it catalyst? → Trading Book Catalyst or not a trade)
2. Is it at HTF range low (long) / range high (short)? (Yes → Strategic Accumulation; No → Trading Book Single-Range)
3. What instrument matches? (See Trading_OS.md § 6 for the full table)

See `Trading_OS.md` § 4-6 for the full architecture.

## Progression structure

```
Mission (Trading_OS.md § 1)
  └── Quest 1: First $25k Realized Month  ←  quests/
       ├── Sprint 1: Execution Discipline  ←  sprints/
       └── Sprint 2: Calibration (if needed)
  └── Quest 2: Approach BX Replacement
  └── Quest 3: BX Replaced
  └── Quest 4: 8-Figure Trajectory
```

Quests are outcome-defined (financial milestones). Sprints are time-boxed framework-iteration blocks within Quests.

## Files (active)

| File | Purpose | Edited by |
|---|---|---|
| `Trading_OS.md` | Source-of-truth doc — Snapshot, three books, philosophy, setups, sizing, grading, evolution log | Claude (in chats) |
| `Chats_Framework.md` | Defines chat types, launch prompts, promotion paths | Claude (rarely) |
| `quests/` | One markdown file per Quest — Plan / Tracking / Review / Handoff | Claude (throughout each Quest) |
| `sprints/` | One markdown file per Sprint — Plan / Tracking / Review / Handoff | Claude (throughout each Sprint) |
| `campaigns/` | One markdown file per Trading Book campaign | Claude (throughout each campaign) |
| `strategic_allocations/` | One markdown file per Strategic Allocation cycle | Claude (throughout each cycle) |
| `pre_trade_tickets.csv` | Required pre-entry documentation for Trading Book trades. (Passed/missed ideas → `watchlist.csv` resolution column.) | Claude (during Pre-Trade Tickets chat) |
| `trade_log.csv` | Closed Trading Book trade database with all four grades | Claude (during Post-Trade Journal) |
| `open_positions.csv` | Current live exposure across all books | Claude (continuously through lifecycle) |
| `trade_actions.csv` | Every enter / trim / add / roll / exit / hedge / tranche action | Claude (during Live Position Management) |
| `watchlist.csv` | Forward-looking trade candidates with universe tier + resolution | Claude (during Daily Desk and Weekly Review) |
| `daily_desk.csv` | Daily pre-market routine + EOD reconciliation | Claude (during Daily Desk) |
| `mistake_log.csv` | Rule violations, costs, prevention | Claude (when violations occur) |
| `risk_drawdown.csv` | Daily account equity, peak, drawdown, open risk | Claude (during Daily Desk EOD) |
| `capital_allocation.csv` | Snapshot of capital deployed by book and asset; combined household | Claude (Weekly Review + on material movement) |
| `weekly_review.csv` | Weekly regime, P&L by book, process metrics, lessons | Claude (during Weekly Review) |
| `hypotheses_register.csv` | Open falsifiable claims with falsification criteria | Claude (during Framework chats) |
| `intervention_log.csv` | Every framework/rule/sizing change with hypothesis and observed effect | Claude (whenever framework changes) |
| `deferred/` | Files not useful until later phases | See `deferred/README.md` |

## How to use

- Open any markdown file in any editor or CSVs in any spreadsheet app
- Read the Snapshot at the top of `Trading_OS.md` to know the current state
- Start a new chat per chat type using a launch prompt from `Chats_Framework.md`
- Claude updates files directly during the chat

## Data flow

- **Pre-market** → user starts Daily Desk chat; Claude pulls SPY/QQQ context, macro, news; produces daily plan; appends to `daily_desk.csv`; updates `watchlist.csv`
- **Trade idea (Trading Book)** → user brings opportunity to Pre-Trade Tickets chat; Claude pressure-tests; if Take, appends to `pre_trade_tickets.csv` + creates/links Campaign; if Pass/Wait, adds to `watchlist.csv` with resolution
- **Strategic Allocation opportunity** → user brings dislocation/inflection observation to Long-Term Positioning chat; Claude pressure-tests against § 19 discipline; if trigger valid, creates cycle file in `strategic_allocations/` with Plan section; tranches executed and logged in cycle file + `trade_actions.csv`
- **Live position management** → user reports active position event; Claude works through Live Position Management chat; appends to `trade_actions.csv`; updates `open_positions.csv` and relevant campaign/cycle file
- **Trade close** → user reports closed trade in Post-Trade Journal; Claude appends to `trade_log.csv` with all four grades; updates `mistake_log.csv` if violations; closes campaign file if applicable
- **Cycle exit** → user reports Strategic Allocation exit trigger fired in Long-Term Positioning chat; Claude executes full exit per § 19, fills Review section in cycle file, returns capital to BIL accounting
- **End of day** → user runs EOD in Daily Desk; Claude reconciles open positions, updates `risk_drawdown.csv` and `capital_allocation.csv`, marks daily completion
- **Weekly review** → Sunday; user starts Weekly Review chat; Claude computes weekly metrics, updates Snapshot, appends to `weekly_review.csv`, updates `capital_allocation.csv`, updates Sprint Tracking, plans next week
- **Sprint review** → end of each Sprint; Claude fills Sprint Review, identifies framework v.next changes, opens next Sprint file
- **Quest review** → outcome-triggered or at the 4-week time guard; Claude fills Quest Review, evaluates against success criteria, opens next Quest file if Quest closes
- **Framework evolution** → user starts Framework chat; Claude proposes changes, updates `Trading_OS.md` and CSVs, appends to `intervention_log.csv`, updates Evolution Log
- **Emergency reset** → triggered by guard rail OR user-initiated; user starts Emergency Reset chat; mandatory pause and documented postmortem

## Setup notes

- Claude Desktop + the official MCP filesystem server (`@modelcontextprotocol/server-filesystem`) is what makes in-place editing work
- Path exposed to Claude: `/Users/karan/Documents/_Personal/Projects/Trading`
- Each file write requires one-time approval in Claude Desktop
- Source PDFs (Elite Options FAQs, Golden Rules, etc.) remain in the Claude.ai Project as reference inputs but the OS doc is the governing source

## Capital architecture

**Brokerage:** ~$375k starting. Houses all three books.

**Solo 401k:** ~$117k. **Out of scope for Sprint 1-2.** At Quest 2 close, activated for Strategic Allocation only (no options trading; tax-advantaged long-horizon money is the natural fit).

See `Trading_OS.md` § 26 for the full account architecture.

## Deprecated

- `phases/` — superseded by `quests/` + `sprints/` in v0.3. Can be deleted manually.
- Google Sheet + Google Docs versions — superseded by this local folder in v0.2 migration.
