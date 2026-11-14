# ALMA Observations of Quasar Host Galaxies at z ≃ 4.8

`2020ApJ...895...74N` | The Astrophysical Journal 2020 | first author: Nguyen, Nathen H. | arXiv: 2003.00525 | DOI: 10.3847/1538-4357/ab8bd3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the host galaxy properties (dust, dynamical and gas masses, SFR, companions, [C II]-Mg II offsets) of luminous z~4.8 quasars, split into Herschel-detected (FIR-bright) and undetected (FIR-faint)?  
  > "we continue to probe the connection between SMBHs and their host galaxies using an optically selected, flux-limited sample of the most luminous quasars at $z \sim
4.8$." (1 Introduction)
- Target **12 new SDSS quasars at z~4.8 (6 FIR-bright, 6 FIR-faint), e.g. SDSS J080715.11+132805.1, J144734.09+102513.1, J205724.14-003018.7**: coordinates given in target names (SDSS JHHMMSS.ss+DDMMSS.s), Table 1  
  > "which provides an angular scale of about $6.47\,{\rm kpc} /\hbox{$^{\prime\prime}$}$ at $z=4.8$, the typical redshift of our sources." (1 Introduction); z/distance z ~ 4.66-4.95 ([C II] redshifts, Table of redshifts)  
  > "which provides an angular scale of about $6.47\,{\rm kpc} /\hbox{$^{\prime\prime}$}$ at $z=4.8$, the typical redshift of our sources." (1 Introduction); distance from [C II] redshifts; Mg II redshifts from T11  
  > "which provides an angular scale of about $6.47\,{\rm kpc} /\hbox{$^{\prime\prime}$}$ at $z=4.8$, the typical redshift of our sources." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.01515.S
- bands: Band 7  
  > "The twelve new targets were observed using ALMA band-7 during the Cycle-4 period of 2016 November 9 to 2017 May 6." (2.2 ALMA Observations)
