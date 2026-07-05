# The Coordination Layer

### A shared memory for communities building the next economy

*Concept document for discussion — v0.2, July 2026*

---

## Why this exists

Across the world, thousands of communities are working on the same problem from different directions. Homesteading and self-sufficiency networks are rebuilding local resilience. Communities like r/antiwork are rejecting extractive hierarchies of labor. The ValueFlows project is formalizing the ontology of post-capitalist economic activity. Platform cooperativists are building democratically owned alternatives to venture-backed platforms.

These groups share a diagnosis — economies spiraling into tragedy-of-the-commons dynamics — and, broadly, a direction of travel. What they do not share is any way of finding each other. Each community lives inside its own silo: an Instagram page, a subreddit, a Discord server, a phpBB forum from 2009. The homesteader who needs a governance model for a seed-share co-op has no way to discover that another community solved that problem formally. The toolbuilder who needs real communities to pilot with has no way to find the twenty groups who would say yes tomorrow. The r/antiwork member who is ready to build, not just vent, has nowhere to be pointed.

This is not a content problem or a platform problem. It is a coordination problem. The movement's knowledge exists but is fragmented; its people exist but are invisible to one another; its shared purpose exists but has no connective tissue.

This document proposes that connective tissue: not another platform to migrate to, but a coordination layer that overlays the platforms these communities already use.

## What it is

The coordination layer is a shared, inspectable memory — a knowledge graph of people, projects, topics, and discussions — with an AI interface in front of it, reachable through a simple link that any community can post in its existing space: a pinned Discord message, a subreddit sidebar, an Instagram bio, a forum footer. Nobody has to leave anything. Nobody has to migrate.

When someone clicks the link, they enter a conversation. The AI learns what they are working on, what they are looking for, and what they can offer — and it gives back value in that same first conversation: pointing them to people working on the same thing, discussions they should know about, groups circling the same questions. Over time, through thousands of these conversations and the links people share, the graph becomes a living map of the movement: who is doing what, where the overlapping efforts are, which debates keep recurring, and which connections have not yet been made.

The layer then acts on that map. It suggests introductions between people working on the same problem in different communities. It convenes: when analysis of the graph shows that eleven people across four communities are all circling community land trusts, it can propose a call and help organize it. It answers questions from the accumulated knowledge of the whole network, with citations back to the original discussions, so that no group has to rediscover what another has already learned.

In short: a shared memory and an active network-weaver, in service of communities that remain sovereign in their own spaces.

## The architecture of trust

One design decision underlies everything else in this document, so it comes first.

**The AI has no memory of its own. The graph is the memory.**

The AI is a stateless reader and writer of a knowledge graph, operating under a published system prompt. Everything it knows, it reads from the graph; everything it learns, it writes to the graph as explicit, sourced entries. There is no hidden model state accumulating in the background. This makes the layer's core promises structural rather than aspirational:

- **Inspectable.** What the layer knows about you is a query, not a mystery. Every person can see their own nodes and edges in full.
- **Deletable.** Deleting your data means deleting nodes and edges — a well-understood operation that actually completes, not a request lodged against an opaque model.
- **Auditable.** Every fact in the graph exists because a specific conversation, contributed link, or confirmed suggestion put it there. Provenance is native to the structure, not bolted on.
- **Governable.** The system prompt and the graph schema are published documents. Trusting the layer does not mean trusting a model's disposition; it means trusting a schema and a set of instructions that the membership can read, contest, and change.

Alongside the graph sits a second, humbler component: a similarity index over contributed discussions and profiles. Its job is discovery across vocabularies — recognizing that a "seed-share co-op" and a "community grain library" are circling the same idea even though no one wrote that down. The rule that governs it is strict: **the index may suggest, but only the graph may assert.** A similarity match is never treated as a fact. It becomes a proposal, reviewed by the AI and — in the pilot — by a human steward, and only on confirmation is it written into the graph as an explicit, sourced connection. The graph is the movement's memory; the index is its intuition; and intuition never gets to speak with the authority of memory.

Pattern detection works the same way. The layer does not "watch" anyone. Scheduled analyses — cluster detection for convenings, contribution-balance checks against extraction — run as defined, published queries over the graph, and their outputs go to human stewards or into proposals, never directly into action.

