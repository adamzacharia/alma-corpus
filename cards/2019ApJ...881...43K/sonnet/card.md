# The Molecular Outflow in NGC 253 at a Resolution of Two Parsecs

`2019ApJ...881...43K` | The Astrophysical Journal 2019 | first author: Krieger, Nico | arXiv: 1907.00731 | DOI: 10.3847/1538-4357/ab2d9c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How much molecular gas is in a non-disk (outflow) component in the center of NGC 253, and what are the molecular mass outflow rate, kinetic energy and momentum?  
  > "By decomposing the detected emission, we aim to measure the total molecular gas outflow rate in NGC 253 and improve upon previous less systematic results." (Introduction)
- Target **NGC 253**: coordinates 00h47m33.134s, -25d17m19.68s (kinematic center)  
  > "NGC 253 is one of the nearest starburst systems at a distance of 3.5 Mpc (cite: Rekola:2005ha)." (Introduction); "the kinematic center at $\alpha, \delta = 00^h47^m33.134^s, -25^\circ17^m19.68^s$ as identified in (cite: MullerSanchez:2010dr)" (Introduction); z/distance 3.5 Mpc (1" = 17 pc)  
  > "NGC 253 is one of the nearest starburst systems at a distance of 3.5 Mpc (cite: Rekola:2005ha)." (Introduction); "the kinematic center at $\alpha, \delta = 00^h47^m33.134^s, -25^\circ17^m19.68^s$ as identified in (cite: MullerSanchez:2010dr)" (Introduction); distance from Rekola et al. 2005  
  > "NGC 253 is one of the nearest starburst systems at a distance of 3.5 Mpc (cite: Rekola:2005ha)." (Introduction); "the kinematic center at $\alpha, \delta = 00^h47^m33.134^s, -25^\circ17^m19.68^s$ as identified in (cite: MullerSanchez:2010dr)" (Introduction)

## Data provenance

- ALMA projects: 2011.1.00172.S, 2012.1.00108.S, 2015.1.00274.S
- bands: Bands 3, 6, 7 (CO(1-0), CO(2-1), CO(3-2))  
  > "observations in ALMA cycles 2, 3 and 4 in bands 3, 6 and 7 that cover the redshifted emission in NGC 253 of CO(1–0), CO(2–1) and CO(3–2)" (2.1 Data reduction)
- frequencies and spectral setup: Band 7: LSB 342.0-345.8 GHz, USB 353.9-357.7 GHz, 976.6 kHz channels (0.8 km/s)  
  > "we tuned the lower side band to $342.0-345.8$ GHz and the upper side band to $353.9-357.7$ GHz (total bandwidth 7.6 GHz) with 976.6 kHz channel width" (2.1 Data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m compact and extended, 7 m ACA, and Total Power; four-pointing 12 m mosaic, five-pointing ACA mosaic  
  > "in a linear four pointing mosaic with two configurations of the 12 m array (12 m compact and 12 m extended, half power beam width $\sim 17\ensuremath{''}$) and a five pointing mosaic of the 7 m array" (2.1 Data reduction)
- configurations: _not stated_
- baselines: 8.9-49.0 m (ACA), 15.1-783.5 m (12 m compact), 15.1-1813.1 m (12 m extended)  
  > "The baseline ranges covered by this setup are 8.9-49.0 m, $15.1 - 783.5$ m and $15.1 - 1813.1$ m for the ACA and the two 12 m setups, respectively." (2.1 Data reduction)
- angular resolution: CO(3-2) 0.17" x 0.13" (2.9 x 2.2 pc); CO(1-0) 1.85" x 1.32"; CO(2-1) 1.70" x 1.02"  
  > "spatial resolution | $1.85\ensuremath{''} \times 1.32\ensuremath{''}$ | $1.70\ensuremath{''} \times 1.02\ensuremath{''}$ | $0.17\ensuremath{''} \times 0.13\ensuremath{''}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: RMS per channel: 1.99 mJy/beam (CO1-0), 2.19 (CO2-1), 0.81 mJy/beam = 0.37 K (CO3-2)  
  > "RMS noise per channel | 1.99 mJy beam$^{-1}$ | 2.19 mJy beam$^{-1}$ | 0.81 mJy beam$^{-1}$" (Table 1)
- time on source: Band 7 total 48h45m (TP 27h23m, ACA 14h57m, 12 m compact 2h37m, 12 m extended 3h59m)  
  > "The total on-source observation time is $48^h45^m$ split across $27^h:23^m$ (TP), $14^h57^m$ (ACA), $2^h37^m$ (12 m compact) and $3^h59^m$ (12 m extended)." (2.1 Data reduction)
- observing dates: Band 7: Dec 2015 to Nov 2016, mainly first half of 2016  
  > "The observations were carried out primarily in the first half of 2016" (2.1 Data reduction)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Line: CO 2-1 (not stated)
- Line: CO 1-0 (not stated)
- External data: CO(1-0) and CO(2-1) ALMA data products (band 3 and 6)  
  > "Data products for CO(1–0) are shown in (cite: 2013Natur.499..450B), (cite: 2015ApJ...801...63M), (cite: Leroy:2015ds) and (cite: 2018ApJ...867..111Z) presents the CO(2–1) data." (2.2 Imaging) [from Bolatto et al. 2013; Meier et al. 2015; Leroy et al. 2015; Zschaechner et al. 2018]
- External data: CO line ratios r21=0.80, r31=0.67  
  > "we assume typical line ratios of $r_{21} = 0.80$ and $r_{31} = 0.67$ relative to CO(1–0) as implied by (cite: 2018ApJ...867..111Z)" (4.2 Masses of components) [from Zschaechner et al. 2018]
- External data: alpha_CO = 1.1 Msun (K km/s pc^2)^-1, X_CO = 0.5e20, starburst value  
  > "corresponding to $\alpha_\mathrm{CO} = 1.1\,\mathrm{M}_\odot\,\left(\mathrm{K\,km\,s}^{-1}\,\mathrm{pc}^{-1}\right)^{-1}$ discussed by (cite: Leroy:2015ds)" (4.2 Masses of components) [from Leroy et al. 2015]
- External data: SFR in central region 1.7-2.8 Msun/yr  
  > "The present day star formation rate in the central region of NGC 253 is $1.7-2.8$ M$_\odot$ yr$^{-1}$" (4.3 Mass outflow rate) [from Ott et al. 2005; Leroy et al. 2015; Bendo et al. 2015]
- External data: Ionized outflow opening angle ~60 deg  
  > "the NGC 253 outflow is approximately bi-conical with an axis normal to the disk and an opening angle of $\sim60^\circ$ (cite: Westmoquette:2011bp)" (3.1) [from Westmoquette et al. 2011]
- External data: Escape velocity 500 km/s  
  > "no gas reaches the escape velocity of $v_\mathrm{esc} = 500$ km s$^{-1}$(cite: 2017ApJ...835..265W)" (4.3 Mass outflow rate) [from Walter et al. 2017]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline (cycle 3 for 12 m data, cycle 4 for others)  
  > "Visibilities of the 12 m data are calibrated using the ALMA cycle 3 pipeline in CASA 4.6.0 and the delivered calibration script." (2.1 Data reduction)
- casa version: CASA 4.6.0 (12 m); CASA 4.7.2 (others)  
  > "The other datasets are calibrated in CASA 4.7.2 and the cycle 4 pipeline." (2.1 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (flux); J0006-0623 bandpass; J0038-2459 gain  
  > "J0006-0623 (bandpass); J0038-2459 (complex gain); the asteroid Pallas (absolute flux density)" (2.1 Data reduction)
- flux scale uncertainty: ~10-15%  
  > "The calibration uncertainty for the flux measurements is $\sim10-15\%$ for the ALMA observations." (4.2 Masses of components)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.4.0  
  > "Combined imaging of the interferometric data is done with the `tclean` task in CASA 5.4.0" (2.2 Imaging)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "Applying a Briggs weighting scheme with robust parameter 0.5" (2.2 Imaging)
- uv taper: _not stated_
- cell size: 0.05"  
  > "(pixel scale $0.05\ensuremath{''}$)" (2.2 Imaging)
- image size: _not stated_
- masking: clean mask from low-resolution compact 12 m CO(3-2) image; cleaned to 2.5x RMS  
  > "using a clean mask derived from a low resolution image of the compact 12 m array CO(3–2) data only" (2.2 Imaging)
- multiscale scales: _not stated_
- continuum subtraction: first order polynomial in uv plane on line-free channels  
  > "we subtract the continuum in the $U,V$ plane using a first order polynomial fitted to the channels that do not contain strong spectral lines" (2.1 Data reduction)
- line free channels: _not stated_
- primary beam correction: mosaic sensitivity pattern correction  
  > "We correct the cleaned images for the mosaic sensitivity pattern (mosaic primary beam response pattern)" (2.2 Imaging)
- array combination: 12 m interferometric images feathered with TP; ACA excluded  
  > "combine them with the TP images using `feather` and finally convert the units to brightness temperature." (2.2 Imaging); "For the final images, we do not consider the ACA data" (2.2 Imaging)
- smoothing: Regridded to 2.5 km/s; no beam matching, native resolution used  
  > "we do not match the spatial resolution to that of the data with the lowest resolution, but perform our analysis at the native resolution of each dataset" (2.2 Imaging)
- final beam: 0.17" x 0.13"  
  > "results in a synthesized beam of $0.17\ensuremath{''} \times 0.13\ensuremath{''}$" (2.2 Imaging)
- final rms: 0.81 mJy/beam (0.37 K) per channel for CO(3-2)  
  > "RMS noise per channel | 1.99 mJy beam$^{-1}$ | 2.19 mJy beam$^{-1}$ | 0.81 mJy beam$^{-1}$" (Table 1)

### Inherited from earlier work

- Data reduction and imaging of band 3 and 6 data (CO(1-0), CO(2-1))  
  > "For data reduction and imaging of the band 3 and 6 data see (cite: 2013Natur.499..450B), (cite: Leroy:2015ds), (cite: 2015ApJ...801...63M) and (cite: 2018ApJ...867..111Z)." (2.1 Data reduction) [from Bolatto et al. 2013; Leroy et al. 2015; Meier et al. 2015; Zschaechner et al. 2018]
- Kinematic center position  
  > "The slices assume the kinematic center is $\alpha,\delta = 00^h47^m33.134^s, -25^\circ17^m19.68^s$ (cite: MullerSanchez:2010dr)" (3.3) [from Müller-Sánchez et al. 2010]
- Disk fitting with diskfit  
  > "using the kinematic fitting tool `diskfit` (cite: 2007ApJ...664..204S; 2010MNRAS.404.1733S; 2015arXiv150907120S)" (3.4 Modeling the disk) [from Spekkens & Sellwood 2007; Sellwood & Sánchez 2010; Sellwood & Spekkens 2015]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- CO(1-0) and CO(2-1) data cubes (imaging parameters are only in earlier papers)
- Exact moment-mask and clean-mask definitions and the removed spiral-arm regions
- Region definitions for the western superbubble and the disk-co-spatial component
- Cone geometry and Monte Carlo details (number of draws, launch-site treatment)
- Exact feather parameters and single-dish scaling
- Dv(x) parameters were chosen visually, no objective criterion
- Outflow velocity reference for launching site; how outflow pixels are selected exactly

## Analysis recipe

1. **Image CO(3-2) mosaic**: tclean with Briggs weighting on 12 m data, primary-beam correction, feather with TP  
  > "Applying a Briggs weighting scheme with robust parameter 0.5 results in a synthesized beam of $0.17\ensuremath{''} \times 0.13\ensuremath{''}$" (2.2 Imaging)
   - software: CASA
   - parameter: 2.5 km/s channels; clean to 2.5 x RMS; masked at 5 sigma  
  > "All further steps work on the data cubes masked at $5.0 \sigma$" (2.2 Imaging)
   - fitting: _not stated_
   - validation: Compared images with and without ACA; flux scale and small-scale structure unchanged  
  > "we can confirm that neither the overall flux scale, nor the small scale structure is significantly altered" (2.2 Imaging)
2. **Model disk velocity field**: diskfit velocity-field fit (rotation plus m=2 bar) to CO(1-0) first-moment map masked at 20 sigma, plus a 2D Gaussian residual correction  
  > "`diskfit` will fit for rotation plus a bisymmetric model with $m=2$ perturbations to the potential (bar)" (Kinematic model of the central molecular gas)
   - software: diskfit
   - parameter: ellipse 75" major axis, PA=53 deg, eps=0.66; rings 12.5" to 300"  
  > "all pixels within an ellipse of $75\ensuremath{''}$ major axis length (`regrad`), $\mathrm{PA} = 53^\circ$ (`regpa`) and ellipticity $\epsilon = 0.66$" (Kinematic model)
   - assumption: No radial flows, no warp, centre fixed  
  > "We do not fit for radial flows (radial flows toggle)" (Kinematic model)
   - fitting: _not stated_
   - validation: Model fits velocity field better than +-25 km/s  
  > "The model typically fits the observed velocity field better than $\pm 25$ km s$^{-1}$" (Kinematic model)
3. **Separate disk and non-disk emission**: Slice cubes into 5" wide pV slices along PA=55 deg with 50% overlap; disk mask = model velocity +- Dv(x); non-disk is the complement  
  > "each slice is $5.0\ensuremath{''}$ (85 pc) wide, and we overlap slices by half their width ($2.5\ensuremath{''}$, 42 pc)" (3.3)
   - parameter: Dv(x)=120 exp(-(x/2.5)^2)+100 km/s, x in arcsec  
  > "\Delta v\,(x) = 120\,\exp \left( - \left(\frac{x}{2.5}\right)^2 \right) + 100" (3.4 Modeling the disk)
   - fitting: Dv parameters selected visually  
  > "the parameters (120, 2.5 and 100) in equation [\[equation: delta v\]](#equation: delta v) are visually selected to fit the fit pV diagrams as best as possible" (3.4 Modeling the disk)
   - validation: Varied mask width by 10%; luminosities change by 0.01 dex (disk) and ~0.07-0.12 dex (non-disk)  
  > "The effect of a $^{+10}_{-10}$% ($^{+0.04}_{-0.04}$ dex) variation in mask velocity width results in a $^{+0.01}_{-0.01}$ dex change in integrated disk luminosity" (Velocity width appendix)
4. **Measure CO luminosities and gas masses**: Integrate disk/non-disk luminosity; convert with starburst X_CO and line ratios; split non-disk into outflow, superbubble and other-disk  
  > "The total gas mass $M$ is estimated from the CO line luminosity, using the conversion factor $\mathrm{X}_{\mathrm{CO}} = 0.5\times10^{20}" (4.2 Masses of components)
   - parameter: r21=0.80, r31=0.67; includes helium  
  > "The masses we report include the contribution of Helium to the total mass." (4.2 Masses of components)
   - assumption: X_CO = 0.5e20 (alpha_CO = 1.1), uniform line ratios  
  > "we do not measure line ratios from the images but adopt a uniform factor" (4.2 Masses of components)
   - fitting: _not stated_
   - validation: Masses from the three transitions agree within 10% (disk) and 50% (non-disk); compared with literature masses  
  > "They match within 10% for the disk component, and within 50% for the non-disk component." (4.2 Masses of components)
5. **Derive outflow rate, energy and momentum**: Per-voxel rate m/(ds/v), binned by ejection time or distance; deprojected by cone geometry; E=0.5 m v^2, P=m v  
  > "we calculate the outflow rate $\dot{m}_i$ of the gas that was ejected at time $t_{{\mathrm{eject}},i}$ over the time interval $\Delta t_{\mathrm{cross},i}$" (4.3 Mass outflow rate)
   - parameter: Cone opening ~60 deg, axis perpendicular to disk, i=78 deg, theta 48-108 deg  
  > "the range of effective inclination of outflowing gas can be anywhere between $\theta = 48^\circ$ and $\theta = 108^\circ$" (4.3 Mass outflow rate)
   - assumption: Launch in the disk plane; flow perpendicular to bar plane; constant X_CO; two cases: no acceleration after launch, or constant outflow rate  
  > "we assume that the projected direction of flow is perpendicular the the central plane of the bar and that CO emission traces the mass with a constant conversion factor" (4.3 Mass outflow rate)
   - fitting: Monte Carlo over outflow direction on the cone surface; 16th-84th percentiles  
  > "We use a Monte Carlo approach to derive the errors introduced by deprojection" (4.3 Mass outflow rate)
   - validation: Compared with Bolatto et al. 2013 and Zschaechner et al. 2018 outflow rates  
  > "is consistent with this number using an independent and a more complete methodology than the original work" (4.3 Mass outflow rate)
6. **Compare with starburst energy and momentum**: Use Starburst99 bolometric output, SN energy and momentum injection rates to compute coupling efficiencies  
  > "According to Starburst99 (cite: Leitherer:1999jt), the bolometric magnitude of a starburst at an age of $10^7$ yr to $10^8$ yr is $M_\mathrm{bol} \sim -20.5$" (4.4)
   - software: Starburst99 (cited)
   - parameter: SFR 2.8 Msun/yr over 1 Myr  
  > "In 1 Myr, a constant SFR of 2.8 M$_\odot$ yr$^{-1}$ yields $8.9 \times 10^8$ M$_\odot$ km s$^{-1}$." (4.4)
   - assumption: 10^51 erg per SN, equal wind contribution (50%)  
  > "Each SN releases approximately $10^{51}$ erg in kinetic energy" (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.6.0 / 4.7.2 (calibration), 5.4.0 (imaging): Calibration, tclean imaging, feather, immoments  
  > "Combined imaging of the interferometric data is done with the `tclean` task in CASA 5.4.0" (2.2 Imaging)
- **diskfit** : Kinematic model of CO(1-0) disk velocity field  
  > "We derive a model for the velocity of the disk component from the CO(1–0) observations using the kinematic fitting tool `diskfit`" (3.4 Modeling the disk)
- **astropy** : Listed in software section  
  > "CASA (cite: McMullin:2007tj), astropy (cite: Collaboration:2013cd; Collaboration:2018ji), APLpy (cite: Robitaille:2012wl)" (Software)
- **APLpy** : Listed in software section (plotting)  
  > "CASA (cite: McMullin:2007tj), astropy (cite: Collaboration:2013cd; Collaboration:2018ji), APLpy (cite: Robitaille:2012wl)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk CO(3-2) luminosity | 1.8e8 | not stated | K km/s pc^2 | 4 | L$_\mathrm{CO}$               / K km s$^{-1}$ pc$^2$          / $2.8 \times 10^8$ / $4.2 \times 10^7$    / $2.3 \times 10^8$ / $4.5 \times 10^7$    / $1.8 \times 10^8$ / $1.2 \times 10^7$ |
| Non-disk CO(3-2) luminosity | 1.2e7 | not stated | K km/s pc^2 | 4 | L$_\mathrm{CO}$               / K km s$^{-1}$ pc$^2$          / $2.8 \times 10^8$ / $4.2 \times 10^7$    / $2.3 \times 10^8$ / $4.5 \times 10^7$    / $1.8 \times 10^8$ / $1.2 \times 10^7$ |
| Total central molecular gas mass | ~3.6e8 | factor ~2 systematic | Msun | 4 | The total gas mass in the center of NGC 253 is $\sim 3.6 \times 10^8$ M$_\odot$, with $\sim 0.5 \times 10^8$ M$_\odot$ in the non-disk component. |
| Outflow rate, constant-rate case, CO(1-0) | 29 | +0.48/-0.35 dex | Msun/yr | 5 | 29 M$_\odot$ yr$^{-1}$($^{+0.48}_{-0.35}$ dex), 39 M$_\odot$ yr$^{-1}$($^{+0.49}_{-0.34}$ dex) |
| Outflow rate, constant-rate case, CO(2-1) | 39 | +0.49/-0.34 dex | Msun/yr | 5 | 29 M$_\odot$ yr$^{-1}$($^{+0.48}_{-0.35}$ dex), 39 M$_\odot$ yr$^{-1}$($^{+0.49}_{-0.34}$ dex) |
| Outflow rate within past 1 Myr, CO(1-0) | 14 | +0.25/-0.29 dex | Msun/yr | 5 | the *average* outflow rates are 14 M$_\odot$ yr$^{-1}$($^{+0.25}_{-0.29}$ dex), 20 M$_\odot$ yr$^{-1}$($^{+0.27}_{-0.37}$ dex) |
| Mass loading factor | 5.4-23.5 | not stated | dimensionless | 5 | This results in a mass loading factor $\eta = \dot{M}_\mathrm{out} / \dot{M}_\mathrm{SFR}$ in the range $\eta \sim 5.4-23.5$. |
| Outflow kinetic energy within 340 pc, CO(1-0) | 2.5e54 | +0.96/-0.65 dex | erg | 5 | the kinetic energies amount to $2.5 \times 10^{54}$ erg ($^{+0.96}_{-0.65}$ dex) in CO(1–0) |
| Outflow momentum within 340 pc, CO(1-0) | 4.8e8 | +0.48/-0.35 dex | Msun km/s | 5 | $4.8 \times 10^8$ M$_\odot$ km s$^{-1}$($^{+0.48}_{-0.35}$ dex) in CO(1–0) |
| Kinetic energy coupling efficiency to SN kinetic energy | ~8 | order of magnitude | % | 6 | the observed starburst is sufficient to kinetically power the measured molecular outflows with $\sim 8\%$ efficiency |

## Qualitative findings

- A significant fraction of the outflow emission is faint and diffuse rather than in discrete streamers.  
  > "A significant amount of the outflow emission we identify is faint and diffuse, while part of the emission is in discrete, higher surface brightness structures" (Summary)
- No gas reaches the escape velocity of 500 km/s.  
  > "In our data, no gas reaches the escape velocity of $v_\mathrm{esc} = 500$ km s$^{-1}$" (4.3)

## Claim tuples

- H: A non-disk component can be separated kinematically from the disk in all three CO lines | E: diskfit disk model plus pV-slice disk mask applied to CO(1-0), (2-1), (3-2) | R: Non-disk luminosity fraction ~7-16%; masses agree within 50% | F: ~15% of the central gas mass (~0.5e8 Msun) is non-disk | **supported**
- H: The molecular outflow rate exceeds the SFR | E: Voxel-wise outflow rate with Monte Carlo deprojection | R: 14-39 Msun/yr, 0.4 dex uncertainty | F: Mass loading eta ~8-20 to ~300 pc | **supported**
- H: Starburst feedback can power the outflow energetically | E: Compare outflow energy and momentum to SN and wind injection | R: ~8% of kinetic energy and ~2.5-4% of momentum | F: Starburst can power outflow; geometry is the main uncertainty | **supported**

## Reasoning

- Why this data: Higher resolution CO(3-2) is needed to disentangle outflow from disk  
  > "Also, resolution plays an important role in the ability to disentangle outflows from material in the starbursting disk." (Introduction)
- Why this method: Disk mask built from a velocity-field model in 2D pV slices to avoid biases  
  > "In order to avoid introducing biases we model the large-scale disk velocity field and use this model as the basis of the kinematic separation." (3.1)
- Alternative: ACA data excluded as they introduce large-scale noise fluctuations at the mosaic edge  
  > "we do not consider the ACA data as they introduce large scale noise fluctuation towards the edge of the mosaic" (2.2 Imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): CO(3-2) field of view is small and surface brightness sensitivity is low, so its outflow values are lower limits  
  > "The measurements in CO(3–2) should thus be interpreted as a lower limit" (4.3)
- Limitation (authors): Unknown outflow geometry and launching sites dominate uncertainty  
  > "The unknown outflow geometry and launching sites are the primary source of uncertainty in this study." (abstract)
- Caveat (inferred, ours): Visually chosen Dv(x) disk mask defines the non-disk fraction
- Caveat (inferred, ours): Fixed X_CO and uniform line ratios across disk and outflow
- Caveat (inferred, ours): Non-disk gas may include infall; all treated as outflow
- Caveat (inferred, ours): Summary eta definition inverted and CO(2-1) luminosity text typo, minor inconsistencies

## Reproducibility

- Data public (paper): ALMA data identified by project code in Table 1 and acknowledgments; archival CO(1-0), CO(2-1)  
  > "Together with archival ALMA CO(1–0) and CO(2–1) data" (abstract)
- Products in archive: _not stated_
- Missing: Imaging recipe for CO(1-0) and CO(2-1) cubes (in earlier papers)
- Missing: Mask regions and Monte Carlo details
- Missing: No code released
- Data volume (inferred): Hundreds of GB to ~1 TB across three bands including mosaics, TP and ACA
- Score (inferred): 3/5, Data are public and the method is described in detail, but key choices rely on earlier papers, visual mask tuning and unstated region definitions.
- Rediscovery candidate: no, Requires multiple archival datasets processed per earlier papers and subjective region definitions; the recipe is not fully reproducible.

## Links

- Method: Spekkens & Sellwood 2007; Sellwood & Spekkens 2015 (diskfit) (Disk kinematic fitting tool)
- Companion: Bolatto et al. 2013 (Original CO(1-0) detection of NGC 253 molecular outflow)
- Companion: Zschaechner et al. 2018 (CO(2-1) data and line ratios)
- Companion: Leroy et al. 2018 (High-resolution super star cluster study of NGC 253)

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 94,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00172.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00172.S",
  "2013.1.00191.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 70,
  "rate": 0.787
 },
 "evidence_ok": true
}
```
