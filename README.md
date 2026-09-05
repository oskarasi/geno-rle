# geno-rle

Run-length encoding (RLE) for simple alphanumeric strings, written in [Geno](https://github.com/davidiach/geno-lang).

## Encoding scheme

Each run of identical characters becomes `<char><count>`:

| Input | Encoded |
|-------|---------|
| `aaabbc` | `a3b2c1` |
| `abc` | `a1b1c1` |
| `W12` runs of W then B… | `W12B1…` (multi-digit counts allowed) |
| `` (empty) | `` |

- `char` is a single alphanumeric character (`A–Z`, `a–z`, `0–9`).
- `count` is one or more decimal digits and must be ≥ 1.
- Encode does not validate character classes; decode does, and returns `Result[String, String]`.

## API

- `encode(s: String) -> String`
- `decode(s: String) -> Result[String, String]`
- `round_trip(s: String) -> String` — encode then decode

## Run

```bash
geno test .
geno run .
```

## Layout

- `geno.toml` — project manifest
- `Main.geno` — encode/decode and `main` demo
