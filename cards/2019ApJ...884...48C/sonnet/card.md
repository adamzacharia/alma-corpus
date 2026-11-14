# The Seven Most Massive Clumps in W43-Main as Seen by ALMA: Dynamical Equilibrium and Magnetic Fields

`2019ApJ...884...48C` | The Astrophysical Journal 2019 | first author: Cortes, Paulo C. | arXiv: 1907.12994 | DOI: 10.3847/1538-4357/ab378d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How fragmented and magnetized are the most massive W43-Main clumps, and are their cores gravitationally bound once turbulence and magnetic fields are included?  
  > "By using our estimations, we evaluated the dynamical equilibrium of our cores by computing the total virial parameter $\alpha_{\mathrm{total}}$." (abstract)
- Target **W43-MM2, MM3, MM4, MM6, MM7, MM8**: coordinates phase centers from Motte et al. 2003 Table 1; cores near 18:47:36, -02:00:50 (MM2)  
  > "The W43-Main is a large molecular complex located within the W43 region at 5.5 kpc from the sun" (1 INTRODUCTION); "the phase center coordinates for each clump were taken from Table 1 in (cite: Motte2003)." (2.1 ALMA OBSERVATIONS); z/distance 5.5 kpc  
  > "The W43-Main is a large molecular complex located within the W43 region at 5.5 kpc from the sun" (1 INTRODUCTION); "the phase center coordinates for each clump were taken from Table 1 in (cite: Motte2003)." (2.1 ALMA OBSERVATIONS); distance from Motte2003; Zhang2014a  
  > "The W43-Main is a large molecular complex located within the W43 region at 5.5 kpc from the sun" (1 INTRODUCTION); "the phase center coordinates for each clump were taken from Table 1 in (cite: Motte2003)." (2.1 ALMA OBSERVATIONS)

## Data provenance

- ALMA projects: 2013.1.00725.S
- bands: Band 6 (1.3 mm), full polarization  
  > "The data presented here corresponds to ALMA observations at 1.3 mm (band 6)" (2.1 ALMA OBSERVATIONS)
