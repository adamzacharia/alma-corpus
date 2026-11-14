# A Higher Efficiency of Converting Gas to Stars Pushes Galaxies at z ∼ 1.6 Well Above the Star-forming Main Sequence

`2015ApJ...812L..23S` | The Astrophysical Journal Letters 2015 | first author: Silverman, J. D. | arXiv: 1505.04977 | DOI: 10.1088/2041-8205/812/2/L23

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do high-redshift (z~1.6) starbursts, selected as outliers above the star-forming main sequence, convert gas to stars with higher efficiency than main-sequence galaxies?  
  > "Our primary interest is to determine whether high-redshift starbursts convert gas into stars with a higher efficiency than MS galaxies at these epochs." (CO-to-IR ratio)
- Target **Seven Herschel-selected main-sequence outliers in COSMOS (PACS-299, 325, 819, 830, 867, 282, 164)**: coordinates Table 1 lists RA/Dec in COSMOS, e.g. PACS-299 09:59:41.31 +02:14:42.91  
  > "| 299 | 09:59:41.31 | 02:14:42.91 | 1.6483 | 1.6467 |" (Table 1); "Six targets, labeled in Figure [1](#fig:sample), are extracted from this sample with an additional galaxy at a slightly higher redshift (PACS-282; $z=2.19$)" (Introduction); z/distance z = 1.44-2.19 (z_CO)  
  > "| 299 | 09:59:41.31 | 02:14:42.91 | 1.6483 | 1.6467 |" (Table 1); "Six targets, labeled in Figure [1](#fig:sample), are extracted from this sample with an additional galaxy at a slightly higher redshift (PACS-282; $z=2.19$)" (Introduction); distance from Halpha redshifts from FMOS-COSMOS; zCOSMOS-Deep for PACS-282; CO centroid redshifts  
  > "| 299 | 09:59:41.31 | 02:14:42.91 | 1.6483 | 1.6467 |" (Table 1); "Six targets, labeled in Figure [1](#fig:sample), are extracted from this sample with an additional galaxy at a slightly higher redshift (PACS-282; $z=2.19$)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00952.S
- bands: Band 3  
  > "using 25-30 12m antennas and the band 3 receiver tuned to intermediate frequencies between 86.395 - 94.888 GHz" (Observations of CO emission at high-z)
- frequencies and spectral setup: 86.395-94.888 GHz, 488 kHz resolution, 1.875 GHz bandpass  
  > "with a resolution of 488 kHz and spectral bandpass of 1.875 GHz" (Observations of CO emission at high-z)
- continuum bandwidth: _not stated_
- arrays: 12m, 25-30 antennas  
  > "using 25-30 12m antennas" (Observations of CO emission at high-z)
- configurations: _not stated_
- baselines: up to ~400 m (SB1), ~200 m (SB2)  
  > "The antenna configurations had baselines up to $\sim$400m ($\sim$200m) for SB1 (SB2)" (Observations of CO emission at high-z)
- angular resolution: 1.3" x 1.0" (SB1); 4.5" x 2.0" (SB2); 5.4" x 2.7" for PACS 325  
  > "resulting in a beam size (FWHM) of $1.3\ensuremath{''} \times 1.0\ensuremath{''}$ ($4.5\ensuremath{''} \times 2.0\ensuremath{''}$; $5.4\ensuremath{''} \times 2.7\ensuremath{''}$ for PACS 325 only)" (Observations of CO emission at high-z)
- max recoverable scale: _not stated_
- sensitivity: 0.12 (819) and 0.10 (830) mJy/beam over 400 km/s; deeper fields 0.073-0.14 mJy/beam  
  > "The images of PACS-819 (830) have a flux sensitivity level of 0.12 (0.10) mJy beam$^{-1}$ over a bandwidth of 400 km s$^{-1}$" (Observations of CO emission at high-z)
- time on source: 32 min (819, 830), 2.3 h (299, 325), 3.8 h (867)  
  > "On-source exposure times were 32 minutes (819 and 830), 2.3 hours (299 and 325) and 3.8 hours (867)" (Observations of CO emission at high-z)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (not stated)
- Line: 12CO 3-2 (PACS-282 only) (not stated)
- Other facility **IRAM/PdBI**: CO observations of PACS-282 (3-2) and PACS-164 (2-1)  
  > "interferometric measurements were obtained with IRAM/PdBI for PACS-282 (CO 3-2) and PACS-164 (CO 2-1)" (Observations of CO emission at high-z)
- Other facility **Subaru FMOS (FMOS-COSMOS)**: Halpha etc. spectra for redshifts, SFRs, metallicities  
  > "These spectra provide a detection of key diagnostic emission lines" (Introduction)
