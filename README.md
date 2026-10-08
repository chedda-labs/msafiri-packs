# Msafiri terrain packs

Region packs for [Msafiri](https://github.com/chedda-labs/msafiri)'s offline line-of-sight
checks. Each pack is a set of `.msdt` elevation tiles (format in `core/src/terrain.rs` of the
app repo), published as the assets of one release, tagged `<pack id>-v<version>`.

The app reads `manifest.json` from the **latest** release
(`releases/latest/download/manifest.json`). Each pack in it carries a `base_url` pinned to its
own release, so a phone mid-download keeps fetching one consistent version. Every release
must therefore attach a manifest listing **all** current packs.

Packs are built with `msafiri-packer` in the app repo:

```sh
cargo run --release -p msafiri-packer -- --src glo30/ --out out/ --id central-kenya \
  --name "Central Kenya" --bounds 36.5,-1.5,37.6,0 --arcsec 3 --version 1 \
  --base-url https://github.com/chedda-labs/msafiri-packs/releases/download/central-kenya-v1
```

## Data

Tiles are block-averaged to 3 arc-seconds (about 90 m) from the Copernicus DEM GLO-30.

Produced using Copernicus WorldDEM-30 © DLR e.V. 2010–2014 and © Airbus Defence and Space
GmbH 2014–2018, provided under COPERNICUS by the European Union and ESA; all rights reserved.
The Copernicus DEM is distributed under the
[Copernicus DEM licence](https://spacedata.copernicus.eu/documents/20123/121286/CSCDA_ESA_Mission-specific+Annex_31_Oct_22.pdf).
