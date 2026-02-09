---
name: svg-to-png
description: Convert SVG files to PNG using Inkscape CLI. Use when the user asks to convert SVG to PNG, export SVG as image, or generate PNG from SVG files.
---

# SVG to PNG Converter (Inkscape)

Convert SVG files to PNG format using Inkscape's command-line interface.

## Inkscape Path

Inkscape may be installed in different locations. Detect the correct path:

```bash
which inkscape 2>/dev/null || ls /Applications/Inkscape.app/Contents/MacOS/inkscape 2>/dev/null
```

Use whichever path is found. If neither exists, inform the user to install Inkscape:
- macOS: `brew install --cask inkscape`
- Linux: `sudo apt install inkscape`

## Basic Conversion

```bash
inkscape <input.svg> --export-type=png --export-filename=<output.png>
```

## Common Options

| Option | Description | Example |
|--------|-------------|---------|
| `--export-width=N` | Set output width in pixels | `--export-width=1080` |
| `--export-height=N` | Set output height in pixels | `--export-height=878` |
| `--export-dpi=N` | Set resolution (default 96) | `--export-dpi=300` |
| `--export-background=COLOR` | Set background color | `--export-background=#ffffff` |
| `--export-background-opacity=N` | Background opacity (0.0-1.0) | `--export-background-opacity=0` |

## Examples

### Fixed dimensions (e.g. Line banner 1080x878)

```bash
inkscape input.svg --export-type=png --export-filename=output.png --export-width=1080 --export-height=878
```

### High-DPI (retina @2x)

```bash
inkscape input.svg --export-type=png --export-filename=output@2x.png --export-dpi=192
```

### Transparent background

```bash
inkscape input.svg --export-type=png --export-filename=output.png --export-background-opacity=0
```

### Batch conversion (all SVGs in a directory)

```bash
for f in *.svg; do inkscape "$f" --export-type=png --export-filename="${f%.svg}.png"; done
```

## Workflow

1. Confirm the input SVG path exists
2. Determine output path (default: same directory, same name with `.png` extension)
3. Ask about dimensions/DPI if the user hasn't specified
4. Run the conversion command
5. Verify the output file was created with `ls -lh`
6. Show the PNG to the user with the Read tool so they can preview it

## Notes

- Inkscape warnings about duplicate options or extensions are harmless — ignore them
- `feDropShadow` SVG filter is NOT supported by Inkscape. Use the equivalent `feGaussianBlur` + `feOffset` + `feFlood` + `feComposite` + `feMerge` chain instead
- If the output looks wrong, check for unsupported SVG features in the Inkscape stderr output
