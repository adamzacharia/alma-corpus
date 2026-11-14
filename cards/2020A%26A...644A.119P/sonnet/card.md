# ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). III. The interplay between gas and dust in the protoplanetary disk of DG Tau

`2020A&A...644A.119P` | Astronomy and Astrophysics 2020 | first author: Podio, L. | arXiv: 2011.01081 | DOI: 10.1051/0004-6361/202038600

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the distribution and abundance of H2CO, CS and CN in the DG Tau protoplanetary disk, and how do they compare with the dust distribution?  
  > "We aim to characterize the distribution and abundance of molecules in the protoplanetary disk of DG Tau and to compare them with its dust distribution." (abstract)
- Target **DG Tau**: coordinates _not stated_; z/distance 121 ± 2 pc  
  > "One of the sources targeted in the context of ALMA-DOT is the T Tauri star DG Tau ($d=121\pm2$ pc, (cite: gaia16; gaia18))." (Introduction); distance from Gaia (gaia16; gaia18)  
  > "One of the sources targeted in the context of ALMA-DOT is the T Tauri star DG Tau ($d=121\pm2$ pc, (cite: gaia16; gaia18))." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00846.S
- bands: _not stated_
- frequencies and spectral setup: 12 high-resolution (0.122 MHz) SPWs plus one lower resolution (0.977 MHz) continuum SPW also covering CS 5-4  
  > "The correlator setup consists of 12 high-resolution (0.122 MHz) spectral windows (SPWs)" (2.1 Observations); "one lower resolution spectral window (0.977 MHz) for the continuum also covering the CS $5-4$ line" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA Cycle 4 observations  
  > "ALMA observations of DG Tau were performed during Cycle 4 in August 2017" (2.1 Observations)
- configurations: _not stated_
- baselines: 17 m to 3.7 km  
  > "with baselines ranging from 17 m to 3.7 km" (2.1 Observations)
- angular resolution: ~0.15 arcsec (~18 au)  
  > "at an unprecedented resolution of $\sim 0.15\ensuremath{''}$, or $\sim 18$ au" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.12 mJy/beam; line rms 0.6-1.7 mJy/beam per channel  
  > "The continuum image has an r.m.s. of $0.12$ mJy/beam." (2.1 Observations)
- time on source: _not stated_
- observing dates: August 2017  
  > "performed during Cycle 4 in August 2017" (2.1 Observations)
- pi or archival as stated: PI L. Podio  
  > "This paper uses ALMA data from project 2016.1.00846.S (PI: L. Podio)." (Acknowledgements)
- Line: o-H2CO 3(1,2)-2(1,1) (225697.775 MHz)
- Line: CS 5-4 (244935.557 MHz)
- Line: CN 2-1 hyperfine components (226874.1908 MHz (J=5/2-3/2, F=5/2-3/2))
- Other facility **ALMA 0.87 mm polarimetric map (Bacciotti et al. 2018)**: 0.87 mm continuum/polarization image used for unsharp masking and comparison  
  > "as well as to that presented by (cite: bacciotti18) at 0.87 mm" (3.2 Dust substructures)
- External data: Molecular parameters and partition functions from CDMS  
  > "Molecular parameters from the CDMS database (cite: muller01)." (Table 1) [from (cite: muller01)]
- External data: H2CO ortho/para ratio used for total H2CO column  
  > "based on the o/p ratio estimated by (cite: guzman18a)" (3.3 Molecular column density) [from (cite: guzman18a)]
- External data: Dust opacity 2.3 cm2/g at 1.3 mm  
  > "is assumed to be a global 2.3 $\rm cm^2\,g^{-1}$ (cite: beckwith90)" (4.2 The interplay of gas and dust) [from (cite: beckwith90)]
