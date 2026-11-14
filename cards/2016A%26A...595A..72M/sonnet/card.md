# GRB 980425 host: [C II], [O I], and CO lines reveal recent enhancement of star formation due to atomic gas inflow

`2016A&A...595A..72M` | Astronomy and Astrophysics 2016 | first author: Michałowski, M. J. | arXiv: 1609.01742 | DOI: 10.1051/0004-6361/201629441

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Is star formation in the GRB 980425 host fuelled by a recent inflow of atomic gas, as probed by FIR line, CO and SFR indicators?  
  > "Our aim is to test this possibility by studying in detail the properties of gas in the closest galaxy hosting a GRB (980425)." (abstract)
- Target **GRB 980425 host**: coordinates _not stated_; z/distance z=0.0085; 36.5 Mpc  
  > "GRB 980425 at $z=0.0085$ is at a luminosity distance of 36.5 Mpc and $1''$ corresponds to 175 pc at its redshift." (1 Introduction); distance from redshift from Tinney et al. 1998; H0=70, OmegaL=0.7, Omegam=0.3  
  > "GRB 980425 at $z=0.0085$ is at a luminosity distance of 36.5 Mpc and $1''$ corresponds to 175 pc at its redshift." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00046.S
- bands: Band 3  
  > "We performed Band 3 ALMA observations on 1 Sep 2012" (2 Data)
