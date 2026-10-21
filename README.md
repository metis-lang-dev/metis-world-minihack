# metis-world-minihack — a small world for learning, with the small model in the loop

[MiniHack](https://github.com/samvelyan/minihack) (NLE: NetHack's engine, configurable
levels) under the metis agentic loop with the small LLM agent (Gemma E2B, metis-agent) IN
the loop: the agent acts in the level through the domain's intents, its surprises feed the
agentic loop, and the domain is **extracted after** from what the agent did. The approach
under comparison with ALFWorld's: **agent first, domain after**. The program and its
measures: `metis-agentic-loop/docs/LEARNING.md`.

Grounding: NLE gives glyphs, chars, messages and the bottom-line stats; the world's
perception adapter turns the visible map into atoms (cells, the agent's position, objects,
monsters, terrain) and messages into events. Level families are MiniHack's configurable
`.des` levels; held-out combinations of hazards, items and terrain never appear during
discovery.

## Layout (step 1)

| path | what |
|---|---|
| `setup.sh` | the world's venv (`.venv/`, Python 3.12): `nle` 1.3.0, `minihack` 1.0.2, `setuptools<81` (minihack imports `pkg_resources`) |
| `world/mh_host.py` | the host over one MiniHack level: tick / on_event / observe / snapshot / restore; the perception adapter |
| `world/levels.py` | the level families (`.des` variants) and the splits |
| `domains/<level>/` | the packages extracted from the agent's runs |
| `experiments/` | the runs and their records |

## Not here
The agent-in-the-loop wiring (metis-agent), the extraction (the agentic loop's `take`),
the gate policy and the metrics: the metis side.
