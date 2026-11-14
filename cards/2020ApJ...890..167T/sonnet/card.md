# The Fifth Candidate for an Intermediate-mass Black Hole in the Galactic Center

`2020ApJ...890..167T` | The Astrophysical Journal 2020 | first author: Takekawa, Shunya | arXiv: 2002.05173 | DOI: 10.3847/1538-4357/ab6f6f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism
- Question: What is the internal structure and kinematics of the high-velocity compact cloud HCN–0.085–0.094, and does it harbor an intermediate-mass black hole?  
  > "This paper reports on the results of the ALMA high-resolution observations of HCN–0.085–0.094 and the discovery of a very compact molecular clump showing a signature of a rotational motion." (Introduction)
- Target **HCN–0.085–0.094**: coordinates field centered at (l, b) = (-0.083°, -0.091°)  
  > "HCN–0.085–0.094 is at a projected distance of $\sim 8$ pc from the Galactic nucleus Sgr A$^*$ (cite: takekawa17b)." (Introduction); "The distance to the Galactic center is assumed to be $D=8$ kpc." (Introduction); z/distance D = 8 kpc (assumed Galactic center distance)  
  > "HCN–0.085–0.094 is at a projected distance of $\sim 8$ pc from the Galactic nucleus Sgr A$^*$ (cite: takekawa17b)." (Introduction); "The distance to the Galactic center is assumed to be $D=8$ kpc." (Introduction); distance from assumed  
  > "HCN–0.085–0.094 is at a projected distance of $\sim 8$ pc from the Galactic nucleus Sgr A$^*$ (cite: takekawa17b)." (Introduction); "The distance to the Galactic center is assumed to be $D=8$ kpc." (Introduction)

## Data provenance

- ALMA projects: 2017.1.01557.S
- bands: _not stated_
- frequencies and spectral setup: HCN 4–3 (354.5 GHz), HCO+ 4–3 (353.6 GHz), CS 7–6 (342.9 GHz); spw bandwidths 1, 0.5, 2 GHz; 1.953 MHz channels  
  > "The bandwidths of the spectral windows were 1, 0.5, and 2 GHz with a 1.953 MHz channel width for the HCN, HCO$^+$, and CS observations, respectively." (Observations)
- continuum bandwidth: _not stated_
- arrays: 7 m, 12 m and Total Power arrays  
  > "with eleven 7 m antennas (on May 13), forty-six 12 m antennas (on May 14), and four Total Power (TP) antennas (on May 24 and 28)." (Observations)
- configurations: 12 m array C43-2  
  > "The 12 m array observations were operated in the C43-2 configuration with baseline lengths of 15–314 m." (Observations)
- baselines: 15–314 m (12 m array)  
  > "The 12 m array observations were operated in the C43-2 configuration with baseline lengths of 15–314 m." (Observations)
- angular resolution: ~0.93"x0.76" (HCN)  
  > "$0\ensuremath{''}.93\times 0\ensuremath{''}.76$ with a position angle (PA) of $-27\ensuremath{^\circ}.3$ at 354.5 GHz" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 7, 9, 6 mJy/beam (HCN, HCO+, CS)  
  > "the rms noise levels of the HCN, HCO$^+$, and CS cubes were 7, 9, and 6 mJy beam$^{-1}$, respectively." (Observations)
- time on source: 51.74, 10.89, 186.48 min for 7 m, 12 m, TP  
  > "The on-source times were 51.74, 10.89, and 186.48 min for the 7 m, 12 m, and TP array observations, respectively." (Observations)
- observing dates: 2018 May 13, 14, 24, 28  
  > "were performed in 2018 May with eleven 7 m antennas (on May 13), forty-six 12 m antennas (on May 14)" (Observations)
- pi or archival as stated: _not stated_
- Line: HCN J=4–3 (354.5 GHz)
- Line: HCO+ J=4–3 (353.6 GHz)
- Line: CS J=7–6 (342.9 GHz)
- Other facility **VLA**: 5.5 GHz continuum image  
  > "Very Large Array (VLA) 5.5 GHz continuum image (cite: zhao13; zhao16)" (Counterparts)
