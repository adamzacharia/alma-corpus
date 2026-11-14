# Multiwavelength study of OT 081: broadband modelling of a transitional blazar

`2025MNRAS.540..364A` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Abe, H. | arXiv: 2410.22557 | DOI: 10.1093/mnras/stae2469

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: What is the broadband emission and emitting-region location of the blazar OT 081 during its July 2016 flare with first VHE detection, and is it a transitional BL Lac/FSRQ?  
  > "The discovery of VHE $\gamma$-ray emission happened during a high state of $\gamma$-ray activity in July 2016, observed by many instruments from radio to VHE $\gamma$-rays." (abstract)
- Target **OT 081 (PKS 1749+096, 4C 09.57)**: coordinates _not stated_; z/distance z = 0.320 ± 0.005  
  > "OT 081, also known as PKS 1749+096 and 4C 09.57, is a blazar located at a redshift of $z$=0.320 $\pm~ 0.005$ (cite: 1988A&A...191L..16S)." (1 Introduction); distance from (cite: 1988A&A...191L..16S)  
  > "OT 081, also known as PKS 1749+096 and 4C 09.57, is a blazar located at a redshift of $z$=0.320 $\pm~ 0.005$ (cite: 1988A&A...191L..16S)." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00856.S
- bands: 250, 320 and 450 GHz bands  
  > "observed OT 081 in the 250, 320, and 450 GHz bands." (2.5 Radio band)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12-m array baselines up to 16 km (general ALMA description)  
  > "the 12-m array with baselines up to 16 km" (2.5 Radio band)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **MAGIC**: VHE gamma-ray spectrum and light curve  
  > "The energy range of the MAGIC analysis performed in this work extends from 55 to 300 GeV." (2.1.1 MAGIC)
- Other facility **H.E.S.S.**: VHE gamma-ray data from the 28-m telescope  
  > "The analysis presented here only includes monoscopic data from the 28-meter telescope." (2.1.2 H.E.S.S.)
- Other facility **Fermi-LAT**: HE gamma-ray light curve and spectra  
  > "We used the Fermitools software package (cite: 2019ascl.soft05011F) to analyse Pass8 `source` class (P8R3) events in the energy range 0.1-300 GeV." (2.2 HE gamma-rays)
- Other facility **Swift XRT/UVOT**: X-ray and UV/optical data  
  > "carried out 9 observations of OT 081 between 11 July (MJD 57580) and 28 July 2016 (MJD 57597)." (2.3 X-rays)
- Other facility **OVRO 40-m**: 15 GHz radio light curve  
  > "The 15 GHz data of OT 081 were obtained from the Owens Valley Radio Observatory (OVRO) 40-m Telescope blazar monitoring program" (2.5 Radio band)
- Other facility **VLBA (BU blazar program)**: 43 GHz jet kinematics  
  > "Very Long Baseline Array (VLBA) observations of OT 081 were obtained at 43 GHz for 23 epochs from June 2015 to June 2017" (2.5 Radio band)
- External data: Optical spectrum from 30 August 2016 (Steward Observatory database) used for H-beta luminosity  
  > "more recent spectra are available in the Steward observatory database." (4.1 Leptonic emission model) [from Steward Observatory spectropolarimetric monitoring]
- External data: EBL absorption model  
  > "estimated using the model from (cite: 2011MNRAS.410.2556D)" (2.1.1 MAGIC) [from (cite: 2011MNRAS.410.2556D)]

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

- VLBA data reduction and uncertainty relations  
  > "The data reduction was performed using the Astronomical Image Processing System (AIPS) and *Difmap* software packages as described in (cite: 2017ApJ...846...98J)." (2.5 Radio band) [from (cite: 2017ApJ...846...98J)]
- OVRO calibration and reduction  
  > "Complete details of the reduction and calibration procedure can be found in (cite: 2011ApJS..194...29R)." (2.5 Radio band) [from (cite: 2011ApJS..194...29R)]

### Not stated but needed to reproduce (our reading)

- ALMA reduction: calibration, flux calibrators, imaging and how light curve fluxes were extracted are not described
- Which ALMA band/epochs form the 250 GHz light curve
- Fit procedure and priors for SED models (parameters hand-tuned)
- Underlying data for the SED modelling not given as files

## Analysis recipe

1. **Quantify variability of light curves**: Fractional variability computed for each light curve including ALMA 250 GHz  
  > "We have calculated the fractional variability ($F_{\textrm{var}}$) as in Eq. 3 of (cite: 2003MNRAS.345.1271V) for the light curves shown in Fig. [2]" (3 Multi-wavelength light curves)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit gamma-ray spectra**: Fermi-LAT and VHE points fitted with power law and log-parabola by chi2 minimisation with MCMC  
  > "the minimisation was performed with the Markov Chain Monte Carlo method implemented in the emcee python package." (4.1 Leptonic emission model)
   - software: emcee
   - fitting: chi2, emcee MCMC; likelihood ratio test for significance  
  > "The significance C.L. is derived from a likelihood ratio test comparing the log-parabola fit to the power-law." (4.1 Leptonic emission model)
   - validation: _not stated_
