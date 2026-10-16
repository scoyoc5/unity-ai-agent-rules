# AGENTS.md (Unity, free mini)
- Read ProjectSettings/ProjectVersion.txt and Packages/manifest.json first. Target that version and only installed packages.
- Never invent Unity APIs. Say "unverified" if unsure.
- Keep all needed `using` directives, and never remove one you haven't checked.
- Write complete compilable files. The file name must match the MonoBehaviour class name.
- Unity null checks: `== null`, never `?.` / `??` on UnityEngine.Object.
- Unity 6: `linearVelocity`/`linearDamping`. 2022 LTS: `velocity`/`drag`.
- Before saying "done", confirm the code compiles.

Full kit (8 rules, CLAUDE.md, phased planning workflow, 20 task prompts, batchmode compile/test loop): https://johnvanscoyoc.itch.io/unity-ai-agent-kit-rules-prompts-workflow-for-cursor-and-claude-code