- Other facility **HST**: Paschen alpha emission image  
  > "the *Hubble Space Telescope* (*HST*) P$\alpha$ emission image (cite: wang10; dong11)" (Counterparts)
- Other facility **Chandra**: X-ray point source catalog  
  > "the *Chandra* X-ray point source catalog (cite: muno09)" (Counterparts)
- Other facility **Spitzer**: 24 micron image for mid-IR luminosity  
  > "the *Spitzer* 24 $\mu$m image (cite: carey09) provides a mid-infrared luminosity toward T1 of $\sim10^2$ $L_\odot$" (Origin of T1)
- External data: VLA 5.5 GHz continuum image  
  > "Very Large Array (VLA) 5.5 GHz continuum image (cite: zhao13; zhao16)" (Counterparts) [from (cite: zhao13; zhao16)]
- External data: HST Pa alpha image  
  > "the *Hubble Space Telescope* (*HST*) P$\alpha$ emission image (cite: wang10; dong11)" (Counterparts) [from (cite: wang10; dong11)]
- External data: Chandra X-ray point source catalog  
  > "the *Chandra* X-ray point source catalog (cite: muno09)" (Counterparts) [from (cite: muno09)]
- External data: HCN abundance [HCN]/[H2] = 4.8e-8  
  > "a fractional abundance of $\rm [HCN]/[H_2] = 4.8\times10^{-8}$ (cite: tanaka09; oka11)" (Origin of T1) [from (cite: tanaka09; oka11)]

## Processing

### Calibration

- pipeline or manual: calibration script provided by the East Asian ALMA Regional Center  
  > "The calibration was performed in CASA version 5.1.2 with the calibration script provided by the East Asian ALMA Regional Center." (Observations)
- casa version: CASA 5.1.2 (calibration); 5.4.1 (imaging)  
  > "The calibration was performed in CASA version 5.1.2 with the calibration script provided by the East Asian ALMA Regional Center." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924–2914 and J1517–2422 (flux and bandpass)  
  > "J1924–2914 and J1517–2422 were used for the flux and bandpass calibrations." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.4.1  
  > "The interferometric images were created by the task “tclean", using Briggs weighting with a robust parameter of 0.5 in CASA version 5.4.1" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "Continuum emissions were subtracted from the visibility data by the task “uvcontsub”." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: interferometric and TP images combined with feathering  
  > "generated by combining the interferometric images and TP images with the task “feathering"." (Observations)
- smoothing: CS moment-1 smoothed with 1.5" FWHM Gaussian for model fit  
  > "we used the moment-1 values of the CS image smoothed with a Gaussian kernel of $1.5\ensuremath{''}$ FWHM" (Keplerian Model)
- final beam: 0.93"x0.76" PA -27.3° (HCN); 0.93"x0.76" PA -28.1° (HCO+); 0.95"x0.77" PA -28.3° (CS)  
  > "$0\ensuremath{''}.95\times 0\ensuremath{''}.77$ with a PA of $-28\ensuremath{^\circ}.3$ at 342.9 GHz" (Observations)
- final rms: 7, 9, 6 mJy/beam at 2 km/s resolution  
  > "the rms noise levels of the HCN, HCO$^+$, and CS cubes were 7, 9, and 6 mJy beam$^{-1}$, respectively." (Observations)

### Inherited from earlier work

- Keplerian orbital fitting approach and coordinate definition  
  > "This coordinate definition is the same one used in (cite: takekawa19a)." (Keplerian Model) [from (cite: takekawa19a)]
- LTE optically thin mass estimate with Tex = 36 K  
  > "with an excitation temperature of 36 K in the optically thin limit (cite: takekawa17b)" (Origin of T1) [from (cite: takekawa17b)]

### Not stated but needed to reproduce (our reading)

- Channel ranges used for continuum estimation in uvcontsub
- tclean cell size, image size, niter, threshold, masking
- Number and positions of loci beyond the figure, and fit uncertainties' definition
- Feathering parameters
- Exact moment-map clipping thresholds
- Fitting code for orbit and chi-square grid

