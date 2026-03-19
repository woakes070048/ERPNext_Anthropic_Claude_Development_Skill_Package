<p align="center">
  <img src="docs/social-preview.png" alt="28 Deterministic Claude AI Skills for ERPNext/Frappe" width="100%">
</p>

<p align="center">
  <a href="#-installation"><img src="https://img.shields.io/badge/Claude_Code-Ready-27ca40?style=for-the-badge" alt="Claude Code Ready"></a>
  <a href="#-version-compatibility"><img src="https://img.shields.io/badge/ERPNext-v14_|_v15_|_v16-0089FF?style=for-the-badge" alt="ERPNext Versions"></a>
  <a href="https://agentskills.org"><img src="https://img.shields.io/badge/Agent_Skills-Standard-DA7756?style=for-the-badge" alt="Agent Skills Standard"></a>
  <a href="LICENSE.md"><img src="https://img.shields.io/badge/License-LGPL--3.0-lightgrey?style=for-the-badge" alt="LGPL-3.0 License"></a>
</p>

<p align="center">
  <strong>28 deterministic skills</strong> enabling Claude AI to generate flawless ERPNext/Frappe code.<br>
  Built on the <a href="https://agentskills.org">Agent Skills</a> open standard.
</p>

---

## 🎯 Why This Exists

Claude is powerful, but without domain-specific guidance it generates ERPNext code that *looks* correct but **fails in production**.

**The #1 cause of AI-generated ERPNext failures:**

```python
# ❌ WRONG - This fails silently in Server Scripts
from frappe.utils import nowdate
today = nowdate()

# ✅ CORRECT - Server Scripts block all imports
today = frappe.utils.nowdate()
```

This package encodes **28 hard-won lessons** like this into deterministic skills that Claude follows automatically.

---

## 📦 Skill Categories

| Category | Count | What's Covered |
|:---------|:-----:|:---------------|
| **Syntax** | 8 | Client scripts, server scripts, controllers, hooks, whitelisting, Jinja templating, scheduler events, custom apps |
| **Core** | 3 | Database operations, permissions system, REST API patterns |
| **Implementation** | 8 | Step-by-step development workflows for common tasks |
| **Error Handling** | 7 | Production-ready error patterns and debugging |
| **Agents** | 2 | Code interpretation and validation agents |

---

## 🚀 Installation

### Claude Code (Recommended)

```bash
# Clone the repository
git clone https://github.com/OpenAEC-Foundation/ERPNext_Anthropic_Claude_Development_Skill_Package.git

# Copy skills to your Claude Code skills directory
cp -r ERPNext_Anthropic_Claude_Development_Skill_Package/skills/source/* ~/.claude/skills/
```

### Claude.ai Web/Desktop

1. Download skill folders from [`skills/source/`](skills/source/)
2. ZIP each folder individually
3. Upload via **Settings → Capabilities → Skills**

### Claude.ai Projects

1. Create a new project
2. Upload `SKILL.md` files to the **Knowledge** section

---

## 🔄 Version Compatibility

| Feature | v14 | v15 | v16 |
|:--------|:---:|:---:|:---:|
| Type annotations | ❌ | ✅ | ✅ |
| UUID autoname | ❌ | ✅ | ✅ |
| Data masking | ❌ | ❌ | ✅ |
| Scheduler improvements | ❌ | ✅ | ✅ |
| Virtual DocTypes | ❌ | ✅ | ✅ |

---

## 📚 Documentation

| Document | Description |
|:---------|:------------|
| **[INDEX.md](INDEX.md)** | Complete skill catalog with descriptions |
| **[USAGE.md](USAGE.md)** | Platform-specific installation guides |
| **[WAY_OF_WORK.md](WAY_OF_WORK.md)** | 7-phase development methodology |
| **[LESSONS.md](LESSONS.md)** | Technical discoveries and gotchas |

---

## 🤝 Contributing

This package also serves as a **template** for building Claude skill packages in other technology domains.

See [`WAY_OF_WORK.md`](WAY_OF_WORK.md) for the methodology we used to build these skills.

**Found an issue?** [Open an issue](https://github.com/OpenAEC-Foundation/ERPNext_Anthropic_Claude_Development_Skill_Package/issues/new)
**Want to contribute?** PRs welcome!

---

## 📄 License

LGPL-3.0 — See [LICENSE.md](LICENSE.md) for details.

---

<p align="center">
  <sub>Built with ❤️ by <a href="https://github.com/OpenAEC-Foundation">OpenAEC Foundation</a></sub><br>
  <sub>Open standards for AEC technology</sub>
</p>

<p align="center">
  <a href="https://github.com/OpenAEC-Foundation/ERPNext_Anthropic_Claude_Development_Skill_Package/stargazers">⭐ Star this repo if it helps you!</a>
</p>
