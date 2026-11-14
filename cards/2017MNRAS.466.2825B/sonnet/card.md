# ALMA observations of atomic carbon in z ∼ 4 dusty star-forming galaxies

`2017MNRAS.466.2825B` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Bothwell, M. S. | arXiv: 1612.04380 | DOI: 10.1093/mnras/stw3270

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the molecular gas masses and ISM physical conditions (density, UV field, temperature) of z~4 SPT dusty star-forming galaxies, as traced by [CI](1-0) and PDR modelling?  
  > "Using the  line as a tracer of the molecular ISM, we find a mean molecular gas mass for SPT-DSFGs of $6.6 \times 10^{10}$ M$_{\ensuremath{\odot}}$." (abstract)
- Target **13 SPT DSFGs (SPT0113-46, SPT0125-50, SPT0300-46, SPT0345-47, SPT0418-47, SPT0441-46, SPT0459-59, SPT0529-54, SPT0532-50, SPT2103-60, SPT2132-58, SPT2146-55, SPT2147-50)**: coordinates e.g. SPT0113-46 01:13:09.82 -46:17:52.2 (J2000); others in Table 1  
  > "SPT0113-46 | 01:13:09.82 | $-$46:17:52.2 | 4.2328" (Table 1); "Thirteen DSFGs were found to lie at redshifts $3.24 < z < 4.85$, shifting the ($1-0$) into ALMA Band 3." (1 Introduction); z/distance 3.24 < z < 4.85 (e.g. SPT0113-46 z=4.2328)  
  > "SPT0113-46 | 01:13:09.82 | $-$46:17:52.2 | 4.2328" (Table 1); "Thirteen DSFGs were found to lie at redshifts $3.24 < z < 4.85$, shifting the ($1-0$) into ALMA Band 3." (1 Introduction); distance from ALMA Cycle 0 blind redshift search (Weiss et al. 2013)  
  > "SPT0113-46 | 01:13:09.82 | $-$46:17:52.2 | 4.2328" (Table 1); "Thirteen DSFGs were found to lie at redshifts $3.24 < z < 4.85$, shifting the ($1-0$) into ALMA Band 3." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00957.S, 2011.0.00958.S, 2012.1.00844.S, 2012.1.00994.S
- bands: Band 3 (84-116 GHz) full-band scan  
  > "26 SPT DSFGs were observed across the entirety of ALMA Band 3 ($= 84 - 116$ GHz) as part of the Cycle 0 ‘early compact array’ setup." (2 Sample, Observations and Reduction)