3. **Model SEDs (leptonic EIC, lepto-hadronic, proton-synchrotron)**: Leptonic model of Maraschi & Tavecchio 2003; hadronic code of Cerruti et al. 2015; parameters fine-tuned to fit SED  
  > "These values are taken as indicative starting values which are then fine tuned to provide a good fit to the SED." (4.1 Leptonic emission model)
   - assumption: Torus blackbody T=10^3 K; BLR covering factor 0.1; IR covering 0.4-0.6  
  > "Adopting the standard covering factor for the BLR, $f_{\rm cov_{BLR}}=0.1$" (4.1 Leptonic emission model)
   - fitting: _not stated_
   - validation: _not stated_
4. **Constrain emitting region location via gamma-gamma opacity**: Extrapolate HE spectrum to VHE, compare with EBL-corrected data, 95th percentile of 10^4 realizations, compare with agnpy opacity  
  > "the limit on $\tau_{\gamma \gamma} (E)$ is estimated as the 95th percentile of the distribution for $10^{4}$ realizations." (4.3 Constraints on the location of the emitting region)
   - software: agnpy
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC spectral fits  
  > "implemented in the emcee python package." (4.1 Leptonic emission model)
- **agnpy** revision 0113497b: gamma-gamma opacity calculations  
  > "These calculations are carried out using the agnpy code (revision 0113497b)" (4.3 Constraints on the location of the emitting region)
- **Fermitools** : Fermi-LAT likelihood analysis  
  > "We used the Fermitools software package (cite: 2019ascl.soft05011F)" (2.2 HE gamma-rays)
- **XSPEC** 12.13.0c: X-ray spectral fitting  
  > "The X-ray spectral analysis was performed using the XSPEC 12.13.0c software package" (2.3 X-rays)
- **MARS** : MAGIC analysis  
  > "the analysis was performed using the standard MAGIC analysis framework MARS" (2.1.1 MAGIC)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fvar ALMA 250 GHz light curve | 0.28 | 0.01 | dimensionless | 1 | we calculated an $F_{\textrm{var}}$ of 0.28$\pm$0.01 for the ALMA light curve at 250 GHz. |
| MAGIC intrinsic VHE spectral index (55-300 GeV) | 3.27 | 0.44 stat, 0.15 sys | dimensionless | 2 | index $3.27\pm0.44_{\rm stat}\pm0.15_{\rm sys}$ (MAGIC) |
| H.E.S.S. intrinsic VHE spectral index | 3.39 | 0.58 stat, 0.64 sys | dimensionless | 2 | $3.39\pm0.58_{\rm stat}\pm0.64_{\rm sys}$ (H.E.S.S.) |
| Emitting region distance lower limit | >0.8 R_BLR | not stated | R_BLR | 4 | the location of the emitting region would be located at a distance of $>0.8\times R_{\rm{BLR}}$. |

## Qualitative findings

- One-zone SSC cannot reproduce the broadband SED; an external Compton component is required; the source appears a transitional blazar.  
  > "The broadband emission cannot be sucessfully reproduced by a simple one-zone synchrotron self-Compton model. Instead, an additional external Compton component is required." (abstract)

## Claim tuples

- H: Is a one-zone SSC model sufficient for OT 081 during the flare? | E: Constrain SSC parameters from synchrotron and IC peaks | R: Implied delta ≈ 122 and B ≈ 8.2e-6 G, CD ~20 | F: SSC insufficient; external Compton needed | **supported**
- H: Where is the emitting region? | E: gamma-gamma opacity test with BLR | R: >0.8 R_BLR | F: At BLR edge or beyond; torus-dominated radiation field | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Proton-synchrotron dominated model requires extreme proton luminosity L_p = 5.6e48 erg/s  
  > "The proton luminosity would reach extreme values, $L_{p} = 5.6\times10^{48}$ erg s$^{-1}$" (4.2 Lepto-hadronic emission model)
- How they decided it was enough: _not stated_
- Limitation (authors): Sparse simultaneous multiwavelength data prevent detailed study of the double flare  
  > "the sparse MWL data simultaneous to the most active period in the HE band do not allow a detailed study of the double structured flare." (3 Multi-wavelength light curves)
- Caveat (inferred, ours): ALMA processing is entirely undescribed
- Caveat (inferred, ours): SED model parameters hand-tuned without uncertainties
- Caveat (inferred, ours): Degenerate solutions in hadronic models

## Reproducibility

- Data public (paper): MAGIC FITS and data tables released after publication; other data on request  
  > "Other data underlying this article will be shared on reasonable request to the corresponding authors." (Data availability)
- Products in archive: _not stated_
- Missing: ALMA calibration and flux extraction details
- Missing: Proprietary MAGIC/H.E.S.S. data and analysis chains
- Data volume (inferred): ALMA part small (flux monitoring); other facilities not ALMA-related
- Score (inferred): 2/5, ALMA is a minor ancillary light curve with no processing details; the main results rely on non-public IACT data.
- Rediscovery candidate: no, ALMA role is minor and undocumented, and main results rely on non-ALMA, largely non-public data.

## Links

- Related: VLBA-BU-Blazar program
- Related: OVRO 40-m monitoring program
- Related: Steward Observatory monitoring

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 30,
  "rate": 0.405
 },
 "evidence_ok": true
}
```
