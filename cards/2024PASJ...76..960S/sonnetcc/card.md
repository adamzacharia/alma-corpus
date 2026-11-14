# Spiral magnetic fields and their role on accretion dynamics in the circumnuclear disk of Sagittarius A*: Insight from λ = 850 μm polarization imaging

`2024PASJ...76..960S` | Publications of the Astronomical Society of Japan 2024 | first author: Sato, Kazuki | arXiv: 2407.05093 | DOI: 10.1093/pasj/psae062

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Structure and strength of the magnetic field in the Circumnuclear Disk around Sgr A*, from JCMT 850 um polarization compared with the Wardle & Koenigl model, and its implication for accretion and the magnetorotational instability; ALMA CS J=2-1 is used only to isolate CND gas by velocity  
  > "We showcase a study on the physical properties of the Circumnuclear Disk (CND)" (abstract); "Our analysis of the newly obtained polarization data has revealed the presence of a well-ordered" (4 Discussion)
- Target **Circumnuclear Disk (CND) around Sgr A***: coordinates _not stated_; z/distance 8.178 kpc (8178 pc)  
  > "which corresponds to 0.50 pc at a distance $d$ of 8.178 kpc" (2.1 JCMT polarization data); "is located at a distance of $8178\pm 13_{\rm stat}\pm 22_{\rm sys}$ pc (cite: GRAVITY2019)" (1.2 Galactic Center); distance from GRAVITY2019 (GRAVITY Collaboration 2019)  
  > "which corresponds to 0.50 pc at a distance $d$ of 8.178 kpc" (2.1 JCMT polarization data); "is located at a distance of $8178\pm 13_{\rm stat}\pm 22_{\rm sys}$ pc (cite: GRAVITY2019)" (1.2 Galactic Center)

## Data provenance

