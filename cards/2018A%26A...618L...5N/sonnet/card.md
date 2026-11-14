# Detection of a high-mass prestellar core candidate in W43-MM1

`2018A&A...618L...5N` | Astronomy and Astrophysics 2018 | first author: Nony, T. | arXiv: 1810.01404 | DOI: 10.1051/0004-6361/201833863

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do high-mass analogs of low-mass prestellar cores exist in W43-MM1, in the least clustered part of the cloud?  
  > "We search for high-mass analogs of low-mass prestellar cores in W43-MM1." (abstract)
- Target **W43-MM1 (cores #3 and #6)**: coordinates Core #3: 18:47:46.37 -1:54:33.41; core #6: 18:47:46.16 -1:54:33.30 (J2000)  
  > "W43, located at 5.5 kpc from the Sun (cite: zhang14), contains two of the largest groups of molecular clouds in the first Galactic quadrant" (Introduction); "| #6 | 18:47:46.16 | -1:54:33.30 | 1300 |" (Table 2); z/distance 5.5 kpc  
  > "W43, located at 5.5 kpc from the Sun (cite: zhang14), contains two of the largest groups of molecular clouds in the first Galactic quadrant" (Introduction); "| #6 | 18:47:46.16 | -1:54:33.30 | 1300 |" (Table 2); distance from zhang14 (cite)  
  > "W43, located at 5.5 kpc from the Sun (cite: zhang14), contains two of the largest groups of molecular clouds in the first Galactic quadrant" (Introduction); "| #6 | 18:47:46.16 | -1:54:33.30 | 1300 |" (Table 2)

## Data provenance

- ALMA projects: 2013.1.01365.S
- bands: 1.3 mm  
  > "We conducted a 1.3 mm ALMA mosaic of the complete W43-MM1 cloud" (abstract)
- frequencies and spectral setup: Four spws: SiO 217.033, CO 230.462, 13CS 231.144 GHz, continuum 233.4 GHz  
  > "| Continuum      | 233.4           | 1875      | 0.43                 | 1.3                  | 1.9    |   |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m and 7 m (ACA)  
  > "with ALMA 12 m and 7 m (ACA) arrays and baselines ranging from 7.6 m to 1045 m" (2 Observations and data reduction)
- configurations: _not stated_
- baselines: 7.6 m to 1045 m  
  > "baselines ranging from 7.6 m to 1045 m" (2 Observations and data reduction)
- angular resolution: 0.37'' x 0.53'' (~2400 au) for 12 m continuum  
  > "synthesized beam of 0.37$\ensuremath{''}$ $\times$ 0.53$\ensuremath{''}$, $\sim$2400 au at 5.5 kpc" (2 Observations and data reduction)
- max recoverable scale: 12'' (12 m), 21'' (ACA)  
  > "the maximum detectable scale is of 12$\ensuremath{''}$ (21$\ensuremath{''}$ with ACA)" (2 Observations and data reduction)
- sensitivity: 0.13 mJy/beam on the 1.9 GHz averaged map  
  > "the best sensitivity (0.13 mJy beam$^{-1\,}$ on the 1.9 GHz averaged map)" (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: July 2014 to June 2015 (Cycle 2)  
  > "Observations were carried out in Cycle 2 between July 2014 and June 2015" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 13CS J=5-4 (not stated)
- Line: CO 2-1 (not stated)
- Line: SiO 5-4 (not stated)
- External data: Catalog of 131 getsources sources in W43-MM1; fluxes corrected for free-free and line contamination  
  > "The final getsources catalogs of the W43-MM1 cloud contains 131 reliable sources presented in (cite: motte18b)." (3.1) [from (cite: motte18b)]
- External data: Dust temperatures from PPMAP applied to all existing continuum data  
  > "The mean dust temperature of cores was estimated by applying the Bayesian PPMAP procedure (cite: marsh2015) to all existing continuum data of W43-MM1 (cite: motte18b)." (3.1) [from (cite: marsh2015); (cite: motte18b)]
- External data: Total luminosity of W43-MM1 ~2e4 Lsun  
  > "from the total luminosity of W43-MM1, $\sim\,2 \times 10^4\, \ensuremath{L_{\odot}}$ (cite: motte03)" (4) [from (cite: motte03)]

## Processing

### Calibration

- pipeline or manual: Manual and self-calibration scripts  
  > "Data were reduced in CASA 4.3.1, applying manual and self-calibration scripts." (2 Observations and data reduction)
- casa version: CASA 4.3.1  
  > "Data were reduced in CASA 4.3.1" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: applied (details not given)  
  > "applying manual and self-calibration scripts" (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: CLEAN with multiscale option  
  > "We then used the CLEAN algorithm with a robust weight of 0.5 and the multiscale option" (2 Observations and data reduction)
- weighting robust: robust = 0.5  
  > "CLEAN algorithm with a robust weight of 0.5" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m + 7 m merged data for line studies; 12 m only for core extraction  
  > "For the molecular line studies we used the merged (12 m + 7 m) data" (2 Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core catalog, flux corrections, line contamination and luminosities taken from the W43-MM1 paper  
  > "Fluxes given in Table [\[cores\]](#cores) are also corrected for contamination by free-free and line emission (cite: motte18b)." (3.1) [from (cite: motte18b)]

### Not stated but needed to reproduce (our reading)

- Multiscale scales, cell size, image size, masks and clean thresholds
- Line-free channels and the continuum subtraction method
- Self-calibration solution intervals and flux calibrators
- Dust temperature PPMAP details per core
- How outflow velocity ranges for integration were chosen
- Details of the filament/outflow subtraction from the 13CS spectra

## Analysis recipe

1. **Extract cores and measure fluxes**: getsources on the 12 m 1.3 mm continuum map  
  > "Compact sources were extracted using getsources (v1.140127), a multiscale, multiwavelength source-extraction algorithm" (3.1)
   - software: getsources
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive core masses**: Opacity-corrected mass formula using peak and integrated fluxes and Planck function  
  > "Equation [\[Mcore\]](#Mcore) thus includes a correction for dust opacity, which increases the mass of cores #3 and #6 by 20%." (3.1)
   - assumption: kappa_1.3mm = 0.01 cm2/g (gas+dust); d = 5.5 kpc; T_dust from PPMAP  
  > "We adopted $\kappa_{\rm 1.3 mm} = {\rm 0.01~ cm^{2}g^{-1}}$ as being the most appropriate" (3.1)
   - fitting: _not stated_
   - validation: Absolute mass uncertainty about a factor of two  
  > "The absolute uncertainties on core masses is estimated to be about a factor of two." (3.1)
3. **Measure turbulence and virial parameter**: Gaussian fit to 13CS(5-4) spectra after subtracting filament and outflow contribution; line FWHM is the average of fits before and after subtraction; virial mass from sigma_NT  
  > "The line FWHM given in Table [\[cores\]](#cores) corresponds to the average of the fits before and after this subtraction." (3.2)
   - assumption: density index n=2 for both cores, n=0 for core #6  
  > "We assume a density index of $n=2$ (case of a centrally concentrated protostar) for both cores and $n=0$" (3.2)
   - fitting: Gaussian line fit  
  > "We thus subtracted, from each core spectrum, the contribution of the core parental filament and outflow before fitting a Gaussian (see Fig. [5](#cs-spec))." (Result and analysis, Virial mass and gravitational boundedness)
   - validation: alpha_vir well below unity even with factor-of-two mass uncertainty  
  > "even with a factor of two uncertainty on masses, cores #3 and #6 are gravitationally bound" (3.2)
4. **Search for outflows**: Integrate high-velocity wings of CO(2-1) and SiO(5-4) around systemic velocity  
  > "We integrated the high-velocity line wings of CO(2-1) and SiO(5-4) around the systemic velocities" (3.3)
   - fitting: _not stated_
   - validation: CO and SiO lobes compared  
  > "present an excellent agreement between the CO(2-1) and SiO(5-4) line tracers" (3.3)
5. **Assess molecular complexity (hot core)**: Inspect the 1.9 GHz continuum band spectra and compare flux in a 65 MHz line-free band with the full-band flux  
  > "comparing the flux integrated over a line-free composite band of 65 MHz with the flux integrated over the 1.9 GHz full band" (3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: Data reduction and CLEAN imaging  
  > "Data were reduced in CASA 4.3.1" (2 Observations and data reduction)
- **getsources** v1.140127: Core extraction  
  > "Compact sources were extracted using getsources (v1.140127)" (3.1)
- **PPMAP** : Dust temperature estimation (Bayesian)  
  > "applying the Bayesian PPMAP procedure (cite: marsh2015)" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass core #3 | 59 | 4 (statistical); factor of 2 absolute | Msun | 2 | $59 \pm 4$ |
| Mass core #6 | 56 | 9 (statistical); factor of 2 absolute | Msun | 2 | $56 \pm 9$ |
| 13CS FWHM core #3 | 4.0 | 0.3 | km/s | 3 | $4.0 \pm 0.3$ |
| 13CS FWHM core #6 | 3.3 | 0.2 | km/s | 3 | $3.3 \pm 0.2$ |
| Virial parameter | 0.2-0.3 | not stated | dimensionless | 3 | $\alpha_{\rm vir}\,=\,M_{\rm vir}/M_{\rm core}=0.2-0.3$ |
| Dust temperature core #6 | 23 | 2 | K | 2 | $23 \pm 2$ |
| Line contamination core #3 | >13% | not stated | % | 5 | is $>\!13\%$ for core #3 and $\sim\!0\%$ toward core #6 |

## Qualitative findings

- Core #6 shows no outflow and no hot-core line forest, making it a high-mass prestellar core candidate  
  > "core #6 is, for now, an excellent high-mass prestellar core candidate" (4)

## Claim tuples

- H: Are cores #3 and #6 gravitationally bound? | E: Virial analysis with 13CS line widths and continuum masses | R: alpha_vir = 0.2-0.3 | F: Both cores are bound despite turbulence | **supported**
- H: Is core #6 prestellar? | E: Search for CO/SiO outflows and hot-core lines | R: No outflow, almost no line forest | F: Core #6 is a high-mass prestellar core candidate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Core #6 could be a very young protostellar core with a very low-mass embryo (IR-quiet phase)  
  > "the second interpretation would put core #6 in the IR-quiet protostellar core phase (step 4)" (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher sensitivity and resolution are needed to confirm the lack of outflow  
  > "more sensitive and higher resolution observations (see Table [1](#cont)) will be needed to confirm this finding" (3.3)
- Caveat (inferred, ours): Only two cores, with a factor-of-two mass uncertainty
- Caveat (inferred, ours): Prestellar nature is inferred from non-detections at limited sensitivity
- Caveat (inferred, ours): The virial parameter depends on the assumed density index

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Details of the spectral baseline and outflow subtraction
- Missing: getsources configuration
- Missing: PPMAP temperatures come from another paper
- Data volume (inferred): ~100s GB (large 12 m + ACA mosaic)
- Score (inferred): 3/5, Public data and simple formulas, but many processing details are deferred to Motte et al. 2018b or not given.
- Rediscovery candidate: no, Key inputs (catalog, temperatures) come from another paper and imaging details are missing.

## Links

- Method: Men'shchikov et al. 2012 (cite: men2012multi) (getsources algorithm)
- Method: Marsh et al. 2015 (cite: marsh2015) (PPMAP)
- Companion: Motte et al. 2018b (cite: motte18b) (Full W43-MM1 core catalog and ALMA data analysis)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 39,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
