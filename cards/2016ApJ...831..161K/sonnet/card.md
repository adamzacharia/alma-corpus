# Ocular Shock Front in the Colliding Galaxy IC 2163

`2016ApJ...831..161K` | The Astrophysical Journal 2016 | first author: Kaufman, Michele | arXiv: 1608.02130 | DOI: 10.3847/0004-637X/831/2/161

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Do the ALMA CO velocity fields show gas streaming into the eyelids of IC 2163 that drives the pileup of molecular gas and turbulence, as predicted by encounter simulations?  
  > "The goal of the present paper is to use the ALMA data to look for the predicted gas flows into the eyelids that drive the pileup of gas there" (Introduction)
- Target **IC 2163 / NGC 2207**: coordinates phase center 06 16 22.809, -21 22 30.71 (J2000)  
  > "we adopt a distance of $35 \pm 2.5$ Mpc for IC 2163/NGC 2207 with a Hubble constant $H$ = 73 km s$^{-1}$ Mpc$^{-1}$ and corrected for infall towards Virgo." (Introduction); "The phase center was R.A., decl. (2000) = 06 16 22.809, -21 22 30.71." (2 Observations and data reduction); z/distance 35 ± 2.5 Mpc  
  > "we adopt a distance of $35 \pm 2.5$ Mpc for IC 2163/NGC 2207 with a Hubble constant $H$ = 73 km s$^{-1}$ Mpc$^{-1}$ and corrected for infall towards Virgo." (Introduction); "The phase center was R.A., decl. (2000) = 06 16 22.809, -21 22 30.71." (2 Observations and data reduction); distance from NED, H0 = 73 km/s/Mpc, Virgo infall corrected  
  > "we adopt a distance of $35 \pm 2.5$ Mpc for IC 2163/NGC 2207 with a Hubble constant $H$ = 73 km s$^{-1}$ Mpc$^{-1}$ and corrected for infall towards Virgo." (Introduction); "The phase center was R.A., decl. (2000) = 06 16 22.809, -21 22 30.71." (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2012.1.00357.S
- bands: 12CO J=1-0 (central frequency 114.1973 GHz in cube)  
  > "a central frequency of 114.1973 GHz and a total bandwidth of 0.3845 GHz" (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, 34-pointing mosaic, 32 antennae (two flagged)  
  > "in a mosaic of 34 pointings with the ALMA 12-m array of 32 antennae" (2 Observations and data reduction)
- configurations: C32-4, Cycle 1  
  > "The observations are from Configuration C32-4 of Cycle 1." (2 Observations and data reduction)
- baselines: uv-coverage 8.0 to 169 kλ  
  > "The uv-coverage ranged from 8.0 to 169 k$\lambda$." (2 Observations and data reduction)
- angular resolution: 2.00'' x 1.52'', PA -68.5 deg  
  > "$2.00'' \times 1.52''$, $-68.5\ensuremath{^\circ}$" (Table 1)
- max recoverable scale: 15'' = 2.6 kpc  
  > "The maximum recoverable scale with this ALMA configuration is $15''$ = 2.6 kpc" (2 Observations and data reduction)
- sensitivity: 3.7 mJy/beam per 10 km/s channel  
  > "rms noise per channel | 3.7 mJy beam$^{-1}$" (Table 1)
- time on source: 38 minutes  
  > "The on-source time was 38 minutes" (2 Observations and data reduction)
- observing dates: 2014 April 3  
  > "On 2014 April 3, IC 2163 and NGC 2207 were observed" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **VLA HI**: HI surface density and velocity field images (13.5'' x 12'') for comparison  
  > "The latter have a point spread function (PSF) with FWHM equal to $13.5'' \times 12''$, PA = $90\ensuremath{^\circ}$." (2 Observations and data reduction)
- Other facility **HST, Halpha, Spitzer IRAC/MIPS**: comparison images of eyelids and star-forming clumps  
  > "We also display the HST image from (cite: elmegreen00), the H$\alpha$ image from (cite: elmegreen01), the *Spitzer* 8 $\mu$m image from (cite: elmegreen06)" (2 Observations and data reduction)
- External data: X_CO = 1.8 ± 0.3 x 10^20 (H2 cm^-2)/(K km/s)  
  > "we take $X_{CO}$ = $1.8 \pm 0.3 \times 10^{20}$ (H$_2$ cm$^{-2}$)/(K km s$^{-1}$) from (cite: dame01)" (2 Observations and data reduction) [from (cite: dame01)]
- External data: IC 2163 projection parameters PA = 65 deg, inclination 40 deg  
  > "We adopted values of the projection parameters of IC 2163 from (cite: elmegreen95a; elmegreen95b)" (3.1) [from (cite: elmegreen95a; elmegreen95b)]
- External data: VLA HI cubes and velocity field  
  > "We compare our CO images of IC 2163 with the VLA H I observations by (cite: elmegreen95a)." (2 Observations and data reduction) [from (cite: elmegreen95a)]

## Processing

### Calibration

- pipeline or manual: Calibration and flagging by ALMA Data Reduction Team; one amplitude spike flagged additionally  
  > "Calibration and flagging were carried out by the ALMA Data Reduction Team." (2 Observations and data reduction)
- casa version: CASA 4.2.1  
  > "The CASA 4.2.1 software package was used for the data reduction." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Butler-JPL-Horizons 2012 model  
  > "Ganymede served as the flux calibrator with the Butler-JPL-Horizons 2012 frequency-dependent flux model" (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Using the CASA clean routine, a cleaned data cube of line emission from the galaxy pair was made" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural  
  > "Weighting | Natural" (Table 1)
- uv taper: _not stated_
- cell size: 0.5''  
  > "Pixel size | $0.5''$" (Table 1)
- image size: 551 x 301 pixels, 64 channels (subcube)  
  > "Cube Size | $551 \times 301$ pixels, 64 channels" (Table 1)
- masking: cube convolved to 6'', clipped at 2.5 rms, kept if in at least two adjacent channels; applied to original cube  
  > "we convolved the above cube to $6''$ resolution, clipped it at 2.5 times its rms noise, and retained regions of emission only if they appear in at least two adjacent channels." (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied after masking; factor 1.0-1.2 for most emission  
  > "the correction for primary beam attenuation is a factor of $1.0 -  1.2$ for almost all of the CO emission" (2 Observations and data reduction)
- array combination: no single-dish combination  
  > "our interferometric data could not be combined with single-dish observations." (2 Observations and data reduction)
- smoothing: _not stated_
- final beam: 2.00'' x 1.52''  
  > "$2.00'' \times 1.52''$" (Table 1)
- final rms: 3.7 mJy/beam per channel  
  > "rms noise per channel | 3.7 mJy beam$^{-1}$" (Table 1)

### Inherited from earlier work

- Projection parameters (PA 65 deg, i = 40 deg)  
  > "We adopted values of the projection parameters of IC 2163 from (cite: elmegreen95a; elmegreen95b)" (3.1) [from (cite: elmegreen95a; elmegreen95b)]
- X_CO conversion  
  > "we take $X_{CO}$ = $1.8 \pm 0.3 \times 10^{20}$ (H$_2$ cm$^{-2}$)/(K km s$^{-1}$) from (cite: dame01)" (2 Observations and data reduction) [from (cite: dame01)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters: niter, threshold, clean masks, and the interactive vs automatic choice
- Velocity grid and spectral line-free channels; continuum subtraction method not described
- Exact rest frequency used for velocity conversion
- AIPS tasks and parameters for moment maps and polar transformation
- Procedure to compute the beam-gradient velocity dispersion correction
- Whether the Hanning-smoothed channels were regridded to 10 km/s

## Analysis recipe

1. **Image and mask the CO cube**: CASA clean with natural weighting, then 6'' smoothed 2.5-sigma mask with two-channel continuity, primary-beam correction, subcube  
  > "The result was applied as a blanking mask to the original cube, and after correcting for primary-beam attentuation, we took a $551 \times 301$ pixel $\times 64$ channel subcube" (2 Observations and data reduction)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and convert to column density**: Moment maps from subcube; blank where I(CO) <= 200 Jy/beam m/s; N(H2) from X_CO  
  > "We also blanked the image of the intensity-weighted velocity field and the velocity dispersion image where the CO surface brightness $I{\rm (CO)} \leq 200$ Jybeam$^{-1}$ ms$^{-1}$" (2 Observations and data reduction)
   - software: AIPS
   - assumption: X_CO = 1.8e20 (H2 cm^-2)/(K km/s)  
  > "we take $X_{CO}$ = $1.8 \pm 0.3 \times 10^{20}$ (H$_2$ cm$^{-2}$)/(K km s$^{-1}$) from (cite: dame01)" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure velocity differences across eyelids in face-on polar coordinates**: Deproject with PA = 65 deg, i = 40 deg, nucleus center; measure Δv between outer and inner edges at fixed θ, averaged over 4 pixels (9.3 deg); dv/dR = Δv/(sin i)/ΔR  
  > "We then averaged our measurements over four pixels ($9.3\ensuremath{^\circ}$) in $\theta$ as that gives an arclength $R \Delta \theta$ approximately equal to the FWHM of the PSF" (3.1)
   - software: AIPS
   - parameter: eyelid edge at I(CO) = 200 Jy/beam m/s; minimum Δv uncertainty 7 km/s  
  > "Given the channel width, the minimum uncertainty in $\Delta v$ is 7 km s$^{-1}$." (3.1)
   - assumption: Δv_z negligible across the eyelid width (nearly in-plane perturbation)  
  > "we assume that across the eyelid width, $\Delta v_z$ for the molecular gas is negligible compared to $\Delta v_R$ or $\Delta v_t$" (3.1)
   - fitting: _not stated_
   - validation: Compared with HI velocity field PA and v_sys  
  > "This is consistent with the value PA = $65\ensuremath{^\circ} \pm 10\ensuremath{^\circ}$ that (cite: elmegreen95a) obtain for the kinematic major axis in H I." (3.2)
4. **Correlate N(H2) with |dv/dR|**: Linear regression of N(H2) on |dv/dR| for 25 azimuth points (and the northern eyelid alone)  
  > "A linear regression of $N({\rm H}_2)$ on $|dv/dR|$ for all 25 points in this figure gives" (4.1)
   - fitting: least-squares linear regression; priors not applicable  
  > "A linear regression of $N({\rm H}_2)$ on $|dv/dR|$ for all 25 points in this figure gives" (Correlation between |dv/dR| and the Molecular Column Densities, Observed Correlation)
   - validation: Correlation coefficients with degrees of freedom  
  > "The correlation coefficient is 0.84 with 23 degrees of freedom, and thus there is a strong correlation." (4.1)
5. **Measure CO velocity dispersion**: Second-moment dispersion, corrected for mean velocity gradient across the PSF; compared with single-Gaussian fits to unmasked line profiles  
  > "The ratio of the Gaussian $\sigma _v$ to the second moment $\sigma_v$ has a mean value of 0.98, with an rms scatter of $\pm 0.18$." (5 CO Velocity Dispersion)
   - software: AIPS
   - fitting: single Gaussian fits to line profiles  
  > "from fitting the line profile in the unmasked cube with a single Gaussian" (5 CO Velocity Dispersion)
   - validation: Compared with Mogotsi et al. 2016 normal-galaxy dispersions  
  > "their average for the CO mean velocity dispersions in 11 galaxies is $10.5 \pm 3.6$ km s$^{-1}$" (5 CO Velocity Dispersion)

## Software

- **CASA** 4.2.1: data reduction and cube imaging with clean  
  > "The CASA 4.2.1 software package was used for the data reduction." (2 Observations and data reduction)
- **AIPS** : data analysis: moment maps and masking  
  > "For the data analysis we used the AIPS software package." (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total integrated CO flux | 500 | ±5 | Jy km/s | 1 | Total integrated $S$(CO) / $500 \pm 5$ Jy km s$^{-1}$ |
| Regression N(H2) vs |dv/dR|, all 25 points: slope | 0.45 | ±0.06 | Msun pc^-2 per (km/s/kpc) | 4 | N({\rm H}_2) = 41 + (0.45 \pm 0.06) \vert\frac{dv}{dR} \vert |
| Correlation coefficient, all points | 0.84 | not stated | dimensionless | 4 | The correlation coefficient is 0.84 with 23 degrees of freedom |
| Northern eyelid regression slope | 0.52 | ±0.08 | Msun pc^-2 per (km/s/kpc) | 4 | N({\rm H}_2) = 28 + (0.52 \pm 0.08) \vert\frac{dv}{dR} \vert |
| Radial streaming at θ=270 on northern eyelid (in-plane) | 171 | ±40 | km/s | 3 | equivalent to $\Delta v/\sin i$ =$171 \pm 40$ km s$^{-1}$ in the plane of the disk |
| Corrected CO velocity dispersion, northern eyelid | 37 | ±20 (rms scatter) | km/s | 5 | (W3) northern eyelid / $42 \pm 21$ / $37 \pm 20$ |
| Corrected CO velocity dispersion, NGC 2207 arms west of bar | 10 | ±10 (rms scatter) | km/s | 5 | the mean $(\sigma_v)_{\rm corr}$ $\pm$ rms scatter is $10 \pm 10$ km s$^{-1}$ |

## Qualitative findings

- Gas in the eyelids shows large velocity gradients with sense consistent with inflow from the outer disk and a pileup.  
  > "The sense of the radial streaming in the eyelids is consistent with the idea that gas from the outer part of IC 2163 flows inward" (abstract)

## Claim tuples

- H: Gas streams inward and piles up in the eyelids of IC 2163 | E: Measure CO velocity differences between outer and inner eyelid edges in face-on polar coordinates | R: |Δv| exceeds 100 km/s at some azimuths; sign consistent with inward streaming | F: Observed velocity field is consistent with inflow and abrupt slowing producing the eyelid pileup | **supported**
- H: Column density correlates with velocity gradient across the eyelids | E: Linear regression of N(H2) on |dv/dR| | R: r = 0.84 (25 points), slope 0.45±0.06 | F: Strong correlation | **supported**
- H: Eyelids have elevated turbulence not caused by stellar feedback | E: Velocity dispersion maps compared with 24 μm and Halpha clumps | R: High corrected dispersion (~34-37 km/s) on much of the eyelids, not tied to bright clumps | F: Turbulence from the ocular shock front remains a viable explanation | **partially**

## Reasoning

- Why this data: HI resolution of 13.5''x12'' is too coarse for the ~6'' eyelid width; ALMA CO resolves outer and inner edges.  
  > "the spatial resolution afforded by the ALMA CO observations allows us to distinguish between the outer and the inner edges of each eyelid" (Introduction)
- Why this method: _not stated_
- Alternative: Inner eyelid edge moving outward was considered as an alternative; checked against v_sys. Northern consistent, southern inner edge appears to move outward.  
  > "an alternative interpretation would have the inner edge of the eyelids moving outwards with respect to the outer edge." (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings could underestimate CO flux; data could not be combined with single-dish.  
  > "The missing short-spacing data in our ALMA maps could lead to underestimates of the total CO flux of each galaxy." (2 Observations and data reduction)
- Limitation (authors): Cannot separate direct radial impact from shear-driven shocks.  
  > "we are unable to disentangle how much of the observed correlation in Figure [7](#fig7) is due to direct radial impact" (4.2)
- Caveat (inferred, ours): Constant X_CO assumed in a shocked, possibly turbulent region
- Caveat (inferred, ours): Regression is dominated by the northern eyelid; points at neighbouring azimuths are not independent given beam averaging
- Caveat (inferred, ours): No pre-eyelid density measured, so the shear-density relation is untested quantitatively
- Caveat (inferred, ours): Mixing radial and tangential streaming with a single inclination

## Reproducibility

- Data public (paper): ALMA project data cited via ADS/JAO.ALMA#2012.1.00357.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00357.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters (niter, threshold, masks)
- Missing: AIPS procedures for polar transformation and dispersion correction
- Missing: exact edge-definition pixel positions
- Data volume (inferred): ~10-50 GB raw; a single 34-pointing mosaic
- Score (inferred): 3/5, Public data, with a clear measurement recipe and table of results, but imaging parameters and AIPS steps are underspecified.
- Rediscovery candidate: yes, Public data and numeric tables (Table 2, regression) allow redoing the analysis, though some steps are loosely described.

## Links

- Method: (cite: elmegreen95a) (HI observations and kinematic projection parameters)
- Companion: (cite: elmegreen16) (Companion study of star formation in NGC 2207/IC 2163)
- Companion: (cite: struck05) (SPH model of the encounter)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 74,
  "stated": 53,
  "rate": 0.716
 },
 "evidence_ok": true
}
```
