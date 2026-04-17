# Excalidraw Diagram Skill

A comprehensive skill/command that enables AI coding assistants to generate Excalidraw diagrams as Obsidian-compatible `.md` files. Supports **Claude Code** (skill) and **opencode** (slash command). Covers the complete Excalidraw JSON schema, all element types, styling options, layout patterns, and rendering details -- derived from exhaustive analysis of the Excalidraw source code.

## What It Does

When you ask Claude Code to create a diagram, flowchart, mind map, or any visual representation, this skill generates a fully valid `.md` file that renders natively in Obsidian's Excalidraw plugin.

**Supported diagram types:** Flowchart, Mind Map, Hierarchy/Org Chart, Timeline, Entity Relationship, Network/Architecture, Relationship Map, Comparison, Matrix/Quadrant, Bar Chart, Line Chart, Radar Chart, Freeform/Brainstorm.

**Trigger phrases:** "create a diagram", "flowchart", "mind map", "visualize", "draw", "sketch", "diagram this", "map this out", "chart this", etc.

## Installation

### Claude Code

**Option 1: One-liner**

```bash
mkdir -p ~/.claude/skills/excalidraw-diagram && curl -o ~/.claude/skills/excalidraw-diagram/SKILL.md \
  https://raw.githubusercontent.com/secemp9/excalidraw_skill/main/claude/skills/excalidraw-diagram/SKILL.md
```

**Option 2: Clone and symlink** (easier updates via `git pull`)

```bash
git clone https://github.com/secemp9/excalidraw_skill.git ~/excalidraw_skill
mkdir -p ~/.claude/skills/excalidraw-diagram
ln -sf ~/excalidraw_skill/claude/skills/excalidraw-diagram/SKILL.md ~/.claude/skills/excalidraw-diagram/SKILL.md
```

**Verify:** Start Claude Code and type `/excalidraw-diagram` or ask it to "create a flowchart".

### opencode

**Option 1: One-liner**

```bash
curl -o ~/.config/opencode/command/excalidraw.md \
  https://raw.githubusercontent.com/secemp9/excalidraw_skill/main/opencode/command/excalidraw.md
```

**Option 2: Clone and symlink** (easier updates via `git pull`)

```bash
git clone https://github.com/secemp9/excalidraw_skill.git ~/excalidraw_skill
ln -sf ~/excalidraw_skill/opencode/command/excalidraw.md ~/.config/opencode/command/excalidraw.md
```

**Verify:** Start opencode and type `/excalidraw create a flowchart`.

## Usage

Just ask your AI assistant to create any kind of diagram:

**Claude Code** -- just describe what you want naturally:
```
> create a flowchart of user authentication flow
> visualize the microservice architecture
> draw an ER diagram for the users database
```

**opencode** -- use the `/excalidraw` slash command:
```
/excalidraw flowchart of user authentication flow
/excalidraw mind map the project requirements
/excalidraw bar chart of quarterly revenue
```

The assistant will:
1. Analyze your content and choose the best diagram type
2. Generate the complete Excalidraw JSON with all elements, arrows, and text
3. Save an Obsidian-compatible `.md` file to your current directory
4. Report what was generated and how to view it

### Viewing in Obsidian

1. Open the generated `.md` file in Obsidian
2. Click the **More Options** menu (three dots)
3. Select **Switch to Excalidraw View**

## What's Covered

The skill file (~2700 lines) is an exhaustive reference covering:

- **All 10+ element types** with every property documented
- **Complete color palette** with 13 color families, 5 shades each
- **All 14 arrowhead types** including ER diagram cardinality notation
- **Arrow bindings** with both legacy and modern formats
- **Text containers** with dimension formulas for rectangle, ellipse, diamond, and arrow
- **9 font families** with metrics, line heights, and fallback chains
- **Frame elements** with ordering rules, opacity stacking, and complete examples
- **Elbow arrows** with A* pathfinding, corner radius, and routing details
- **13 layout pattern recipes** with spacing constants and positioning formulas
- **Dark mode** support with exact color transformation formulas
- **Chart generation** constants for bar, line, and radar charts
- **Obsidian-specific format** details (compressed JSON, bracket encoding, wikilinks)
- **Common style recipes** for dashed borders, borderless fills, self-referencing arrows
- **Quick start example** -- a complete copy-paste-ready diagram
- **Troubleshooting guide** for 7 common rendering issues

## Repo Structure

```
claude/skills/excalidraw-diagram/SKILL.md  # Claude Code skill (mirrors ~/.claude/)
opencode/command/excalidraw.md             # opencode slash command (mirrors ~/.config/opencode/)
SKILL.md                                   # Standalone copy (same as claude/ version)
```

## Requirements

- [Claude Code](https://claude.ai/code) or [opencode](https://github.com/opencode-ai/opencode)
- [Obsidian](https://obsidian.md/) with the [Excalidraw plugin](https://github.com/zsviczian/obsidian-excalidraw-plugin) installed (for viewing diagrams)

## License

MIT