- frequencies and spectral setup: TDM, 4 spectral windows of 1875 MHz, 128 channels of 15.625 MHz (~15 km/s); two windows centered on expected [CII], other two ~12 GHz higher; central frequency 317-349 GHz  
  > "We chose the TDM correlator mode which provides four spectral windows, each covering an effective bandwidth of 1875 MHz, which corresponds to $\sim1650\,{\rm km\,s}^{-1}$ at the observed frequencies." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5  
  > "The observations were done with the C40-5 configuration" (2.2 ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.19-0.33 arcsec (~2 kpc)  
  > "with an observed angular resolution variation of 0.19-0.33$^{\prime\prime}$" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 2.8e-2 to 6.2e-2 mJy/beam  
  > "SDSS J101759.63$+$032739.9 | 41 | 2064 | 2.8 $\times 10^{-2}$" (Table 1)
- time on source: 1001-2276 s per target  
  > "the exposure time ranged from 1001 - 2276 seconds" (2.2 ALMA Observations)
- observing dates: 2016 Nov 9 to 2017 May 6 (Cycle 4)  
  > "Cycle-4 period of 2016 November 9 to 2017 May 6" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2-2P1/2 (157.74 micron)
- Other facility **Herschel/SPIRE**: 250/350/500 micron photometry used to define FIR-bright/faint and for SED fits (values from N14)  
  > "For the FIR-bright objects, we will also use the *Herschel* measurements." (3.1.2 SEDs and SFRs)
- Other facility **Gaia DR2 / Pan-STARRS1**: optical centers for optical-ALMA separation  
  > "we obtain the optical centers of our objects." (2.5 Optical Center Separation)
- External data: Mg II-based redshifts, black hole masses and bolometric luminosities  
  > "Black Hole masses were taken from T11 and are based on Mg II measurements." (3.1.1) [from Trakhtenbrot et al. 2011 (T11)]
- External data: Herschel photometry values and errors  
  > "values and errors from N14, with the 250 $\mu$m flux error corrected as explained above" (3.1.2 SEDs and SFRs) [from Netzer et al. 2014 (N14)]
- External data: Six quasars from pilot sample, ALMA measurements  
  > "Previously, in T17, we observed three FIR-bright, and three FIR-faint quasar from our sample using ALMA." (2.2 ALMA Observations) [from (cite: Trakhtenbrot2017)]
- External data: SDSS redshifts  
  > "we also list the SDSS-based redshift determinations published in (cite: Hewett_2010)" (3.1.1) [from (cite: Hewett_2010)]
- External data: Literature [CII]-Mg II offsets for z>~6 quasars compilation  
  > "eight quasars taken from (cite: Decarli2018)" (3.1.1) [from Decarli2018, Willott 2013/2015/2017, Venemans 2012/2016/2017, Mazzucchelli2017, Banados2015, Wang2016]
- Simulation/model as data: SED templates: Chary & Elbaz 2001 grid, Magnelli 2012 SMG SED; main sequence of Schreiber 2015 and Tomczak 2016  
  > "For the first method we use the grid of FIR SEDs provided by (cite: CharyElbaz2001)." (3.1.2 SEDs and SFRs)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% ALMA band-7 absolute flux calibration, added in quadrature  
  > "ALMA absolute flux calibration in band-7 is claimed to be of the order of 10%." (3.1.2 SEDs and SFRs)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "`CLEAN` algorithms were ran with "briggs" weighting and a robustness parameter of 0.5" (2.3 Data Reduction)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0.5  
  > "`CLEAN` algorithms were ran with "briggs" weighting and a robustness parameter of 0.5 in order to create continuum and emission line images." (2.3 Data Reduction)
- uv taper: _not stated_
- cell size: 0.06 arcsec  
  > "SDSS J080715.11$+$132805.1 | 43 | 2054 | 5.1 $\times 10^{-2}$ | 0.37 $\times$ 0.21 | 0.06" (Table 1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB on [CII] window pair; continuum from line-free window pair  
  > "Continuum emission images were constructed using the line-free spectral window pair, while the `UVCONTSUB` command was used to subtract continuum emission from the \[C ii\] window pair" (2.3 Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Same spectral/spatial setup and measurement approach (spatial method for line flux) as pilot  
  > "For consistency we aimed to have the same spectral and spatial resolutions as T17." (2.2 ALMA Observations) [from T17 (cite: Trakhtenbrot2017)]
- Dynamical mass method (inclined rotating disk)  
  > "We use the same method as in T17 and several other studies of \[C ii\] and CO emission in high-redshift sources" (4.1 Dynamical Masses) [from T17; Wang2013; Willot2015; Venemans2016]
- Gray-body Td=47 K, beta=1.6; 50 Myr growth time  
  > "Following T17 and other works, we use a temperature of $T_d = 47$ K and dust emissivity coefficient $\beta = 1.6$." (3.1.2 SEDs and SFRs) [from T17]
- AGN contribution to 250 micron error (0.32 times AGN luminosity at 1450A)  
  > "as explained in N14, we add in quadrature an uncertainty estimated as 0.32 times the AGN luminosity at 1450Å" (3.1.2 SEDs and SFRs) [from N14]

### Not stated but needed to reproduce (our reading)

- Flux/bandpass/phase calibrator names and pipeline vs manual calibration
- Cleaning threshold, masks, and image size
- Channel width of final cubes and line-free channels used for UVCONTSUB
- Aperture sizes for J1447/J1151 photometry
- Inclination derivation details from axis ratio
- Mg II-based redshifts and L_AGN values needed from T11
- How SED chi2 fits and uncertainties were computed
- Moment-map clipping thresholds

## Analysis recipe

1. **Image continuum and [CII] cubes**: CLEAN with Briggs weighting; continuum from line-free spw pair; UVCONTSUB on [CII] pair  
  > "Continuum emission images were constructed using the line-free spectral window pair, while the `UVCONTSUB` command was used to subtract continuum emission" (2.3 Data Reduction)
   - software: CASA
   - parameter: robust = 0.5  
  > "a robustness parameter of 0.5" (2.3 Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum and [CII] fluxes and sizes**: 2D Gaussian fits to continuum and zero-moment images (spatial); 1D spectral Gaussian fits as check; aperture photometry for J1447  
  > "Sizes of the continuum emitting regions were determined from the respective images by fitting spatial 2D Gaussians to the sources" (2.3 Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: spatial and spectral methods agree with median difference of 0.05 dex  
  > "with a median difference of 0.05 dex" (2.3 Data Reduction)
3. **Compare [CII] and Mg II redshifts**: Velocity offsets between [CII] and Mg II (and SDSS) redshifts; compile with literature quasars  
  > "we compare the redshifts obtained from the \[C ii\] and Mg II lines" (3.1.1)
   - assumption: [CII] traces systemic redshift  
  > "it is a good measure of the systemic redshift of the quasar host galaxy" (3.1.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **FIR SED fits and SFR**: Fit Chary&Elbaz, Magnelli SMG, and gray-body SEDs to ALMA (+Herschel) photometry; integrate 8-1000 micron; SFR = L_FIR/1e10  
  > "the SFR is obtained using $\rm SFR / \Msun\,{\rm yr}^{-1} =
L_{\rm FIR}\ / 10^{10} L_{\odot}$" (3.1.2 SEDs and SFRs)
   - parameter: gray-body T = 40,45,50,55,60,70 K; beta = 1.5,1.7 (plus 47 K, 1.6)  
  > "we also try gray-body SEDs with a wider range of temperatures (40, 45, 50, 55, 60 and 70 K) and $\beta$ values (1.5 and 1.7)" (3.1.2 SEDs and SFRs)
   - assumption: FIR emission dominated by SF-heated dust; Chabrier IMF  
  > "we assume that the FIR emission of the sources in our sample is dominated by dust heated by SF activity" (3.1.2 SEDs and SFRs)
   - fitting: chi2 best fit on grid; mean chi2 ~2 for FIR-bright  
  > "The mean $\chi^2$ for our nine FIR-bright quasars is $\sim 2$ (for one degree of freedom)." (3.1.2 SEDs and SFRs)
   - validation: _not stated_
5. **Dust masses**: Optically thin dust: Md = S D_L^2 / (kappa B(T))  
  > "$\kappa_{d}(\lambda_{rest})=
0.077\ (850 / \lambda_{rest})^{\beta}$ m$^{2}$ kg$^{-1}$" (3.1.4 Dust masses)
   - assumption: Td = 47 K, beta = 1.6, kappa(850um)=0.077 m2/kg  
  > "To calculate the dust mass we assume $T_d = 47\,$ K and $\beta = 1.6$." (3.1.4 Dust masses)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dynamical and gas masses**: Mdyn = 9.8e8 D FWHM^2/sin^2 i; dispersion-dominated alternative; Mgas = 100 x Mdust  
  > "We can determine gas masses, $M_{gas}$, making use of a gas-to-dust ratio (GDR) of 100" (4.2 Gas Masses)
   - assumption: inclined rotating disk; GDR = 100  
  > "which assumes the \[C ii\]-traced ISM is arranged in an inclined, rotating disk" (4.1 Dynamical Masses)
   - fitting: _not stated_
   - validation: mean error 0.44 dex by propagation  
  > "We estimate a mean error of 0.44 dex by propagating systematic uncertainties" (4.1 Dynamical Masses)
7. **Main sequence and BH-host comparison**: Adopt Mstar = 0.4 Mdyn (fgas=0.6); compare SFR-Mstar with Schreiber2015/Tomczak2016 MS; compute MBH/Mstar and growth rates over 50 Myr with eta=0.1  
  > "We can then conservatively assume that for our systems $f_{gas} = M_{gas}/M_{dyn} = 0.6$ and therefore $M_{\star} = 0.4\ M_{\rm dyn}$." (4.3 The Main Sequence at z~5)
   - assumption: radiative efficiency 0.1  
  > "We assume the radiative efficiency to be $\eta
= 0.1$." (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: data reduction, imaging, Gaussian fitting, moments  
  > "Data reduction was performed using the CASA package version 4.7.2" (2.3 Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean Mg II blueshift relative to [CII] (17 hosts) | 464 | std 657 | km/s | 3 | The average value for $\Delta v_{{\rm Mg}\,\textsc{ii} }$ is 464 km s$^{-1}$, with a standard deviation of 657 km s$^{-1}$ |
| Median Mg II offset | 379 | not stated | km/s | 3 | while the median is found to be at 379 km s$^{-1}$ |
| Mean offset in compilation incl. literature | 372 | std 582 | km/s | 3 | we found a mean $z_{\left[{\rm C}\,\textsc{ii}\right] }
- z_{{\rm Mg}\,\textsc{ii} }$ of 372 km s$^{-1}$ |
| Dust mass range (16 detected) | 2-15e8 | not stated | Msun | 5 | find a range of $M_{dust} \sim 2-15\times 10^8 M_{\odot}$ |
| Mean dust mass FIR-bright / FIR-faint | 10^9.0 / 10^8.4 | not stated | Msun | 5 | with dust masses of $10^{9.0}$ and $10^{8.4}
M_{\odot}$, respectively |
| Mean dynamical mass | 9e10 | 0.44 dex mean error | Msun | 6 | The mean is $9 \times 10^{10}$ $M_{\odot}$. |
| Companion fraction | 5/18 (28%) | not stated | dimensionless | 0 | our total observed sample of 18 quasars has 5 sources with companions |
| Mean MBH/Mstar | 1/19 | not stated | dimensionless | 7 | We find a mean $M_{BH}/M_{\star}$ ratio of 1/19 |
| Optical-ALMA separation range | 0.005-0.062 | median error ~11 mas | arcsec | 2 | OS values have a range of 0.005” - 0.062” for our entire sample. |

## Qualitative findings

- Companions are found preferentially around FIR-faint quasars; FIR-bright all lie >=1 dex above the main sequence  
  > "Clearly, all of our FIR-bright quasars are found in the starbursting domain and at least 1 dex from the MS." (4.3 The Main Sequence at z~5)

## Claim tuples

- H: Is the Mg II BLR line offset from the host systemic redshift traced by [CII]? | E: Compare [CII] and Mg II redshifts for 17 hosts plus literature compilation | R: Mean offset 464 km/s (median 379); compilation mean 372 km/s | F: Mg II is blueshifted by several hundred km/s relative to host | **supported**
- H: Do FIR-bright quasars show more companions (mergers) than FIR-faint ones? | E: Search for [CII]/continuum companions in ALMA maps | R: 5/18 with companions: 1 FIR-bright, 4 FIR-faint | F: Companions preferentially around FIR-faint; possibly earlier merger stage | **partially**
- H: Do the hosts lie on the z~5 main sequence? | E: Compare SFR vs Mstar (0.4 Mdyn) with MS curves | R: Majority above MS | F: Hosts are starbursting relative to main sequence | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: [CII] and FIR continuum chosen because AGN dominates optical-NIR  
  > "The best strategy is to observe these systems in the far-IR (FIR), where dust heated by the starformation dominates the continuum emission" (1 Introduction)
- Alternative: Velocity-field modeling/beam-smearing correction not done since sources only partially resolved  
  > "our targets are only partially resolved and modeling the rotation is not possible" (2.4 [C II] Line Properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas and dynamical masses highly uncertain  
  > "the determination of gas and dynamical masses for our quasar hosts are highly uncertain" (3 Results and Discussion)
- Caveat (inferred, ours): Mstar assumed from fixed fgas=0.6, so main-sequence offsets depend on assumption
- Caveat (inferred, ours): Gray-body SED fits with 1 d.o.f. and fixed T, beta
- Caveat (inferred, ours): Small sample, no statistical tests of FIR-bright vs faint difference
- Caveat (inferred, ours): Noisy data with atmosphere-affected windows

## Reproducibility

- Data public (paper): ALMA data cited with project code in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01515.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration details and calibrators
- Missing: Clean thresholds/masks
- Missing: Inclination derivation
- Missing: T11 and N14 input values
- Data volume (inferred): ~50-100 GB raw for 12 Band 7 targets
- Score (inferred): 3/5, Data are public and the main steps are simple formulas, but imaging details and external inputs are missing.
- Rediscovery candidate: yes, Public data, numeric results from simple flux/line fits and standard formulae.

## Links

- Method: (cite: Trakhtenbrot2017) (Pilot sample and analysis methods)
- Method: (cite: Dunne2000) (Dust mass opacity method)
- Companion: (cite: Netzer2014) (Herschel observations of the sample)
- Companion: (cite: Trakhtenbrot2011) (Mg II redshifts and BH masses)
- Related: Herschel/SPIRE campaign of z~4.8 quasars
- Related: Decarli et al. 2018 [CII] quasar survey

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 51,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
