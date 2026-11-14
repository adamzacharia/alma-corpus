# ALMA Observations of the Extraordinary Carina Pillars: HH 901/902

`2020AJ....159...62C` | The Astronomical Journal 2020 | first author: Cortes-Rangel, Geovanni | arXiv: 1911.11026 | DOI: 10.3847/1538-3881/ab6295

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the molecular outflows, dusty disks/envelopes and pillar kinematics and masses of the HH 901/902 protostellar objects in Carina, and how fast will the pillars photo-evaporate?  
  > "In this study, we have carried out new ALMA observations of the HH 901/HH 902 objects in order to better characterize their optical jets, disks, and molecular pillars." (Introduction)
- Target **HH 902**: coordinates RA(J2000)=10h44m01.7s, Dec(J2000)=-59d30'32.0''  
  > "$\delta(J2000) = -59^\circ~ 30'~ 32.0''$ for the HH 902" (Observations); z/distance 2.3±0.1 kpc  
  > "$\delta(J2000) = -59^\circ~ 30'~ 32.0''$ for the HH 902" (Observations); distance from Smith & Brooks 2008 (cite: sb2008), distance to Carina Nebula  
  > "$\delta(J2000) = -59^\circ~ 30'~ 32.0''$ for the HH 902" (Observations)
- Target **HH 901**: coordinates RA(J2000)=10h44m03.5s, Dec(J2000)=-59d31'2.0''  
  > "$\alpha(J2000) = 10^h~ 44^m~ 3\rlap.^s5$; $\delta(J2000) = -59^\circ~ 31~ 2.0''$ for the HH 901" (Observations); z/distance 2.3±0.1 kpc  
  > "$\alpha(J2000) = 10^h~ 44^m~ 3\rlap.^s5$; $\delta(J2000) = -59^\circ~ 31~ 2.0''$ for the HH 901" (Observations); distance from Smith & Brooks 2008 (cite: sb2008), distance to Carina Nebula  
  > "$\alpha(J2000) = 10^h~ 44^m~ 3\rlap.^s5$; $\delta(J2000) = -59^\circ~ 31~ 2.0''$ for the HH 901" (Observations)

## Data provenance

- ALMA projects: 2017.1.00912.S
- bands: Band 6 (1.3 mm)  
  > "carried out with the ALMA at Band 6 in 2018 January 1st and 4th (C43-6), and April 20th (C43-3)" (Observations)
- frequencies and spectral setup: four spws at 218.014, 219.578, 231.239, 230.556 GHz; channel spacing 0.63 km/s  
  > "four spectral windows centered at: 218.014 GHz(spw0), 219.578 GHz(spw1), 231.239 GHz(spw2), and 230.556 GHz(spw3)" (Observations)
- continuum bandwidth: about 4.3 GHz  
  > "The total bandwidth for the continuum is about 4.3 GHz." (Observations)
- arrays: _not stated_
- configurations: C43-6 and C43-3  
  > "2018 January 1st and 4th (C43-6), and April 20th (C43-3)" (Observations)
- baselines: 15-2516 m (C43-6); 15-500 m (C43-3)  
  > "baselines with projected lengths from 15 $-$ 2516 m (11.5 $-$ 1935 k$\lambda$) for C43-6 and 15 $-$ 500 m (11.5 $-$ 384.6 k$\lambda$) for C43-3" (Observations)
