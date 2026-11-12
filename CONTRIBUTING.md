# Contributing

Ground rules: every claim links a source; public numbers only, with source; mark anything not independently checked **(unverified)**; never invent citations. Prefer DOIs (check with `curl https://api.crossref.org/works/<doi>`) or arXiv abs pages.

Weekly flow: branch `weekly/YYYY-MM-DD` → add update file → file findings into papers/current-work/competitors → update indexes → PR titled `weekly: YYYY-MM-DD`.

## Template: paper
Add to the right `papers/<category>.md` and a row/mention in [papers/README.md](papers/README.md).

```markdown
### <Title>
- **Citation:** <Authors>. *<Title>.* <Venue>, <Year>.
- **Link:** <https://doi.org/...> (verified via Crossref | verified on arXiv | (unverified))
- **Summary:** <2–4 sentences: model, main result, how it was shown.>
- **Implication for referralTree:** <one line: what to build, measure, avoid or say differently.>
```

New category? Create `papers/<slug>.md` with a one-paragraph scope and "Category takeaway", then add it to the index table.

## Template: current work
Add a file under [current-work/](current-work/README.md) and a row in that index. Use this section for hackathon projects, prototypes, and open-source repos — not peer-reviewed papers and not shipped industry products.

```markdown
# <Name>
- **What:** <one line + builders + link>
- **Links:** <repo, showcase, or site, with fetch date>
- **Launch / prize:** <dates, venue, prize if any, with source>
- **Summary:** <2–4 sentences: what it does and the mechanism.>
- **Activity / usage:** <last commit or launch date, stars, whether demos are up, public numbers with source, or "none public">
- **Implication for referralTree:** <one line>
```

## Template: competitor
Add to the right `competitors/<segment>.md` (or `recent-signals.md` if new) and a row in [competitors/README.md](competitors/README.md).

```markdown
### <Name>
- **What:** <one line + link>
- **Mechanism:** <who gets paid, for what, how attribution and payout work>
- **Traction:** <public numbers with source link, or "none public">
- **vs referralTree:** <multilevel? on-chain? verifiable? funding source? what we learn>
```

## Template: weekly update
Create `updates/YYYY-MM-DD.md` and add a line at the top of [updates/README.md](updates/README.md).

```markdown
# Weekly update: YYYY-MM-DD

<One-sentence headline, or "Quiet week.">

## Papers
- **<Authors>, *<Title>*, <id>**: <what it shows>. [link] → [papers/<file>](../papers/<file>.md)

## Competitors / signals
- **<Name>**: <what changed, date>. [source] → [competitors/<file>](../competitors/<file>.md)

## Infrastructure / standards
- ...

## Product
- <referralTree / Exchange changes worth noting>

## No material change
<tracked items checked with nothing new>

## Corrections
<anything earlier entries got wrong>
```
