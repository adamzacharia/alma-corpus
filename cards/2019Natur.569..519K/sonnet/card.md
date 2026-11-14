# Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback

`2019Natur.569..519K` | Nature 2019 | first author: Kruijssen, J. M. Diederik | arXiv: 1905.08801 | DOI: 10.1038/s41586-019-1194-3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Why does the gas depletion time exceed the GMC dynamical time by two orders of magnitude: slow, efficient star formation over many dynamical times, or fast, inefficient star formation with rapid GMC dispersal?  
  > "Either most of a GMC’s mass is converted into stars over many dynamical times(cite: koda09), or only a small fraction turns into stars before the GMC is dispersed on a dynamical timescale" (abstract)
- Target **NGC300**: coordinates 00h54m53.48s -37d41m03.8s (optical disc centre, NED)  
  > "The distance of NGC300 is taken to be $D = 2.0$ Mpc, derived from Hubble Space Telescope observations of the tip of the red giant branch(cite: dalcanton09)." (Methods); "The center of the optical disc is at right ascension $\alpha = \textrm{00h54m53.48s}$ and declination $\delta = \textrm{-37d41m03.8s}$ (NED)." (Methods); z/distance D = 2.0 Mpc  
  > "The distance of NGC300 is taken to be $D = 2.0$ Mpc, derived from Hubble Space Telescope observations of the tip of the red giant branch(cite: dalcanton09)." (Methods); "The center of the optical disc is at right ascension $\alpha = \textrm{00h54m53.48s}$ and declination $\delta = \textrm{-37d41m03.8s}$ (NED)." (Methods); distance from HST tip of the red giant branch (Dalcanton et al. 2009)  
  > "The distance of NGC300 is taken to be $D = 2.0$ Mpc, derived from Hubble Space Telescope observations of the tip of the red giant branch(cite: dalcanton09)." (Methods); "The center of the optical disc is at right ascension $\alpha = \textrm{00h54m53.48s}$ and declination $\delta = \textrm{-37d41m03.8s}$ (NED)." (Methods)

## Data provenance

- ALMA projects: 2013.1.00351.S, 2015.1.00258.S
- bands: CO(1-0) (Band 3 implied, not named)  
  > "The ALMA receivers were tuned to the ground-state rotational transition of carbon monoxide, CO(1-0)." (Methods)
- frequencies and spectral setup: 122 kHz per channel (0.32 km/s), 468.750 MHz bandwidth per baseband  
  > "The observations were performed with a spectral resolution of $122$ kHz per channel (0.32 km s$^{-1}$) and a total bandwidth of 468.750 MHz per baseband." (Methods)
- continuum bandwidth: _not stated_
- arrays: 12-m main array, 7-m and 12-m ACA, plus total power  
  > "Observations were carried out for $10$ hours with the 12-m main array and for $92$ hours with the 7-m and 12-m antennas of the ALMA Compact Array (ACA)" (Methods)
- configurations: C34-2 and C36-2 (12-m)  
  > "The 12-m array was used in configurations C34-2 and C36-2 that provide maximum (unprojected) baselines of $0.330$ km." (Methods)
- baselines: _not stated_
- angular resolution: 2.5'' x 1.8'' ≈ 20 pc  
  > "The resulting beam size is $2.5'' \times 1.8'' \approx 20$ pc" (Methods)
- max recoverable scale: all spatial scales (ACA + total power combined)  
  > "We combine the interferometric and total power data cubes in Fourier space making our observations sensitive to all spatial scales." (Methods)
- sensitivity: 6.7 mJy/beam per 2 km/s channel  
  > "the r.m.s. noise level is $6.7$ mJy per beam and per 2 km s$^{-1}$ channel" (Methods)
- time on source: 10 h (12-m), 92 h (ACA)  
  > "Observations were carried out for $10$ hours with the 12-m main array and for $92$ hours with the 7-m and 12-m antennas of the ALMA Compact Array (ACA)" (Methods)
- observing dates: June 6, 2014 to November 19, 2016 (Cycles 2 and 3)  
  > "between June 6, 2014 and November 19, 2016" (Methods)
- pi or archival as stated: PI A. Schruba, public in ALMA archive  
  > "(PI A. Schruba) and are publicly available through the ALMA archive" (Data Availability)
