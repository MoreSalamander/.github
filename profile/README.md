# MoreSalamander StudioLabs Productions

> *Scientia Ludusque — Knowledge and Play.*

A small studio building software, games, and creative work under one
methodological commitment: **AI does the high-volume synthesis under
human-owned constraints, with verification at every boundary.**

Two imprints. One thesis. A growing body of work that's all the same
instinct applied to different problems.

---

## What this is

MoreSalamander is a personal studio currently operated by one person.
It exists to organize a body of work — software projects, games,
videos, simulations — under a shared methodological frame instead of
shipping each project as a standalone artifact with no connecting
thread.

The studio's two imprints split the work by medium:

- **MoreSalamander StudioLabs** publishes engineering work — software,
  tools, products, games. The methodology is encoded in code.
- **MoreSalamander Productions** publishes creative work — videos,
  performances, comedy. The methodology shapes the production process
  but the deliverable isn't an engineered system.

Both imprints share the same underlying thesis (below), the same
visual language (forthcoming), and the same authoring voice.

---

## Why this exists

The honest version: this studio is being built **while its founder
learns to be the engineer who could build it.** Every project is both
an artifact and a training exercise. The body of work to date is the
public record of that learning, in approximate chronological order.

The pattern across the projects wasn't designed in advance — it
emerged. Each project taught the lesson the next one required. After
several projects had shipped, the underlying instinct became
articulable: human-owned constraints, AI-powered synthesis,
verification at every boundary. The studio is the formalization of
that pattern into a brand.

---

## The thesis

> *A well-fenced LLM inside a deterministic scaffold becomes reliable
> as a system, because the unreliable component is wrapped in reliable
> ones that decide whether to trust each output, when to retry, when
> to skip, when to score, when to commit.*

This is the principle that ties every MoreSalamander project together.
In production-LLM engineering circles the pattern goes by names like
**compound AI systems** (Zaharia et al., Berkeley AI Research, 2024),
**guardrails**, or **constrained generation**. In MoreSalamander's
work it's been earned through specific failures and codified into
explicit doctrine.

The three moves of the methodology, in every project:

1. **Explain (human-owned).** Write the constraints down before any
   AI synthesis happens. Page templates, output schemas, algorithm
   specs, verification criteria. The constraints are the doctrine the
   work is judged against.

2. **Synthesize (AI-powered).** Let the model do the high-volume
   work — drafting prose, extracting structure, generating code,
   writing answers. The model is one component, not the system.

3. **Verify (deterministic).** Wrap the model output in Python (or
   similar) that decides whether to trust each result. Reject what
   can't be grounded against the source. Score what passes. Persist
   only what survives.

Every MoreSalamander project encodes these three moves explicitly,
in some form. The pattern is portable across domains — engineering,
documentation, games, video.

---

## How the methodology was earned

The MoreSalamander thesis isn't an abstract design preference picked
up from a book. It has **two lineages**, both earned through
specific work on specific projects. The combination of the two is
what the Deterministic Scaffold thesis encodes.

### Lineage one — the pipeline-shape discipline

In January 2026, while building **Build It**, the studio's founder
built a small n8n workflow called the **Build It Publisher** to
convert markdown guides into styled HTML and push them to GitHub
Pages. The workflow had six stages:

> *Webhook Trigger → Parse Markdown → Convert to HTML → Build Full
> HTML → Push to GitHub → Respond Success.*

Each stage had a single responsibility, an explicit name, and a
visible data connection to the next stage. n8n's visual
node-and-edge model made the architectural pattern unavoidable:
stages must be named, data flow must be explicit, each stage must
do one thing.

That pattern got internalized and then re-encoded — in code, in
project after project:

- **my-AI-stro's ingestion pipeline** — graph_entry → retrieval →
  summarization → validation → memory_write
- **my-AI-stro's advisor pipeline** — retrieval → arc → section ×N →
  recap → assembly → done
