# AFOP — LocPack Converter

Converts Snowdrop engine localisation files between `.locpack` (CSV) and `.locpackbin` (binary) in both directions.

Supports **Avatar: Frontiers of Pandora** and **Star Wars: Outlaws** locpack files.

---

## Usage

Use the **Browse File** button (or click the drop zone) and select one or more files. Direction is detected automatically from the file extension.

| Input | Output |
|-------|--------|
| `file.locpack` | `file.locpackbin` |
| `file.locpackbin` | `file.locpack` |

You can select multiple files in one browse session — each is converted in sequence.

---

## File format

### `.locpack` (CSV text, `\r\n` line endings)

Two variants are auto-detected from the header row:

**Menus** — 4 fields per row:
```
GUID,lineVer,maxLen,text
```

**Subtitles** — 6 fields per row:
```
GUID,unk0,unk1,unk2,unk3,text
```

Text fields are CSV-quoted when they contain commas, double-quotes, or newlines.

### `.locpackbin` (binary)

Binary encoding of the same data. Uses a custom 16-byte GUID layout, mixed little/big-endian integer fields, and variable-length text with a 16-bit length prefix.

---

## Building the exe

Run `build_all.bat` from the `AFOP_HEX_TOOLS` root. The output will be at:
```
dist\AFOP_LocPack_Converter\AFOP_LocPack_Converter.exe
```

Place `locpack_converter.ico` in this folder before building to embed a custom icon.
