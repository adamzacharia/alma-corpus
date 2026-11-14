# Resolving Twin Jets and Twin Disks with JWST and ALMA: The Young WL 20 Multiple System

`2024ApJ...973...42B` | The Astrophysical Journal 2024 | first author: Barsony, Mary | arXiv: 2409.03016 | DOI: 10.3847/1538-4357/ad5da1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the jets, disks and outflow gas in the WL 20 multiple system, and what is the system's evolutionary stage, as seen with JWST MIRI MRS and ALMA?  
  > "we have acquired JWST MIRI MRS integral field unit imaging spectroscopy encompassing all three components, covering the 5 $-$ 28 $\mu$m wavelength range, supplemented by high-resolution ALMA data." (Introduction)
- Target **WL 20 (E, W, SW, SE)**: coordinates 16h27m15.77s, -24d38m44.3s (MIRI pointing center)  
  > "$\alpha_{2000}$ $=$ 16h 27m 15.77s, $\delta_{2000}$ $-24^{\circ}$ 38$^{\prime}$ 44.3$^{\prime\prime}$" (2.1 MIRI MRS); "for an assumed distance of d$=$ 125 pc, derived from VLBA parallax measurements (cite: Loinardetal2008)" (4.3.1 The Dust Disks Detected by ALMA); z/distance 125 pc  
  > "$\alpha_{2000}$ $=$ 16h 27m 15.77s, $\delta_{2000}$ $-24^{\circ}$ 38$^{\prime}$ 44.3$^{\prime\prime}$" (2.1 MIRI MRS); "for an assumed distance of d$=$ 125 pc, derived from VLBA parallax measurements (cite: Loinardetal2008)" (4.3.1 The Dust Disks Detected by ALMA); distance from VLBA parallax (Loinard et al. 2008)  
  > "$\alpha_{2000}$ $=$ 16h 27m 15.77s, $\delta_{2000}$ $-24^{\circ}$ 38$^{\prime}$ 44.3$^{\prime\prime}$" (2.1 MIRI MRS); "for an assumed distance of d$=$ 125 pc, derived from VLBA parallax measurements (cite: Loinardetal2008)" (4.3.1 The Dust Disks Detected by ALMA)

## Data provenance

