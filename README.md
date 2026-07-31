# xbox360-god-title-folders

> [!WARNING]
> **This didn't actually work for what it was built for.** The goal was to
> build a GOD-recognizable folder for every Xbox 360 game, all at once, and
> use that to trick XM360 into thinking I owned every game so I could pull
> the full DLC list for each one. It
> didn't work — an empty folder-of-folders with the right title IDs wasn't
> enough to fool XM360's detection. It's possible populating each folder with
> its `00007000` or `00020000` subfolder (with real content, not just empty
> dirs) would get further, but I'm done poking at this. I can't think of any
> other real use for it. It's published as-is, mostly for reference — don't
> expect it to solve anything for you, and don't rely on it for an actual GOD
> setup.

A Bash script that scaffolds empty `0000000000000000/<TITLE_ID>` folders for
known Xbox 360 GOD (Games on Demand) titles, driven by `gamelist_xbox360.csv`
(bundled in this repo).

The idea was to prepare a directory layout (e.g. on a USB drive or hard disk
used with an Xbox 360) before copying in the actual game data. The script
does not download, contain, or provide any copyrighted game files — it only
creates empty folder structure.

This makes like 1k files btw, this is kinda not helpful for any aurora or xbox 360
hdd GOD formatting. Just a tool I made to try to archive a CSV list of all possible 
DLC's parse-able from XM360. And once again, it did not work for this.

## Usage

```bash
./make_god_folders
```

Run it from anywhere — the script locates its own directory and creates the
`0000000000000000/` folder next to itself, not in your shell's current
working directory. `gamelist_xbox360.csv` must stay in that same directory.

What it does:

- Reads `gamelist_xbox360.csv` (tab-separated: `title_id`, `media_id`,
  `title_name`) and keeps only rows with a non-empty `media_id` — that's
  the signal used to filter out demos, dashboard items, and other junk rows
  that aren't real games.
- Creates a `0000000000000000/<TITLE_ID>/` folder for every title ID that
  survives the filter.
- Prunes any existing `0000000000000000/<TITLE_ID>/` folder that is **empty**
  and no longer in the CSV-derived list (stale folders that still contain
  files are left alone and reported).
- Prints a summary with the total folder count when finished.

## Requirements

- Bash
- Standard Unix tools (`mkdir`, `rmdir`, `grep`, `awk`, `sort`, `mktemp`) —
  no external dependencies beyond what ships with macOS/Linux.

## After running

Copy your own extracted GOD game data into the matching `<TITLE_ID>` folder
under `0000000000000000/`.
