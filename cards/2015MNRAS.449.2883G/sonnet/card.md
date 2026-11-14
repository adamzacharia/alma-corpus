# The nature of the [C II] emission in dusty star-forming galaxies from the SPT survey

`2015MNRAS.449.2883G` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Gullberg, B. | arXiv: 1501.06909 | DOI: 10.1093/mnras/stv372

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: What is the nature of [CII] emission in lensed SPT dusty star-forming galaxies, and what ISM conditions explain the [CII]/CO(1-0) and [CII]/FIR ratios?  
  > "The [CII], low-$J$ CO and FIR data allow us to constrain the properties of the interstellar medium." (abstract)
- Target **SPT DSFGs (20 lensed sources, e.g. SPT0346-52, SPT0418-47)**: coordinates see Table 1 in weiss13 and Appendix Table 1 (two new sources: SPT2311-54 23:11:23.94 -54:50:30.0; SPT2319-55 23:19:21.67 -55:57:57.8)  
  > "These 20 sources are a subset of those selected from the first 1300 deg$^2$ of the 2500 deg$^2$ SPT-SZ survey." (1 Introduction); z/distance z = 2.123-5.699  
  > "These 20 sources are a subset of those selected from the first 1300 deg$^2$ of the 2500 deg$^2$ SPT-SZ survey." (1 Introduction); distance from CO lines from ALMA plus [CII] (weiss13)  
  > "These 20 sources are a subset of those selected from the first 1300 deg$^2$ of the 2500 deg$^2$ SPT-SZ survey." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00957.S, 2011.0.00958.S, 2012.1.00844.S
- bands: ALMA band 3 continuum for two new sources; CO(3-2) to CO(6-5) lines from ALMA  
  > "Source positions are based on the ALMA 3 mm continuum data." (New redshifts)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: APEX/FLASH on-source 1.5-5 h per source (82 h total); SPIRE FTS 3.8 h per source  
  > "On-source integration times were between 1.5 and 5 hours." (2.2 APEX/FLASH)
- observing dates: ALMA not dated; APEX 345 GHz 2012 Aug-2014 Jun, 460 GHz 2013 Mar-Aug  
  > "were observed in the 345 GHz channel between 2012 August and 2014 June" (2.2 APEX/FLASH)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um fine structure (1900.54 GHz)
- Other facility **APEX/FLASH**: [CII] spectra for 17 sources  
  > "We detect [CII] emission in 16 out of 17 sources observed with FLASH." (2.2 APEX/FLASH)
- Other facility **Herschel SPIRE FTS**: [CII] for three z~2 sources  
  > "We thus observed these sources with the SPIRE Fourier Transform Spectrometer" (2.3 Herschel/SPIRE)
- Other facility **ATCA**: low-J CO for 11 sources  
  > "low-$J$ CO emission lines (CO(1–0) or CO(2–1)) were observed with the Australia Telescope Compact Array (ATCA) for 11" (2.1 Supporting ALMA and ATCA observations)
- External data: Lens models and magnifications for four sources (mu 5.4-21.0)  
  > "The four sources with lens models have lensing magnification factors $\mu$ between $\sim5.4-21.0$" (3.2 Lensing) [from (cite: hezaveh13)]
- External data: Low-z and high-z comparison sample of [CII] and CO  
  > "We compare the SPT sample with that of Gracia-Carpio et al. (in prep), which is comprised of 333 sources." (4.1 Comparison sample) [from Gracia-Carpio et al. (in prep); (cite: diazsantos13); (cite: brauher08)]
- External data: ATCA low-J CO fluxes  
  > "Details of the observations, fluxes and associated uncertainties will be presented in a forthcoming paper by Aravena *et al.*" (2.1 Supporting ALMA and ATCA observations) [from Aravena et al. in prep]
