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

A self-contained Bash script that scaffolds empty `0000000000000000/<TITLE_ID>`
folders for known Xbox 360 GOD (Games on Demand) titles.

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