- angular resolution: 0.32'' x 0.27'' PA -65 deg (continuum)  
  > "50 $\mu$Jy beam$^{-1}$ at a angular resolution of 0.32$''$ $\times$ 0.27$''$ with a PA of $-$65$^\circ$ for both images" (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 50 uJy/beam; line rms 6.5 mJy/beam km/s  
  > "For the line image rms noise we obtained a value of 6.5 mJy beam$^{-1}$ km s$^{-1}$" (Observations)
- time on source: about 9 min (C43-6), about 3.5 min (C43-3)  
  > "for the C43-6 configuration was about 9 min. and for the C43-3 configuration is about 3.5 min." (Observations)
- observing dates: 2018 Jan 1 and 4, April 20  
  > "in 2018 January 1st and 4th (C43-6), and April 20th (C43-3)" (Observations)
- pi or archival as stated: _not stated_
- Line: C18O 2-1 (219.56035 GHz)
- Line: 13CS 5-4 (231.22068 GHz)
- Line: N2D+ 3-2 (231.32186 GHz)
- Line: 12CO 2-1 (230.53800 GHz)
- Other facility **HST/ACS**: Halpha optical jet images of HH 901/902 used as overlays  
  > "we present the *HST/ACS* image from (cite: smi2010) of the optical jet HH 901 overlaid with the ALMA high velocity CO(2$-$1)" (HH 901)
- External data: Jet inclination ~20 deg to plane of sky  
  > "where $\theta$ is the inclination angle taken to be 20$^\circ$ (cite: rei2013; rei2014)" (HH 901) [from (cite: rei2013; rei2014)]
- External data: Tr 14 UV luminosity Q_H = 2e50 photon/s  
  > "The Tr 14 cluster has an UV luminosity $(Q_H)$ of $2 \times 10^{50} \mathrm{\ photon\ s^{-1}}$ (cite: sb2008)" (HH 901) [from (cite: sb2008)]
- External data: Dust mass opacity 0.015 cm2/g at 1.3 mm  
  > "Assuming a dust mass opacity ($\kappa_\nu$) of 0.015 cm$^2$ g$^{-1}$ (taking a dust-to-gas ratio of 100) appropriate for these wavelengths (1.3 mm) (cite: Oss1994)" (HH 901) [from (cite: Oss1994)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1  
  > "using the Common Astronomy Software Applications (CASA) Version 5.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0904-5735 and J1107-4449 (bandpass and flux); J1032-5917 gain  
  > "Quasars, J0904-5735 and J1107-4449 were used for the bandpass and flux calibrations. J1032-5917 was used for correcting the gain fluctuations." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Attempted on continuum, no significant improvement, not used  
  > "Phase self-calibration was attempted on the continuum images but the resulting maps did not improved significantly" (Observations)

### Imaging

- task: CLEAN and TCLEAN; CONCAT to combine configurations  
  > "Imaging of the calibrated visibilities was done using the CLEAN and TCLEAN tasks." (Observations)
- deconvolver: _not stated_
- weighting robust: natural for main images; robust = 0.5 for Gaussian fits  
  > "We used the ROBUST parameter of CLEAN in CASA set to natural." (Observations); "from a map obtained using ROBUST parameter equal to 0.5 (yielding a better angular resolution)" (HH 901)
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
- final beam: 0.32'' x 0.27'' PA -65 (continuum); 0.31'' x 0.26'' PA -64 (lines)  
  > "at a angular resolution of 0.31$''$ $\times$ 0.26$''$ with a PA of $-$64$^\circ$" (Observations)
- final rms: 50 uJy/beam continuum  
  > "The resulting image rms noise for the continuum was 50 $\mu$Jy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Column and volume density procedure  
  > "We can also estimate the volumetric and column density following the procedure described in (cite: her2014)." (HH 901) [from (cite: her2014)]
- CO mass equation (LTE, J=2-1)  
  > "we can estimate the masses using the equations presented in (cite: sco1986; palau2007) for the J=2$-$1 transition" (HH 901) [from (cite: sco1986; palau2007)]
- EUV photo-evaporation rate approach  
  > "Following (cite: del2016), we can estimate the photo-evaphoration time-scale for the pillar or globulette associated with the HH 901 object." (HH 901) [from (cite: del2016)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Clean threshold, masks, cell and image size
- Which continuum/moment velocity ranges and clip levels
- How the continuum beta=1.2 was derived
- Which archival calibration (pipeline or manual) was used
- Exact method for average intensities and areas in mass equation
- How 0.1 Msun and flux uncertainties were propagated

## Analysis recipe

1. **Calibrate, concatenate and image**: CASA calibration, CONCAT of C43-6 and C43-3, CLEAN/TCLEAN with natural weighting  
  > "We concatenated the data from both dates for the C43-6 and C43-3 configurations with the CONCAT task." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared rms to theoretical noise (43 uJy/beam)  
  > "The ALMA theoretical rms noise for this configuration, integration time, and frequency is about 43 $\mu$Jy beam$^{-1}$" (Observations)
2. **Fit continuum sources and derive disk+envelope dust mass**: Gaussian fit to robust=0.5 map; optically thin isothermal dust mass equation  
  > "Assuming that the dust emission is optically thin and isothermal, the dust mass (M$_\mathrm{d}$) is directly proportional to the flux density" (HH 901)
   - software: CASA
   - assumption: kappa=0.015 cm2/g, beta=1.2, Td=50 K (30 K for source B), dust-to-gas 100, D=2.3 kpc  
  > "a typical opacity power-law index $\beta$ = 1.2 (obtained from our ALMA data), as well as a characteristic dust temperature of 50 K" (HH 901)
   - fitting: Gaussian fit  
  > "From a gaussian fitting to the continuum source from a map obtained using ROBUST parameter equal to 0.5 (yielding a better angular resolution), we obtained a deconvolved size of" (Results and discussion, HH 901)
   - validation: Mass uncertainty factor 3-4 acknowledged  
  > "The mass uncertainty could be very large (a factor of up to 3 or 4)" (HH 901)
3. **Outflow and pillar gas masses from C18O/CO**: LTE mass equation with opacity correction, inclination correction for outflow; energy, momentum, force  
  > "we corrected the mass value by a factor of $\left[\frac{\tau_0}{1-\mathrm{exp}(-\tau_0)}\right]$" (HH 901)
   - parameter: Tex=50 K, X(H2/CO)~1e4, mean molecular weight 2.8, inclination 20 deg  
  > "an excitation temperature ($T_\mathrm{ex}$) of 50 K" (HH 901)
   - assumption: tau0=0.2 from C18O/12CO ratio ~5  
  > "we estimate an average opacity ($\tau_0$) of 0.2" (HH 901)
   - fitting: _not stated_
   - validation: Pillar mass consistent with Reiter & Smith 2013 volume-density estimate  
  > "this mass estimation is in agreement with the mass obtained for the HH 901 pillar using a volumetric density of 10$^5$ cm$^{-3}$" (HH 901)
4. **Photo-evaporation timescale**: EUV mass-loss rate formula, timescale = pillar mass / rate  
  > "we obtain a mass photo-evaporation rate ${\dot M}$ equal to 1 $\times$ 10$^{-6}$ M$_\odot$ year$^{-1}$." (HH 901)
   - parameter: F_EUV=1e12 photon/s/cm2; R=1000 au (HH 901), 4000 au (HH 902)  
  > "a radius of 4 $\times$ 10$^3$ au" (HH 902)
   - assumption: Only Tr 14 considered, Tr 16 ignored  
  > "we ignored at this point the radiation for the massive cluster located also in this region Tr 16" (HH 901)
   - fitting: _not stated_
   - validation: Compared with globulette 105-600 timescale (~1e6 yr)  
  > "This timescale is shorter to that estimated, for example, for the massive EGG or globulette 105-600 (cite: del2016) of about 10$^6$ years." (HH 901)

## Software

- **CASA** 5.1: calibration, imaging, analysis (CLEAN, TCLEAN, CONCAT)  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA) Version 5.1." (Observations)
- **KARMA** : listed in software section  
  > "CASA(cite: mac2007), KARMA(cite: goo1996)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HH 901 continuum deconvolved size | 0.49'' x 0.33'' PA 100 deg | ±0.03'' ±0.03'' ±7 deg | arcsec | 2 | we obtained a deconvolved size of 0.49$''$ $\pm$ 0.03$''$ $\times$ 0.33$''$ $\pm$ 0.03$''$ with a PA of 100$^\circ$ $\pm$ 7$^\circ$ |
| HH 901 integrated continuum flux | 6.8 | ±0.4 | mJy | 2 | an integrated flux of 6.8 $\pm$ 0.4 mJy Beam$^{-1}$ |
| HH 901 disk+envelope mass | ~0.1 | factor 3-4 | Msun | 2 | of the disk and envelope system associated with HH 901 of about 0.1 M$_\odot$ |
| HH 902 A integrated flux | 6.5 | ±0.7 | mJy | 2 | an integrated flux of 6.5 $\pm$ 0.7 mJy Beam$^{-1}$ |
| HH 902 source B flux density | 38 | ±2.0 | mJy | 2 | has a flux density of 38 $\pm$ 2.0 mJy Beam$^{-1}$ |
| HH 901 outflow mass (inclination corrected) | 1e-3 | not stated | Msun | 3 | so the $dv_{real}$ = 16 km s$^{-1}$ and the mass is 10$^{-3}$ M$_\odot$ |
| HH 901 pillar mass | ~0.1 | not stated | Msun | 3 | for the pillar of $\sim$ 0.1 M$_\odot$ |
| HH 902 pillar mass | ~0.2 | not stated | Msun | 3 | for the pillar of $\sim$ 0.2 M$_\odot$ |
| HH 901 outflow force F_CO | 1.5e-5 | not stated | Msun/yr km/s | 3 | we obtain a value of 1.5 $\times$ $10^{-5}$ M$_\odot$ yr$^{-1}$ km s$^{-1}$ |
| HH 901 pillar photo-evaporation time | ~1e5 | not stated | yr | 4 | the pillar will be photo-evaporated in around 10$^5$ years |
| HH 902 pillar photo-evaporation time | ~2e4 | not stated | yr | 4 | photo-evaporated in around 2 $\times$ 10$^4$ years |

## Qualitative findings

- Bipolar CO outflows and compact dusty disks/envelopes detected for HH 901/902; N2D+ traces only dense gas coincident with continuum  
  > "Our observations reveal for the first time, the bipolar CO collimated outflows, and the dusty disks (plus envelopes)" (Conclusions)

## Claim tuples

- H: HH 901/902 are driven by embedded protostars with compact outflows and disks | E: ALMA 1.3 mm continuum and CO line imaging | R: Bipolar CO outflows and 0.1 Msun disk+envelope detected | F: Driving sources are low- or maybe intermediate-mass Class 0/I protostars | **supported**
- H: Pillars will be photo-evaporated quickly | E: EUV photo-evaporation rate from Tr 14 and pillar masses | R: 1e5 yr (HH 901), 2e4 yr (HH 902) | F: Disks inside will be affected soon, forming proplyds | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-calibrated continuum maps not used since no significant improvement  
  > "so at this point we did not used the self-calibrated maps" (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust emission probably not optically thin, so masses are lower limits; mass uncertainty factor 3-4  
  > "hence the estimated mass is considered to be the lower limit" (HH 901)
- Caveat (inferred, ours): Single short integrations; flux units given as mJy/beam for integrated fluxes
- Caveat (inferred, ours): Assumed Tex and Td uniform, not measured
- Caveat (inferred, ours): Photo-evaporation uses only Tr 14 and a simple formula
- Caveat (inferred, ours): Short baseline mass filtering unquantified

## Reproducibility

- Data public (paper): ALMA project code given; acknowledgement of ADS/JAO.ALMA#2017.1.00912.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00912.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters, masks, image sizes
- Missing: Line-free channel selection
- Missing: Exact intensity/area values behind mass equation
- Missing: Calibration pipeline details
- Data volume (inferred): ~20-50 GB for raw MSs of two configurations
- Score (inferred): 3/5, Data are public and the analysis is simple with stated assumptions, but imaging details and extraction choices are missing.
- Rediscovery candidate: yes, Public data, simple recipe with numeric masses and fluxes, though imaging details are partly missing.

## Links

- Method: (cite: sco1986; palau2007) (CO mass equation)
- Method: (cite: her2014) (column and volume density procedure)
- Companion: (cite: del2016) (ALMA disks in Carina and photo-evaporation formulation)
- Companion: (cite: rei2013; rei2014) (HH 901/902 optical studies)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 50,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