- External data: CO snowline ~30 au from ProDiMo disk model  
  > "at $R_{\rm CO} \sim 30$ au, as computed by the thermo-chemical disk model ProDiMo (cite: podio13)" (4.2 The interplay of gas and dust) [from (cite: podio13)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, standard procedures  
  > "Data reduction was carried out following standard procedures using the ALMA pipeline in CASA 4.7.2." (2.1 Observations)
- casa version: CASA 4.7.2  
  > "using the ALMA pipeline in CASA 4.7.2" (2.1 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 and J0510+1800  
  > "The flux calibration was performed using the quasars J0238+1636 and J0510+1800" (2.1 Observations)
- flux scale uncertainty: ~10%  
  > "obtaining an accuracy of $\sim 10\%$" (2.1 Observations)
- self calibration: Self-cal on continuum using line-free channels; phase solutions applied to continuum-subtracted SPWs  
  > "Self-calibration was performed on the source continuum emission by combining a selection of line-free channels and applying the phase-solutions to the continuum-subtracted SPWs." (2.1 Observations)

### Imaging

- task: tclean  
  > "Continuum images and spectral cubes were produced with "tclean"" (2.1 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs parameter 0.5  
  > "and a Briggs parameter of 0.5" (2.1 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactive mask until residuals show no appreciable signal  
  > "using an interactive mask on the visible signal until the residuals show no appreciable signal" (2.1 Observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum level estimated from line-free channels adjacent to lines  
  > "The continuum subtraction is performed by estimating the continuum level from the frequency range adjacent to the targeted lines" (2.1 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: H2CO 0.17x0.13 arcsec; CS 0.13x0.10; CN 0.14x0.12  
  > "$0.13\ensuremath{''} \times 0.10\ensuremath{''}$ ($-9.6\ensuremath{^\circ}$)" (Table 1)
- final rms: continuum 0.12 mJy/beam; lines 0.6-1.7 mJy/beam  
  > "The continuum image has an r.m.s. of $0.12$ mJy/beam." (2.1 Observations)

### Inherited from earlier work

- Column density procedure same as for H2CO  
  > "Here, we followed the same procedure to constrain the column density of CS and CN." (3.3 Molecular column density) [from (cite: podio19)]
- Disk ring definition 0.33-0.75 arcsec used for integration  
  > "We integrated the relative emission over the same area as the H$_2$CO (a circular ring extending from $0.33\ensuremath{''}$ to $0.75\ensuremath{''}$)" (3.3 Molecular column density) [from (cite: podio19)]
- Unsharp masking approach (divide by local variance, subtract smoothed image)  
  > "Similarly to (cite: garufi16), here we first divided the original image by the local variance in each pixel and then subtracted the image smoothed by 60 mas." (3.2 Dust substructures) [from (cite: garufi16)]
- Exclusion of dust opacity as cause of inner depression  
  > "Following (cite: podio19) we exclude that the depression in the H$_2$CO and CS emission is due to dust opacity for $r>20$ au." (4.1 The origin of ring-like emission) [from (cite: podio19)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction and self-calibration
- Self-calibration solution intervals and number of iterations
- tclean cell size, image size, clean threshold, and niter
- Spectral cube channel binning/velocity resolution details beyond Table 1
- Exact phase center/coordinates of DG Tau
- Exact LTE column-density conversion formulas and partition function details
- Procedure for unsharp-masking variance window size
- Gaussian fit method details for ring peak positions

## Analysis recipe

1. **Calibrate and image data**: ALMA pipeline calibration, self-calibration on continuum, tclean imaging and continuum subtraction  
  > "Data reduction was carried out following standard procedures using the ALMA pipeline in CASA 4.7.2." (2.1 Observations)
   - software: CASA, tclean
   - parameter: Briggs robust 0.5  
  > "and a Briggs parameter of 0.5" (2.1 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and radial profiles**: Moment-0 integrated over Vsys ±3 km/s with 3σ clipping (none for CN); azimuthal averaging of unclipped moment-0 after deprojection  
  > "The radial intensity profiles of the lines and of the 1.3 mm continuum emission are obtained by azimuthally averaging the unclipped moment-0 maps after deprojecting for the disk inclination" (2.2 Data products)
   - parameter: Vsys = +6.24 km/s; PA=135 deg, i=35 deg  
  > "$V_{\rm sys} = +6.24$ km s$^{-1}$" (2.2 Data products); "We obtain PA$=135\ensuremath{^\circ}$ and i$=35\ensuremath{^\circ}$." (Footnote 1)
   - fitting: Gaussian fit to peak of radial profile; position uncertainty ~1/5 of beam  
  > "the position of the intensity peak determined by Gaussian fitting the peak profile is affected by an uncertainty of approximately one-fifth of the nominal resolution imposed by the beam" (3.1 Spatial distribution)
   - validation: 10 au offset between H2CO and CS peaks exceeds position uncertainty  
  > "Therefore, the radial offset between the H$_2$CO and CS emission peaks is real and not due to a resolution effect." (3.1 Spatial distribution)
3. **Find dust substructure**: Unsharp masking of 1.3 mm and 0.87 mm continuum images  
  > "we applied an unsharp masking filter to the continuum image at 1.3 mm as well as to that presented by (cite: bacciotti18) at 0.87 mm" (3.2 Dust substructures)
   - parameter: smoothing 60 mas  
  > "then subtracted the image smoothed by 60 mas" (3.2 Dust substructures)
   - fitting: _not stated_
   - validation: Compared with second derivative of intensity profile from Podio et al. 2019 (38-44.5 au)  
  > "is between 38 and 44.5 au, in perfect agreement with the position of the ring revealed by applying unsharp masking" (3.2 Dust substructures)
4. **Derive molecular column densities**: Ring-integrated flux (0.33-0.75 arcsec) converted to column density assuming LTE and optically thin emission with CDMS parameters  
  > "converted this integrated flux into column density assuming local thermodynamic equilibrium (LTE) and optically thin emission" (3.3 Molecular column density)
   - parameter: Tex = TK = 20-100 K  
  > "compute the column density of H$_2$CO, CS, and CN for $T_{\rm ex} = T_{\rm K} = 20-100$ K" (3.3 Molecular column density)
   - assumption: LTE, optically thin, o/p ratio of H2CO from Guzman+18  
  > "based on the o/p ratio estimated by (cite: guzman18a)" (3.3 Molecular column density)
   - fitting: _not stated_
   - validation: Brightness temperature ~1.5 K well below gas temperature, so lines likely optically thin; may be underestimated by a factor of a few  
  > "Thus, we conclude that the observed lines are likely optically thin." (3.3 Molecular column density)
5. **Estimate dust mass of disk and ring**: Optically thin dust mass from 1.3 mm flux  
  > "The dust mass of disk and ring can be obtained from the aforementioned fluxes in the assumption of optically thin emission" (4.2 The interplay of gas and dust)
   - parameter: Disk flux 0.29 Jy, ring flux 0.04 Jy  
  > "The flux integrated over this region is 0.29 Jy whereas the ring flux amounts to 0.04 Jy." (4.2 The interplay of gas and dust)
   - assumption: kappa(1.3mm)=2.3 cm2/g, Tdust=20 K, d=121 pc  
  > "Planck function $B_{\lambda}(T_{\rm dust})$ is calculated from an overall dust temperature $T_{\rm dust}$ of 20 K" (4.2 The interplay of gas and dust)
   - fitting: Gaussian fit to observed emission gives disk major axis 0.45 arcsec and i=35 deg  
  > "A Gaussian fit to the observed emission yields a disk major axis of $0.45\ensuremath{''}$ and a disk inclination $i$ of 35$\ensuremath{^\circ}$." (4.2 The interplay of gas and dust)
   - validation: _not stated_

## Software

- **CASA** 4.7.2: ALMA pipeline calibration and imaging  
  > "using the ALMA pipeline in CASA 4.7.2" (2.1 Observations)
- **tclean** : continuum images and spectral cubes  
  > "Continuum images and spectral cubes were produced with "tclean"" (2.1 Observations)
- **ProDiMo** : CO snowline location from literature model (Podio+13)  
  > "as computed by the thermo-chemical disk model ProDiMo (cite: podio13)" (4.2 The interplay of gas and dust)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2CO ring emission peak radius | ~60 | ~3.6 au | au | 2 | the H$_2$CO emission peaks at $\sim 60$ au and extends out to $\sim 120$ au |
| CS ring emission peak radius | ~70 | ~3 au | au | 2 | while the CS emission peaks at $\sim 70$ au and extends out to $\sim 130$ au |
| CN emission peak radius | ~80 | not stated | au | 2 | with a peak at $\sim 80$ au and extending out to $\sim 500$ au |
| Total H2CO column density | 2.4-8.6e13 | not stated | cm^-2 | 4 | a total column density of $2.4-8.6 \times 10^{13}$ cm$^{-2}$ for H$_2$CO |
| CS column density | 1.7-2.5e13 | not stated | cm^-2 | 4 | and of $1.7 - 2.5 \times 10^{13}$ cm$^{-2}$ for CS |
| CN column density | 1.9-4.7e13 | not stated | cm^-2 | 4 | a column density of $1.9 - 4.7\times 10^{13}$ cm$^{-2}$ is estimated |
| Dust ring radius from unsharp masking | ~40 | not stated | au | 3 | This technique revealed a ring at $\sim40$ au in the continuum maps at 0.87 mm and at 1.3 mm |
| Total dust mass | ~120 | not stated | Earth masses | 5 | the total dust mass is $\sim 120$ M$_{\oplus}$ and the ring dust mass is $\approx16\,{\rm M_{\oplus}}$ |
| Ring dust mass | ~16 | not stated | Earth masses | 5 | the total dust mass is $\sim 120$ M$_{\oplus}$ and the ring dust mass is $\approx16\,{\rm M_{\oplus}}$ |
| Peak brightness temperature of H2CO and CS ring spectra | ~1.5 | not stated | K | 4 | the intensity peak of the H$_2$CO $3_{1,2}-2_{1,1}$ and CS $5-4$ integrated spectra is T$_{\rm B} \sim 1.5$ K |

## Qualitative findings

- H2CO and CS emission come from a disk ring at the edge of the 1.3 mm continuum; CS is displaced outward by ~10 au  
  > "Both H$_2$CO and CS emission originate from a disk ring located at the edge of the 1.3 mm dust continuum." (abstract)
- CN arises from an outer, more extended disk/envelope region  
  > "CN originates from an outermost and more extended disk/envelope region" (abstract)
- CS also traces streams possibly accreting onto the disk  
  > "while CS also probes two streams of material possibly accreting onto the disk" (abstract)

## Claim tuples

- H: Do H2CO and CS trace the same disk region, linked chemically? | E: Compare azimuthally averaged radial profiles of the lines | R: Both are rings at the mm continuum edge, with CS peak ~10 au further out | F: Molecules are co-spatial and likely chemically linked | **supported**
- H: Is there dust substructure related to molecular rings? | E: Unsharp masking of 1.3 mm and 0.87 mm continuum | R: Ring at ~40 au, just outside CO snowline (~30 au), with ~10% flux enhancement | F: Possible change in dust properties outside the CO snowline linked to molecular emission and polarization change | **partially**
- H: Where does CN emission originate? | E: Channel maps, radial profile, and spectra integrated over ring and 3 arcsec | R: CN barely detected, peak ~80 au extending to ~500 au; spectra affected by envelope | F: CN is outside the dusty disk and likely largely from the envelope | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Unsharp masking used to highlight possible dust substructures  
  > "To highlight the possible presence of dust substructures, we applied an unsharp masking filter" (3.2 Dust substructures)
- Alternative: Dust opacity rejected as the cause of the inner depression for r>20 au  
  > "we exclude that the depression in the H$_2$CO and CS emission is due to dust opacity for $r>20$ au" (4.1 The origin of ring-like emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Column densities may be underestimated by a factor of a few if lines are mildly optically thick  
  > "our estimates of the column densities may also be underestimated by a factor of a few" (3.3 Molecular column density)
- Limitation (authors): Unsharp-masked ring morphology is uncertain due to the technique's arbitrariness  
  > "the precise morphology of the ring should be interpreted with caution given the arbitrariness of the technique" (3.2 Dust substructures)
- Limitation (authors): Excitation temperature must be assumed since only one line per species  
  > "The temperature of the emitting layer has to be assumed as we have only one line per species." (3.3 Molecular column density)
- Caveat (inferred, ours): Column densities depend on an assumed temperature range and single-line LTE
- Caveat (inferred, ours): Dust mass assumes uniform kappa and T and is not tied to the ring-enhancement uncertainty
- Caveat (inferred, ours): Ring-like line emission may be affected by continuum over-subtraction, not separated quantitatively
- Caveat (inferred, ours): Link between molecular rings and dust ring is suggestive, not tested with models

## Reproducibility

- Data public (paper): Project 2016.1.00846.S cited; public status not explicitly stated  
  > "This paper uses ALMA data from project 2016.1.00846.S (PI: L. Podio)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cell/image size and clean threshold
- Missing: Line-free channel selection
- Missing: Self-calibration parameters
- Missing: Exact column density formulas and flux integration regions beyond ring radii
- Missing: 0.87 mm polarization image from Bacciotti+18
- Data volume (inferred): ~100-300 GB raw for the Cycle 4 12m dataset with 13 spectral windows
- Score (inferred): 3/5, Data and main software are stated and the approach is simple, but many imaging and self-calibration parameters are unstated and some inputs are inherited from Podio+19.
- Rediscovery candidate: no, Recipe is incomplete; key imaging parameters and inherited choices are unspecified and results are partly qualitative.

## Links

- Method: (cite: podio19) (Earlier H2CO analysis and column density procedure for this source)
- Method: (cite: garufi16) (Unsharp masking technique)
- Companion: (cite: podio19) (ALMA-DOT H2CO analysis of DG Tau)
- Companion: (cite: garufi20b) (ALMA-DOT study of DG Tau B)
- Companion: (cite: podio20a) (ALMA-DOT study of IRAS 04302+2247)
- Related: ALMA-DOT (ALMA chemical survey of Disk-Outflow sources in Taurus)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 59,
  "rate": 0.702
 },
 "evidence_ok": true
}
```