- frequencies and spectral setup: continuum/TDM, 64 channels per spw, 31.25 MHz resolution; spws centered at 224, 226, 240, 242 GHz  
  > "Each spectral window was centered at the standard ALMA band 6 polarization frequencies (224, 226, 240, and 242 GHz)." (2.1 ALMA OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: 35 antennas  
  > "An array of 35 antennas was used" (2.1 ALMA OBSERVATIONS)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 arcsec (~0.01 pc)  
  > "reaching an angular resolution of $\sim$ 0.5$^{\prime \prime}$" (2.1 ALMA OBSERVATIONS)
- max recoverable scale: 5.12 arcsec (0.14 pc)  
  > "the maximum recoverable angular scale for our data is about 5.12$^{\prime \prime}$ or 0.14 pc" (3.1 DUST CONTINUUM EMISSION)
- sensitivity: Stokes I rms ~200 uJy/beam; polarized intensity rms ~54 uJy/beam  
  > "average rms for Stokes I of $\left< \sigma_{\mathrm{I}} \right> \sim 200 \mu$Jy beam$^{-1}$" (2.1 ALMA OBSERVATIONS)
- time on source: about 12 minutes per field  
  > "In total, we obtained about 12 minutes per field (clump)" (2.1 ALMA OBSERVATIONS)
- observing dates: May 30th, 2015; two executions  
  > "Two successful executions were done using the session scheme" (2.1 ALMA OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: HCO+ J=4-3 (ASTE) (356.7342880 GHz)
- Line: HCN J=4-3 (ASTE) (354.5054773 GHz)
- Other facility **ASTE**: HCN and HCO+ J=4-3 maps of MM2 and MM3  
  > "We simultaneously observed HCO$^{+}(J=4\rightarrow3)$ and HCN$(J=4\rightarrow3)$ with a beam size of $\sim 22^{\prime \prime}$" (2.3 ASTE OBSERVATIONS)
- Other facility **Spitzer IRAC**: archival images of MM3  
  > "we obtained SPITZER IRAC archival images towards MM3." (3.1.2 W43-MM3 CONTINUUM)
- External data: H13CO+(3-2) spectra/line widths and V_lsr for DCF velocity dispersions and infall  
  > "we use the published H$^{13}$CO$^{+}$($J=3 \rightarrow 2$) from (cite: Motte2003) spectra to confirm the self-absorption." (3.3 LINE EMISSION) [from (cite: Motte2003)]
- External data: 13CO and C18O (2-1) spectra from large-scale CO mapping  
  > "shows extracted $^{13}$CO$(J=2 \rightarrow 1)$ and C$^{18}$O$(J=2 \rightarrow 1)$ spectra from the W43-Main large scale CO mapping by (cite: Carlhoff2013)." (4.1.5) [from (cite: Carlhoff2013)]
- External data: Clump dust temperatures and masses from SED fitting  
  > "The temperature range used in the mass calculation was taken from the Spectral Energy Density (SED) fitting by (cite: Motte2003; Bally2010)" (3.1 DUST CONTINUUM EMISSION) [from (cite: Motte2003; Bally2010)]
- External data: Kolmogorov exponent n=0.36  
  > "(cite: Li2008) derived $n=0.36$ from their M17 emission" (6 THE DCF METHOD) [from (cite: Li2008)]

## Processing

### Calibration

- pipeline or manual: CASA calibration with polarization calibration  
  > "Calibration and imaging was done using the Common Astronomical Software Applications (CASA) (cite: McMullin2007)." (2.1 ALMA OBSERVATIONS)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); J1751+0939 bandpass; J1851+0035 phase; J1924-292 polarization  
  > "along with J1751+0939 to calibrate the bandpass, J1851+0035 to calibrate the phase, and Titan to calibrate the flux." (2.2 Calibration and imaging in full polarization mode)
- flux scale uncertainty: _not stated_
- self calibration: three phase-only iterations, final solint 90 s  
  > "The final images were produced after three, phase-only, self-calibration iterations using a final solution interval of 90 seconds." (2.2 Calibration and imaging in full polarization mode)

### Imaging

- task: CASA clean, clarkstokes  
  > "we imaged the data using the $clean$ CASA task with the *Briggs* weighting scheme, robust number 0.5" (2.2 Calibration and imaging in full polarization mode)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "with the *Briggs* weighting scheme, robust number 0.5, for sidelobe robustness" (2.2 Calibration and imaging in full polarization mode)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Gaussian fits done on primary-beam-corrected maps  
  > "2D Gaussian fitting by means of the CASA task *imfit* used over the primary beam corrected maps." (3.1 DUST CONTINUUM EMISSION)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- getsources core extraction and DCF analysis as in W43-MM1 paper  
  > "As in , we used the *getsources* algorithm (cite: Menshchikov2012) to extract core candidates from the continuum emission." (3.1 DUST CONTINUUM EMISSION) [from Cortes et al. 2016 (paper I; (cite: Cortes2016))]
- Core nomenclature and T=70 K hot-core mass for MM2-A  
  > "Following , we also consider here T=70 K to estimate the mass for MM2-$A$ which yields $M_{A} = 118$ M$_{\odot}$." (4.1.5) [from Cortes2016]
- Star formation efficiency of 25%  
  > "assuming a star formation efficiency of 25% (cite: Motte2003)" (4.1.5) [from (cite: Motte2003)]

### Not stated but needed to reproduce (our reading)

- Image sizes, cell sizes, clean thresholds, masks and number of iterations
- CASA version
- Line-free channels / whether any continuum subtraction was done
- Polarization debiasing and exact EVPA/pseudo-vector sampling
- getsources parameters and detection thresholds
- Exact scale L and b for each DCF region and the Q factor value
- Flux calibration uncertainty
- Final beam for each clump

## Analysis recipe

1. **Calibrate and image full-polarization continuum**: Polarization calibration with J1924-292, clean with Briggs robust 0.5, clarkstokes, three phase-only self-cal rounds  
  > "Using this source, we derived solutions for the cross polarization delay, the *XY*-phase, and the D-terms." (2.2 Calibration and imaging in full polarization mode)
   - software: CASA
   - parameter: robust 0.5; final self-cal solint 90 s  
  > "final solution interval of 90 seconds" (2.2 Calibration and imaging in full polarization mode)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract cores and derive masses**: getsources seeds a 2D Gaussian fit with imfit; keep converged fits; column density and mass from optically thin dust emission  
  > "The extracted core position and size was used as a seed for a 2D Gaussian fitting by means of the CASA task *imfit*" (3.1 DUST CONTINUUM EMISSION)
   - software: getsources, CASA imfit
   - parameter: kappa_230GHz = 0.01 cm2/g (incl. gas-to-dust 100); mu=2.33  
  > "$\kappa_{\nu} = 0.01$ cm$^{2}$ gr$^{-1}$ is the emissivity of the dust grains at 230 GHz, which includes a gas to dust ratio of a 100" (3.1 DUST CONTINUUM EMISSION)
   - assumption: Td 23 K (MM2), 27 K (MM3), 28 K (MM4), 25 K (MM6-8); d=5.5 kpc; optically thin  
  > "we assumed T = 25 K which is the mean value between the temperatures determined by the SED fitting" (3.1 DUST CONTINUUM EMISSION)
   - fitting: 2D Gaussian (imfit)  
  > "The extracted core position and size was used as a seed for a 2D Gaussian fitting by means of the CASA task *imfit* used over the primary beam corrected maps." (3.1 DUST CONTINUUM EMISSION)
   - validation: only cores with converged Gaussian fit kept  
  > "only cores where the Gaussian fitting converged were considered here." (3.1 DUST CONTINUUM EMISSION)
3. **Estimate plane-of-sky magnetic field strength**: DCF and two variants (Falceta-Goncalves 2008, Heitsch 2001) over regions of continuous EVPA; velocity dispersion extrapolated with Kolmogorov sigma^2=bL^n from H13CO+(3-2)  
  > "by using the Davis-Chandrasekhar-Fermi (DCF) method (cite: Davis1951; Chandrasekhar1953) and its variants" (3.2 THE MAGNETIC FIELD STRENGTH FROM DUST CONTINUUM)
   - parameter: n=0.36; at least 10 independent (Nyquist) points per region; delta phi as std of EVPA  
  > "We use the standard deviation of the EVPA values from the polarization map as our estimator of the dispersion." (6 THE DCF METHOD)
   - assumption: Dust grains aligned with B; EVPA dispersion due to non-thermal motions; spherical geometry for density  
  > "assuming a Kolmogorov like power spectrum and the dispersion in the polarization position angle (also called the electric vector position angle, or EVPA) is due to perturbations from the gas non-thermal motions." (3.2 THE MAGNETIC FIELD STRENGTH FROM DUST CONTINUUM)
   - fitting: _not stated_
   - validation: Compared with W43-MM1 values; lower limits flagged where infall drives dispersion  
  > "Therefore, this bias in the estimation of $\delta \phi$, likely, yielded magnetic field strengths estimations which are lower limits from the “true” magnetic field strength around the MM2-$A$ and $D$ cores." (THE W43-MM2 FIELD)
4. **Model infall in MM2 and MM3**: Double-Gaussian fit then two-layer infall model (Myers 1996), chi2 minimised by Levenberg-Marquardt; infall rate from spherical formula  
  > "The model was then adjusted to the resulting Gaussian spectra by minimizing the $\chi^{2}$ function through the Levenburg-Marquardt algorithm (cite: Press2002)." (3.4 INFALLING MOTIONS)
   - parameter: R = 0.3 pc; mu=2.35; n_H2 from Table 3; filling factor 0  
  > "where $\mu$ = 2.35 is the mean molecular weight, R = 0.3 pc is the geometric radius" (3.4 INFALLING MOTIONS)
   - fitting: chi2 minimisation, Levenberg-Marquardt  
  > "The model was then adjusted to the resulting Gaussian spectra by minimizing the $\chi^{2}$ function through the Levenburg-Marquardt algorithm (cite: Press2002)." (INFALLING MOTIONS)
   - validation: Blue excess dV_be from H13CO+  
  > "The $\Delta V_{\mathrm{be}}$ values obtained for both MM2 and MM3 from the HCN and HCO$^{+}$ emission are all suggestive of infalling motions." (3.4 INFALLING MOTIONS)
5. **Virial analysis**: M_kin, M_Phi, alpha_total=(M_kin+M_Phi)/M_gas and lambda_B for cores with B estimates  
  > "we can now calculate a total virial parameter as," (4.1.1)
   - parameter: k=5/3 (constant density); core scale 1 arcsec; T +-5 K error bars  
  > "by using a $\pm 5$ K temperature deviation relative to the nominal SED temperature of the clump" (4.1.3)
   - assumption: rotation neglected  
  > "we do not consider rotation here." (4.1.1)
   - fitting: power-law fit alpha=b(M0/Mobs)^a  
  > "we fitted our data with such power law obtaining $b=1.06$ and $a=-0.92$ for the initial 17 cores" (4.1.3)
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, imfit  
  > "Calibration and imaging was done using the Common Astronomical Software Applications (CASA) (cite: McMullin2007)." (2.1 ALMA OBSERVATIONS)
- **getsources** : core extraction  
  > "we used the *getsources* algorithm (cite: Menshchikov2012) to extract core candidates" (3.1 DUST CONTINUUM EMISSION)
- **NEWSTAR** : ASTE data reduction  
  > "Initial data reduction and calibration was done using the NEWSTAR package (cite: Ikeda2001)." (2.3 ASTE OBSERVATIONS)
- **matplotlib** : plotting  
  > "exported to be plotted using matplotlib (cite: Hunter2007)" (2.3 ASTE OBSERVATIONS)
- **APLpy** : plotting  
  > "CASA (cite: McMullin2007), NEWSTAR (cite: Ikeda2001), APLpy (cite: Robitaille2012)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of cores extracted | 81 (96 with MM1) | not stated | cores | 2 | we extracted 81 cores (96 with the MM1 cores) |
| Mass sensitivity | 0.08 | not stated | Msun | 2 | a mass sensitivity of 0.08 M$_{\odot}$ |
| MM2-A mass | 425.7 | not stated | Msun | 2 | / 354.1 $\pm$ 17.8 / 879.8 / 0.79 / 0.63 / 149.80 / 283.7 / 425.7 / |
| Mean B_pos whole sample | 1.8 | not stated | mG | 3 | (with a $\left<\mathrm{B}_{\mathrm{pos}}\right>$=1.8 mG for the whole sample) |
| Mass infall rate MM3 | 6.3e-3 | not stated | Msun/yr | 4 | $\dot{\mathrm{M}}_{\mathrm{MM3}} = 6.3 \times 10^{-3}$ M$_{\odot}$ yr$^{-1}$ |
| Mass infall rate MM2 | 1.2e-2 (abstract/summary); 1.8e-2 in Section 3.4 | not stated | Msun/yr | 4 | $\dot{\mathrm{M}}_{\mathrm{MM2}} = 1.2 \times 10^{-2}$ M$_{\odot}$ yr$^{-1}$ |
| Fraction of 17 cores with alpha_total<1 | 71% (12 of 17) | not stated | percent | 5 | The remaining 12 cores, or 71% of the total, have $\alpha_{\mathrm{total}} < 1$ |
| Mean M_kin/M_Phi | 1.43 | not stated | dimensionless | 5 | $\left<M_{\mathrm{kin}}/M_{\mathrm{\Phi}}\right> = 1.43$ |
| Predicted max stellar mass in MM2-A | 28 +-14 | 14 | Msun | 5 | which gives $M_{\mathrm{max}} = 28 \pm 14$ M$_{\odot}$ |

## Qualitative findings

- Clumps split into two populations: MM2/3/4 are less fragmented, dominated by one core and strongly polarized; MM6/7/8 are more fragmented and weakly polarized.  
  > "In the population 1, the polarized intensity is weaker and compact while in the population 2 the polarized emission is strong and widely distributed" (3.1 DUST CONTINUUM EMISSION)

## Claim tuples

- H: Are cores in W43-Main bound when turbulence and magnetic fields are both included? | E: Computed alpha_total for 17 cores with B_pos estimates | R: 12 of 17 (71%) have alpha_total<1; 5 (29%) are unbound | F: Unbound, less massive cores are still accreting; star formation timescales are non-uniform | **supported**
- H: Do the massive clumps show infall? | E: Blue asymmetry and infall model on ASTE HCN/HCO+ 4-3 | R: Infall rates ~1e-2 Msun/yr | F: MM2 and MM3 are infalling | **supported**
- H: Does fragmentation correlate with polarization and field strength? | E: Compared polarized emission and fractional polarization with Stokes I | R: MM6/7/8 are unpolarized despite sufficient Stokes I | F: Weaker fields may explain higher fragmentation, but more data are needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature poorly constrained; higher core temperatures would lower masses and raise alpha_total  
  > "The mass estimates depends on the dust temperature, a proxy for the gas temperature, which is not well constrain for these clumps." (4.1.2 Caveats)
- Limitation (authors): Velocity dispersion extrapolated via an assumed Kolmogorov law  
  > "We are deriving velocity dispersions by assuming a Kolmogorov-like power spectrum" (4.1.2 Caveats)
- Caveat (inferred, ours): Text gives inconsistent MM2 infall rate (1.8e-2 vs 1.2e-2) and 81 vs 96 core counts across sections
- Caveat (inferred, ours): DCF applied with extrapolated sigma and no uncertainty propagation
- Caveat (inferred, ours): Unbound fraction for the full sample depends on assumed B values
- Caveat (inferred, ours): Beam elongated and sensitivity not met due to low elevation

## Reproducibility

- Data public (paper): ALMA project 2013.1.00725.S acknowledged; ASTE data not stated public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#.2013.1.00725.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: getsources settings
- Missing: DCF region definitions beyond the figure
- Missing: ASTE spectra
- Data volume (inferred): ~10-50 GB raw (two executions, 7 fields, band 6 TDM)
- Score (inferred): 3/5, ALMA data are public and the main steps are described, but many imaging and extraction settings and inherited choices are missing.
- Rediscovery candidate: no, Recipe incomplete (getsources settings, DCF inputs) and ASTE data not obviously public.

## Links

- Method: (cite: Cortes2016) (Paper I: MM1 polarization and DCF methodology)
- Method: (cite: Myers1996) (Two-layer infall model)
- Method: (cite: Menshchikov2012) (getsources algorithm)
- Companion: (cite: Motte2018a) (ALMA W43-MM1 core catalog)
- Related: Motte et al. 2003 W43 1.3 mm survey
- Related: Carlhoff et al. 2013 CO survey

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 83,
  "stated": 55,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
