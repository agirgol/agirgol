# Ege Ağırgöl

Software developer in Istanbul. Currently technical co-founder at Saspera, building an ESG
reporting platform; before that, core banking APIs across five countries and production
systems for a defence engine manufacturer.

Environmental engineering degree, which is why the first group below is what it is.

## Carbon accounting, in three layers

These are not three projects. They are one system, split where the seams belong:

```
carbon-accounting-dotnet     the arithmetic
        ↓                    GHG Protocol / ISO 14064-1, source-cited factors,
        ↓                    AR4/5/6 potentials, unit conversion — zero dependencies
        ↓
mcp-carbon-server            the protocol surface
        ↓                    MCP tools, schemas, stdio and Streamable HTTP.
        ↓                    Gives a language model real accounting instead of
        ↓                    a half-remembered emission factor
        ↓
esg-ui-kit                   the visual layer
                             React components typed against the server's contracts,
                             so a tool result renders with no adapter in between
```

The split is deliberate: the accounting has to be usable from an ERP or a batch job, not
only from a chat client.

**[→ Storybook](https://agirgol.github.io/esg-ui-kit)** · **[→ Live demo](https://esg-ui-kit-demo.vercel.app)**

The demo runs the whole chain: type a quantity, and the tools execute over MCP against the
deployed server while the results render through the component kit.

## What they are careful about

A greenhouse gas figure is easy to compute and easy to get subtly, invisibly wrong. Most
of the work in these repositories is refusing to do that:

- A number never travels without its unit — not in the API, not in the types, not on screen
- Biogenic CO₂ is disclosed outside the scopes, so it is never a stack segment
- Scope 2 is reported under both methods, and only one of them belongs in a total
- A capped search result says how many it capped, because 25 of 98 reads exactly like 25
- A factor set that has not been checked against its source is marked unfit to disclose
- A figure whose publisher gave no gas breakdown cannot be re-aggregated under a different
  assessment report — restating it would mean inventing a split nobody published

Every categorical colour in the kit was validated under colour-vision-deficiency simulation
rather than chosen by eye, and the [first palette failed](https://github.com/agirgol/esg-ui-kit/blob/main/docs/color.md).

## Elsewhere in the stack

The carbon repositories are one system. These three are not — separate problems, opened
because the work they correspond to sits behind a bank's firewall and cannot be shown.

**[ledger-core](https://github.com/agirgol/ledger-core)** — a double-entry ledger for the
JVM. Immutable, append-only, and unable to hold an unbalanced set of books. This is the 
invariant underneath it, held against a thousand generated histories per property per build
rather than against the examples I would have chosen. Postgres enforces the append-only part
with a trigger, because a guarantee the database does not hold is a convention, and an ArchUnit test
fails the build if the domain ever acquires a dependency outside the JDK.

**[polyglot-microservices-reference](https://github.com/agirgol/polyglot-microservices-reference)**
— three services, two runtimes, one trace. .NET 10 for the domain service, Spring Boot 4.1
for the Kafka consumer, YARP at the edge, and ten decision records covering the choices
including the rejected ones. One of them records a plan that turned out to be impossible:
MassTransit's transactional outbox does not support Kafka, because Kafka is a rider there
rather than a transport, and the outbox covers transports only. The Java service is not
there to prove Java — a Kafka contract has to be language-neutral to be worth anything.

**[turkish-legal-retrieval](https://github.com/agirgol/turkish-legal-retrieval)** — a
retrieval benchmark on Turkish legislation, with a gold set nobody had to write. Turkish
law is drafted in cross-reference, and every reference is a relevance label somebody
applied years before anyone thought to measure a retriever with it: **5,010 query and
passage pairs over 907 laws**. BM25, dense, hybrid and chunking all measured against it —
and the point of the repository is the measurements that went the other way from the
prediction. Snowball stems *kanun* (law) to *kan* (blood) and splits one lemma across two
stems, so stemming should have hurt. It helps, 12% at R@10. Chunking is worth a great deal
and almost everything specific to Turkish legal structure in the chunker is worth nothing
measurable, which took a paired significance test to establish rather than a table.

## Elsewhere

`C#` · `.NET` · `Java` · `Spring Boot` · `Python` · `TypeScript` · `React` · `Next.js` ·
`PostgreSQL` · `Oracle PL/SQL` · `Kafka` · `Docker` · `Kubernetes` · `Azure`

[LinkedIn](https://linkedin.com/in/egeagirgol) · egeagirgol@gmail.com
