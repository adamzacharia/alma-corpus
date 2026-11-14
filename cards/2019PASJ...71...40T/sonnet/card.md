# Environmental impacts on molecular gas in protocluster galaxies at z ∼ 2

`2019PASJ...71...40T` | Publications of the Astronomical Society of Japan 2019 | first author: Tadaki, Ken-ichi | arXiv: 1901.07173 | DOI: 10.1093/pasj/psz005

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do molecular gas fractions and depletion timescales of protocluster galaxies at z~2-2.5 differ from field-galaxy scaling relations, and does this depend on stellar mass?  
  > "A key question is whether the environmental variations in molecular gas properties exceed the time-variations seen in field galaxies." (Introduction)
- Target **PKS1138-262 protocluster**: coordinates _not stated_; z/distance z=2.16  
  > "PKS 1138-262 (PKS1138) at $z=2.16$" (Introduction); distance from _not stated_
- Target **USS1558-003 protocluster**: coordinates _not stated_; z/distance z=2.53  
  > "USS 1558-003 (USS1558) at $z=2.53$" (Introduction); distance from _not stated_
- Target **4C23.56 protocluster**: coordinates _not stated_; z/distance z=2.49  
  > "4C 23.56 (4C23) at $z=2.49$" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00395.S
- bands: Band 3, central frequencies 110 and 98 GHz  
  > "we use the Band-3 receivers with the 64-input correlator in Time Division Mode in a central frequency of 110 and 98 GHz." (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms 125, 90, 97 µJy/beam per 100 km/s (1138-F1, 1558-F1, 1558-F2); 174 µJy/beam for 4C23  
  > "The rms levels are 125 $\mu$Jy beam$^{-1}$, 90 $\mu$Jy beam$^{-1}$, and 97 $\mu$Jy beam$^{-1}$ per 100 km s$^{-1}$ bin." (2.2 ALMA observations)
- time on source: 1.3 hours in PKS1138; 2.4 hours per pointing in USS1558  
  > "On-source time is 1.3 hours in PKS1138 and 2.4 hours per pointing in USS1558." (2.2 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Other facility **Subaru/MOIRCS**: Narrow-band Halpha emitter survey of the protoclusters  
  > "we have made a systematic H$\alpha$ emitter survey with narrow-band filters" (2.1 Halpha emitter survey with Subaru)
- Other facility **Spitzer/MIPS 24 um**: IR luminosities and SFRs of dusty HAEs  
  > "We use a *Spitzer*/MIPS 24 $\mu$m image to identify dusty star formation and estimate total infrared (IR) luminosities of HAEs." (2.2 Stellar mass and star formation rate)
- Other facility **3D-HST**: Catalog used to calibrate J-K color stellar mass relation  
  > "for $\sim$3000 star-forming galaxies at $z=2.1-2.6$ in the 3D-HST catalog" (2.2 Stellar mass and star formation rate)
- Other facility **HiZELS**: Field Halpha emitter mean surface density  
  > "we use a large sample of H$\alpha$ emitters from High-Z Emission Line Survey" (3.1 Target fields)
- External data: Field-galaxy scaling relations of gas fraction and depletion time (667 galaxies)  
  > "establish the scaling relations of gas mass fraction" (Introduction) [from (cite: 2018ApJ...853..179T)]
- External data: 4C23 CO(3-2) ALMA observations covering 21 HAEs  
  > "have made CO(3–2) observations to cover 21 H$\alpha$ emitters with four ALMA pointings." (2.2 ALMA observations) [from (cite: 2017ApJ...842...55L)]
- External data: Halpha dust extinction prediction from stellar mass and EW  
  > "A combination of stellar mass and H$\alpha$ equivalent width predicts the dust extinction level" (2.2 Stellar mass and star formation rate) [from (cite: 2015MNRAS.453..879K)]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA (method not detailed)  
  > "We utilize the Common Astronomy Software Application package (`CASA`; (cite: 2007ASPC..376..127M)) for the data calibration." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We reconstruct clean maps with channel width of 100 km s$^{-1}$, adopting natural weighting." (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 4C23 maps smoothed to match beam sizes for galaxy-integrated fluxes  
  > "We also smooth the maps to match the beam size to for measurements of galaxy-integrated fluxes." (2.2 ALMA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Gas mass estimation method  
  > "We estimate the gas masses in the protocluster galaxies by following the method by (cite: 2018ApJ...853..179T)." (4 Molecular gas properties) [from (cite: 2018ApJ...853..179T)]
- 4C23 cleaned in same way as the other fields  
  > "We make clean maps in the same way as PKS1138 and USS1558 data." (2.2 ALMA observations) [from (cite: 2017ApJ...842...55L)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (calibrators, flagging)
- Synthesized beam sizes (blank in text)
- Clean threshold, masking, image size and cell size
- Exact SFR conversion details and Wuyts template application
- Coefficients of the scaling relations evaluated per galaxy
- Individual galaxy coordinates and catalogs

## Analysis recipe

1. **Estimate stellar masses**: Linear J-K color/K-band relation calibrated on 3D-HST SED masses  
  > "we derive a simple relation by linear fitting (Figure [1](#fig;JK)) as," (2.2 Stellar mass and star formation rate)
   - parameter: J-K clipped to 0.5-2.0; scatter 0.13 dex included in errors  
  > "We set $J-K=0.5$ and 2.0 to the minimum and maximum value" (2.2 Stellar mass and star formation rate)
   - fitting: _not stated_
   - validation: Median offset 0.02 dex, std 0.13 dex vs SED masses  
  > "the median and the standard deviation of differences between single color-based and SED fitting-based stellar masses are 0.02 dex and 0.13 dex, respectively" (2.2 Stellar mass and star formation rate)
2. **Estimate SFRs**: MIPS 24um to LIR with Wuyts templates then Kennicutt; Halpha with dust correction for non-detections  
  > "we use (cite: 2008ApJ...682..985W) templates to avoid the overestimate of SFRs." (2.2 Stellar mass and star formation rate)
   - software: MOPEX
   - parameter: 7 arcsec aperture, aperture correction 2.57  
  > "We use an aperture correction of 2.57 to derive total fluxes" (2.2 Stellar mass and star formation rate)
   - assumption: [NII] correction from mass-metallicity relation; A_Halpha systematic 0.32 mag  
  > "with the systematic uncertainty of 0.32 mag" (2.2 Stellar mass and star formation rate)
   - fitting: _not stated_
   - validation: _not stated_
3. **Detect CO and measure fluxes**: Search >5 sigma peak in 400 km/s binned cubes within 2'' of HAEs; fit single Gaussians; moment-0 over velocities above 15% of Gaussian peak  
  > "We made moment-0 maps in the velocity range where the flux density is above 15 % of the peak of the best-fit Gaussian spectra" (2.3 CO detections)
   - software: CASA
   - parameter: redshift window Δz=±0.02  
  > "in the frequency range expected from the narrow-band redshift ($\Delta z=\pm0.02$)" (2.3 CO detections)
   - fitting: Single Gaussian to spectra  
  > "Fitting the CO (3–2) spectra with single Gaussian function" (2.3 CO detections)
   - validation: Negative 5 sigma search found nothing; simulated spectra with 35 noise spectra give flux ratios 0.97-1.03  
  > "The median values range from 0.97 to 1.03, indicating little systematic boosting effects." (2.3 CO detections)
4. **Derive gas masses, fractions and depletion times**: Convert L'(3-2) to L'(1-0) and apply metallicity-dependent alphaCO; compare with Tacconi scaling relations  
  > "we assume the same CO excitation with $L'_{(1-0)}/L'_{(3-2)}$=1.8" (4 Molecular gas properties)
   - parameter: alphaCO=4.36 f_metal; f_metal=1.1 at logM=11, 1.4 at 10.5; upper limits 5 sigma with 400 km/s  
  > "The correction factor is $f_\mathrm{metal}=1.1$ at $\log(M_\mathrm{star}/M$$)=11$ and $f_\mathrm{metal}=1.4$ at $\log(M_\mathrm{star}/M$$)=10.5$." (4 Molecular gas properties)
   - assumption: Field-like CO excitation, no environmental dependence  
  > "which is a typical value in field galaxies" (4 Molecular gas properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and cleaning of ALMA data  
  > "for the data calibration. We reconstruct clean maps with channel width of 100 km s$^{-1}$" (2.2 ALMA observations)
- **MOPEX** : Mosaicking and photometry of MIPS 24um images  
  > "make mosaic images with a pixel scale of 1.25 arcsec, using MOPEX software" (2.2 Stellar mass and star formation rate)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO-detected galaxies | 16 | not stated | galaxies | 3 | We have detected the CO line from a total of 16 galaxies (4 in PKS1138, 6 in USS1558 and 6 in 4C23). |
| CO detection rate at logMstar>10.5 | 69% (11/16) | not stated | percent | 3 | The CO detection rate is high, 69% (11/16), in the stellar mass range of $\log(M_\mathrm{star}/M$$)>10.5$ |
| CO FWHM range | 180-740 | not stated | km/s | 3 | the line width is over a wide range of FWHM=180–740 km s$^{-1}$ |
| Overdensity in PKS1138 and USS1558 | 121 and 145 | not stated | dimensionless | 0 | typically have overdensities of $\delta =121$ and $145$, respectively |
| f_gas of massive CO-detected galaxies | 0.37-0.53 | not stated | dimensionless | 4 | moderately gas-rich with $f_\mathrm{gas}=0.37-0.53$ |

## Qualitative findings

- Depletion times at 10.5<logM<11.0 exceed scaling relation by 0.5 dex  
  > "the gas depletion timescales are longer than expected from the scaling relation by 0.5 dex" (4 Molecular gas properties)

## Claim tuples

- H: Protocluster galaxies have gas properties differing from field scaling relations | E: ALMA CO(3-2) of HAEs in three protoclusters, compared to Tacconi+18 relations | R: Larger f_gas and longer tau_depl at 10.5<logM<11.0 | F: Gas accretion enhanced in less massive protocluster galaxies | **supported**
- H: Effect depends on stellar mass | E: Same comparison for logM>11 | R: Gas content comparable to or smaller than scaling relation | F: Accretion suppressed in the most massive systems | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Larger sample needed; CO excitation assumed; low-mass detections biased  
  > "although we need a larger sample to verify the scaling relation in high-density environments" (5 Discussion)
- Caveat (inferred, ours): Constant CO(3-2)/(1-0)=1.8 may bias gas masses in dense environments
- Caveat (inferred, ours): Low-mass sample biased to CO-bright, high-SFR galaxies
- Caveat (inferred, ours): Colour-based stellar masses assume field-like relation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Full source table values
- Missing: Subaru and Spitzer catalogs of HAEs
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public ALMA data and clear gas-mass recipe, but imaging details and catalogs are missing.
- Rediscovery candidate: no, Needs unpublished ancillary catalogs (HAE sample, masses, SFRs) and imaging details not given.

## Links

- Method: (cite: 2018ApJ...853..179T) (Scaling relations and gas mass method)
- Companion: (cite: 2017ApJ...842...55L) (Earlier 4C23 CO(3-2) observations)
- Related: MAHALO
- Related: HiZELS
- Related: 3D-HST

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 36,
  "rate": 0.45
 },
 "evidence_ok": true
}
```
