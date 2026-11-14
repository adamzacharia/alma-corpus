# ALMA captures feeding and feedback from the active galactic nucleus in NGC 613

`2019A&A...632A..33A` | Astronomy and Astrophysics 2019 | first author: Audibert, A. | arXiv: 1905.01979 | DOI: 10.1051/0004-6361/201935845

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How does the molecular gas in the central kpc of NGC 613 trace AGN feeding (nuclear trailing spiral, gravity torques) and AGN feedback (a molecular outflow), and what drives the outflow?  
  > "This object presents a nuclear trailing spiral and we discovered a molecular outflow in its nuclear region." (Introduction)
- Target **NGC 613**: coordinates RA 01h34m18.23s, Dec -29d25m06.56s (J2000, NED); new AGN position 01h34m18.19s, -29d25m06.59s (this work)  
  > "NGC 613 is a nearby barred SB(rs)bc galaxy (cite: vau91) at a distance of 17.2 Mpc (1$''$=83 pc)." (2.1 NGC 613); "V$\rm _{hel}$            |    1481$\pm$5 km$\rm s^{-1}$" (Table 1); z/distance 17.2 Mpc; Vhel = 1481 km/s  
  > "NGC 613 is a nearby barred SB(rs)bc galaxy (cite: vau91) at a distance of 17.2 Mpc (1$''$=83 pc)." (2.1 NGC 613); "V$\rm _{hel}$            |    1481$\pm$5 km$\rm s^{-1}$" (Table 1); distance from NED  
  > "NGC 613 is a nearby barred SB(rs)bc galaxy (cite: vau91) at a distance of 17.2 Mpc (1$''$=83 pc)." (2.1 NGC 613); "V$\rm _{hel}$            |    1481$\pm$5 km$\rm s^{-1}$" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00404.S, 2016.1.00296.S
- bands: Band 7  
  > "continuum in band 7, at rest frame frequencies $\nu_{rest}$ of 345.8, 342.9, 354.5, 356.7 and 350 GHz, respectively." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1800 MHz (Cycle 3); 1.875 GHz per spectral window  
  > "1800 MHz bandwidth in the continuum" (2 Observations)
- arrays: _not stated_
- configurations: Cycle 3: TC (15-630 m) and TE (15-1400 m); Cycle 4: TM2 (19-500 m) and TM1 (19-3100 m)  
  > "The compact configuration (TM2, baselines 19 to 500m) was observed with 44 antennas for an integration time of 14 minutes" (2 Observations)
- baselines: _not stated_
- angular resolution: 0.21''x0.19'' combined cube (~17 pc)  
  > "resulting in a synthesised beam of 0.21$''$$\times$0.19$''$ for the concatenated data cube" (2 Observations)
- max recoverable scale: ~12''  
  > "The largest recoverable angular scale corresponding to the shortest baseline is about 12$''$." (2 Observations)
- sensitivity: continuum rms 87 uJy/beam; 0.43 mJy/beam per 10 km/s channel  
  > "The total integration time provided an rms of 87$\mu$Jy/beam in the continuum, and in the line channel maps 0.43 mJy/beam per channel of 10 km/s" (2 Observations)
- time on source: TC 20 min, TE 40 min (incl. overheads), TM2 14 min, TM1 1.2 hr  
  > "total integration of 40 minutes and a synthesised beam of $\sim$0.14$''$" (2 Observations)
- observing dates: TC April 2016; TE August 2016; Cycle 4 November 2016 and July 2017  
  > "The Cycle 4 observation were carried out in November 2016 and July 2017" (2 Observations)
- pi or archival as stated: PI F. Combes (own programs)  
  > "(project ID: #2016.1.00296.S, PI F. Combes)" (2 Observations)
