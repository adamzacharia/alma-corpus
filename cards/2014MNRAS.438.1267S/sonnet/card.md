# An ALMA survey of sub-millimetre Galaxies in the Extended Chandra Deep Field South: the far-infrared properties of SMGs

`2014MNRAS.438.1267S` | Monthly Notices of the Royal Astronomical Society 2014 | first author: Swinbank, A. M. | arXiv: 1310.6362 | DOI: 10.1093/mnras/stt2273

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the far-infrared properties (colours, luminosities, dust temperatures, dust and gas masses) of ALMA-located SMGs in the ECDFS, and what do they imply for cosmic star formation and H2 density?  
  > "we use the far-infrared (70–870$\mu$m) and 1.4 GHz radio photometry together with new optical/mid-infrared-derived photometric redshifts from Simpson et al. (2013) to derive the far-infrared luminosities, characteristic dust temperatures, dust masses" (1 Introduction)
- Target **ALESS SMGs (99 ALMA-detected LESS sources in the ECDFS)**: coordinates _not stated_; z/distance photometric redshifts, median z = 2.5 ± 0.2  
  > "an ALMA survey of the 126 sub-mm sources in the 0.5 $\times$ 0.5 degree Extended *Chandra* Deep Field South (ECDFS), taken from the “LESS” survey (cite: Weiss09)" (1 Introduction); distance from Simpson et al. (2013) photometric redshifts  
  > "an ALMA survey of the 126 sub-mm sources in the 0.5 $\times$ 0.5 degree Extended *Chandra* Deep Field South (ECDFS), taken from the “LESS” survey (cite: Weiss09)" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00294.S
- bands: Band 7 (345 GHz, 870 um)  
  > "observations of 122 of the 126 LESS sources were obtained with ALMA in Cycle 0 at 345 GHz (Band 7)" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, 12-15 antennae  
  > "The observations employed 12–15 antennae and were obtained between 2011 October and 2011 November" (2.1 ALMA)
- baselines: _not stated_
- angular resolution: ~1.6'' x 1.2'' synthesised beam  
  > "yielding a synthesised beam of $\sim$ 1.6$''\times$1.2$''$" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: σ = 0.4–0.5 mJy/beam  
  > "typical noise levels of $\sigma$ = 0.4–0.5 mJy beam$^{-1}$" (2.1 ALMA)
- time on source: _not stated_
- observing dates: 2011 October to November  
  > "obtained between 2011 October and 2011 November in good conditions" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **Herschel SPIRE (HerMES)**: 250, 350, 500 um maps deblended for SMG fluxes  
  > "observations covering ECDFS were taken as part of the *Herschel* Multi-tiered Extra-galactic Survey (HerMES) guaranteed time program" (Herschel / PACS and SPIRE Imaging)
- Other facility **Herschel PACS (PEP)**: 70-160 um photometry  
  > "were taken as part of the PACS Evolutionary Probe (PEP) survey" (Herschel / PACS and SPIRE Imaging)
- Other facility **Spitzer MIPS 24um (FIDEL)**: 24 um catalog used for positional priors  
  > "*Spitzer* / MIPS 24 $\mu$m imaging is also available for the ECDFS as part of the Far-Infrared Deep Extra-galactic Legacy (FIDEL) survey." (2.2)
- Other facility **JVLA 1.4 GHz**: radio catalog and imaging  
  > "The ECDFS was observed with the JVLA in D, C, B and A configurations in 2007 June to September" (2.2)
- External data: ALESS SMG catalog (99 main-catalog SMGs, S/N>3.5)  
  > "From the ALMA maps, (cite: Hodge13) extract 99 SMGs with S / N$>$3.5 from the best maps" (2.1 ALMA) [from (cite: Hodge13)]
- External data: Photometric redshifts and stellar masses of ALESS SMGs  
  > "Simpson et al. (2013) used the 16-band optical–mid-infrared photometric coverage of ECDFS to derive photometric redshifts for 77 of the 99 ALESS SMGs." (2.5) [from Simpson et al. (2013)]
