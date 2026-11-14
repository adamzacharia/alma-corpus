# Molecular gas on large circumgalactic scales at z = 3.47

`2017MNRAS.468.3468G` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Ginolfi, M. | arXiv: 1611.07026 | DOI: 10.1093/mnras/stx712

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is there extended molecular gas (CO 4-3) around the massive z=3.47 galaxy Candels-5001 tracing cold accretion streams, and what are its properties and environment?  
  > "In this study we report ALMA observations of an extended molecular gas structure around a massive star forming galaxy at $\rm z=3.47$ located in an overdense region" (Introduction)
- Target **Candels-5001**: coordinates 03:32:23.336, -27:51:56.862 (J2000)  
  > "| 03:32:23:336 | -27.51.56.862 | 3.473 |" (Table 1); "Candels-5001 (ID 4417 in the GOODS-MUSIC catalogue; (cite: Grazian2006)) is a Lyman-break-selected star forming galaxy at redshift $\rm z=3.47$" (2 Candels-5001); z/distance z=3.473  
  > "| 03:32:23:336 | -27.51.56.862 | 3.473 |" (Table 1); "Candels-5001 (ID 4417 in the GOODS-MUSIC catalogue; (cite: Grazian2006)) is a Lyman-break-selected star forming galaxy at redshift $\rm z=3.47$" (2 Candels-5001); distance from [OIII]5007 redshift (Maiolino2008)  
  > "| 03:32:23:336 | -27.51.56.862 | 3.473 |" (Table 1); "Candels-5001 (ID 4417 in the GOODS-MUSIC catalogue; (cite: Grazian2006)) is a Lyman-break-selected star forming galaxy at redshift $\rm z=3.47$" (2 Candels-5001)

## Data provenance

- ALMA projects: 2012.1.00423.S
- bands: Band 3  
  > "A total bandwidth of 7.5 GHz was employed in Band 3, using 4 wavebands between 90 GHz and 106 GHz." (3 ALMA Observations and Data Reduction)