## How it works

**The intake conversation.** The first conversation is the product. The AI introduces itself honestly — what the graph is, what gets recorded, who governs it — and asks what the person is building or seeking. Before asking for anything more, it reciprocates with something concrete from the network. Consent is negotiated conversationally, not buried in a settings page: what may be shared with others, whether the person is open to introductions, whether their name or only their project is visible, and whether they wish to share a rough location (city-level, always volunteered, never inferred) to enable in-person connection.

**Links as donations of context.** Any member can paste a link to a public discussion — a Reddit thread, a blog post, a public forum debate — and it is ingested into the shared corpus. This turns every participant into a sensor for the network. It also solves consent cleanly: material enters the corpus because a human who cared about it chose to contribute it. Private or gated spaces are never scraped; they join the corpus only if a group's admins deliberately connect them.

**The living map, in the movement's own vocabulary.** The graph is deliberately structured on the ValueFlows ontology — agents, resources, processes, intents, commitments — an open vocabulary for describing economic activity beyond the firm and the market. This is not an implementation detail, and it is not an affiliation with any single implementation or stack. It means "who is doing what, seeking what, offering what" is recorded in a form that any alternative economic platform speaking that vocabulary can eventually interoperate with directly. The map of the movement and the movement's own economic substrate converge.

**Knowledge with provenance.** Everything in the graph is a claim with sources. Every synthesized statement links back to the discussions it came from. Claims are never overwritten: when someone corrects the record, the correction is appended and the old claim is marked superseded or disputed, with the history preserved. Crucially, the layer is designed to surface disagreement, not to smooth it over. Where communities genuinely diverge — market-oriented cooperativism versus anti-market mutualism, for instance — its job is to document the divergence faithfully, not to manufacture false consensus. Dissent is a first-class data type.

**Introductions and convenings.** Introductions are double-opt-in and precision-first: the layer proposes a connection to both parties with its reasoning — which, because the reasoning is a path through the graph, can always be shown — and contact happens only when both agree. A mediocre introduction costs more trust than ten good ones earn, so nothing is suggested rather than something weak, and in the pilot phase every proposed introduction is reviewed by a human network-weaver before it is sent. Convenings scale this from one-to-one to many-to-many: cluster analyses identify shared work across communities and propose gatherings, online or in person. Notes from each convening flow back into the corpus, so coordination compounds.

## Data, trust, and power

A shared memory for economically dissident organizing is also, if built carelessly, a surveillance instrument and a map for infiltrators. This section is not an afterthought; for many of the communities this layer serves, it is the first question, and rightly so.

**Minimal collection, user sovereignty.** The graph stores only what a person chooses to tell it. Pseudonymity is a first-class mode, not a degraded one. Every person can see exactly what the graph holds about them, correct it, or delete it entirely — and deletion propagates through everything derived from it, including the similarity index and any synthesized material.

**Public sources only.** The corpus is built from public discussions contributed by humans and from spaces whose stewards explicitly connected them. Nothing is scraped from private channels.

**Defenses against extraction.** A layer that introduces people can be exploited by a bad actor to harvest the network. Introductions are therefore rate-limited; they flow more freely toward people vouched for by existing members; and published, scheduled analyses flag accounts that accumulate contacts without contributing — to human stewards, who decide what to do.

**No single organ.** Each community's slice of the graph is a portable bundle: its event log, its nodes and edges, its configuration. Because the memory is an explicit graph rather than opaque model state, this bundle is straightforward to define — it is at once the export format, the backup format, and, on the roadmap, the federation unit, so that the shared memory can become a replicated, community-held organ rather than a central one. A movement against centralized extraction cannot depend indefinitely on a centralized database, and this design commits to that trajectory from day one rather than retrofitting it later.

**Governed by its members.** The coordination layer itself will be constituted as a platform cooperative, owned and governed by the communities that use it. This is not branding; it is the only coherent ownership structure for the purpose, and the platform cooperativism community is its natural first steward. The layer must be an instance of the world it exists to help build.

## What it is not

