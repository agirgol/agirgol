# Ege Ağırgöl

Software developer in Istanbul. Currently technical co-founder at Saspera, building an ESG
reporting platform; before that, core banking APIs across five countries and production
systems for a defence engine manufacturer.

Environmental engineering degree, which is why the repositories below are what they are.

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

## Elsewhere

`C#` · `.NET` · `Java` · `Spring Boot` · `TypeScript` · `React` · `Next.js` ·
`PostgreSQL` · `Oracle PL/SQL` · `Kafka` · `Docker` · `Kubernetes` · `Azure`

[LinkedIn](https://linkedin.com/in/egeagirgol) · egeagirgol@gmail.com
