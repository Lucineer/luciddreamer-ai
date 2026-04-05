<p align="center">
  <img src="https://cocapn-logos.casey-digennaro.workers.dev/img/cocapn-logo-v1.png" alt="Cocapn" width="100">
</p>

<h1 align="center">LucidDreamer.ai</h1>

<p align="center">The fleet's infotainment streaming platform.</p>

<p align="center">
  <a href="https://luciddreamer-ai.casey-digennaro.workers.dev">Live</a> ·
  <a href="https://github.com/Lucineer/luciddreamer-ai">GitHub</a> ·
  <a href="#stream">Stream</a> ·
  <a href="#visual-pipeline">Visual Pipeline</a> ·
  <a href="#build-your-own">Build Your Own</a>
</p>

---

**Live:** [luciddreamer-ai.casey-digennaro.workers.dev](https://luciddreamer-ai.casey-digennaro.workers.dev)

An endless content stream. Stories, reviews, tutorials, deep dives — generated continuously from the fleet ecosystem. Listen while driving. Clone what catches your eye.

## The Stream

Inspired by OpenMaiC but adapted for the fleet. The default state is **endless accumulation** — the dream cycle runs every 30 minutes, generating:

- **Stories** — narrative journeys through fleet vessels
- **Reviews** — hands-on vessel tests by Critic, with storyboards
- **Tutorials** — getting started guides for each vessel
- **Deep Dives** — explorations of fleet concepts and architecture
- **Changelogs** — weekly fleet news
- **Video Scripts** — scene-by-scene with camera, lighting, mood

### Content Discovery

The stream algorithm scores content by:

| Signal | Weight | Purpose |
|---|---|---|
| **Votes** (net up-down) | 2x, capped at 50 | Community approval |
| **Hits** (views) | logarithmic | Popular content rises, but not runaway |
| **Recency** | exponential decay (3-day half-life) | Fresh content surfaces |
| **New creator boost** | +15 for first 3 pieces | New voices get discovered |
| **Canon** | +100 | User-declared essential content |
| **Quality** | 0.5x–1x multiplier | Auto-assessed content quality |
| **Trending velocity** | +30 for hot content | Recent spikes get boosted |

### Trending

Velocity-based trending — not just volume, but growth rate. A topic with 2 pieces today and 5 total has higher velocity than 50 pieces with no new activity. Trending tags appear on the landing page and stream.

### Clone-to-Deploy

Heard a review that caught your interest? Every vessel has a GitHub link and a one-command deploy. The stream is the discovery engine — the fleet is the product.

## Characters

Five built-in voices narrate the fleet:

| Character | Role | Purpose |
|---|---|---|
| 🔮 **Navigator** | Narrator | Patterns across domains, deep dives |
| 🔧 **Builder** | Explainer | Code demos, tutorials, hands-on |
| 📣 **Herald** | Announcer | Fleet news, changelogs, excitement |
| 🔍 **Skeptic** | Critic | Challenges assumptions, stress tests |
| 🎬 **Critic** | Reviewer | Hands-on vessel reviews, scores, verdicts |

Create your own characters with custom personalities, ElevenLabs voice IDs, sprites, and relationships.

## Visual Pipeline

Every piece of content can have a **storyboard** — 4-8 slides ready for visual production.

### Slide Types
- **landscape** — wide establishing shots
- **interior** — workspace, room scenes
- **terminal** — code on screen, command outputs
- **diagram** — architecture, flow charts
- **character** — character close-ups with expressions
- **split** — side-by-side comparisons
- **transition** — title cards, CTAs

### Each slide includes:
- **Scene description** — what to show
- **Narration** — voiceover text (~30 words per slide)
- **Duration** — seconds
- **Mood** — dramatic, warm, techy, mysterious, playful
- **Camera angle** — wide, medium, close, over-shoulder, bird-eye, pan
- **Camera motion** — static, slow-zoom, pan-left, dolly, orbit
- **Lighting** — natural, neon, studio, dramatic, warm-glow
- **Sprite positions** — character placement with expression/action

### Production Workflow

```
Text content → Storyboard (4-8 slides)
                  │
                  ├── Slides → Generative AI images (sprites, backgrounds)
                  │              ↓
                  │         Slide deck / presentation
                  │
                  ├── Sprites → Game engine (Unity/Godot/Blender)
                  │              ↓
                  │         Sprite-animated video (cheap, fast)
                  │
                  └── First/last frames → Video generation tool
                                     ↓
                                AI video (expensive, highest quality)
```

The same storyboard feeds multiple production paths. Start cheap (slides), graduate to expensive (AI video) when the content proves popular.

### Video Scripts

Video scripts use `[SCENE: description|character:name|mood:techy|camera:medium|lighting:neon]` metadata format. Each scene gets:
- Camera angle and motion for game engine positioning
- Avatar positions for sprite animation
- First/last frame prompts for video generation
- CAD-style motion scripts for CAM tools
- Dialogue timing for voice trigger points

## API

| Endpoint | Method | What |
|---|---|---|
| `/` | GET | Landing page |
| `/stream` | GET | Endless stream (topic filter via `?topic=`) |
| `/trending` | GET | Trending topics with velocity |
| `/reviews` | GET | Vessel reviews |
| `/videos` | GET | Video scripts |
| `/characters` | GET | Character gallery |
| `/studio` | GET | Content creation studio |
| `/content/:id` | GET | Content detail + upvote/downvote |
| `/health` | GET | Health check |
| `/api/stream` | GET | Stream API (paginated) |
| `/api/trending` | GET | Trending topics API |
| `/api/content` | GET | Content list (type filter) |
| `/api/content/:id` | GET | Single content with storyboards |
| `/api/generate/story` | POST | Generate story |
| `/api/generate/review` | POST | Generate vessel review |
| `/api/generate/deepdive` | POST | Generate deep dive |
| `/api/generate/video` | POST | Generate video script |
| `/api/vote` | POST | Upvote/downvote |
| `/api/promote` | POST | Promote to greatest hit / canon |
| `/api/characters` | GET/POST | List/create characters |
| `/api/directions` | GET/POST | List/queue directions |
| `/api/dream` | POST | Trigger dream cycle |
| `/api/speak` | POST | Legacy podcast (SSE) |

## Build Your Own

```bash
git clone https://github.com/Lucineer/luciddreamer-ai.git
cd luciddreamer-ai
echo "your-deepseek-key" | npx wrangler secret put DEEPSEEK_API_KEY
npx wrangler deploy
```

Fill `directions/` with topics to explore. Create characters in `characters/`. The dream engine starts immediately.

### Your Content, Your Canon

Promote content to canon — the engine learns what you value and generates more like it. Vote on what surfaces. Your stream becomes your voice.

## Fleet

[The Fleet](https://github.com/Lucineer/the-fleet) · [Capitaine](https://github.com/Lucineer/capitaine) · [Equipment](https://github.com/Lucineer/cocapn-equipment) · [Playground](https://the-fleet.casey-digennaro.workers.dev)

---

**Superinstance & Lucineer (DiGennaro et al.)** · MIT License