- frequencies and spectral setup: 5 tunings of 7.5 GHz each covering the band  
  > "Each observation consisted of 5 distinct 7.5 GHz tunings, spaced to cover the band." (2 Sample, Observations and Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms channel noise 2.1 mJy and 2.6 mJy per 50 km/s channel (SPT0300-46, SPT2103-60); 2.4 mJy for SPT0345-47  
  > "which we measure to be 2.1 mJy and 2.6 mJy per 50 km/s channel respectively" (2 Sample, Observations and Reduction)
- time on source: 120 s per tuning per source  
  > "Each source was observed for 120s in each tuning configuration." (2 Sample, Observations and Reduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CI] 3P1-3P0 (1-0) (492.161 GHz)
- Other facility **APEX FLASH and Herschel SPIRE FTS**: [CII] line observations  
  > "The  observations were obtained from the APEX First Light APEX Submillimetre Heterodyne receiver (FLASH), and the Herschel ‘SPIRE’ FTS spectrometer." (2.1 Ancillary data)
- Other facility **ATCA**: low-J CO(2-1) observations  
  > "The low-$J$ CO observations were taken by the Australia Telescope Compact Array (ATCA)" (2.1 Ancillary data)
- External data: Lens models and magnifications from ALMA 870um  
  > "Lensing magnifications are derived from visibility-based lens models fit to ALMA 870$\mu$m observations (Spilker et al. 2016)." (Table 1) [from Spilker et al. 2016 (cite: spilker16)]
- External data: [CII] data  
  > "data are taken from Gullberg et al. (2015)." (Table 1) [from Gullberg et al. (2015) (cite: gullberg15)]
- External data: CO(2-1) data  
  > "CO$(2-1)$ data are taken from Aravena et al. (2016)" (Table 1) [from Aravena et al. (2016) (cite: aravena16)]
- External data: Comparison local galaxy sample from Herschel SPIRE FTS  
  > "we use a sample observed with the *Herschel*/SPIRE Fourier Transform Spectrometer (FTS), presented by (cite: kamenetzky16)." (3.3) [from (cite: kamenetzky16)]
- Simulation/model as data: 3d-pdr grid of uniform-density 1D models, 2<=log nH<=7, -0.2<=log G<=5.8  
  > "The parameter space covers $2\le \log(n_{\rm H}/{\rm cm}^{-3})\le 7$ in density and $-0.2\le\log(G/G_{\circ})\le 5.8$ in UV field" (4.1 Model description)

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observing programme details and data reduction  
  > "Further details of the observing programme and data reduction can be found in (cite: weiss13)." (2 Sample, Observations and Reduction) [from (cite: weiss13)]
- Tex = 30 K for carbon mass  
  > "Instead, we adopt a ‘typical’ value of 30K (Weiß et al. 2013)" (3.4) [from Weiß et al. 2013]
- CO(2-1)/CO(1-0) brightness temperature ratio 0.8  
  > "We assume a CO$(2-1)$/CO$(1-0)$ brightness temperature ratio of r$_{21/10} = 0.8$ (Aravena et al., 2016)." (3.5) [from Aravena et al., 2016]
- Gas radius of 2 kpc  
  > "Following the source size analysis of the SPT-DSFGs sample presented by (cite: spilker16), we take a typical radius of 2kpc." (3.6) [from (cite: spilker16)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging steps for the [CI] cubes (deferred to Weiss et al. 2013)
- Line flux extraction method (aperture, line fitting) and FWHM fitting
- Synthesized beam and weighting
- Continuum subtraction
- Method for deriving PDR probability distributions and uncertainties from line ratios
- Treatment of CO(5-4) to CO(4-3) conversion details

## Analysis recipe

1. **Measure [CI](1-0) line fluxes and upper limit**: Extract spectra at source positions; 3 sigma upper limit for non-detection SPT0345-47 using mean linewidth  
  > "$\Delta V_{\rm CO}$ is the mean linewidth of the detected sample (=410 km/s), and $dv$ is the bin size in km s$^{-1}$ (=50 km/s)." (2 Sample, Observations and Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute line luminosities and correct for lensing**: Solomon & Vanden Bout formulae; divide by magnification from lens models  
  > "Luminosities in solar units (L$_{\ensuremath{\odot}}$), which represent the true energy output carried by the emission line (used, for example, for calculating cooling contributions) are calculated following (cite: solomon05):" (Line luminosities and ratios)
   - assumption: Lens models from dust emission apply to [CI] gas  
  > "we make the assumption that these lens models also apply to the cold molecular gas traced by ." (3.2)
   - fitting: _not stated_
   - validation: Discussion of differential lensing  
  > "Overall, it is likely that differential lensing does not significantly affect the ability of  to trace molecular gas." (Correction for magnification due to gravitational lensing)
3. **Derive atomic carbon and H2 masses**: Weiss et al. 2005 carbon mass formula; Papadopoulos & Greve 2004 H2 mass formula  
  > "(cite: papadopoulos04b) give an expression for calculating the total H$_2$ mass from the luminosity of the ($1-0$) line" (3.5)
   - parameter: Tex = 30 K; X_CI = 3e-5; A10 = 7.93e-8 s^-1; Q10 = 0.6  
  > "we adopt a literature-standard /H$_2$ abundance ratio of $3 \times 10^{-5}$, and the Einstein $A$ coefficient $A_{10} = 7.93 \times 10^{-8} s^{-1}$." (3.5)
   - fitting: _not stated_
   - validation: Compared [CI] and low-J CO linewidths (KS test P=0.88)  
  > "A Kolmogorov-Smirnov test comparing the CO and  linewidths returns $P=0.88$" (3.5)
4. **Derive alpha_CO implied by [CI] gas masses**: Ratio of M(H2)[CI] to L'CO(1-0), with CO(1-0) from CO(2-1) or higher-J via SLED  
  > "The units of $L'_{\rm CO}$ result in the ratio M(H$_2)^{\rm CI}$/$L'_{\rm CO(1-0)}$ being equal to the value of $\alpha_{\rm CO}$ required to force agreement." (3.5.1)
   - parameter: r21/10 = 0.8  
  > "We assume a CO$(2-1)$/CO$(1-0)$ brightness temperature ratio of r$_{21/10} = 0.8$" (3.5.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **PDR modelling of density, UV field, temperature**: Grid of 3d-pdr 1D models; probability distributions from ratios [CII]/[CI], CO(4-3)/CO(2-1), [CI]/CO(4-3)  
  > "we find probability density distributions for the mean density and the mean UV field strength for each galaxy, based on our grid of one-dimensional PDR models." (4.2)
   - software: 3d-pdr
   - parameter: zeta_CR = 1e-15 s^-1; integrate to Av=7; vturb = 1.5 km/s  
  > "The cosmic-ray ionisation rate is taken to be $\zeta_{\rm CR}=10^{-15}\,{\rm s}^{-1}$" (4.1)
   - assumption: Solar undepleted elemental abundances; UMIST 2012 subset network  
  > "We use a subset of the UMIST 2012 network (cite: McEl13) of 33 species (including e$^{-}$ and 330 reactions)" (4.1)
   - fitting: Peak of probability distribution over the grid  
  > "take $\log n$ and $\log G$ to be the peak of the probability distribution function defined by these line ratio constraints." (Comparing to other PDR models)
   - validation: Compared with Kaufman et al. 1999 models; tested zeta_CR = 5e-15  
  > "Re-calculating our values of $n,G$ with CR fluxes $\zeta_{\rm CR}=5 \times 10^{-15}\,{\rm s}^{-1}$ ($500 \times \zeta_{\rm CR, MW}$), we find that the derived values of $n,G$ typically increase by $\sim 0.5$ dex" (4.3)

## Software

- **3d-pdr** : PDR modelling of line ratios  
  > "We model our line intensities and line ratios using the 3d-pdr code (cite: bisbas12)" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean H2 mass from [CI] (X_CI=3e-5) | 6.6e10 | 2.1e10 | Msun | 3 | we measure a mean (corrected for gravitational magnification) M(H$_2)^{\rm CI} = (6.6 \pm 2.1) \times 10^{10}$ M$_{\ensuremath{\odot}}$ |
| Mean [CI] mass | 1.2e7 | 0.3e7 | Msun | 3 | $(1.2 \pm 0.3) \times 10^7$ M$_{\ensuremath{\odot}}$ |
| Mean H2 mass from CO (alpha=0.8) | 2.8e10 | 1.7e10 | Msun | 4 | $<$M(H$_2)^{\rm CO, \alpha=0.8} > = (2.8 \pm 1.7) \times 10^{10}$ M$_{\ensuremath{\odot}}$ |
| Mean implied alpha_CO | 2.0 | 1.0 | Msun (K km/s pc^2)^-1 | 4 | we find a mean CO-to-H$_2$ conversion factor of $\alpha_{\rm CO} = 2.0 \pm 1.0$ |
| Mean L[CI]/LFIR | 7.7e-6 | 2.4e-6 | dimensionless | 2 | $(7.7 \pm 2.4) \times 10^{-6}$ |
| Mean log n (3d-pdr) | 5.2 | 0.6 | log cm^-3 | 5 | $< \log n > = 5.2 \pm 0.6$ cm$^{-3}$, and $< \log G > = 2.9 \pm 1.5$ |
| Mean log G | 2.9 | 1.5 | log Habing | 5 | $< \log G > = 2.9 \pm 1.5$ |
| Mean gas temperature | 25 | not stated | K | 5 | We find a mean gas temperature for our sources of 25 K. |
| Mean log n with Kaufman99 models | 4.4 | 0.4 | log cm^-3 | 5 | $< \log n > = 4.4 \pm 0.4$ cm$^{3}$ |
| Mean r_CO43/CI | 2.6 | 0.9 | dimensionless | 0 | $<$$r_{\rm CO43/CI}$ $>$ = $2.6 \pm 0.9$ |

## Qualitative findings

- SPT-DSFGs have dense gas with strong UV fields, denser than local ULIRGs and than found with Kaufman99 models.  
  > "We find that the ISM within our DSFGs is characterised by dense gas permeated by strong UV fields." (abstract)

## Claim tuples

- H: [CI]-based gas masses agree with CO- and dust-based masses under standard assumptions | E: Compared M(H2) from [CI] (X=3e-5) with CO (alpha=0.8) | R: [CI] masses 6.6e10 vs CO 2.8e10 Msun | F: Requires alpha_CO~2-2.4 and GDR~200, or X_CI~7e-5 | **supported**
- H: Modern PDR models give different ISM conditions than older ones | E: 3d-pdr vs Kaufman99 on same ratios | R: Density 5.2 vs 4.4 dex | F: Past works likely underestimated densities | **supported**
- H: SPT-DSFGs differ in density from unlensed DSFGs | E: 2D KS test on L[CI]/LFIR vs L[CI]/LCO(4-3) | R: p=0.061 | F: Tentative difference only | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot rule out AGN; Tex assumed; X_CI assumed; differential lensing possible  
  > "Due to a lack of X-ray data for our sample we cannot rule out a possible AGN component in any of our 13 DSFGs." (2 Sample, Observations and Reduction)
- Caveat (inferred, ours): Results strongly dependent on assumed X_CI, Tex, Q10 and zeta_CR
- Caveat (inferred, ours): No reduction details for [CI] cubes
- Caveat (inferred, ours): PDR uses single-component clouds with lensed multi-aperture line ratios
- Caveat (inferred, ours): Small sample, p=0.061

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduction/imaging parameters
- Missing: Line fitting procedure
- Missing: 3d-pdr grid details and fitting code
- Data volume (inferred): small (~10-50 GB, Cycle 0 short observations)
- Score (inferred): 3/5, Final tables and formulae given and archive data exist, but reduction and PDR fitting details are missing.
- Rediscovery candidate: no, Reduction recipe not described and PDR code fitting details lacking.

## Links

- Method: Weiß et al. 2013 (cite: weiss13) (Observing program and data reduction)
- Method: Bisbas et al. 2012 (cite: bisbas12) (3d-pdr code)
- Companion: Spilker et al. 2016 (cite: spilker16) (Lens models)
- Companion: Gullberg et al. 2015 (cite: gullberg15) ([CII] data)
- Companion: Aravena et al. 2016 (cite: aravena16) (CO(2-1) data)
- Related: South Pole Telescope survey

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 36,
  "rate": 0.468
 },
 "evidence_ok": true
}
```
