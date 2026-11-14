# An observational study of dust nucleation in Mira (o Ceti). I. Variable features of AlO and other Al-bearing species

`2016A&A...592A..42K` | Astronomy and Astrophysics 2016 | first author: Kamiński, T. | arXiv: 1604.05641 | DOI: 10.1051/0004-6361/201628664

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, astrochemistry
- Question: Identify and characterize aluminum bearing species in the circumstellar gas of Mira (o Ceti) to elucidate their role in the production of Al2O3 dust.  
  > "Identify and characterize aluminum bearing species in the circumstellar gas of Mira ($o$ Ceti) in order to elucidate their role in the production of Al$_2$O$_3$ dust." (abstract)
- Target **Mira (o Ceti)**: coordinates _not stated_; z/distance 107 pc  
  > "This is equivalent to 2.4$\times$10$^{13}$ cm or 331 R$_{\ensuremath{\odot}}$ at the distance of 107 pc to the star (cite: distance)." (1.1 o Ceti); distance from Knapp et al. 2003 (cite: distance)  
  > "This is equivalent to 2.4$\times$10$^{13}$ cm or 331 R$_{\ensuremath{\odot}}$ at the distance of 107 pc to the star (cite: distance)." (1.1 o Ceti)

## Data provenance

- ALMA projects: 2011.0.00014.SV, 2013.1.00047.S, 2012.1.00524.S, 2013.1.00156.S
- bands: Band 7 (9-8 line); SV continuum-mode data covering 6-5 near 230 GHz  
  > "Mira was observed by ALMA again in Band 7 on 21 July 2015 reaching the best resolution and sensitivity so far at these wavelengths." (2.3 ALMA)
