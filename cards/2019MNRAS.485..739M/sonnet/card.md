# Asymmetric mid-plane gas in ALMA images of HD 100546

`2019MNRAS.485..739M` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Miley, J. M. | arXiv: 1902.07506 | DOI: 10.1093/mnras/stz426

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust and gas masses, gas-to-dust ratio, azimuthal asymmetry and radial grain-size trends in the HD 100546 disc, using new Band 6 continuum, 13CO and first-detected C18O plus archival Band 7 continuum?  
  > "In this paper we present new ALMA observations towards Herbig Ae/Be star HD 100546 in order to characterise the dust and gas in its disc." (1 Introduction)
- Target **HD 100546**: coordinates 11h33m25.3209s -70d11m41.2432s (Gaia DR2, proper-motion corrected)  
  > "The star is located at a distance of 110pc (cite: Lindegren2018)" (2 HD 100546); "giving a position of 11h33m25.3209s -70d11m41.2432s" (4 Results); z/distance 110 pc  
  > "The star is located at a distance of 110pc (cite: Lindegren2018)" (2 HD 100546); "giving a position of 11h33m25.3209s -70d11m41.2432s" (4 Results); distance from Lindegren2018 (Gaia DR2)  
  > "The star is located at a distance of 110pc (cite: Lindegren2018)" (2 HD 100546); "giving a position of 11h33m25.3209s -70d11m41.2432s" (4 Results)

## Data provenance

- ALMA projects: 2015.1.01600.S, 2011.0.00863.S
- bands: Band 6 (new, 1.3 mm); Band 7 (archival, 867 um)  
  > "We present new ALMA observations of HD 100546 with band 6 receivers across 4 unique spectral windows (SPWs)" (3 Observations & Data Reduction)
- frequencies and spectral setup: SPW0 232 GHz and SPW1 234 GHz continuum (128 channels of 15625 kHz); SPW2 13CO at 220398 MHz (1920 channels, 61.035 kHz); SPW3 C18O at 219560 MHz (3840 channels, 0.166 km/s)  
  > "SPW2 contains 1920 channels of width 61.035 kHz, which at central frequency 220398 MHz gives resolution of 0.083kms$^{-1}$" (3 Observations & Data Reduction)