- Other facility **Herschel**: far-IR photometry for L_TIR and sample selection  
  > "identified with Herschel observations over the COSMOS field" (Introduction)
- External data: MS outlier sample selection  
  > "identified with Herschel observations over the COSMOS field (cite: Rodighiero2011)" (Introduction) [from Rodighiero2011]
- External data: Literature CO and L_TIR compilation of low- and high-z galaxies, and empirical model  
  > "include both low- and high-redshift galaxies with measurements available in the literature and compiled in (cite: Sargent2014)" (CO-to-IR ratio) [from Sargent2014]
- External data: Mass-metallicity relation at z~1.6  
  > "we show the mass-metallicity relation at $z\sim1.6$ (cite: Zahid2014)" (Gas masses, $\alpha_{\rm CO}$, and SFE) [from Zahid2014]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars, Ganymede  
  > "Standard targets were used for flux (Mars, Ganymede), bandpass, and phase calibration." (Observations of CO emission at high-z)
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

- Stellar masses and SFRs (L_TIR) derived as in earlier work  
  > "thus accounting for the obscured star formation as in (cite: Magdis2012)" (Introduction) [from (cite: Magdis2012)]
- Dynamical mass method for gas mass  
  > "we can estimate the total gas mass using the dynamical mass method (cite: Tan2014)" (Gas masses, $\alpha_{\rm CO}$, and SFE) [from (cite: Tan2014)]
- CO excitation corrections 0.85 and 0.7 for CO(2-1), CO(3-2)  
  > "using values of 0.85 and 0.7, respectively for CO (2-1) and CO (3-2) (Daddi et al. 2015)" (CO-to-IR ratio) [from Daddi et al. 2015]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure/pipeline
- Bandpass and phase calibrator names
- Imaging parameters (weighting, cell size, deconvolution)
- uvfit settings and line integration window
- How L_TIR, SFR and M* were computed in detail

## Analysis recipe

1. **Measure CO flux and size**: Fit visibilities in UV space with GILDAS uvfit using a point source or circular Gaussian  
  > "We measure the CO flux by fitting the data in UV space with the GILDAS task ‘uvfit’ available in the MAPPING package." (Observations of CO emission at high-z)
   - software: GILDAS uvfit, CASA imfit
   - fitting: Point source or circular Gaussian model returning centroid, deconvolved size and integrated flux  
  > "returns the centroid, de-convolved source size, and integrated flux" (Observations of CO emission at high-z)
   - validation: Compared with CASA imfit in the image plane  
  > "We find good agreement between fluxes returned from GILDAS with those using ‘imfit’ in the image plane with CASA." (Observations of CO emission at high-z)
2. **Compare L'CO/L_TIR with the main sequence**: Convert to CO(1-0), plot L'CO vs L_TIR and normalised ratios against the Sargent2014 compilation  
  > "All line luminosities are converted to CO (1-0) using values of 0.85 and 0.7, respectively for CO (2-1) and CO (3-2)" (CO-to-IR ratio)
   - fitting: _not stated_
   - validation: Tested alternative excitation corrections  
  > "Different excitation corrections than those applied here would not impact our results" (CO-to-IR ratio)
3. **Gas masses and alpha_CO from dynamical mass**: M_dyn = 5 sigma^2 r_1/2 / G; subtract half the stellar mass and dark matter to get gas mass, for the two resolved sources  
  > "$$\begin{equation} M_{\rm dyn}(r<r_{\rm 1/2}) \simeq \frac{5 \sigma^2 r_{\rm 1/2}}{G} \label{eq1} \end{equation}$$" (Gas masses, $\alpha_{\rm CO}$, and SFE)
   - assumption: Spherical symmetry; dark matter M_DM = 0.25 M_dyn  
  > "a dark matter component ($M_{\rm DM}=0.25\times$ $M_{dyn}$; (cite: Daddi2010a))" (Gas masses, $\alpha_{\rm CO}$, and SFE)
   - fitting: _not stated_
   - validation: Compared with alpha_CO of GN20 and merger values; metallicity check  
  > "both not far from those found for the high-redshift submillimeter galaxies in the proto-cluster GN20 (cite: Tan2014) and consistent with lower conversion factors for galaxies in mergers (cite: Narayanan2011)" (Gas masses, $\alpha_{\rm CO}$, and SFE)
4. **Gas masses for unresolved sources**: Apply the average alpha_CO = 1.1 to the CO luminosities  
  > "using the average ($\alpha_{\rm CO}=1.1$ M$_{\odot}$ / K km s$^{-1}$ pc$^{-2}$) value of the two estimates" (Gas masses, $\alpha_{\rm CO}$, and SFE)
   - fitting: _not stated_
   - validation: Checked metallicity via mass-metallicity relation and BPT diagram  
  > "In Figure [4](#fig:emlines)$a$, we show the mass-metallicity relation at $z\sim1.6$ (cite: Zahid2014) based on \[NII\]$\lambda6585$/H$\alpha$, with our sample shown in red." (Gas masses, $\alpha_{\rm CO}$, and SFE)