- frequencies and spectral setup: 4 wavebands 90-106 GHz; one centred at 103.1 GHz on CO(4-3); others continuum  
  > "One of the wavebands was centred at 103.1 GHz, which is the frequency of the CO J=4-3 transition at the target redshift, i.e. z=3.473." (3 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 30 antennas of 12 m  
  > "making use of 30 antennas ($\rm 12\,m$ diameter), with a maximum baseline of $\rm 1.2\,km$" (3 ALMA Observations and Data Reduction)
- configurations: _not stated_
- baselines: max 1.2 km, mostly compact  
  > "with a maximum baseline of $\rm 1.2\,km$, but most of the antennae were distributed in a relatively compact configuration" (3 ALMA Observations and Data Reduction)
- angular resolution: ~1.5'' natural weighting; ~1'' with Briggs  
  > "synthesized beam full-width at half-maximum (FWHM) of about 1.5$''$ in size, if using the natural weighting of the visibilities" (3 ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 9.6 uJy/beam continuum; 6 mJy/beam km/s in 20 km/s bins on CO band  
  > "We achieve an rms sensitivity of $\rm 9.6\, \mu Jy/beam$ for the continuum image and $\rm 6 \,mJy/beam\,km\,s^{-1}$ in the waveband centred on the CO J=4-3 transition" (3 ALMA Observations and Data Reduction)
- time on source: 116 minutes over three execution blocks  
  > "A total of 116 minutes of on-source integration time, distributed over three execution blocks ($\sim 40$ minutes each), were obtained." (3 ALMA Observations and Data Reduction)
- observing dates: November 2013, Cycle 1  
  > "Observations were carried out during ALMA cycle 1, in November 2013" (3 ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=4-3 (103.1 GHz observed at z=3.473)
- Other facility **HST**: F775W and F160W images for optical/near-IR counterparts  
  > "the same contours are overlaid onto an optical *Hubble Space Telescope* (HST) image (F775W), tracing the rest-frame UV emission" (4.1)
- Other facility **Herschel**: far-IR data for SED fitting  
  > "We have combined the ALMA continuum detection with *Herschel* data of the same galaxy." (4.3)
- Other facility **Chandra**: stacked X-ray image of CO systems  
  > "a $3\sigma$ detection is also obtained by the stacked *Chandra*/ACIS X-ray image ($\rm 0.5-8~keV$)" (4.4)
- Other facility **SINFONI**: [OIII] kinematics maps  
  > "as traced by the \[OIII\]5007$\rm \mathring{A}$ optical nebular line (SINFONI observations; Fig. [4](#fig:kinematics)a)" (5 Discussion)
- External data: Stellar mass of Candels-5001 ~1.9e10 Msun  
  > "$\rm M_{\star} \sim 1.9 \times 10^{10}\,M_{\odot}$; (cite: Santini2015)" (2 Candels-5001) [from (cite: Santini2015)]
- External data: SFR of Candels-5001 ~200-250 Msun/yr and H-beta based SFRs of the three galaxies  
  > "It is actively forming stars at a rate of $\rm \sim 200 -250 \,M_{\odot} yr^{-1}$ ((cite: Troncoso2014))." (2 Candels-5001) [from (cite: Troncoso2014)]
- External data: Metallicity-dependent H2-to-dust ratio  
  > "the metallicity dependent H$_2$-to-dust ratio derived by (cite: Leroy2011)" (4.3) [from (cite: Leroy2011)]

## Processing

### Calibration

- pipeline or manual: ALMA observatory staff standard calibration; extra flagging of bad channels by authors  
  > "The ALMA observatory staff performed initial data calibration, as part of standard data processing and delivery." (3 ALMA Observations and Data Reduction)
- casa version: CASA 4.5.3  
  > "performing additional flagging of bad channels, using `CASA` version 4.5.3" (3 ALMA Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The absolute flux systematic uncertainty (associated with the flux calibration) is $\sim$10%." (3 ALMA Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting; Briggs robustness 2 for 1'' resolution  
  > "maps with a resolution of 1$''$ can be achieved by using different (Briggs, with robustness parameter of 2) weighting of the baselines" (3 ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: fluxes of large-scale CO systems corrected for primary beam response  
  > "where line fluxes have been corrected for the primary beam response function" (10 Additional maps)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.6'' x 1.3'', PA=54.32 deg (natural)  
  > "specifically beam of $\rm 1.6'' \times 1.3''$ with PA=$54.32^\circ$" (4.1)
- final rms: _not stated_

### Inherited from earlier work

- Gas metallicity ~0.5 Zsun adopted from earlier work  
  > "the same gas metallicity inferred for the central and nearby galaxies ($\rm \sim 0.5\, Z_{\odot}$, e.g. (cite: Maiolino2008), (cite: Troncoso2014)" (4.1) [from (cite: Maiolino2008); (cite: Troncoso2014)]
- CO-to-H2 conversion factor alpha_CO~10+-2 and CO4-3/CO1-0 ratios  
  > "$\rm \alpha_{CO}\sim10\pm2$; (cite: Wolfire2010); (cite: Feldmann2011); (cite: Saintonge2013); (cite: Bolatto2013)" (4.1) [from (cite: Bolatto2013); (cite: Carilli2013)]
- Constant dust temperature 25 K tracer of dust mass  
  > "(cite: Scoville2014; Scoville2016) have shown that, for most galaxies, in the Rayleigh-Jeans region a constant dust temperature of 25 K can be assumed" (4.3) [from (cite: Scoville2014; Scoville2016)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channels and continuum definition
- Cleaning parameters (threshold, masks, cell and image size, deconvolver)
- Details of the astrometric shift applied
- CIGALE model setup, priors and Herschel fluxes
- Exact CO4-3/CO1-0 ratios and alpha_CO values per estimate
- Detection search algorithm details (source finding, spectral binning positions)
- Stacking procedure details
- Calibrator names

## Analysis recipe

1. **Image continuum and cubes**: Re-analyse calibrated data in CASA with extra flagging; natural weighting and Briggs weighting  
  > "The data have been imaged initially using the `CASA` natural weighting of the visibility data to create continuum map and datacubes." (3 ALMA Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make CO flux map and measure fluxes**: Collapse channels -140 to +140 km/s; flux of central galaxy within one beam on HST UV peak  
  > "collapsing the channels containing line emission, ($\rm -140 < v < +140 \, km\,s^{-1}$" (4.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Simulation convolving SINFONI [OIII] maps with ALMA beam to test beam smearing  
  > "We convolved the higher resolution \[OIII\]5007$\rm \mathring{A}$ SINFONI map (Fig. [4](#fig:kinematics)) of Candels-5001 and its companions with the ALMA beam." (9 Angular resolution effects)
3. **Derive molecular gas mass**: Convert CO(4-3) flux to H2 mass with metallicity-dependent alpha_CO and a range of 4-3/1-0 ratios  
  > "The given range of gas masses reflects the uncertainty on $\rm \alpha_{CO}$ and on the CO J=4-3/CO J=1-0 lines flux ratio" (4.1)
   - assumption: metallicity ~0.5 Zsun, alpha_CO~10+-2  
  > "conservatively assuming for such a system the same gas metallicity inferred for the central and nearby galaxies" (4.1)
   - fitting: _not stated_
   - validation: Compared with dust-based gas mass  
  > "which is roughly consistent with what inferred through the CO emission, within uncertainties" (4.3)
4. **Kinematics**: Fit one or two Gaussians per pixel to line profiles for velocity and dispersion maps; p-v diagram along major axis  
  > "Velocity and velocity dispersion maps of the 40 kpc-scale gaseous structure were obtained by fitting one or two Gaussians to the line profiles" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **SED fit for SFR and dust mass**: Fit IR-to-mm SED with ALMA continuum plus Herschel; dust mass converted to gas via Leroy2011 ratio  
  > "performed a fit of the IR-to-millimeter SED of the entire 40 kpc emitting region by using the fitting code CIGALE" (4.3)
   - software: CIGALE
   - assumption: half-solar metallicity  
  > "Assuming a metallicity of half solar (as inferred for Candles-5001)" (4.3)
   - fitting: _not stated_
   - validation: Compared to summed SFR of three galaxies (325+-120) and CO gas mass  
  > "This is roughly consistent, although somewhat lower, to the sum of the star formation rates inferred from the optical-UV SED fitting or the (extinction-corrected) H$\beta$ emission of the three merging galaxies" (4.3 Continuum thermal emission within the 40 kpc extended structure)
6. **Search for CO systems in field and stack**: Collapse channels of widths 40-200 km/s across band within primary beam >30%; 5.2 sigma threshold; inverted cube false-positive test; stack continuum, HST and Chandra  
  > "To select the reliable CO detections we used a threshold of $\rm 5.2\,\sigma$ for CO peak emission" (4.4)
   - fitting: _not stated_
   - validation: Negative detections in flux-inverted cube: 1 vs 10 positive  
  > "we obtain 10 positive detections and only one negative detection within the spectral window centred onto the CO J=4-3 transition" (4.4)

## Software

- **CASA** 4.5.3: re-flagging, imaging  
  > "using `CASA` version 4.5.3" (3 ALMA Observations and Data Reduction)
- **CIGALE** : IR-to-mm SED fitting  
  > "by using the fitting code CIGALE ((cite: Burgarella2005))" (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(4-3) flux, global structure | 0.30 | 0.05 | Jy km/s | 2 | / Line Flux CO(4-3) / $0.30\pm 0.05$ / $0.17\pm 0.04$ / |
| Molecular gas mass of structure | 2-6e11 | range from alpha_CO and line ratio | Msun | 3 | We infer a mass of the large gaseous structure of $\rm M_{gas}\sim2-6 \times 10^{11} M_{\odot}$. |
| Total SFR of 40 kpc region | 198 | 63 | Msun/yr | 5 | the inferred total star formation rate is $\rm 198\pm 63 ~M_{\odot}yr^{-1}$ |
| Dust mass | 1.58e9 | 0.57e9 | Msun | 5 | $\rm M_{dust}=1.58~(\pm 0.57) ~\times 10^9~M_{\odot}$ |
| Gas mass from dust | 2.1e11 | 0.75e11 | Msun | 5 | we infer a total molecular mass in the central 40 kpc of $\rm 2.1~(\pm 0.75)~\times
10^{11}~M_{\odot}$ |
| CO systems detected in field | 9 (10 positive detections at 5.2 sigma incl. central, 1 negative) | not stated | count | 6 | we obtain 10 positive detections and only one negative detection |
| Average SFR of stacked CO systems from X-ray | 50-120 | not stated | Msun/yr | 6 | average SFR in the range of 50–120 $\rm M_{\odot}yr^{-1}$ |

## Qualitative findings

- CO velocity dispersion low (30-100 km/s) and no coherent rotation in p-v diagram  
  > "The p-v diagram does not show any signature of coherent rotation around the massive galaxy." (4.2)

## Claim tuples

- H: Is there extended molecular gas beyond the galaxies? | E: CO(4-3) mapping of Candels-5001 field | R: Elongated CO structure over 40 kpc; ~60% of mass not associated with galaxies | F: Large CGM molecular reservoir around massive galaxy | **supported**
- H: Is the structure a rotating disc, tidal debris or outflow? | E: Kinematic and mass arguments | R: No coherent rotation, mass too large, low dispersion | F: Interpretation as accreting streams favoured | **supported**
- H: Are there additional gas-rich systems tracing streams on larger scales? | E: Blind CO search and stacking of continuum and X-ray | R: Nine CO systems within 250 kpc, stacked 3 sigma continuum and X-ray | F: Systems form stars inefficiently within streams/protocluster | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Large rotating disc, tidally stripped gas and outflows rejected  
  > "An alternative scenario in which the observed extended CO emission is tracing tidally stripped molecular gas is also not plausible." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Low resolution prevents resolving internal kinematics; Herschel cannot separate extended emission  
  > "We cannot perform a similar SED analysis on spatially resolved basis due to the low angular resolution of the *Herschel* data." (4.3)
- Caveat (inferred, ours): Gas mass dominated by uncertain alpha_CO and CO excitation ratio
- Caveat (inferred, ours): Beam is non-Gaussian; extended emission may be affected by sidelobes/deconvolution
- Caveat (inferred, ours): Accretion interpretation is indirect; astrometric shift applied
- Caveat (inferred, ours): Stream association of distant CO systems with large velocity offsets is uncertain

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00423.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cleaning and mask parameters
- Missing: CIGALE configuration and Herschel photometry
- Missing: Stacking details
- Missing: Astrometric shift exact values
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 4/5, Public data and standard processing, but many imaging and analysis parameters missing.
- Rediscovery candidate: no, Key imaging and detection settings unstated and results depend on assumptions.

## Links

- Companion: (cite: Maiolino2008) (SINFONI [OIII] observations and redshift)
- Companion: (cite: Troncoso2014) (SFR and metallicity of the galaxies)
- Related: GOODS-S
- Related: CANDELS

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 78,
  "stated": 46,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
