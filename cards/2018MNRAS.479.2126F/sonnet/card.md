# ALMA observations of a metal-rich damped Ly α absorber at z = 2.5832: evidence for strong galactic winds in a galaxy group

`2018MNRAS.479.2126F` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Fynbo, J. P. U. | arXiv: 1806.01715 | DOI: 10.1093/mnras/sty1520

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: Is CO(3-2) emission detected from the galaxy counterpart of the metal-rich DLA at z=2.5832 towards Q0918+1636, and what does the field reveal about the DLA's group environment and outflows?  
  > "We do not detect CO emission from the previously identified DLA galaxy counterpart." (abstract); "Instead we detect CO(3-2) emission from another intensely star-forming galaxy at an impact parameter of 117 kpc" (abstract)
- Target **Q0918+1636 DLA field (z=2.5832)**: coordinates _not stated_; z/distance z=2.5832  
  > "The galaxy counterpart is detected at a projected distance of 1.98 arcsec from the quasar (i.e. 16.2 kpc at $z=2.5832$)." (Introduction); distance from DLA absorption redshift in the quasar spectrum  
  > "The galaxy counterpart is detected at a projected distance of 1.98 arcsec from the quasar (i.e. 16.2 kpc at $z=2.5832$)." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00628.S
- bands: _not stated_
- frequencies and spectral setup: one of four spectral windows centred on CO(3-2) at 96.5 GHz, 3.9 MHz resolution; other three for continuum  
  > "one of the four spectral windows was centered on the redshifted CO(3$-$2) line at 96.5 GHz with a frequency resolution of 3.9 MHz." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, maximum baseline 383 m  
  > "observed with ALMA on UT 2017 January 9 with a compact configuration (maximum baseline of 383 m)" (2 ALMA Observations)