## Software

- **GILDAS (MAPPING, uvfit)** : UV-plane fitting of CO flux  
  > "GILDAS task ‘uvfit’ available in the MAPPING package" (Observations of CO emission at high-z)
- **CASA (imfit)** : Image-plane check of fluxes  
  > "using ‘imfit’ in the image plane with CASA" (Observations of CO emission at high-z)
- **Hyperz** : SED fitting for stellar masses  
  > "Stellar masses are derived from SED-fitting using Hyperz" (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO integrated flux range | 0.28-1.18 | not stated | Jy km/s | 1 | integrated flux densities ($I_{CO}$) ranging from 0.28 to 1.18 Jy km s$^{-1}$ |
| Median L'CO/<L'CO>_MS | 0.60 | 0.04 | dimensionless | 2 | We measure a median value of $L^\prime_{\rm CO}/<L^\prime_{\rm CO}>_{\rm MS}=0.60\pm0.04$ for our sample. |
| Gas mass PACS-819 | 2.0e10 | 1.2e10 | Msun | 3 | $2.0\pm1.2 \; (6.2\pm2.2)\times10^{10}$ M$_{\odot}$ |
| Gas mass PACS-830 | 6.2e10 | 2.2e10 | Msun | 3 | $2.0\pm1.2 \; (6.2\pm2.2)\times10^{10}$ M$_{\odot}$ |
| alpha_CO PACS-819 | 0.6 | 0.3 | Msun/(K km/s pc^2) | 3 | we estimate $\alpha_{\rm CO}=0.6\pm0.3$ for PACS-819 and $1.6\pm0.6$ for PACS-830 |
| alpha_CO PACS-830 | 1.6 | 0.6 | Msun/(K km/s pc^2) | 3 | we estimate $\alpha_{\rm CO}=0.6\pm0.3$ for PACS-819 and $1.6\pm0.6$ for PACS-830 |
| Gas fractions | 28-52% | not stated | percent | 4 | gas fractions $f_{\rm gas}=M_{\rm gas} / (M_{\rm gas} + M_{*}$) between 28 and 52% |

## Qualitative findings

- All sample galaxies lie below the MS L'CO-L_TIR correlation, with a smaller offset than local starbursts  
  > "All galaxies in our sample have $L^\prime_{\rm CO}/L_{\rm TIR}$ below the well-defined correlation for MS galaxies." (CO-to-IR ratio)

## Claim tuples

- H: High-z MS outliers have a lower L'CO/L_TIR (higher SFE) than MS galaxies | E: CO(2-1)/(3-2) with ALMA and PdBI for 7 Herschel-selected outliers | R: Median ratio 0.60±0.04 of MS, offset 1.7±0.1x | F: Offset exists but is smaller than the ~3x of local starbursts | **supported**
- H: SFE is bimodal | E: Compare sample with MS trend vs sSFR | R: Sample follows a continuation of the MS trend | F: Suggests continuous SFE distribution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO uncertain; metallicity of ionised gas may not represent molecular gas; AGN cannot be excluded  
  > "we cannot rule out the presence of a low-to-moderate luminosity AGN" (Gas masses, $\alpha_{\rm CO}$, and SFE)
- Caveat (inferred, ours): alpha_CO derived from two marginally resolved sources and applied to all
- Caveat (inferred, ours): Small sample of seven with mixed ALMA/PdBI data
- Caveat (inferred, ours): Dynamical mass assumes spherical geometry and widths from low S/N lines

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging details
- Missing: L_TIR and M* values require external catalogues
- Missing: Line integration windows for uvfit
- Data volume (inferred): ~10-30 GB for ALMA raw data
- Score (inferred): 4/5, Few processing details; the main numbers depend on external catalogues, but the analysis is simple.
- Rediscovery candidate: no, Calibration and fit details are missing, and the L_TIR and stellar mass inputs come from external catalogues.

## Links

- Method: Tan2014 (Dynamical mass method for gas mass)
- Method: Sargent2014 (Empirical model and CO compilation)
- Companion: Silverman2015 (FMOS-COSMOS survey)
- Companion: Rodighiero2011 (MS outlier selection)
- Related: FMOS-COSMOS
- Related: COSMOS
- Related: zCOSMOS-Deep

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 36,
  "rate": 0.514
 },
 "evidence_ok": true
}
```
