---
license: cc-by-4.0
task_categories:
- summarization
- text-classification
- feature-extraction
- token-classification
tags:
- cybersecurity
- threat-intelligence
- news
- summarization
- security
pretty_name: Threat incident clusters
size_categories:
- 10K<n<100K
---

# Threat incident clusters

Security incidents as deduplicated stories rather than individual articles. Each row is one incident that at least two outlets reported, with a generated title and prose summary, the entities involved, the reporting outlets, scores and the reporting window.

Built from the [ThreatCluster](https://threatcluster.io) corpus. **19,205 rows**, snapshot generated 2026-09-06.

## Fields

| Field | Description |
|---|---|
| `cluster_id` | Short identifier; the page is https://threatcluster.io/cluster/<cluster_id> |
| `url` | Canonical page for the incident |
| `title` | Generated headline for the incident |
| `summary` | Generated prose summary of the incident |
| `entities` | Named entities extracted from the reporting, grouped by type: threat actors, ransomware groups, malware, CVEs, vendors, products, countries, sectors and MITRE ATT&CK techniques. Raw indicators (IPs, hashes, domains) are not included |
| `sources` | Distinct outlets that reported this incident |
| `source_count` | Number of distinct outlets |
| `article_count` | Number of distinct articles clustered into this incident |
| `threat_score` | Composite 0-100 score used for ranking |
| `severity_score` | Severity component |
| `credibility_score` | Source-credibility component |
| `urgency_level` | Categorical urgency |
| `keywords` | Extracted keywords |
| `first_reported` | Earliest article date in the cluster |
| `last_reported` | Latest article date in the cluster |

## Important caveats

Titles and summaries are MODEL-GENERATED from the underlying articles and are not human-verified; they may contain errors. Source article text is not included (third-party copyright) — only ThreatCluster's own summaries and metadata. Scores are ThreatCluster's editorial ranking, not a standard severity scale.

Clusters scoring below 10 are excluded: at that level the corpus is conference announcements, vendor awards and hiring posts rather than incidents. This is a noise filter, not an importance filter — plenty of significant incidents score in the 20s, so do not read `threat_score` as severity.

## Provenance and refresh

ThreatCluster continuously ingests security reporting and collects ransomware
leak sites first-hand. This dataset is a periodic snapshot; the live data is
available through the [API](https://threatcluster.io/api), which has a free tier, and through the
public feeds at [https://threatcluster.io/feeds](https://threatcluster.io/feeds).

## Licence and citation

Released under CC-BY-4.0. Attribution is required:

```bibtex
@misc{threatcluster_threat_incident_clusters},
  title  = {Threat incident clusters},
  author = {ThreatCluster},
  year   = {2026},
  url    = {https://huggingface.co/datasets/threatcluster/threat-incident-clusters}
}
```

## Ethical use

This data is published to support defensive security research, measurement and
education. It names organisations that criminal groups have claimed as victims;
they are the injured parties. Do not use it to target, harass or profile them.
