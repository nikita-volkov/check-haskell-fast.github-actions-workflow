# Summary

Automation of CI for Haskell libraries maximizing parallelization of execution of various checks and efficiently utilizing caching.

Prioritizes providing results on various checks as fast as possible at the cost of a bit more compute due to some steps being repeated in parallel jobs. For open source projects this should not matter. If you're optimizing your resource utilisation consider using [the alternative sequential workflow](https://github.com/nikita-volkov/check-haskell-optimally.github-actions-workflow) instead.

# Features

## Building and testing on 2 versions of GHC

One version is controlled via the `minimal-ghc` parameter and is `8.10` by default.

The other is the latest released one.

## Execution of doctests

Optional. Controlled by the `skip-doctest` parameter, which is `false` by default.

## Execution of `cabal check`

Optional. Controlled by the `skip-cabal-check` parameter, which is `false` by default.

## Generation of Haddock documentation

Optional. Controlled by the `skip-haddock` parameter, which is `false` by default.

# How to use

In your workflow under the `jobs` section add the following job:

```yaml
check:
  uses: nikita-volkov/check-haskell-fast.github-actions-workflow/.github/workflows/check-haskell-fast.yaml@v1
  with:
    minimal-ghc: "9.0"
    skip-cabal-check: true
```

# Examples

- https://github.com/nikita-volkov/posix-path/blob/f7cf200bdd6f59f9ee14492b7d7878285cb5a8e8/.github/workflows/ci.yaml#L16
