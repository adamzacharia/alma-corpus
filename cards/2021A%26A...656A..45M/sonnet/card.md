# AGN feeding and feedback in Fornax A. Kinematical analysis of the multi-phase ISM

`2021A&A...656A..45M` | Astronomy and Astrophysics 2021 | first author: Maccagni, F. M. | arXiv: 2108.05247 | DOI: 10.1051/0004-6361/202141143

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How do the multi-phase gas kinematics in Fornax A reveal concurrent AGN feeding (Chaotic Cold Accretion) and feedback (outflows)?  
  > "We aim to understand if and how the cold and ionised gas have triggered the nuclear activities in the last $3$ Myr, and what are the feedback effects resulting from these." (Introduction)
- Target **NGC 1316 (Fornax A)**: coordinates _not stated_; z/distance 20.8 Mpc  
  > "at the assumed distance of 20.8 Mpc" (2.1 Neutral atomic hydrogen observations); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00129.S
- bands: _not stated_
- frequencies and spectral setup: 112.8 - 114.7 GHz bandwidth; 3.8 kHz (~9.9 km/s) spectral resolution; text also says '108 GHz observation'  
  > "| ALMA | 5.7 hrs | 112.8 - 114.7 GHz | $22$$''$$\times18$$''$ | 3.8 kHz ($\sim 9.9$ $\,$km s$^{-1}$) |  |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: original PSF 15.5'' x 7''; re-made at 22'' x 18''  
  > "The PSF of the resulting datacube is very asymmetric ($15.5$$''$$\times7$$''$)" (2.2 Molecular gas observations)
- max recoverable scale: _not stated_
- sensitivity: 12 mJy/beam per channel (9.9 km/s); 3 sigma surface brightness limit 0.33 Msun/pc2  
  > "The noise in the datacube is $12$ mJy beam$^{-1}$ per channel ($\Delta v\sim9.9$$\,$km s$^{-1}$)." (2.2 Molecular gas observations)
- time on source: 5.7 hrs  
  > "| ALMA | 5.7 hrs | 112.8 - 114.7 GHz |" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO (1-0) (not stated)
- Other facility **MeerKAT**: H I 21-cm cube, 22''x18''  
  > "We observed Fornax A with MeerKAT (cite: Jonas:2016; Camilo:2018) in two different commissioning observations in June 2018." (2.1 Neutral atomic hydrogen observations)
- Other facility **MUSE (VLT)**: ionised gas emission lines, archival wide-field and centre-field cubes  
  > "we select two different sets of MUSE observations available on the ESO archive" (2.3 Ionised gas observations)
- External data: X-ray halo temperature <Tx> = 0.77 keV between 1 and 8 kpc  
  > "temperature of the X-ray halo measured by (cite: Nagino:2009) between 1 and 8 kpc, $\langle T_{\rm x} \rangle = 0.77$ keV" (7.1 Feeding) [from (cite: Nagino:2009)]
- External data: Baryonic Tully-Fisher flat velocity 340 km/s  
  > "$v_{\rm rotational}=v_{\rm flat}=340$$\,$km s$^{-1}$ (cite: Iodice:2017)" (6 Analysis of the kinematics) [from (cite: Iodice:2017)]
- Simulation/model as data: CCA simulation k-plot expectations (line width and shift ellipses) compared to data  
  > "expected from CCA simulations, if the cold and ionised gas were undergoing condensation and inducing rainfalls (cite: Gaspari:2018)" (7.1 Feeding)

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
- final beam: 22'' x 18'' (matched to H I)  
  > "we generate a new CO (1–0)  datacube at the same spatial resolution of the H I." (2.2 Molecular gas observations)
- final rms: 12 mJy/beam per channel  
  > "The noise in the datacube is $12$ mJy beam$^{-1}$ per channel" (2.2 Molecular gas observations)

### Inherited from earlier work

- ALMA data reduction  
  > "A complete description of the reduction of the ALMA 108 GHz observation can be found in (cite: Morokuma:2019)." (2.2 Molecular gas observations) [from (cite: Morokuma:2019)]
- MeerKAT H I reduction  
  > "A complete description of the data reduction of the 21-cm observations can be found in (cite: Kleiner:2021)." (2.1 Neutral atomic hydrogen observations) [from (cite: Kleiner:2021)]
