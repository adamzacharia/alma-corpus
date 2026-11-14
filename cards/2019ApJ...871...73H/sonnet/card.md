# AT2018cow: A Luminous Millimeter Transient

`2019ApJ...871...73H` | The Astrophysical Journal 2019 | first author: Ho, Anna Y. Q. | arXiv: 1810.10880 | DOI: 10.3847/1538-4357/aaf473

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: transients
- Question: What are the properties of the shock and the origin of the X-ray emission in the luminous millimeter transient AT2018cow?  
  > "A basic interpretation of the data suggests $E_k \gtrsim \mbox{$\rm 4 \times 10^{48}\,\mbox{$\rm erg$}$}$ coupled to a fast but sub-relativistic ($v \approx \mbox{$\rm 0.13c$}$) shock" (abstract)
- Target **AT2018cow**: coordinates _not stated_; z/distance d = 60 Mpc  
  > "AT2018cow was discovered on 2018 June 16 UT as an optical transient" (1.2 AT2018cow); "its close proximity ($d=60\,$Mpc)" (1.2 AT2018cow); distance from _not stated_

## Data provenance

- ALMA projects: 2017.A.00047.T
- bands: Bands 3, 4, 7, 8, 9  
  > "AT2018cow was observed with ALMA as part of DD time during Cycle 5 using Bands 3, 4, 7, 8, and 9." (2.1.3 ALMA)
