# Windows ARM64 JDK Downloads

A small download hub for Azul Zulu OpenJDK ZIP archives for Windows on ARM64. It provides a human-friendly website, direct GitHub Release downloads, and `wget` commands for automated or headless downloads.

## Available archives

| Java release | Archive | Type |
| --- | --- | --- |
| 17 | `zulu17.70.113-ca-jdk17.0.21.0.3-win_aarch64.zip` | LTS |
| 21 | `zulu21.54.109-ca-jdk21.0.13.0.3-win_aarch64.zip` | LTS |
| 25 | `zulu25.38.109-ca-jdk25.0.5.0.3-win_aarch64.zip` | LTS |
| 27 | `zulu27.30.109-ca-jdk27.0.1.0.3-win_aarch64.zip` | Early access |

These are Windows ARM64 (`aarch64`) builds, not x64 or Linux builds.

## Download

### Website

Open the GitHub Pages site for this repository and select **Download ZIP** for the Java release you need. The buttons link directly to the corresponding GitHub Release asset.

### `wget`

Download a specific archive directly from a terminal:

```sh
wget -c https://github.com/BrunoRNS/homebrew-jdk-holder-windows-arm/releases/download/jdk-downloads/zulu21.54.109-ca-jdk21.0.13.0.3-win_aarch64.zip
```

Replace the filename in the URL to select a different release. `-c` resumes an interrupted download. The archives and `SHA256SUMS.txt` are published on the [`jdk-downloads` release](https://github.com/BrunoRNS/homebrew-jdk-holder-windows-arm/releases/tag/jdk-downloads).

To check an archive's SHA-256 on Linux:

```sh
wget -O SHA256SUMS.txt https://github.com/BrunoRNS/homebrew-jdk-holder-windows-arm/releases/download/jdk-downloads/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt --ignore-missing
```

## Publishing the archives

The ZIP files are intentionally not stored in Git: each archive exceeds GitHub's 100 MiB limit for regular Git files. The **Publish Windows ARM64 JDK downloads** workflow downloads the archives from Azul, checks each ZIP's integrity, calculates SHA-256 checksums, and uploads the complete files to a GitHub Release. Release assets support files up to 2 GiB, so the current archives do not need to be split into parts.

To publish or refresh the downloads:

1. Open the repository's **Actions** tab.
2. Select **Publish Windows ARM64 JDK downloads**.
3. Choose **Run workflow**.
4. After the run succeeds, the website's download links will serve the release assets.

The workflow needs the repository's standard `GITHUB_TOKEN` with **Contents: read and write** permission; this is declared in the workflow. The Java versions and exact archive filenames are listed in `.github/workflows/publish-jdks.yml`. Update that list and the matching links in `site/index.html` when changing versions.

## Deploying the website

The **Deploy download page** workflow publishes the static site from `site/` to GitHub Pages whenever that directory changes on `main`, or when manually started.

For the first deployment, open **Settings → Pages** and set the build and deployment source to **GitHub Actions**. The resulting site URL is shown in the Pages workflow run and in the repository's Pages settings.

## License and notices

The JDK archives are Azul Zulu builds and retain their bundled license and notice files. Review the included `DISCLAIMER` and the terms applicable to each archive before use or redistribution. This repository's website and automation do not change the licensing of the downloaded software.
