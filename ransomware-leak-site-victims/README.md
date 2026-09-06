---
license: cc-by-4.0
task_categories:
- tabular-classification
- time-series-forecasting
tags:
- cybersecurity
- ransomware
- threat-intelligence
- dark-web
- security
pretty_name: Ransomware leak-site victims
size_categories:
- 10K<n<100K
---

# Ransomware leak-site victims

Every victim listing ThreatCluster has collected first-hand from ransomware and extortion leak sites: the group, the named organisation, when it appeared, and the sector and country where known.

Built from the [ThreatCluster](https://threatcluster.io) corpus. **20,627 rows**, snapshot generated 2026-09-06.

## Fields

| Field | Description |
|---|---|
| `group_name` | Ransomware or extortion group that published the listing |
| `victim_name` | Organisation named by the group |
| `country` | ISO-2 country of the victim, where identified |
| `sector` | Industry sector, where identified |
| `discovered` | Date ThreatCluster first observed the listing (UTC) |
| `published` | Date the group published it, where the site exposes one |
| `delisted` | Whether the listing has since been removed |
| `delisted_at` | Date it was observed removed |
| `has_website` | Whether the listing included a victim website (the URL itself is not published) |
| `group_victim_seq` | Ordinal of this listing within that group's history (1 = first) |
| `group_total_victims` | Total listings by that group in this dataset |
| `is_headline_style` | True when the group used this field as a post headline rather than an organisation name. Filter these out for clean org-level analysis (~0.3% of rows); a few name individuals rather than companies. |

## Important caveats

Every row is a CLAIM made by the group, not a confirmed breach. Groups list organisations that never paid, re-list old victims, and occasionally fabricate. Treat listings as evidence of a claim and of group activity, not of compromise.

Around 0.3% of rows carry a post headline instead of an organisation name, and a small number of those name individuals (typically hacktivist posts about public figures). They are flagged with `is_headline_style` — filter on it for organisation-level analysis, and think carefully before republishing those rows.

## Provenance and refresh

ThreatCluster continuously ingests security reporting and collects ransomware
leak sites first-hand. This dataset is a periodic snapshot; the live data is
available through the [API](https://threatcluster.io/api), which has a free tier, and through the
public feeds at [https://threatcluster.io/feeds](https://threatcluster.io/feeds).

## Licence and citation

Released under CC-BY-4.0. Attribution is required:

```bibtex
@misc{threatcluster_ransomware_leak_site_victims},
  title  = {Ransomware leak-site victims},
  author = {ThreatCluster},
  year   = {2026},
  url    = {https://huggingface.co/datasets/threatcluster/ransomware-leak-site-victims}
}
```

## Ethical use

This data is published to support defensive security research, measurement and
education. It names organisations that criminal groups have claimed as victims;
they are the injured parties. Do not use it to target, harass or profile them.
