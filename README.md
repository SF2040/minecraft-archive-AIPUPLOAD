# Minecraft Auto-Archiver - archive repository

Archive of Minecraft Java Edition worlds captured from public servers by the Auto-Archiver
and organised after the OAIS reference model (ISO 14721 / CCSDS 650.0-M-2).
This is a personal prototype; it follows OAIS as a framework, not as a certification.

## Designated Community
People who study or preserve Minecraft servers and player-built structures (archivists,
researchers, historians) and can open a Java Edition world.

## Virtual Submission Agreement
Accepted: world captures made by WorldTools through the Auto-Archiver (folder or zip named
`<ip>_<port>`), together with Minecraft's log and the archiver's `archival_log.txt`.
Each submission (SIP) is checked at ingest and gets a status in `catalogue.csv`:

| qa_status  | meaning |
|------------|---------|
| complete   | WorldTools reported the save, metadata file present, no storage errors in the log |
| incomplete | stored, but the log shows a failed or unconfirmed save - use with care |
| unverified | files look fine but no Minecraft log evidence was available |
| rejected   | not stored (empty, corrupt, no level.dat / region data, or too large) |

## Layout
    aips/<ip>_<port>_<timestamp>/   one Archival Information Package per capture
        content/                    the world (zip)
        pdi/                        preservation description information (reference, provenance,
                                    context, fixity, access rights, log excerpt)
        aip.json                    packaging information: every file and its SHA-256
    catalogue.csv                   descriptive information: one row per AIP
    reports/                        ingest receipts and storage confirmations
    docs/representation_information.md   how to open the worlds

Times without a time zone come from the archiving PC's local clock.

## Checking integrity
    python upload_aip.py --repo . --verify-only

## Access rights - read before sharing
Worlds were captured from public servers by joining as an ordinary client. The server owners and
players were not asked for permission, rights are unknown, and worlds may contain player data
(UUIDs in `playerdata/` and `stats/`). Keep this repository private until that is reviewed.

STACK
(*) = REQUIRED
- *Language: Python 3.12
- *Automation: PyAutoGUI (mouse/keyboard control)
- *Minecraft Java Edition (1.21.4) Fabric
- Mods:
  - *Meteor Client (structure detection via logs)
	  - https://anticope.pages.dev/addons/?
		    *https://anticope.pages.dev/addons/?addon=etianl%2FTrouser-Streak (Basefinder Module)
	     https://www.meteoraddons.com/ (Meteor Addons)
	  - *[WorldTools](https://www.curseforge.com/minecraft/mc-mods/worldtools) (World downloader)
	  - *[ViaFabricPlus](https://modrinth.com/mod/viafabricplus) (cross-version compatibility, this archiver can download worlds on MOST versions but may lead to corruption)
	  - *[Baritone](https://meteorclient.com/api/downloadBaritone)  
	  - [ImmediatelyFast](https://modrinth.com/mod/immediatelyfast) (Chunk loading performance for faster detections)
	  - Lithium (performance)
	  - *Fabric-api
	  - *Fabric-language-koltin
	  - *Cloth-config
	  - Sodium (performance)
		Sodium Extra (performance)
- [Data Source](https://github.com/kgurchiek): Open port servers (https://api.cornbread2100.com/) 
