# Far-infrared laboratory spectroscopy of aminoacetonitrile and first interstellar detection of its vibrationally excited transitions

`2020A&A...641A.160M` | Astronomy and Astrophysics 2020 | first author: Melosso, M. | arXiv: 2006.13753 | DOI: 10.1051/0004-6361/202038466

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can accurate vibrational energies and partition function of aminoacetonitrile from FIR laboratory spectroscopy enable detection of its vibrationally excited states toward Sgr B2(N1) in ReMoCA data?  
  > "We wanted to accurately determine the energies of the low-lying vibrational states of aminoacetonitrile, which are expected to be populated in Sgr B2(N1), the main hot core of Sgr B2(N)." (abstract)
- Target **Sgr B2(N1S)**: coordinates 17h47m19.870s, -28°22'19.48" (J2000)  
  > "Sgr B2(N1S) is located at ($\alpha, \delta$)$_{\rm J2000}$= ($17^{\rm h}47^{\rm m}19{s}870$, $-28^\circ22\ensuremath{^{\prime}} 19{\ensuremath{''}}48$), about 1$\ensuremath{^{\prime\!\prime}}$ to the south of Sgr B2(N1)." (4.1 Observations); "at a distance of 8.2 kpc from the Sun (cite: Reid19)" (Introduction); z/distance 8.2 kpc  
  > "Sgr B2(N1S) is located at ($\alpha, \delta$)$_{\rm J2000}$= ($17^{\rm h}47^{\rm m}19{s}870$, $-28^\circ22\ensuremath{^{\prime}} 19{\ensuremath{''}}48$), about 1$\ensuremath{^{\prime\!\prime}}$ to the south of Sgr B2(N1)." (4.1 Observations); "at a distance of 8.2 kpc from the Sun (cite: Reid19)" (Introduction); distance from Reid et al. 2019  
  > "Sgr B2(N1S) is located at ($\alpha, \delta$)$_{\rm J2000}$= ($17^{\rm h}47^{\rm m}19{s}870$, $-28^\circ22\ensuremath{^{\prime}} 19{\ensuremath{''}}48$), about 1$\ensuremath{^{\prime\!\prime}}$ to the south of Sgr B2(N1)." (4.1 Observations); "at a distance of 8.2 kpc from the Sun (cite: Reid19)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00074.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz, five tunings, 488 kHz resolution (1.7 to 1.3 km/s)  
  > "the observations covered the frequency range from 84.1 GHz to 114.4 GHz with five tunings, with a spectral resolution of 488 kHz (1.7 to 1.3 km s$^{-1}$)." (4.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.3" to ~0.8", median 0.6"  
  > "The angular resolution (HPBW) varied between $\sim$0.3$\ensuremath{^{\prime\!\prime}}$ and $\sim$0.8$\ensuremath{^{\prime\!\prime}}$, with a median value of 0.6$\ensuremath{^{\prime\!\prime}}$" (4.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.35 to 1.1 mJy/beam, median 0.8  
  > "The rms sensitivity ranged from 0.35 mJy beam$^{-1}$ to 1.1 mJy beam$^{-1}$, with a median value of 0.8 mJy beam$^{-1}$." (4.1 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: aminoacetonitrile (NH2CH2CN) rotational lines in v=0, v11=1, v18=1 (also searched v17=1, v11=2) (90-112 GHz (Table))
- Other facility **SOLEIL AILES beamline**: Synchrotron FIR absorption spectra of aminoacetonitrile, 100-500 cm-1  
  > "The FIR spectrum of aminoacetonitrile was recorded between 100 and 500  cm$^{-1}$ on the AILES[^2] beamline of the SOLEIL synchrotron facility." (2 Experimental details)
- External data: Pure rotational transition frequencies of ground and excited states included in the fit  
  > "Pure rotational transitions of the ground state (cite: macdonald1972microwave; pickett1973microwave; brown1977quadrupole; bogey1990millemeter; motoki2013submillimeter) and excited states of aminoacetonitrile (cite: degli2017millimeter) were also included in the analysis." (3.3 Results from the analysis) [from macdonald1972; pickett1973; brown1977; bogey1990; motoki2013; degli2017millimeter]
- External data: Dipole moments mu_a=2.577(7) D, mu_b=0.575(1) D  
  > "the permanent dipole moment values $\mu_a=2.577(7)$ D and $\mu_b=0.575(1)$ D were taken from (cite: pickett1973microwave)" (3.4 Partition function) [from (cite: pickett1973microwave)]
- External data: Methanol column density 2.0e19 cm-2 for Sgr B2(N1S)  
  > "using an observational methanol column density of $2.0 \times 10^{19}$ cm$^{-2}$ for Sgr B2(N1S) (cite: Motiyenko20)" (5.3 Formation of aminoacetonitrile) [from (cite: Motiyenko20)]

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
- continuum subtraction: continuum and line separated in image plane with an updated algorithm over the field of view  
  > "We made some progress with our algorithm that performs this splitting across the whole field of view and we use the newly obtained spectra for the present analysis." (4.1 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observational setup and data reduction of ReMoCA  
  > "Details about the observational setup and data reduction of this survey were reported in (cite: Belloche19)." (4.1 Observations) [from (cite: Belloche19)]
- Offset position Sgr B2(N1S) and 2" emission size assumption  
  > "The model assumes a diameter (FWHM) of 2$\ensuremath{^{\prime\!\prime}}$ for the emission of aminoacetonitrile, as was done for other species reported by (cite: Belloche19)" (4.2 Detection) [from (cite: Belloche19)]
- Population diagram method  
  > "we constructed a population diagram for aminoacetonitrile following the same method as (cite: Belloche16)." (4.2 Detection) [from (cite: Belloche16)]

### Not stated but needed to reproduce (our reading)

- Updated continuum/line separation algorithm details and resulting spectra (not public in the paper)
- Calibration and imaging parameters of ReMoCA (in Belloche et al. 2019)
- Which lines were used in the population diagram and optical depth/contamination correction details
- How the model of other identified species was constructed
- Weeds fitting procedure (manual vs automatic) and goodness criteria

## Analysis recipe

1. **Laboratory spectral fit and partition function**: Weighted least-squares fit of ~11000 ro-vibrational and >2000 rotational lines with Watson S-reduced Hamiltonian plus Coriolis term; partition function from SPCAT  
  > "The newly observed ro-vibrational transitions were analyzed in a weighted least-squares procedure performed with the `SPFIT` subprogram of the `CALPGM` suite (cite: pickett1991)." (3.3 Results from the analysis)
   - software: SPFIT, SPCAT, LWW
   - parameter: Uncertainties 1e-4 cm-1 for new data; 1.5e-4 cm-1 for v11 band  
  > "A conservative uncertainty of $1.5\times10^{-4}$  cm$^{-1}$ was given to the transition frequencies of the weaker $\nu_{11}$ band" (3.3 Results from the analysis)
   - assumption: Dipole moments unchanged upon vibrational excitation  
  > "assumed to not change upon the vibrational states." (3.4 Partition function)
   - fitting: Weighted least squares, dimensionless sigma 0.99  
  > "The overall standard deviation of the fit ($\sigma$) is 0.99" (3.3 Results from the analysis)
   - validation: _not stated_
2. **LTE modelling of ReMoCA spectrum at Sgr B2(N1S)**: Weeds LTE synthetic spectrum with 5 parameters per species, combining all identified molecules; v=0 fit first, same parameters applied to vibrational states  
  > "We derived a best-fit synthetic spectrum of each molecule separately, and then added the contributions of all identified molecules together." (4.1 Observations)
   - software: Weeds
   - parameter: size 2", T=200 K, N=1.1e17 cm-2, dV=5.0 km/s, Voff=0, Vsys=62 km/s  
  > "| $\varv=0$ | d | 18 | 2.0 | 200 | 1.1 (17) | 1.00 | 5.0 | 0.0 |" (Table 3)
   - assumption: LTE  
  > "under the assumption of local thermodynamic equilibrium (LTE), which is appropriate given the high densities" (4.1 Observations)
   - fitting: _not stated_
   - validation: Gaussian size fit of six least-contaminated lines gave ~1.9"  
  > "yields a mean size of $\sim$1.9$\ensuremath{^{\prime\!\prime}}$ with an rms dispersion of $\sim$0.15$\ensuremath{^{\prime\!\prime}}$" (4.2 Detection)
3. **Population diagram**: Population diagram after correction for optical depth and contamination  
  > "The fit to the population diagram of Fig. 5b yields a rotational temperature of $245 \pm 47$ K." (4.2 Detection)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SPFIT/SPCAT (CALPGM)** : Least-squares fit and partition function  
  > "have been input in the `SPCAT` subroutine (cite: pickett1991) to compute the ro-vibrational partition function of aminoacetonitrile analytically." (Partition function)
- **Loomis-Wood for Windows (LWW)** : Assignment of ro-vibrational transitions  
  > "The assignment procedure was performed with the Loomis-Wood for Windows (LWW) program package" (3.2 Assignment procedure)
- **Weeds** : LTE modelling of ALMA spectrum  
  > "We modeled the spectrum of Sgr B2(N1S) with the software Weeds (cite: Maret11)" (4.1 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Vibrational energy v11=1 | 210.575842 | 0.000005 | cm-1 | 1 | / $E$         /  cm$^{-1}$ / 0.0           / 210.575842(5)  / 244.891525(3)  / 368.104657(3)  / |
| Vibrational energy v18=1 | 244.891525 | 0.000003 | cm-1 | 1 | / $E$         /  cm$^{-1}$ / 0.0           / 210.575842(5)  / 244.891525(3)  / 368.104657(3)  / |
| Vibrational energy v17=1 | 368.104657 | 0.000003 | cm-1 | 1 | / $E$         /  cm$^{-1}$ / 0.0           / 210.575842(5)  / 244.891525(3)  / 368.104657(3)  / |
| Column density of aminoacetonitrile at Sgr B2(N1S) | 1.1e17 | not stated | cm-2 | 2 | The column density of aminoacetonitrile derived from our LTE modelling of the ReMoCA spectrum toward Sgr B2(N1S), $1.1 \times 10^{17}$ cm$^{-2}$ |
| Rotational temperature from population diagram | 245 | 47 | K | 3 | yields a rotational temperature of $245 \pm 47$ K |
| Aminoacetonitrile/methanol ratio | 5.5e-3 | not stated | dimensionless | 2 | an observational ratio of $5.5 \times 10^{-3}$ is found |

## Qualitative findings

- Four v11=1 lines and one v18=1 line detected, consistent with LTE; v17=1 and v11=2 contribute but are not securely identified  
  > "No transitions of $\varv_{17}=1$ and $\varv_{11}=2$ are unambiguously detected, but some of them contribute significantly to the signal detected with ALMA" (4.2 Detection)

## Claim tuples

- H: Vibrationally excited aminoacetonitrile is detectable toward Sgr B2(N1S) with new spectroscopy | E: LTE modelling of ReMoCA spectrum with new catalogs | R: 4 v11=1 and 1 v18=1 lines consistent with model at 200 K, N=1.1e17 | F: v11=1 and v18=1 detected | **supported**
- H: Precise vibrational energies can be determined from FIR spectrum | E: Synchrotron FT-FIR spectrum and combined fit | R: Energies with relative uncertainty down to 2e-8 | F: Accurate predictions up to THz | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Rotational temperature uncertain due to continuum and contamination; spectral baseline quality limited  
  > "These are the reasons why the fitted rotational temperature is uncertain, and its (purely) statistical uncertainty may be underestimated." (4.2 Detection)
- Caveat (inferred, ours): Only five vibrationally excited lines detected; the detection rests on LTE model without formal significance
- Caveat (inferred, ours): Temperature fixed at 200 K versus 245 K from population diagram

## Reproducibility

- Data public (paper): Interferometric data in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Updated continuum/line separated spectra and algorithm
- Missing: Full model of other species for blending
- Data volume (inferred): hundreds of GB (five-tuning ALMA Band 3 survey, if reprocessed)
- Score (inferred): 3/5, Lab part reproducible in principle; ALMA part relies on unreleased processing and companion paper.
- Rediscovery candidate: no, Key spectra depend on an unpublished updated line/continuum separation and a large companion model.

## Links

- Method: Belloche et al. 2019 (cite: Belloche19) (ReMoCA observations and reduction)
- Method: Degli Esposti et al. 2017 (prior rotational data and Coriolis analysis)
- Related: ReMoCA
- Related: EMoCA

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 68,
  "stated": 30,
  "rate": 0.441
 },
 "evidence_ok": true
}
```