## Analysis recipe

1. **Calibrate and image the data**: Calibration script from EA ARC, uvcontsub, tclean (Briggs), feather with TP  
  > "The final image cubes of the HCN, HCO$^+$, and CS lines were generated by combining the interferometric images and TP images with the task “feathering"." (Observations)
   - software: CASA
   - parameter: robust = 0.5; 2 km/s velocity resolution  
  > "using Briggs weighting with a robust parameter of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Keplerian orbit geometry to T1 ring**: Least-squares fitting of orbital elements to loci of the ring  
  > "By least-square fitting to the loci, we determined the orbital parameters: the semimajor axis ($a$), eccentricity ($e$), longitude of ascending node ($\Omega$), argument of pericenter ($\omega$), and inclination angle ($i$)." (Keplerian Model)
   - parameter: dynamical center at (l,b)=(-0.0841°,-0.0957°)  
  > "We placed the dynamical center at $(l,\ b)=(-0\ensuremath{^\circ}.0841,\ -0\ensuremath{^\circ}.0957)$" (Keplerian Model)
   - assumption: Keplerian motion  
  > "we performed orbital fitting to the T1 ring assuming a Keplerian motion." (Keplerian Model)
   - fitting: least squares  
  > "By least-square fitting to the loci, we determined the orbital parameters: the semimajor axis ($a$), eccentricity ($e$), longitude of ascending node ($\Omega$), argument of pericenter ($\omega$), and inclination angle ($i$)." (Discussion, Keplerian Model)
   - validation: best-fit orbit projected on maps  
  > "The best-fit orbit is projected in Figures 3(a) and (b)." (Keplerian Model)
3. **Fit dynamical mass and systemic velocity**: Chi-square minimization of observed moment-1 velocities along the ring  
  > "we estimated the mass ($M_{\rm dyn}$) and line-of-sight velocity ($V_{\rm sys}$) of the dynamical center by fitting the observed velocities on the T1 ring with a chi-square ($\chi^2$) minimization approach." (Keplerian Model)
   - parameter: CS moment-1 smoothed with 1.5" FWHM  
  > "we used the moment-1 values of the CS image smoothed with a Gaussian kernel of $1.5\ensuremath{''}$ FWHM" (Keplerian Model)
   - assumption: D = 8 kpc  
  > "The distance to the Galactic center is assumed to be $D=8$ kpc." (Introduction)
   - fitting: chi-square minimization with confidence contours in Mdyn–Vsys  
  > "Figure 3(f) shows the confidence level contours as a function of $M_{\rm dyn}$ and $V_{\rm sys}$." (Keplerian Model)
   - validation: modeled velocity field compared with observed  
  > "Figure 3(e) shows the modeled velocity field with the best-fit parameters." (Keplerian Model)
