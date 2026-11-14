# ALMA Discovery of Dust Belts around Proxima Centauri

`2017ApJ...850L...6A` | The Astrophysical Journal Letters 2017 | first author: Anglada, Guillem | arXiv: 1711.00578 | DOI: 10.3847/2041-8213/aa978b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, exoplanets
- Question: Does Proxima Centauri host circumstellar dust belts (a Kuiper belt analog), and what are their location, temperature and mass?  
  > "aiming at characterizing the architecture of its planetary system through the thermal emission of the surrounding dust." (Introduction)
- Target **Proxima Centauri**: coordinates RA 14h29m42.9485s, Dec -62d40'46.163'' (J2000.0, with proper motion)  
  > "Proxima Centauri, at a distance of 1.3 pc (van Leeuwen 2007), is the closest star to the Sun." (Introduction); "a parallax of 768.13 mas (Lurie et al. 2014)" (Observations); z/distance 1.3 pc  
  > "Proxima Centauri, at a distance of 1.3 pc (van Leeuwen 2007), is the closest star to the Sun." (Introduction); "a parallax of 768.13 mas (Lurie et al. 2014)" (Observations); distance from van Leeuwen 2007; parallax from Lurie et al. 2014  
  > "Proxima Centauri, at a distance of 1.3 pc (van Leeuwen 2007), is the closest star to the Sun." (Introduction); "a parallax of 768.13 mas (Lurie et al. 2014)" (Observations)

## Data provenance

- ALMA projects: 2016.A.00013.S
- bands: Band 6 (1.3 mm)  
  > "we report the first results of ALMA band 6 observations towards the star closest to our Sun" (Introduction)
