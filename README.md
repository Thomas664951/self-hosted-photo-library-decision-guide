# Self-Hosted Photo Library Decision Guide


> **Decision:** Use this guide to choose whether a photo library owns imported media, indexes an existing tree, or presents albums before comparing search and sharing features; skip it if export and restore are out of scope.
>
> **For:** families, photographers, and privacy-focused users leaving a hosted photo cloud  ·  **Not for:** users seeking a benchmark winner or unwilling to round-trip representative media

This is a non-commercial, source-traceable decision guide. It normalizes upstream declarations; it does not claim that repository reachability proves functionality, security, maintenance, or fitness.

**Start here:** [Download the media ownership ledger](assets/photo-ownership-map.csv) — twelve projects, located upstream evidence, and explicit unknowns.

## Choose by workload


- Mobile-first household cloud replacement: shortlist Immich and Ente, then test export and account recovery.
- Index an existing photography tree: compare PhotoPrism, PiGallery2, PhotoView, Damselfly, HomeGallery, and Photofield.
- Public albums and gallery presentation: compare Lychee and Piwigo.
- Nextcloud already owns the files: Memories is an app inside that stack, not an independent storage service.
- Need ML discovery: distinguish stable search from explicitly alpha tagging or face features.

## Choose who owns the originals

Managed uploads, existing-tree indexes and gallery publishing require different recovery plans. LibrePhotos belongs in the indexed-library tier, not an omitted fifth category.

## Originals and derivatives map


- **Managed cloud replacements** — Immich and Ente center mobile clients, users, backup, and sharing; their database and recovery paths are part of the product.
- **Indexes over existing media** — LibrePhotos, PhotoPrism, PiGallery2, PhotoView, Damselfly, HomeGallery, and Photofield vary in write behavior and ML scope; preserve the original tree independently.
- **Gallery publishing** — Lychee and Piwigo focus on album management and sharing; compare upload ownership, plugins, and public access controls.
- **Existing-platform app** — Memories lives in Nextcloud and inherits its storage, users, upgrades, and backup responsibilities.


## Media ownership ledger