4. **Test protostellar outflow alternative**: LTE gas mass from HCN, kinetic energy, compared with Spitzer 24 micron luminosity  
  > "The molecular gas mass of T1 was estimated to be approximately 2 $M_\odot$ according to the HCN intensity under the assumption of the local thermodynamic equilibrium (LTE)" (Origin of T1)
   - assumption: Tex = 36 K, optically thin, [HCN]/[H2]=4.8e-8  
  > "with an excitation temperature of 36 K in the optically thin limit (cite: takekawa17b) and a fractional abundance of $\rm [HCN]/[H_2] = 4.8\times10^{-8}$" (Origin of T1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.2 (calibration), 5.4.1 (imaging): calibration, uvcontsub, tclean, feathering  
  > "The data were calibrated and reduced with the Common Astronomy Software Applications (cite: mcmullin07) software package." (Observations)
- **Astropy** : listed in software section  
  > "CASA (cite: mcmullin07), Astropy (cite: astropy13; astropy18), Matplotlib (cite: hunter07), Numpy (cite: vanderwalt11)" (Software)
- **Matplotlib** : listed in software section  
  > "CASA (cite: mcmullin07), Astropy (cite: astropy13; astropy18), Matplotlib (cite: hunter07), Numpy (cite: vanderwalt11)" (Software)
- **Numpy** : listed in software section  
  > "CASA (cite: mcmullin07), Astropy (cite: astropy13; astropy18), Matplotlib (cite: hunter07), Numpy (cite: vanderwalt11)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamical mass log10(M/Msun) | 4.10 | +0.05/-0.10 | dimensionless | 3 | $\log_{10}({M_{\rm dyn}}/M_\odot) = 4.10^{+0.05}_{-0.10}$ |
| Systemic velocity Vsys | -25.75 | 1.25 | km/s | 3 | $V_{\rm sys} = -25.75\pm1.25$ km s$^{-1}$ |
| Semi-major axis | 0.075 | 0.005 | pc | 2 | Semi-major axis, $a$                  / $0.075 \pm 0.005$ pc |
| Eccentricity | 0.19 | 0.06 | dimensionless | 2 | Eccentricity, $e$                     / $0.19 \pm 0.06$ |
| Orbital period | 1.7e4 | not stated | yr | 2 | Orbital period                        / $1.7\times10^4$ yr |
| T1 LTE gas mass | ~2 | not stated | Msun | 4 | The molecular gas mass of T1 was estimated to be approximately 2 $M_\odot$ |
| Virial mass of whole cloud | ~2e5 | not stated | Msun | 0 | The virial mass for the whole of HCN-0.085-0.094 was estimated at $\sim 2\times10^5$ $M_\odot$ |

## Qualitative findings

- HCN–0.085–0.094 resolves into three clumps T1–T3 with broad velocity widths; T1 has a ring with steep velocity gradient  
  > "HCN–0.085–0.094 is resolved into three major clumps (labeled as T1, T2, and T3), which are clearly traced in all the three lines." (Results)

## Claim tuples

- H: T1 orbits an invisible massive object | E: Keplerian orbit and chi-square mass fit to CS ring kinematics | R: Mdyn ≈ 1.3e4 Msun, Vsys ≈ -26 km/s | F: T1 harbors a possible quiescent IMBH | **supported**
- H: T1 is a protostellar outflow | E: Compared kinetic energy with mid-IR luminosity | R: Mid-IR luminosity ~1e2 Lsun vs expected >1e4 Lsun | F: Outflow scenario not plausible | **refuted**
- H: The clumps are close to Sgr A* | E: Compared with VLA 5.5 GHz continuum | R: Radio blobs at NE edges of T1–T3 | F: Clumps lie within ~10 pc of Sgr A* | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Bipolar outflow from massive protostar rejected; dense cluster of dark remnants cannot be ruled out  
  > "Although the possibility of a cluster of dark stellar remnants cannot be ruled out yet" (Indications)
- How they decided it was enough: _not stated_
- Limitation (authors): A single source of ~1e4 Msun cannot explain T2 and T3 kinematics; diffuse mass distribution possible  
  > "However, there could be diffuse mass distribution around the point-like mass." (Indications)
- Caveat (inferred, ours): Mass from only a partial ring with non-Keplerian northern side; degeneracy with extended mass
- Caveat (inferred, ours): Fit uncertainties likely underestimated; loci selection subjective
- Caveat (inferred, ours): Line-of-sight distance to the clump assumed from radio association only

## Reproducibility

- Data public (paper): ALMA project code given and acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01557.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Cell/image size, clean threshold, masks
- Missing: Line-free channels for uvcontsub
- Missing: Locations of loci used in orbit fit
- Missing: Fitting code
- Data volume (inferred): ~50-200 GB raw (7 m, 12 m, TP mosaics)
- Score (inferred): 3/5, Public data and basic imaging parameters given, but many tclean and fitting details are missing.
- Rediscovery candidate: no, Orbit fitting depends on subjectively chosen loci and unstated imaging details.

## Links

- Method: (cite: takekawa19a) (Keplerian orbital fitting approach and coordinate system)
- Companion: (cite: takekawa19a) (HCN–0.044–0.009 observed in the same ALMA project)
- Companion: (cite: takekawa17b) (earlier study of HCN–0.085–0.094)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "stated": 54,
  "rate": 0.692
 },
 "evidence_ok": true
}
```