- External data: CO-derived H2 masses used to calibrate gas-to-dust ratio  
  > "we exploit the CO-derived H$_{\rm 2}$ masses from (cite: Bothwell13) who derive $M_{\rm H2}$ = 3.6 $\pm$ 1.0 $\times$ 10$^{10}$ M$_{\odot}$" (4.4) [from (cite: Bothwell13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: planets (flux); J0403-360 phase, J0538-440 bandpass  
  > "Phase and bandpass calibration was based on J0403$-$360, J0538$-$440 respectively and flux calibration performed on available planets at the time of observation." (2.1 ALMA)
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

- ALMA observations, reduction and source catalog  
  > "Details of the ALMA observations of the sub-millimeter sources from the ALMA LESS (ALESS) survey are described in (cite: Hodge13) (cite: Karim13)." (2.1 ALMA) [from (cite: Hodge13); (cite: Karim13)]
- Photometric redshifts  
  > "Simpson et al. (2013) show that the redshift distribution of the 96 ALESS SMGs is centered at $z$ = 2.5 $\pm$ 0.2" (2.5) [from Simpson et al. (2013)]
- Detection limit and upper-limit definitions for deblending  
  > "Following (cite: Magnelli13), we define the 3-$\sigma$ detection limit when 68% of the distribution are recovered with a fractional error less than 30%." (2.3.1) [from (cite: Magnelli13)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging parameters (deferred to Hodge13)
- Exact SED template library files and fit priors/redshift handling details
- Grey-body fit details (fixed beta, wavelengths used) for individual T_d
- Bootstrap details for composite SED and luminosity function
- Choice of ALMA data products used (archive vs. published catalog)

## Analysis recipe

1. **Deblend SPIRE maps with positional priors**: Monte Carlo deblending using 24um, radio and ALMA positions as priors; 1000 initial models, iterated until convergence; 350/500um priors require >2σ detection at the shorter band  
  > "To deblend the SPIRE map we develop a Monte Carlo algorithm." (2.3.1)
   - parameter: 1.5'' matching radius for prior catalog; thumbnail extent ±2.5×FWHM  
  > "we extract a thumbnail which has an extent $\pm$ 2.5 $\times$ the FWHM of the beam at that wavelength." (2.3.1)
   - fitting: chi^2 minimisation over random flux models  
  > "We then convolve this image with the relevant SPIRE point spread function (PSF) and record the amplitude of the residuals and $\chi^2$." (2.3.1)
   - validation: Simulated SPIRE maps recover input fluxes (ratio 0.96, 0.97, 1.17); comparison to XID gives ~10% agreement  
  > "This suggests that the “XID” and our deblending produce consistent flux densities to $\mathrel{\raise 0.35ex\hbox{$\scriptstyle <$}\kern-0.6em\lower 0.40ex\hbox{{$\scriptstyle \sim$}}}$ 10% accuracy." (2.3.1)
2. **Fit SEDs for L_IR, T_d and dust mass**: Fit library of 185 templates plus modified black-body to 24um–1.4GHz photometry at photometric redshift; integrate 8–1000 um for L_IR  
  > "Using the best-fit dust SEDs, we calculate the infrared luminosity ($L_{\rm IR}$) by integrating the rest-frame SED between 8–1000$\mu$m (rest-frame)." (3.3)
   - assumption: kappa_870 = 0.15 m^2 kg^-1  
  > "for a dust mass absorption coefficient of $\kappa_{870\mu m}$ = 0.15 m$^2$ kg$^{-1}$" (2.5)
   - fitting: chi^2 minimisation  
  > "We fit these template SEDs to the 24 $\mu$m–1.4 GHz photometry of the composite SED using a $\chi^2$ minimisation" (3.1)
   - validation: _not stated_
3. **Derive H2 masses and cosmic density contributions**: Apply gas-to-dust ratio to dust masses; luminosity functions via 1/Vmax; extrapolate to 1 mJy with counts  
  > "For simplicity, in all of the following analysis, we therefore adopt a single gas-to-dust ratio of $\delta_{\rm GDR}$ = 90 $\pm$ 25." (4.4)
   - assumption: gas-to-dust ratio 90 ± 25; burst duration 250 Myr  
  > "Assuming the SMGs have a burst duration of 250 Myr, we calculate the duty cycle as a function of redshift" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : processing the ALMA data  
  > "The data were processed with the Common Astronomy Software Application ( casa; (cite: McMullin07))." (2.1 ALMA)
- **hyper-z** : photometric redshifts (Simpson et al.)  
  > "using hyper-z with the spectral templates of (cite: Bruzual03)" (2.5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median L_IR | 3.0e12 | ±0.3e12 | L_sun | 2 | The median infrared luminosity for the ALESS SMGs is $L_{\rm IR}$ = (3.0 $\pm$ 0.3) $\times$ 10$^{12}$ $L_{\odot}$ |
| Median dust mass | 3.6e8 | ±0.3e8 | M_sun | 2 | The median dust mass for all of the SMGs in our sample is $M_{\rm d}$ = (3.6 $\pm$ 0.3) $\times$ 10$^{8}$ M$_{\odot}$ |
| Median H2 mass | 4.2e10 | ±0.4e10 | M_sun | 3 | this suggests a median H$_2$ mass of $M_{\rm H2}$ = (4.2 $\pm$ 0.4) $\times$ 10$^{10}$ M$_{\odot}$ for the ALESS SMGs. |
| Median photometric z of SPIRE-undetected SMGs | 3.3 | ±0.5 | dimensionless | 0 | with $z$ = 3.3 $\pm$ 0.5 (c.f. $z$ = 2.5 $\pm$ 0.2; Simpson et al. 2013; Fig. [6](#fig:Nz)) |
| Gas depletion timescale | 130 | ±15 | Myr | 3 | gas depletion time-scale of $M_{\rm H_2}$ / SFR$\sim$ 130 $\pm$ 15 Myr |

## Qualitative findings

- ALESS SMGs have dust temperatures 3–5 K cooler than local galaxies at fixed L_IR  
  > "for a fixed luminosity, ALESS SMGs have cooler dust temperatures ($\Delta T_{\rm d}$ = 3–5 K)" (4.1)

## Claim tuples

- H: SPIRE peak wavelength tracks SMG redshift | E: Deblend SPIRE at ALMA positions and split by SED peak | R: median z = 2.3, 2.5, 3.5 for 250, 350, 500um peakers | F: Redder SEDs lie at higher redshift | **supported**
- H: SMGs contribute significantly to cosmic SFR density | E: Extrapolate counts to 1 mJy | R: ~20% of SFRD at z~1–5 | F: S870>1 mJy SMGs contribute ~20% | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Deblending requiring 250um detection for 350um priors may bias against 250um-faint sources  
  > "which may bias against galaxies that are faint at 250-$\mu$m and peak at longer wavelengths." (3.3)
- Caveat (inferred, ours): Photometric redshifts have large uncertainties that propagate to L_IR and T_d
- Caveat (inferred, ours): Single gas-to-dust ratio calibrated on a small CO sample
- Caveat (inferred, ours): Extrapolation to 1 mJy assumes same redshift distribution and scaling

## Reproducibility

- Data public (paper): All data in public archives  
  > "All of the ALMA, *Herschel*, VLA and *Spitzer* data employed in this analysis are available through the ESO, Herschel VLA and *Spitzer* archives." (acknowledgments)
- Products in archive: _not stated_
- Missing: Deblending code not released; template library mentioned at URL only
- Missing: ALMA reduction details in Hodge13
- Data volume (inferred): ~10-50 GB (Cycle 0 ALMA plus Herschel/Spitzer maps)
- Score (inferred): 3/5, ALMA only supplies positions via an inherited catalog; main analysis uses Herschel data and templates with partial detail.
- Rediscovery candidate: no, ALMA role is minor and the key inputs (catalog, photo-z) come from companion papers.

## Links

- Method: (cite: Hodge13) (ALMA catalog and data reduction)
- Method: (cite: Magnelli13) (detection limit definitions and PACS catalogs)
- Companion: Simpson et al. (2013) (photometric redshifts and stellar masses)
- Companion: (cite: Karim13) (ALESS number counts)
- Related: ALESS
- Related: LESS
- Related: HerMES
- Related: PEP
- Related: FIDEL

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 69,
  "stated": 33,
  "rate": 0.478
 },
 "evidence_ok": true
}
```
