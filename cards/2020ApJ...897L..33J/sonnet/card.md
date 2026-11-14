# The Ionized Warped Disk and Disk Wind of the Massive Protostar Monoceros R2-IRS2 Seen with ALMA

`2020ApJ...897L..33J` | The Astrophysical Journal Letters 2020 | first author: Jiménez-Serra, Izaskun | arXiv: 2006.15853 | DOI: 10.3847/2041-8213/aba050

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do massive protostellar disks show warps or internal holes, and how is the ionized disk and wind around MonR2-IRS2 structured, as probed by the H21alpha maser line?  
  > "it remains unknown the internal physical structure of these disks and, in particular, whether they present warps or internal holes as observed in low-mass proto-planetary disks." (abstract)
- Target **Monoceros R2 IRS2 (MonR2-IRS2)**: coordinates RA(J2000)=06h07m45.8034s, Dec(J2000)=-06d22m53.5155s  
  > "Monoceros R2 (hereafter MonR2) is a massive star-forming cluster located at a distance of 893$\,$pc (cite: dzib16)." (1 Introduction); "the peak coordinates of MonR2-IRS2 are $\alpha$(J2000)=06$^h$07$^m$45.8034$^s$ ($\pm$0.0008$^s$)" (3.1 0.4 mm continuum emission); z/distance 893 pc  
  > "Monoceros R2 (hereafter MonR2) is a massive star-forming cluster located at a distance of 893$\,$pc (cite: dzib16)." (1 Introduction); "the peak coordinates of MonR2-IRS2 are $\alpha$(J2000)=06$^h$07$^m$45.8034$^s$ ($\pm$0.0008$^s$)" (3.1 0.4 mm continuum emission); distance from Dzib et al. 2016  
  > "Monoceros R2 (hereafter MonR2) is a massive star-forming cluster located at a distance of 893$\,$pc (cite: dzib16)." (1 Introduction); "the peak coordinates of MonR2-IRS2 are $\alpha$(J2000)=06$^h$07$^m$45.8034$^s$ ($\pm$0.0008$^s$)" (3.1 0.4 mm continuum emission)

## Data provenance

- ALMA projects: 2012.1.00522.S
- bands: Band 9  
  > "observed on 25 September 2015 with ALMA in Band 9 (project 2012.1.00522.S) using the 12m array" (2 Observations)
- frequencies and spectral setup: H21alpha at 662.40416 GHz; bandwidth 1.875 GHz; resolution 976 kHz (0.44 km/s); dual polarization  
  > "using a spectral bandwidth of 1.875$\,$GHz and a spectral resolution of 976$\,$kHz (0.44$\,$km$\,$s$^{-1}$)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "using the 12m array (baselines from 43$\,$m to 2.27$\,$km)" (2 Observations)
- configurations: _not stated_
- baselines: 43 m to 2.27 km  
  > "using the 12m array (baselines from 43$\,$m to 2.27$\,$km)" (2 Observations)
- angular resolution: 80 mas x 60 mas (line); 60 mas x 50 mas (continuum)  
  > "The beam and rms noise level of the H21$\alpha$ image were 80$\,$mas$\times$60$\,$mas, P.A.=$-$88$^{\circ}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 30 mJy/beam per 1 km/s channel (line); 1.9 mJy/beam (continuum)  
  > "and 30$\,$mJy$\,$beam$^{-1}$ in 1$\,$km$\,$s$^{-1}$-channels, respectively." (2 Observations)
- time on source: _not stated_
- observing dates: 25 September 2015  
  > "observed on 25 September 2015 with ALMA in Band 9" (2 Observations)
- pi or archival as stated: _not stated_
- Line: H H21alpha RRL (662.40416 GHz)
- Other facility **SMA**: Earlier H30alpha and H26alpha RRL data and continuum spectral index, from the literature  
  > "High-angular resolution observations carried out with the Submillimeter Array (SMA) revealed that MonR2-IRS2 is a UC HII region" (1 Introduction)