- baselines: _not stated_
- angular resolution: continuum beam 3.2'' x 2.5'' at PA 69 deg  
  > "resulting in a synthesized beam of $3.''2 \times 2.''5$ at 69$^\circ$" (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 14.3 uJy/beam; cube rms 0.24 mJy/beam per 48.5 km/s channel  
  > "The resulting root mean square (RMS) noise of the continuum image is 14.3 $\mu$Jy beam$^{-1}$" (2 ALMA Observations); "resulting in a RMS noise of 0.24 mJy beam$^{-1}$ per 48.5 km s$^{-1}$ channel" (2 ALMA Observations)
- time on source: 2117 s  
  > "for a total on-source integration time of 2117 seconds" (2 ALMA Observations)
- observing dates: UT 2017 January 9  
  > "observed with ALMA on UT 2017 January 9" (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated (observed at 96.5 GHz))
- Other facility **HST/WFC3**: F606W, F105W, F160W imaging for SED and counterpart identification  
  > "observed with the Wide Field Camera 3 (WFC3) on-board *HST* in the $F606W$, $F105W$, and $F160W$ filters" (3.2.3 Physical properties from SED fitting)
- Other facility **NOT (ALFOSC, NOTCam)**: u, g and Ks imaging  
  > "From the NOT we obtained $u$ and $g$ SDSS filter images using ALFOSC and a $K_s$ band image using NOTCam." (3.2.3 Physical properties from SED fitting)
- External data: DLA galaxy stellar mass, SFR, photometry and HST/NOT data details  
  > "F13 derived a stellar mass of $\log (M_{\star}/M_{\odot}) =
10.10^{+0.17}_{-0.11}$" (1 Introduction) [from (cite: Fynbo13)]
- External data: L'CO(3-2)/L'CO(1-0)=0.57  
  > "we assume $L'_{\mathrm{CO}(3-2)} / L'_{\mathrm{CO}(1-0)} = 0.57$ (cite: Dessauges-Zavadsky15)" (3.1) [from (cite: Dessauges-Zavadsky15)]
- External data: alpha_CO = 4.3  
  > "a CO-to-H$_2$ conversion of $\alpha_{\mathrm{CO}} = 4.3~M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: Bolatto13)" (3.1) [from (cite: Bolatto13)]
- External data: Galactic extinction E(B-V)=0.022  
  > "Galactic foreground extinction of $E(B-V) = 0.022$ mag (cite: Schlafly11)" (3.2.3) [from (cite: Schlafly11)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA plus additional manual flagging  
  > "After this initial round of calibration, additional flagging was performed in CASA." (2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231 (bandpass/phase: J0852+2006)  
  > "quasar J0750+1231 was used for flux calibration" (2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA  
  > "Using the task `TCLEAN` in CASA, a spectral cube was made" (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Natural weighting was used and the cube was Hanning-smoothed" (2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning-smoothed to 48.5 km/s  
  > "the cube was Hanning-smoothed to a velocity resolution of 48.5 km s$^{-1}$" (2 ALMA Observations)
- final beam: 3.2'' x 2.5'' at 69 deg (continuum)  
  > "synthesized beam of $3.''2 \times 2.''5$ at 69$^\circ$" (2 ALMA Observations)
- final rms: 0.24 mJy/beam per 48.5 km/s channel  
  > "RMS noise of 0.24 mJy beam$^{-1}$ per 48.5 km s$^{-1}$ channel" (2 ALMA Observations)

### Inherited from earlier work

- alpha_CO and CO excitation ratio adopted to match Neeleman et al. 2018  
  > "To facilitate comparison, we will use similar values here" (3.2.1) [from (cite: Neeleman18)]
- HST and NOT observation details  
  > "(see F13 for details)" (3.2.3) [from F13 (cite: Fynbo13)]

### Not stated but needed to reproduce (our reading)

- tclean cell size, image size, niter/threshold and masking
- continuum image details (spectral window frequencies and bandwidth)
- CASA/pipeline version
- aperture/extraction region for the CO spectrum and line-integration velocity range
- how the continuum flux of 40 uJy was measured
- MAGPHYS priors/settings and photometry with ALMA continuum treatment
- target coordinates

## Analysis recipe

1. **calibrate and image**: ALMA pipeline calibration, extra flagging, continuum image from three spws (natural weighting) and tclean cube of CO spw  
  > "The continuum image was generated from the three continuum spectral windows, using natural weighting" (2 ALMA Observations)
   - software: CASA, tclean
   - parameter: Hanning smoothing to 48.5 km/s; cube spans ±2890 km/s  
  > "The spectral cube spans a velocity window of $\pm 2890$ km s$^{-1}$ around the DLA redshift." (2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **search cube for lines and derive DLA-counterpart upper limit**: search full cube; 3 sigma upper limit on line flux converted to L'CO and Mmol  
  > "Assuming a similar line width for the emission profile gives a $3\sigma$ upper limit on the velocity-integrated line flux" (3.1)
   - assumption: r31=0.57, alpha_CO=4.3  
  > "a CO-to-H$_2$ conversion of $\alpha_{\mathrm{CO}} = 4.3~M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: Bolatto13)" (3.1)
   - fitting: _not stated_
   - validation: chance probability of tentative 5.8 sigma line estimated assuming Gaussian noise  
  > "Assuming Gaussian noise characteristics, the chance probability of such a signal to occur in the full data cube due to noise fluctuations is $7 \times 10^{-4}$." (3 Results)
3. **measure CO galaxy flux, luminosity and gas mass**: extract line profile, integrate flux, convert via Solomon05 and alpha_CO  
  > "From the CO spectral cube, we have extracted a line profile at the position of the CO emission" (3.2.1)
   - assumption: lower mass uncertainty includes starburst-like conditions  
  > "the lower uncertainty on the mass includes the assumption of starburst-like conditions" (3.2.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fit of CO galaxy**: MAGPHYS fit to HST/NOT photometry (2 arcsec apertures) plus ALMA continuum  
  > "MAGPHYS is a tool that fits the photometric data to stellar population and dust emission synthesis models, assuming a (cite: Chabrier03) IMF" (3.2.3)
   - software: MAGPHYS
   - assumption: Chabrier IMF; Galactic extinction correction  
  > "assuming a (cite: Chabrier03) IMF to generate the output galaxy models" (3.2.3)
   - fitting: _not stated_
   - validation: authors caution the modelling is the best possible given the multi-component morphology  
  > "We stress that this photometric modeling is only the best possible with the data in hand." (3.2.3)

## Software

- **CASA** : pipeline calibration, flagging, imaging  
  > "The initial data were calibrated using the ALMA pipeline, which is part of the Common Astronomy Software Applications (cite: McMullin07) package." (2 ALMA Observations)
- **tclean** : spectral cube  
  > "Using the task `TCLEAN` in CASA, a spectral cube was made" (2 ALMA Observations)
- **MAGPHYS** : SED fitting  
  > "we use MAGPHYS[^2] (cite: daCunha08)" (3.2.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) line flux of CO galaxy | 0.73 | 0.08 | Jy km/s | 3 | $0.73 \pm 0.08$ Jy km s$^{-1}$ |
| L'CO(3-2) of CO galaxy | 2.5e10 | 0.3e10 | K km/s pc^2 | 3 | $L'_{\mathrm{CO}(3-2)} = (2.5 \pm 0.3) \times 10^{10}$ K km s$^{-1}$ pc$^{2}$ |
| Mmol of CO galaxy | 1.8e11 | +0.2/-1.6 e11 | Msun | 3 | $M_{\mathrm{mol}} = (1.8^{+0.2}_{-1.6})\times 10^{11} M_{\odot}$ |
| L'CO(3-2) upper limit for DLA galaxy | <1.7e9 | not stated | K km/s pc^2 | 2 | $L'_{\mathrm{CO}(3-2)} < 1.7\times 
10^9$ K km s$^{-1}$ pc$^{2}$ |
| Mmol upper limit for DLA galaxy | <1.3e10 | not stated | Msun | 2 | $M_{\mathrm{mol}} < 
1.3 \times 10^{10} M_{\odot}$ |
| CO galaxy continuum flux density | 40 | 13 | uJy | 3 | measured flux density of 40$\pm$13 $\mu$Jy |
| CO galaxy SFR (SED) | 112 | +111/-68 | Msun/yr | 4 | SFR ($M_{\odot}$ yr$^{-1}$)          /     /     /     /     /      $112^{+111}_{-68}$ |
| CO galaxy log stellar mass | 10.45 | +0.10/-0.20 | log Msun | 4 | $10.45^{+0.10}_{-0.20}$ |

## Qualitative findings

- Absorption component at +131 km/s in the DLA low- and high-ionisation lines coincides with the CO galaxy redshift, plausibly outflow from it  
  > "there is an absorption component consistent with the redshift of this CO-emitting galaxy." (abstract)

## Claim tuples

- H: Is CO emitted by the DLA counterpart? | E: ALMA CO(3-2) cube at counterpart position | R: no detection; Mmol<1.3e10 Msun | F: Limit consistent with other star-forming galaxies at similar z | **supported**
- H: Are there other group members and outflows? | E: Cube search plus comparison with quasar absorption profiles | R: CO galaxy at 117 kpc, +131 km/s with matching absorption component | F: Plausibly galactic outflow traced beyond 100 kpc in a group | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: chance alignment of absorption component cannot be ruled out  
  > "Whereas we cannot rule out that the match is a chance effect, a causal relation seems plausible." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA resolution cannot resolve CO and HST multi-component counterpart/astrometry offset  
  > "Unfortunately, the resolution of the spectral cube emission is insufficient to resolve the CO emission." (3.2.1)
- Caveat (inferred, ours): Single short observation; low S/N.
- Caveat (inferred, ours): alpha_CO and r31 assumed.
- Caveat (inferred, ours): HST-ALMA association uncertain.
- Caveat (inferred, ours): Outflow interpretation speculative.

## Reproducibility

- Data public (paper): project code given; public status not explicitly stated  
  > "ADS/JAO.ALMA#2016.1.00628.S (PI Prochaska)" (footnote 1)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: extraction apertures and integration range
- Missing: HST/NOT photometry reduction
- Missing: MAGPHYS settings
- Data volume (inferred): ~5-10 GB raw
- Score (inferred): 3/5, Simple dataset and short recipe, but imaging and extraction details are missing.
- Rediscovery candidate: no, Public status not stated and key parameters missing, though results are numeric.

## Links

- Companion: (cite: Neeleman18) (Same ALMA survey of metal-rich DLAs; adopted conversions)
- Companion: (cite: Fynbo13) (Previous identification of DLA counterpart and ancillary data)
- Related: ALMA study of metal-rich DLAs at z>2 (PI Prochaska)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 41,
  "rate": 0.562
 },
 "evidence_ok": true
}
```
