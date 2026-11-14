# A centrally concentrated sub-solar-mass starless core in the Taurus L1495 filamentary complex

`2019PASJ...71...73T` | Publications of the Astronomical Society of Japan 2019 | first author: Tokuda, Kazuki | arXiv: 1904.05490 | DOI: 10.1093/pasj/psz051

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Is the sub-solar-mass starless core MC5-N in Taurus L1495 centrally concentrated and evolved enough to be a progenitor of brown dwarf(s) or very low-mass star(s)?  
  > "brown dwarf(s) or very low-mass star(s) may be going to be formed in this core." (abstract)
- Target **MC5-N (Taurus L1495)**: coordinates _not stated_; z/distance ~140 pc  
  > "which is corresponding to $\sim$1050 au $\times$ 840 au at a distance of Taurus ($\sim$140 pc, (cite: Elias78))" (2.2 1.2 mm continuum: the Atacama Compact Array); distance from Elias78  
  > "which is corresponding to $\sim$1050 au $\times$ 840 au at a distance of Taurus ($\sim$140 pc, (cite: Elias78))" (2.2 1.2 mm continuum: the Atacama Compact Array)

## Data provenance

- ALMA projects: 2016.1.00928.S
- bands: Band 6 (1.2 mm)  
  > "in both Band 6 (1.2 mm) dust continuum and molecular lines toward 16 dense cores" (2.2 1.2 mm continuum: the Atacama Compact Array)
- frequencies and spectral setup: Two spectral windows (H13CO+ 3-2, H13CN 3-2), 58.59 MHz, 1920 channels each  
  > "targeting H$^{13}$CO$^{+}$ (3–2) and H$^{13}$CN (3–2), and the correlator for each spectral window was set to have a bandwidth of 58.59 MHz with 1920 channels." (2.2 1.2 mm continuum: the Atacama Compact Array)
- continuum bandwidth: three basebands, 1875 MHz bandwidth  
  > "We used three basebands for the continuum emission with a bandwidth of 1875 MHz." (2.2 1.2 mm continuum: the Atacama Compact Array)
- arrays: ACA 7 m array (continuum), 7 m + Total Power (lines)  
  > "The dust continuum and molecular line observations were conducted with the 7 m array alone and with both the 7 m array and the TP array, respectively." (2.2 1.2 mm continuum: the Atacama Compact Array)
- configurations: _not stated_
- baselines: uv range 6.5–34 kλ  
  > "The $uv$ range of the 7 m array data is 6.5–34 k$\lambda$." (2.2 1.2 mm continuum: the Atacama Compact Array)
- angular resolution: 7.5" x 5.2" (PA = -55 deg)  
  > "resultant synthesized beam size of the MC5-N observation was 7$\ensuremath{''}$5 $\times$ 5$\ensuremath{''}$2 (PA = $-$55$\degree$)" (2.2 1.2 mm continuum: the Atacama Compact Array)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma = 0.8 mJy/beam  
  > "The sensitivity of the continuum observation (1$\sigma$ noise level) was 0.8 mJy beam$^{-1}$." (2.2 1.2 mm continuum: the Atacama Compact Array)
- time on source: _not stated_
- observing dates: October 2016 to May 2017  
  > "The observations have been done during October 2016 and May 2017." (2.2 1.2 mm continuum: the Atacama Compact Array)
- pi or archival as stated: PI Tachihara, Cycle 4  
  > "ALMA Cycle 4 (P.I.: Tachihara, #2016.1.00928.S)" (2.2 1.2 mm continuum: the Atacama Compact Array)