- **Prompt Polish Studio** — analyze → questions → polish → compare
- **SprinklerPro 3D auto-placement** — build irrigable polygon →
  build placement grid → filter points → place heads → route pipe
- **The House Always Wins** per-frame AI loop — assess → detect
  patterns → identify opportunities → decide → execute → log

The same shape every time. The Build It Publisher is the first
artifact in the studio's body of work that demonstrates pipeline
thinking. Everything afterward inherits its DNA. n8n's visual
node-and-edge model later re-emerged in code as **NDJSON event
streams** with per-stage event vocabulary (`step_start` /
`step_complete` / `token` / `done` / `error`) — the same
discipline, rendered as text events instead of visual lines.

This lineage matters because it shows the methodology has a
specific *origin in hands-on practice*, not in retrospective
articulation. The "compound AI systems" framing
(Zaharia et al., Berkeley AI Research, 2024) puts a name to what
was already being built; n8n is where the underlying pattern was
internalized first.

### Lineage two — the verification discipline

**MyMaestro** was the first attempt at a personal AI study tool —
Next.js, Prisma, Anthropic Claude API. It generated quizzes and
study guides from a student's own course notes. It worked
technically. And it **hallucinated.** A study tool that generates
plausible-sounding wrong content is worse than no study tool,
because students who can't already distinguish correct from invented
don't catch the drift.

The fix wasn't a tighter prompt or a different model. The fix was
architectural: **verification has to be a load-bearing layer in
the data pipeline, not a soft warning at the UI.** MyMaestro was
discontinued. The next attempt — my-AI-stro — was built on that
principle from the ground up, with grounding gates at every
persistence boundary, a deterministic judge that subtracts points
for ungrounded items, an audit loop that rotates canonical
entries toward more-grounded versions over time.

### The combination

