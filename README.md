# Watchtower WIPO Digest Checksums (append-only)

This repository is a public, append-only checksum anchor for Watchtower WIPO weekly digest demo packets.

## Format

`checksums.tsv` rows:

- `version` (release tag)
- `sha256` (hex, lowercase)
- `filename`

## Verify a demo packet against the anchor

1) Obtain `weekly_digest.zip` and its local `weekly_digest.sha256`
2) Confirm the `weekly_digest.zip` sha256 matches **both**:
   - the local `weekly_digest.sha256`
   - the corresponding `checksums.tsv` row for that `version`

## Optional signature (if present)

If `checksums.tsv.sig`, `allowed_signers`, and `pubkey_ed25519.pub` exist:

```bash
ssh-keygen -Y verify -f allowed_signers -I omniscoder -n watchtower-wipo-digest-checksums -s checksums.tsv.sig < checksums.tsv
```

