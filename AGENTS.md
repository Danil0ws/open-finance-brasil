# Agent Integration Guide

This document provides platform-specific integration instructions for the Open Finance Brasil skill.

## Platform Compatibility

This skill follows the [AgenticSkills.io](https://agenticskills.io) specification and works across all major AI agent platforms.

## Installation Paths by Platform

### Claude Code (Anthropic)

**Path:** `~/.claude/skills/open-finance-brasil/SKILL.md`

**Installation:**
```bash
mkdir -p ~/.claude/skills/open-finance-brasil
cp -r . ~/.claude/skills/open-finance-brasil/
```

**Verification:**
```bash
ls ~/.claude/skills/open-finance-brasil/SKILL.md
```

### OpenAI Codex

**Path:** `~/.codex/skills/open-finance-brasil/SKILL.md`

**Installation:**
```bash
mkdir -p ~/.codex/skills/open-finance-brasil
cp -r . ~/.codex/skills/open-finance-brasil/
```

**Verification:**
```bash
ls ~/.codex/skills/open-finance-brasil/SKILL.md
```

### Cursor

**Path:** `.cursor/skills/open-finance-brasil/SKILL.md` (project-level)

**Installation:**
```bash
mkdir -p .cursor/skills/open-finance-brasil
cp -r . .cursor/skills/open-finance-brasil/
```

**Verification:**
```bash
ls .cursor/skills/open-finance-brasil/SKILL.md
```

### Gemini CLI (Google)

**Path:** `~/.gemini/skills/open-finance-brasil/SKILL.md`

**Installation:**
```bash
mkdir -p ~/.gemini/skills/open-finance-brasil
cp -r . ~/.gemini/skills/open-finance-brasil/
```

**Verification:**
```bash
ls ~/.gemini/skills/open-finance-brasil/SKILL.md
```

### GitHub Copilot

**Path:** `.github/skills/open-finance-brasil/SKILL.md` (repository-level)

**Installation:**
```bash
mkdir -p .github/skills/open-finance-brasil
cp -r . .github/skills/open-finance-brasil/
```

**Verification:**
```bash
ls .github/skills/open-finance-brasil/SKILL.md
```

### Windsurf

**Path:** `.windsurf/skills/open-finance-brasil/SKILL.md` (project-level)

**Installation:**
```bash
mkdir -p .windsurf/skills/open-finance-brasil
cp -r . .windsurf/skills/open-finance-brasil/
```

**Verification:**
```bash
ls .windsurf/skills/open-finance-brasil/SKILL.md
```

### Roo Code

**Path:** `.roo/skills/open-finance-brasil/SKILL.md` (project-level)

**Installation:**
```bash
mkdir -p .roo/skills/open-finance-brasil
cp -r . .roo/skills/open-finance-brasil/
```

**Verification:**
```bash
ls .roo/skills/open-finance-brasil/SKILL.md
```

### Amp

**Path:** `.amp/skills/open-finance-brasil/SKILL.md` (project-level)

**Installation:**
```bash
mkdir -p .amp/skills/open-finance-brasil
cp -r . .amp/skills/open-finance-brasil/
```

**Verification:**
```bash
ls .amp/skills/open-finance-brasil/SKILL.md
```

### Goose

**Path:** `.goose/skills/open-finance-brasil/SKILL.md` (project-level)

**Installation:**
```bash
mkdir -p .goose/skills/open-finance-brasil
cp -r . .goose/skills/open-finance-brasil/
```

**Verification:**
```bash
ls .goose/skills/open-finance-brasil/SKILL.md
```

## Skill Activation

The skill is automatically activated when the agent detects queries related to:

- Open Finance Brasil / Open Banking Brasil
- API endpoints, schemas, Swagger, OpenAPI
- FAPI, DCR, mTLS, consentimento
- Certificação funcional/de segurança
- SLA de APIs financeiras brasileiras
- Instruções Normativas e Resoluções BCB
- Informes do ecossistema

## Skill Behavior

Once activated, the skill will:

1. **Prefer local references**: Check `references/` directory first
2. **Fallback to official sources**: Use GitHub repository when local file is unavailable
3. **Preserve version accuracy**: Never substitute versions without confirmation
4. **Provide source attribution**: Always inform which file or URL was consulted

## Troubleshooting

### Skill not activating

1. Verify SKILL.md exists in the correct path
2. Check that the `name` field in frontmatter is valid (lowercase, hyphens only)
3. Ensure `description` field includes relevant keywords

### Files not found

1. Verify `references/` directory exists alongside SKILL.md
2. Check `references/INDEX.md` for complete inventory
3. Use fallback procedure to GitHub repository

### Outdated information

1. Update local repository using the update scripts
2. Consult official Portal do Desenvolvedor for latest information
3. Verify regulatory documents against BCB official sources

## Additional Resources

- **AgenticSkills Specification**: https://agenticskills.io/specification
- **Skill Directory**: https://agenticskills.io/browse
- **Open Finance Brasil Portal**: https://openfinancebrasil.atlassian.net/wiki/spaces/OF
- **GitHub Repository**: https://github.com/OpenBanking-Brasil/all-services-repo

## Support

For issues with this skill:

1. Check the [references/INDEX.md](references/INDEX.md) for available content
2. Consult the [Portal do Desenvolvedor](https://openfinancebrasil.atlassian.net/wiki/spaces/OF) for official support
3. Review the [GitHub repository](https://github.com/OpenBanking-Brasil/all-services-repo) for latest specifications
