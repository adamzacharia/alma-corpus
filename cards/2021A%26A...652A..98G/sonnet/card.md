# The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies

`2021A&A...652A..98G` | Astronomy and Astrophysics 2021 | first author: García-Burillo, S. | arXiv: 2104.10227 | DOI: 10.1051/0004-6361/202141075

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What are the sizes, orientations, masses and gas properties of dusty molecular tori in nearby Seyferts, and does AGN feedback leave an imprint on the radial distribution of molecular gas?  
  > "We imaged with ALMA the emission of molecular gas and dust in the CND of our targets using the CO(3–2) and HCO$^+$(4–3) lines and their underlying continuum emission" (1 Introduction)
- Target **GATOS core sample (10 Seyferts: NGC 6300, 5643, 7314, 4388, 4941, 7213, 7582, 6814, 5506, 7465) plus NGC 1068, NGC 1365, NGC 3227**: coordinates Phase centers in Table 1 (e.g. NGC 6300 17:16:59.473 -62:49:13.98)  
  > "NGC6300 | 17:16:59.473 | -62:49:13.98 | 14.0" (Table 1); "Distances are median values of redshift-independent estimates from the Nasa Extragalactic Database (NED) after excluding select measurements from unreliable or outdated references" (Table 1 notes); z/distance 14.0-27.2 Mpc (Table 1)  
  > "NGC6300 | 17:16:59.473 | -62:49:13.98 | 14.0" (Table 1); "Distances are median values of redshift-independent estimates from the Nasa Extragalactic Database (NED) after excluding select measurements from unreliable or outdated references" (Table 1 notes); distance from Median redshift-independent NED estimates  
  > "NGC6300 | 17:16:59.473 | -62:49:13.98 | 14.0" (Table 1); "Distances are median values of redshift-independent estimates from the Nasa Extragalactic Database (NED) after excluding select measurements from unreliable or outdated references" (Table 1 notes)

## Data provenance

- ALMA projects: 2017.1.00082.S, 2018.1.00113.S, 2016.1.00254.S
- bands: Band 7  
  > "with ALMA during Cycle 6 and 7 using band 7 receivers" (3.1 ALMA data)