- continuum bandwidth: 2 GHz total  
  > "to give a total bandwidth of 2 GHz" (3 Observations & Data Reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-460 m, 43 antennas  
  > "employing 43 antennas with a baseline range of 15-460 metres" (3 Observations & Data Reduction)
- angular resolution: 1.05x0.77 arcsec continuum  
  > "giving a synthesized beam of 1$\ensuremath{''}$05 x 0$\ensuremath{''}$77, P.A. = -20$^{\circ}$ for the continuum image" (3 Observations & Data Reduction)
- max recoverable scale: 10.6 arcsec (Band 6); 5.3 arcsec (Band 7)  
  > "giving a maximum angular scale of 10$\ensuremath{''}$6." (3 Observations & Data Reduction)
- sensitivity: continuum rms 0.5 mJy/beam  
  > "measured with an image rms of 0.5 mJy/beam" (4 Results)
- time on source: 625 s  
  > "for a total time of 625s on source" (3 Observations & Data Reduction)
- observing dates: 28 March 2016  
  > "Observations were made on the 28th March 2016" (3 Observations & Data Reduction)
- pi or archival as stated: _not stated_
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **HST ACS**: F435W scattered-light image (Ardila2007) compared with C18O  
  > "Figure [5](#fig:hst) displays the HST image in the F435W band presented by (cite: Ardila2007)." (5.2.1 Evidence in ALMA Images)
- Other facility **Gaia DR2**: stellar position and distance  
  > "We adjusted the GAIA data release 2 (2018) position of HD 100546 for proper motion" (4 Results)
- External data: dust opacity kappa(1.3mm)=1.15 cm2/g for amax=1 mm, and opacity indices beta  
  > "Assuming a maximum grain size $a_{\rm max}$ = 1 mm yields $\kappa_{1.3 \rm mm}$ = 1.15 $\rm cm^{2}g^{-1}$ (cite: Draine2006)." (5.1.1 Dust Mass) [from (cite: Draine2006)]
- External data: ISM ratio CO/C18O ~ 550  
  > "CO/C$^{18}\rm O \sim$ 550 (cite: Wilson1994)" (5.1.2 Gas Mass) [from (cite: Wilson1994)]
- External data: 13CO/C18O = 8 ISM ratio  
  > "the isotopic ratio $^{13}$CO/C$^{18}$O=8 based on ISM values (cite: Wilson1999)" (5.2 Radial Flux Profiles) [from (cite: Wilson1999)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0  
  > "Calibration and reduction was carried out using CASA version 4.7.0." (3 Observations & Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449  
  > "The flux calibrator was J1107-4449" (3 Observations & Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Self-cal using line-free continuum channel models, solutions applied to all channels; solint not given  
  > "Line free continuum channels were used to construct image models to be used for self-calibration, the solutions were then applied to all channels." (3 Observations & Data Reduction)

### Imaging

- task: CASA CLEAN  
  > "imaging was performed using CASA tasks and the CLEAN algorithm (cite: Rau2011)" (3 Observations & Data Reduction)
- deconvolver: _not stated_
- weighting robust: briggs, robust=0.5  
  > "images were created with briggs weighting and robust=0.5" (3 Observations & Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "by subtracting the continuum from SPWs containing the line emission using CASA task *uvcontsub*" (3 Observations & Data Reduction)
- line free channels: _not stated_
- primary beam correction: not applied  
  > "Source emission is contained within the inner third of the primary beam and so primary beam correction was not applied to images." (3 Observations & Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 13CO 1.08x0.82 arcsec; C18O 1.10x0.83 arcsec; Band 7 continuum 0.95x0.42 arcsec, later imaged with Band 6 beam  
  > "The continuum from this data is imaged using the same beam as the band 6 1.3mm continuum." (5.4 Spectral Index)
- final rms: 1.3 mm 0.5 mJy/beam; 13CO 0.033 and C18O 0.027 Jy/beam km/s  
  > "with rms noise 0.033 Jy/beam kms$^{-1}$ and 0.027 Jy/beam kms$^{-1}$ respectively" (4 Results)

### Inherited from earlier work

- Band 7 data originally reduced by Walsh et al.; re-reduced here  
  > "We re-reduce and image this data, applying self calibration as described above" (3 Observations & Data Reduction) [from (cite: Walsh2014)]
- beta method for non-Rayleigh-Jeans  
  > "we take an approach similar to that of (cite: Guidi2016) and calculate $\beta_{\rm mm}$" (5.4 Spectral Index) [from (cite: Guidi2016)]
- gas mass formula  
  > "we calculate the total gas mass similarly to (cite: Hughes2008; Matra2015; White2016)" (5.1.2 Gas Mass) [from (cite: Hughes2008; Matra2015; White2016)]

### Not stated but needed to reproduce (our reading)

- self-calibration solution intervals, number of rounds, and which continuum channels
- CLEAN threshold, masks, cell and image size
- line-free channels for uvcontsub
- Band 7 calibration and imaging details (robust, flux scale)
- how the uvcontsub-based uniform disc fit was actually done
- CO excitation/partition details for the gas-mass temperature range
- flux calibrator flux density and flux-scale uncertainty

## Analysis recipe

1. **Calibrate, self-calibrate and image**: CASA 4.7.0 calibration, self-cal, CLEAN with briggs robust=0.5, uvcontsub, immoments  
  > "Integrated intensity, from which fluxes are measured, and intensity weighted velocity maps were created with CASA task *immoments*" (3 Observations & Data Reduction)
   - software: CASA
   - parameter: robust=0.5; channels with >3 sigma signal summed  
  > "by summing all emission in channels containing significant (\>3$\sigma$) signal" (3 Observations & Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Determine geometry and centre of emission**: Minor axis from systemic-velocity channel; elliptical Gaussian fit with PA prior for inclination; image- and uv-plane centre fits  
  > "we then fit an elliptical Gaussian to each of the CO isotopologue integrated emission maps to determine inclinations" (4 Results)
   - software: CASA
   - fitting: 2D Gaussian in image; uniform elliptical disc in uv  
  > "fitting a uniform, elliptical disc geometry in the uv plane" (4 Results)
   - validation: compared with Walsh2014 and Pineda2014 geometry; astrometric error budget 50 mas  
  > "We adopt this greater value of 50 mas as a conservative uncertainty on coordinate positions in the image." (4 Results)
3. **Dust mass**: Optically thin flux-to-mass relation within 3 sigma contour  
  > "We measure the flux within a 3$\sigma$ contour of the 1.3 mm continuum image." (5.1.1 Dust Mass)
   - parameter: T = 20-40 K; amax = 1 mm; kappa = 1.15 cm2/g  
  > "we therefore adopt a range of 20K – 40K" (5.1.1 Dust Mass)
   - assumption: dn/da ∝ a^-3.5  
  > "assuming a dust grain size distribution $dn/da \propto a^{-3.5}$ (cite: Mathis1977)" (5.1.1 Dust Mass)
   - fitting: _not stated_
   - validation: compared with Wright2015 and Band 7 flux estimate  
  > "a disc mass of 0.7$\times 10^{-3}~$M$_{\odot}$ is found" (5.1.1 Dust Mass)
4. **Gas mass and g/d**: Optically thin LTE C18O (2-1) mass, ISM abundances, over range of T; g/d from T=20 K masses  
  > "assuming optically thin emission and local thermodynamic equilibrium, we calculate the total gas mass" (5.1.2 Gas Mass)
   - parameter: CO/H2 ~1e-4; CO/C18O ~550; minimum at 20 K  
  > "The minimum gas mass was calculated with a temperature of 20 K, giving a minimum disc gas mass of 0.018 M$_{\odot}$." (5.1.2 Gas Mass)
   - assumption: ISM C18O abundance, no isotope-selective photodissociation or freeze-out  
  > "The calculated gas mass assumes ISM abundances of C$^{18}$O relative to CO." (5.1.2 Gas Mass)
   - fitting: _not stated_
   - validation: treated as lower limit  
  > "In light of the discussion above, our calculated gas estimate represents a firm lower limit, but a very large one in comparison to other Herbig discs." (Gas Mass)
5. **Asymmetry: density vs temperature**: Flux ratios of 60-degree segments on opposite sides; required density or temperature change; Toomre Q  
  > "We split each half of the disc, bisected along the major axis, into three 60$^\circ$ degree segments and sum the flux in the segment." (5.3.1 Density Scenario)
   - fitting: _not stated_
   - validation: compared against Panic2017 models  
  > "the radiative transfer models of (cite: Panic2017) show that in reality an increase in disc temperature from 20 to 32K" (Temperature Scenario)
6. **Radial profiles and extent**: Deproject (i=43, PA=144) and azimuthally average; noise from off-source polynomial fits; edge where flux < 2x noise  
  > "we take this to be the point at which the average flux becomes less than 2 times the average noise fluctuations at that radius" (5.2 Radial Flux Profiles)
   - fitting: polynomials fitted to off-source fluctuations  
  > "The amplitudes of these fluctuations as a function of radius are fitted with polynomials, the polynomials are then averaged over the different off-source locations." (Radial Flux Profiles)
   - validation: surface density comparison across tracers  
  > "We explore this by calculating surface density profiles for each tracer, which are plotted in Figure [10](#fig:surf_dens)." (Radial Flux Profiles)
7. **Spectral and opacity index radial profile**: Azimuthally averaged 867 um and 1.3 mm profiles, beta from d log F - d log B over d log nu  
  > "calculate $\beta_{\rm mm}$ with" (5.4 Spectral Index)
   - parameter: T(R)=T100 (R/R100)^0.5, T100=25 K  
  > "We adopt a temperature profile that obeys a power law, $T(R) = T_{100}~( R/R_{100} )^{0.5}$, and take $T_{100}$=25K." (5.4 Spectral Index)
   - assumption: p=3.5 size distribution; optically thin  
  > "We have assumed in our analysis that dust grains in the disc have a size distribution of $dn/da \propto a^{-p}$, where p=3.5" (Spectral Index)
   - fitting: _not stated_
   - validation: optical depth check; temperature sensitivity test  
  > "The results are shown in Figure [13](#fig:opt_depth) and suggest that over all emissivities tested, the 1.3 mm emission is always optically thin for the entirety of the disc." (Spectral Index)

## Software

- **CASA** 4.7.0: calibration, imaging, uvcontsub, immoments  
  > "Calibration and reduction was carried out using CASA version 4.7.0." (3 Observations & Data Reduction)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgements)
- **Astropy** : general analysis  
  > "of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum flux | 492 | not stated | mJy | 1 | The integrated continuum flux in the 1.3 mm image of 492 mJy |
| 13CO (2-1) integrated flux | 12.872 | not stated | Jy km/s | 1 | The $^{13}$CO (2-1) integrated flux is measured at 12.872 Jy kms$^{-1}$ |
| C18O (2-1) integrated flux | 2.948 | not stated | Jy km/s | 1 | an integrated flux of 2.948 Jy kms$^{-1}$ for the (2-1) transition |
| position angle | 144 | 2.4 | deg | 2 | The average value of the two is $144\pm 2.4^\circ$ which we adopt henceforth. |
| inclination | 43 | not stated | deg | 2 | We adopt an average inclination of $43^{\circ}$ for all further analysis. |
| systemic velocity | 5.42 | not stated | km/s | 2 | giving 5.42 kms$^{-1}$ |
| dust mass | 4.1e-4 (40 K) to 9.6e-4 (20 K) | not stated | Msun | 3 | 4.1$\times 10^{-4}~$M$_{\odot}$ for $T$= 40 K, and 9.6$\times 10^{-4}~$M$_{\odot}$ for $T$= 20 K |
| minimum gas mass (T=20 K) | 0.018 | not stated | Msun | 4 | giving a minimum disc gas mass of 0.018 M$_{\odot}$ |
| gas-to-dust ratio | 19 | not stated | dimensionless | 4 | we calculate a g/d for HD 100546 of $\approx$ 19 |
| outer radius continuum / 13CO / C18O | 286 / 385 / 297 | 11 | au | 6 | detected as far out as 385$\pm$11 au |
| SW/NE brightness ratio, outer disc C18O | 1.27 | 0.18 | dimensionless | 5 | the brightness ratio is 1.27$\pm$0.18 |
| minimum Toomre Q | ~24 at ~80 au | not stated | dimensionless | 5 | Q(R) for this disc reaches a minimum $\sim 24$ at $\sim$80 au |
| C18O optical depth maximum | 0.68 | not stated | dimensionless | 6 | with $\tau \le$ 0.68 |
| inner spectral index | 2.1, rising by ~0.3 outward | not stated | dimensionless | 7 | begins in the inner disc with a value of 2.1 and steadily rises with radius by $\Delta \alpha_{\rm mm} \approx$ 0.3 |

## Qualitative findings

- Extended C18O emission bulges coincide with HST scattered-light spiral structures.  
  > "Each of the low-level bulges in the extended C$^{18}$O (2-1) emission is found in the same region of the disc as one of the 3 scattered light structures." (5.2.1 Evidence in ALMA Images)
- Emission centres are offset from the stellar position by ~70-110 mas.  
  > "the disc is seen to have a puzzling offset from the known stellar position of between $\approx$70-110 milliarcseconds" (Conclusions)

## Claim tuples

- H: The disc retains a large gas reservoir | E: Optically thin C18O mass with ISM abundances | R: Mg ≥ 0.018 Msun, g/d ≈ 19 | F: Large lower-limit gas mass for a transition disc | **supported**
- H: Mid-plane gas is asymmetric and linked to scattered-light spirals | E: Compare C18O maps with HST, segment flux ratios | R: Ratio 1.27±0.18 in outer disc; bulges coincide with structures | F: Density increase needed; temperature alone is ruled out | **partially**
- H: Grain sizes increase toward the star | E: Radial alpha and beta between 867 um and 1.3 mm | R: alpha rises outward from 2.1; beta indicates cm grains | F: Radial grain-size sorting, cm sizes inside ~200 au | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O is used because it is less optically thick and traces the dense mid-plane.  
  > "In this study we observe C$^{18}$O, a less optically thick alternative to other CO isotopologues" (1 Introduction)
- Alternative: Temperature-only and gravitational instability explanations for the asymmetry rejected.  
  > "Calculation of the Toomre parameter, Q, based on the radial profile of C$^{18}$O rules out gravitational instability in the disc." (5.3.1 Density Scenario)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass is a lower limit because C18O/CO abundance could differ from ISM values.  
  > "so our calculation represents a lower limit" (5.1.2 Gas Mass)
- Limitation (authors): Resolution of ~1 arcsec dilutes azimuthal variations.  
  > "Given the 1$\ensuremath{''}$0 resolution of the data, it is feasible that there are much larger azimuthal density variations" (5.3.1 Density Scenario)
- Caveat (inferred, ours): Dust temperature and opacity assumptions dominate mass and beta uncertainty
- Caveat (inferred, ours): Band 6 vs Band 7 flux-scale uncertainty and different uv coverage affect spectral index
- Caveat (inferred, ours): Asymmetry significance depends on a 1 arcsec beam and uncertain astrometry
- Caveat (inferred, ours): Gas-to-dust ratio depends on assumed ISM isotope ratio

## Reproducibility

- Data public (paper): Both datasets given by ALMA project code; archival Band 7 stated as archival  
  > "We also utilise archival cycle 0 ALMA observations of HD 100546 in band 7" (3 Observations & Data Reduction)
- Products in archive: _not stated_
- Missing: self-cal parameters
- Missing: CLEAN parameters
- Missing: exact flux used in mass calculation
- Missing: segment definitions detail
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data are public and main steps are described, but many imaging and self-calibration parameters are missing.
- Rediscovery candidate: yes, Public data, numeric results (fluxes, masses, g/d) are well defined, though imaging details are partly missing.

## Links

- Method: (cite: Draine2006) (Opacity and beta calculations)
- Method: (cite: Guidi2016) (Spatially resolved beta approach)
- Companion: (cite: Walsh2014) (Original Band 7 observations of HD 100546)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 62,
  "rate": 0.713
 },
 "evidence_ok": true
}
```
