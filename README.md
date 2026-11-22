# n624-dev APT repositories

This repository publishes signed APT packages for n624-dev projects. Each project has its own repository path, enrollment file, and signing key.

| Project | Installation guide | APT origin |
| --- | --- | --- |
| LaTeX Renderer | [CLI installation](https://latex-render.n624.jp/docs/client/) | https://apt.n624.jp/latex-renderer/ |

The publishing workflow builds the amd64 and arm64 packages from the latest immutable, attested Stable release. Use **Actions → publish-apt → Run workflow** with the Stable tag after the project's release checks pass. The public APT suite is `stable`.

To verify an immutable release candidate, run the same workflow with its RC tag and select **Verify only**. The workflow tests package installation on both architectures and leaves the public repository untouched.

## Maintenance

The GitHub Pages site serves the complete set of repositories in a single deployment. Add each new project under its own path and include its signed repository in the deployment so previous paths continue to work. Keep package-signing keys separate and give each project a protected signing environment restricted to the main branch. The LaTeX Renderer signing environment is named `latex-renderer-signing`.

Set the environment secret `APT_SIGNING_KEY` to the signing subkey export and the variable `APT_SIGNING_FINGERPRINT` to its primary key fingerprint. Store the primary key and revocation material offline. Publish a renewed enrollment file through a trusted channel before retiring a signing key.