- ALMA projects: 2019.1.01792.S, 2022.1.01734.S
- bands: Band 6 (1.3 mm) and Band 4 (1.9 mm, 155 GHz)  
  > "Band 4 (1.9 mm) 155 GHz ALMA observations were obtained on 2023 June 12" (2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 6 continuum ~0.11"; lines ~1.1"; Band 4 0.096" x 0.16"  
  > "one high-angular-resolution dust continuum observation reaching $\sim\,0.11^{\prime\prime}$ with 36 sec of integration time" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: Band 6: 0.27 mJy/beam continuum; 25 mJy/beam per 0.125 km/s lines; Band 4: 0.075 mJy/beam  
  > "sensitivity of 0.075 mJy beam$^{-1}$ measured from the rms signal in an emission-free part of the continuum image" (2.2 ALMA)
- time on source: Band 6: 36 s (continuum), 194 s (lines); Band 4: 30 s  
  > "a lower-angular-resolution observation reaching $\sim\,1.1^{\prime\prime}$ with 194 sec of integration time" (2.2 ALMA)
- observing dates: Band 4: 2023 June 12  
  > "Band 4 (1.9 mm) 155 GHz ALMA observations were obtained on 2023 June 12" (2.2 ALMA)
- pi or archival as stated: Band 6 PI D. Mardones; Band 4 PI Ł. Tychoniec  
  > "program 2019.1.01792.S (PI: D. Mardones)" (2.2 ALMA)
- Line: CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **JWST MIRI MRS**: 5-28 micron IFU spectroscopy and images: jets, H2, continuum, discovery of WL 20SE  
  > "WL 20 was observed during UTC 12-13 April 2023 as part of Guaranteed Time Observations (PID 01236; P.I. Ressler)" (2.1 MIRI MRS)
- External data: Spectral types, Teff and A_V (16, 41) for WL 20E/W/S  
  > "The extinction at 12.81 $\mu$m was derived from the published values of $A_V$ of 16 for both WL 20E and WL 20W, and $A_V\ =$ 41 toward WL 20S (cite: BGB2002)." (4.3.2 X-ray excited 12.8um [NeII] Disk Emission) [from (cite: BGB2002)]
- External data: Distance 125 pc  
  > "for an assumed distance of d$=$ 125 pc, derived from VLBA parallax measurements (cite: Loinardetal2008)" (4.3.1 The Dust Disks Detected by ALMA) [from (cite: Loinardetal2008)]
- External data: System age ~2-2.5e6 yr from HR diagram of WL 20E/W  
  > "the most plausible system age is determined to be $\sim$ 2 $-$ 2.5 $\times$ 10$^{6}$ yr (cite: ResslerBarsony2001)." (5 Conclusions) [from (cite: ResslerBarsony2001)]
- External data: Dust opacity 0.9 cm2/g at 1.3 mm  
  > "$\kappa_{1.3 {\rm mm}}= 0.9 \ {\rm cm^{2}\ g^{-1}}$ provided in (cite: Ossenkopf.Henning1994)" (3.2.1 ALMA Band 4 Data) [from (cite: Ossenkopf.Henning1994)]
- External data: Disk gas mass models  
  > "We can estimate disk gas masses using the models of (cite: WilliamsBest2014)" (4.3.3 ALMA Constraints on Disk Gas Masses) [from (cite: WilliamsBest2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Band 4 data self-calibrated with auto_selfcal package  
  > "The observations were self-calibrated with the `auto`$\_$`selfcal` package[^1]." (2.2 ALMA)

### Imaging

- task: CASA tclean (CASA 6.5.2)  
  > "We used the `tclean` task of CASA version 6.5.2 to produce the dust continuum image and molecular line channel maps" (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Band 6 robust 0.0 (continuum), -0.5 (lines); Band 4 robust 0.5  
  > "Robust parameters of 0.0 and -0.5 were used for the dust continuum and molecular line maps, respectively." (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh (Band 6); automasking with standard parameters (Band 4)  
  > "with Briggs weighting and the auto-multithresh option for the masking operations" (2.2 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 4 0.096" x 0.16"; Band 6 continuum 0.14" x 0.11"; CO beam ~10x larger, two beam areas 0.46" x 0.92" at PA 345  
  > "(0.14$^{\prime\prime}\ \times\ 0.11^{\prime\prime}$ and 0.096$^{\prime\prime}\, \times\, 0.16^{\prime\prime}$, respectively)" (4.3.1 The Dust Disks Detected by ALMA)
- final rms: 0.27 mJy/beam (Band 6 cont.), 25 mJy/beam per 0.125 km/s (lines), 0.075 mJy/beam (Band 4)  
  > "We reached noise levels of 0.27 mJy beam$^{-1}$ and 25 mJy beam$^{-1}$ per 0.125 km s$^{-1}$" (2.2 ALMA)

### Inherited from earlier work

- Gas mass formula adapted from 13CO(1-0) to 13CO(2-1)  
  > "Adjusting the formula for the gas mass estimate derived for $^{13}$CO(1$-$0) from (cite: SargentBeckwith1987) (following (cite: Scoville1986)) to $^{13}$CO(2$-$1):" (4.4.1 ALMA) [from (cite: SargentBeckwith1987); (cite: Scoville1986)]
- Dust mass equation (optically thin)  
  > "assuming optically thin dust emission, using the equation from (cite: Hildebrand1983)" (3.2.1 ALMA Band 4 Data) [from (cite: Hildebrand1983)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline vs manual and flux calibrator for ALMA data
- Line-free channels and continuum subtraction for CO lines
- Image size, cell size, channel width used for Band 4 and Band 6
- Band 6 spectral windows and the observing configurations
- 13CO and C18O abundance X(13CO) used in the gas mass
- Details of the Williams & Best model use and gas mass derivation
- Moment-map clipping thresholds
- Deconvolution method for the MIRI jet images

## Analysis recipe

1. **Image ALMA continuum and lines**: tclean with Briggs weighting and auto-multithresh masks for Band 6 and Band 4 (Band 4 self-calibrated first)  
  > "The resulting measurement set was imaged with the `tclean` procedure within CASA version 6.5.2" (2.2 ALMA)
   - software: CASA, auto_selfcal
   - parameter: robust 0.0 continuum, -0.5 lines (Band 6); 0.5 (Band 4)  
  > "A robust parameter of 0.5 was used, and automasking with standard parameters was applied." (2.2 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum positions and fluxes**: imfit; single Gaussian for WL 20E/W, two Gaussians for WL 20SE/SW (positions averaged, fluxes summed)  
  > "their elongated morphologies are best fit by a combination of two Gaussian components." (3.2.1 ALMA Band 4 Data)
   - software: CASA imfit
   - fitting: Gaussian fits  
  > "By contrast, WL 20SE and WL 20SW are both resolved by ALMA (see Figure 13), and their elongated morphologies are best fit by a combination of two Gaussian components." (3.2.1 ALMA Band 4 Data)
   - validation: Total 1.3 mm flux 61.1 mJy compared with IRAM 30m 95 mJy (~20% uncertainty)  
  > "The total 1.3 mm flux from the entire WL 20 system is 61.1 mJy" (4.3.1 The Dust Disks Detected by ALMA)
3. **Derive disk dust masses**: Optically thin M = D^2 F / (kappa B(T))  
  > "The temperature of the dust is assumed to be 30 K, typical for young protostellar envelopes" (3.2.1 ALMA Band 4 Data)
   - parameter: kappa_1.9mm = 0.6 cm2/g scaled from 0.9 at 1.3 mm with beta=1  
  > "A value of $\kappa_{1.9 {\rm mm}}= 0.6 \ {\rm cm^{2}\ g^{-1}}$ was used" (3.2.1 ALMA Band 4 Data)
   - assumption: T_dust = 30 K, optically thin, d = 125 pc  
  > "assuming optically thin dust emission" (3.2.1 ALMA Band 4 Data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure 13CO and C18O fluxes and limits**: Integrate moment-0 maps in two beam areas on disks; 3 sigma rms limits from line-free region for WL 20E/W  
  > "Quantitative upper limits on this emission are derived by measuring the 3 $\sigma$ rms in a line-free region of the $^{13}$CO(2$-$1) moment-zero map" (3.2.2 ALMA Band 6 Data)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate disk and envelope gas masses**: Williams & Best (2014) models for disks; optically thin 13CO formula for remnant envelope with Tex = 30 K  
  > "Assuming $T_{ex}\ =$ 30K at 125 pc distance, and using the measured $S_{\nu}\, dv$ of 4.01 Jy km s$^{-1}$" (4.4.1 ALMA)
   - assumption: CO/C18O ratio 550 or 1650; d = 125 pc  
  > "for an assumed CO/C$^{18}$O ratio of 550, or just $\sim$1 M$\oplus$ for the case of a CO/C$^{18}$O ratio of 1650" (4.3.3 ALMA Constraints on Disk Gas Masses)
   - fitting: _not stated_
   - validation: Compared with core mass 0.024 Msun from JCMT 850um  
  > "a core mass of 0.024 M$_{\odot}$ (or just 25 M$_{Jupiter}$) for WL 20 was derived from submillimeter continuum mapping of the $\rho$ Oph cloud at 850 $\mu$m" (5.1.1 ALMA (Gas Emission from the Surroundings))

## Software

- **CASA** 6.5.2: tclean imaging and imfit  
  > "We used the `tclean` task of CASA version 6.5.2" (2.2 ALMA)
- **auto_selfcal** : self-calibration of Band 4 data  
  > "The observations were self-calibrated with the `auto`$\_$`selfcal` package[^1]." (2.2 ALMA)
- **JWST calibration pipeline** 1.11.4: MIRI MRS reduction  
  > "These were performed using the JWST pipeline version 1.11.4 (cite: Bushouse2023)" (2.1 MIRI MRS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass WL 20SW | 42 | 2 | Earth masses | 3 | / WL 20SW / 14 $\pm$ 2 / 89 $\pm$1 / 47.5 $\pm$ 5 / 2300 $\pm$ 5 / 36.1 $\pm$ 0.6 / 16.2 $\pm$ 0.3 / 42 $\pm$ 2 / |
| Dust mass WL 20SE | 24 | 4 | Earth masses | 3 | / WL 20SE / 3.7$\pm$ 0.5 / $-$ / $-$ / $-$ / 20.1 $\pm$ 0.6 / 9.0 $\pm$ 0.3 / 24 $\pm$ 4 / |
| Dust masses WL 20E, WL 20W | 3.3 and 3.6 | 0.4 and 0.5 | Earth masses | 3 | dust masses of 3.3 $\pm$ 0.4 M$_{\oplus}$ and 3.6 $\pm$ 0.5 M$_{\oplus}$ for WL 20E and WL 20W |
| Combined gas mass of WL 20SE+SW disks | ~100 (CO/C18O=550) or ~1 (1650) | not stated | Earth masses | 5 | a combined gas mass of about 100 M$\oplus$ (3 $\times$ 10$^{-4}$ M$_{\odot}$) for an assumed CO/C$^{18}$O ratio of 550 |
| Remnant envelope gas mass | 4.5e-3 | not stated | Msun | 5 | yields a remnant envelope gas mass of just 4.5 $\times$ 10$^{-3}$ M$_{\odot}$ |
| H2 excitation temperature at S(5) apex | 1161 | 70 | K | 0 | T$_{ex}\,=$ 1161K $\pm$ 70K |

## Qualitative findings

- No molecular outflow or cavity walls seen in CO isotopologues; H2 biconical structure attributed to wide-angle disk winds  
  > "the observed H$_2$ structures must have their origins in wide-angled disk winds, in the absence of any ambient, swept-up gas." (abstract)

## Claim tuples

- H: WL 20S is a binary driving twin jets from edge-on disks | E: MIRI MRS imaging plus ALMA Band 4/6 continuum | R: New source WL 20SE found; ALMA resolves two edge-on disks of ~100 au; twin jets in [FeII],[NiII],[ArII],[NeII] | F: Twin disks power twin jets | **supported**
- H: Northern disks WL 20E and WL 20W are gas-depleted | E: 13CO and C18O upper limits vs dust masses with Williams & Best models | R: Limits well below lowest model gas mass | F: Gas-to-dust ratio at least 10 times lower than 100 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Flattened CO structure as pseudo-disk (infall velocities not observed) or single Keplerian disk (not centered on sources)  
  > "The expected velocity gradients for infalling gas motions are, however, not observed in the individual CO(2$-$1) velocity channel maps" (4.4.1 ALMA)
- How they decided it was enough: _not stated_
- Limitation (authors): CO observations lack resolution to separate the twin disks  
  > "Recall that the large beam size of the CO(2$-$1) observations could not resolve the twin disks" (4.4.1 ALMA)
- Caveat (inferred, ours): Gas masses depend on assumed CO/C18O ratios and spanning two orders of magnitude
- Caveat (inferred, ours): Fixed dust T=30 K and kappa uncertain for disks
- Caveat (inferred, ours): ALMA role is secondary; coeval age assumption drives the evolutionary claim
- Caveat (inferred, ours): Gas mass derivation is not reproducible from details given

## Reproducibility

- Data public (paper): ALMA programs cited with ADS/JAO.ALMA codes; JWST data from MAST  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01792.S and ADS/JAO.ALMA#2022.1.01734.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration details and pipeline version for ALMA
- Missing: Image and cell sizes, line channel selection
- Missing: Full gas mass model procedure
- Data volume (inferred): ~tens of GB for both ALMA datasets (short integrations)
- Score (inferred): 3/5, ALMA flux and dust mass recipe is clear, but gas mass and line steps are underspecified.
- Rediscovery candidate: no, Main results are partly from JWST and ALMA recipes lack detail; gas masses rely on external models.

## Links

- Method: Williams & Best 2014 (cite: WilliamsBest2014) (Disk gas mass models from CO isotopologues)
- Companion: Ressler & Barsony 2001 (cite: ResslerBarsony2001) (Earlier mid-IR imaging and age)
- Related: MIRI JOYS+
- Related: ODISEA

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 43,
  "rate": 0.566
 },
 "evidence_ok": true
}
```
