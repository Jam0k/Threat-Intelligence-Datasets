# Threat Intelligence Datasets

Open datasets built from the [ThreatCluster](https://threatcluster.io) corpus:
ransomware leak-site activity, CVE exploitation signals, and deduplicated
security incidents. 100,711 rows in total, refreshed periodically.

Also on the [Hugging Face Hub](https://huggingface.co/threatcluster) and
[Kaggle](https://www.kaggle.com/datasets/threatcluster/threat-intelligence-datasets).

## Datasets

| Dataset | Contents | Rows | Mirrors |
|---|---|---|---|
| [`ransomware-leak-site-victims`](./ransomware-leak-site-victims) | Ransomware leak-site victims | 20,627 | [Hugging Face](https://huggingface.co/datasets/threatcluster/ransomware-leak-site-victims) · [Kaggle](https://www.kaggle.com/datasets/threatcluster/threat-intelligence-datasets) |
| [`cve-exploitation-signals`](./cve-exploitation-signals) | CVE exploitation signals | 60,879 | [Hugging Face](https://huggingface.co/datasets/threatcluster/cve-exploitation-signals) · [Kaggle](https://www.kaggle.com/datasets/threatcluster/threat-intelligence-datasets) |
| [`threat-incident-clusters`](./threat-incident-clusters) | Threat incident clusters | 19,205 | [Hugging Face](https://huggingface.co/datasets/threatcluster/threat-incident-clusters) · [Kaggle](https://www.kaggle.com/datasets/threatcluster/threat-intelligence-datasets) |

Each directory holds newline-delimited JSON (`data.jsonl`, one object per line)
and a dataset card describing every field and its caveats. Read the card before
using the data — each set has limits that matter.

```python
import json
rows = [json.loads(l) for l in open("cve-exploitation-signals/data.jsonl")]

# or straight from the Hub
from datasets import load_dataset
ds = load_dataset("threatcluster/cve-exploitation-signals")
```

### Ransomware leak-site victims

Victim listings collected first-hand from ransomware and extortion leak sites: which group named which organisation, when, in what sector and country.

`ransomware-leak-site-victims/data.jsonl` — 20,627 rows. Fields and caveats: [`ransomware-leak-site-victims/README.md`](./ransomware-leak-site-victims/README.md).

### CVE exploitation signals

One row per CVE joining reference data (CVSS, CWE, affected products) with exploitation evidence: CISA KEV, public exploit availability and ransomware use.

`cve-exploitation-signals/data.jsonl` — 60,879 rows. Fields and caveats: [`cve-exploitation-signals/README.md`](./cve-exploitation-signals/README.md).

### Threat incident clusters

Security incidents as deduplicated stories rather than individual articles, with the entities involved and the outlets that reported each one.

`threat-incident-clusters/data.jsonl` — 19,205 rows. Fields and caveats: [`threat-incident-clusters/README.md`](./threat-incident-clusters/README.md).

## What is deliberately not here

Victim screenshots and enrichment, leak-site post URLs, the extortion copy
groups write about their victims, and the full text of source articles. The
first three carry personal data or belong behind the paid API; the last is
third-party copyright. Only ThreatCluster's own summaries, scores and metadata
are published, alongside links back to the original reporting.

## Honest limits

- **Leak-site listings are claims, not confirmed breaches.** Groups name
  organisations that never paid, re-list old victims and occasionally fabricate.
- **Exploitation labels are observed, not exhaustive.** `in_kev` and
  `has_exploit` mean "known to us"; absence is not evidence of absence. Both are
  time-dependent, so respect `published_date` when splitting train and test data.
- **Incident titles and summaries are model-generated** and not human-verified.
- **`threat_score` is a ranking signal, not a severity scale.** Significant
  incidents routinely score in the 20s.

## Where else to get these

- **Hugging Face** — https://huggingface.co/threatcluster (loads with `datasets.load_dataset`)
- **Kaggle** — https://www.kaggle.com/datasets/threatcluster/threat-intelligence-datasets (all three as one dataset)
- **This repository** — raw `data.jsonl` per dataset
- **Live, queryable** — the [ThreatCluster API](https://threatcluster.io/api), free tier available

## Licence

Data: [CC BY 4.0](./DATA-LICENSE) — free to use and redistribute, including
commercially, with attribution to ThreatCluster. The GPL-3.0 `LICENSE` file
covers code, not data.

## Ethical use

Published to support defensive security research, measurement and education.
The organisations named here are the injured parties in criminal attacks. Do not
use this data to target, harass or profile them.

## Live data

These are periodic snapshots. The live corpus is available through the
[ThreatCluster API](https://threatcluster.io/api), which has a free tier, and
through the public feeds at [threatcluster.io/feeds](https://threatcluster.io/feeds).
