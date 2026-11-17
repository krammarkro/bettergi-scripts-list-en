The files in this directory are utility scripts used during development for batch processing route files. They are not required for running the main script.

---

## split-routes.js
Splits routes containing multiple Teleport Waypoints (`teleport`) into independent sub-routes for easier tag management.

```bash
node split-routes.js
```

Automatically runs `reindex-positions.js` upon completion.

## merge-routes.js
Re-merges split sub-routes (`name-01.json`, `name-02.json`...) into parent routes, automatically consolidating and deduplicating tags.

```bash
node merge-routes.js
```

Automatically runs `reindex-positions.js` upon completion.

## reindex-positions.js
Re-indexes waypoint `id` fields in sequential numerical order (1, 2, 3...) across all route files and cleans UTF-8 BOM.

```bash
node reindex-positions.js
```

## update-bgi-version.js
Batch updates `info.bgi_version` in route files, supplements missing `info.version` fields, and strips BOM. Edit the `newVersion` constant before running.

```bash
node update-bgi-version.js
```

## rename-tag.js
Replaces targeted tags with a new tag in route files (exact element matching). Modify `oldTag` and `newTag` in the script before running.

```bash
node rename-tag.js
```

## cleanup-fields.js
Batch removes `config` and `farming_info` fields from route files and cleans BOM.

```bash
node cleanup-fields.js
```