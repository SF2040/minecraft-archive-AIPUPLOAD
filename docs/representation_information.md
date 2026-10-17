# Representation Information - Minecraft Java Edition world captures

Format: Minecraft Java Edition world folder, stored zipped. Captured with WorldTools (Fabric mod)
on the client. It contains **only what the client was sent** (chunks near where the bot travelled),
not the server's full world.

| Path in the zip | Format |
|---|---|
| `level.dat` | gzip-compressed NBT: world settings and version |
| `region/r.X.Z.mca`, `entities/r.X.Z.mca` | Anvil region files (blocks / entities), one file per 32x32 chunks |
| `playerdata/<uuid>.dat` | gzip-compressed NBT, one per player captured |
| `stats/<uuid>.json` | JSON player statistics |
| `data/` | NBT data files (maps, etc.) |
| `session.lock` | lock file written by Minecraft, no archival value |
| `WorldTools/Capture Metadata.md` | WorldTools' own description of the capture |

How to open: unzip into `.minecraft/saves/` and load with Minecraft Java Edition (the version in
`pdi/provenance.json`, or newer - Minecraft upgrades old worlds). To inspect without playing use an
NBT/Anvil tool such as NBTExplorer or Amulet Map Editor.

Software that produced the capture (exact versions are recorded per AIP in `pdi/provenance.json`):
Minecraft Java, Fabric Loader, WorldTools, Meteor Client (build detection), Baritone (pathing),
ViaFabricPlus (version compatibility).
