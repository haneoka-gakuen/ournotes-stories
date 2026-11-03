# Our Notes Stories

Complete story and chat scripts for BanG Dream! Our Notes (JP and Intl).

[![Dataset publication](https://github.com/haneoka-gakuen/ournotes-stories/actions/workflows/release.yml/badge.svg)](https://github.com/haneoka-gakuen/ournotes-stories/actions/workflows/release.yml)

## Data layout

`jp/ja/` and `intl/{ja,en,zh-TW,zh-CN,ko}/` contain one UTF-8 TXT file per story. Each line contains a speaker name followed by the dialogue, in story order:

```text
灯：想一点一点，慢慢地累积下去啊……
```

Names and dialogue use the selected translation. The converter resolves the playable story commands and removes presentation markup. The root `manifest.json` records the Master version for both servers.

## Read a story

```sh
git clone https://github.com/haneoka-gakuen/ournotes-stories.git
cd ournotes-stories
cat intl/zh-CN/afterlive_10109.txt
```

## Snapshots and downloads

`main` contains complete published datasets. Pin a `jp-<master-version>` or `intl-<master-version>` tag for a reproducible snapshot. The version follows the Master generation. The Master content identity is stored separately as `hash`.

[GitHub Releases](https://github.com/haneoka-gakuen/ournotes-stories/releases) provide complete archives and `SHA256SUMS`:

```sh
sha256sum -c SHA256SUMS
# For a split archive, concatenate parts in filename order:
cat jp.tar.gz.part* > jp.tar.gz
tar -xzf jp.tar.gz
```

Validate a local full checkout with `python tools/release.py --tag jp-1.1.0.200 --check-only`. This verifies the complete file digest and local Cubism dependency closure where applicable.

## Automatic updates

[Our Notes Data Pipeline](https://github.com/haneoka-gakuen/ournotes-data-pipeline) checks official Master and MoeNotes version signals every 20 minutes and exports successful Haneoka resource builds. This repository consumes the sealed feed with its own short-lived `GITHUB_TOKEN`; it needs no cross-repository credentials. Data commits occur when the dataset or its version record changes. Every file is verified before the complete snapshot reaches `main`; release tags never request another resource build.

Each export uses one fixed, hash-verified production resource release. JP and Intl publish independently; a failed export preserves the previous complete snapshot.

## Related projects

[Masterdata](https://github.com/haneoka-gakuen/ournotes-masterdata) · [Stories](https://github.com/haneoka-gakuen/ournotes-stories) · [Charts](https://github.com/haneoka-gakuen/ournotes-charts) · [Live2D](https://github.com/haneoka-gakuen/ournotes-live2d) · [Spine](https://github.com/haneoka-gakuen/ournotes-spine) · [Resource catalog](https://github.com/haneoka-gakuen/ournotes-resource-catalog) · [Automation](https://github.com/haneoka-gakuen/ournotes-data-pipeline)

Maintained by [Haneoka](https://haneoka.org). See [NOTICE.md](NOTICE.md) for game-content attribution and [LICENSE](LICENSE) for the helper-code license.