- frequencies and spectral setup: 2015: four ranges 342.1–344.0, 344.1–346.0, 354.2–356.1, 356.1–358.0 GHz at 0.98 km/s  
  > "The spectra cover four ranges, 342.1–344.0, 344.1–346.0, 354.2–356.1, and 356.1–358.0 GHz at a resolution of 0.98 km s$^{-1}$." (2.3 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 2015: 42 antennas, baselines 15–1574 m  
  > "The observations with 42 antennas of the 12-m array arranged on baselines between 15 and 1574 m resulted in an angular resolution of about 0.158$''$$\times$0.127$''$ near the line of AlO." (2.3 ALMA)
- baselines: _not stated_
- angular resolution: SV ~34x24 mas; 2015 0.158x0.127''; June 2014 0.34x0.32''  
  > "These high angular-resolution observations with a beam of about 34$\times$24 mas are the most detailed observations of Mira to date." (2.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 29 Oct/1 Nov 2014 (SV); 24 Feb, 3 May, 12/14/15 Jun 2014; 21 Jul 2015  
  > "The observations were obtained twice, on 24 Feb. 2014 and 3 May 2014, in nearly the same frequency setup but with different array configurations" (2.3 ALMA)
- pi or archival as stated: SV data, archival Ramstedt et al. and Planesas et al. data, plus own 2015 observations  
  > "Because these data were originally collected for the purpose of our study here, they are described in greater detail than the earlier ALMA observations." (2.3 ALMA)
- Line: AlO N=6-5 (229.67025503 GHz)
- Line: AlO N=9-8 (344.45177512 GHz)
- Other facility **APEX (FLASH+, HET230)**: Multi-epoch AlO and AlOH rotational lines  
  > "Mira was observed in 13–14 August 2013 and 30 June–8 July 2014 using the dual-band FLASH+ receiver at APEX." (2.1 APEX/FLASH)
- Other facility **Herschel/HIFI**: AlO 29-28 and AlOH lines from archive  
  > "Here, we analyze only one spectrum which covers the $N$=29–28 line of AlO." (Herschel/HIFI)
- Other facility **Optical echelle archives**: Multi-epoch optical spectra 1965–2012 for AlO, AlH, Al I  
  > "we performed an extensive search for archival spectra and literature data." (4.1 Optical observations)
- External data: AlO line frequencies  
  > "The line frequencies were taken from (cite: YamadaAlO)." (3.1 Identification of AlO) [from (cite: YamadaAlO)]
- External data: Collision rates for AlO scaled from SiO and He  
  > "we used the scaled collision-rate coefficients derived for SiO and He (cite: collRates)" (3.5 Excitation analysis) [from (cite: collRates)]
- External data: Wind terminal velocity and mass-loss from CO modelling  
  > "we constructed a model of the Mira’s wind which strongly disfavors the low terminal velocity and here we adopt $\varv_{\infty}$=5 km s$^{-1}$" (1.2) [from (cite: mira_co)]

## Processing

### Calibration

- pipeline or manual: Archive 2014 Band 7 data reduced with standard pipeline; self-calibration applied  
  > "From the ALMA archive, we extracted the raw data obtained with the 12-m array only and reduced them with the standard pipeline." (2.3 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 2015: J0238+166 (second block via bandpass calibrator J0224+0659)  
  > "The calibrators were J0224+0659 for bandpass, J0217+0144 for phase, and J0238+166 for flux calibration." (2.3 ALMA)
- flux scale uncertainty: Feb 2014 <5% (Ganymede); other secondary calibrators ~15%  
  > "whose fluxes are known to within 15%." (2.3 ALMA)
- self calibration: Iterative phase and amplitude self-cal on continuum channels  
  > "we performed extra optimization of phase and amplitude using an iterative self-calibration procedure performed on channels dominated by continuum emission." (2.3 ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (uniform and natural for reference)  
  > "All the ALMA data were imaged with Briggs weighting with the robust parameter set to 0.5." (2.3 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: 6-5 data imaged in CLEAN after continuum subtraction  
  > "we present only the data processed in CLEAN after continuum subtraction which have a better S/N" (Appendix: Processing of the interferometric data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SV data description and processing  
  > "The data are described in detail in (cite: wong)" (2.3 ALMA) [from (cite: wong)]
- June 2014 observations described elsewhere  
  > "The observations are described in (cite: planesas)." (2.3 ALMA) [from (cite: planesas)]
- Herschel AlO detection with same setup as VY CMa  
  > "This line was detected using the same instrumental setup as in VY CMa (cite: vy_hifi)." (3.1) [from (cite: vy_hifi)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Line-free channels and continuum subtraction ranges
- Self-calibration solution intervals
- Image size, cell size, clean threshold and masks
- Mask/threshold for 3 sigma integrated-flux regions
- Ganymede/other calibrator flux models
- Which flux values were used for each epoch's flux equalization

## Analysis recipe

1. **Image AlO emission**: Image each epoch (CLEAN after continuum subtraction), integrate line to make maps  
  > "Figure 3 presents a map of the continuum-subtracted and profile-integrated flux in the line" (3.2 Location and extent)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "All the ALMA data were imaged with Briggs weighting with the robust parameter set to 0.5." (2.3 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit source size/offset and radial profile**: Gaussian fits to integrated maps; azimuthally averaged radial profile around continuum peak  
  > "A Gaussian fit to the profile-integrated map of AlO(9–8) gives a source size of 123$\times$74 mas ($\pm$6 mas) at PA=95.1$^\circ$$\pm$5.3$^\circ$." (3.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure line velocity and width**: Cross-correlate spectrum with simulated hyperfine profile; chi2 testing  
  > "The central velocity was derived by cross-correlating the spectrum with the simulation in the `rv.fxor` task of IRAF and additional $\chi^2$ model testing was performed in CASSIS" (3.3)
   - software: IRAF, CASSIS
   - fitting: Gaussian hyperfine components with intensity proportional to S_i  
  > "each hyperfine component was represented by a Gaussian of intensity proportional to the component’s strength, $S_i$." (3.3)
   - validation: Consistent with systemic velocity  
  > "The central velocity of $N$=9$\to$8 is consistent to within the uncertainties with the center-of-mass velocity of Mira" (3.3)
4. **Excitation analysis and column density**: Population diagram with weighted least squares; RADEX non-LTE check  
  > "The physical conditions of the AlO-bearing gas were constrained by using a population-diagram (cite: popdiagr)." (3.5)
   - software: RADEX
   - parameter: Source size 0.12'' FWHM for beam filling  
  > "we assumed a source size equal to a circular Gaussian of 0.12$''$ FWHM." (3.5)
   - assumption: Optically thin, isothermal, LTE  
  > "it was assumed that the lines are optically thin and arise in isothermal gas under local thermodynamic equilibrium (LTE) conditions." (3.5)
   - fitting: Weighted linear regression; upper limits and two low 9-8 points excluded  
  > "We obtain a linear fit to the remaining points using a weighted least-square regression procedure." (3.5)
   - validation: RADEX with N=6e15 fits best ALMA fluxes  
  > "a RADEX model with a slightly higher column density, $N$(AlO)=6$\cdot$10$^{15}$ cm$^{-2}$, which fits the fluxes of our best ALMA measurements very well." (3.5)

## Software

- **CASA** : Implied by CLEAN imaging; not named explicitly  
  > "we found significant differences in the depth and shape of absorption features when processed in CLEAN with continuum and after continuum subtraction." (Appendix: Processing of the interferometric data for the AlO 6→5 line)
- **IRAF** : rv.fxcor cross-correlation and optical echelle reduction  
  > "cross-correlating the spectrum with the simulation in the `rv.fxor` task of IRAF" (3.3)
- **CASSIS** : chi2 model testing of AlO profile  
  > "additional $\chi^2$ model testing was performed in CASSIS" (3.3)
- **RADEX** : non-LTE radiative transfer for AlO  
  > "performing additional calculations with the radiative-transfer code RADEX (cite: radex)" (3.5)
- **PGOPHER** : simulating AlH A-X band  
  > "A detailed simulation of the $A$–$X$ band was obtained in `pgopher` (cite: pgopher)" (4.2 AlH)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AlO excitation temperature | 329 | ±51 | K | 4 | $T_{\rm ex}$=329$\pm$51 K and a column density of $N$(AlO)=(4.0$\pm$0.6)$\times$10$^{15}$ cm$^{-2}$. |
| AlO column density | 4.0e15 | ±0.6e15 | cm^-2 | 4 | $T_{\rm ex}$=329$\pm$51 K and a column density of $N$(AlO)=(4.0$\pm$0.6)$\times$10$^{15}$ cm$^{-2}$. |
| AlO V_LSR (9-8, 2015) | 46.9 | ±0.1 | km/s | 3 | This yielded a radial velocity $V_{\rm LSR}$=46.9$\pm$0.1 km s$^{-1}$ and intrinsic line width (FWHM) in the range 8–14 km s$^{-1}$. |
| AlO 9-8 source size | 123x74 mas, PA 95.1 | ±6 mas | mas | 2 | A Gaussian fit to the profile-integrated map of AlO(9–8) gives a source size of 123$\times$74 mas ($\pm$6 mas) at PA=95.1$^\circ$$\pm$5.3$^\circ$. |
| AlOH excitation temperature | 1960 | ±170 | K | 0 | the emission features imply a temperature of 1960$\pm$170 K (assuming a source size of 0.2$''$) |
| AlO abundance | 1e-9 to 1e-7 | order of magnitude | relative to H2 | 4 | We derive an average AlO abundance of 10$^{-9}$–10$^{-7}$ with a high uncertainty |

## Qualitative findings

- AlO emission is clumpy, absorption seen against the stellar disk, infall of 4–7 km/s suggested  
  > "we imply that the AlO gas captured by the observations is most likely infalling on Mira with a typical velocity of about 4–7 km s$^{-1}$." (3.4 Interpretation)

## Claim tuples

- H: Which Al species are observable in Mira? | E: Multi-facility submm/FIR/optical spectroscopy | R: AlO, AlOH, AlH and Al I detected; AlF, AlCl etc. not | F: AlH, AlO, AlOH, Al I trace gas-phase aluminum | **supported**
- H: Is AlO variable? | E: Multi-epoch ALMA/APEX and optical data | R: Flux changes by factor of a few, erratic, uncorrelated with phase | F: AlO is strongly irregularly variable | **supported**
- H: Is AlO depleted onto dust? | E: Radial profiles of ALMA 6-5 map | R: Average profile shows no depletion beyond 3 R*; one cut shows a deficit | F: No strong proof for global depletion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot trace Al depletion quantitatively; LTE assumption likely violated  
  > "We are unable to quantitatively trace aluminum depletion from the gas" (abstract)
- Caveat (inferred, ours): Population diagram mixes epochs of a variable source and excludes points subjectively
- Caveat (inferred, ours): Abundance uncertain by orders of magnitude due to unknown H2
- Caveat (inferred, ours): ALMA 6-5 absorption/emission CLEAN artefacts

## Reproducibility

- Data public (paper): ALMA archival data and SV data used; project codes listed  
  > "From the ALMA archive, we extracted the raw data obtained with the 12-m array only" (2.3 ALMA)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Line-free channels
- Missing: Self-cal parameters
- Missing: Imaging parameters
- Data volume (inferred): Several hundred GB raw across four ALMA projects
- Score (inferred): 3/5, ALMA data archival but processing details are sparse; main results partly numeric.
- Rediscovery candidate: no, Recipe lacks imaging details and relies on multi-facility non-ALMA data.

## Links

- Method: Wong et al. 2016 (cite: wong) (SV data and CLEAN absorption issue)
- Companion: (cite: planesas) (describes June 2014 ALMA data)
- Related: ALMA 2014 Long Baseline Campaign SV
- Related: HIFISTARS

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
