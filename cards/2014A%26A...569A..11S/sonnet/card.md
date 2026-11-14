# A necklace of dense cores in the high-mass star forming region G35.20-0.74 N: ALMA observations

`2014A&A...569A..11S` | Astronomy and Astrophysics 2014 | first author: Sánchez-Monge, Á. | arXiv: 1406.4081 | DOI: 10.1051/0004-6361/201424032

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the fragmentation, kinematics, hot-core chemistry and outflow content of the elongated dense structure in the high-mass star forming region G35.20N, and is it a 1D filament or an edge-on disk-like 'pancake'?  
  > "the main goal of our ALMA observations was to address some fundamental questions such as the fragmentation level of the elongated structure, the kinematics of the dense gas at different scales and the number of outflows and powering sources." (1 Introduction)
- Target **G35.20-0.74 N (G35.20N)**: coordinates 18h58m13.03s, +01d40m36.0s (J2000, phase center)  
  > "The phase center of the observations is $\alpha$(J2000) = 18$^{\rm h}$ 58$^{\rm m}$ 13$s03$, $\delta$(J2000) = 01$\ensuremath{^\circ}$ 40$'$ 36$\ensuremath{''}$0." (ALMA Observations); "G35.20$-$0.74 is a star forming complex located at a distance of $2.19^{+0.24}_{-0.20}$ kpc (cite: zhang2009)." (1 Introduction); z/distance 2.19 (+0.24/-0.20) kpc  
  > "The phase center of the observations is $\alpha$(J2000) = 18$^{\rm h}$ 58$^{\rm m}$ 13$s03$, $\delta$(J2000) = 01$\ensuremath{^\circ}$ 40$'$ 36$\ensuremath{''}$0." (ALMA Observations); "G35.20$-$0.74 is a star forming complex located at a distance of $2.19^{+0.24}_{-0.20}$ kpc (cite: zhang2009)." (1 Introduction); distance from Zhang et al. 2009 (parallax)  
  > "The phase center of the observations is $\alpha$(J2000) = 18$^{\rm h}$ 58$^{\rm m}$ 13$s03$, $\delta$(J2000) = 01$\ensuremath{^\circ}$ 40$'$ 36$\ensuremath{''}$0." (ALMA Observations); "G35.20$-$0.74 is a star forming complex located at a distance of $2.19^{+0.24}_{-0.20}$ kpc (cite: zhang2009)." (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (~350 GHz, 870 um)  
  > "The source was observed in Band 7 ($\sim$350 GHz) with the 16 antennas of the array in the extended configuration" (ALMA Observations)
- frequencies and spectral setup: Four spectral windows of 1875 MHz, 3840 channels each, ~0.4 km/s resolution; 334.97-338.72 GHz and 346.89-350.72 GHz  
  > "The digital correlator was configured in four spectral windows (with dual polarization) of 1875 MHz and 3840 channels each, providing a resolution of $\sim$0.4 km s$^{-1}$." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 16 antennas, ALMA Cycle 0  
  > "G35.20N was observed with ALMA in Cycle 0 between May and June 2012." (ALMA Observations)
- configurations: _not stated_
- baselines: 36-400 m  
  > "baselines in the range 36–400 m, providing sensitivity to structures $\ensuremath{\lesssim}$2$''$." (ALMA Observations)
- angular resolution: continuum beam 0.47"x0.41", PA=46 deg  
  > "The resulting continuum image has a synthesized CLEANed beam of $0.47\ensuremath{''}\times0.41\ensuremath{''}$, PA=46$^\circ$ and a rms noise of 1.8 mJy beam$^{-1}$." (ALMA Observations)
- max recoverable scale: ~2 arcsec  
  > "baselines in the range 36–400 m, providing sensitivity to structures $\ensuremath{\lesssim}$2$''$." (ALMA Observations)
- sensitivity: continuum rms 1.8 mJy/beam; channel rms 5-20 mJy/beam (0.6 km/s channels)  
  > "The rms noise of each spectral channel (of 0.6 km s$^{-1}$) varies between 5 and 20 mJy beam$^{-1}$" (ALMA Observations)
- time on source: _not stated_
- observing dates: May-June 2012  
  > "G35.20N was observed with ALMA in Cycle 0 between May and June 2012." (ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN 19_K-18_K (349453.70 MHz (K=0))
- Line: SiO 8-7 (347330.63 MHz)
- Line: H13CO+ 4-3 (346998.34 MHz)
- Line: C17O 3-2 (337061.05 MHz)
- Other facility **Spitzer/IRAC, MIPSGAL, GLIMPSE, Herschel Hi-GAL, MSX, WISE, ATLASGAL, UKIDSS, VLA 3.6 cm**: IR to mm data for SED, 4.5 um and H2 images, and 3.6 cm continuum for jet comparison  
  > "Figure [10](#f:sed) shows the spectral energy distribution (SED) of G35.20N, obtained from the *Herschel* infrared Galactic Plane Survey" (Spectral energy distribution)
- External data: SMA 880 um continuum, CH3CN and H13CO+ and polarization data used for flux comparison and B-field  
  > "The ALMA 870 $\mu$m dust continuum emission shown in Fig. [1](#f:continuum)a is consistent with the Submillimeter Array (SMA) 880 $\mu$m image obtained by (cite: qiu2013)." (Continuum emission) [from (cite: qiu2013)]
- External data: VLA 3.6 cm continuum map  
  > "free-free 3.6 cm continuum obtained by (cite: gibb2003) with the Very Large Array" (High-velocity SiO outflow emission) [from (cite: gibb2003)]
- External data: Dust opacity 1.75 cm2/g at 870 um  
  > "We have adopted a dust opacity of 1.75 cm$^2$ g$^{-1}$ at 870 $\mu$m (cite: ossenkopfhenning1994), with a gas-to-dust ratio of 100." (Temperature and mass estimates) [from (cite: ossenkopfhenning1994)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (flux, gain, bandpass with J1751+096)  
  > "Flux, gain, and bandpass calibrations were obtained through observations of Neptune and J1751$+$096." (ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA  
  > "The data were calibrated and imaged using CASA[^2] (cite: mcmullin2007)." (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "Continuum and channel maps were created with the robust parameter of (cite: briggs1995) set equal to 0.5" (ALMA Observations)
- uv taper: 1 arcsec taper for C17O, C34S, H13CO+, SiO  
  > "we generated new CLEANed maps for these four species after tapering the data at 1$''$ resolution." (Large-scale molecular emission)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels, subtracted in uv-domain  
  > "A continuum map was obtained from line-free channels and subtracted from the data, directly in the *(u,v)*-domain." (ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectra smoothed to 0.6 km/s  
  > "All the resulting spectra have been smoothed to a resolution of 0.6 km s$^{-1}$." (ALMA Observations)
- final beam: _not stated_
- final rms: 1.8 mJy/beam continuum  
  > "a rms noise of 1.8 mJy beam$^{-1}$" (ALMA Observations)

### Inherited from earlier work

- Moment map procedure  
  > "The moment maps have been computed following the same procedure as in (cite: sanchezmonge2013b)" (Compact molecular emission: hot cores) [from (cite: sanchezmonge2013b)]
- Outflow momentum rate computation from SiO  
  > "We followed the same procedure described in (cite: lopezsepulcre2009)" (High-velocity SiO outflow emission) [from (cite: lopezsepulcre2009)]
- Gaussian deconvolution of core sizes  
  > "see procedure described in Table 3 of (cite: sanchezmonge2013a)" (Continuum emission) [from (cite: sanchezmonge2013a)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration (pipeline vs manual) details
- line-free channel selection for continuum
- clean threshold, mask, cell and image size, deconvolver
- myXCLASS fit initial guesses, parameter bounds, and fitting algorithm settings
- exact SiO outflow momentum computation inputs
- line used for tapered maps' beam

## Analysis recipe

1. **Image continuum and lines**: CASA imaging with robust 0.5; continuum from line-free channels subtracted in uv; tapered maps at 1" for extended tracers  
  > "Continuum and channel maps were created with the robust parameter of (cite: briggs1995) set equal to 0.5" (ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Missing flux estimated vs SCUBA (~30%), SMA and ASTE (~75% for CH3CN)  
  > "The ALMA observations recover around 75% of the flux measured with ASTE." (Compact molecular emission: hot cores)
2. **Identify cores and measure fluxes/sizes**: 2D CLUMPFIND identifies six cores; flux within 5 sigma; deconvolved diameter at 50% contour  
  > "The 2D CLUMPFIND algorithm (cite: williams1994) identifies six of these, which we name cores A–F" (Continuum emission)
   - software: CLUMPFIND
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit CH3CN and CH3OH spectra for temperature and column density**: Single-component LTE fit with myXCLASS/MAGIX minimizing chi2; five free parameters (size, T, N, linewidth, vLSR)  
  > "The procedure searches, by minimizing the $\chi^2$, for the best fit of five parameters: size (in arcsec), temperature (in K), column density (in cm$^{-2}$), linewidth (in km s$^{-1}$) and LSR velocity (in km s$^{-1}$)." (CH3OH and CH3CN myXCLASS fits)
   - software: myXCLASS, MAGIX
   - assumption: 12C/13C = 50  
  > "We assumed the relative abundance \[$^{12}$C/$^{13}$C\] to be 50 for a galactocentric distance of 6.5 kpc" (Temperature and mass estimates)
   - fitting: chi2 minimization with MAGIX  
  > "Once an initial guess is set up, the parameters can be fitted using the program MAGIX" (Temperature and mass estimates)
   - validation: chi2 plots; simultaneous fit of optically thick and thin lines to avoid degeneracies  
  > "thus avoiding possible degeneracies (cite: zernickel2012) between the parameters of the fit" (CH3OH and CH3CN myXCLASS fits)
4. **Derive core masses, densities, abundances**: Optically thin dust mass formula with T=Tex (lower limit 30 K); N, n from spherical homogeneous cores; 30-50 K for cores E, F  
  > "We assume $T=T_\mathrm{ex}$, where $T_\mathrm{ex}$ is obtained from the myXCLASS analysis." (Temperature and mass estimates)
   - assumption: kappa=1.75 cm2/g at 870 um, gas-to-dust 100, mu=2.3, D=2.19 kpc  
  > "We have adopted a dust opacity of 1.75 cm$^2$ g$^{-1}$ at 870 $\mu$m (cite: ossenkopfhenning1994), with a gas-to-dust ratio of 100." (Temperature and mass estimates)
   - fitting: _not stated_
   - validation: Compared with Kauffmann & Pillai mass-size relation  
  > "We also compared the mass and size of the six cores identified in G35.20N with the empirical relation for a dense core to form a massive star" (Temperature and mass estimates)
5. **Virial masses**: M_vir=105 D_S dv^2 using hot-core and H13CO+ linewidths  
  > "$M_\mathrm{vir}=105\,[D_{\rm S}/\mathrm{pc}][\Delta {\rm v}/\mathrm{km~s}^{-1}]^2$ $M_{\ensuremath{\odot}}$" (Dynamical status of the cores)
   - assumption: uniform density  
  > "the numerical value accounts for a uniform density distribution across the core" (Dynamical status of the cores)
   - fitting: _not stated_
   - validation: _not stated_
6. **Velocity fields and Keplerian disk masses**: Moment maps and position-velocity cuts (PA 157 deg core B, 10 deg core A) compared to Keplerian pattern; core A mass from v=1.5 km/s at 0.7"  
  > "Assuming that one is indeed observing a Keplerian disk with a rotation velocity of 1.5 km s$^{-1}$ at a radius of 0.7$''$ (or 1500 AU), we derive a mass of $\sim$4 $M_{\ensuremath{\odot}}$" (Core A)
   - software: GILDAS
   - fitting: core B Keplerian model from Sanchez-Monge 2013b  
  > "The positions of the Gaussian peaks, which provide a picture of the velocity field (see Fig. 4 of (cite: sanchezmonge2013b)), were fitted with a simple Keplerian disk model." (Core B)
   - validation: _not stated_
7. **Test filament vs pancake**: Toomre Q and cylinder fragmentation spacing/critical mass per length  
  > "In practice, one sees that a value of $\Delta V=0.7$ km s$^{-1}$ is required for the theoretical expression to match the observed spacing between the cores" (Nature of the elongated structure)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "The data were calibrated and imaged using CASA" (ALMA Observations)
- **GILDAS (CLASS, GREG)** : analysis of spectral line images  
  > "The spectral line images were analyzed using the CLASS and GREG programs of the GILDAS" (ALMA Observations)
- **CLUMPFIND** : core identification  
  > "The 2D CLUMPFIND algorithm (cite: williams1994) identifies six of these" (Continuum emission)
- **myXCLASS** : LTE spectral fitting of CH3CN and CH3OH  
  > "We fitted the observed methyl cyanide and methanol spectra for all the cores using the CASA interface of the XCLASS software called myXCLASS" (Temperature and mass estimates)
- **MAGIX** : parameter fitting  
  > "the parameters can be fitted using the program MAGIX" (Temperature and mass estimates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum beam | 0.47x0.41, PA 46 | not stated | arcsec, deg | 1 | synthesized CLEANed beam of $0.47\ensuremath{''}\times0.41\ensuremath{''}$, PA=46$^\circ$ |
| Core A flux density | 0.692 | 0.023 | Jy | 2 | A    / 18 58 12.945           / 01 40 37.36                                              / 0.208                          / $0.692\pm0.023$ |
| Core B flux density | 0.333 | 0.008 | Jy | 2 | $0.333\pm0.008$ |
| Mean core spacing | 0.023 | not stated | pc | 2 | mean (projected) separation of $\sim$$2.1\ensuremath{''}$ or $\sim$0.023 pc |
| Core masses | 1-10 | not stated | Msun | 4 | The masses of the cores in G35.20N are in the range 1–10 $M_{\ensuremath{\odot}}$. |
| CH3CN rotation temperature core A | 309 | not stated | K | 3 | A    / 31.8          / 5.2           / 0.24     / 309 |
| Bolometric luminosity | ~3e4 | not stated | Lsun | 0 | We obtain $\sim$$3\times10^{4}$ $L_{\ensuremath{\odot}}$ |
| Central mass core A (Keplerian) | ~4 | not stated | Msun | 6 | we derive a mass of $\sim$4 $M_{\ensuremath{\odot}}$ for the putative central star |
| Critical line mass vs measured | ~40 critical vs ~200 measured | not stated | Msun/pc | 7 | this line width of 0.7 km s$^{-1}$ results in a critical mass per unit length of $\sim$40 $M_{\ensuremath{\odot}}$ pc$^{-1}$, while the measured mass per unit length in our filament is $\sim$200 $M_{\ensuremath{\odot}}$ pc$^{-1}$ |
| Flux recovered vs ASTE (CH3CN) | ~75% | not stated | percent | 1 | The ALMA observations recover around 75% of the flux measured with ASTE. |

## Qualitative findings

- Cores A, B, C are hot cores; cores D-F are weak in complex molecules.  
  > "The rest of the cores are only associated with faint emission of more abundant species such as C$^{17}$O, C$^{34}$S, H$^{13}$CO$^+$" (Line emission)
- Core B jet is consistent with precession; core A may drive an outflow seen in SiO and 3.6 cm.  
  > "This behavior is strongly suggestive of precession about an axis significantly inclined with respect to the N–S direction." (Precessing jet)

## Claim tuples

- H: Is the elongated dust structure fragmented into regularly spaced cores? | E: ALMA 870 um continuum with CLUMPFIND | R: Six cores with ~0.023 pc spacing, masses 1-10 Msun | F: The structure fragments into regularly spaced low-mass dense cores | **supported**
- H: Do cores A and B host Keplerian disks? | E: Moment maps and PV diagrams of hot core tracers | R: Coherent velocity gradients, butterfly PV pattern in B; weaker in A | F: Consistent with Keplerian disks around 4 (A) and 18 (B) Msun, A less certain | **partially**
- H: Is the elongated structure a 1D filament or an edge-on pancake? | E: Velocity field, Toomre/fragmentation analysis, magnetic field orientation | R: Both unstable; regular spacing and B-field parallel to structure | F: Favours a fragmenting 1D filament | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Rotating edge-on 'pancake' disfavoured: counter-rotation of core B, inconsistent core velocities, regular spacing, B-field direction.  
  > "Another problem with the “pancake” scenario is that core B would be counter-rotating with respect to the large-scale velocity field." (Nature of the elongated structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Extended emission resolved out; H13CO+ linewidths are lower limits; missing flux affects abundances.  
  > "We note, however, that extended structures are heavily resolved out in our observations." (Dynamical status of the cores)
- Caveat (inferred, ours): Masses depend on assumed Tdust=Tex and a 30 K floor
- Caveat (inferred, ours): Single-component LTE fits ignore gradients
- Caveat (inferred, ours): Missing flux up to 50-70% affects abundances and filament mass
- Caveat (inferred, ours): Filament vs pancake argument is qualitative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code not printed in paper
- Missing: CASA version and imaging parameters
- Missing: myXCLASS fit set-up details
- Missing: Keplerian model details are in Sánchez-Monge 2013b
- Data volume (inferred): ~50-100 GB raw (Cycle 0, four 1.9 GHz spectral windows)
- Score (inferred): 4/5, Data are archival-public and the recipe is described but with limited imaging detail.
- Rediscovery candidate: no, Imaging parameters are incomplete and several results rely on inherited procedures.

## Links

- Method: (cite: zernickel2012) (myXCLASS fitting)
- Companion: (cite: sanchezmonge2013b) (first ALMA results on G35.20N, Keplerian disk in core B)
- Related: Beltrán et al. G35.03+0.35 ALMA Cycle 0

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00275.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 50,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