- frequencies and spectral setup: Four 1.875 GHz spws (2 LSB, 2 USB); CO(3-2) 345.796 GHz, HCO+(4-3) 356.734 GHz; line cubes binned to 11.7 MHz (~10 km/s)  
  > "Four spectral windows of 1.875 GHz-bandwidth were placed, two in the lower side band (LSB) and two in the upper sideband (USB)." (3.1 ALMA data); "The line data cubes were binned to a common frequency resolution of 11.7 MHz (equivalent to $\sim$10 km s$^{-1}$ in band 7)." (3.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: Two configurations: extended (C43-6) and compact (C43-3), ~43-49 antennas  
  > "We combined two sets of configurations of the ALMA array: *extended* (C43-6) and *compact* (C43-3)." (3.1 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.1" (7-13 pc) common average; MSR/HSR beams in Table 2  
  > "using a common average angular resolution of $\sim0.1\ensuremath{''}$, which translates into a spatial scale $\sim7-13$ pc" (3.1 ALMA data)
- max recoverable scale: ~4" (300-500 pc)  
  > "the largest angular scale recovered in our maps is about $\sim4\ensuremath{''}=300-500$ pc" (3.1 ALMA data)
- sensitivity: Continuum 1σ ~23-60 μJy/beam; CO 0.42-0.65 mJy/beam per 10 km/s channel (Table 2)  
  > "Line sensitivities are derived for channels of 10 km s$^{-1}$-width (except for NGC 1068, where (cite: GB19) used 20 km s$^{-1}$-wide channels)." (Table 2 notes)
- time on source: _not stated_
- observing dates: December 2017 to August 2019  
  > "conducted between December 2017 and August 2019" (3.1 ALMA data)
- pi or archival as stated: PI S. García-Burillo for core sample; NGC 1068, NGC 1365, NGC 3227 data from previously published ALMA programs  
  > "For these galaxies there are ALMA data published by (cite: GB19) (NGC 1068), (cite: Alo19) (NGC 3227), and (cite: Com19) (NGC 1365)" (3.1 ALMA data)
- Line: CO J=3-2 (345.796 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Other facility **HST**: Optical and near-IR archival images for V-H colour maps  
  > "We downloaded fully reduced optical images from the Hubble Legacy Archive (HLA)[^5] taken with the WFPC2/PC instrument" (3.2 Ancillary data)
- Other facility **NuSTAR**: Hard X-ray spectra (3-70 keV) for 11 AGN to fit reflection component  
  > "finding observations for 11 AGN of our sample" (3.2 Ancillary data)
- Other facility **Swift/BAT**: Parent sample selection  
  > "we used the 70 month *Swift*/BAT $14-195\,$ keV all-sky catalog (cite: Bau13) to draw our parent sample from" (1 Introduction)
- External data: X-ray luminosities and column densities N_H(Xabs)  
  > "are taken from (cite: Ric17a)" (Table 1 notes) [from (cite: Ric17a)]
- External data: Eddington ratios  
  > "Eddington ratios ($\frac{L_{\rm AGN}}{L_{\rm Edd}}$) taken from (cite: Kos17)." (Table 1 notes) [from (cite: Kos17)]
- External data: Ionized outflow PA and opening angles  
  > "we adopt the orientation (major axis) and extent (opening angle) of the ionized winds in the galaxies of the core sample derived from the references listed in Appendix" (2 The sample) [from Appendix references; (cite: Das06), (cite: Alo19), (cite: Min19)]
- External data: 230 GHz continuum images of NGC 7582, NGC 5643, NGC 3227  
  > "we used the 230 GHz-continuum images of NGC 7582, NGC 5643 and NGC 3227, published by (cite: Alo18; Alo19; Alo20)" (4.3 Spectral index maps) [from (cite: Alo18; Alo19; Alo20)]
- External data: NUGA torus sizes and CO data  
  > "For sources of the NUGA sample we adopted the torus sizes published by (cite: Com19)." (8.1) [from (cite: Com19)]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; uv-tables exported to GILDAS  
  > "We calibrated the data making use of the ALMA reduction package `CASA` (cite: McM07)[^3]. The calibrated uv-tables were exported to `GILDAS`" (3.1 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10-15%  
  > "The flux accuracy is estimated to be about 10–15$\%$" (3.1 ALMA data)
- self calibration: _not stated_

### Imaging

- task: GILDAS UV-MAP  
  > "by changing in the `GILDAS` task `UV-MAP` the robust parameter ($b$) from 1" (3.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: robust = 1 (MSR) and 0.1 (HSR)  
  > "$robust=1$ (0.1) for the MSR (HSR) configuration" (Table 2 notes)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: GILDAS UV-BASELINE, polynomial degree zero in uv plane, line masked over ~300-600 km/s  
  > "We fitted a baseline to the $(u,v)$ data sets through a polynomial of degree zero masking the line emission around each transition with a range of velocity widths $\sim300-600$ km s$^{-1}$ adapted for each target" (3.1 ALMA data)
- line free channels: Velocity masks of 300-600 km/s adapted per target (exact channels not given)  
  > "making use of the same velocity width masks employed by the `UV-BASELINE` task" (3.1 ALMA data)
- primary beam correction: CO maps corrected for primary beam attenuation, 3σ clipping  
  > "The maps were derived using a 3$\sigma$ clipping on the emission extracted from the MSR dataset and corrected for primary beam attenuation." (5.1)
- array combination: Extended and compact configurations combined  
  > "We combined two sets of configurations of the ALMA array" (3.1 ALMA data)
- smoothing: _not stated_
- final beam: MSR/HSR beams per target listed in Table 2 (e.g. NGC 6300 0.13x0.10 / 0.11x0.08 arcsec)  
  > "Columns (5) and (6) list the range of spatial resolutions (in $\ensuremath{''}$ and pc) reached for the MSR and HSR observations respectively." (Table 2 notes)
- final rms: Continuum 23-60 μJy/beam; CO 0.23-0.65 mJy/beam (Table 2)  
  > "Columns (2), (3), and (4) list the range of 1$\sigma$ sensitivities for the continuum as well as for the CO and HCO$^+$ line observations." (Table 2 notes)

### Inherited from earlier work

- Kinemetry fitting approach for velocity fields  
  > "following the approach adopted by (cite: GB14) and (cite: GB19) to fit the velocity field of NGC 1068" (Appendix: Kinemetry fits) [from (cite: GB14); (cite: GB19)]
- Dust temperature 100 K adopted as in NGC 1068 torus studies  
  > "a common $T_{\rm dust}$ for all sources similar to the one used by (cite: GB14) and (cite: Vit14)" (4.4) [from (cite: GB14); (cite: Vit14)]
- CO 3-2/1-0 brightness temperature ratio ~2.9 from NGC 1068 torus  
  > "we adopted a 3–2/1–0 brightness temperature ratio $\sim2.9$, which is similar to the overall ratio measured by (cite: GB14) and (cite: Vit14)" (4.4) [from (cite: GB14); (cite: Vit14)]
- NGC 1068 torus parameters from 440 μm continuum  
  > "In the case of NGC 1068 we used the torus parameters derived by (cite: GB16) from the ALMA continuum images at 440 $\mu$m." (4.2) [from (cite: GB16)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channels / velocity masks per target
- CASA version and pipeline details, calibrators
- Cell size, image size, deconvolution and cleaning thresholds in GILDAS
- How CO/dust masses were integrated (apertures, noise masks)
- Details of the 1D-Gaussian strip fits (initial guesses)
- Subtraction of point source in spectral index maps and beam matching details
- XSPEC fit priors/start values and f-test threshold
- Combined NUGA sample values for measurements taken from Combes et al. 2019

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration; GILDAS uv-baseline continuum subtraction and UV-MAP imaging at robust 1 and 0.1  
  > "The calibrated uv-tables were exported to `GILDAS`[^4] to proceed with the continuum subtraction and imaging procedures as detailed below." (3.1 ALMA data)
   - software: CASA, GILDAS
   - parameter: robust 1 (MSR), 0.1 (HSR); 10 km/s channels  
  > "$robust=1$ (0.1) for the MSR (HSR) configuration" (Table 2 notes)
   - fitting: _not stated_
   - validation: _not stated_
2. **Decompose continuum into point source and extended Gaussian**: Three-step fit: 1D Gaussian strips along PA=0 and 90 for point source intensity; free 2D point source fit; 2D elliptical Gaussian fit to residual  
  > "In a third step we freely fitted a 2D elliptical Gaussian (of intensity $I_{\rm Gauss}$) to the residual obtained after subtraction of the point source estimated in *step-2*." (4.2)
   - parameter: Point source sizes fixed to projected ALMA beams in step 1  
  > "We fixed the sizes of the point sources for each target by projecting the ALMA beams along the corresponding strips." (4.2)
   - assumption: Inclination lower limit assuming axisymmetry and negligible thickness: i=acos(FWHMy/FWHMx)  
  > "$i_{\rm Gauss}$=acos(FWHM$_{\rm y}$/FWHM$_{\rm x}$)" (Table 3 notes)
   - fitting: Least-squares-type fits; sampler/likelihood not stated  
  > "In a third step we freely fitted a 2D elliptical Gaussian (of intensity $I_{\rm Gauss}$) to the residual obtained after subtraction of the point source estimated in *step-2*." (4.2 Decomposition of continuum emission: point sources and extended components)
   - validation: Inspection of residuals  
  > "We evaluated the goodness of the final fits by an inspection of the residuals" (4.2)
3. **Spectral index maps**: Combine 230 GHz and 351 GHz images convolved to common resolution 0.13-0.16"; alpha maps before and after point-source subtraction  
  > "We convolved all the images employed in this analysis to obtain a common range of spatial resolutions $0.13\ensuremath{''}$–$0.16\ensuremath{''}$ (11-18 pc)." (4.3)
   - fitting: _not stated_
   - validation: Compared alpha values with expectations for dust vs free-free/synchrotron  
  > "The value derived for $\alpha$ throughout the starburst ring, $\geq2-3$, can be accounted for by dust thermal emission." (4.3 Spectral index maps)
4. **Derive molecular gas masses from dust and CO**: Modified blackbody dust mass with gas-to-dust 100; CO mass via Bolatto et al. Eq. 3 with 1.36 He factor; compared dust-based and CO-based masses  
  > "The CO-based molecular gas masses derived from Equation (3) of (cite: Bol13), after including the mass of Helium" (4.4)
   - parameter: T_dust=100 K; kappa_351GHz=0.0865 m^2/kg; gas-to-dust ~100; X_CO=2e20; 3-2/1-0 = 2.9 (tori), 0.7 (FOV), 2.0 (200 pc)  
  > "We assumed a dust temperature $T_{\rm dust} \sim T_{\rm gas}=100$ K and a dust emissivity $\kappa_{{\rm 351~GHz}}=0.0865$ m$^2$ kg$^{-1}$ (cite: Kla01)" (4.4)
   - assumption: Galactic X_CO  
  > "we assumed a galactic CO–to–H$_2$ conversion factor ($X_{\rm CO}=2\times10^{20}$mol cm$^{-2}$ (K km s$^{-1}$)$^{-1}$)" (4.4)
   - fitting: _not stated_
   - validation: Dust vs CO masses agree to ~0.23 dex median; Pearson ~0.74 excluding NGC 7213  
  > "their median values differ only by $\sim0.23$ dex" (4.4)
5. **Test orientation of extended components relative to outflows**: Compute Delta between PA_Gauss and PA_out; KS and AD tests against uniform distribution  
  > "Using standard statistical tools, like Kolmogorov-Smirnov (KS) and Anderson-Darling (AD) tests, we quantify below the likeliness" (4.5)
   - assumption: Randomly oriented outflows give uniform Delta in 0-90 deg  
  > "if outflows were randomly oriented in space with respect to tori, the probability distribution of $\Delta$ would be uniform from 0$^\circ$ to 90$^\circ$" (4.5)
   - fitting: _not stated_
   - validation: p-values in Table 5  
  > "The low $p$ values of the two two-sided tests, in particular those for the MSR sample, imply that the agreement with a uniform distribution from 0$^{\circ}$ to 90$^\circ$ can be rejected at a very high significance." (Orientation of the extended components: equatorial (torus-like) or polar?)
6. **Line ratios CO/HCO+ at AGN positions**: Compare velocity-integrated CO(3-2) and HCO+(4-3) at AGN and stacked spectra  
  > "The fairly low CO/HCO$^+$ velocity-integrated intensity ratios measured towards the AGN in these sources, $\sim2.8-5.7$" (6)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit NuSTAR spectra and compare column densities**: XSPEC model zpcfabs*cutoffpl + borus02 + 2 zgauss; compare N_H(CO) with N_H(Xabs) and N_H(Xref) via correlation tests  
  > "For the reflection component we used the smooth model `borus02` provided by (cite: Bal18)." (7.2)
   - software: XSPEC, NuSTARDAS
   - parameter: Fe lines at 6.7 and 6.97 keV, 0.1 keV width; spectra grouped at 60 counts/bin; 3-70 keV  
  > "we used the grppha task to group the spectra with at least 60 counts per bin" (3.2 Ancillary data)
   - fitting: chi^2 fitting; f-test for linked vs unlinked absorbers  
  > "we linked together these two values ($N_{\rm H}^{\rm linked}$) when fitting and perform an f-test" (7.2)
   - validation: chi2/dof in Table 6  
  > "Table [\[Tab6\]](#Tab6) lists the best-fit $\rm{\chi^2}$ statistics together with the resulting parameters." (Dusty molecular tori and X-ray reflection)
8. **Kinemetry fits of CO velocity fields to find non-circular motions**: kinemetry on 32 ellipses (r=0.25" to 8.25", step 0.25") in three iterations (free PA,i; fixed i; fixed PA,i); non-circular deviations >30 km/s in p-v diagrams  
  > "We used in the fit 32 ellipses with semi major axes covering the disks from $r=0.25\ensuremath{''}$ to $r=8.25\ensuremath{''}$, with a spacing $\Delta r=0.25\ensuremath{''}$." (Fits of mean-velocity fields)
   - software: kinemetry
   - assumption: Thin coplanar disks; dynamical center at AGN position  
  > "We assumed that the dynamical centers for our sources coincide with the AGN positions derived in Sect." (Fits of mean-velocity fields)
   - fitting: Fourier decomposition, minimising non-circular terms  
  > "At each step, `kinemetry` finds the best fitting ellipses by maximizing the contribution of circular motions and by minimizing the contribution of noncircular motions" (Fits of mean-velocity fields, Kinemetry fits)
   - validation: _not stated_
9. **Gas concentration indices vs AGN luminosity**: Compute Sigma_H2 at r<=50 pc, torus scale, and r<=200 pc; indices as log ratios; Spearman, Kendall, Pearson tests vs L_2-10keV and Eddington ratio  
  > "We normalized the nuclear surface densities $\Sigma_{\rm H_2}^{\rm 50pc}$ and $\Sigma_{\rm H_2}^{\rm torus}$ to the H$_{\rm 2}$ surface densities measured on ’circumnuclear’ scales" (8.1)
   - assumption: 3-2/1-0 ratios ~2.0 (circumnuclear) and ~2.9 (nuclear); Milky Way X_CO  
  > "we assumed slightly different 3–2/1–0 brightness temperature ratios of $\sim2.0$ and $\sim2.9$, respectively" (8.1)
   - fitting: _not stated_
   - validation: Systematic uncertainty ±0.20 dex from conversion factors  
  > "Under these extreme hypotheses the total uncertainty amounts to $\pm$0.20 dex" (8.1)

## Software

- **CASA** : ALMA data calibration  
  > "We calibrated the data making use of the ALMA reduction package `CASA` (cite: McM07)" (3.1 ALMA data)
- **GILDAS** : Continuum subtraction (UV-BASELINE, UV-FILTER, UV-CONT) and imaging (UV-MAP)  
  > "using the `GILDAS` tasks `UV-FILTER` and `UV-CONT`" (3.1 ALMA data)
- **kinemetry** : Fitting CO(3-2) velocity fields  
  > "we used the software package `kinemetry`, developed by (cite: Kra06), to fit the velocity fields derived from the CO(3–2) data" (8.3)
- **XSPEC** : NuSTAR spectral fitting  
  > "a cutoff power-law model, `cutoffpl` in `XSPEC`" (7.2)
- **NuSTARDAS** v.1.4.4: NuSTAR data reduction  
  > "`NuSTAR` data reduction was done using the data analysis software `NuSTARDAS` ($v.1.4.4$)" (3.2 Ancillary data)
- **MultiDrizzle** : HLA WFPC2 image drizzling (archival product)  
  > "The HLA WFPC2 images are drizzled to a pixel size of 0.05$''$ using the MultiDrizzle software." (3.2 Ancillary data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Full-size (diameter) of extended continuum components, median | ~42 | range ~25-130 pc | pc | 2 | range from $\sim25$ pc to $\sim130$ pc with a median value of $\sim42$ pc |
| Molecular gas mass of extended components, median | ~6e5 | range ~5e4-1e7 | Msun | 4 | a median value of $\sim6\times10^{5}$M$_{\ensuremath{\odot}}$ |
| Median difference log M_gas(dust) vs M_gas(CO) | 0.23 | not stated | dex | 4 | their median values differ only by $\sim0.23$ dex |
| Pearson correlation M_dust vs M_CO (excluding NGC 7213) | ~0.74 | p~6e-3 | dimensionless | 4 | show Pearson correlation parameters $\sim+0.74$ and two-sided $p$ values $\sim6\times10^{-3}$ |
| Median I_Gauss/I_point | ~6 | range 0.5-55 | dimensionless | 2 | their median value, $\sim$6, is high |
| CO/HCO+ ratios towards AGN (bright HCO+ sources) | 2.8-5.7 (4.9 stacked) | not stated | dimensionless | 6 | $\sim2.8-5.7$ ($\sim4.9$ from the stacked spectra) |
| Pearson r, log N_H(CO) vs log N_H(Xabs) | +0.57 | one-sided p~0.02 | dimensionless | 7 | Pearson’s correlation coefficient, $r=+0.57$, and its associated one-sided $p$ value $\sim0.02$ |
| Median offset N_H(torus,CO) vs N_H(Xref) | ~1.54 | not stated | dex | 7 | differ now by $\simeq1.54$ dex |
| Spearman rho, index-II vs log L(2-10keV) | -0.79 | p=1e-4 | dimensionless | 9 | $\rho_{\rm Sp}$=**–0.79** , $p$=${\bf 10^{-4}}$ |
| Gas concentration index-I variation across sample | ~1 | not stated | dex | 9 | the gas concentration measured by index-I changes by $\sim1$ dex across the sample |
| Gas concentration index-II variation across sample | ~2 | not stated | dex | 9 | The corresponding decrease is of $\sim$2 dex for index-II. |
| KS two-sided p-value for Delta uniformity (MSR) | 2.9e-3 | not stated | dimensionless | 5 | KS (two-sided) / sample comes from uniform distribution / $4.8\times10^{-1\phantom{0}}$ / $2.9\times10^{-3}$ |
| Molecular outflow velocities in NGC 4388 and NGC 5506 | ~50-100 | not stated | km/s | 8 | have moderate radial velocities $\sim50-100$ km s$^{-1}$ |

## Qualitative findings

- All core-sample galaxies show resolved 870 μm disks around the AGN, mostly dust-dominated except NGC 7213 and partly NGC 6814  
  > "the bulk of the continuum flux of the extended components can be accounted for by thermal emission from dust in all of our sources with the exception of NGC 7213" (9 Summary)
- HCO+(4-3) detected in four GATOS Seyferts  
  > "We detected the emission of the 4–3 line of HCO$^+$, a tracer of dense molecular gas (n(H$_{\rm2}$) $\geq10^5-10^6$ cm$^{-3}$) in four GATOS Seyferts." (9 Summary)

## Claim tuples

- H: Extended 870 μm components trace dusty tori preferentially perpendicular to AGN winds | E: Compare PA_Gauss with outflow PA and test Delta against uniform distribution with KS/AD | R: 9 of 13 galaxies have Delta~60-90 deg; uniformity rejected (p~1e-3 to 3e-3 MSR) | F: Extended components have a preferential equatorial orientation relative to outflows | **supported**
- H: The extended continuum is dominated by dust | E: Compare dust-based and CO-based gas masses; spectral index maps | R: Median offset 0.23 dex; alpha~1.5-3 in extended components | F: Dust dominates except NGC 7213 (and partly NGC 6814) | **supported**
- H: Molecular column densities of tori contribute to X-ray obscuration | E: Correlate N_H(CO) with N_H(Xabs) and with N_H(Xref) from NuSTAR fits | R: r=+0.57 for absorption with similar medians; reflection column offset by 1.54 dex | F: Torus gas contributes to X-ray absorption; reflection arises at much smaller radii | **partially**
- H: AGN feedback imprints nuclear gas deficits that scale with luminosity and Eddington ratio | E: Gas concentration indices vs L_2-10keV and Eddington ratio in the combined GATOS+NUGA sample; kinemetry outflow search | R: Indices decrease with luminosity (rho_Sp up to -0.81); outflows in 4 of 5 sources with strongest deficits | F: Stronger feedback imprint in higher luminosity / Eddington ratio sources | **supported**
- H: Kiloparsec-scale gas mass correlates with AGN luminosity | E: M_gas[FOV] vs L_AGN and Eddington ratio | R: No significant correlation | F: Not found, attributed to AGN variability and scale mismatch | **refuted**

## Reasoning

- Why this data: CO(3-2) and HCO+(4-3) probe dense, hot gas; 351 GHz continuum limits non-dust contamination  
  > "the obtention of 351 GHz continuum images in our targets is a prerequisite to deriving the dust content of tori by keeping low the contribution from other mechanisms alien to thermal dust emission" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Common T_dust adopted for all sources; mass estimates depend on assumed conversion factors  
  > "In the absence of estimates for each galaxy, we were constrained to adopt a common $T_{\rm dust}$ for all sources" (4.4)
- Limitation (authors): Spectral index maps only possible for 3 sources  
  > "meaningful spectral index maps cannot be obtained for the rest of the GATOS galaxies" (4.3)
- Limitation (authors): Small-number statistics for orientation and correlations  
  > "Within the limits imposed by the sparse statistics" (4.5)
- Caveat (inferred, ours): Delta classification depends on poorly known outflow PAs (several uncertain)
- Caveat (inferred, ours): Point-source subtraction may bias extended masses where I_Gauss/I_point<=1
- Caveat (inferred, ours): Fixed X_CO, 3-2/1-0 and T_dust drive systematics in mass trends
- Caveat (inferred, ours): Correlation significance with n~19 and many tests is borderline
- Caveat (inferred, ours): Evolutionary scenario is speculative

## Reproducibility

- Data public (paper): Project IDs given; ALMA data referenced via ADS/JAO.ALMA  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2017.1.00082.S, $\#$2018.1.00113.S, and $\#$2016.1.00254.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel masks per target
- Missing: GILDAS imaging parameters (cell, size, cleaning)
- Missing: Outflow PA values compiled in appendix references
- Missing: NUGA comparison data (Combes et al. 2019)
- Missing: XSPEC fit start values
- Data volume (inferred): ~100-300 GB raw for 10 targets; NuSTAR/HST small
- Score (inferred): 3/5, Data and main steps are described, but GILDAS imaging parameters, line-free masks and several literature inputs are missing.
- Rediscovery candidate: no, Recipe depends on GILDAS custom steps and many external inputs not fully specified.

## Links

- Method: (cite: Kra06) (kinemetry method)
- Method: (cite: Bal18) (borus02 reflection model)
- Method: (cite: GB19) (NGC 1068 analysis approach used as template)
- Companion: AH21 (Alonso-Herrero et al. 2021 in prep.), paper II (Torus and polar dust emission compared with disk+wind models)
- Companion: (cite: Com19) (NUGA sample and NGC 1365 data)
- Related: GATOS
- Related: NUGA
- Related: Swift/BAT AGN survey

## Checks

```json
{
 "quotes": 102,
 "quotes_ok": 102,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 74,
  "rate": 0.725
 },
 "evidence_ok": true
}
```