- Simulation/model as data: PDR model grids used in diagnostic diagram  
  > "The PDR model used in this diagram (cite: kaufman99) models a plane-parallel slab divided into a number of zones of different depths." (5.2.1)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ATCA absolute flux accurate to 15%  
  > "Absolute flux calibration of the ATCA data is estimated to be accurate to within 15%." (2.1 Supporting ALMA and ATCA observations)
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

- SED fitting for L_FIR and Td (greybody, beta=2.0)  
  > "fixing the emissivity index ($\beta$) at 2.0, $\mu_0=100$ and fitting $\lambda_{\text{rest}}<50\,\mu$m, following (cite: greve12)" (4.1.2 FIR luminosities) [from (cite: greve12) and Strandet et al. (in prep)]
- SPIRE FTS line flux method  
  > "We determine the integrated line flux in the same manner as (cite: valtchanov11)" (3.1) [from (cite: valtchanov11)]
- CO scaling factors to CO(1-0)  
  > "we adopt the scaling factor of 0.9 from (cite: stacey10)" (4.1.1) [from (cite: stacey10)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction, CASA version and imaging settings for CO spectra
- Extraction apertures for ALMA CO spectra
- ATCA CO(1-0) fluxes (forthcoming paper)
- Comparison sample table (Gracia-Carpio in prep)
- SED photometry inputs for L_FIR

## Analysis recipe

1. **reduce APEX [CII] spectra**: CLASS processing, linear baseline subtraction, regrid to ~90 km/s  
  > "We subtracted linear baselines from the individual spectra in each of the two FFTS units, and regridded to a velocity resolution of $\sim90$ km s$^{-1}$" (2.2 APEX/FLASH)
   - software: CLASS
   - fitting: _not stated_
   - validation: _not stated_
2. **compare CO and [CII] line profiles**: Single/double Gaussian fits, joint fit with one scaling parameter  
  > "We then simultaneously fit the single or double Gaussian profile (depending on what is necessary to fit the profiles individually) to the CO and [CII] velocity profiles" (3.1)
   - parameter: accept if reduced chi2 < 1+5*sqrt(2 n_dof)  
  > "We accept the single Gaussian fit if the reduced $\chi^2$ does not exceed 1+5$\times \sqrt{2 n_\textrm{dof}}$" (3.1)
   - fitting: chi2 Gaussian fits  
  > "We accept the single Gaussian fit if the reduced $\chi^2$ does not exceed 1+5$\times \sqrt{2 n_\textrm{dof}}$, where $n_\textrm{dof}$ is the number of degrees of freedom." (3.1 Velocity profiles and line fluxes)
   - validation: FWHM cross-checked with velocity-weighted moments  
  > "we also fit the spectra by taking velocity-weighted moments, and find fully consistent results." (3.1)
3. **derive L_FIR and Td**: Greybody SED fit, integrate 42-500 um rest  
  > "We integrate the SED between $\lambda_{\text{rest}}=42-500\,\mu m$ in the rest frame to obtain $L_{\text{FIR}}$." (4.1.2)
   - assumption: beta = 2.0  
  > "by fitting the well-sampled spectral energy distributions (SEDs) with a greybody law fixing the emissivity index ($\beta$) at 2.0" (4.1.2 FIR luminosities)
   - fitting: _not stated_
   - validation: _not stated_
4. **constrain excitation temperature and optical depth from [CII]/CO(1-0)**: Source-function model of luminosity ratio compared with observed ratio  
  > "We now generalise this line ratio method by comparing the source functions." (5.1.1)
   - assumption: same filling factors for [CII] and CO  
  > "where we have assumed that the \[CII\] and CO emitting gas have the same filling factors" (5.1.1 Determining the optical depth of the [CII] line)
   - assumption: Tex,CO(1-0)=Td~35 K  
  > "allows us to fix the $T_{\text{ex,CO(1--0)}}$ = $T_{\text{d}}$ $\simeq35\,$K" (5.1.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **compare with PDR models**: Place sources on [CII]/FIR vs CO/FIR diagnostic diagram with Kaufman99 tracks to estimate G0 and n  
  > "we obtain a rough estimate of the radiation field strength and the gas density of $100<G_0<8000$" (5.2.1)
   - assumption: alpha_CO = 0.8 (and 2) Msun/(K km/s pc2); 70% of [CII] from PDRs  
  > "(cite: hailey-dunsheath10) assume that 70% of the \[CII\] emission originates from PDRs" (5.2.1 Implications of the photodissociation region structure)
   - fitting: _not stated_
   - validation: PDR sizes compared with lens model radii  
  > "The estimated radii of the PDRs, while fairly uncertain, are comparable to the source sizes determined by the lens models." (5.2.1 Implications of the photodissociation region structure)

## Software

- **CLASS** : APEX/FLASH data processing  
  > "The data were processed with the Continuum and Line Analysis Single-dish Software (CLASS" (2.2 APEX/FLASH)
- **HIPE** v11: SPIRE FTS reduction  
  > "in the *Herschel* reduction tool HIPE v11" (2.3 Herschel/SPIRE)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] detections | 17 of 20 | not stated | sources | 1 | We have 17 [CII] emission line detections (16 with FLASH and one with *Herschel* SPIRE FTS) |
| L[CII]/L_CO(1-0) | 5200 | 1800 | dimensionless | 4 | we determine the $L_{\text{[C{\scriptsize II}]}}/L_{\text{CO(1--0)}}$ ratio to be $5200\pm1800$ |
| [CII] FWHM range | ~210-820 | not stated | km/s | 2 | The resulting FWHMs are in the range $\sim210-820\,$km/s. |
| G0 range | 100-8000 | not stated | Habing | 5 | $100<G_0<8000$ and $10^{2}\,$cm$^{-3}<n<10^5$ cm$^{-3}$ |
| mean magnification | 14.1 | 7.8 | dimensionless | 0 | mean magnification factor $\langle\mu\rangle=14.1\pm7.8$ |

## Qualitative findings

- [CII] and CO profiles are consistent, so differential lensing is not significant  
  > "the similar [CII] and CO velocity profiles suggest that such differential lensing is not significant." (3.2 Lensing)

## Claim tuples

- H: Is differential lensing between [CII] and CO significant? | E: Compared Gaussian fits of [CII] and ALMA CO profiles | R: 13 of 14 consistent | F: Differential lensing not significant | **supported**
- H: What ISM conditions give the observed [CII]/CO(1-0) ratio? | E: Source-function model with different Tex and tau | R: Requires Tex[CII]>Tex[CO], CO thick, [CII] tau<~1 | F: Consistent with PDR structure | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Equal excitation temperatures ruled out since they need Tex>~180 K versus CO Tex<~50 K  
  > "the average CO excitation temperatures in the SPT sample are $\lesssim50$ K" (5.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): PDR sizes and molecular gas sizes are rough/uncertain  
  > "The sizes estimated using this method are quite uncertain" (5.2.1)
- Caveat (inferred, ours): Many ALMA lens magnifications assumed from the mean
- Caveat (inferred, ours): Reliance on unpublished comparison data and ATCA fluxes
- Caveat (inferred, ours): Tex/tau degeneracy

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA CO spectra reduction
- Missing: ATCA CO fluxes
- Missing: Comparison sample table
- Missing: APEX spectra
- Data volume (inferred): small (<1 GB for APEX spectra; ALMA part not reprocessed)
- Score (inferred): 2/5, ALMA is only supporting; key inputs unpublished.
- Rediscovery candidate: no, Main data are APEX/Herschel and unpublished inputs.

## Links

- Method: (cite: greve12) (SED fitting)
- Method: (cite: valtchanov11) (SPIRE FTS line extraction)
- Companion: (cite: weiss13) (ALMA redshifts of SPT sources)
- Companion: (cite: hezaveh13) (Lens models)
- Companion: (cite: spilker14) (CO stacking)
- Related: SPT-SZ survey

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 36,
  "rate": 0.462
 },
 "evidence_ok": true
}
```