- Line: CO 3-2 (345.8 GHz)
- Line: CS 7-6 (342.9 GHz)
- Line: HCN 4-3 (354.5 GHz)
- Line: HCO+ 4-3 (356.7 GHz)
- Other facility **SEST**: CO(1-0) and CO(2-1) single-dish spectra (Bajaja et al. 1995) for missing-flux comparison  
  > "We compare it to the central spectrum obtained with the 15-m single dish obtained with the Swedish-ESO Submillimeter Telescope (SEST)" (3.3 CO luminosity and H2 mass)
- Other facility **HST**: F814W image for morphology and the stellar potential  
  > "The gravitational potential is computed in the plane of the galaxy using a red image (F814W) from HST" (5 Torques and AGN fueling)
- Other facility **VLA**: 4.86 GHz radio jet map (Hummel & Jorsater 1992)  
  > "We compare the molecular to the radio emission observed with the Karl G. Jansky Very Large Array (VLA) at 4.86 GHz (cite: hum92)" (4.1 The CO(3-2) kinematics of the outflow)
- Other facility **SINFONI**: NIR [FeII], Brgamma, H2 maps (Falcon-Barroso et al. 2014)  
  > "NIR maps of \[FeII\], Br$\gamma$ and H$\rm_{2}\lambda 2.12\mu m$ presented in (cite: fal14)" (3.6 Comparison to the warm molecular and ionised gas)
- External data: SEST CO(2-1) central spectrum (T_A*=200 mK, FWHM=300 km/s, 1504 Jy km/s in 22'' beam) and CO(1-0) masses  
  > "found a CO(2-1) spectrum peaking at T$_A^*$= 200 mK with FWHM=300 km/s, yielding a total integrated flux of 1504 Jy km/s, in a beam of 22$''$" (3.3 CO luminosity and H2 mass) [from (cite: bajaja95)]
- External data: NIR line fluxes for nucleus, ring spots and intermediate aperture  
  > "We use the line emission listed in Tables 1 and 2 of (cite: fal14) for different apertures" (3.6 Comparison to the warm molecular and ionised gas) [from (cite: fal14)]
- External data: AGN bolometric luminosity from [OIII], L_AGN=4e42 erg/s  
  > "We adopt the bolometric AGN luminosity derived from the O \[iii\] emission line, $L_{AGN}=4\times10^{42}$ erg/s (cite: davies17)" (4.5 The driving mechanism: AGN or star formation?) [from (cite: davies17)]
- External data: X-ray luminosity log L_X(2-10keV)=41.3 erg/s  
  > "(cite: casta13) reported a X-ray luminosity of log$L_{X}(2-10keV)=$41.3 erg/s" (4.5 The driving mechanism: AGN or star formation?) [from (cite: casta13)]
- External data: Jet flux at 4.86 GHz, 7.2 mJy; NVSS 179.6 mJy at 1.4 GHz  
  > "At 4.86 GHz, the flux associated to the jet is $S_\nu$=7.2 mJy" (4.5 The driving mechanism: AGN or star formation?) [from (cite: hum92); (cite: condon98)]
- External data: Stellar mass 4.5e10 Msun and BH mass 3.7e7 Msun from Paper I  
  > "the stellar mass of $M_*=4.5\times10^{10}M_\odot$ calculated in Paper I" (4.5 The driving mechanism: AGN or star formation?) [from Paper I (cite: combes18)]
- External data: Halpha rotation curve  
  > "the H$\alpha$ rotation curve taken from (cite: bur64)" (3.4 CO(3-2) kinematics) [from (cite: bur64)]

## Processing

### Calibration

- pipeline or manual: Calibrated and concatenated with CASA  
  > "The data from Cycle 3 and 4 were calibrated and concatenated with the CASA software" (2 Observations)
- casa version: 4.5.3 to 4.7.2  
  > "CASA software (version from 4.5.3 to 4.7.2" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: radio quasars close to the target, regularly monitored at ALMA  
  > "The flux calibration was done with radio quasars close to the position in the sky of the target, which are regularly monitored at ALMA" (2 Observations)
- flux scale uncertainty: 10%  
  > "resulted in 10% accuracy" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: GILDAS imaging and cleaning  
  > "the imaging and cleaning were performed with the GILDAS software" (2 Observations)
