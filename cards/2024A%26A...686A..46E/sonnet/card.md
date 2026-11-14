# AGN feedback in the Local Universe: Multiphase outflow of the Seyfert galaxy NGC 5506

`2024A&A...686A..46E` | Astronomy and Astrophysics 2024 | first author: Esposito, Federico | arXiv: 2403.03981 | DOI: 10.1051/0004-6361/202449245

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How do the molecular (ALMA CO(3-2)) and ionised ([OIII], GTC/MEGARA) outflow phases of the Seyfert galaxy NGC 5506 compare, and how do they couple to the disc?  
  > "In this study, we investigate the molecular and ionised gas phases of NGC 5506, an Sa spiral galaxy in the GATOS sample" (Introduction)
- Target **NGC 5506**: coordinates RA 14h13m14.877s, Dec -03d12m27.67s (J2000)  
  > "at a redshift-independent distance of 26 Mpc (cite: karachentsev06). At this distance the spatial scale is $125$ pc/$\ensuremath{''}$." (Introduction); "$\alpha_{2000} = 
14^{\text{h}}13^{\text{m}}14.877^{\text{s}}$, $\delta_{2000} = -03^{\circ}12\ensuremath{'} 27.67\ensuremath{''}$" (2.1 ALMA Band 7); z/distance 26 Mpc (1" = 125 pc)  
  > "at a redshift-independent distance of 26 Mpc (cite: karachentsev06). At this distance the spatial scale is $125$ pc/$\ensuremath{''}$." (Introduction); "$\alpha_{2000} = 
14^{\text{h}}13^{\text{m}}14.877^{\text{s}}$, $\delta_{2000} = -03^{\circ}12\ensuremath{'} 27.67\ensuremath{''}$" (2.1 ALMA Band 7); distance from Karachentsev et al. 2006 (redshift-independent)  
  > "at a redshift-independent distance of 26 Mpc (cite: karachentsev06). At this distance the spatial scale is $125$ pc/$\ensuremath{''}$." (Introduction); "$\alpha_{2000} = 
14^{\text{h}}13^{\text{m}}14.877^{\text{s}}$, $\delta_{2000} = -03^{\circ}12\ensuremath{'} 27.67\ensuremath{''}$" (2.1 ALMA Band 7)

## Data provenance

- ALMA projects: 2017.1.00082.S
- bands: Band 7 (870 um continuum), CO(3-2)  
  > "We observed NGC 5506 with the Band 7 ALMA receiver and a single pointing" (2.1 ALMA Band 7)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.21" x 0.13" (26 x 16 pc), PA = -60 deg  
  > "The datacube has a $0.21 \ensuremath{''} \times 0.13 \ensuremath{''}$ (26 pc $\times$ 16 pc) beam (with PA $=-60^{\circ}$" (2.1 ALMA Band 7)
- max recoverable scale: 4" (0.5 kpc) largest angular scale; 17" FoV  
  > "a $17 \ensuremath{''}$ (2.1 kpc) field of view (FoV) and a largest angular scale of $4 \ensuremath{''}$ (0.5 kpc)" (2.1 ALMA Band 7)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI S. García-Burillo; moderate-resolution cube from García-Burillo et al. 2021  
  > "We analysed the moderate resolution datacube from (cite: garciaburillo21)." (2.1 ALMA Band 7)
- Line: CO J=3-2 (not stated)
- Other facility **GTC/MEGARA IFU**: Optical IFU spectroscopy (LR-B, LR-R) of Hbeta, [OIII], Halpha, [NII], [SII], [OI]; observed 20/03/2021  
  > "We observed the central region of NGC 5506 on 20/03/2021 (Program GTC27-19B; PI: A. Alonso-Herrero), with MEGARA in IFU mode" (2.2 GTC/MEGARA Bands B and R)
- Other facility **HST**: F606W image used for astrometry and comparison  
  > "we first aligned the HST/F606W image (top panel of Fig. [1](#fig:ngc5506)) with the position of stars (from the Gaia mission)" (2.1 ALMA Band 7)
- Other facility **VLA (literature)**: 8.46 GHz A-array image from Schmitt et al. 2001 compared with outflow map  
  > "In Fig. [19](#fig:ion_MOR_VLA) we plot the contours of (cite: schmitt01) VLA image against the ionised mass outflow rate map" (6.3 Extending the spectrum)
- External data: ALMA CO(3-2) moderate-resolution datacube and continuum/HST aligned position  
  > "We analysed the moderate resolution datacube from (cite: garciaburillo21)." (2.1 ALMA Band 7) [from (cite: garciaburillo21)]
- External data: Black hole mass 2.0e7 Msun  
  > "The black hole mass is $M_{\rm BH} = 2.0^{+8.0}_{-1.6} \times 10^7$ M$_{\odot}$ (cite: gofford15)" (Introduction) [from (cite: gofford15)]
- External data: log Lbol = 44.1 +/- 0.09 from X-ray luminosity  
  > "$\log (L_{\text{bol}} / \text{erg s}^{-1})
= 44.1 \pm 0.09$ obtained by (cite: davies20) from the X-ray luminosity given by (cite: ricci17)" (5.3 The [OIII] outflow mass) [from (cite: davies20); (cite: ricci17)]
- External data: Average CO(3-2)/CO(1-0) brightness temperature ratio r31 = 0.7  
  > "this is the average value found by (cite: israel20) in 126 nearby galaxy centres" (4.3 The molecular mass outflow rate) [from (cite: israel20)]
- External data: logU empirical relation and effective line emissivity table  
  > "We interpolated the values listed in (cite: baron19), Table 2, to calculate $\gamma_{\text{[OIII]}}$ for every spaxel." (5.3 The [OIII] outflow mass) [from (cite: baron19)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used the previously published moderate-resolution datacube from García-Burillo et al. 2021  
  > "We analysed the moderate resolution datacube from (cite: garciaburillo21)." (2.1 ALMA Band 7)
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
- final beam: 0.21" x 0.13" (PA -60 deg)  
  > "The datacube has a $0.21 \ensuremath{''} \times 0.13 \ensuremath{''}$ (26 pc $\times$ 16 pc) beam" (2.1 ALMA Band 7)
- final rms: _not stated_

### Inherited from earlier work

- ALMA datacube production (calibration, imaging) and astrometry alignment  
  > "We analysed the moderate resolution datacube from (cite: garciaburillo21)." (2.1 ALMA Band 7) [from (cite: garciaburillo21)]
- MEGARA data reduction  
  > "The data reduction was performed by following (cite: peraltadearriba23) and using the official MEGARA pipeline (cite: pascual21)." (2.2 GTC/MEGARA Bands B and R) [from (cite: peraltadearriba23); (cite: pascual21)]
- Non-parametric velocity method (percentiles)  
  > "We followed the method described by (cite: harrison14) to spatially resolve the velocities of the [OIII] emission line." (5.2 Non-parametric [OIII] velocities) [from (cite: harrison14)]
- Ionised density/mass method via ionisation parameter  
  > "We follow (cite: baron19), (cite: davies20), and (cite: peraltadearriba23), in estimating the ionised gas density from the ionisation parameter $\log U$" (5.3 The [OIII] outflow mass) [from (cite: baron19); (cite: davies20); (cite: peraltadearriba23)]
- r31=0.7 adopted for consistency  
  > "we adopt it for consistency with (cite: garciaburillo21)" (4.3 The molecular mass outflow rate) [from (cite: garciaburillo21)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, pipeline/CASA versions, imaging parameters (robust, channel width, rms) of the datacube (in García-Burillo+2021)
- Observing dates, configurations, and time on source for ALMA
- 3DBarolo settings: mask/threshold, normalisation type, fitting function, version
- Which CO moment/flux integration and region used for M_out; how CO(3-2) flux converted to mass numerically
- ALUCINE settings (continuum windows, AoN handling, constraints on Gaussian widths)
- Criterion separating narrow vs broad Gaussians
- Definition of the deprojected radius for the molecular rings

## Analysis recipe

1. **Kinematic model of CO disc**: 3DBarolo ring fits, first with vrad=0 then with free vrad  
  > "We modelled the CO($3-2$) datacube with ^3D^BAROLO[^2] (cite: diteodoro15), which creates a disc model for the rotating gas by dividing the emission into concentric rings" (4 Modelling the molecular gas kinematics)
   - software: 3DBarolo
   - parameter: 0.15" (~19 pc) rings, 60 rings, centre fixed at continuum peak  
  > "We set a ring radial size of $0.15 \ensuremath{''}$ ($\simeq 19$ pc), similar to the ALMA beam ($0.21 \ensuremath{''} \times 0.13 \ensuremath{''}$), and a total of 60 rings" (4 Modelling the molecular gas kinematics)
   - assumption: Outflow velocities are upper limits because bar elliptical motions possible  
  > "we conservatively assume that the outflow velocities we derive between $R_{out,min}^{\rm mol} = 0.4 \ensuremath{''}$ (50 pc) and $R_{out,max}^{\rm mol} = 5 \ensuremath{''}$ (610 pc) are upper limits" (4.2 Rotating disc with a radial velocity component)
   - fitting: _not stated_
   - validation: Compared PV diagrams and mean velocities along minor axis for models with and without vrad; vsys compared with literature  
  > "Fig. [6](#fig:barolo_PV) shows the PV diagrams of this run, where we can appreciate a better fit along the minor axis" (4.2 Rotating disc with a radial velocity component)
2. **Molecular outflow mass and rate**: CO(3-2) converted to CO(1-0) with r31, then Galactic X_CO; Mdot = M v / R (shell geometry)  
  > "Assuming a simple shell geometry (cite: alonsoherrero23), we can write the mass outflow rate as" (4.3 The molecular mass outflow rate)
   - parameter: r31 = 0.7; X_CO = 2e20 mol cm-2 (K km/s)-1; between 0.4" and 5"  
  > "a Galactic CO-to-H$_2$ conversion factor of $X_{\rm CO} = 2 \times 10^{20}$ mol cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (4.3 The molecular mass outflow rate)
   - assumption: Galactic X_CO since no merger and not IR luminous; helium included  
  > "because NGC 5506 does not show any indication of merger and is not particularly luminous in the infrared" (4.3 The molecular mass outflow rate)
   - fitting: _not stated_
   - validation: Uncertainty range explored with r31=0.4-1 and X_CO=(0.8-2)e20  
  > "we plotted errorbars in Fig. [9](#fig:mol_MOR) corresponding to the typical ranges $r_{31} = 0.4 - 1$" (4.3 The molecular mass outflow rate)
3. **Fit MEGARA lines with Gaussians**: Spaxel-by-spaxel ALUCINE fit with 1 or 2 Gaussians, AoN>3; broad = outflow, narrow = rotation  
  > "The ALUCINE code determines, based on the AoN $>3$ cut, whether one or two Gaussians are necessary for each spaxel." (5.1 Gaussian decomposition)
   - software: ALUCINE
   - parameter: vsys input 1893 km/s for [OIII]  
  > "we achieved better results by setting $v_{sys, \text{[OIII]}}=1893$ km s$^{-1}$" (5.1 Gaussian decomposition)
   - fitting: _not stated_
   - validation: Residual maps (Appendix)  
  > "See Fig. [21](#fig:residuals)." (Goodness of ALUCINE fit)
4. **Non-parametric [OIII] velocities**: Percentile velocities (v02..v98, W80, Δv) from sum of two Gaussians per spaxel  
  > "For every spaxel we calculate the velocities corresponding to different percentiles to the flux contained in the modelled line profile" (5.2 Non-parametric [OIII] velocities)
   - fitting: _not stated_
   - validation: _not stated_
5. **Ionised outflow mass and rate**: logU from Baron & Netzer 2019 line-ratio relation -> n_e; extinction-corrected broad [OIII] luminosity; M = mu m_H L/(gamma n_e); Mdot = M v/R  
  > "Finally, the ionised outflow mass $M_{\rm out}^{\rm ion}$ is given by (cite: rose18; baron19):" (5.3 The [OIII] outflow mass)
   - parameter: Cardelli extinction law, R_V=3.1; intrinsic Ha/Hb=3.1; mu=1.4; central pixel r = half pixel size  
  > "we assume an intrinsic ratio $H \alpha / H \beta = 3.1$, and we use the (cite: cardelli89) extinction law ($R_V = 3.1$)" (5.3 The [OIII] outflow mass)
   - assumption: Broad component is outflow; n_H ~ n_e  
  > "we consider the flux of the broad component as the outflow (whereas the narrow component is associated to the ordered gas rotation)" (5.3 The [OIII] outflow mass)
   - fitting: _not stated_
   - validation: Compared logU, n_e, L[OIII] with Davies et al. 2020 X-shooter values  
  > "We recover a median value of $\log U = -2.9$, in agreement with the integrated value of $-2.87 \pm 0.12$ found by (cite: davies20)" (5.3 The [OIII] outflow mass)
6. **Compare phases**: Energy and momentum rates (E=Mdot v^2/2, P=Mdot v); overlay of Mdot_ion on CO dispersion; compare with radio/X-ray literature  
  > "These two quantities can be straightforwardly calculated as $\dot{E}_{\rm out} = \dot{M}_{\rm out} v_{\rm out}^2 / 2$ and $\dot{P}_{\rm out} = \dot{M}_{\rm out} v_{\rm out}$." (6.2 Comparing molecular and ionised outflows)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **3DBarolo** : Tilted-ring kinematic modelling of CO(3-2) cube  
  > "We modelled the CO($3-2$) datacube with ^3D^BAROLO[^2] (cite: diteodoro15)" (4 Modelling the molecular gas kinematics)
- **ALUCINE** : Gaussian fitting of MEGARA emission lines  
  > "we extracted and fitted every spaxel of the MEGARA FoV with the ALUCINE[^1] (cite: peraltadearriba23)" (3.2 GTC/MEGARA emission lines)
- **MEGARA DRP (megaradrp)** v0.11: MEGARA data reduction  
  > "using the official MEGARA pipeline (cite: pascual21)" (2.2 GTC/MEGARA Bands B and R)
- **pvextractor** : PV diagrams (acknowledged)  
  > "pvextractor (cite: pvextractor)" (Acknowledgements)
- **SpectralCube** v0.4.4: cube handling (acknowledged)  
  > "and SpectralCube (cite: spectralcube)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO systemic velocity | 1872 | 10 | km/s | 1 | $v_{\rm sys}=1872 \pm 10$ km s$^{-1}$ |
| CO disc inclination and PA | i=80, PA=265 | not stated | deg | 1 | $i=80^{\circ}$, PA $=265^{\circ}$ |
| CO rotation velocity plateau | 193 at r=3.5" (440 pc) | not stated | km/s | 1 | We find $v_{\rm rot}$ reaching $193$ km s$^{-1}$ at $r = 3.5 \ensuremath{''}$ (440 pc) |
| Molecular outflowing mass | 1.75e8 | factor ~0.28 to ~1.75 | Msun | 2 | We calculate $M_{\rm out}^{\rm mol} = 1.75 \times 10^8$ M$_{\odot}$ |
| Mean molecular outflow velocity | 25.6 | 9.4 | km/s | 2 | we find $v_{\rm out}^{\rm mol} = 25.6 \pm 9.4$ km s$^{-1}$ |
| Molecular mass outflow rate | 8 | 3 | Msun/yr | 2 | $\dot{M}_{\rm out}^{\rm mol} = 8 \pm 3$ M$_{\odot}$ yr$^{-1}$ |
| Peak molecular mass outflow rate | 28 | not stated | Msun/yr | 2 | up to $\dot{M}_{out,max}^{\rm mol} = 28$ M$_{\odot}$ yr$^{-1}$ |
| Median logU of broad [OIII] | -2.9 | not stated | dimensionless | 5 | We recover a median value of $\log U = -2.9$ |
| Max electron density | 8.5e5 | not stated | cm-3 | 5 | The maximum $n_{e, \text{max}} = 8.5 \times 10^5$ cm$^{-3}$ is exactly at the AGN position. |
| Ionised outflow mass | 9.8e4 | not stated | Msun | 5 | We calculated a total ionised outflowing mass of $M_{\rm out}^{\rm ion} = 9.8 \times 10^4$ M$_{\odot}$. |
| Ionised outflow velocity (R=525 pc) | 422 | 97 | km/s | 5 | we find $v_{\rm out}^{\rm ion} = 422 \pm 97$ km s$^{-1}$ |
| Ionised mass outflow rate | 0.076 | 0.017 | Msun/yr | 5 | $\dot{M}_{\rm out}^{\rm ion} = 0.076 \pm 0.017$ M$_{\odot}$ yr$^{-1}$ |
| Max W80 | 826 | not stated | km/s | 4 | The maximum value observed is $W_{80, max} = 826$ km s$^{-1}$ located $\sim 6 \ensuremath{''}$ W. |
| Momentum rate ratio mol/ion | 7 | not stated | dimensionless | 6 | which in our case is $\dot{P}_{\rm mol} / \dot{P}_{\rm ion} = 7$ |

## Qualitative findings

- BPT diagrams show AGN-dominated excitation in both narrow and broad components  
  > "we can conclude that most of the observed central emission is due to the AGN activity rather than star formation, both for the narrow and broad components." (5.1 Gaussian decomposition)
- Ionised gas rotates slower than molecular gas (~60%)  
  > "Interestingly, the ionised gas seems to be rotating at $60 \%$ the velocity of the molecular gas." (5.2 Non-parametric [OIII] velocities)

## Claim tuples

- H: Does the molecular disc of NGC 5506 host an outflow? | E: 3DBarolo model of CO(3-2) with radial velocity component | R: Mean outward vrad 25.6±9.4 km/s, Mdot_mol = 8±3 Msun/yr (upper limit) | F: Rotating and outflowing molecular ring, with possible inflow inside 0.4" | **partially**
- H: What is the ionised outflow rate? | E: Two-Gaussian decomposition, percentile velocities, logU density method | R: Mdot_ion = 0.076±0.017 Msun/yr, v=422±97 km/s within 525 pc | F: Ionised outflow is much weaker in mass rate than molecular | **supported**
- H: Are the two phases coupled? | E: Overlay of Mdot_ion map and CO dispersion | R: Spatial correlation with high CO dispersion | F: Weak coupling, ionised bicone partially intercepts the disc; multiple outflow episodes | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Galactic X_CO chosen for comparison with literature and no merger/IR luminosity  
  > "We chose the Galactic value to better compare our results with most of the literature" (4.3 The molecular mass outflow rate); "we limited our analysis to two components to have a simpler interpretation of them" (5.1 Gaussian decomposition)
- Alternative: Bar elliptical orbits as alternative for radial motion; treated molecular velocities as upper limits  
  > "or *(ii)* elliptical orbits associated with a bar" (4.2 Rotating disc with a radial velocity component)
- How they decided it was enough: _not stated_
- Limitation (authors): Molecular outflow quantities are upper limits due to possible bar  
  > "we cannot rule out the potential existence of a bar within the central kiloparsec." (6.1 The case for elliptical motions due to a bar)
- Limitation (authors): Inflow within 0.4" not confirmable (only two radial points)  
  > "but since we only have two radial points we could not confirm this finding" (4.2 Rotating disc with a radial velocity component)
- Caveat (inferred, ours): 3DBarolo radial velocity in a highly inclined (80 deg) disc is degenerate with non-circular motion
- Caveat (inferred, ours): Mdot assumes shell geometry and average velocity; r31 and X_CO uncertain
- Caveat (inferred, ours): No uncertainties propagated from fits; scatter used as error
- Caveat (inferred, ours): Ionised outflow area limited by Hbeta broad component

## Reproducibility

- Data public (paper): ALMA project ID given; GTC program ID given  
  > "(project-ID: #2017.1.00082.S; PI: S. García-Burillo)" (2.1 ALMA Band 7)
- Products in archive: _not stated_
- Code: ALUCINE available at GitLab; 3DBarolo public  
  > "Available at <https://gitlab.com/lperalta_ast/alucine>" (footnote 1)
- Missing: Original calibrated ALMA cube processing details
- Missing: MEGARA raw data access/status
- Missing: 3DBarolo and ALUCINE parameter files
- Data volume (inferred): ALMA: a few GB for one Band 7 project; processed cube <1 GB
- Score (inferred): 3/5, Public ALMA data and clear formulae, but cube production and fit settings are inherited or unstated, and MEGARA data also needed.
- Rediscovery candidate: no, Requires MEGARA data and unstated 3DBarolo/ALUCINE settings; ALMA cube from previous paper.

## Links

- Method: (cite: diteodoro15) (3DBarolo)
- Method: (cite: peraltadearriba23) (ALUCINE and MEGARA reduction)
- Method: (cite: baron19) (logU density and outflow mass method)
- Method: (cite: harrison14) (non-parametric velocities)
- Companion: (cite: garciaburillo21) (Source of the ALMA CO(3-2) datacube)
- Companion: (cite: davies20) (X-shooter study of NGC 5506 ionised outflow)
- Related: GATOS

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 53,
  "rate": 0.576
 },
 "evidence_ok": true
}
```
