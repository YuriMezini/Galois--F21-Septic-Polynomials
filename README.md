# Galois--F21-Septic-Polynomials

# Septic polynomials with Galois group \(F_{21}=C_7 \rtimes C_3\) via Dickson \(D_7\)

This repo implements a one-file SageMath constructor for irreducible septics
with Galois group \(F_{21}\) using a Dickson-Chebyshev approach:
\[
S = u^2 + 7v^2,\quad f(x) = D_7(x,S) - 2u\,S^3,
\]
optionally followed by a flip-scale transform for a compact integral model.

It includes:
- Fast Dickson \(D_n(x,a)\) over \(\mathbb{Z}[x]\)
- A canonical `flip_scale` to tidy models
- A lightweight Frobenius sieve checking mod-\(p\) factorization patterns \([1,3,3]\) and \([7]\)
- Optional exact `galois_group()` certification
- Batch harvesting over a box of \((u,v)\) with export to CSV

## Quick start

### Requirements
- **SageMath ≥ 10.x** (tested)
- No external deps beyond Python stdlib `csv`/`argparse`

### One-shot run
```bash
sage -python src/f21_dickson.py harvest \
  --u-max 3 --v-max 3 \
  --compact --certify \
  --out data/F21_from_Dickson.csv --coeff-order asc
