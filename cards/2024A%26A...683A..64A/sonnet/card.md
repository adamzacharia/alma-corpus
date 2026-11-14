# Extended Lyman-α emission towards the SPT2349-56 protocluster at z = 4.3

`2024A&A...683A..64A` | Astronomy and Astrophysics 2024 | first author: Apostolovski, Yordanka | arXiv: 2301.01328 | DOI: 10.1051/0004-6361/202245785

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Do the SPT2349-56 protocluster and its dusty galaxies show Lyman-alpha emitters or extended Lyman-alpha emission, and what powers any extended structure?  
  > "We conducted a deep Lyman-$\alpha$ line emission survey around SPT2349-56 using the Multi-Unit Spectroscopic Explorer (MUSE) at Very Large Telescope (VLT) in order to characterize this uniquely dense environment." (abstract)
- Target **SPT2349-56**: coordinates _not stated_; z/distance z=4.304  
  > "SPT2349-56 is located at $z=4.304$ and has a surface density of more than ten times the average blank-field value and a volume density 1000 times the average" (1 Introduction); distance from mean [CII]-derived redshift from ALMA (Miller et al. 2018; Hill et al. 2020)  
  > "SPT2349-56 is located at $z=4.304$ and has a surface density of more than ten times the average blank-field value and a volume density 1000 times the average" (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00273.S, 2018.1.00058.S
- bands: Band 7 ([CII])  
  > "observations of the redshifted \[CII\]$_{158\mu\text{m}}$ fine structure line towards the SPT2349-56 system were obtained using ALMA in Band 7." (2.2 Previous ALMA observations)
- frequencies and spectral setup: centered at 358.4 GHz  
  > "These were centered at a frequency of $\nu_{obs}=358.4$ GHz" (2.2 Previous ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.43'' x 0.34'' average synthesized beam  
  > "yielding an average synthesized beam size of $0.43'' \times 0.34''$ and 3$\sigma$ sensitivities of $\approx 0.3$ mJy beam$^{-1}$" (2.2 Previous ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 3 sigma ≈ 0.3 mJy/beam  
  > "yielding an average synthesized beam size of $0.43'' \times 0.34''$ and 3$\sigma$ sensitivities of $\approx 0.3$ mJy beam$^{-1}$" (2.2 Previous ALMA observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 micron fine structure (not stated)
- Line: CO 4-3 (not stated)
- Other facility **VLT/MUSE**: Primary data: two WFM pointings, 5 h each, Lyman-alpha datacubes  
  > "Each pointing was observed for 5 hours (a total of 10 hours) between November 2017 and September 2018." (2.1 MUSE observations)
- Other facility **HST/WFC3-IR**: F110W and F160W images, program 15701  
  > "We used HST/*Wide Field Camera 3 (WFC3)-IR* images under program 15701 (PI: S. Chapman)." (2.3 HST imaging)
- Other facility **APEX/LABOCA**: 870 micron maps showing the IR-bright structures  
  > "The SPT2349-56 system has two main infrared (IR) bright structures as seen in the APEX/LABOCA 870 $\mu$m maps" (1 Introduction)
- External data: ALMA [CII]/CO(4-3) source catalogue, positions, redshifts, line widths and fluxes of protocluster members (C1-C23, NL3)  
  > "previously identified through ALMA Cycle 5 and 6 observations. These observations and the corresponding data reduction and source identification are described in detail by (cite: miller18) and (cite: hill20)" (2.2 Previous ALMA observations) [from (cite: miller18); (cite: hill20)]
- External data: Protocluster core dynamical mass ~9e12 Msun used for escape velocity  
  > "The significant mass of the central core of the protocluster is $\sim 9 \times 10^{12} M_\odot$" (4.1 Lyman-alpha emitters) [from (cite: hill20)]
- External data: Field LAE counts from MUSE HUDF (144 LAEs at z=4-5 above logL=41.0)  
  > "(cite: drake17) finds 144 LAEs in the redshift range $z=4.0-5.0$." (4.1 Lyman-alpha emitters) [from (cite: drake17); (cite: inami17)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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

- ALMA data reduction and source identification  
  > "we refer the reader to those papers for full details." (2.2 Previous ALMA observations) [from (cite: miller18); (cite: hill20)]
- Lya-to-systemic velocity correction  
  > "we obtain a statistical correction to the systemic redshift of each galaxy using the relation described in (cite: verhamme18)" (4.1 Lyman-alpha emitters) [from (cite: verhamme18)]
- Lya luminosity to SFR conversion  
  > "Following (cite: furlanetto05), the Lyman-$\alpha$ emission can be used to yield an estimate of the underlying SFR from the powering source." (4.4 The protocluster core as the origin for the LAB?) [from (cite: furlanetto05)]

### Not stated but needed to reproduce (our reading)

- LSDCat filter kernel sizes and smoothing parameters
- Continuum subtraction method for narrowband image
- Exact narrowband image/flux extraction method and noise estimates
- tlac fitting settings (priors, number of photons, sampler)
- Coordinates of target and ALMA source positions
- ALMA calibration/imaging details (in earlier papers)

## Analysis recipe

1. **Reduce and combine MUSE cubes**: MUSE pipeline, combine OB cubes with MPDAF sigma-clipped mean, ZAP sky subtraction  
  > "The data cubes were merged using a sigma-clipped mean with $\sigma_{\text{clip}}=5$." (2.1 MUSE observations)
   - software: MUSE pipeline, MPDAF, ZAP
   - parameter: sigma_clip = 5; mask on continuum sources for ZAP  
  > "For this process, we used a mask in order to avoid spaxels that contained obvious continuum sources." (2.1 MUSE observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind LAE search**: LSDCat 3D matched filtering over 4000 km/s around z=4.304; threshold set from negative cube; FWHM filter 50-600 km/s  
  > "we find that the most significant feature in the negative cube is found at (snr)$_{\rm{det}}$ $\sim 5$, thus yielding our detection threshold." (3.1 Blind Search)
   - software: LSDCat
   - parameter: snr_det ~5; FWHM 50-600 km/s; 1 arcsec apertures (2 arcsec for LAE3, LAE8)  
  > "We extracted the spectra of each of the LAE candidates using apertures with radii of 1 arcsec." (3.1 Blind Search)
   - fitting: _not stated_
   - validation: Manual inspection of spectra for lower-z lines; secure vs tentative split by aperture significance  
  > "All the spectra were manually inspected and searched for other lines that would point to a lower redshift possibility." (3.1 Blind Search)
3. **Narrowband image and LAB flux**: Continuum-subtracted smoothed narrowband image, 2000 km/s width (6401.3-6487.2 A); polygon of pixels >2 sigma for spectrum  
  > "we draw a polygon around this source, containing all pixels detected above 2$\sigma$ in the narrowband image" (3.2 Narrowband Image)
   - software: LSDCat
   - fitting: _not stated_
   - validation: _not stated_
4. **Boundness and field-count comparison, SFR**: Compare velocities with escape velocity envelope; compare to HUDF counts; SFR from Furlanetto relation  
  > "Galaxies that have velocities lower than the the escape velocity envelope at a given radius from the protocluster core are expected to be bound to the structure." (4.1 Lyman-alpha emitters)
   - assumption: Salpeter IMF, two thirds of ionizing photons absorbed in dense ISM; flat LCDM h=0.677  
  > "For star formation episodes following a Salpeter initial mass function (cite: salpeter59) and that two thirds of the ionizing photons are absorbed in the dense ISM, we have:" (4.4 The protocluster core as the origin for the LAB?)
   - fitting: _not stated_
   - validation: _not stated_
5. **Shell-model radiative transfer of LAB spectrum**: tlac Monte Carlo expanding-shell fits with z_sys constrained to 3 sigma [CII] redshift range of C10, C14, C17, core  
  > "we allow for a range in redshift given by the $3\sigma$ uncertainty around measured \[CII\] redshift in each case." (4.5 Modeling the Lyman-alpha spectrum of the extended emission)
   - software: tlac
   - parameter: seven shell parameters: v_exp, N_HI, tau_d, T, z_sys, EW, FWHM  
  > "The shell model is defined by a set of seven parameters" (4.5 Modeling the Lyman-alpha spectrum of the extended emission)
   - assumption: homogeneous spherical expanding shell with mixed HI and dust, central source  
  > "The model assumes an homogeneous, spherical shell that expands radially outwards, with uniformly mixed neutral gas (HI) and dust" (4.5 Modeling the Lyman-alpha spectrum of the extended emission)
   - fitting: _not stated_
   - validation: Model 0 judged not to converge to a proper fit  
  > "We find that the model $0$ does not converge into a proper fit to the data" (4.5 Modeling the Lyman-alpha spectrum of the extended emission)

## Software

- **LSDCat** : blind line search and narrowband image  
  > "using the Line Source Detection and Cataloguing Tool (`LSDCat`; (cite: lsdcat))" (3.1 Blind Search)
- **MUSE pipeline** v2.6: basic reduction  
  > "We reduced the data using the MUSE pipeline v2.6 (cite: weilbacher14)" (2.1 MUSE observations)
- **MPDAF** : combining OB cubes  
  > "We combined the five OB data cubes per field using the MUSE Python Data Analysis Framework (MPDAF; (cite: mpdaf))." (2.1 MUSE observations)
- **ZAP** : PCA sky subtraction  
  > "we used Zurich Atmosphere Purge (ZAP; (cite: zap)) to perform a sky subtraction through principal component analysis (PCA)" (2.1 MUSE observations)
- **tlac** : Lyman-alpha radiative transfer shell models  
  > "the Lyman-$\alpha$ Monte Carlo Radiate Transfer code `tlac` (cite: gronke14a; gronke15)" (4.5 Modeling the Lyman-alpha spectrum of the extended emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| LAB Lyα flux | 3663e-20 | ±1030e-20 (table) | erg cm^-2 s^-1 | 3 | we obtain a flux of $S_{\text{Ly}\alpha} = 3663 \times 10^{-20}$ erg cm$^{-2}$ s$^{-1}$ |
| LAB Lyα FWHM | 760 | ±40 | km/s | 3 | the extended feature shows a line with a FWHM of about $760$ km s$^{-1}$ |
| LAB velocity offset from protocluster z | 365 | not stated | km/s | 3 | a velocity offset with respect to the \[CII\]/CO protocluster redshift of $\Delta v = 365$ km s$^{-1}$ |
| LAB area | 3720 | not stated | kpc^2 | 3 | With a radius of $\approx5''$ (34.4 kpc), this yields an area, $\pi r^2=3720$ kpc$^2$ |
| Number of secure LAEs | 3 | not stated | dimensionless | 2 | Only three sources are securely detected in this fashion (LAE1, LAE3 and LAE8) |
| Expected blank-field LAEs | 3-4 | not stated | dimensionless | 4 | we would thus expect to have found $3-4$ LAEs. |
| LAB SFR from Lyα | 1.32 | 0.37 | Msun/yr | 4 | we obtain a SFR for the extended emission of $1.32 \pm 0.37 \ M_\odot$ yr$^{-1}$ |
| Median Lyα velocity offsets north/south | 930 / 430 | not stated | km/s | 2 | The northern and southern LAEs are found to have velocity offsets of $\Delta v = 930$ and $\Delta v = 430$ km s$^{-1}$ respectively |

## Qualitative findings

- Previously known DSFGs are undetected in Lyα (except tentative NL3), consistent with dust obscuration  
  > "All the previously-identified DSFGs in this field are undetected in Lyman-$\alpha$ emission, consistent with the conspicuous dust obscuration in these systems." (abstract)

## Claim tuples

- H: Does SPT2349-56 host an overdensity of LAEs? | E: Blind LSDCat search in MUSE cubes compared with HUDF field counts | R: 3 secure LAEs vs 3-4 expected | F: No LAE overdensity; system is dust-obscured | **supported**
- H: Is there extended Lyα emission near the core? | E: Smoothed narrowband image around z=4.304 | R: ~60x60 kpc^2 LAB 56 kpc from the core, overlapping C10, C14, C17 | F: A LAB is present | **supported**
- H: What powers the LAB? | E: Shell-model tlac fits and velocity comparison with [CII] | R: C14, C17 and core give good fits; C10 does not | F: C14/C17 or the core power the LAB; in-situ production more likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stacking Lyα spectra of undetected SMGs rejected as Lyα does not trace systemic redshift  
  > "We note that stacking of the MUSE spectra to yield a constrain on the average Lyman-$\alpha$ emission in these undetected SMGs is difficult." (3.3 Previously Known Protocluster Members)
- How they decided it was enough: _not stated_
- Limitation (authors): Model fits alone cannot disentangle origin of the LAB  
  > "Based on these results alone it is hard to disentangle the origin of the LAB." (4.5 Modeling the Lyman-alpha spectrum of the extended emission)
- Caveat (inferred, ours): Inconsistent LAB offset direction (east vs west) in text
- Caveat (inferred, ours): Fit uncertainties and sampler not described
- Caveat (inferred, ours): LAB flux uncertainty and 2-sigma polygon dependent
- Caveat (inferred, ours): SFR relation ignores AGN and scattering

## Reproducibility

- Data public (paper): MUSE ESO programme IDs and ALMA project codes given  
  > "as a part of projects 0100.A-0437(A) and 0100.A-0437(B) (PI: M. Aravena)" (2.1 MUSE observations)
- Products in archive: _not stated_
- Missing: LSDCat parameters
- Missing: tlac fitting configuration
- Missing: ALMA catalogue from Hill et al. 2020
- Data volume (inferred): ~10-30 GB MUSE cubes; ALMA products small
- Score (inferred): 3/5, Public MUSE data and named tools but several parameters missing; ALMA role minor.
- Rediscovery candidate: no, Main data are MUSE and the recipe lacks key parameters; ALMA only a reference.

## Links

- Method: (cite: lsdcat) (LSDCat detection method)
- Method: (cite: gronke15) (tlac shell-model parameters)
- Companion: (cite: miller18); (cite: hill20) (ALMA observations and source catalogue)
- Related: SPT survey
- Related: MUSE HUDF

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 80,
  "stated": 37,
  "rate": 0.463
 },
 "evidence_ok": true
}
```
