# gb10-model-configs

Model serve recipes for the **gb10 Model Swapper** (see
[`007applejacks/dgx-spark-model-swapper`](https://github.com/007applejacks/dgx-spark-model-swapper)).

**gb10 is the system of record for this repo.** The swap-ui reads these recipes, and promotes
UI-imported/edited models here by committing + pushing directly from the box (write deploy key).
One `.env` per model — the full vLLM serve recipe + UI metadata.

- `models/*.env` — committed recipes (official). Parsed by both `gb10-serve.sh` (bash) and the
  swap-ui backend (Python); plain `KEY="value"` lines only.
- Uncommitted `.env` files in the working tree are **drafts** (UI-imported, not yet promoted).
- A model's `EXPERIMENTAL="1"` flag clears to `0` only after it passes the swap-ui stability battery.

Lifecycle: import → draft (experimental) → load → stability tests → pass clears experimental →
**Promote** commits + pushes here.