- frequencies and spectral setup: Four 1.875 GHz spectral windows centred at 100.6, 102.4, 112.5, 114.3 GHz; ~488 kHz (~1.3 km/s) resolution  
  > "Four $1.875$ GHz spectral windows were centred at $100.6$, $102.4$, $112.5$, and $114.3$ GHz." (2 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 24-384 m, 23 antennas  
  > "Twenty three antennas and baselines ranging between $24$ and $384$ m were available." (2 Data)
- angular resolution: ~1.7 arcsec synthesised beam  
  > "The synthesised beam of the cube is $\sim1.7\,\ensuremath{''}$." (2 Data)
- max recoverable scale: ~11 arcsec  
  > "our ALMA observations are not sensitive to smooth emission extended over scales of more than $\sim11\ensuremath{''}$" (4 Results)
- sensitivity: _not stated_
- time on source: 67.4 min  
  > "A total of 67.4 min of on-source data were obtained." (2 Data)
- observing dates: 1 Sep 2012  
  > "We performed Band 3 ALMA observations on 1 Sep 2012" (2 Data)
- pi or archival as stated: PI: M. Michałowski  
  > "project no. 2011.0.00046.S, PI: M. Michałowski" (2 Data)
- Line: CO J=1-0 (114.288 GHz)
- Other facility **Herschel/PACS**: [C II] 158 um and [O I] 63 um spectroscopy  
  > "We obtained Herschel (cite: herschel) observations of the GRB 980425 host (project no. OT2_jmcastro_3, PI: J. M. Castro Cerón)" (2 Data)
- Other facility **APEX/SHeFI**: CO(2-1) detection  
  > "The APEX-1 single-sideband (SSB) was tuned to the observed frequency of the CO(2-1) line of 228.6 GHz." (2 Data)
- External data: 100 um map and WR-region SED model, UV/IR SFRs  
  > "using the *Herschel*/PACS map presented in (cite: michalowski14)" (3 Methods) [from (cite: michalowski14)]
- External data: HI mass log(MHI/Msun)~8.849  
  > "$\log(\mbox{$M_{\rm H{\sc I}}$}/\mbox{$M_\odot$})\sim8.849$ (cite: michalowski15hi)" (4 Results) [from (cite: michalowski15hi)]
- External data: Host metallicity 12+log(O/H)~8.6  
  > "metallicity $12 + \log(\mbox{O}/\mbox{H})\sim8.6$ (cite: sollerman05)" (4 Results) [from (cite: sollerman05)]

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
- smoothing: Binned 10 channels to ~4.9 MHz (~13 km/s)  
  > "binning 10 channels resulting in spectral resolution of $\sim4.9\,$MHz (corresponding to $\sim13\,\mbox{km\,s$^{-1}$}$)." (2 Data)
- final beam: ~1.7 arcsec  
  > "The synthesised beam of the cube is $\sim1.7\,\ensuremath{''}$." (2 Data)
- final rms: _not stated_

### Inherited from earlier work

- ALMA continuum map presented earlier  
  > "The continuum map was presented in (cite: michalowski14)" (2 Data) [from (cite: michalowski14)]
- SFR calibration from [CII]/[OI]  
  > "we estimated the SFRs from the \[C ii\] and \[O i\] lines using the conversion of (cite: delooze14)" (3 Methods) [from (cite: delooze14)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration pipeline/CASA version and flagging
- tclean parameters (weighting, robust, cleaning, masks, cell and image size)
- Continuum subtraction and line-free channels
- Exact aperture definitions for the PACS-spaxel CO(1-0) spectra
- Primary beam correction

## Analysis recipe

1. **Extract ALMA CO(1-0) spectra and upper limits**: Spectra extracted over PACS spaxel footprints and 1.7'' WR aperture; flux measured in 40 km/s width at frequency giving highest conservative upper limit  
  > "No significant emission is detected, so we measured fluxes within $40\,\mbox{km\,s$^{-1}$}$ width" (4 Results)
   - software: CASA
   - assumption: alpha_CO = 5 Msun/(K km/s pc^2)  
  > "assuming the Galactic CO-to-H$_2$ conversion factor $\alpha_{\rm CO}=5\mbox{$M_\odot$}/(\mbox{K\,km\,s$^{-1}$\,pc$^2$})$" (3 Methods)
   - fitting: _not stated_
   - validation: Compared with APEX CO(2-1): ALMA misses extended emission  
  > "so our ALMA observations do not seem to probe the main emission component in the GRB 980425 host" (4 Results)

## Software

- **CASA** : ALMA data reduction and analysis  
  > "The data reduction and analysis were done using the Casa package (cite: casa)." (2 Data)
- **HIPE** v12.1.0: PACS data reduction  
  > "Herschel Imaging Processing Environment (cite: hipe) v12.1.0" (2 Data)
- **GILDAS/CLASS** : APEX CO(2-1) reduction  
  > "We reduced and analysed the data using the Continuum and Line Analysis Single Dish Software (Class)" (2 Data)
- **PDR Toolbox** : Density and G0 modelling  
  > "using the Photo Dissociation Region (PDR) Toolbox (cite: pound08; kaufman06)" (3 Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SFE L_IR/L'CO(1-0) | 95 | 19 | Lsun/(K km/s pc^2) | 0 | $L_{\rm IR}/L'_{\rm CO(1-0)}=(95\pm19)\,\mbox{$L_\odot$}/(\mbox{K\,km\,s$^{-1}$\,pc$^2$})$ |
| Mean SFR_line/SFR_continuum in GRB hosts | 1.74 | 0.32 | dimensionless | 0 | The mean ratio of the SFR derived from line indicators to that from the continuum indicator is $1.74\pm0.32$. |
| Host M_H2 from CO(2-1) | 54.2 | 10.7 | 1e6 Msun | 0 | Host / $6.5\pm1.3$ / $5.1$ / $0.0050\pm0.0010$ / $0.021\pm0.004$ / $5.4\pm1.1$ / $54.2\pm10.7$ |

## Qualitative findings

- ALMA CO(1-0) not significantly detected  
  > "No significant emission is detected" (4 Results)

## Claim tuples

- H: GRB host star formation was recently enhanced by atomic gas inflow | E: [CII], [OI], CO and SFR indicators comparison | R: Line SFRs 1.5-6 times above IR SFR; high [OI]/FIR; low CO | F: Consistent with very recent atomic gas inflow | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Low metallicity, end of star formation episode, and minor merger considered less likely  
  > "Here we provide arguments that alternative explanations for our data are less likely." (Alternative explanations)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA CO(1-0) flux of the host underestimated if extended emission present  
  > "if such emission is present, then our CO(1-0) flux of the entire host is underestimated" (4 Results)
- Caveat (inferred, ours): ALMA CO is non-detection and resolves out extended emission
- Caveat (inferred, ours): Inflow interpretation not uniquely constrained

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging parameters
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, ALMA role minor; imaging details missing
- Rediscovery candidate: no, ALMA part non-detection with unstated imaging parameters.

## Links

- Companion: (cite: michalowski15hi) (HI inflow hypothesis)
- Companion: (cite: michalowski14) (ALMA continuum and SED)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 30,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
