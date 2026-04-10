# Riftbound Summoner Release Feed

This folder is the local staging area for Riftbound Summoner Windows releases.

## Files written here

- `latest.json`
- versioned zip packages like `Riftbound-Summoner-win64-0.1.0.zip`
- `release-config.json`

## Publish flow

1. Export the Windows build into `z:\not-pokemon\Executable`.
2. Make sure `release-config.json` points at your GitHub Releases asset URL template.
3. Run:

```powershell
powershell -ExecutionPolicy Bypass -File z:\not-pokemon\tools\publish_release.ps1 -Version 0.1.0
```

That command packages the exported `.exe` and matching `.pck`, computes SHA-256, writes `release_feed\windows\latest.json`, and also writes `z:\not-pokemon\latest.json` so you can use the same raw GitHub manifest pattern as the existing Shadowfall setup.

## Launcher config

If you want Hex-Launcher to update Riftbound Summoner from a raw GitHub file, point the game's `manifestUrl` to the hosted `latest.json`, for example:

`https://raw.githubusercontent.com/hexaban43/Hex-Studios/main/latest.json`