- Line: H13CO+ 3-2 (not stated)
- Line: H13CN 3-2 (not stated)
- Other facility **IRAM 30 m / MAMBO-2**: 1.2 mm single-dish continuum map (11" beam) used for feathering and profiles  
  > "The FWHM (full width at half-maximum) size of the main beam on the sky was measured to be 11$\ensuremath{''}$ based on beam maps of Uranus." (2.1 1.2 mm continuum: the IRAM 30 m telescope)
- Other facility **Nobeyama 45 m**: N2H+ (1-0) and N2D+ (1-0) maps for deuterium fraction and linewidths  
  > "The N$_{2}$D$^{+}$ (1–0) observations were carried out in the on-the-fly (OTF) mapping mode" (2.3 N2H+ and N2D+: the Nobeyama 45 m telescope)
- External data: Gas temperature ~9 K from NH3 used as dust temperature  
  > "We use 9 K as the dust temperature to derive the column density in this study." (3.1) [from (cite: Seo15)]
- External data: Herschel Gould Belt dust temperature ~8 K and mass ~0.4 Msun comparison  
  > "actually, (cite: Marsh16) using the *Herschel* data also derived the similar mass of $\sim$0.4 $M_{\odot}$." (3.1) [from (cite: Marsh16)]

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

- task: CLEAN in CASA  
  > "We used the natural weighting for the CLEAN process" (2.2)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used the natural weighting for the CLEAN process" (2.2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: feathering of 7 m and IRAM 30 m data per CASA instruction  
  > "We used the feathering technique to combine the two different data sets in accordance with the CASA instruction" (3.1)
- smoothing: _not stated_
- final beam: 7.5" x 5.2", PA -55 deg  
  > "resultant synthesized beam size of the MC5-N observation was 7$\ensuremath{''}$5 $\times$ 5$\ensuremath{''}$2 (PA = $-$55$\degree$)" (2.2)
- final rms: 0.8 mJy/beam  
  > "The sensitivity of the continuum observation (1$\sigma$ noise level) was 0.8 mJy beam$^{-1}$." (2.2)

### Inherited from earlier work

- Feathering procedure  
  > "in accordance with the CASA instruction (see also (cite: Tokuda16))" (3.1) [from (cite: Tokuda16)]
- N2H+/N2D+ column density estimation details  
  > "The details of the column density estimation are given in (cite: Caselli02)." (3.2) [from (cite: Caselli02)]
- Virial mass potential-energy correction coefficient  
  > "using the correction coefficient to use for the potential energy term described by (cite: Sipila11)" (3.2) [from (cite: Sipila11)]

### Not stated but needed to reproduce (our reading)

- Feathering parameters and single-dish calibration/scaling
- Pipeline vs manual calibration and calibrators
- Cell size, image size, masking, clean threshold
- Source coordinates
- Plummer fit form and fitted values details
- Dust-to-gas ratio and mean molecular weight values used
- Primary beam correction

## Analysis recipe

1. **Image ACA 7 m continuum and combine with IRAM**: CLEAN with natural weighting in CASA, feathered with IRAM 30 m 1.2 mm map  
  > "We used the feathering technique to combine the two different data sets in accordance with the CASA instruction" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared 7 m peak to IRAM, JCMT/SCUBA2 and N2D+ peaks  
  > "We found that the peak position of the 7 m array image is slightly shifted ($\sim$6$\ensuremath{''}$) from that of the IRAM image." (3.1)
2. **Derive H2 column density and mass**: Optically thin dust emission with uniform Td  
  > "assuming uniform dust temperature $T_{\rm d}$, and the optically thin emission" (3.1)
   - parameter: Td = 9 K; beta = 2; kappa231GHz = 0.005 and 0.01 cm2/g  
  > "we consider two values, $\kappa_\mathrm{231 GHz}$ = 0.005 and 0.01 cm$^2$ g$^{-1}$ to derive the column density" (3.1)
   - assumption: Isothermal 9 K; dust opacity uncertainty 0.005–0.02  
  > "We use 9 K as the dust temperature to derive the column density in this study." (3.1)
   - fitting: _not stated_
   - validation: Compared mass with Herschel-derived map  
  > "We compared our column density map with that derived from the *Herschel* observations to estimate this effect." (3.1)
3. **Radial column density profile and flat radius**: 2D Gaussian fit to IRAM column density, circular averaging with equivalent radius, Plummer-like fit with three parameters  
  > "we estimated the radius of the inner flattened region, $R_{\rm flat}$, using Plummer-like function fitting to the column density profile" (3.1)
   - parameter: Southern/eastern features masked within PA = 50–250 deg  
  > "corresponding to the fan-shaped area within PA = 50–250$\degree$ centered on the peak" (3.1)
   - fitting: Plummer-like: R_flat, <N_H2>, asymptotic power index  
  > "with three parameters; $R_{\rm flat}$, $\ensuremath{\langle N_{\rm H_2}\rangle} _{R_{\rm flat}}$, and the asymptotic power index" (3.1)
   - validation: _not stated_
4. **N2H+/N2D+ hyperfine fitting, deuterium fraction, nonthermal width, virial mass**: Hyperfine multi-Gaussian model with optical depth; nonthermal linewidth and virial parameter  
  > "We fit the observed spectra at the center of the core using the hyperfine spectrum model of multiple Gaussian components with the line optical depth effect" (3.2)
   - software: PySpecKit
   - parameter: Tk = 9 K  
  > "If we assume a kinematic temperature, $T_k$, of 9 K, the resultant $M_{\rm vir}$ is $\sim$0.6 $M_{\odot}$." (3.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.0.0: ACA data reduction and imaging  
  > "We performed the data reduction using the Common Astronomy Software Application (CASA) package (cite: McMullin07) version 5.0.0." (2.2)
- **PySpecKit** : Hyperfine fitting of N2H+ and N2D+ spectra  
  > "was performed with the Pyspeckit module of Python (cite: Ginsburg11)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core mass M_FWHM | 0.2–0.4 | not stated | Msun | 3 | to be $M_{\rm FWHM}$ $\sim$0.2–0.4 $M_{\odot}$ |
| Central density | ~(1–2)e6 | not stated | cm^-3 | 3 | are $\sim$(1–2) $\times$ 10$^{6}$ cm$^{-3}$, and $\sim$(4–7) $\times$ 10$^5$ cm$^{-3}$, respectively |
| Average density | ~(4–7)e5 | not stated | cm^-3 | 3 | are $\sim$(1–2) $\times$ 10$^{6}$ cm$^{-3}$, and $\sim$(4–7) $\times$ 10$^5$ cm$^{-3}$, respectively |
| N(N2D+)/N(N2H+) | ~30% | not stated | dimensionless | 4 | $N$(N$_{2}$D$^{+}$)/$N$(N$_{2}$H$^{+}$), $\sim$30% |
| Nonthermal width N2D+ | 0.29 | not stated | km/s | 4 | the $\Delta v_{\rm NT}$ of N$_{2}$D$^{+}$ is calculated to be 0.29 km s$^{-1}$ |
| Virial mass | ~0.6 | not stated | Msun | 4 | the resultant $M_{\rm vir}$ is $\sim$0.6 $M_{\odot}$ |

## Qualitative findings

- 7 m array marginally resolves core center into two peaks separated by ~4", below 1 sigma contrast; need higher resolution  
  > "the separation is $\sim$4$\ensuremath{''}$. We need higher angular resolution observations to confirm the substructures" (3.1)

## Claim tuples

- H: MC5-N is a centrally concentrated, evolved sub-solar core | E: IRAM+ACA 1.2 mm continuum profile and column densities | R: Mass 0.2–0.4 Msun, central density ~1e6 cm^-3 | F: Steep density profile; a very evolved low-mass core | **supported**
- H: The core is chemically evolved | E: N2H+ and N2D+ with Nobeyama 45 m | R: Deuterium fraction ~30% | F: Core is on verge of proto-brown dwarf/VLM star formation | **supported**
- H: Substructures exist at the core center | E: ACA 7 m imaging | R: Two marginal peaks ~4" apart, <1 sigma contrast | F: Possible only; needs higher resolution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Substructures could be artifacts of incomplete uv coverage of ACA  
  > "also caused by the observation effect having incomplete *uv* coverage of the ACA observations" (5 Summary & Future prospects)
- Caveat (inferred, ours): Mass depends on uncertain dust opacity and isothermal assumption
- Caveat (inferred, ours): Substructure significance below 1 sigma
- Caveat (inferred, ours): Single core, one ACA dataset

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and feathering details
- Missing: IRAM map data
- Missing: Nobeyama data processing (Miyamoto et al. in prep.)
- Data volume (inferred): ~10 GB for ACA 7 m project data
- Score (inferred): 3/5, ALMA project code and key assumptions given, but imaging and combination details missing; IRAM and Nobeyama data not public here.
- Rediscovery candidate: no, Recipe incomplete and requires non-ALMA single-dish data.

## Links

- Method: (cite: Tokuda16) (Feathering and ACA continuum analysis)
- Method: (cite: Caselli02) (Column density estimation from N2H+/N2D+)
- Companion: Miyamoto et al. in prep. (Nobeyama N2H+ survey details)
- Related: ACA survey of 16 dense cores (2016.1.00928.S)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 39,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