- k-plot method  
  > "Following (cite: Gaspari:2018), Fig. [8](#fig:kplot) (the kinematical-plot, ‘k-plot’)" (6.2) [from (cite: Gaspari:2018)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, robust, tclean settings, continuum subtraction)
- SoFiA parameters used for the CO cube
- How the CO cube was regridded/smoothed to 22''x18''
- Mapping of the ALMA moment maps to region masses (R1-R6 selection thresholds)
- CO-to-H2 line ratio and temperature assumptions

## Analysis recipe

1. **make CO cube and moment maps at H I resolution**: New CO(1-0) cube at same resolution as H I; SoFiA used for moment maps  
  > "We create the total CO (1–0)  image, velocity field and velocity-dispersion field using `SoFiA`, analogously to what done for the H I." (2.2 Molecular gas observations)
   - software: SoFiA
   - assumption: Galactic X_CO = 4.3 Msun (K km/s pc^2)^-1  
  > "assuming a Galactic CO (1–0) -to-H$_{\,2}$ conversion factor $X_2=4.3$${\rm M}_\odot$(K $\,$km s$^{-1}$ pc$^{-2}$)$^{-1}$" (2.2 Molecular gas observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **classify cold gas kinematics with rotation model and k-plot**: Schematic rotating disk plus expanding ring model; spectra matching model for at least 50% of the zero-intensity width are 'rotating'; remaining points clustered in k-plot (width vs centroid) into R1-R6  
  > "We define as ‘rotating’, every spectrum of the \[N II\]$\lambda$6583 datacube whose fitted emission line matches the model line for at least $50\%$ of its full-width at zero intensity." (6.2)
   - parameter: inner disk i=89 deg, PA=-30 deg, v_rot=340 km/s; ring v_exp=2000 km/s; dispersion 35 km/s  
  > "The expansion velocity $v_{\rm exp} = 2000$$\,$km s$^{-1}$ of the outer ring follows from its low inclination" (6.1 Modelling the kinematics of the ISM)
   - fitting: not an automated fit  
  > "we do not constrain all the parameters of the model with an automated fit." (6.1 Modelling the kinematics of the ISM)
   - validation: _not stated_
3. **derive masses, Taylor number, C-ratio, outflow properties**: Masses per region (H2 from CO), Ta_t=v_rot/sigma_3D, C=t_cool/t_eddy, outflow mass and power from R1, R5, R6  
  > "we use the masses of the H I, CO and ionised gas in regions $R1$, $R5$ and $R6$ (see Table [1](#tab:masses)) to determine the total mass of the outflow $M_{\rm out}\sim 2\times10^7$ ${\rm M}_\odot$." (7.2 Feedback)
   - assumption: outflow ejected at same time as jets (3 Myr), v_OUT=2000 km/s  
  > "Assuming that the outflow was ejected at the same time of the jets, the mass outflow rate is $\dot{M}_{\rm OUT}\sim 5$ ${\rm M}_\odot$ yr$^{-1}$." (7.2 Feedback)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SoFiA** : CO and H I moment maps  
  > "We create the total CO (1–0)  image, velocity field and velocity-dispersion field using `SoFiA`" (2.2 Molecular gas observations)
- **CARACal** : MeerKAT H I data reduction  
  > "The data reduction was made with `CARACal`[^1] (cite: Jozsa:2020)." (2.1 Neutral atomic hydrogen observations)
- **GISTpipeline** : MUSE Voronoi binning and stellar continuum fit  
  > "This step is performed using the `GISTpipeline`[^4] (cite: Bittner:2019)." (2.3 Ionised gas observations)
- **lmfit** : Gaussian line fitting of MUSE lines  
  > "The fits are performed using the Python library `lmfit` (cite: Newville:2014)." (2.4 Estimate of the line emission parameters)
- **GuFo** : fitting routine and outputs for MUSE  
  > "make use of the `GuFo`[^5] suite we developed." (2.4 Estimate of the line emission parameters)
- **Montage** : mosaicking MUSE cubes  
  > "We mosaic together the four stellar-subtracted datacubes using `Montage`." (2.3 Ionised gas observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total H2 mass from CO(1-0) | 5.8e8 | not stated | Msun | 3 | we measure a total H$_{\,2}$ $=5.8\times 10^{8}$ ${\rm M}_\odot$ |
| Total H I mass | 6.7e7 | not stated | Msun | 3 | / Total / $6.7\times10^7$ / $5.8\times10^8$ / $1.6\times10^6$ / |
| Integrated H2/H I ratio | ~5.5 | not stated | dimensionless | 3 | The integrated H$_{\,2}$/H I ratio is $\sim 5.5$ |
| Outflow mass | ~2e7 | not stated | Msun | 3 | $M_{\rm out}\sim 2\times10^7$ ${\rm M}_\odot$ |
| Mass outflow rate | ~5 | not stated | Msun/yr | 3 | $\dot{M}_{\rm OUT}\sim 5$ ${\rm M}_\odot$ yr$^{-1}$ |
| Outflow power | ~6e42 | not stated | erg/s | 3 | estimate $P_{\rm OUT}\sim 6\times 10^{42}$ erg s$^{-1}$ |
| EW-stripe H2 mass | 9.6e6 | not stated | Msun | 3 | $9.6\times10^6$ ${\rm M}_\odot$ for the H$_{\,2}$ derived from the CO observations |

## Qualitative findings

- Cold gas (H I and CO) follows the dust and shows high dispersion in the wake of the jets and in the outer ring  
  > "In both phases of the gas, the highest dispersion is found where the radio jets bend in the NW and, more evidently in the SE." (3)

## Claim tuples

- H: Is the outer ring an outflow rather than rotation? | E: Compare MUSE, H I and CO velocity fields with rotation/expansion models | R: Ring terminal velocities along short axis, ~2000 km/s expansion if radial | F: Outer ring is a multi-phase outflow of ~2e7 Msun | **supported**
- H: Is gas in the EW-stripe undergoing CCA? | E: k-plot, Taylor number and C-ratio | R: EW-stripe consistent with CCA expectations, C-ratio approaching unity | F: CCA likely ongoing, feeding the AGN | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: EW-stripe as edge-on circumnuclear disk rejected: redshifted on east without blueshifted west counterpart  
  > "The stripe has redshifted velocities in the east but does not show a blueshifted counterpart in the west." (5)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA and MeerKAT broad wings often below S/N~3; w80 inferred from Gaussian dispersion  
  > "the shallow broad wings that dominate $w80$ are often seen below the $S/N\sim3$, making uncertain a direct measurement of the full extent of the lines." (Footnote 11)
- Caveat (inferred, ours): Kinematic model is schematic, not fitted; no uncertainties on masses or outflow quantities
- Caveat (inferred, ours): Galactic X_CO may be inappropriate
- Caveat (inferred, ours): Poor spatial resolution of ALMA data limits k-plot statistics
- Caveat (inferred, ours): Outflow velocity of 2000 km/s hinges on assumed low ring inclination

## Reproducibility

- Data public (paper): MUSE from ESO archive; ALMA project cited  
  > "we select two different sets of MUSE observations available on the ESO archive" (2.3 Ionised gas observations)
- Products in archive: _not stated_
- Code: GuFo on GitHub  
  > "<https://github.com/Fil8/GuFo>" (Footnote 5)
- Missing: ALMA reduction details (deferred to Morokuma-Matsui 2019)
- Missing: SoFiA parameters
- Missing: Region selection thresholds in k-plot
- Data volume (inferred): ALMA ~tens of GB; MeerKAT and MUSE additional
- Score (inferred): 2/5, ALMA is a minor component, processing is inherited, and the kinematic model is schematic.
- Rediscovery candidate: no, ALMA recipe is deferred to another paper and multi-facility inputs are needed.

## Links

- Method: (cite: Morokuma:2019) (ALMA CO data reduction)
- Method: (cite: Gaspari:2018) (k-plot and C-ratio method)
- Companion: (cite: Kleiner:2021) (MeerKAT H I reduction)
- Companion: (cite: Maccagni:2020) (radio continuum and flickering history)
- Related: MeerKAT Fornax Survey

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "facts": 73,
  "stated": 34,
  "rate": 0.466
 },
 "evidence_ok": true
}
```