- ALMA projects: 2017.1.00040.S
- bands: _not stated_
- frequencies and spectral setup: CS J=2-1 at nu = 97.980 GHz; velocity resolution 2.0 km/s in final cubes  
  > "for the 2.67$''$$\times$1.67$''$ beam at a frequency of $\nu = 97.980$ GHz" (2.2 ALMA CS data); "were created with a velocity resolution of 2.0 km s$^{-1}$" (2.2 ALMA CS data)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 7 m ACA, and Total Power array  
  > "The ALMA images reproduced by us were obtained by combining visibility data from three arrays" (Table 1 caption); "To combine the visibility data from both the main 12 m-dish array and the 7 m-dish Atacama Compact Array (ACA)," (2.2 ALMA CS data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.67'' x 1.67'' beam (combined cube)  
  > "for the 2.67$''$$\times$1.67$''$ beam at a frequency of $\nu = 97.980$ GHz" (2.2 ALMA CS data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 4.42 h total (Table 1); 7 m array 82 min, Total Power 162 min; 12 m array exposures of 14 min and 7 min  
  > "4.42" (Table 1); "the 7-m array (82-minute exposure, yielding 18.27$''$$\times$8.43$''$ beam), and the Total Power array (162-minutes with 66.0$''$ beam)" (Table 1 caption)
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data taken by Tsuboi et al. 2018 (tsu18)  
  > "We retrieved the archival ALMA data taken by (cite: tsu18)" (2.2 ALMA CS data)
- Line: CS J=2-1 (97.980 GHz)
- Other facility **JCMT POL-2/SCUBA-2 (850 um polarization; proposals M16BP061, M17AP074)**: Archival 850 um Stokes I, Q, U polarization data, 14.6 h in total; the primary dataset of the paper  
  > "The archival data were initially obtained by P. T. P. Ho (Proposal ID: M16BP061) and G. Bower (M17AP074) over the course of nine nights, consisting of 29 exposures" (2.1 JCMT polarization data)
- Other facility **VLA (6 cm, project AZ44)**: Already-reduced 6 cm continuum image, C array, used for morphology comparison  
  > "From the NRAO data archive, we retrieved the already-reduced image taken in the" (2.3 VLA and SOFIA data); "with the C-array configuration over a 2-hour period on April 3, 1992" (2.3 VLA and SOFIA data)
- Other facility **SOFIA/FORCAST (37.1 um, proposal 07-0189)**: Fully reduced 37.1 um continuum image used to define the CND extent (20 sigma contour)  
  > "The data were originally acquired during the seventh cycle as part of the FORCAST Galactic Center Legacy Project (cite: han20)" (2.3 VLA and SOFIA data)
- External data: JCMT beam size and flux-conversion factor 2.19 +/- 0.13 Jy arcsec^-2 pW^-1  
  > "we applied the updated flux-conversion factor of $2.19\pm 0.13$ Jy arcsec$^{-2}$ pW$^{-1}$ (cite: mai21)" (2.1 JCMT polarization data) [from Mairs et al. 2021 (cite: mai21)]
- External data: WK model fiducial parameters (omega, theta, alpha_WK, beta_WK, delta_WK, epsilon_WK ranges) for gc1-gc5  
  > "Although these four parameters are presented as free parameters, fiducial values are provided in the (cite: war90) paper (refer to their Table 1)." (3.3.2 Analysis of Magnetic-field Structure) [from Wardle & Koenigl 1990 (cite: war90)]
- External data: Disk inclination i_disk = 67 deg (error 5 deg)  
  > "We adopted the disk inclination angle $i_{\mathrm{disk}} = 67^{\circ}$ from (cite: lau13)" (3.3.2 Analysis of Magnetic-field Structure) [from Lau et al. 2013 (cite: lau13)]
- External data: CND thickness 0.5 pc at r = 2 pc and 0.34 pc at r = 1.4 pc, used for z_half  
  > "The thickness of the CND is estimated to be approximately 0.5 pc at $r = 2$ pc (cite: gus87) and 0.34 pc at $r =$ 1.4 pc (cite: lau13)." (3.3.2 Analysis of Magnetic-field Structure) [from Gusten et al. 1987 (cite: gus87); Lau et al. 2013 (cite: lau13)]
- External data: CS kinetic temperature 200 K from LVG analysis, and CS density from LVG read from Figure 10a  
  > "the LVG analysis of the multi-transition CS lines observations (200 K; (cite: tsu18)) toward the CND" (4.2.2 Plasma beta); "(read from Figure 10a in (cite: tsu18))" (4.2.2 Plasma beta) [from Tsuboi et al. 2018 (cite: tsu18)]
- External data: H2CO temperature 63 K used with the CS temperature to set the isothermal sound speed  
  > "a representative value from the H$_2$CO observations (63 K; (cite: gin16))" (4.2.2 Plasma beta) [from Ginsburg et al. 2016 (cite: gin16)]
- External data: Atomic hydrogen density in the inner cavity taken from continuum spectrum analysis (2.5e3 cm^-3)  
  > "Considering the ambiguity of the observational estimate, we selected the density estimated from the continuum spectrum analysis." (4.1.1 B0 estimate) [from Zylka et al. 1995 (cite: zyl95)]
- External data: Smallest non-thermal velocity dispersion 9.96 km/s adopted for the effective plasma beta  
  > "we selected the smallest estimate of $\sigma_{\rm nth} =$ 9.96 km s$^{-1}$ by (cite: hen16)" (4.2.2 Plasma beta) [from Henshaw et al. 2016 (cite: hen16)]
- External data: Black hole mass 4.152e6 Msun used for the Keplerian velocity  
  > "for a central mass of $4.152\times 10^6 M_\odot$ (cite: EHT2022)" (4.2.3 MRI) [from EHT Collaboration 2022 (cite: EHT2022)]
- External data: Plane-of-sky B-field strength from modified DCF, used for comparison  
  > "as derived by (cite: gue23) (see their Table 5)" (4.1.2 B-field strength) [from Guerra et al. 2023 (cite: gue23)]
- Simulation/model as data: Wardle & Koenigl (1990) self-similar magnetized disk models gc1-gc5, evaluated at each polarization segment  
  > "The WK model, encompassing five variations denoted as gc1, gc2, gc3, gc4, and gc5, proposes that" (3.3.2 Analysis of Magnetic-field Structure)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline with Cycle 5 calibration scripts  
  > "calibrated the visibility data using the Common Astronomy Software Applications (CASA v5.1.1-5) pipeline along with calibration scripts for Cycle 5 data" (2.2 ALMA CS data)
- casa version: CASA v5.1.1-5 (calibration); CASA v6.4 (concat, tclean, feather)  
  > "calibrated the visibility data using the Common Astronomy Software Applications (CASA v5.1.1-5) pipeline" (2.2 ALMA CS data); "tasks in CASA (v6.4) with a Briggs robust parameter of 0.5" (2.2 ALMA CS data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: concat (12 m + ACA), tclean, and feather (with Total Power) in CASA v6.4  
  > "Image construction and deconvolution using interferometric visibilities, as well as single-dish ones from the total power array, were carried out using the" (2.2 ALMA CS data); "tasks in CASA (v6.4) with a Briggs robust parameter of 0.5" (2.2 ALMA CS data)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "tasks in CASA (v6.4) with a Briggs robust parameter of 0.5" (2.2 ALMA CS data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: tclean automasking  
  > "The automasking function in" (2.2 ALMA CS data); "was utilized during the cleaning process." (2.2 ALMA CS data)
- multiscale scales: _not stated_
- continuum subtraction: continuum emission subtracted after concatenation of the 12 m and 7 m data  
  > "followed by the subtraction of continuum emission" (2.2 ALMA CS data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m and 7 m visibilities concatenated, then combined with Total Power by feather  
  > "To combine the visibility data from both the main 12 m-dish array and the 7 m-dish Atacama Compact Array (ACA)," (2.2 ALMA CS data); "our enhanced image cube, produced from the 12 m, 7 m, and total power (TP) arrays" (2.2 ALMA CS data)
- smoothing: _not stated_
- final beam: 2.67'' x 1.67''  
  > "for the 2.67$''$$\times$1.67$''$ beam at a frequency of $\nu = 97.980$ GHz" (2.2 ALMA CS data)
- final rms: _not stated_

### Inherited from earlier work

- ALMA CS J=2-1 data set and project taken from the earlier analysis of the same data  
  > "We retrieved the archival ALMA data taken by (cite: tsu18)" (2.2 ALMA CS data) [from (cite: tsu18)]
- JCMT POL-2 reduction follows the standard pipeline of a given version  
  > "We followed the standard pipeline (version dated July 23, 2021) as described in, e.g., (cite: war17)." (2.1 JCMT polarization data) [from (cite: war17)]
- Debiasing of the polarized intensity with a modified asymptotic estimator  
  > "using a modified asymptotic estimator as described by (cite: pla14; mon15)" (2.1 JCMT polarization data) [from (cite: pla14; mon15)]
- Rotating-disk model for the CND velocity field, with parameters adopted from earlier work  
  > "According to (cite: gus87; chr05; tsu18), the inclination-corrected LSR velocity of the CND at each sky position for a radius of the disk can be expressed as" (3.2.2 Velocity field) [from (cite: gus87; chr05; tsu18)]
- WK model parameters other than the azimuthal angle fixed to fiducial values  
  > "with other parameters set to fiducial values from Table 1 of (cite: war90)" (4.1.1 B0 estimate) [from (cite: war90)]

### Not stated but needed to reproduce (our reading)

- ALMA band and full spectral setup (spectral windows, channelization) for the CS J=2-1 data
- Line-free channels used for the ALMA continuum subtraction
- tclean parameters: cell size, image size, clean threshold, niter, automasking thresholds, and the per-array weighting used when combining 12 m and 7 m visibilities
- feather settings (scaling of the single-dish data) and the final cube RMS
- Which ALMA pipeline-calibrated products and flux calibrator were used
- pol2map configuration (masks, mapping parameters, iteration settings) for the JCMT reduction
- How the 12.6'' resolution polarization segments were selected, binned and thresholded (S/N cut, pixel/segment spacing) and the exact selection of the 51 segments plus the four excluded ones
- Exact procedure for converting the sky position to the WK azimuthal angle phi and the orientation of the CND major axis used in the model
- Total density rho_tot and the error budget behind the lambda_max and plasma beta uncertainties
- The 37.1 um and 6 cm images' processing details and alignment between datasets

## Analysis recipe

1. **Reduce the JCMT 850 um POL-2 data into Stokes I, Q, U and polarization maps**: pol2map reduction in Starlink SMURF, instrumental polarization subtracted with the 2019 model, flux conversion and attenuation correction, polarized intensity debiased  
  > "which is implemented in the SMURF package of the Starlink suite (cite: cha13)" (2.1 JCMT polarization data); "Instrumental polarizations were subtracted using the 2019 model." (2.1 JCMT polarization data)
   - software: Starlink SMURF pol2map
   - parameter: flux conversion factor 2.19 +/- 0.13 Jy arcsec^-2 pW^-1  
  > "we applied the updated flux-conversion factor of $2.19\pm 0.13$ Jy arcsec$^{-2}$ pW$^{-1}$ (cite: mai21)" (2.1 JCMT polarization data)
   - parameter: attenuation factor 1.35 +/- 0.008 for the POL-2 insertion  
  > "we applied an attenuation factor of $1.35\pm0.008$ (P. Friberg, private comm.)" (2.1 JCMT polarization data)
   - parameter: beam 12.6'' HPBW, 4.0'' pixels  
  > "we adopt the updated beam size (cite: mai21) of 12$''$6 in HPBW" (2.1 JCMT polarization data); "with a 4.0$''$-pixel size" (2.1 JCMT polarization data)
   - assumption: distance 8.178 kpc  
  > "which corresponds to 0.50 pc at a distance $d$ of 8.178 kpc" (2.1 JCMT polarization data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Define the CND extent from the 37.1 um contour and check what 850 um traces**: Ellipse defined by the 20 sigma contour of the 37.1 um image; area measured and converted to an effective radius; visual comparison with a published spectral-index map  
  > "We measure the area, $A$, enclosed by the contour to be 7750 arcsec$^2$, corresponding to $A = 12.2$ pc$^{-2}$." (3.1.1 Morphological comparisons); "We compared their Figure 9 with our images (Figure [1](#fig:ContImages)) visually using graphic software" (3.1.2 Spectral indices)
   - parameter: R_eff = sqrt(A/pi) = 2.0 pc  
  > "yields an effective radius $R_{\rm eff}$ of 2.0 pc" (3.1.1 Morphological comparisons)
   - assumption: 850 um morphology approximated as an ellipse to first order  
  > "We consider that the $\lambda=$ 850 $\mu$m emission morphology is reasonably described as an ellipse as a first-order approximation." (3.1.1 Morphological comparisons)
   - fitting: _not stated_
   - validation: Compared with the low-alpha region of the Garcia-Marin et al. spectral index map  
  > "confirmed that the elliptical region (defined in §[3.1.1](#sss:MorComp)) agrees with the low-$\alpha$ region" (3.1.2 Spectral indices)
3. **Measure the 850 um polarization fraction and its radial profile**: Polarization fraction plotted against projected radius from Sgr A*, with linear slopes on each side of the 2.0 pc break  
  > "which shows the radial dependence of the $P_{850}$ values" (3.1.3 Polarization fraction map); "Note that the radius is the projected one to the plane of the sky" (3.1.3 Polarization fraction map)
   - fitting: Linear slopes with Spearman correlation coefficients (0.45 inner, -0.47 outer)  
  > "is characterized by a slope of ${\rm d}P_{850}/{\rm d}r_{\rm pos} = +0.56\pm0.26$ percent pc$^{-1}$" (3.1.3 Polarization fraction map)
   - validation: _not stated_
4. **Make the ALMA CS J=2-1 cube and moment maps**: Calibrate with the Cycle 5 pipeline, concat 12 m and ACA, subtract continuum, tclean and feather with TP, convert to brightness temperature, then zeroth and first moment maps  
  > "Image construction and deconvolution using interferometric visibilities, as well as single-dish ones from the total power array, were carried out using the" (2.2 ALMA CS data); "we made the integrated-intensity map by calculating the zeroth order of the momentum over an LSR-velocity range of" (3.2.1 Morphological comparisons)
   - software: CASA
   - parameter: Briggs robust 0.5, velocity resolution 2.0 km/s  
  > "tasks in CASA (v6.4) with a Briggs robust parameter of 0.5" (2.2 ALMA CS data); "were created with a velocity resolution of 2.0 km s$^{-1}$" (2.2 ALMA CS data)
   - parameter: 2 sigma detection threshold per channel for moment maps  
  > "A $2\sigma$ detection threshold was used for each velocity channel to compute the zeroth and first order moment maps." (3.2.2 Velocity field)
   - fitting: _not stated_
   - validation: Cube compared with the earlier cube of Tsuboi et al. that did not include TP data  
  > "is overall consistent with the one used in (cite: tsu18), which did not include TP data" (2.2 ALMA CS data)
5. **Isolate CND gas by velocity with a rotating-disk model and define subregions**: Rotating-disk line-of-sight velocity model with a random velocity term, evaluated over radii; ring divided into five subregions A to E with velocity ranges  
  > "we adopted the rotating-disk hypothesis to identify the velocity components attributable to the CND" (3.2.2 Velocity field); "we divided the ring into five subregions, labeled A to E" (3.2.2 Velocity field)
   - parameter: V_rot = 105 km/s, i_cnd = 67 deg, Phi_0 = 91 deg; random velocity up to +/-30 km/s  
  > "we derived a value of 105 km s$^{-1}$, along with other geometrical parameters, aligning with previous studies" (3.2.2 Velocity field)
   - parameter: inner cavity radius r_cav(3D) of about 2.2 pc and CND radius R_eff(3D) of about 5.0 pc  
  > "set a radius of the inner cavity $r_{\rm cav}^{\rm 3D} \simeq 2.2$ pc" (3.2.2 Velocity field); "yielding a 3-dimensional CND radius of $R_{\rm eff}^{\rm 3D} \simeq 5.0$ pc" (3.2.2 Velocity field)
   - assumption: CND rotates as a disk; parameters taken from earlier work  
  > "Here, we adopt $V_{\mathrm{rot}} = 105\,\mathrm{km \: s^{-1}}$, $i_{\mathrm{cnd}} = 67^{\circ}$, and $\Phi_0 = 91^{\circ}$ based on the preceding argument." (3.2.2 Velocity field)
   - fitting: Model compared with the observed centroid-velocity map by eye; no fit stated  
  > "A robust comparison between the observed and the model centroid-velocity maps indicates that the simple model described by" (3.2.2 Velocity field)
   - validation: Consistent with earlier HCN and HCO+ centroid-velocity maps  
  > "Visual confirmation revealed that all spatio-velocity structures are consistent with previously derived centroid-velocity maps" (3.2.2 Velocity field)
6. **Compare the observed B-field position angles with the five WK models**: B-field vectors from polarization angles rotated by 90 deg; model Stokes q,u computed per segment as a function of azimuth phi; residuals Delta PA and chi-square compared across gc1-gc5; MAD_stat used for preference  
  > "derived by rotating the polarization segments in Figure [2](#fig:PinCNDaround) by $90^\circ$" (3.3.1 B-field structure); "In practice, we measured the $\phi$ value at each position and calculated the Stokes $q$ and $u$ parameters to determine the $PA_{\mathrm{model}}$ for each position." (3.3.2 Analysis of Magnetic-field Structure)
   - parameter: n = 51 segments inside the 20 sigma 37.1 um contour, excluding four segments affected by Sgr A*  
  > "resulting in a total of $n=51$ segments for analysis." (3.3.2 Analysis of Magnetic-field Structure)
   - parameter: half-thickness z_half = 0.4 pc, z/r about 0.08  
  > "We, therefore, arbitrarily adopted a geometrical mean of 0.4 pc as the half-thickness of the disk" (3.3.2 Analysis of Magnetic-field Structure)
   - assumption: i_disk = 67 deg; all other WK parameters at fiducial Table 1 values  
  > "We adopted the disk inclination angle $i_{\mathrm{disk}} = 67^{\circ}$ from (cite: lau13)" (3.3.2 Analysis of Magnetic-field Structure)
   - fitting: Single free parameter phi per segment; goodness by chi2 = sum(Delta PA)^2 / n; no sampler or priors  
  > "This approach consequently renders the Stokes $u$ and $q$ as functions of a single parameter, $\phi$." (3.3.2 Analysis of Magnetic-field Structure); "The quality of the fits was quantified with a Chi-square fit, given by" (3.3.2 Analysis of Magnetic-field Structure)
   - validation: Compared with the earlier WK analysis of 100 um KAO polarization  
  > "Our results are essentially consistent with those reported by (cite: war90), who investigated the 100 $\mu$m polarization data from the KAO (cite: hil90)." (3.3.2 Analysis of Magnetic-field Structure)
7. **Estimate the midplane field strength B0 in the inner cavity**: Invert WK Eqs. 2.11a and 2.11b for B0 so that alpha_WK and beta_WK approach their Table 1 ranges; weighted mean over gc1-gc3 using chi2  
  > "considering the average of $\alpha(B_0)$ and $\beta(B_0)$, so that they approximate the $\alpha$ and $\beta$ values given in Table 1 of (cite: war90) as closely as possible." (4.1.1 B0 estimate); "we also presented the weighted-mean strength of $0.24^{+0.05}_{-0.04}$ mG calculated for the gc1, 2, and 3 models" (4.1.1 B0 estimate)
   - parameter: n_H = 2.5e3 cm^-3, v_phi0 = 105 km/s, epsilon_WK = 0.22, r_cav = 2.2 pc  
  > "Considering the ambiguity of the observational estimate, we selected the density estimated from the continuum spectrum analysis." (4.1.1 B0 estimate)
   - assumption: Because the dependence on B0 is common to alpha and beta, a single B0 cannot satisfy both; an average is used  
  > "it is impossible to have a $B_0$ value that satisfies both functions simultaneously" (4.1.1 B0 estimate)
   - fitting: Numerical search for the most plausible B0  
  > "Therefore, we numerically searched for the" (4.1.1 B0 estimate)
   - validation: _not stated_
8. **Derive B_r, B_phi, B_z and the CND field strength, and a mass accretion rate**: WK scalings B_phi/B0 = -alpha z/r, B_r/B0 = beta z/r, B_z = f_z B0 with z/r = 0.08, then the 3D field and the accretion rate from WK Eq. 5.3  
  > "Analysis based on the WK model further allows us to derive representative $\vec{B}$-field strengths for the radial, azimuthal, and vertical components as" (abstract); "B_{\rm CND}^{3D} \simeq 0.8 \pm 0.3 \,{\rm mG}." (4.1.2 B-field strength)
   - parameter: z/r = 0.08 with about 30% uncertainty; f_z = 1.0  
  > "with an uncertainty of approximately 30%" (3.3.2 Analysis of Magnetic-field Structure)
   - assumption: Thin disk, fiducial WK structure with z << r  
  > "thereby satisfying the thin-disk approximation" (3.3.2 Analysis of Magnetic-field Structure)
   - fitting: _not stated_
   - validation: Compared with the plane-of-sky estimate of Guerra et al. and an OH Zeeman measurement  
  > "as derived by (cite: gue23) (see their Table 5)" (4.1.2 B-field strength)
9. **Apply the DCF method to the model residuals**: Original DCF equipartition formula B = sqrt(4 pi rho) sigma_nth / sigma_phi with sigma_phi from the MAD_stat of the gc1 residuals; Q = 1 gives an upper limit  
  > "The $\sigma_{\phi}$ value is derived from the MAD$_{\rm stat}$ of the residual for the gc1 model" (4.1.3 DCF); "By selecting $Q = 1.0$" (4.1.3 DCF)
   - parameter: rho = 1.0e-18 g cm^-3, sigma_nth = 21 km/s, sigma_phi = 0.105 rad (Tsuboi et al.); alternative rho = 8.9e-20 g cm^-3, sigma_nth = 35 km/s (Guerra et al.)  
  > "we derive a tighter constraint for $B_{\rm CND}^{\rm pos} \lesssim 35\,\mathrm{mG}$" (4.1.3 DCF)
   - assumption: Equipartition between turbulent kinetic and magnetic energy  
  > "we advocate for the use of the original DCF formula" (4.1.3 DCF)
   - fitting: _not stated_
   - validation: Authors conclude the method gives no meaningful constraint  
  > "Consequently, we ascertain that the DCF method does not provide meaningful constraints on the plane-of-sky component of the" (4.1.3 DCF)
10. **Estimate the plasma beta (naive and effective)**: beta = 2 (c_iso/V_A)^2 with V_A = B_CND(3D)/sqrt(4 pi rho); effective beta adds turbulent velocity dispersion to c_iso  
  > "The value of $V_{\rm A} = \frac{B_{\rm CND}^{\rm 3D}}{\sqrt{4\pi \rho}}$ is estimated using the" (4.2.2 Plasma beta)
   - parameter: c_iso from geometric mean of 200 K (CS LVG) and 63 K (H2CO); rho from n = (2.2 +/- 1.4)e5 cm^-3; sigma_nth = 9.96 km/s for the upper limit  
  > "we selected the smallest estimate of $\sigma_{\rm nth} =$ 9.96 km s$^{-1}$ by (cite: hen16)" (4.2.2 Plasma beta)
   - assumption: Effective sound speed assumes an isotropic velocity field  
  > "we describe a potential caveat regarding the use of the effective sound speed, which implicitly assumes an isotropic velocity field" (4.2.2 Plasma beta)
   - fitting: _not stated_
   - validation: Compared with the plasma beta of Hsieh et al. 2018  
  > "although their Eq.(5) omits the factor of 2" (4.2.2 Plasma beta)
11. **Test the MRI criterion lambda_max < scale height H**: lambda_max = (8 pi / sqrt(15)) V_A / Omega with V_A from B_z; compare with H_iso, H_eff and H_obs; probability that H > lambda_max from normal distributions  
  > "assuming both $\lambda_{\rm max}$ and $H$ follow normal distributions, with uncertainties represented as $1\sigma$ errors." (4.2.3 MRI)
   - parameter: Keplerian v about 90 km/s at 2.2 pc vs observed v_phi0 = 105 km/s; z_half = 0.41 +/- 0.08 pc  
  > "yielding $z_{\rm half} = 0.41 \pm 0.08$ pc" (4.2.3 MRI)
   - assumption: CND initially threaded by a vertical field, so B_z is used; Keplerian rotation assumed  
  > "The selection of $B_z$ is predicated on the assumption that the CND was initially threaded by a vertical $\vec{B}$ field" (4.2.3 MRI)
   - fitting: Error propagation by partial derivatives of lambda_max  
  > "with the standard error in $\lambda_{\rm max}$ calculated from its variance via" (4.2.3 MRI)
   - validation: Additional stability parameters Q_phi and Q_z compared with published MRI regions in Appendix  
  > "the instability we observe for the CND is clearly within the MRI region" (Appendix A)

## Software

- **CASA (ALMA pipeline)** v5.1.1-5: Calibration of the Cycle 5 ALMA visibilities  
  > "calibrated the visibility data using the Common Astronomy Software Applications (CASA v5.1.1-5) pipeline" (2.2 ALMA CS data)
- **CASA (concat, tclean, feather)** v6.4: Combine 12 m and 7 m visibilities, deconvolve, and feather with Total Power  
  > "tasks in CASA (v6.4) with a Briggs robust parameter of 0.5" (2.2 ALMA CS data)
- **Starlink SMURF (pol2map)** pipeline version dated July 23, 2021: Reduction of the JCMT POL-2 data into Stokes I, Q, U  
  > "which is implemented in the SMURF package of the Starlink suite (cite: cha13)" (2.1 JCMT polarization data); "We followed the standard pipeline (version dated July 23, 2021) as described in, e.g., (cite: war17)." (2.1 JCMT polarization data)
- **Astropy** : Used in the research; specific use not stated  
  > "This research used the Astropy Suite (Astropy Collaboration 2013, 2018)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I noise level of the 850 um map | 15.8 | not stated | mJy arcsec^-2 | 1 | We estimate that the resultant Stokes $I$ map has achieved a noise level of 15.8 mJy arcsec$^{-2}$ with a 4.0$''$-pixel size |
| Area enclosed by the 20 sigma 37.1 um contour | 7750 arcsec^2 (12.2 pc^2) | not stated | arcsec^2 | 2 | We measure the area, $A$, enclosed by the contour to be 7750 arcsec$^2$, corresponding to $A = 12.2$ pc$^{-2}$. |
| Effective radius R_eff of the CND | 2.0 | not stated | pc | 2 | yields an effective radius $R_{\rm eff}$ of 2.0 pc |
| Inner slope of polarization fraction vs radius (0.5-2.0 pc) | +0.56 | 0.26 | percent pc^-1 | 3 | is characterized by a slope of ${\rm d}P_{850}/{\rm d}r_{\rm pos} = +0.56\pm0.26$ percent pc$^{-1}$ |
| Outer slope of polarization fraction vs radius | -1.0 | 0.42 | percent pc^-1 | 3 | may have a steeper slope of ${\rm d}P_{850}/{\rm d}r_{\rm pos} = -1.0\pm 0.42$ percent pc$^{-1}$ |
| CND rotational velocity | 105 | not stated | km/s | 5 | we derived a value of 105 km s$^{-1}$, along with other geometrical parameters, aligning with previous studies |
| Inner cavity radius r_cav(3D) | 2.2 | not stated | pc | 5 | set a radius of the inner cavity $r_{\rm cav}^{\rm 3D} \simeq 2.2$ pc |
| 3D CND radius R_eff(3D) | 5.0 | not stated | pc | 5 | yielding a 3-dimensional CND radius of $R_{\rm eff}^{\rm 3D} \simeq 5.0$ pc |
| Number of polarization segments used in the model comparison | 51 | not stated | dimensionless | 6 | resulting in a total of $n=51$ segments for analysis. |
| chi-square of the gc1 model fit | 29.8 | not stated | deg^2 | 6 | 29.8 |
| MAD_stat of the gc1 residuals | 6.0 | 3.2 | deg | 6 | 6.0$\pm$3.2 |
| Weighted-mean midplane B-field strength |B0(3D)| | 0.24 | +0.05/-0.04 | mG | 7 | we also presented the weighted-mean strength of $0.24^{+0.05}_{-0.04}$ mG calculated for the gc1, 2, and 3 models |
| B_r, B_phi, B_z in the CND | (0.4, -0.7, 0.2) | (0.1, 0.2, 0.05) | mG | 8 | $(B_r, B_\phi, B_z) = (0.4 \pm 0.1, -0.7 \pm 0.2, 0.2 \pm 0.05)$ mG |
| 3D B-field strength of the CND | 0.8 | 0.3 | mG | 8 | B_{\rm CND}^{3D} \simeq 0.8 \pm 0.3 \,{\rm mG}. |
| Mass accretion rate to the SMBH | 1e-2 | not stated | Msun/yr | 8 | considering the estimated mass accretion rate of $10^{-2} M_{\odot}$ yr$^{-1}$ to the SMBH |
| DCF plane-of-sky field upper limit (Tsuboi et al. rho and sigma_nth) | 72 | not stated | mG | 9 | B_{\rm CND}^{\rm pos} \lesssim 72\,\mathrm{mG} |
| DCF plane-of-sky field upper limit (Guerra et al. rho and sigma_nth) | 35 | not stated | mG | 9 | we derive a tighter constraint for $B_{\rm CND}^{\rm pos} \lesssim 35\,\mathrm{mG}$ |
| Alfven velocity and isothermal sound speed | V_A = 2.2, c_iso = 0.63 | 0.9, 0.48 | km/s | 10 | $2.2 \pm 0.9$ km s$^{-1}$, exceeds the isothermal sound speed of $0.63 \pm 0.48$ km s$^{-1}$ |
| Naive plasma beta | 0.2 | 0.1 | dimensionless | 10 | The naive estimation of ${\beta_{\rm Plasma}^{\rm na\acute{i}ve}} \simeq 0.2 \pm 0.1$ implies that magnetic pressure dominates over gas pressure. |
| Effective plasma beta upper limit | <~ 40 | not stated | dimensionless | 10 | we obtained an effective $\beta_{\rm Plasma}^{\rm eff} \lesssim 40$ |
| Maximum unstable MRI wavelength lambda_max | 0.1 | 0.1 | pc | 11 | The estimated maximum unstable wavelength, $\lambda_{\rm max} = 0.1 \pm 0.1$ pc, is smaller than the CND |
| Observed scale height H_obs and probability H_obs > lambda_max | 0.22 pc, 82% | 0.07 pc | pc | 11 | $H_{\rm obs} \simeq 0.22 \pm 0.07$ pc, exceeding $\lambda_{\rm max} \simeq 0.090^{+0.12}_{-0.10}$ pc (82% probability) |
| Effective scale height H_eff and probability H_eff > lambda_max | 0.21 pc, 75% | 0.12 pc | pc | 11 | $H_{\rm eff} \simeq 0.21 \pm 0.12$ pc, surpassing $\lambda_{\rm max} \simeq 0.090^{+0.12}_{-0.10}$ pc (75% probability) |
| Isothermal scale height H_iso and probability H_iso > lambda_max | 0.013 pc, 26% | 0.008 pc | pc | 11 | $H_{\rm iso} \simeq 0.013 \pm 0.008$ pc, greater than $\lambda_{\rm max} \simeq 0.090^{+0.12}_{-0.10}$ pc (26% probability) |

## Qualitative findings

- The 850 um emission principally traces the CND, with contamination from the Minispiral to the southwest  
  > "In conclusion, we argue that the $\lambda=$ 850 $\mu$m observations principally trace the CND with contamination from the Minispiral to the southwest." (3.1.1 Morphological comparisons)
- All WK models fail to reproduce the observed angles in subregion A  
  > "are unable to replicate the observed angles in the Subregion A identified in the CS line velocity field analysis" (3.3.2 Analysis of Magnetic-field Structure)
- The CS emission has complicated spectra with multiple components and absorption, so CS is used only to define subregions  
  > "Consequently, we constrain our study to utilize the CS lines to define the subregions." (3.2.3 Spectra)

## Claim tuples

- H: Is the CND B-field consistent with an accretion-disk model with open field lines? | E: Compared 51 observed 850 um B-field position angles with the five WK models using chi-square and MAD_stat of residuals | R: gc1, gc2 and gc3 give comparable, lower chi-square than gc4 and gc5; gc1 has the smallest MAD_stat | F: The field shows a coherent spiral pattern favoring gas-pressure-dominant models without excluding a comparable gas and field model | **supported**
- H: Is the CND field predominantly toroidal? | E: Scaled WK components from B0 and z/r to obtain B_r, B_phi, B_z | R: B_r = 0.4, B_phi = -0.7, B_z = 0.2 mG | F: The toroidal component dominates | **supported**
- H: Can an effective MRI operate in the CND? | E: Compared lambda_max with three scale-height estimates and computed naive and effective plasma beta | R: Naive beta about 0.2, effective beta <~ 40, H_obs and H_eff exceed lambda_max with 82% and 75% probability, H_iso only 26% | F: An effective MRI may be active, but ideal MRI is insufficient to explain the field | **partially**
- H: Can the DCF method constrain the plane-of-sky field strength in the CND? | E: Applied the original DCF formula using the gc1 residual dispersion and densities and velocity dispersions from two sources | R: Upper limits of 72 mG and 35 mG | F: The DCF method does not give meaningful constraints on the plane-of-sky field | **refuted**
- H: Does the 850 um polarization fraction show a characteristic scale in the CND? | E: Radial profile of P_850 compared with the 37.1 um effective radius | R: P_850 rises to about 2.0 pc then falls, matching R_eff = 2.0 pc | F: r of about 2.0 pc is a characteristic CND scale | **partially**

## Reasoning

- Why this data: Archival JCMT polarization data were chosen for the scientific goals, with ALMA CS, VLA and SOFIA data used to interpret them  
  > "Given the scientific goals, we generated polarization images using two archival data sets acquired from the James Clerk Maxwell Telescope" (2 Data Retrieval); "To interpret the data from JCMT, we utilized molecular line data from the archive of the Atacama Large Millimeter/submillimeter Array" (2 Data Retrieval)
- Why this method: Only the CS J=2-1 line was analyzed because the focus is the JCMT polarimetry  
  > "As the focus of this paper is on the results from the polarimetric observations at JCMT, we limited our analysis to the sole CS" (2.2 ALMA CS data)
- Alternative: Modified DCF of Guerra et al. (shear flow) not adopted; original DCF formula used  
  > "we note that the estimated values might be subject to systematic errors due to uncertainties in gas density and possibly velocity dispersion" (4.1.3 DCF); "Consequently, we advocate for the use of the original DCF formula" (4.1.3 DCF)
- Alternative: Small-beta WK models gc4 and gc5 judged not locally applicable  
  > "we deduce that the small-$\beta$ models (gc4 and 5) are not locally applicable" (4.2.1 Role of B)
- How they decided it was enough: _not stated_
- Limitation (authors): CS spectra have multiple components and absorption, limiting physical quantities  
  > "These spectra present non-negligible caveats for deriving meaningful physical quantities due to the presence of multiple components and absorption features." (3.2.3 Spectra)
- Limitation (authors): Applying DCF to the CND has significant limitations  
  > "We emphasize significant limitations in applying the DCF method to the CND." (4.1.3 DCF)
- Limitation (authors): Gas properties at the Galactic Center are hard to estimate because of distance and line-of-sight contamination  
  > "Estimating gas properties in the Galactic Center region is fundamentally challenging due to the 8 kpc distance and line-of-sight contamination." (1.2 Galactic Center)
- Limitation (authors): Effective sound speed assumes an isotropic velocity field  
  > "we describe a potential caveat regarding the use of the effective sound speed, which implicitly assumes an isotropic velocity field" (4.2.2 Plasma beta)
- Caveat (inferred, ours): Key field strengths rest on WK fiducial parameters and an assumed density (2.5e3 cm^-3) and z/r = 0.08, so the quoted B uncertainties are likely underestimated
- Caveat (inferred, ours): Only one WK parameter (phi) is fitted and chi-square differences among gc1-gc3 are small, so model preference is weak
- Caveat (inferred, ours): 850 um polarization is partly synchrotron-contaminated and line-of-sight averaged, and the CS gas may not trace the same material as the dust
- Caveat (inferred, ours): ALMA data play only a velocity-selection role, and the combination and imaging details are thin

## Reproducibility

- Data public (paper): All datasets retrieved from public archives  
  > "All the data were retrieved from the archive." (Table 1 caption)
- Products in archive: VLA and SOFIA images are already-reduced archive products; ALMA and JCMT data were reduced by the authors  
  > "From the NRAO data archive, we retrieved the already-reduced image taken in the" (2.3 VLA and SOFIA data); "The ALMA images reproduced by us were obtained by combining visibility data from three arrays" (Table 1 caption)
- Missing: No code released; WK model implementation and polarization segment table handling must be rewritten
- Missing: pol2map parameters and ALMA clean parameters (threshold, masks, cell and image size) are missing
- Missing: Selection of the four excluded segments and exact plan of how vectors were binned
- Data volume (inferred): About 50-100 GB raw for the ALMA 12 m, 7 m and TP data plus tens of GB for the 29 JCMT POL-2 exposures; the VLA and SOFIA images are small reduced products
- Score (inferred): 2/5, Data are public and the WK analysis is described with equations and a result table, but the ALMA imaging and JCMT reduction settings are only partly given and no code is released
- Rediscovery candidate: no, ALMA is a minor ancillary dataset and the recipe lacks key imaging and map-reduction settings, so the main numeric results cannot be reproduced from the text alone

## Links

- Method: Wardle & Koenigl 1990 (cite: war90) (WK magnetized-disk model used for the B-field comparison and field strength estimates)
- Method: Mairs et al. 2021 (cite: mai21) (JCMT beam size and flux-conversion factor)
- Method: Ward-Thompson et al. 2017 (cite: war17) (Standard POL-2 reduction pipeline followed)
- Method: Guerra et al. 2023 (cite: gue23) (Modified DCF method and plasma beta approach)
- Companion: Tsuboi et al. 2018 (cite: tsu18) (Original ALMA CS data analysis and LVG density and temperature used here)
- Companion: Hsieh et al. 2018, 2019 (cite: Hsieh2018; Hsieh2019) (Earlier SCUPOL 850 um polarization analysis of the CND)
- Related: JCMT proposals M16BP061 and M17AP074
- Related: SOFIA FORCAST Galactic Center Legacy Project (07-0189)
- Related: VLA project AZ44

## Checks

```json
{
 "quotes": 164,
 "quotes_ok": 164,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 132,
  "stated": 100,
  "rate": 0.758
 },
 "evidence_ok": true
}
```
