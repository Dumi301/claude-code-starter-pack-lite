# Agent Reach: let Claude Code read Reddit, YouTube, GitHub and the web

The tool from the reel: **[Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach)** (MIT). 112,291 stars · last push 2026-11-08, from the GitHub API on 2026-11-16. Not affiliated.

## Why
Claude Code's own web fetch can't reach some sites. On 2026-11-16 a fetch of reddit.com returned `Claude Code is unable to fetch from www.reddit.com`. Agent Reach is a CLI that hands any agent read and search access to GitHub, YouTube (search and subtitles), Reddit, X, Bilibili, V2EX and the web. It returns JSON and is read-only: it never posts or logs in for you.

## Install
```
uv tool install https://github.com/Panniantong/Agent-Reach/releases/latest/download/agent-reach.zip
agent-reach setup
```
Install from the release zip above, **not the PyPI package**. Reddit and X are opt-in: `agent-reach add reddit`.

## Try it
```
agent-reach github search "claude code skills"
agent-reach youtube search "claude code" --limit 3
agent-reach youtube subtitle <video url>
```

---

The full Claude Code starter pack (paid): https://payhip.com/b/r8lqU
