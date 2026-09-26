# Browser proof artifacts

This directory contains visual evidence for the Case Study Symmetry implementation. The files are labeled by evidence status so reviewers can distinguish current design references, historical acceptance captures, and video evidence.

## Current continuous recording

[`two-browser-live-demo.mp4`](two-browser-live-demo.mp4) is a 75-second continuous recording supplied by the applicant on 27 September 2026. It shows two independent Brave browser windows, each using a 427 × 952 mobile device viewport, against the **local Firebase emulator**. The recording shows image selection/crop controls, a Community article, likes and comments updating to the same count in both windows, and share controls. It is **not** a native Android/iOS recording or a public Hosting demo. It does not establish that the external NewsAPI feed works. The local-only demo uses illustrative content and was not deployed publicly.

The source was a 3024 × 1964 H.264 `.mov` screen recording. The committed MP4 is a 1920 × 1246 H.264 transcode of the same continuous timeline; it was scaled and compressed, not reconstructed from screenshots. SHA-256: `23660859b5c62eb0c4517e9da161545f5a4f8ee857f399c3fe06f1403391da2d`.

## Current visual reference captures

These captures document the Figma-oriented proportional UI pass:

| File | Dimensions | Demonstrates |
| --- | ---: | --- |
| [`figma-home.jpg`](figma-home.jpg) | 1280×720 | Constrained 482px home, dense article rows, and pink publish FAB |
| [`figma-editor-empty.jpg`](figma-editor-empty.jpg) | 1280×720 | Empty editor with outlined title field and raised Attach Image control |
| [`figma-editor-filled.jpg`](figma-editor-filled.jpg) | 1280×720 | Selected image, tall body field, and fixed pink publish footer |

The bytes in these files are JPEGs; the `.jpg` extension is intentional. They are visual reference evidence, not a substitute for automated validation or the current realtime social smoke.

## Historical functional-acceptance captures

The numbered frames were captured during an earlier browser acceptance run. They remain useful for the behavior they show, but they do not prove the current tab layout, crop workflow, realtime social interactions, or a current Hosting release:

| File | Dimensions | Historical behavior |
| --- | ---: | --- |
| [`01-public-feed.jpg`](01-public-feed.jpg) | 1280×720 | Public Community feed is readable without authentication |
| [`02-auth-gate.jpg`](02-auth-gate.jpg) | 1280×720 | Publish action opens the authentication gate |
| [`03-required-image.jpg`](03-required-image.jpg) | 1280×720 | Publish rejects a submission without an image |
| [`04-ready-to-publish.jpg`](04-ready-to-publish.jpg) | 1280×720 | Valid title, body, and image are ready to publish |
| [`05-published-feed.jpg`](05-published-feed.jpg) | 1280×720 | Successful publish returns to Community |
| [`06-published-detail.jpg`](06-published-detail.jpg) | 1280×720 | Article body and thumbnail render in detail |
| [`07-reloaded-feed.jpg`](07-reloaded-feed.jpg) | 1280×720 | The article remains after a reload |
| [`08-bookmark-after-reload.jpg`](08-bookmark-after-reload.jpg) | 1280×720 | The original NewsAPI article remains in Saved Articles after reload |

The duplicate [`public-feed.jpg`](public-feed.jpg) is retained as an earlier named copy of the public-feed capture.

## Historical production captures

These captures are retained as historical snapshots from a previous production validation pass. They remain historical evidence; Hosting is now disabled and there is no current live smoke check:

- [`production-public-detail.jpg`](production-public-detail.jpg) — public Community list/detail smoke.
- [`production-publish-success.jpg`](production-publish-success.jpg) — authenticated publish and thumbnail upload result.
- [`production-browser-persisted.jpg`](production-browser-persisted.jpg) — anonymous reload rendering the persisted article.
- [`production-mobile.jpg`](production-mobile.jpg) — responsive check at a recorded 390×844 DOM viewport.