The pipeline-shape discipline (from the Build It Publisher) tells
you HOW a system is structured: named stages, atomic
responsibilities, explicit data flow. The verification discipline
(from MyMaestro's failure) tells you what every stage must do
BEFORE it persists anything: ground the model output against the
source, reject what fails, score what passes, commit only what
survives.

**Pipeline shape + verification at every boundary = the
Deterministic Scaffold.**

The methodology didn't come from a paper. It came from building the
Build It Publisher in n8n in January 2026 and then watching
MyMaestro hallucinate two months later. Both lineages are traceable
to specific work on specific projects, and both are visible in every
project the studio has shipped since.

---

## Two imprints

### MoreSalamander StudioLabs

Engineering work — anything where the deliverable is a running system,
a codebase, a product. Software is shipped under explicit constraint
documents (Constitution, ARCHITECTURE.md, SPEC.md, etc.) that codify
what the AI is and isn't allowed to do during development.

The active engineering body of work:

- **[my-AI-stro](https://github.com/kroeone29-sys/myAistro)** — a
  local-first, self-improving personal knowledge system. Five-stage
  ingestion pipeline with deterministic validation, audit loop with
  pure-Python judge, curation chain across Ingest → SOT → Chat →
  Notebook → Classroom, mobile-friendly PWA. The Deterministic
  Scaffold thesis made architectural.

- **The House Always Wins** — a casino-heist game in development.
  M1 milestone (combat AI prototype with deterministic replay and a
  real-time debug overlay showing every decision) shipped. M2+
  (guard perception, crew AI, full casino heist) in progress. Game
  AI built so every decision is auditable in real time.

- **SprinklerPro 3D** — a commercial 3D irrigation estimator for
  homeowners and landscapers. Three.js + React Three Fiber + a locked
  auto-placement algorithm spec. Real production infrastructure
  (Stripe, NextAuth, Prisma + PostgreSQL). The methodology applied
  at product scale.

- **[Prompt Polish Studio](#)** — a web app that scores prompts
  across a five-dimension rubric, generates clarifying questions,
  rewrites the prompt incorporating user answers, and compares outputs
  side-by-side. Built as an entry to a vibe-coding-themed hackathon;
  didn't win, but it remains the studio's **first publicly shipped
  project** and a meaningful proof that a working multi-step AI agent
  pipeline could ship under deadline pressure. The methodology
  applied to prompt engineering itself.

- **[Build It](#)** — an educational programming guide series. Each
  project is broken into atomic steps under an explicit instructional
  Constitution (v2.0). AI-co-authored guides with named role
  boundaries between human producer and AI synthesizers.

Retired:

- **MyMaestro** — *discontinued. Hallucinated content into a study
  tool, which violates the premise. The lesson became the foundation
  of my-AI-stro.*

### MoreSalamander Productions

Creative work — videos, performances, comedy. Production happens under
detailed shooting and tone specs (the same explicit-constraint pattern
as the engineering work, applied to creative output instead of code).

The active creative body of work:

- **The Journal of Informal Human Protocols (2026)** —
  a David Attenborough-style mockumentary series treating petty human
  rituals ("Not It," "Shotgun," "Dibs," "Tap Tap Spot Back," "Finders
  Keepers," "I Called It") with academic reverence. Imprint: University
  of Nowhere Press. Produced under detailed shot, narration, and music
  specifications passed to AI video generation tools.

---

## The body of work, chronologically

Most studios present their work as a curated grid. MoreSalamander's
work also reads as a trajectory — each project taught the lesson the
next one required. Reading the list in chronological order reveals
the methodology being acquired in real time.

1. **Coral Reef Aquarium** *(month ~3 of programming)* — ecosystem
   simulation in pygame. First experience with AI as line-by-line
   collaborator on substantial code. Multi-trophic-level ecology with
   closed-loop water chemistry, predator target deconfliction.
   Sketchbook-shaped, no methodology document yet.

2. **Build It** *(month ~4)* — first project with explicit methodology.
   Constitution v2.0. Atomic step rules. The moment "I need a system
   for thinking about my systems" became conscious. Also produced the
   **Build It Publisher** — a small n8n workflow that converted
   markdown guides into styled HTML and pushed them to GitHub Pages.
   The pipeline pattern that workflow encoded (named stages, explicit
   data flow, atomic per-stage responsibility) became the architectural
   backbone of every project the studio has shipped since. *See
   "How the methodology was earned" above for the full lineage.*

3. **The Journal of Informal Human Protocols** *(month ~5)* — the
   methodology generalizes to non-code work. Same constraint-driven
   production pattern, applied to video.

4. **Prompt Polish Studio** *(month ~6)* — **first publicly shipped
   project.** Built as an entry to a vibe-coding-themed hackathon;
   didn't win the hackathon, but learned the discipline of shipping
   a working AI agent pipeline under a deadline. Express backend,
   React frontend, real deployment. The losing entry that taught
   how to ship.

5. **SprinklerPro 3D** *(month ~7)* — commercial intent. Locked
   algorithm spec for the auto-placement engine. Real production
   infrastructure (auth, payments, database).

6. **MyMaestro** *(month ~7)* — first attempt at a personal AI study
   tool. **Hallucinated. Discontinued.** The failure became the
   foundation of the next project.

7. **my-AI-stro** *(month ~8 onward)* — rebuilt from the lesson.
   Local-first, pipeline-shaped, verification-driven. The
   Deterministic Scaffold thesis made architectural.

8. **The House Always Wins** *(ongoing)* — game AI with auditable
   reasoning. The thesis applied to game development.

The trajectory itself is the strongest signal in the body of work.

---

## What MoreSalamander is *not*

To make the brand's shape clearer:

- **Not a services consultancy.** No client work. No contracts. No
  freelance offerings. The studio publishes its own projects under
  its own banner.

- **Not a venture-backed startup.** No external funding, no
  investors, no growth targets. Projects ship at their own pace,
  evaluated by their own quality.

- **Not a content farm.** The work isn't optimized for views or
  reach. Each project ships when it meets its own quality bar,
  whether or not anyone reads it.

- **Not pretending to be larger than it is.** The studio is currently
  one person. The brand structure (two imprints, multiple projects)
  reflects how the work is organized, not how many people are working
  on it.

- **Not done.** This is the founding-era body of work. The
  methodology and the brand will both evolve.

---

## What this trajectory is pointing at

The studio is being built in service of a specific career direction —
not a hobby, not a vanity project, not a portfolio for portfolio's
sake. The work is preparing the founder for **simulation engineering
at research-leaning AI labs**, with a long-arc target of working at
**Anthropic, DeepMind, or a peer frontier-research organization**
within roughly a decade.

Both targets are deliberate and informed by what the studio has
already been building, without naming the direction explicitly until
recently. The body of work reveals the intent in retrospect:

- **Simulation engineering is the through-line.** Of the eight
  shipped projects, five are simulations in some sense — the Coral
  Reef Aquarium's multi-trophic ecosystem, Build It's Particle Life
  sub-project, SprinklerPro 3D's coverage simulation, The House
  Always Wins's combat AI prototype, my-AI-stro's audit loop
  simulating how a knowledge system self-improves over time. The
  simulation interest didn't get declared; it got demonstrated,
  project after project. Naming it is just recognition of an
  instinct that was already operating.

- **Auditable AI under human-owned constraints** — the Deterministic
  Scaffold thesis — maps directly to what Anthropic and DeepMind
  value in their research engineering work. Anthropic's published
  thinking on constitutional AI, evaluation harnesses, and structured
  AI reliability lines up structurally with the methodology
  MoreSalamander has been encoding in code. DeepMind's lineage of
  auditable game AI (AlphaGo's value/policy introspection,
  AlphaStar's behavioral traces) maps directly to The House Always
  Wins's debug-overlay-as-audit-layer pattern. The portfolio reads
  as preparation for those orgs whether or not it was conscious
  preparation.

The projects in the body of work *are* the preparation for the work
at those labs. The studio's projects aren't separate from the
founder's career trajectory — they're the public version of it.
Every methodology document, every constraint spec, every grounding
gate is evidence that the founder thinks the way the target labs
hire for.

This is being built on a realistic timeline. Research-engineering
roles at frontier AI labs are not entry-level positions. The honest
path is approximately:

> undergrad → smaller AI-adjacent role (or research-leaning
> internship) → intermediate research-leaning company → frontier
> lab — possibly with a master's somewhere in the middle.

The studio's job in the years between now and then is to keep
producing artifacts that demonstrate the underlying thinking at
every stop along the way. Each step's portfolio should be visibly
stronger than the last's, not because the founder is showing off,
but because the methodology compounds. The artifacts produced under
the methodology *are* the credential.

The founder is currently in **month ~8 of programming**, in the
second year of an **Associate of Applied Science in AI Software
Engineering at Maestro**. The 10-year horizon is realistic if the
intermediate steps are deliberate.

**What success looks like, in order:**

1. **Graduate with a portfolio strong enough that a research-leaning
   first role is achievable** — methodology articulation essays
   published, depth on my-AI-stro and The House Always Wins,
   The Journal pilot produced.
2. **Land a first job at a research-adjacent AI company** —
   smaller AI lab, AI-focused startup, or research engineering role
   somewhere with serious engineering culture and exposure to actual
   research workflow.
3. **Build production seasoning** — real systems running with real
   users, on-call rotations, performance work at scale, mentorship
   from senior engineers, real code review at team scale. The
   skills that don't develop in solo work.
4. **Move toward simulation-focused work specifically** — RL
   environments, agent benchmarks, AI evaluation infrastructure,
   game-AI research, alignment evaluation tooling. The specialty
   gets sharper.
5. **Eventually: a role at a frontier research lab** — Anthropic,
   DeepMind, or a peer organization. Doing the kind of work the
   methodology has been preparing for the whole time.

None of those steps are guarantees. Each step has to be earned by
the work that precedes it. The studio's job is to make the work
that earns each one possible.

---

## Where this is going

The studio's near-term direction:

- **Continued depth on my-AI-stro and The House Always Wins** as the
  flagship pieces of the engineering imprint
- **Production of the Journal of Informal Human Protocols pilot** as
  the founding piece of the creative imprint
- **A landing page at a real domain** to give the studio a public
  home where all the work is collected and contextualized
- **A simple wordmark and visual identity** so the studio reads as a
  coherent thing across projects
- **Cross-linking the existing projects** so each one points at the
  studio and at the others

The studio's medium-term direction:

- **Simulation engineering as the specialty** — five of the existing
  projects are simulations in some sense (ecosystem, irrigation,
  combat AI, particle life, the curation-improvement loop of
  my-AI-stro). Future StudioLabs projects will likely cluster around
  this thread.

- **Auditable AI as the consistent thesis** — every future project
  will continue to encode the human-owned-constraints + AI-synthesis
  + deterministic-verification pattern. Different domains, same
  doctrine.

The studio's long-term direction:

- **A body of work substantial enough that the trajectory itself
  becomes the credential.** Not "look at this single project" but
  "look at the seven-year arc of shipping under one methodology."

---

## On AI collaboration

Every MoreSalamander project is co-authored with AI systems. This is
disclosed explicitly on each project, in the commit history, and as a
matter of brand identity. The collaboration is not hidden, dressed up,
or sometimes-acknowledged; it is *how the studio works.*

Specifically, across the body of work:

- **Anthropic Claude** (via direct chat, then later via Claude Code)
  has been the primary AI collaborator on every engineering project.
- **OpenAI ChatGPT** contributed to the early structuring of Build It
  and to selected MoreSalamander Productions specifications.
- **Local LLMs via Ollama** (Llama 3, Llama 3.1, Llama 3.2, Mistral)
  power my-AI-stro's runtime entirely.

The human role across all projects is the same: design the
constraints, define acceptance criteria, judge outputs, refine the
specifications, decide what ships. The AI role is high-volume
synthesis inside the constraints. **Neither party does the other's
job; both parties are visible in the result.**

This collaboration mode predates Claude Code (the studio's founder
started with Claude in the chat interface, transcribing line-for-line).
The mode persisted as tooling improved. The friction-baked discipline
of those early line-for-line sessions carried forward into how the
modern, lower-friction tooling is used.

---

## On the name

**MoreSalamander** is the parent brand. The compound name balances
two registers: *MoreSalamander* (warm, slightly whimsical, organic)
and *StudioLabs* / *Productions* (formal, credible, professional).
The combination is deliberate — the studio's voice sits at the
intersection of *play* and *rigor*, and the name announces that
before any project does.

**Scientia Ludusque** — *Knowledge and Play* — is the studio's motto.
It captures what the engineering work and the creative work share:
serious thinking about subjects that don't always look serious.
Programming taught through real projects (not toy "hello world"
examples). Mockumentary anthropology of playground rituals.
Combat-AI simulation with reasoning visible at every frame. An
irrigation estimator with the tagline *"Design your irrigation.
See your coverage. Know your cost."* All of it is knowledge approached
as play, or play conducted with the rigor of knowledge.

---

## Found at

The studio's projects currently live in scattered repositories,
mostly on GitHub. A central index is forthcoming. The methodology
documents (Build It's Constitution, my-AI-stro's ARCHITECTURE.md,
SprinklerPro 3D's auto-placement spec, the Journal's production
notes) are the most concrete artifacts of the studio's authoring
voice — read any of them to understand how the work is made.

---

*A studio someone is building while learning to be the engineer who
could build it.*

*Watch this space.*

— **MoreSalamander StudioLabs Productions**
*Scientia Ludusque*