- deconvolver: Hogbom  
  > "The CLEANing was performed using the Hogbom method and a natural weighting" (2 Observations)
- weighting robust: natural weighting  
  > "The CLEANing was performed using the Hogbom method and a natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: moment maps clipped at <5 sigma_rms  
  > "We constructed the moment maps of the CO(3-2) line clipping the emission at $<$5$\rm\sigma_{rms}$." (3.2 Molecular gas distribution and morphology)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction with UV_CONTINUUM and UV_SUBTRACT  
  > "subtraction of the continuum in the $uv$-plane using the tasks UV_CONTINUUM and UV_SUBTRACT" (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied  
  > "The final maps were corrected for primary beam attenuation." (2 Observations)
- array combination: all configurations (TC, TE, TM2, TM1) concatenated  
  > "in this work we have combined all the configurations to improve the sensitivity" (2 Observations)
- smoothing: cubes smoothed to 10 km/s (11.5 MHz)  
  > "The data cubes were then smoothed to 10 km/s (11.5 MHz)." (2 Observations)
- final beam: 0.21''x0.19''  
  > "synthesised beam of 0.21$''$$\times$0.19$''$ for the concatenated data cube" (2 Observations)
- final rms: 87 uJy/beam continuum; 0.43 mJy/beam per 10 km/s channel  
  > "rms of 87$\mu$Jy/beam in the continuum" (2 Observations)

### Inherited from earlier work

- Observations of the NUGA sample and torus analysis (Paper I)  
  > "The observations of the NUGA sample are described in Paper I; here we include additional details for NGC 613." (2 Observations) [from Paper I (cite: combes18)]
- Gravitational torque method  
  > "following the methodology described by (cite: santi05)" (5 Torques and AGN fueling) [from (cite: santi05)]
- Rotation curve model  
  > "We assume a simple model for the rotation curve, proposed by (cite: ber91)" (3.4 CO(3-2) kinematics) [from (cite: ber91)]
- Outflow rate geometry  
  > "Following (cite: fio17) and (cite: cicone14), for a spherical or multi-conical geometry" (4.3 Mass outflow rate) [from (cite: fio17); (cite: cicone14)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for UV_CONTINUUM
- Clean mask, threshold and iterations in GILDAS
- Data cube velocity-channel range used for the nuclear spectrum fits
- 3D-Barolo parameter files (ring widths, number of rings, mask)
- Tilted-ring fitting details (ring centres, weighting)
- How flux scale and rms were derived when combining the different cycles
- Aperture definitions for dense-gas ratios (clump aperture)
- Fixed r31, aCO values for the nuclear region used in Paper I

## Analysis recipe

1. **Calibrate, concatenate and image**: CASA calibration/concatenation of Cycle 3 and 4; GILDAS Hogbom cleaning, natural weights; uv continuum subtraction; smoothing to 10 km/s  
  > "The data from Cycle 3 and 4 were calibrated and concatenated with the CASA software" (2 Observations)
   - software: CASA, GILDAS
   - parameter: natural weighting; beam 0.21''x0.19''  
  > "resulting in a synthesised beam of 0.21$''$$\times$0.19$''$ for the concatenated data cube" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum AGN position and flux**: Circular Gaussian fit in uv-plane  
  > "We determine the peak of the continuum emission by fitting a circular Gaussian source in the $uv$-plane using the GILDAS UV_FIT task." (3.1 Continuum emission)
   - software: GILDAS UV_FIT
   - fitting: circular Gaussian in uv-plane  
  > "fitting a circular Gaussian source in the $uv$-plane using the GILDAS UV_FIT task" (3.1 Continuum emission)
   - validation: Consistent with Miyamoto et al. and X-ray positions  
  > "Within the error bar, the AGN position is consistent with the positions derived by (cite: miy17) and from X-ray observations (cite: liu05)." (3.1 Continuum emission)
3. **Total CO flux, missing flux and H2 mass**: Integrate the CO(3-2) spectrum over the 18'' FoV, fit 3 Gaussians, compare to SEST-based expected flux, convert to mass  
  > "We decomposed the spectrum in three components, C1, C2 and C3, and the results of the Gaussian fits for each component are displayed in Table [2]" (3.3 CO luminosity and H2 mass)
   - parameter: r31=0.82, r21~1  
  > "We assume a ratio of $\rm r_{31}=T_{3-2}/T_{1-0}$ of 0.82, typical for Seyfert galaxies (cite: mao10)" (3.3 CO luminosity and H2 mass)
   - assumption: Milky Way alpha_CO conversion factor of 2e20 cm-2/(K km/s), thermally excited gas  
  > "assuming thermally excited gas, and a Milky-Way like CO-to-H$_2$ conversion factor, of 2$\times$10$^{20}$cm$^{-2}$/(K.km/s)" (3.3 CO luminosity and H2 mass)
   - fitting: Gaussian fits  
  > "We decomposed the spectrum in three components, C1, C2 and C3, and the results of the Gaussian fits for each component are displayed in Table [2](#tab:flux)." (3.3 CO luminosity and H2 mass)
   - validation: Compared with SEST fluxes; missing flux up to 40-50%  
  > "Therefore, we should expect some missing flux by a factor up to $\sim$40-50%" (3.3 CO luminosity and H2 mass)
4. **Rotation curve and kinematic modeling**: Bertola model fit to radial velocities, tilted-ring fit to the velocity field (dr=0.3''), 3D-Barolo on the cube  
  > "We adopted a $\Delta r$=0.3$''$, that corresponds to the deprojected resolution of our observations in the galaxy plane." (3.4 CO(3-2) kinematics)
   - software: 3DBarolo
   - parameter: PA=120 deg, i=41 deg fixed in Barolo, with AGN position as centre  
  > "fixing the PA, inclination and central position to 120$^\circ$, 41$^\circ$ and AGN position, respectively" (3.4 CO(3-2) kinematics)
   - assumption: circular orbits in a plane  
  > "assuming the gas is on circular orbits in a plane" (3.4 CO(3-2) kinematics)
   - fitting: _not stated_
   - validation: Compared with Halpha curve and optical PA/i; Barolo agrees with 2D approach  
  > "the results using ^3D^BAROLO are quite coherent with the 2D approach described above in the text" (3.4 CO(3-2) kinematics)
5. **Dense-gas line ratios and diagnostic diagram**: Measure HCN/HCO+ and HCN/CS ratios in a 0.3'' central aperture and in a clump, place on the Izumi et al. diagram  
  > "We measured the line intensity ratios R$_{\rm HCN/HCO^{+}}$ and R$_{\rm HCN/CS}$ in these two regions" (3.5 Dense gas: HCO+, HCN and CS emission)
   - fitting: _not stated_
   - validation: _not stated_
6. **Outflow detection and flux**: Fit a Gaussian core to the nuclear spectrum (0.28'' aperture), integrate blue and red residual wings; alternatively moment maps in velocity ranges  
  > "First, we fit a Gaussian to the nuclear spectrum to take into account the contribution of the main rotating disk" (4.1 The CO(3-2) kinematics of the outflow)
   - parameter: second approach: blue -400 to -120 km/s, red +120 to 300 km/s  
  > "taking the velocity channels from -400 to -120 km/s for the blue component and from +120 km/s to 300 km/s for the red wing" (4.1 The CO(3-2) kinematics of the outflow)
   - fitting: Gaussian core fit; residual wings integrated  
  > "First, we fit a Gaussian to the nuclear spectrum to take into account the contribution of the main rotating disk (black line in Fig. [15](#fig:outfit))." (4.1 The CO(3-2) kinematics of the outflow)
   - validation: Ruled out central-mass rotation (MBH 1.9e9) and coplanar inflow; velocities limited to 300 km/s to avoid H13CN  
  > "The order of magnitude of the co-planar inflow would be too large, and therefore we can exclude this hypothesis." (4.1 The CO(3-2) kinematics of the outflow)
7. **Outflow mass, rate and energetics**: L'CO from Solomon & Vanden Bout; M(H2)=alpha_CO L'CO r13; Mdot = v M/R (thin shell); P_K=0.5 v^2 Mdot  
  > "In the following estimates, we use Eq. [\[shell\]](#shell) to derive more conservative outflow energetics, since the observations cannot constrain the geometry, and thus favour one scenario over the other." (4.3 Mass outflow rate)
   - parameter: R_out=0.28'' (~23 pc), v_out=300 km/s, r31=0.82, D_L=17.2 Mpc  
  > "the outflow is found in a region of $R_{out}$=0.28$''$ ($\sim$23 pc) and here we will consider the maximum projected velocity of the wings, $v_{out}$=300 km/s" (4.3 Mass outflow rate)
   - assumption: Galactic alpha_CO=4.36 (upper limit) or 1/4 of this for galaxy centres  
  > "the recommended value to be applied in galaxy centers is $\alpha_{CO,cen}\sim\frac{1}{4}\alpha_{CO,MW}$, with a 0.3 dex uncertainty" (4.2 CO-to-H2 conversion)
   - fitting: _not stated_
   - validation: Compared with Fluetsch et al. 2019 relation (4.8 Msun/yr predicted)  
  > "we should expect an outflow mass rate of $4.8\,M_\odot yr^{-1}$ in NGC 613" (4.5 The driving mechanism: AGN or star formation?)
8. **Gravity torques**: Potential from deprojected HST F814W image via Fourier transform, torques weighted by CO surface density, azimuthally averaged  
  > "The image has been rotated and deprojected according to PA=120$^\circ$ and i=41$^\circ$, and then Fourier transformed to compute the gravitational potential and forces." (5 Torques and AGN fueling)
   - parameter: M/L=0.5 (I-band), h_z=317 pc, pixel 0.06''=5 pc  
  > "The potential has been obtained assuming a constant mass-to-light ratio of M/L=0.5 in the I-band" (5 Torques and AGN fueling)
   - assumption: No bulge-disk separation, no dark matter, exponential disk with h_z = 1/12 h_r  
  > "We have not separated the bulge from the disk contribution since NGC 613 is a late type (Sbc) galaxy." (5 Torques and AGN fueling)
   - fitting: M/L fit to reproduce the CO rotation curve  
  > "The stellar M/L value was fit to reproduce the observed CO rotation curve." (5 Torques and AGN fueling)
   - validation: _not stated_

## Software

- **CASA** 4.5.3 to 4.7.2: Calibration and concatenation  
  > "calibrated and concatenated with the CASA software" (2 Observations)
- **GILDAS** : Imaging, cleaning, continuum subtraction, uv fitting, analysis  
  > "The analysis were made in GILDAS together with PYTHON packages" (2 Observations)
- **3DBarolo** : 3D tilted-ring modelling with radial velocity components  
  > "^3D^BAROLO performs a 3D tilted-ring modeling of the emission line data-cubes" (3.4 CO(3-2) kinematics)
- **APLpy** : Python plotting package cited  
  > "PYTHON packages (cite: radiotools; aplpy; pyspec)" (2 Observations)
- **PySpecKit** : Python spectroscopic toolkit cited for analysis  
  > "PYTHON packages (cite: radiotools; aplpy; pyspec)" (2 Observations)
- **Astropy** : Acknowledged use  
  > "This research made use of Astropy, a community developed core Python package for Astronomy." (Acknowledgements)
- **GALFIT** : Stellar mass decomposition in Paper I  
  > "derived from the S$\rm ^4$G3.6 $\mu$m IR image and the GALFIT decomposition" (4.5 The driving mechanism: AGN or star formation?)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux of AGN at 350 GHz | 2.4 | 0.1 | mJy | 2 | the flux is 2.4$\pm$0.1 mJy |
| Total CO(3-2) flux in 18'' FoV | 1307 | 121 | Jy km/s | 3 | The total flux is $\rm S_{CO(3-2)}=1307\pm121$ Jy.km/s. |
| Molecular mass in FoV (corrected for missing flux) | 5.6e8 | not stated | Msun | 3 | we find a molecular mass of 5.6$\times$10$^8$M$_\odot$ in our FoV |
| Nuclear core mass inside 23 pc | 4.8e7 | not stated | Msun | 6 | inside the radius of 23 pc is $\rm4.8\times10^{7}M_\odot$ |
| Outflow mass (Galactic alpha_CO) | 1.9-2.2e6 | not stated | Msun | 7 | This implies a molecular mass of $M_{out}$=1.9-2.2$\times$10$^6$M$_\odot$. |
| Outflow mass (alpha_CO = 1/4 MW) | 4.8-5.5e5 | not stated | Msun | 7 | in the range of $\rm M_{out}=4.8-5.5\times10^5 M_\odot$ |
| Mass outflow rate (Galactic alpha_CO) | 25-29 | not stated | Msun/yr | 7 | we find a mass outflow rate of $\dot{M}_{out}$=(25-29) $\rm M_\odot yr^{-1}$ |
| Mass outflow rate (alpha_CO = 1/4 MW) | ~7 | not stated | Msun/yr | 7 | we find that the mass load rate is $\dot{M}_{out}\sim7\,M_\odot yr^{-1}$ |
| Outflow kinetic power | 8e41 | not stated | erg/s | 7 | we find $P_{K,out}=8\times10^{41}$ erg/s, which corresponds to 20%$L_{AGN}$ |
| Outflow momentum rate in L_AGN/c | ~400 | not stated | dimensionless | 7 | it is higher by a factor of $\dot{M}_{out}v\sim400L_{AGN}/c$ |
| Jet power | 5.5e42 | not stated | erg/s | 7 | we find $P_{jet}=5.5\times10^{42}$ erg/s |
| R_HCN/HCO+ in AGN | 1.76 | 0.26 | dimensionless | 5 | AGN        /    1.76$\pm$0.26    /  7.95$\pm$1.19 |
| R_HCN/CS in AGN | 7.95 | 1.19 | dimensionless | 5 | AGN        /    1.76$\pm$0.26    /  7.95$\pm$1.19 |
| HCN(4-3)/CO(3-2) in core vs wings | ~0.2 core, up to ~0.6 wings | not stated | dimensionless | 6 | has a ratio of $\sim$0.2 and the ratio increases for the high-velocities towards the wings, up to values of $\sim$0.6 |
| Gas rotation period at 100 pc | 9.5 | not stated | Myr | 8 | which is $T_{rot}(100pc)\sim$9.5 Myr |

## Qualitative findings

- A 2-arm trailing nuclear spiral at r<~100 pc lies inside the ILR ring, connected to the ring by filaments.  
  > "The 2-arm nuclear gas spiral at $\rm r\lesssim$100 pc is trailing toward the center" (3.2 Molecular gas distribution and morphology)
- Star formation alone cannot drive the outflow; AGN radio jet entrainment is favoured.  
  > "we conclude that star formation alone is not able to drive the nuclear molecular outflow in NGC 613." (4.5 The driving mechanism: AGN or star formation?)

## Claim tuples

- H: Is there a molecular outflow in the nucleus of NGC 613? | E: PVDs and nuclear spectra at 0.2'' resolution, wing integration | R: Blue and red wings up to ±300 km/s within r~0.3'' not explained by rotation or coplanar inflow | F: A nuclear molecular outflow is detected, co-spatial with the radio jet blob | **supported**
- H: Is the outflow driven by star formation or the AGN? | E: Compare Mdot_out with nuclear SFR and with AGN and jet power | R: Mdot ~27 Msun/yr vs nuclear SFR ~0.015; Pjet one to two orders above the outflow kinetic power | F: AGN via radio jet drives the flow; energetics exceed AGN feedback models (possible fossil outflow) | **partially**
- H: Is gas being fuelled toward the AGN? | E: Gravity torques from HST potential weighted by CO surface density | R: Torques negative from 25 to 100 pc | F: Nuclear trailing spiral provides efficient fuelling of the central BH | **supported**
- H: Does the dense gas show an AGN signature and enhanced HCN in the outflow? | E: Line ratios and HCN/CO along the nuclear spectrum | R: AGN region in the XDR part of the submm-HCN diagram; HCN/CO rises from 0.2 to 0.6 in the wings | F: XDR-like excitation; HCN enhanced in the outflow (dense gas or shocks) | **supported**

## Reasoning

- Why this data: Combining all configurations to improve sensitivity to faint broad wings  
  > "the data analyzed here have more sensitivity in order to detect faint broad wings usually associated to outflows." (Introduction)
- Why this method: Smaller alpha_CO and thin-shell geometry adopted for conservative outflow estimates  
  > "In the following estimates, we use Eq. [\[shell\]](#shell) to derive more conservative outflow energetics, since the observations cannot constrain the geometry, and thus favour one scenario over the other." (4.3 Mass outflow rate)
- Alternative: Central BH mass explaining high velocities rejected (needs 1.9e9 Msun); coplanar inflow rejected (460 km/s too large)  
  > "The order of magnitude of the co-planar inflow would be too large, and therefore we can exclude this hypothesis." (4.1 The CO(3-2) kinematics of the outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux from lack of short spacings; outflow mass uncertain by alpha_CO; outflow rate uncertain by a factor of a few; geometry unconstrained  
  > "Although this estimate is uncertain by a factor of a few, given the unknown projection and the assumptions previously discussed in the text" (4.5 The driving mechanism: AGN or star formation?)
- Limitation (authors): Wings barely resolved  
  > "Due to the small size of the outflow, we can barely resolve each wing contribution" (4.1 The CO(3-2) kinematics of the outflow)
- Caveat (inferred, ours): Outflow wing separation depends on the core Gaussian subtraction and H13CN contamination
- Caveat (inferred, ours): Outflow geometry, inclination and alpha_CO are unconstrained, so the energetics are uncertain by a factor of several
- Caveat (inferred, ours): Gas-torque result depends on assumed M/L and a deprojected single-component stellar potential
- Caveat (inferred, ours): The jet driving argument rests on an empirical radio-power relation and a spectral index assumption

## Reproducibility

- Data public (paper): Project codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.0.00404.S, and ADS/JAO.ALMA#2016.0.00296.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: GILDAS clean parameters and masks
- Missing: Barolo and tilted-ring settings
- Missing: Aperture definitions for spectra and ratios
- Missing: Torque code details (inherited method)
- Data volume (inferred): ~100-300 GB raw for four configurations in two projects
- Score (inferred): 3/5, Data identified and main steps described, but imaging and fitting parameters are partly missing and the torque and Barolo details are unstated.
- Rediscovery candidate: no, The recipe lacks key parameters (clean masks, line-free channels, Barolo settings), and the torque analysis needs HST data and code not given.

## Links

- Method: (cite: ber91) (Rotation curve model)
- Method: (cite: barolo) (3D-Barolo)
- Method: (cite: santi05) (Gravity torque method)
- Method: (cite: izumi16) (Submm-HCN diagram)
- Method: (cite: fio17) (Outflow rate geometry)
- Companion: Paper I (cite: combes18) (NUGA CO(3-2) torus sample including NGC 613 data and BH mass)
- Companion: (cite: fal14) (SINFONI NIR data)
- Related: NUGA

## Checks

```json
{
 "quotes": 113,
 "quotes_ok": 113,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.0.00404.S",
  "2016.0.00296.S"
 ],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 104,
  "stated": 84,
  "rate": 0.808
 },
 "evidence_ok": true
}
```
