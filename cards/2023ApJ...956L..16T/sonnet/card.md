# An ALMA-resolved View of 7000 au Protostellar Gas Ring around the Class I Source CrA-IRS 2 as a Possible Sign of Magnetic Flux Advection

`2023ApJ...956L..16T` | The Astrophysical Journal Letters 2023 | first author: Tokuda, Kazuki | arXiv: 2309.13821 | DOI: 10.3847/2041-8213/acfca9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is there an observable gas ring around the Class I protostar CrA-IRS 2 that could be a magnetic wall produced by magnetic flux advection via interchange instability?  
  > "A ring-like structure produced by magnetic flux loss has been predicted theoretically, but no observational identification has been presented." (abstract)
- Target **CrA-IRS 2**: coordinates not stated (mosaic central coordinate 19h01m39.4s, -36d58m16.0s)  
  > "protostar IRS 2 in the Corona Australis (CrA) star-formation region whose distance is 149 pc (cite: Galli_2020)" (Introduction); z/distance 149 pc  
  > "protostar IRS 2 in the Corona Australis (CrA) star-formation region whose distance is 149 pc (cite: Galli_2020)" (Introduction); distance from Galli et al. 2020  
  > "protostar IRS 2 in the Corona Australis (CrA) star-formation region whose distance is 149 pc (cite: Galli_2020)" (Introduction)

## Data provenance

- ALMA projects: 2021.1.00715.S
- bands: Band 6 (1.3 mm)  
  > "using the 12 m array C43-1 configuration with the Band 6 receivers" (Observations and Data Reduction)
- frequencies and spectral setup: C18O and SO: 59 MHz, 480 channels at 219.562 and 219.951 GHz; continuum SPWs at 232.999 and 216.354 GHz  
  > "The C$^{18}$O and SO bandwidths were 59 MHz with 480 channels at central sky frequencies of 219.562 GHz and 219.951 GHz, respectively." (Observations and Data Reduction)
- continuum bandwidth: 1.875 GHz, 1920 channels in each of two SPWs  
  > "The bandwidth and channel number were 1.875 GHz and 1920, respectively, in each." (Observations and Data Reduction)
- arrays: 12 m array  
  > "using the 12 m array C43-1 configuration with the Band 6 receivers" (Observations and Data Reduction)