| Project | Role | Ingest and ownership model | Users and sharing | Metadata and extraction |
|---|---|---|---|---|
| Immich | managed cloud replacement | Uploads photos and videos from mobile and web clients | Multi-user support; mobile and web | EXIF/map metadata viewing; mobile and web |
| PhotoPrism | photo catalogue | Unknown in the frozen upstream README | PhotoPrism® is an AI-powered, privacy-first app for browsing, organizing, and sharing photos and videos. It helps tag, search, and rediscover media without gett… | Metadata can be extracted and merged from Exif, XMP, and other sources like Google Photos |
| LibrePhotos | managed photo library | - Scans your existing folders and accepts uploads from the web and mobile apps | - Multiple users, shared albums and public links - Albums generated from events, like "Saturday in Lisbon" | - Semantic search ("dog on a beach") and search by metadata - RAW+JPEG pairs kept as one photo, burst and bracket stacks, and duplicate detection |
| PiGallery2 | filesystem gallery | - 📁 Directory-first: Shows your folder structure as it is. - Read-only: Your photo folder is never modified. | Unknown in the frozen upstream README | Unknown in the frozen upstream README |
| PhotoView | filesystem gallery | Photoview is a simple and user-friendly photo gallery that's made for photographers and aims to provide an easy and fast way to navigate directories, with thous… | - Have support for multiple users and ways to share albums and photos also publicly | - Made for photography. Photoview is built with photographers in mind, and thus supports RAW file formats, and EXIF parsing. |
| Lychee | web gallery | Uploads are managed by the server gallery | Photo sharing through the server gallery | Unknown in the frozen upstream README |
| Ente | encrypted photo platform | Ente is a service that provides a fully open source, end-to-end encrypted platform for you to store your data in the cloud without needing to trust the service … | Our flagship product. 3x data replication. Face detection. Semantic search. Private sharing. Collaborative albums. Family plans. Easy import, easier export. Bac… | Our flagship product. 3x data replication. Face detection. Semantic search. Private sharing. Collaborative albums. Family plans. Easy import, easier export. Bac… |
| Damselfly | filesystem catalogue | Completely automated background indexing of images, so that the collection is automatically and quickly updated | Multi-user support with user accounts, and role-based entitlements (e.g., users with ReadOnly | GeoLocation with map display of photo locations where metadata exists |
| Piwigo | gallery platform | Manage your photo library. Piwigo is open source photo gallery software for the web. Designed for organisations, teams and individuals. | Manage your photo library. Piwigo is open source photo gallery software for the web. Designed for organisations, teams and individuals. | Unknown in the frozen upstream README |
| Memories | Nextcloud photo app | - For automatic uploads, you can use the official Nextcloud mobile apps. | - 🖼️ Albums: Create albums to group photos and videos together. Then share these albums with others. - 🫱🏻‍🫲🏻 External Sharing: Share photos and videos with peop… | - ✏️ Edit Metadata: Edit dates and other metadata on photos quickly and in bulk. |
| HomeGallery | local gallery index | - Support of read only and offline media sources. Once the preview files are generated and their meta data are extracted, the original sources are not touched a… | Unknown in the frozen upstream README | - Meta data export to XMP sidecar files |
| Photofield | high-density gallery | Read-only file system based collections. The original files are not touched. You are encouraged to even mount your photos as read-only to ensure | Unknown in the frozen upstream README | EXIF metadata and [prominent color] are extracted as separate follow-up operations and run at up to ~200 files/sec and ~1000 files/sec on a fast system. |

Values are short excerpts from the frozen upstream README, not feature-test scores. The CSV retains the located evidence for each cell. “Unknown” means the retrieved document did not establish that axis; it is not a claim that the feature is absent.

## Keep the authority path explicit


Keep originals in a separately backed-up filesystem or object store, then let the chosen library build derivatives and indexes. Run a disposable import first, export metadata, delete the instance, and restore it. If mobile upload and an existing photo tree both feed the system, document deduplication and deletion ownership.


## Adoption notes by project

### Immich

- **Choose it for:** Families wanting a Google Photos-like flow.
- **License at the frozen source:** [AGPL-3.0](https://raw.githubusercontent.com/immich-app/immich/9b3d3d861ccf5f52f05a2a53c3a8bfb5b9bb2aee/LICENSE).
- **Adoption test:** Follow supported backup/restore guidance and test mobile upload, external libraries, metadata export, and upgrade cadence.
- **Source:** [immich-app/immich](https://github.com/immich-app/immich).

### PhotoPrism

- **Choose it for:** Photographers prioritizing discovery over mobile backup.
- **License at the frozen source:** [AGPL-3.0 core with separately offered paid features/support](https://raw.githubusercontent.com/photoprism/photoprism/6383b439983d6a9d558876f64a5cdb83477df9df/LICENSE).
- **Adoption test:** Confirm whether import or index mode is authoritative and which features or support belong to paid editions.
- **Source:** [photoprism/photoprism](https://github.com/photoprism/photoprism).

### LibrePhotos

- **Choose it for:** Users wanting a community photo-cloud alternative.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/LibrePhotos/librephotos/6340b20847d78d42aef11efb1f0a5db8b3cc194e/LICENSE).
- **Adoption test:** Resource use, model behavior, mobile ingestion, metadata export, and restore require representative media.
- **Source:** [LibrePhotos/librephotos](https://github.com/LibrePhotos/librephotos).

### PiGallery2

- **Choose it for:** Very light gallery over an organized tree.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/bpatrik/pigallery2/c741ee2ff78e4b4ed11dbb1cbbb2eef50f32309b/LICENSE).
- **Adoption test:** Third-party tools are not maintained by the project; confirm write behavior, cache rebuild, and video/RAW coverage.
- **Source:** [bpatrik/pigallery2](https://github.com/bpatrik/pigallery2).

### PhotoView

- **Choose it for:** Sharing an existing directory tree.
- **License at the frozen source:** [AGPL-3.0](https://raw.githubusercontent.com/photoview/photoview/7cd83fb845d5af0ef98792e8c8094894f489773f/LICENSE.txt).
- **Adoption test:** Back up originals independently and test metadata, symlinks, permissions, and database rebuild with your layout.
- **Source:** [photoview/photoview](https://github.com/photoview/photoview).

### Lychee

- **Choose it for:** Curated albums and public presentation.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/LycheeOrg/Lychee/ef9339bac648a30557fb4e8dfda65af9d3e67268/LICENSE).
- **Adoption test:** Verify upload storage, metadata round-trip, plugin/theme compatibility, and public-share authorization.
- **Source:** [LycheeOrg/Lychee](https://github.com/LycheeOrg/Lychee).

### Ente

- **Choose it for:** Privacy-first users prepared for a larger deployment.
- **License at the frozen source:** [AGPL-3.0 root; check any component-specific license in the selected release](https://raw.githubusercontent.com/ente/ente/b251f2e34d1e268d9dcf8f08b127af94236329ef/LICENSE).
- **Adoption test:** Check the root AGPL grant and any per-component terms at the selected revision. Test recovery keys, export, background upload and the self-hosted server path.
- **Source:** [ente/ente](https://github.com/ente/ente).

### Damselfly

- **Choose it for:** Large local photography collections.
- **License at the frozen source:** [GPL-3.0](https://raw.githubusercontent.com/Webreaper/Damselfly/e110926104cc93d3c87a9617ba7ab4ae70dbb216/LICENSE).
- **Adoption test:** Benchmark initial indexing, metadata write behavior, ML resource use, and restore on a copy of the library.
- **Source:** [Webreaper/Damselfly](https://github.com/Webreaper/Damselfly).

### Piwigo

- **Choose it for:** Long-lived shareable galleries.
- **License at the frozen source:** [GPL-2.0](https://raw.githubusercontent.com/Piwigo/Piwigo/2224114b2de8e11f77ac55e81c69ac1e8e4264d3/LICENSE.txt).
- **Adoption test:** Use maintained PHP versions; test plugin/theme compatibility, permissions, and full file-plus-database restore.
- **Source:** [Piwigo/Piwigo](https://github.com/Piwigo/Piwigo).

### Memories

- **Choose it for:** Existing Nextcloud operators wanting a photo experience.
- **License at the frozen source:** [AGPL-3.0; subpackages may use their own licenses](https://raw.githubusercontent.com/pulsejet/memories/504243ba5eb07cf29770e5802ca91874e960e681/COPYING).
- **Adoption test:** It is not standalone; include Nextcloud, database, preview/video services, app compatibility, and media storage in the upgrade plan.
- **Source:** [pulsejet/memories](https://github.com/pulsejet/memories).

### HomeGallery

- **Choose it for:** Single-user private media browsing near a NAS.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/xemle/home-gallery/7bef4087db8435f79abfd3d6e2ccdcc2a3115ef3/LICENSE).
- **Adoption test:** Upstream describes a spare-time project without warranty and a one-user model; verify support expectations and index recovery.
- **Source:** [xemle/home-gallery](https://github.com/xemle/home-gallery).

### Photofield

- **Choose it for:** Browsing many existing images without importing originals.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/smilyorg/photofield/a0e647a0fa15ee235a29762b5d6678236142f101/LICENSE).
- **Adoption test:** Tagging and face detection are alpha; keep metadata elsewhere if those annotations must survive.
- **Source:** [smilyorg/photofield](https://github.com/smilyorg/photofield).

## Round-trip representative media

1. Import a copy containing RAW, video, EXIF/IPTC and duplicate files.
2. Compare original hashes and determine whether tags write back to the media tree.
3. Export users, albums and metadata separately from thumbnails.
4. Restore the database/index and verify mobile upload and sharing permissions.

## What this guide covers

Photo originals, derivatives, discovery and sharing, not general file synchronization or vision benchmarks.

## Adjacent guides

- [open-source-document-workflow-index](https://github.com/mckee19/open-source-document-workflow-index) — Use it when scans and PDFs, rather than media libraries, need OCR, records, retrieval, and preservation stages.
- [self-hosted-file-sync-selector](https://github.com/Lindenberg668/self-hosted-file-sync-selector) — Use it when devices need replica or gateway synchronization outside the photo application.
- [encrypted-backup-tool-selector](https://github.com/Anguianodd/encrypted-backup-tool-selector) — Use it when originals, metadata, albums, and databases need an independent encrypted restore plan.

## Located sources and update policy

[`sources.json`](sources.json) binds each cited declaration to a commit, document, exact line range and local snapshot hash. [`assets/projects.json`](assets/projects.json) holds the normalized roles and decision axes. Current HEAD reachability is recorded separately; it is not a maintenance or security assessment. Licensing is version- and directory-specific. Re-read the selected release before adoption.

Run the local evidence and package checks, then opt into public-source reachability:

```bash
python3 scripts/verify_sources.py
python3 scripts/verify_sources.py --online
```

These checks validate source binding, excerpts, hashes, language, the decision asset and nonempty public content. They do not certify feature behavior, migration success or restore success. No popularity score, paid placement or affiliate ranking is used. Restricted-license and historical examples are explicit contrasts, not silently recommended open-source defaults.

If this saved you a decision, star the repo — it is how the next reader finds it.