- frequencies and spectral setup: 2SB 4 GHz each sideband centered 91.5/103.5, 138/150, 337.5/349.5, 399/411 GHz; Band 9 DSB 8 GHz at 663 and 679 GHz  
  > "The Band 9 observations used double-sideband (DSB) receivers with 8 $\rm GHz$ bandwidth" (2.1.3 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1, 46-48 antennas, baselines 12-312 m  
  > "The ALMA 12-m antenna array was in its most compact C43-1 configuration, with 46–48 working antennas and baselines ranging from 12–312 m." (2.1.3 ALMA)
- baselines: _not stated_
- angular resolution: 3.3"x2.5" (Band 3) to 0.50"x0.36" (Band 9)  
  > "with a synthesized beam that ranges from $3.3\ensuremath{''}\,\times\,2.5$$''$ ($\mathrm{PA}=29^{\circ}$) in Band 3" (2.1.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 6-8 min for Bands 3-8; 40 min for Band 9  
  > "The on-source integration time was 6–8 min for Bands 3–8, and 40 min for Band 9." (2.1.3 ALMA)
- observing dates: 30 June, 8 July, 10 July 2018  
  > "Observations were performed on 30 June 2018 ($\Delta t\approx14\,\mbox{$\rm days$}$; Bands 7 and 8)" (2.1.3 ALMA)
- pi or archival as stated: Director's discretionary time  
  > "This finding led us to seek Director’s discretionary (DD) time with ALMA" (1.2 AT2018cow)
- Other facility **SMA**: 230 and 340 GHz light curves, Compact configuration  
  > "Observations took place over the period of UT 2018 Jun 21–UT 2018 August 3" (2.1.1 SMA)
- Other facility **ATCA**: 5-34 GHz centimeter observations  
  > "We obtained six epochs of centimeter-wavelength observations" (2.1.2 ATCA)
- Other facility **Swift/XRT**: X-ray light curves  
  > "We downloaded the *Swift*/XRT data products (light curves and spectra)" (2.2.1 Swift/XRT)
- Other facility **NuSTAR**: Four epochs of hard X-ray spectra  
  > "*NuSTAR* observed AT2018cow on four epochs" (2.2.2 NuSTAR)
- External data: UVOIR bolometric luminosity and spectral evolution  
  > "the bolometric luminosity as measured in the UVOIR is $5 \times 10^{42}\,\mbox{$\rm erg\,s^{-1}$}$ (cite: Perley2018)" (3.2) [from (cite: Perley2018)]
- External data: Peak frequencies/luminosities of other transients  
  > "we use the report in (cite: Soderberg2010) that from their first spectrum at $\Delta t = 20\,\mbox{$\rm days$}$" (Appendix) [from (cite: Soderberg2010)]

## Processing

### Calibration

- pipeline or manual: Bands 3-8 standard ALMA pipeline; Band 9 manual calibration by NA ALMA Science Center  
  > "The data in Bands 3–8 were calibrated with the standard ALMA pipeline" (2.1.3 ALMA); "Band 9 observations were delivered following manual calibration by the North American ALMA Science Center" (2.1.3 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1337-1257 (B7), J1550+0527 (B3/4), J1517-2422 (B8, B9)  
  > "using J1337$-$1257 (Band 7), J1550+0527 (Band 3/4) or J1517$-$2422 (Band 8) to calibrate the bandpass response and apply an absolute flux scale" (2.1.3 ALMA)
- flux scale uncertainty: ~5% Bands 3,4; 10% Bands 7,8; 20% Band 9  
  > "ALMA measurements have roughly 5% uncertainties in Bands 3 and 4, 10% uncertainties in Bands 7 and 8, and a 20% uncertainty in Band 9." (Table 1)
- self calibration: Phase-only self-cal on target for Bands 3-8; none for Band 9  
  > "We subsequently applied a phase-only self-calibration using the target source (for Bands 3–8)" (2.1.3 ALMA); "Therefore, we did not apply a self-calibration to the Band 9 data." (7 ALMA Band 9 Calibration)

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
- primary beam correction: flux-corrected for primary beam response  
  > "performed a deconvolution, imaged the data, and flux-corrected for the response of the primary beam" (2.1.3 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.3"x2.5" (PA 29) Band 3 to 0.50"x0.36" (PA -46) Band 9; unresolved source  
  > "AT2018cow is unresolved in our ALMA data" (2.1.3 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Time zero-point MJD 58285  
  > "from the zero-point MJD 58285 (following (cite: Perley2018))" (2 Observations) [from (cite: Perley2018)]
- Synchrotron shock framework (R, B, U formulas)  
  > "adopt the framework in (cite: Chevalier1998) (hereafter referred to as C98) to estimate properties of the shock at this epoch" (3.2) [from (cite: Chevalier1998)]
- epsilon_e=epsilon_B=1/3 convention  
  > "we follow (cite: Soderberg2010) in setting $\epsilon_e=\epsilon_B=1/3$" (3.2) [from (cite: Soderberg2010)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Self-calibration solution interval and imaging parameters (weighting, cell size, image size, masking)
- Method and aperture used to measure ALMA flux densities
- Details of Monte Carlo uncertainties beyond input percentages
- Position of AT2018cow

## Analysis recipe

1. **Measure multi-band flux densities**: Point-source fluxes from calibrated SMA/ATCA/ALMA data; ALMA via imaging after self-cal  
  > "AT2018cow is unresolved in our ALMA data" (2.1.3 ALMA)
   - software: CASA, MIRIAD
   - fitting: _not stated_
   - validation: Band 9 checked by splitting in time, uv-range, polarization; calibrators compared with catalog  
  > "The change in flux density between the different time-bins was within 6$\%$." (7 ALMA Band 9 Calibration)
2. **Derive shock properties from SED peak on Day 22**: Chevalier (1998) equations with nu_p=nu_a, F_p, p=3.2 mapped to p=3 constants  
  > "we assume that $\nu_p = \nu_a$, and adopt the framework in (cite: Chevalier1998) (hereafter referred to as C98)" (3.2)
   - parameter: nu_p ≈ 100 GHz, F_p ≈ 94 mJy, f=0.5  
  > "find $\nu_p \approx \mbox{$\rm 100\,GHz$}$ and $F_p \approx \mbox{$\rm 94\,mJy$}$" (3.2)
   - assumption: eps_e=eps_B=1/3, d=60 Mpc, f=0.5  
  > "Following C98 we take $f=0.5$" (3.2)
   - fitting: Monte Carlo of 10,000 samples with 10% errors on F_p, nu_p and 50% on p  
  > "a Monte Carlo with 10,000 samples gives uncertainties of 0.15–0.3 dex in these derived parameters" (3.2)
   - validation: _not stated_
3. **Compare with other transients and test X-ray origin**: Rederive velocity-energy using same equations for other events; compare IC and synchrotron extrapolations to X-rays  
  > "we take the peak frequency, peak luminosity, and peak time for each event, and run them through the same equations" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA calibration and imaging  
  > "All calibration and imaging was done with the Common Astronomical Software Applications (CASA; (cite: mcmullin2007))." (2.1.3 ALMA)
- **MIRIAD** : SMA imaging and ATCA reduction; imfit  
  > "The data were reduced and calibrated using standard techniques implemented in the MIRIAD software" (2.1.2 ATCA)
- **XSPEC** v12.10.0c: NuSTAR spectral fitting  
  > "Spectra were analysed in XSPEC (v12.10.0c)" (2.2.2 NuSTAR)
- **HEASOFT** 6.24: NuSTAR data extraction  
  > "*NuSTAR* data were extracted using `nustardas_06Jul17_v1` from HEASOFT 6.24." (2.2.2 NuSTAR)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak frequency Day 22 | 100 | not stated | GHz | 2 | find $\nu_p \approx \mbox{$\rm 100\,GHz$}$ and $F_p \approx \mbox{$\rm 94\,mJy$}$ |
| Shock radius | 7e15 | 0.15–0.3 dex | cm | 2 | $R_p \approx \mbox{$\rm 7 \times 10^{15}\,\mbox{$\rm cm$}$}$ and $B_p \approx \mbox{$\rm 6\,\mbox{$\rm G$}$}$ |
| Total energy U | 4e48 | 0.15–0.3 dex | erg | 2 | We find that the total energy $U \approx \mbox{$\rm 4 \times 10^{48}\,\mbox{$\rm erg$}$}$. |
| Mean velocity | 0.13 | not stated | c | 2 | is $v=R_p/t_p=\mbox{$\rm 0.13c$}$ |
| Electron density | 3e5 | not stated | cm^-3 | 2 | $n_e \approx \mbox{$\rm 3 \times 10^{5}\,\mbox{$\rm cm^{-3}$}$}$ |
| Optically thin spectral index Day 22 | -1.1 | not stated | dimensionless | 2 | On Day 22, we measure $\alpha=-1.1$ where $F_\nu \propto \nu^{\alpha}$, which corresponds to $p=3.2$. |
| Brightness temperature | >=3e10 | not stated | K | 1 | \gtrsim 3 \times 10^{10}\,\mbox{$\rm K$} |

## Qualitative findings

- X-ray emission is not explained by extension of the synchrotron spectrum or by IC of UVOIR photons; a central engine is invoked  
  > "Taken together, we are led to invoke an additional source of X-ray emission: the central engine of the event." (abstract)

## Claim tuples

- H: Is the radio-mm emitting shock sub-relativistic and in a dense medium? | E: Day 22 ALMA SED peak with Chevalier framework | R: v=0.13c, n_e=3e5 cm^-3, U=4e48 erg | F: Sub-relativistic shock into dense medium | **supported**
- H: Can the X-rays arise from IC scattering or synchrotron extension? | E: Compare energy densities and extrapolated spectrum with X-ray data | R: X-ray 25x brighter than extrapolation, flatter index, L_X/L_radio >~30 | F: Additional X-ray source needed | **supported**

## Reasoning

- Why this data: Bright, still-rising submm emission motivated DD time at higher frequencies to resolve the SED peak  
  > "which enabled us to resolve the peak of the SED" (1.2 AT2018cow)
- Why this method: _not stated_
- Alternative: IC scattering of UVOIR photons and synchrotron extension rejected for X-rays  
  > "We conclude that the X-ray emission during the plateau phase does not naturally arise from IC scattering of the UVOIR source" (5)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 9 excess is only 2 sigma  
  > "the apparent excess in the Band 9 flux is only 2$\sigma$" (6 Conclusions)
- Caveat (inferred, ours): Energy depends strongly on assumed epsilon_e, epsilon_B
- Caveat (inferred, ours): Peak frequency from few ALMA points
- Caveat (inferred, ours): Equating nu_p with nu_a assumed

## Reproducibility

- Data public (paper): Code released; ALMA data cited by project code  
  > "The code used to produce the results described in this paper was written in Python and is available online in an open-source repository" (6 Conclusions)
- Products in archive: _not stated_
- Code: https://github.com/annayqho/AT2018cow  
  > "https://github.com/annayqho/AT2018cow" (footnote 8)
- Missing: CASA version
- Missing: imaging parameters
- Missing: flux extraction method
- Data volume (inferred): ~tens of GB for ALMA DD data
- Score (inferred): 3/5, Flux table and equations given, but ALMA imaging details missing
- Rediscovery candidate: yes, Public DD data, analytic recipe, numeric results; imaging details partly missing.

## Links

- Method: (cite: Chevalier1998) (Synchrotron self-absorption shock framework)
- Companion: (cite: Perley2018) (UVOIR observations of AT2018cow)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
