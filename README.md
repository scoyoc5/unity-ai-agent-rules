# Unity AI Agent Rules (Free Mini)

Cursor rules and an `AGENTS.md` that stop the most common AI coding mistakes in Unity C#:

- **Missing or deleted `using` directives** (the #1 cause of CS0246 after an AI edit)
- **Invented APIs** (`GameObject.FindByTag`, `transform.GetChildByName`, `Rigidbody.AddVelocity`…)
- **Unity 6 vs 2022.3 LTS API mixups** (`velocity` → `linearVelocity`, `drag` → `linearDamping`, obsolete `FindObjectOfType`)

Works with **Cursor**, **Claude Code**, and any agent that reads `AGENTS.md`. There's also a paste-in header for ChatGPT and Claude chat.

### Also catches bugs that compile fine
| AI writes | What breaks | Rule says |
|---|---|---|
| `target?.TakeDamage(1)` | MissingReferenceException after `Destroy`. `?.` can't see Unity's "fake null" | Use `target != null` on UnityEngine.Object (full kit) |
| renames `speed` → `moveSpeed` | Every prefab's tuned value quietly resets | Add `[FormerlySerializedAs("speed")]` (full kit) |
| `+=` an event in `Start` with no `-=` | Errors after a scene reload | Subscribe in `OnEnable`, unsubscribe in `OnDisable` (full kit) |

## What's inside
| File | What it does |
|---|---|
| `.cursor/rules/00-unity-core.mdc` | Always on. Reads ProjectVersion.txt and manifest.json first, no invented APIs, writes complete compilable files |
| `.cursor/rules/01-namespaces-usings.mdc` | Keeps usings, plus a type → namespace lookup table and name-clash fixes |
| `.cursor/rules/04-unity-versions-api.mdc` | 2022.3 LTS vs Unity 6 API table |
| `AGENTS.md` | The same guidance for Claude Code, Codex and other agents |
| `PRIMING_HEADER.md` | Paste at the start of a ChatGPT or Claude chat |

## Quick start (60 seconds)
```bash
git clone https://github.com/scoyoc5/unity-ai-agent-rules
cp -r unity-ai-agent-rules/.cursor unity-ai-agent-rules/AGENTS.md /path/to/YourUnityProject/
```
Then ask your agent: *"Add a jump to PlayerController."* It should read `ProjectVersion.txt` first and keep your `using` lines.

## Install
1. Copy `.cursor/` and `AGENTS.md` into your Unity project root, next to `Assets/`.
2. That's it. Cursor picks up the rules automatically. For chat tools, paste `PRIMING_HEADER.md` first.

## Quick reference: Unity 6 vs 2022.3
| Topic | 2022.3 LTS | Unity 6 |
|---|---|---|
| Rigidbody velocity | `rb.velocity` | `rb.linearVelocity` |
| Drag | `rb.drag`, `rb.angularDrag` | `rb.linearDamping`, `rb.angularDamping` |
| Find objects | `FindFirstObjectByType<T>()` | same (`FindObjectOfType` obsolete) |
| Async | Coroutines | Coroutines or `Awaitable` |

## Want the full kit? 🎃 25% off in the itch.io Halloween Sale (Oct 25 – Nov 4)
The **Unity AI Agent Kit** adds lifecycle, serialization, Input System, performance and test rules, a `CLAUDE.md`, a phased feature-planning workflow with templates, 20 task prompts (controllers, save/load, FSM, inventory, pooling, UI…), and a batchmode compile + EditMode test loop.
👉 **[Get it on itch.io](https://johnvanscoyoc.itch.io/unity-ai-agent-kit-rules-prompts-workflow-for-cursor-and-claude-code)** ($12 suggested, $9 minimum)

## Contributing
Seen an AI invent a Unity API? Open an issue with the fake call and the real one, and I'll add it to the list.

## License
MIT. Not affiliated with or endorsed by Unity Technologies, Anysphere (Cursor), or Anthropic.

<sub>Keywords: cursor rules for unity, .cursorrules unity, claude code unity, CLAUDE.md unity, AGENTS.md unity, chatgpt unity c#, unity 6 linearVelocity, CS0246 AI.</sub>