- External data: SMA continuum spectral index alpha=-0.16+/-0.2 and H30alpha/H26alpha line data  
  > "spectral index of $\alpha$=$-$0.16$\pm$0.2 measured by the SMA (cite: jimenez-serra13)" (3.1 0.4 mm continuum emission) [from (cite: jimenez-serra13)]
- External data: Dust temperature 500-1200 K  
  > "by assuming dust temperatures T$_{dust}$=500-1200$\,$K (cite: howard94)" (3.1 0.4 mm continuum emission) [from (cite: howard94)]
- External data: Dust opacity 25.8 cm2/g  
  > "a dust opacity $\kappa_{dust}$=25.8$\,$cm$^2$$\,$g$^{-1}$ (cite: ossenkopf94)" (3.1 0.4 mm continuum emission) [from (cite: ossenkopf94)]
- External data: Hydrogen departure coefficients b_n and beta_n  
  > "the departure coefficients of hydrogen, $b_n$ and $\beta_n$, calculated by (cite: walmsley90)" (4 Modelling of the H21alpha RRL) [from (cite: walmsley90)]

## Processing

### Calibration

- pipeline or manual: Original pipeline reduction scripts, plus self-calibration  
  > "The calibrated dataset was obtained by running the original pipeline reduction scripts, and the data were additionally self-calibrated" (2 Observations)
- casa version: CASA 5.0.0  
  > "using the CASA (the Common Astronomy Software Applications) package version 5.0.0" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 (bandpass J0522-3627; phase J0607-0834)  
  > "J0522-3627 was used for bandpass calibration, J0423-013 for flux calibration, and J0607-0834 for phase and amplitude calibration." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Applied in CASA; details not given  
  > "the data were additionally self-calibrated using the CASA" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub across 5.61 GHz of line-free bandwidth  
  > "the 0.4$\,$mm continuum map was generated by using the CASA task *uvcontsub* across 5.61$\,$GHz of line-free bandwidth" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Velocity resolution smoothed to 1 km/s  
  > "after smoothing the velocity resolution to 1$\,$km$\,$s$^{-1}$" (2 Observations)
- final beam: Line 80x60 mas PA -88 deg; continuum 60x50 mas PA 78 deg  
  > "The angular resolution of the 0.4$\,$mm continuum image was 60$\,$mas$\times$50$\,$mas, P.A.=78$^{\circ}$" (2 Observations)
- final rms: 1.9 mJy/beam continuum; 30 mJy/beam per 1 km/s channel line  
  > "the rms noise level was 1.9$\,$mJy$\,$beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Non-LTE radiative transfer modelling approach with Keplerian disk plus wind  
  > "We have thus adopted a similar physical structure to model the H21$\alpha$ centroid map derived for MonR2-IRS2." (4 Modelling of the H21alpha RRL) [from (cite: martin-pintado11; baez13; zhang17); MWC922 (cite: sanchez-contreras19)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting/robust, cell size, image size, deconvolver, masking, niter, threshold)
- self-calibration solution intervals and number of rounds
- which channels were line-free for continuum
- how the flux scale uncertainty was set
- MORELI code availability and fitting procedure (grid, goodness of fit, uncertainties on model parameters)
- Method for deriving the free-free contribution of 130 mJy
- Details of centroid fitting (fit region, channel selection)

## Analysis recipe