- frequencies and spectral setup: four spectral windows at 225, 227, 239, 241 GHz, each 1.875 GHz effective bandwidth, 120 channels, dual polarization  
  > "with four spectral windows centered at 225, 227, 239 and 241 GHz, each with a 1.875 GHz effective bandwidth split into 120 channels." (Observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7-m and 12-m array  
  > "using both the Atacama Compact Array (ACA) of 7-m antennas and the main ALMA array of 12-m antennas." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ACA beam ~6''; 12-m beam ~0.7''  
  > "synthesized beam FWHM$\simeq$$0.7''$" (Observations)
- max recoverable scale: ACA <~29''; 12-m <~6''  
  > "Observations were sensitive to angular scales $\ensuremath{\lesssim}6''$." (Observations)
- sensitivity: _not stated_
- time on source: ACA 13 sessions of ~1.6 h each incl. overheads; 12-m single session of 2.6 h  
  > "was used in a single session of 2.6 h on 2017 April 25." (Observations)
- observing dates: ACA 2017 Jan 21 to Mar 24 (13 sessions); 12-m 2017 April 25  
  > "ACA observations were made between 2017 January 21 and 2017 March 24, with 8-11 antennas available, in 13 separate sessions" (Observations)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 1-3 GHz measurements used to estimate non-thermal stellar emission (in prep.)  
  > "as well as our own ATCA measurements between 1 and 3 GHz (J.F. Gómez et al., in prep.)" (3.1 The Emission from the Star)
- External data: Stellar parameters (Teff, mass, radius, luminosity) and SED photospheric model giving 74±4 uJy at 1.3 mm  
  > "giving an extrapolated flux density at 1.3 mm of $74\pm4\,\mu$Jy" (3.1 The Emission from the Star) [from Ribas et al. 2017 (cite: 2017A&A...603A..58R)]
- External data: Proper motion and parallax for phase-center tracking  
  > "proper motions of $-$3775.75 and 765.54 mas yr$^{-1}$ (van Leeuwen et al. 2007)" (Observations) [from van Leeuwen 2007; Lurie et al. 2014]
- External data: Solar Kuiper belt mass ~1e-2 Earth masses for comparison  
  > "This mass is similar to that of the solar Kuiper belt ($\sim10^{-2}~M_\ensuremath{\oplus}$; Bernstein et al. 2004)" (3.2 Dust Around Proxima Centauri) [from Bernstein et al. 2004]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Calibration was performed with the ALMA pipeline, using CASA versions 4.7.0 and 4.7.2 for ACA and 12-m array data, respectively." (Observations)
- casa version: CASA 4.7.0 (ACA), 4.7.2 (12-m)  
  > "using CASA versions 4.7.0 and 4.7.2 for ACA and 12-m array data, respectively." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ACA: Ganymede, Callisto, Titan, J1427-4206, J1517-2422; 12-m: J1617-5848 and Titan  
  > "J1617$-$5848 and Titan were used for absolute flux calibration" (Observations)
- flux scale uncertainty: 7% flux calibration  
  > "absolute errors (5% of the resolution in astrometry and 7% in flux calibration)" (Observations)
- self calibration: attempted, unsuccessful (insufficient S/N)  
  > "Self-calibration was attempted, but was unsuccessful due to insufficient S/N." (Observations)

### Imaging

- task: CASA CLEAN, multifrequency synthesis combining all spws  
  > "Images were obtained by combining all spectral windows in multifrequency synthesis mode, applying a robust parameter of 0.5, and deconvolving with the CLEAN algorithm." (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "applying a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ACA and 12-m data combined in images; ACA epochs assigned the first-epoch position before combining  
  > "all data were assigned the formal position of the first epoch of observation, prior to combination of all epochs." (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dust mass/total mass formulation (collisional cascade) following earlier work  
  > "Following a formulation similar to that of Wyatt & Dent (2002)" (3.2 Dust Around Proxima Centauri) [from Wyatt & Dent (2002)]
- Dust temperature law  
  > "The dust temperature can be approximated as $(T_d/{\rm K})=278\, (L/L_\ensuremath{\odot})^{0.25}\, (r/{\rm au})^{-0.5}$ (Wyatt 2008)." (3.2 Dust Around Proxima Centauri) [from Wyatt 2008]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, number of iterations and clean threshold/masks
- Exact elliptical annulus binning and noise estimation for the 30 au profile
- Which ACA+12m combination weighting was used for combined images
- Detailed derivation of the total flux of 1.7 mJy for the outer belt
- Calculation excluding substellar companion via RV

## Analysis recipe

1. **Image and measure source flux and position**: Multifrequency synthesis CLEAN images; IMSTAT for flux densities, IMFIT for positions and sizes  
  > "Flux densities and intensities were measured with task IMSTAT. Source positions and sizes were determined with task IMFIT." (Observations)
   - software: CASA, IMSTAT, IMFIT
   - parameter: robust 0.5  
  > "applying a robust parameter of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Separate stellar from dust emission**: Compare ALMA 12-m peak and photospheric model prediction with ACA flux  
  > "indicates that $\sim$70-80% of the flux density detected by ACA ($340\pm60\,\mu$Jy; Fig. [1](#fig:aca)) does not arise from the star" (3.1 The Emission from the Star)
   - assumption: Star unresolved; non-thermal emission negligible  
  > "is negligible ($\ll$1 $\mu$Jy)" (3.1 The Emission from the Star)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive dust temperature and masses**: Optically thin dust mass formula with T_d(r) law; total mass scaled via collisional cascade up to 50 km  
  > "Taking $D_{\rm dust}\simeq 1$ cm, we obtain $m_{\rm tot}\simeq2200\, m_{\rm dust}\,(D_{\rm max}/\rm 50\,km)^{0.5}$." (3.2 Dust Around Proxima Centauri)
   - parameter: D_dust 1 cm, D_max 50 km  
  > "if we integrate up to $D_{\rm max}\simeq50$ km" (3.2 Dust Around Proxima Centauri)
   - assumption: kappa_nu = 2 cm^2 g^-1; size distribution power-law index -3.5  
  > "a dust opacity of $\kappa_\nu=2~\rm cm^2~g^{-1}$ has been adopted" (3.2 Dust Around Proxima Centauri)
   - fitting: _not stated_
   - validation: _not stated_
4. **Search for outer belt in ACA data**: Azimuthal averaging over elliptical annuli with a grid of PA and eccentricity  
  > "We analyzed a grid of different position angles and eccentricities of the ellipses." (3.3 A Possible Outer Belt at 30 au)
   - parameter: best PA ~140 deg, i ~45 deg, peak at ~23''  
  > "ellipse PA $\simeq140\ensuremath{^\circ}$ (major axis) and an eccentricity corresponding to an inclination angle $i\simeq45\ensuremath{^\circ}$" (3.3 A Possible Outer Belt at 30 au)
   - assumption: Circular belt tilted; T_d ~10 K with same temperature law  
  > "It would be extremely cold (with $T_d\simeq10$ K, if the same temperature law is assumed)" (3.3 A Possible Outer Belt at 30 au)
   - fitting: _not stated_
   - validation: Peak vanishes progressively for deviating parameters; detection stated as marginal  
  > "Deviations from this combination of parameters produce a progressive vanishing of the feature." (3.3 A Possible Outer Belt at 30 au)

## Software

- **CASA** 4.7.0 (ACA), 4.7.2 (12-m): Calibration, imaging, analysis  
  > "Data were processed using the Common Astronomy Software Applications (CASA) package." (Observations)
- **IMSTAT** : Flux densities and intensities  
  > "Flux densities and intensities were measured with task IMSTAT." (Observations)
- **IMFIT** : Source positions and sizes  
  > "Source positions and sizes were determined with task IMFIT." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ACA flux density | 340 | 60 | uJy | 1 | The source has a flux density of $340\pm60$ $\mu$Jy. |
| 12-m central source flux density | 106 | 12 | uJy | 1 | The flux density is $106\pm12$ $\mu$Jy |
| Secondary source flux density | 38 | 10 | uJy | 1 | A secondary source with a flux density of $38\pm10$ $\mu$Jy is marginally detected |
| Dust temperature (1-4 au belt) | ~40 | not stated | K | 3 | we obtain $T_d\simeq40$ K and a dust mass $m_d\simeq4\times10^{-6}~M_\ensuremath{\oplus}$. |
| Total mass inner belt | ~1e-2 | not stated | Earth masses | 3 | we obtain a total mass of $m_{\rm tot}\simeq10^{-2}~M_\ensuremath{\oplus}$. |
| Outer belt total flux density | ~1.7 | not stated | mJy | 4 | we estimate a total flux density of $\sim$ 1.7 mJy |
| Outer belt total mass | 0.33 | not stated | Earth masses | 4 | corresponding to a total mass (including large bodies) of $0.33~M_\ensuremath{\oplus}$ |

## Qualitative findings

- Marginal compact source at 1.2'' could be a background galaxy, Trojan cloud, or ring around an undiscovered giant planet; second epoch needed  
  > "Given the large proper motions of the star, a second-epoch observation would easily reveal whether this source moves together with the star" (3.4 A Ring around an Undiscovered Planet)

## Claim tuples

- H: Proxima Cen has circumstellar dust belt(s) | E: Compare ACA, 12-m and stellar model fluxes | R: ACA 340 uJy vs stellar 74 uJy; ~270 uJy excess spread over 1-4 au | F: A Kuiper belt analog at 1-4 au, T~40 K, mass ~0.01 Earth masses | **supported**
- H: A cold outer belt exists at ~30 au | E: Elliptical annulus averaging of ACA image | R: Peak at ~23'' for PA 140 deg, i 45 deg | F: Tentative outer belt requiring confirmation | **partially**
- H: Warmer dust near star | E: Elongation of 12-m central source | R: Excess ~30 uJy, T~90 K | F: Hint of warm inner dust | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Secondary source as background galaxy, substellar companion (rejected via RV), collisional cloud, Trojan cloud, or planetary ring  
  > "A substellar companion with a temperature of the order of 1000 K could also produce the observed emission." (3.4 A Ring around an Undiscovered Planet)
- How they decided it was enough: _not stated_
- Limitation (authors): Data insufficient for proper modeling; secondary source could be a noise peak  
  > "While our data are insufficient for a proper modeling" (3.2 Dust Around Proxima Centauri)
- Caveat (inferred, ours): Dust mass depends on a crude temperature law and a single opacity
- Caveat (inferred, ours): Outer belt and secondary source are marginal (~4 sigma) and not independently verified
- Caveat (inferred, ours): ACA flux may include background sources or ISM within 6'' beam

## Reproducibility

- Data public (paper): ALMA data identified by project code 2016.A.00013.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.A.00013.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust 0.5
- Missing: Elliptical annulus profile procedure details
- Data volume (inferred): ~20-50 GB (13 ACA sessions plus one 12-m session, raw)
- Score (inferred): 6/5, Short letter with data code and basic processing but limited imaging and profile details.
- Rediscovery candidate: yes, Data are public, recipe is simple, and the main results are numeric flux densities and masses.

## Links

- Method: Wyatt & Dent 2002 (Collisional cascade total mass formulation)
- Companion: Ribas et al. 2017 (cite: 2017A&A...603A..58R) (Stellar SED model giving the photospheric flux)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 73,
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