Firebase Hosting was disabled at the applicant’s request. The earlier public verification is historical evidence only; there is no current live web demo.

Supplemental responsive captures:

- [`persisted-article-desktop.jpg`](persisted-article-desktop.jpg) — 1280×720 article detail.
- [`persisted-article-mobile.jpg`](persisted-article-mobile.jpg) — 390×844 article detail.

## Earlier sampled-frame walkthrough

[`browser-walkthrough-sampled-frames.mp4`](browser-walkthrough-sampled-frames.mp4) is a 16-second, eight-frame visual walkthrough generated from genuine numbered screenshots. Each frame is shown for two seconds at 1280×720. It is explicitly a **sampled-frame walkthrough**, not a continuous screen recording; no UI was generated or composited into the source captures.

## Integrity and MIME verification

All 18 still-image artifacts in this directory report `JPEG image data` from `file` and use the `.jpg` extension. Both video files report as MP4 containers. Verify locally:

```bash
find docs/proof -maxdepth 1 -type f -name '*.jpg' -print0 | xargs -0 file
file docs/proof/browser-walkthrough-sampled-frames.mp4
file docs/proof/two-browser-live-demo.mp4
```

## SHA-256 checksums

```text
2d348482c4cfe4a13ad56324df45b072144c083ea954baacc0435cfd86437a00  01-public-feed.jpg
2d348482c4cfe4a13ad56324df45b072144c083ea954baacc0435cfd86437a00  public-feed.jpg
362a017b09a82d41103fdbe835b1e74ddb21e1406622622d22a77818f50573ab  browser-walkthrough-sampled-frames.mp4
3d86616965d7e9bfd2135ea3b403cf7bcb9e64163ebd4e9b102c38e3a7a6d787  production-mobile.jpg
41e6120e01d9e12b21a5e6c3a40e71eddc5f116d0397adad3c52dc3278bdb4e3  04-ready-to-publish.jpg
47410df25e14fc0c219588b4865d9747c2bea706fe7046ca6dd6125dd53c9b4e3  06-published-detail.jpg
51f607322d13e57b978ca16b15c6c51cc1b299275ad838dd1bc873e2356865fa  03-required-image.jpg
5a74f51c1d6a3e00ff566799dfaf2f97c57f7d4a2df23a9a7c7b23963124f0b8  figma-editor-filled.jpg
626adb52e3555862419cbf6dc86b0fa5cde6251faab41f1b414292ecefc9544f  production-publish-success.jpg
638c1ea31251a988767abe5beae5c4e9129a998a6a2719268f1bdf9bde197741  figma-editor-empty.jpg
7602029bde098a37c51631ec22bac8adba1093b29f8912ac9d0996215a8468f2  07-reloaded-feed.jpg
7e8e12862d300f33f9582393646e9127f98ca42fcd5c4d6394fcf54ceb8ca5ce  persisted-article-desktop.jpg
800a9d79245c9eb0cef7e9b921b11de29e51adecb9678cecbd972434b4ee8cf2  production-browser-persisted.jpg
8dbb43f8f4420b8afed0d6c0e8c07648de6e39b00faf85abcea5ce09302d639c  05-published-feed.jpg
b814990e31169c731d419d8637e4f93059d14398501e247648c32910fa938bd5  08-bookmark-after-reload.jpg
bfb55890157351e2f6243184f18204df76bea11a1791fbda0bd5447c1a845465  persisted-article-mobile.jpg
ca0ae707c7719811fafa4359581d4f28ccfb5d7cfd89918b03cf19a24fad5f40  figma-home.jpg
d35eb1702532426a2b360fd9287197fd0f95b8d5f35816c4c6aad7f8a81140d5  02-auth-gate.jpg
f21bb2c7ac473b1083d746f1899b5b8aea8704068e5e5e605aa41a04ca405564  production-public-detail.jpg
```
