# A high dust emissivity index β for a CO-faint galaxy in a filamentary Lyα nebula at z = 3.1

`2018PASJ...70L...6K` | Publications of the Astronomical Society of Japan 2018 | first author: Kato, Yuta | arXiv: 1807.07933 | DOI: 10.1093/pasj/psy087

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is the dusty galaxy LAB18.b in the SSA22 Lyα nebula LAB18 a typical DSFG, judged from its molecular gas depletion time and dust emissivity index β?  
  > "By combining these values, we can constrain the evolutionary stage of LABs and DSFGs." (Introduction)
- Target **SSA22 LAB18 (LAB18.b)**: coordinates LAB18.b: 22:17:28.94 +00:07:47.0 (J2000)  
  > "Our target is SSA22 LAB18 at R.A. (J2000) = 22h17m29.0s, decl. (J2000) = +00$^\circ$07$'$50$''$ (cite: matsuda04) in the SSA22 protocluster at $z=3.1$" (Introduction); "$z_{\rm{CO(4-3)}}$    |               –               |   $3.093\pm0.001$" (Table 1); z/distance z_CO = 3.093 ± 0.001  
  > "Our target is SSA22 LAB18 at R.A. (J2000) = 22h17m29.0s, decl. (J2000) = +00$^\circ$07$'$50$''$ (cite: matsuda04) in the SSA22 protocluster at $z=3.1$" (Introduction); "$z_{\rm{CO(4-3)}}$    |               –               |   $3.093\pm0.001$" (Table 1); distance from CO J=4-3 line fit from these ALMA data  
  > "Our target is SSA22 LAB18 at R.A. (J2000) = 22h17m29.0s, decl. (J2000) = +00$^\circ$07$'$50$''$ (cite: matsuda04) in the SSA22 protocluster at $z=3.1$" (Introduction); "$z_{\rm{CO(4-3)}}$    |               –               |   $3.093\pm0.001$" (Table 1)

## Data provenance

- ALMA projects: 2016.1.01101.S, 2013.1.00704.S
- bands: Band 3 (CO J=4-3, 2.7 and 3 mm continuum); Band 7 850 um from earlier data  
  > "The ALMA Band 3 observations were carried out through 12th to 14th November 2016" (OBSERVATIONS)
