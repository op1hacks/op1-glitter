# theme creation guide

Valid op1-glitter themes must have at least a key "global" in the top-level object. Optionally, additional keys can be added which have the same name as a .svg in an unpacked OP-1 firmware's `/content/display/` directory. 

> to unpack a firmware, run `op1unpacker unpack (firmware)`.

Any keys not associated with a file in this directory will be ignored. Although it is not required, values for theme author, name, and description are good to have in a key named `theme_meta` :)

For example:

```json
    {
        "theme_meta": {
            "name": "neo",
            "description": "This is a very bright theme centered around the colors purple, cyan, and orange.",
            "author": "nanobot567",
        }
        "global": {
            ...
        }
    ...
```

The values of the `global` key or filename keys must be objects. The keys within can either be a color in hex notation (ex. #1049e8, #ffffff), or the name of a SVG element's ID.

If the key is a hex color, the value must be another color in hex notation...

```json
{
    ...
    "presetbrowser": {
        "#21005b": "#093654"
    },
    ...
}
```

If the key is an SVG element ID, the value can either be a hex color...

```json
{
    ...
    "ok": {
        "cowbella": "#b88f5b",
    ...
}
```

...or a table containing the attribute to modify (usually `stroke` or `fill`), then the hex color...

```json
{
    ...
    "ok": {
        "druma": ["stroke", "#9ba8a8"]
    ...
}
```

...or a table containing an original hex color, then the new hex color to replace it with.

```json
{
    ...
    "ok": {
        "synth": ["#ff90a7", "#9ba8a8"]
    ...
}
```


> check out the example themes in `examples/` if you're confused!

## finding a UI element's SVG ID

[Inkscape](https://inkscape.org/) is a good tool for the job! Open the .svg and click on the element you'd like to get the ID of, and it should highlight the ID in the Layers and Objects panel.

## OP-1 SVGs

Some of the SVGs in `content/display/` are pretty self explanatory, although most are named weirdly:

- `bode.svg`: cwo effect
- `cls.svg`: cluster synth engine
- `drum2.svg`: drum sample editor
- `ftwo.svg`: nitro effect
- `id.svg`: dna synth engine
- `lander.svg`: chop lifter!
- `mllp.svg`: punch effect
- `ok.svg`: finger sequencer
- `pd.svg`: phase synth engine
- `pls.svg`: pulse synth engine
- `ptch.svg`: phone effect
- `rymd.svg`: spring effect
- `simple.svg`: arpeggio sequencer
- `slump.svg`: voltage synth engine
- `st.svg`: string synth engine
- `t10.svg`: digital synth engine

## commonly used OP-1 colors

- 00ed95: green encoder
- ff3a5d: red encoder
- 698eff: blue encoder
- dfd9ff: white encoder, most dynamic elements use this color (tape, high EQ, changing text)
- ffffff: white
- aeb1dc: "text" white
- 9256d7: purple background
- 4d9eff: alternate, lighter blue
- 383572: dull dark purple