- Line: 12CO J=1-0 (not stated)
- Other facility **MPG/ESO 2.2-m WFI**: Halpha narrowband map tracing star formation  
  > "These consist of narrowband observations of the H$\alpha$ line (with a total exposure time of $50$ min) and the nearby continuum." (Methods)
- Other facility **VLT/MUSE**: Used to correct Halpha for contaminating lines and verify extinction  
  > "We verified the extinction correction with our MUSE data" (Methods)
- Other facility **Spitzer MIPS 24 um**: Search for embedded star formation  
  > "we compare the H$\alpha$ map to the *Spitzer* MIPS $24~\mu$m map to identify any embedded star formation missed by the H$\alpha$ map" (Methods)
- Other facility **ATCA HI**: HI surface densities, rotation curve, inclination, PA  
  > "derived from a 21 cm atomic hydrogen (Hi) emission map obtained with the Australia Telescope Compact Array (ATCA) telescope(cite: westmeier11)" (Methods)
- External data: Reduced MPG/ESO 2.2-m Halpha map of NGC300  
  > "here we use reduced data kindly provided by C. Faesi." (Methods) [from Faesi et al. 2014 (cite: faesi14)]
- External data: Metallicity centre and gradient  
  > "We adopt a metallicity of $[{\rm M}/{\rm H}] = -0.23 \pm 0.06$ dex at the centre of NGC300 and a metallicity gradient of $-0.058 \pm 0.014$ dex kpc$^{-1}$" (Methods) [from (cite: gogarten10)]
- External data: Halpha reference timescale relation t_Ha,ref = 4.32 Myr (Z/Zsun)^-0.086  
  > "t_{\rm H\alpha,ref}=(4.32\pm0.16~{\rm Myr})\times(Z/{\rm Z}_\odot)^{-0.086\pm0.017}" (Methods) [from Haydon et al. 2018 (cite: haydon18)]
- External data: Inclination 42 deg, PA 111 deg, rotation curve from HI  
  > "NGC300’s disc has an inclination of $i = 42 \pm 0.5$ degrees and a position angle of $P.A. = 111 \pm 0.5$ degrees" (Methods) [from Westmeier et al. 2011 (cite: westmeier11)]

## Processing

### Calibration

- pipeline or manual: pipeline-delivered calibrated data sets  
  > "We adopt the pipeline-delivered calibrated data sets." (Methods)