- frequencies and spectral setup: spectral windows ~97–101 GHz and ~109–113 GHz, covering CO J=4-3 for z=3.08–3.23  
  > "The spectral windows were set to $\sim$97–101 GHz and $\sim$109-113 GHz, which covers CO $J=4-3$ line from $z_{\rm{CO}}=3.08-3.23$." (OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–1039 m (~4–290 kλ), 39–41 antennas  
  > "with 39–41 antennas with the baseline lengths of 15–1039 m ($\sim$4–290 k$\lambda$)" (OBSERVATIONS)
- angular resolution: 3 mm beam 1.20"x1.08"; 2.7 mm beam 1.05"x0.98"; CO cube 1.07"x0.99"  
  > "The achieved typical synthesized beam FWHM for CO spectral cube is $1.07\ensuremath{''}\times0.99\ensuremath{''}$ with PA=67$^{\circ}$ at 112.65 GHz." (OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 5.9 uJy/beam (3 mm), 8.7 uJy/beam (2.7 mm)  
  > "The rms noises of the 3 mm and 2.7 mm continuum images are 5.9 $\mu$Jy beam$^{-1}$ and 8.7 $\mu$Jy beam$^{-1}$, respectively." (OBSERVATIONS)
- time on source: ~5 hours  
  > "The total on-source integration time was $\sim$5 hours." (OBSERVATIONS)
- observing dates: 12–14 November 2016  
  > "The ALMA Band 3 observations were carried out through 12th to 14th November 2016" (OBSERVATIONS)
- pi or archival as stated: Cycle 4 project PI Y. Kato; Band 7 data from 2013.1.00704.S via Ao et al. 2018  
  > "We observed the LAB18 in ALMA Cycle 4 project (ID: 2016.1.01101.S; PI: Y. Kato)." (OBSERVATIONS)
- Line: CO J=4-3 (not stated)
- Other facility **Herschel/SPIRE**: 250 um photometry for the SED fit  
  > "fitting a single temperature, optically thin modified black body model to the SPIRE 250 $\mu$m (cite: kato16)" (Dust continuum)
- External data: ALMA Band 7 850 um flux density  
  > "ALMA Band 7 850 $\mu$m ((cite: ao18); Matsuda et al. in prep)" (Dust continuum) [from (cite: ao18); Matsuda et al. in prep]
- External data: SPIRE 250 um flux density and confusion noise  
  > "applied a source confusion noise for photometry error (cite: kato16)" (Dust continuum) [from (cite: kato16)]
- External data: r41 = 0.41 ± 0.07  
  > "we adopted luminous submillimetre galaxies (SMGs) median CO $J=4-3$ luminosity to CO $J=1-0$ luminosity ratio of $r_{41}=0.41\pm0.07$ (cite: bothwell13)" (CO J=4-3 line) [from (cite: bothwell13)]
- External data: kappa_850 = 3.2 cm2/g  
  > "$\kappa_{850}$ is assumed to be $\kappa_{850}=3.2$ cm$^{2}$ g$^{-1}$ (cite: demyk17)" (Dust continuum) [from (cite: demyk17)]

## Processing

### Calibration

- pipeline or manual: pipeline-calibrated data used  
  > "From the calibrated data produced by the pipeline, we made primary beam corrected line free 3 mm and 2.7 mm continuum images" (OBSERVATIONS)
- casa version: CASA 4.7.2  
  > "(CASA; (cite: mcmullin07)) 4.7.2 package in a standard manner" (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 and J0006–0623  
  > "J2148+0657 and J0006–0623 were observed as flux calibrators." (OBSERVATIONS)
- flux scale uncertainty: within 10%  
  > "The accuracy of absolute flux calibration is within 10%." (OBSERVATIONS)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "using clean with natural weighting" (OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using clean with natural weighting" (OBSERVATIONS)
- uv taper: _not stated_
- cell size: 0.1"  
  > "The pixel size is set to $0.1\ensuremath{''}$ for all data." (OBSERVATIONS)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum-subtracted cube with 80 km/s channels  
  > "a continuum subtracted spectral cube with a 80 km s$^{-1}$ velocity resolution" (OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: applied  
  > "we made primary beam corrected line free 3 mm and 2.7 mm continuum images" (OBSERVATIONS)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3 mm 1.20"x1.08" PA 65; 2.7 mm 1.05"x0.98" PA 67  
  > "are $1.20\ensuremath{''}\times1.08\ensuremath{''}$ with PA=65$^{\circ}$ and $1.05\ensuremath{''}\times0.98\ensuremath{''}$ with PA=67$^{\circ}$, respectively." (OBSERVATIONS)
- final rms: 5.9 uJy/beam (3 mm), 8.7 uJy/beam (2.7 mm)  
  > "The rms noises of the 3 mm and 2.7 mm continuum images are 5.9 $\mu$Jy beam$^{-1}$ and 8.7 $\mu$Jy beam$^{-1}$, respectively." (OBSERVATIONS)

### Inherited from earlier work

- ALMA 850 um continuum data and SPIRE 250 um photometry taken from earlier work  
  > "ALMA Band 7 850 $\mu$m ((cite: ao18); Matsuda et al. in prep)" (Dust continuum) [from (cite: ao18); (cite: kato16)]
- CO luminosity computed following Solomon & Vanden Bout  
  > "Following (cite: solomon05), we estimated the CO $J=4-3$ luminosity" (CO J=4-3 line) [from (cite: solomon05)]

### Not stated but needed to reproduce (our reading)

- line-free channel ranges used for continuum
- CLEAN threshold, masks and iterations
- imfit regions and fitting setup
- SED fitting code, priors and grid
- rest frequency used for the L'CO conversion
- Band 7 850 um flux density and SPIRE 250 um flux values
- how the 2013.1.00704.S data were reduced

## Analysis recipe

1. **Image continuum and CO cube**: CASA clean with natural weighting on pipeline-calibrated data; 3 mm and 2.7 mm line-free continuum and continuum-subtracted cube at 80 km/s  
  > "using clean with natural weighting" (OBSERVATIONS)
   - software: CASA
   - parameter: pixel 0.1"  
  > "The pixel size is set to $0.1\ensuremath{''}$ for all data." (OBSERVATIONS)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO line and flux**: Single Gaussian fit to the spectrum for z_CO; imfit on the integrated map with primary beam correction for flux  
  > "We measured the total flux density of CO $J=4-3$ by using imfit task of CASA on the spectrally integrated flux map with primary beam correction." (CO J=4-3 line)
   - software: CASA imfit
   - fitting: single Gaussian for redshift  
  > "The derived systemic redshift is $z_{\rm{CO}}=3.093\pm0.001$ by using single Gaussian fitting" (CO J=4-3 line)
   - validation: two-component Gaussian fit to spectrum gave no significant change  
  > "We checked the total flux density of CO $J=4-3$ by using two components Gaussian fitting on the spectrum data, and found that the result does not significantly change." (CO J=4-3 line)
3. **Derive molecular gas mass**: M_gas = r41 * alpha_CO * L'CO(4-3)  
  > "$M_{\rm{gas}}=r_{41}\alpha_{\rm{CO}}L'_{\rm{CO(4-3)}}$" (CO J=4-3 line)
   - assumption: r41=0.41±0.07, alpha_CO=0.8 (starburst/merger)  
  > "starbursts and mergers conversion factor of $\alpha_{\rm{CO}}=0.8$ $M_{\rm{\odot}}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: downes98)" (CO J=4-3 line)
   - fitting: _not stated_
   - validation: Galactic alpha=4.36 would raise gas mass by factor five  
  > "the molecular gas mass increases by a factor of five given the so-called Galactic conversion factor" (CO J=4-3 line)
4. **Fit dust SED for T_d, beta, L_IR**: Single-temperature optically thin modified blackbody chi2 fit to SPIRE 250 um, ALMA 850 um, 2.7 mm, 3 mm  
  > "fitting a single temperature, optically thin modified black body model to the SPIRE 250 $\mu$m (cite: kato16)" (Dust continuum)
   - assumption: 10% flux calibration error on Band 7  
  > "The accuracy of the ALMA Band 7 850 $\mu$m absolute flux calibration is evaluated to be within 10%" (Dust continuum)
   - fitting: chi2 fit, 68% confidence intervals  
  > "These errors show 68% confidence intervals of the $\chi^2$ SED fits to the photometry data." (Dust continuum)
   - validation: re-fit with SPIRE flux reduced by factor three: Td=24.1, beta=2.6  
  > "the best-fit results are $T_{\rm{d}}=24.1\pm1.3$ K, $\beta=2.6\pm0.1$" (Dust continuum)
5. **Derive SFR, dust mass, GDR, depletion time**: SFR=1.0e-10 L_IR (Kennicutt98, Chabrier IMF); dust mass from 3 mm flux with kappa_850=3.2; tau_dep = M_gas/SFR  
  > "SFR=$1.0\times10^{-10} \it{L}_{\rm{IR}}$" (Dust continuum)
   - assumption: kappa_850 = 3.2 cm2/g  
  > "$\kappa_{850}$ is assumed to be $\kappa_{850}=3.2$ cm$^{2}$ g$^{-1}$ (cite: demyk17)" (Dust continuum)
   - fitting: _not stated_
   - validation: kappa_850=1.0 gives dust mass 3x larger, GDR ≈30  
  > "if we adopt $\kappa_{850}=1.0$ cm$^{2}$ g$^{-1}$, the dust mass increases by a factor of three" (DISCUSSION AND SUMMARY)

## Software

- **CASA** 4.7.2: data reduction, clean imaging, imfit flux measurement  
  > "(CASA; (cite: mcmullin07)) 4.7.2 package in a standard manner" (OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| z_CO | 3.093 | 0.001 | dimensionless | 2 | systemic $z_{\rm{CO}}=3.093\pm0.001$ |
| L'CO(4-3) | 2.3e9 | 0.2e9 | K km/s pc^2 | 2 | $L'_{\rm{CO(4-3)}}=(2.3\ \pm\ 0.2)\times10^9$ K km s$^{-1}$ pc$^2$ |
| M_gas | 4.4e9 | +0.9/-0.6 e9 | Msun | 3 | $M_{\rm{gas}} = (4.4^{+0.9}_{-0.6}) \times 10^9\, M_{\rm{\odot}}$ |
| beta | 2.3 | 0.2 | dimensionless | 4 | $\beta=2.3 \pm 0.2$ |
| T_dust | 31.7 | 4.1 | K | 4 | $T_{\rm{d}}= 31.7 \pm 4.1$ K |
| L_IR | 2.7e12 | 1.6e12 | Lsun | 4 | $L_{\rm{IR}}=(2.7\pm1.6)\times10^{12}\,L_{\rm{\odot}}$ |
| SFR | 269 | 158 | Msun/yr | 5 | SFR$=269\pm158$ $M_{\rm{\odot}}$ yr$^{-1}$ |
| dust mass | 4.8e7 | 0.8e7 | Msun | 5 | $M_{\rm{d}}=(4.8\pm0.8)\times10^{7}\,M_{\rm{\odot}}$ |
| gas-to-dust ratio | 93 | +19/-14 | dimensionless | 5 | $\delta_{\rm{GDR}}=93^{+19}_{-14}$ |
| tau_dep | 17 | 10 | Myr | 5 | $\tau_{\rm{dep}}=17\pm10$ Myr |

## Qualitative findings

- LAB18.b has low L'CO/L_IR relative to z>1 DSFGs and lies between local ULIRGs and gas-poor early-type galaxies in the beta diagram.  
  > "LAB18.b is located between local ULIRGs (cite: clements18) and local gas-poor, early-type galaxies (cite: cortese14)." (DISCUSSION AND SUMMARY)

## Claim tuples

- H: Is LAB18.b a typical DSFG? | E: CO J=4-3 luminosity and SED-based L_IR and SFR compared with DSFG/ULIRG samples | R: L'CO is one order of magnitude lower; tau_dep=17±10 Myr vs 100-200 Myr | F: LAB18.b is not a typical DSFG but is in transition to a gas-poor early-type galaxy | **supported**
- H: Does LAB18.b have a high dust emissivity index? | E: Modified blackbody fit from SPIRE to ALMA Band 3 | R: beta=2.3±0.2 (2.6±0.1 with reduced SPIRE flux) | F: beta is high, similar to local gas-poor early-type galaxies, and consistent with Mg-rich amorphous silicates | **supported**

## Reasoning

- Why this data: LAB18 is the brightest at 850 um among SSA22 LABs, making it the best target.  
  > "Since LAB18 is the brightest at 850 $\mu$m among the LABs in the SSA22 protocluster, this source is the best target" (Introduction)
- Why this method: _not stated_
- Alternative: Galactic alpha_CO=4.36 would increase gas mass by a factor five; alpha=0.8 adopted for comparable IR luminosity  
  > "since LAB18.b has a comparable IR luminosity" (CO J=4-3 line)
- How they decided it was enough: _not stated_
- Limitation (authors): SPIRE 250 um photometry could be overestimated due to blending with other ALMA sources.  
  > "We note the SPIRE 250 $\mu$m photometry could be overestimated because of source blending with other ALMA 850 $\mu$m sources." (Dust continuum)
- Limitation (authors): Beam is larger than the offset between the red and blue CO components.  
  > "while the beam FWHM is significantly larger than the offset" (CO J=4-3 line)
- Caveat (inferred, ours): Only four SED points with three free parameters; beta degenerate with Td
- Caveat (inferred, ours): beta and dust mass depend on the single high kappa_850 assumed
- Caveat (inferred, ours): alpha_CO and r41 are assumed, not measured
- Caveat (inferred, ours): Single source, so conclusions about LABs are not general

## Reproducibility

- Data public (paper): ALMA project codes given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016,1.01101.S, ADS/JAO.ALMA#2013.1.00704.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: SED photometry values for SPIRE and Band 7
- Missing: SED fitting code details
- Missing: CLEAN parameters and masks
- Data volume (inferred): ~50-100 GB for Band 3 raw data; Band 7 additional
- Score (inferred): 3/5, Short letter with clear derived quantities and public data, but missing imaging and fitting details and input photometry.
- Rediscovery candidate: yes, Public ALMA data, simple recipe and numeric results (z_CO, L'CO, M_gas, beta), though SED inputs must come from other papers.

## Links

- Method: (cite: solomon05) (CO luminosity definition)
- Method: (cite: kennicutt98) (L_IR-SFR relation)
- Companion: (cite: ao18) (ALMA 850 um observations of LAB18)
- Companion: (cite: kato16) (SPIRE 250 um photometry)
- Related: SSA22 protocluster

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 52,
  "rate": 0.703
 },
 "evidence_ok": true
}
```
