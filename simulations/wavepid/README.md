# WavePID Simulation

Photon origin tracking study for IceCube optical modules using Geant4. For full documentation, see [the WavePID documentation page](https://icecube.github.io/OMSim/md_extra__doc_233__wavepid.html) or `documentation/extra_doc/33_wavepid.md`.

## Quick Start

```bash
# Build
mkdir build && cd build
cmake ..
make OMSim_WavePID_study -j$(nproc)

# Run: 100 events, DOM in SPICE ice, 50 GeV mu- at 5m impact parameter
./OMSim_WavePID_study -n 100 --detector_type 3 --environment 2 -r 5 -e 50 -p mu- -o output

# Run: pDOM (HQE) with harness
./OMSim_WavePID_study -n 100 --detector_type 7 --environment 2 --place_harness -r 5 -e 50 -p mu- -o output_pdom

# Visualization
./OMSim_WavePID_study --detector_type 3 --simple_PMT -v --macro vis_wavepid.mac
```

## Output

ROOT file (`<output>_hits.root`) with TTree `PhotonHits` containing per-photon information: hit time, wavelength, photon origin classification, parent particle info, hit position/direction, and PMT number.

## Detector Types

| `--detector_type` | Module |
|-------------------|--------|
| 1 | Single PMT |
| 2 | mDOM |
| 3 | DOM |
| 4 | LOM16 |
| 5 | LOM18 |
| 6 | D-Egg |
| 7 | pDOM (HQE deepcore) |
