# Windows ARM64 JDK Downloads

A small download hub for Azul Zulu OpenJDK ZIP archives for Windows on ARM64. It provides a human-friendly website, direct downloads from the [`v1.0.0` GitHub Release](https://github.com/BrunoRNS/homebrew-jdk-holder-windows-arm/releases/tag/v1.0.0), and `wget` commands for automated or headless downloads.

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
wget -c https://github.com/BrunoRNS/homebrew-jdk-holder-windows-arm/releases/download/v1.0.0/zulu21.54.109-ca-jdk21.0.13.0.3-win_aarch64.zip
```

Replace the filename in the URL to select another Java release. `-c` resumes an interrupted download. The files are served directly from the [`v1.0.0` release assets](https://github.com/BrunoRNS/homebrew-jdk-holder-windows-arm/releases/expanded_assets/v1.0.0).

The page's **Download ZIP** buttons use the same direct release links.

## Release and Actions

The ZIP archives are already attached to the `v1.0.0` GitHub Release, so they are not downloaded or uploaded again by Actions and are not stored in Git. The **Deploy download page** workflow checks that all four expected archive assets exist in that release, then publishes the static site to GitHub Pages. The download buttons and `wget` commands link directly to the release assets.

If you publish a new release, update the release tag and download URLs in `site/index.html`, plus the release tag and expected asset names in `.github/workflows/pages.yml`.

## Deploying the website

The **Deploy download page** workflow publishes the static site from `site/` to GitHub Pages whenever that directory changes on `main`, or when manually started.

For the first deployment, open **Settings → Pages** and set the build and deployment source to **GitHub Actions**. The resulting site URL is shown in the Pages workflow run and in the repository's Pages settings.

## License and notices

The JDK archives are Azul Zulu builds and retain their bundled license and notice files. Review the included `DISCLAIMER` and the terms applicable to each archive before use or redistribution. This repository's website and automation do not change the licensing of the downloaded software.
