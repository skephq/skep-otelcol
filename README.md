# Skep Collector packages

Linux packages (`.deb` and `.rpm`, amd64 and arm64) for the Skep Collector,
the OpenTelemetry Collector distribution that reports to
[Skep](https://www.skep.observer). This repository holds releases only: the
packages are built and signed by Skep's release pipeline and attached to the
release for each version.

- Install guide: https://www.skep.observer/docs/getting-started/install/linux/
- Container image: `ghcr.io/skephq/skep-otelcol`
- Helm chart: `oci://ghcr.io/skephq/charts/skep-collector` ([skephq/helm-charts](https://github.com/skephq/helm-charts))

## Verify a download

Each release has a `SHA256SUMS` file signed with cosign (keyless). Check the
signature, then the checksums:

```bash
cosign verify-blob --bundle SHA256SUMS.sigstore.json \
  --certificate-identity-regexp '^https://github.com/skephq/skep/\.github/workflows/release-collector\.yml@refs/tags/collector/v' \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  SHA256SUMS
sha256sum --check --ignore-missing SHA256SUMS
```

## Report a problem

Security issues: security@skep.observer. Everything else:
support@skep.observer.