It is not a Discord, Reddit, or forum replacement, and it does not ask any community to migrate, merge, or change its culture. Communities keep their own spaces, norms, and dialects; shared *work*, not forced shared *space*, is the basis of connection. It is not a broadcast channel, a growth-hacked social network, or a data business. And it is not an oracle: the layer curates, connects, and convenes, but people decide.

## How decisions get made

A project that asks communities for trust owes them an honest account of who decides what, especially before anyone asks. This section will feel unusually blunt for a cooperative project. That is deliberate: the graveyard of movement infrastructure is full of tools that spent their energy on governance debates and never shipped, and full of platforms whose founders claimed to be "just building" while quietly keeping all the power. We intend to avoid both fates by separating two kinds of decisions and being explicit about who holds each.

### Values are governed together. Implementation is not.

**The constitution belongs to the communities.** What data may be collected and from where; who owns that data and how deletion works; what the layer is forbidden to do; how introductions and consent operate; how the cooperative itself distributes power and money — these are values questions, decided collectively by the member communities. Because the AI is a stateless interface governed by its instructions, the published system prompt and the graph schema sit in this constitutional layer too: the documents that define what the layer may know and do are themselves subject to member governance. The questions at the end of this document are consultations on exactly this layer, and answers given there will bind the build.

**The implementation belongs to the maintainers.** The technology stack, the interface, the order in which features ship — these are decided by a small maintainer team, currently the founding builders, without a vote. Nobody ballots on database engines. This is not a claim that technical choices are apolitical; it is a claim that a working thing governed imperfectly serves the movement better than a perfect constitution governing vapor.

### How input becomes decisions

Anyone may give feedback at any time, and all of it is recorded — including feedback that conflicts. We do not require consensus and will not manufacture it. Where communities genuinely disagree, the disagreement is documented in both sides' own terms, a maintainer makes the call, and the decision is published with its reasoning and with reference to the positions it weighed. Decisions can be appealed at the next consultation cycle; they are not relitigated continuously in between. (Members will notice this is exactly how the graph itself treats disagreement. The project runs on its own principles.)

Consultations are time-boxed. Every open question comes with a closing date, after which a decision is made and building continues. A question with no deadline is not a consultation; it is a permanent argument.

### The expiry date on founder authority

For version 1 and the first pilot, the maintainer team holds full implementation authority — a benevolent dictatorship, stated plainly, with its decisions logged in public. This authority is temporary by design. When three or more communities are active members, feature priorities pass to a member council constituted under the cooperative's rules, while a maintainer team retains technical authority over how prioritized work is built, accountable to that council. The cooperative's founding documents will encode this transition so it does not depend on anyone's goodwill.

### The right that guarantees all the others

No community's safety here depends on winning any argument. Every group's presence in the coordination layer — its conversations, its knowledge, its members' profiles — is a portable bundle that the group can export in full and take elsewhere at any time, and the long-term architecture aims at communities holding their own copies outright. Exit is a first-class right, built into the schema rather than promised in a policy. We hold ourselves to this because it is the only structural guarantee that voice stays honest: a platform you cannot leave will eventually stop listening, whatever its bylaws say.

## The pilot

The first version is deliberately small: the AI endpoint with its published system prompt, the knowledge graph and similarity index, the intake conversation, link ingestion, and a human-approved introduction flow. No forum software, no migration tooling, no federation protocol yet.

The pilot pairs two allied communities where relationships already exist — the platform cooperativism group and a community active around the ValueFlows vocabulary are the natural candidates, since the second doubles as a test of the ontology with people who know it best. Each posts the link in its own space. Success within roughly ninety days looks like: intake conversations that people finish and return to; a corpus seeded by member-contributed links; and, above all, a first set of cross-community introductions and at least one convening that produced something real — a collaboration, a pilot, a document — that neither community could have produced alone.

That last item is the entire thesis in miniature. If the layer can make two communities smarter together than they were apart, it can do so for two hundred.

## Open questions for the communities reading this

How should the cooperative's governance weight individual members versus member communities? What does your community consider off-limits for ingestion, even from public spaces? What would make you trust — or refuse — an introduction suggested from the graph? And what is the connection your community has needed that never happened?

This document is an invitation, not a specification. Tell us where it is wrong. The consultation on these questions closes thirty days after this document reaches your community; after that, decisions will be published with their reasoning, and building continues.