- configurations: C43-1  
  > "using the 12 m array C43-1 configuration with the Band 6 receivers" (Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: C18O/SO 2.1″×1.3″ (PA −82°); continuum 2.0″×1.3″ (PA −78°)  
  > "2.1$''$ $\times$ 1.3$''$ (P.A. = $-$82 deg.)" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: ~0.2 K per 0.2 km/s channel (lines); ~0.3 mJy/beam (continuum)  
  > "the beam size and sensitivity are 2.0$''$ $\times$ 1.3$''$ (P.A. = $-$78 deg.) and $\sim$0.3 mJy beam$^{-1}$, respectively." (Observations and Data Reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (not stated)
- Line: SO N,J = 5,6–4,5 (not stated)
- Other facility **Herschel/PACS**: 100 and 160 micron images showing a shell-like structure (from literature)  
  > "their Herschel/PACS 100 and 160 $\mu$m images show a bubble or shell-like structure" (Introduction)
- External data: Gas kinetic temperature of 25 K and bolometric luminosity ~0.8 Lsun  
  > "constant gas kinematic temperature of 25 K (cite: Sicilia-Aguilar_2013)" (Results) [from (cite: Sicilia-Aguilar_2013)]
- External data: [H2]/[C18O] abundance 5.9e6  
  > "of 5.9 $\times$10$^{6}$, which is a typical value in the solar neighborhood (cite: Frerking_1982)" (Results) [from (cite: Frerking_1982)]
- External data: Distance 149 pc  
  > "whose distance is 149 pc (cite: Galli_2020)" (Introduction) [from (cite: Galli_2020)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We employed the `tclean` algorithm with the `multi-scale` deconvolver in the analysis." (Observations and Data Reduction)
- deconvolver: multi-scale  
  > "We employed the `tclean` algorithm with the `multi-scale` deconvolver in the analysis." (Observations and Data Reduction)
- weighting robust: natural weighting  
  > "We applied the natural weighting." (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh  
  > "The clean mask regions were automatically determined by the `auto-multithresh` scheme (cite: Kepley_2020)." (Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.1″×1.3″ (PA −82°) lines; 2.0″×1.3″ (PA −78°) continuum  
  > "2.1$''$ $\times$ 1.3$''$ (P.A. = $-$82 deg.)" (Observations and Data Reduction)
- final rms: ~0.2 K at 0.2 km/s channel; ~0.3 mJy/beam continuum  
  > "$\sim$0.2 K at a velocity channel of 0.2 km s$^{-1}$" (Observations and Data Reduction)

### Inherited from earlier work

- Automated clean masking algorithm  
  > "`auto-multithresh` scheme (cite: Kepley_2020)" (Observations and Data Reduction) [from (cite: Kepley_2020)]

### Not stated but needed to reproduce (our reading)

- Multiscale scales list
- Calibration procedure (pipeline vs manual) and flux calibrator
- Cell and image size
- Continuum-subtraction and line-free channels
- Whether primary-beam correction applied
- Clean threshold and niter
- Column density computation details (excitation, optical depth, integration range)
- Ring thickness basis and mass integration region
- Single-dish/ACA combination (none stated)
- Whether 7m/TP data included

## Analysis recipe

1. **image line and continuum data**: tclean multiscale, natural weighting, auto-multithresh  
  > "We employed the `tclean` algorithm with the `multi-scale` deconvolver in the analysis." (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **identify ring and velocity structure**: moment 0/1 maps, channel maps, PV diagram; ring outline determined by eye  
  > "we determined the ring structure guideline based on the boundary by eye as shown in the white dotted circle with a radius of 25$\ensuremath{''}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive systemic velocity**: C18O spectrum at continuum disk position; dip of double-horned profile  
  > "we extracted the C$^{18}$O spectrum at the 1.3 mm continuum disk position" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **derive column density, density and mass of ring**: LTE C18O column density converted to H2  
  > "assuming the local thermodynamical equilibrium (LTE) condition with a constant gas kinematic temperature of 25 K" (Results)
   - assumption: LTE, T = 25 K, [H2]/[C18O] = 5.9e6, ring thickness ~1,000 au (or 100 au)  
  > "Suppose the ring thickness of $\sim$1,000 au (100 au)" (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.4-31: data reduction and imaging  
  > "v.6.4.4-31, in data reduction and imaging" (Observations and Data Reduction)
- **astropy** : listed in software section  
  > "astropy (cite: Astropy18), CASA (cite: CASAteam_2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring diameter | ~7,000 | not stated | au | 2 | We regard it as a quasi-complete ring with a diameter of $\sim$7,000 au around the protostellar source. |
| Ring center projected separation from protostar | ~5,000 | not stated | au | 2 | The projected separation is $\sim$35$\ensuremath{''}$ ($\sim$5,000 au) between the protostar and the ring’s center. |
| Protostar systemic velocity | 6.4 | not stated | km/s | 3 | estimated at 6.4 km s$^{-1}$ |
| Average H2 column density along ring | ~6e21 | not stated | cm^-2 | 4 | we obtained the average H$_2$ column density of $\sim$ 6 $\times$10$^{21}$ cm$^{-2}$ along the ring |
| Ring total mass | ~0.05 | not stated | Msun | 4 | The total mass of the ring is roughly estimated to be $\sim$0.05 $M_{\odot}$ |

## Qualitative findings

- Ring gas is blueshifted ≲1 km/s relative to protostar, with possible expansion; asymmetric velocity, not a symmetric bubble.  
  > "The radial velocity of the gas is $\lesssim1$ km s$^{-1}$ blueshifted from that of the protostar" (abstract)

## Claim tuples

- H: A distinctive gas ring exists around IRS 2 that is not explained by outflows or streamers | E: ALMA Band 6 C18O(2-1) mosaic with moment, channel and PV analysis | R: ~7,000 au diameter ring centered ~5,000 au from the protostar, blueshifted ≲1 km/s | F: Ring is unlike known outflow or streamer features | **supported**
- H: The ring is a magnetic wall from magnetic flux advection by interchange instability | E: Compare ring size, location, and expansion timescale with theory | R: Expansion at ~0.3 km/s gives ~1e5 yr, consistent with Class 0 timescale | F: Plausible, preliminary evidence of flux leakage; theory calculations still needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflow rejected because ring velocity is too small and no high-velocity component >~5 km/s; streamer rejected because SO connection only near systemic velocity  
  > "the observed relative velocity of the C$^{18}$O ring with respect to the protostar is too small for the outflow interpretation" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Ring may be a coincidental line-of-sight cloud component; theoretical calculations needed.  
  > "it cannot be completely ruled out that the ring structure is just a coincidence of unrelated line-of-site components" (Discussion)
- Caveat (inferred, ours): No modelling or simulation specific to IRS 2 supports the magnetic wall interpretation
- Caveat (inferred, ours): No uncertainties on masses or column densities; LTE with fixed T and abundance
- Caveat (inferred, ours): Ring defined by eye
- Caveat (inferred, ours): No magnetic field measurement

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and flux details
- Missing: Multiscale scales, cell and image size
- Missing: Column density and mass calculation specifics
- Missing: Ring definition is by eye
- Data volume (inferred): ~100-300 GB raw (137-pointing 12m mosaic)
- Score (inferred): 3/5, Project code and main imaging settings given, but many details and the mass calculation are underspecified.
- Rediscovery candidate: no, Results are largely morphological/by-eye with few numeric results and incomplete recipe; public status not stated.

## Links

- Method: (cite: Kepley_2020) (auto-multithresh masking)
- Companion: K. Tachihara et al. in prep. (forthcoming paper discussing the CrA ring further)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 32,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