1. **Image continuum and line cube**: Pipeline calibration, self-calibration, uvcontsub continuum; continuum-subtracted cube smoothed to 1 km/s  
  > "The H21$\alpha$ image was obtained from the continuum-subtracted datacube after smoothing the velocity resolution to 1$\,$km$\,$s$^{-1}$." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum position/flux and neutral disk mass**: 2D Gaussian fit to continuum; dust flux of 215 mJy after subtracting free-free; mass from dust emission  
  > "By fitting a 2D gaussian to the continuum emission, the peak coordinates of MonR2-IRS2 are" (3.1 0.4 mm continuum emission)
   - assumption: Tdust=500-1200 K, gas-to-dust ratio 100, kappa=25.8 cm2/g  
  > "a gas-to-dust mass ratio R=100, and a dust opacity $\kappa_{dust}$=25.8$\,$cm$^2$$\,$g$^{-1}$ (cite: ossenkopf94)" (3.1 0.4 mm continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare line-to-continuum ratio with LTE**: Measured LTCR compared with LTE prediction scaling as nu^1.1  
  > "The LTCR is predicted to be $\sim$206$\,$km$\,$s$^{-1}$ for the H21$\alpha$ line." (3.2 H21alpha maser emission)
   - fitting: _not stated_
   - validation: Confirmed by radiative transfer models  
  > "This, together with our RRL radiative transfer calculations of Section$\,$[4](#model), confirm that the RRLs at $\lambda$$\leq$0.85$\,$mm toward MonR2-IRS2 are masers." (3.2 H21alpha maser emission)
4. **Build centroid map**: 2D Gaussian fits to H21alpha emission in 5 km/s channels  
  > "we have constructed the centroid map of the H21$\alpha$ emission in 5$\,$km$\,$s$^{-1}$ channels by using 2D Gaussians" (3.3 H21alpha centroid map)
   - fitting: 2D Gaussian  
  > "we have constructed the centroid map of the H21$\alpha$ emission in 5$\,$km$\,$s$^{-1}$ channels by using 2D Gaussians" (H21$\alpha$ centroid map)
   - validation: Bandpass phase noise <=1 deg implies negligible effect on centroid errors  
  > "the phase noise in the ALMA bandpass data was $\leq$1$^\circ$, which implies a negligible effect in the positional errors of the H21$\alpha$ centroids." (3.3 H21alpha centroid map)
5. **Model spectrum and centroids with disk plus wind**: Non-LTE 3D radiative transfer of Keplerian ionized disk and expanding wind in a double cone; best-fit parameters in Table  
  > "We have used the non-LTE 3D radiative transfer code MORELI (cite: baez13)" (4 Modelling of the H21alpha RRL)
   - software: MORELI
   - parameter: M*=15 Msun, rmin=13 au, Te=5850 K, inclination -25 deg, v0=10 km/s  
  > "Electron temperature, $T_\mathrm{e}$ | 5850$\,$$\mathrm{K}$" (Table 1)
   - assumption: Ne follows r^-2 law  
  > "follows a $r^{-2}$ law with an inner radius of 13$\,$au" (4 Modelling of the H21alpha RRL)
   - fitting: _not stated_
   - validation: Model compared with line profile and centroids; no-wind model fails to reproduce high-velocity deviations; LTE vs non-LTE comparison  
  > "Indeed, the same model but without a wind, does not reproduce such deviations (black line in Figure$\,$[3](#centroid_map_figure))." (4 Modelling of the H21alpha RRL)

## Software

- **CASA** 5.0.0: Self-calibration, uvcontsub, imaging  
  > "using the CASA (the Common Astronomy Software Applications) package version 5.0.0" (2 Observations)
- **MORELI** : Non-LTE 3D radiative transfer modelling  
  > "We have used the non-LTE 3D radiative transfer code MORELI (cite: baez13)" (4 Modelling of the H21alpha RRL)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated continuum flux at 0.4 mm | 345 | 10 | mJy | 2 | The integrated continuum flux at 0.4$\,$mm is (345$\pm$10)$\,$mJy. |
| Free-free contribution at 0.4 mm | 130 | 30 | mJy | 2 | The free-free contribution is 130$\pm$30$\,$mJy |
| Neutral disk mass | 2-4e-4 | 15% | Msun | 2 | The neutral disk mass is $\sim$2-4$\times$10$^{-4}$$\,$M$_\odot$ with a 15% uncertainty. |
| Deconvolved continuum size | 62 x 43 mas (55 x 38 au) | not stated | mas | 2 | deconvolved size 62$\,$mas$\times$43$\,$mas, or 55$\,$au$\times$38$\,$au |
| Measured H21alpha LTCR | ~1130 | not stated | km/s | 3 | is $\sim$1130$\,$km$\,$s$^{-1}$, which clearly exceeds the LTCR predicted under LTE |
| Central mass | 15 | not stated | Msun | 5 | constrains the central mass of the MonR2-IRS2 source to 15$\,$M$_\odot$ |
| Mass loss rate | 2.8e-7 | not stated | Msun/yr | 5 | The predicted mass loss rate for MonR2-IRS2 is 2.8$\times$10$^{-7}$$\,$M$_\odot$$\,$yr$^{-1}$ |
| Ionized disk mass | 2.4e-5 | not stated | Msun | 5 | the mass of the ionized disk is 2.4$\times$10$^{-5}$$\,$M$_\odot$ |
| Electron temperature | 5850 | not stated | K | 5 | The electron temperature, T$_e$, that best fits our ALMA data is 5850$\,$K. |
| Centroid positional errors | 1-2 | not stated | mas | 4 | The typical errors in the centroid positions (error bars in Figure$\,$[3](#centroid_map_figure)) are 1-2$\,$mas (0.9-1.8$\,$au) |

## Qualitative findings

- Ionized gas is a Keplerian disk plus expanding wind; centroids deviate from disk plane suggesting warp, possibly from a companion  
  > "The H21$\alpha$ emission centroids at velocities between $-$10 and 20$\,$km$\,$s$^{-1}$ deviate from the disk plane, suggesting a warping for the disk." (abstract)

## Claim tuples

- H: H21alpha emission toward MonR2-IRS2 is maser-amplified | E: Compare measured LTCR with LTE prediction and non-LTE models | R: Measured LTCR ~1130 km/s vs ~206 km/s predicted under LTE | F: RRLs at <=0.85 mm are masers | **supported**
- H: Ionized gas is in a Keplerian disk plus wind | E: 3D non-LTE modelling of spectrum and centroids | R: Model with 15 Msun, wind of 10 km/s fits the profile and centroids | F: Keplerian ionized disk and expanding wind | **supported**
- H: The disk is warped | E: Compare centroids with the model at low velocities | R: Deviations at 2, 12 and 17 km/s larger than errors | F: Suggests warping, possibly caused by a secondary object; alternatives exist | **partially**
- H: Wind is launched from the disk at ~10 au | E: Compare model with and without wind to high-velocity centroids | R: Wind needed; launching radius ~11 au | F: Consistent with magnetically-regulated disk wind, not X-wind or photoevaporation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Wind velocities >=20 km/s ruled out; photoevaporation rejected since gravitational radius ~100 au; second outer warp disfavoured since twist >90 deg exceeds 60 deg  
  > "Expansion velocities $\geq$20$\,$km$\,$s$^{-1}$ are ruled out because the predicted H21$\alpha$ linewidths in the wings would be too large." (4 Modelling of the H21alpha RRL)
- How they decided it was enough: _not stated_
- Limitation (authors): Some centroid positional errors are large at high velocities; RRL masers are variable  
  > "although some of the associated positional errors are large" (3.3 H21alpha centroid map)
- Caveat (inferred, ours): Model fit is by eye with no uncertainties or degeneracy exploration
- Caveat (inferred, ours): Warp inferred from few centroid deviations
- Caveat (inferred, ours): Single epoch of a variable maser
- Caveat (inferred, ours): Free-free subtraction at 0.4 mm drives neutral disk mass

## Reproducibility

- Data public (paper): Project 2012.1.00522.S used and acknowledged  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA 2012.1.00522.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean imaging parameters
- Missing: self-calibration details
- Missing: MORELI fitting procedure and code access
- Missing: centroid fitting details
- Data volume (inferred): ~50-200 GB raw (Band 9, single 12m execution)
- Score (inferred): 4/5, Public data and a clear parameter table, but imaging, self-calibration and model fitting details are missing.
- Rediscovery candidate: no, Modelling relies on MORELI and unstated fitting procedure; imaging details are incomplete.

## Links

- Method: (cite: baez13) (MORELI radiative transfer code)
- Method: (cite: walmsley90) (Departure coefficients)
- Companion: (cite: jimenez-serra13) (Earlier SMA RRL observations of MonR2-IRS2)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 43,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