- casa version: calibration 4.2.2 (Cycle 2), 4.6.0 (Cycle 3); mapping/deconvolution 4.7.2  
  > "calibration is performed in version 4.2.2 (Cycle 2) and 4.6.0 (Cycle 3); mapping and deconvolution in version 4.7.2." (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars, Venus, Uranus, or Neptune  
  > "The absolute flux scale was set with observations of Mars, Venus, Uranus, or Neptune." (Methods)
- flux scale uncertainty: 5%  
  > "We adopt ALMA’s fiducial absolute flux calibration uncertainty of $5\%$." (Methods)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multi-scale clean at 1, 2, 5, 10 times the 12-m beam, threshold 3 rms  
  > "as well as a multi-scale clean at 1, 2, 5, 10 times the 12-m beam with a threshold at 3 times the root mean square (r.m.s.) noise level" (Methods)
- weighting robust: Briggs, r = 0.5  
  > "deconvolve them according to a “Briggs” scheme with robustness parameter $r = 0.5$" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m + 7-m with empirical noise-based weighting; total power combined in Fourier space  
  > "We combine the 12-m and 7-m array data using an empirical noise-based weighting" (Methods); "We combine the interferometric and total power data cubes in Fourier space" (Methods)
- smoothing: _not stated_
- final beam: 2.5'' x 1.8''  
  > "The resulting beam size is $2.5'' \times 1.8'' \approx 20$ pc" (Methods)
- final rms: 6.7 mJy/beam per 2 km/s channel  
  > "the r.m.s. noise level is $6.7$ mJy per beam and per 2 km s$^{-1}$ channel" (Methods)

### Inherited from earlier work

- Full ALMA data presentation  
  > "The full presentation of the data is the subject of another paper (A.S. *et al.*, manuscript in preparation)." (Methods) [from A.S. et al., in preparation]
- Statistical method and default Heisenberg code input parameters  
  > "performed using the default input parameters listed in Tables 1 and 2 of Ref. (cite: kruijssen18)" (Methods) [from (cite: kruijssen18)]
- Halpha data reduction  
  > "In summary, their data reduction(cite: faesi14) includes instrumental calibration, a combination of exposures, continuum subtraction, and Galactic extinction correction" (Methods) [from (cite: faesi14)]
- Diffuse emission filtering  
  > "we remove diffuse emission from the input maps on size scales $>10\lambda$ by using a high-pass Gaussian filter in Fourier space(cite: hygate18)" (Methods) [from (cite: hygate18)]

### Not stated but needed to reproduce (our reading)

- Which ALMA execution blocks/MOUS were used and the pipeline version used
- CASA clean parameters: cell size, image size, masking, niter
- Details of the modified total power pipeline and how feathering was done
- Image-cube moment/masking used to make the CO map fed to Heisenberg
- Heisenberg code is not public (available on request)
- Exact reference parameters in Kruijssen 2018 Tables 1-2 not reproduced
- Smoothing/regridding to match Halpha PSF and astrometric alignment details

## Analysis recipe

1. **Image CO(1-0) and Halpha maps**: Combine 12-m, 7-m and total power CO data; reduce Halpha WFI data; correct Halpha for [NII] contamination and extinction  
  > "We remove the contribution of from our H$\alpha$ map scaling it by $5/6$." (Methods)
   - software: CASA
   - parameter: A_Halpha = 0.5 mag extinction correction  
  > "We further correct for internal extinction of H$\alpha$ by $A_{\rm H\alpha}=0.5$ mag" (Methods)
   - assumption: alpha_CO = 4.35 (Z/Zsun)^-1 Msun/(K km/s pc^2), 50% uncertainty  
  > "Throughout the analysis, we adopt an uncertainty on $\alpha_{\rm CO}$ of 50%." (Methods)
   - fitting: _not stated_
   - validation: Extinction checked with MUSE Balmer decrement; 24 um compared to check embedded SF  
  > "resulting in $A_{\rm H\alpha}=0.37\pm0.24$ mag (median $\pm$ standard deviation)" (Methods)
2. **Identify emission peaks and measure CO-to-Halpha ratio vs aperture size**: Clumpfind peaks in each map; top-hat apertures; relative CO/Halpha ratio bias vs aperture size with Monte Carlo sampling to avoid overlap  
  > "overlapping apertures are avoided through Monte-Carlo sampling from the emission peak sample and taking the average over $10^3$ such samples" (Methods)
   - software: Clumpfind, Heisenberg
   - parameter: apertures 20 to 2560 pc in steps of sqrt(2); flux range 2.0 dex below brightest peak, contour interval 0.5 dex  
  > "The aperture sizes range from a spatial resolution $l_{\rm ap}=20$ to $2560~{\rm pc}$ in steps of a factor of $\sqrt{2}$." (Methods)
   - fitting: _not stated_
   - validation: Clumpfind levels varied (1-2 dex range, 0.25-1 dex interval); results consistent within uncertainties or ~30%  
  > "these experiments give results that are consistent with the numbers in Table [\[tab:fit\]] to within the uncertainties, or ${\sim}30\%$, whichever is largest" (Methods)
3. **Fit evolutionary timeline model**: Fit analytical model for CO and Halpha-centred bias curves to get t_CO, t_fb, lambda, using Halpha reference timescale  
  > "The free parameters of these expressions are $t_{\rm CO}$, $t_{\rm fb}$, and $\lambda$." (Methods)
   - software: Heisenberg
   - parameter: t_Ha,ref = 4.53-4.69 Myr over R=0-3 kpc; radial bins of 1 and 1.5 kpc width  
  > "which for the observed metallicity gradient(cite: gogarten10) in NGC300 results in values between $t_{\rm H\alpha,ref}=4.53\pm0.14$ and $4.69\pm0.13~{\rm Myr}$" (Methods)
   - fitting: reduced chi^2 fit returning 3D PDF; 16th/84th percentile uncertainties  
  > "The best-fitting model is obtained by carrying out a reduced-$\chi^2$ fit to the observations, which returns a three-dimensional probability distribution function (PDF) of the free parameters." (Methods)
   - validation: Set of reliability criteria checked (peak numbers, resolution, filling factors, nearest-neighbour test)  
  > "This has resulted in a set of quantitative requirements for reliable applications, all of which are satisfied by the observations of NGC300 used in this work." (Methods)
4. **Diffuse emission filtering**: High-pass Gaussian filter in Fourier space on scales >10 lambda, noise mask at 2 rms, iterate  
  > "After removing the diffuse emission, we also apply a noise mask with a threshold at twice the r.m.s. noise level." (Methods)
   - software: Heisenberg
   - assumption: Diffuse Halpha originated from HII regions  
  > "This assumes that the diffuse H$\alpha$ originally emerged from Hii regions" (Methods)
   - fitting: _not stated_
   - validation: Effect on results 7-37%  
  > "its quantitative effect on the inferred quantities ranges from $7{-}37\%$" (Methods)
5. **Derive SFE, mass loading and feedback velocity**: eps_sf = t_CO/t_dep; eta_fb=(1-eps_sf)/eps_sf; v_fb = r_CO/t_fb with Monte Carlo error propagation  
  > "the feedback outflow velocity $$\begin{equation}
\label{eq:vfb}
v_{\rm fb}=\frac{r_{\rm CO}}{t_{\rm fb}}.
\end{equation}$$" (Methods)
   - assumption: H-alpha SFR calibration of Murphy et al. 2011, Kroupa IMF, 20% uncertainty  
  > "We adopt an uncertainty on the H$\alpha$-to-SFR conversion factor of 20%." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with theoretical feedback timescales and cloud properties**: Cprops cloud identification; compare to free-fall, crossing, SN, photoionisation, wind, radiation pressure timescales and Toomre length / scale height  
  > "Molecular clouds are identified and their macroscopic properties determined from the ALMA+ACA data using an updated version of the Cprops code" (Methods)
   - software: Cprops
   - assumption: gas velocity dispersion 6 km/s from M33 HI  
  > "The gas velocity dispersion is assumed to be $6~{\rm km}~{\rm s}^{-1}$" (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2, 4.6.0, 4.7.2: calibration, mapping and deconvolution  
  > "We process the data using the ALMA reduction software CASA" (Methods)
- **Cprops** : cloud identification and properties  
  > "using an updated version of the Cprops code" (Methods)
- **Clumpfind** : emission peak identification  
  > "we apply Clumpfind(cite: williams94) to identify emission peaks" (Methods)
- **Heisenberg** : automated timeline analysis  
  > "The above analysis is automated in the Heisenberg code" (Methods)
- **ESOREX/MUSE pipeline** : MUSE data reduction  
  > "The data were reduced using the MUSE pipeline under the ESOREX environment" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GMC lifetime t_CO (galactic average) | 10.8 | +2.1/-1.7 | Myr | 3 | $0.0$–$3.0$ / $10.8^{+2.1}_{-1.7}$ |
| Feedback timescale t_fb | 1.5 | +0.2/-0.2 | Myr | 3 | $1.5^{+0.2}_{-0.2}$ |
| Region separation length lambda | 104 | +22/-18 | pc | 3 | $104^{+22}_{-18}$ |
| Integrated SFE | 2.5 | +1.9/-1.1 | % | 5 | $2.5^{+1.9}_{-1.1}$ |
| Mass loading factor eta_fb | 40 | +31/-18 | dimensionless | 5 | $40^{+31}_{-18}$ |
| Feedback velocity v_fb | 9.4 | +0.8/-0.7 | km/s | 5 | $9.4^{+0.8}_{-0.7}$ |
| Total SFR from Halpha | 0.092 | not stated | Msun/yr | 1 | we measure a total SFR of $0.092~{\rm M}_\odot~{\rm yr}^{-1}$ in NGC300 |
| CO 5-sigma point-source sensitivity | 5600 | not stated | Msun | 1 | point source sensitivity of $5600~{\rm M}_\odot$ when integrated over $10~{\rm km~s}^{-1}$ |

## Qualitative findings

- CO and Halpha are spatially de-correlated below ~150 pc, implying fast evolutionary cycling  
  > "We find a symmetric de-correlation between CO(1-0) and H$\alpha$ emission on small (${<}150~\mbox{${\rm pc}$}$) scales" (Main text)
- GMCs are dispersed by photoionisation and stellar winds before supernovae  
  > "shows that GMCs in NGC300 are primarily dispersed by photoionisation and stellar winds" (Main text)

## Claim tuples

- H: Star formation within GMCs is fast and inefficient rather than slow and efficient | E: Measure CO-to-Halpha flux ratio vs aperture size and fit timeline model | R: t_CO=10.8 Myr, eps_sf=2.5%, t_fb=1.5 Myr | F: GMCs live about one dynamical time, with low integrated SFE | **supported**
- H: Which feedback mechanism disperses GMCs | E: Compare t_fb and v_fb to predicted timescales | R: t_fb < 3 Myr SN delay; matches photoionisation and winds | F: Early feedback, not supernovae, disperses GMCs | **supported**
- H: Region separation scales with gas disc scale height | E: Compare lambda to scale height and Toomre length | R: lambda=100-150 pc matches scale height | F: ISM structured by feedback-driven bubbles | **supported**

## Reasoning

- Why this data: NGC300 is the closest, face-on southern star-forming disc galaxy; method needs high sensitivity and resolution over a large field  
  > "NGC300 is the perfect target for the first application of this method, as it is the closest ($D=2$ Mpc), face-on, star-forming disc galaxy accessible from the southern hemisphere." (Main text)
- Why this method: _not stated_
- Alternative: Long GMC lifetime of 50 Myr (two model variants) rejected as incompatible with observed ratios  
  > "These alternative models represent two extremes and show that long GMC lifetimes are fundamentally incompatible with the observed CO-to-H$\alpha$ ratios in NGC300." (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Extinction correction might underestimate attenuation toward GMC density peaks  
  > "It might underestimate the attenuation towards the GMC density peaks, where the surface density is $>20~{\rm M}_\odot~{\rm pc}^{-2}$." (Methods)
- Limitation (authors): eps_sf and eta_fb depend on CO-to-H2 and Halpha-to-SFR conversion factors  
  > "Due to their dependence on $t_{\rm dep}$, the quantities $\epsilon_{\rm sf}$ and $\eta_{\rm fb}$ are sensitive to absolute scaling factors" (Methods)
- Caveat (inferred, ours): Single galaxy; generality of timeline unproven
- Caveat (inferred, ours): Result relies on calibrated Halpha reference timescale from simulations
- Caveat (inferred, ours): Halpha astrometric alignment to CO uncertain (no common point sources)
- Caveat (inferred, ours): Code unavailable publicly

## Reproducibility

- Data public (paper): ALMA CO data public in ALMA archive; Halpha raw data public at ESO  
  > "are publicly available through the ALMA archive" (Data Availability)
- Products in archive: _not stated_
- Code: Available from corresponding author on reasonable request; dedicated publication in preparation  
  > "The code is available from the corresponding author (J.M.D.K.) upon reasonable request." (Code Availability)
- Missing: Heisenberg code not public
- Missing: Reduced Halpha map from C. Faesi (raw data only public)
- Missing: Cell size, image size and masking for CO imaging
- Missing: Total power pipeline modifications
- Data volume (inferred): Large: ~100 h of 12-m + ACA + TP mosaics; roughly several hundred GB raw, plus ESO WFI and MUSE data
- Score (inferred): 3/5, Data are public and the method is documented, but the key analysis code is unreleased and the Halpha map and several imaging parameters are not provided.
- Rediscovery candidate: no, Key analysis code (Heisenberg) is only available on request and the processed Halpha map is not public.

## Links

- Method: Kruijssen et al. 2018 (cite: kruijssen18) (Statistical method and Heisenberg code description)
- Method: Haydon et al. 2018 (cite: haydon18) (Halpha reference timescale calibration)
- Method: Hygate et al. 2018 (cite: hygate18) (Diffuse emission filtering and astrometric tolerance)
- Companion: A.S. et al., in preparation (Full presentation of the ALMA NGC300 data)
- Related: xCOLDGASS
- Related: xGASS

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 66,
  "rate": 0.725
 },
 "evidence_ok": true
}
```
