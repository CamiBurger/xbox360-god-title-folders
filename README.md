# xbox360-god-title-folders

> [!WARNING]
> **This didn't actually work for what it was built for.** It was meant to
> pre-scaffold a GOD folder layout that an Xbox 360 dashboard/homebrew app
> would recognize, but that didn't pan out in practice. I can't think of
> another real use for it. It's published as-is, mostly for reference —
> don't expect it to solve anything for you. Use at your own risk, and don't
> rely on it for an actual GOD setup.

A self-contained Bash script that scaffolds empty `0000000000000000/<TITLE_ID>`
folders for known Xbox 360 GOD (Games on Demand) titles.

The idea was to prepare a directory layout (e.g. on a USB drive or hard disk
used with an Xbox 360) before copying in the actual game data. The script
does not download, contain, or provide any copyrighted game files — it only
creates empty folder structure.

## Usage

```bash
./make_god_folders
```

Run it from anywhere — the script locates its own directory and creates the
`0000000000000000/` folder next to itself, not in your shell's current
working directory.

What it does:

- Creates a `0000000000000000/<TITLE_ID>/` folder for every title ID embedded
  in the script.
- Prunes any existing `0000000000000000/<TITLE_ID>/` folder that is **empty**
  and no longer in the embedded list (stale folders that still contain files
  are left alone and reported).
- Prints a summary with the total folder count when finished.

## Requirements

- Bash
- Standard Unix tools (`mkdir`, `rmdir`, `grep`, `mktemp`) — no external
  dependencies.

## After running

Copy your own extracted GOD game data into the matching `<TITLE_ID>` folder
under `0000000000000000/`.
