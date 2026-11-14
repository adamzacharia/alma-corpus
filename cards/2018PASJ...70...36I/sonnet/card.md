# Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). III. Star formation properties of the host galaxies at z ≳ 6 studied with ALMA

`2018PASJ...70...36I` | Publications of the Astronomical Society of Japan 2018 | first author: Izumi, Takuma | arXiv: 1802.05742 | DOI: 10.1093/pasj/psy026

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the star formation properties, sizes, dynamical masses and black hole-host mass relation of low-luminosity (M1450 > -25) quasar hosts at z >~ 6, compared with optically luminous quasars?  
  > "Finally, we find that the ratios of black hole mass to host galaxy dynamical mass of the most of low-luminosity quasars including the HSC ones are consistent with the local value." (abstract)
- Target **J0859+0022**: coordinates _not stated_; z/distance z_Lya = 6.39; z_[CII] = 6.3903  
  > "J0859+0022 (Ly$\alpha$-based redshift $z_{\rm Ly\alpha} = 6.39$)" (1 Introduction); distance from Lya redshift from Matsuoka et al. 2016; [CII] redshift measured  
  > "J0859+0022 (Ly$\alpha$-based redshift $z_{\rm Ly\alpha} = 6.39$)" (1 Introduction)
- Target **J1152+0055**: coordinates _not stated_; z/distance z_Lya = 6.37; z_[CII] = 6.3637  
  > "J1152+0055 ($z_{\rm Ly\alpha} = 6.37$)" (1 Introduction); distance from Lya redshift from Matsuoka et al. 2016; [CII] redshift measured  
  > "J1152+0055 ($z_{\rm Ly\alpha} = 6.37$)" (1 Introduction)
- Target **J2216-0016**: coordinates _not stated_; z/distance z_Lya = 6.10; z_[CII] = 6.0962  
  > "J2216-0016 ($z_{\rm Ly\alpha} = 6.10$)" (1 Introduction); distance from Lya redshift from Matsuoka et al. 2016; [CII] redshift measured  
  > "J2216-0016 ($z_{\rm Ly\alpha} = 6.10$)" (1 Introduction)
- Target **J1202-0057**: coordinates _not stated_; z/distance z_Lya = 5.93; z_[CII] = 5.9289  
  > "J1202-0057 ($z_{\rm Ly\alpha} = 5.93$)" (1 Introduction); distance from Lya redshift from Matsuoka et al. 2016; [CII] redshift measured  
  > "J1202-0057 ($z_{\rm Ly\alpha} = 5.93$)" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.01423.S
- bands: Band 6  
  > "(ID = 2016.1.01423.S, PI: T. Izumi) at band 6 between 2016 December 2 and 2017 April 13" (2 Observations and data reduction)
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz (~7.5 GHz total); native resolution 3.906 MHz binned to ~50 km/s  
  > "The total bandwidth of these observations was $\sim 7.5$ GHz, divided into four spectral windows of width 1.875 GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1-704.1 m (J1202-0057: 15.1-492.0 m)  
  > "Baseline (m) | 15.1–704.1 | 15.1–704.1 | 15.1–704.1 | 15.1–492.0" (Table 1)
- angular resolution: [CII] beams 0.52-0.79 x 0.43-0.71 arcsec  
  > "0$\ensuremath{''}$.64 $\times$ 0$\ensuremath{''}$.47" (Table 1)
- max recoverable scale: ~9.5 arcsec  
  > "With the minimum baseline length (15.1 m), the maximum recoverable scale of our observations is $\sim 9.5\ensuremath{''}$." (2 Observations and data reduction)
- sensitivity: continuum rms 9.5, 20.7, 13.2, 8.8 uJy/beam; [CII] 0.12-0.24 mJy/beam per 50 km/s  
  > "rms noise: | 9.5 | 20.7 | 13.2 | 8.8" (Table 1)
- time on source: 105, 17, 99, 205 min for J0859, J1152, J2216, J1202  
  > "On-source time (minute) | 105 | 17 | 99 | 205" (Table 1)
- observing dates: 2016 December 2 to 2017 April 13  
  > "at band 6 between 2016 December 2 and 2017 April 13" (2 Observations and data reduction)
- pi or archival as stated: PI T. Izumi, Cycle 4  
  > "ALMA Cycle 4 (ID = 2016.1.01423.S, PI: T. Izumi)" (2 Observations and data reduction)
- Line: [CII] 2P3/2 -> 2P1/2 (158 um) (1900.539 GHz)
- Other facility **Subaru HSC**: Optical discovery of the quasars and HSC photometry/photo-z of a field emitter  
  > "originally discovered by (cite: 2016ApJ...828...26M)" (1 Introduction)
- External data: Literature compilation of z>~6 quasar [CII], FIR, Mdyn, MBH and M1450 for comparison  
  > "We have also compiled $M_{\rm BH}$ or $M_{\rm 1450}$" (4.4) [from many, e.g. (cite: 2017arXiv171002212W), (cite: 2013ApJ...773...44W)]
- External data: MBH of J0859+0022 and J2216-0016 from Mg II virial calibration  
  > "See details about the $M_{\rm BH}$ measurement of J0859+0022 and J2216-0016 with the Mg -based calibrations (cite: 2009ApJ...699..800V) in M. Onoue et al. (in preparation)." (Table 4 note) [from Onoue et al. in preparation; (cite: 2009ApJ...699..800V)]
- Simulation/model as data: nu2GC-L semi-analytic galaxy catalog (~41,000 galaxies hosting >=1e7 Msun SMBHs at z~6)  
  > "We selected $\simeq 41,000$ galaxies hosting $\geq10^7~M_\odot$ SMBHs from the simulated catalog" (4.3)

## Processing

### Calibration

- pipeline or manual: CASA, standard manner  
  > "Reduction and calibration of the data were performed with the Common Astronomy Software Applications (CASA) package" (2 Observations and data reduction)
- casa version: CASA 4.7  
  > "version 4.7 in the standard manner" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231 & J0854+2006; J1229+0203; J2148+0657; J1229+0203  
  > "Flux calibrator | J0750+1231, J0854+2006 | J1229+0203 | J2148+0657 | J1229+0203" (Table 1)
- flux scale uncertainty: 10% at Band 6  
  > "the systematic uncertainty of the absolute flux calibration at ALMA band 6 is 10%" (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean, gain = 0.1  
  > "All images were reconstructed with the CASA task `clean` (gain = 0.1, weighting = briggs, robust = 0.5)." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0.5  
  > "weighting = briggs, robust = 0.5" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.1 arcsec  
  > "The pixel scale of all maps in this paper is set to 0$\ensuremath{''}$.1." (2 Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: subtracted in the uv plane; continuum from all line-free channels (~7.5 GHz)  
  > "the continuum emission was subtracted in the ($u$, $v$) plane before making the line cube" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: applied; negligible effect  
  > "We used line intensities corrected for the primary beam attenuation for quantitative discussions, but this had a negligible effect" (2 Observations and data reduction)
- array combination: _not stated_
- smoothing: 11-12 channels binned to ~50 km/s  
  > "11–12 channels were binned to improve the signal-to-noise ratio" (2 Observations and data reduction)
- final beam: see Table 1 (e.g. 0.64x0.47 arcsec J0859)  
  > "0$\ensuremath{''}$.56 $\times$ 0$\ensuremath{''}$.50" (Table 1)
- final rms: continuum 8.8-20.7 uJy/beam  
  > "rms noise: | 9.5 | 20.7 | 13.2 | 8.8" (Table 1)

### Inherited from earlier work

- Emitter search procedure for [CII] line emitters  
  > "We applied the procedure described in (cite: 2017ApJ...845..108Y) to our continuum-subtracted cubes." (3.4.1) [from (cite: 2017ApJ...845..108Y)]
- Mdyn method (thin disk, vcirc=0.75 FWHM/sin i, D=1.5 a_maj)  
  > "by following the standard procedure in previous $z \gtrsim 6$ quasar studies" (4.3) [from (cite: 2010ApJ...714..699W)]
- Orthogonal distance regression fit of [CII]/FIR vs FIR  
  > "We fit the relationship for the high-redshift quasar sample including the objects in this study following (cite: 2017arXiv171002212W)." (4.1) [from (cite: 2017arXiv171002212W)]
- Td=47K, beta=1.6 gray body  
  > "to be consistent with previous $z > 6$ quasar studies" (3.2) [from (cite: 2013ApJ...773...44W; 2015ApJ...801..123W; 2016ApJ...816...37V)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection and velocity ranges for moment-0 maps
- Clean mask, threshold and iteration settings; image size
- CASA task parameters for imfit (regions, initial guesses)
- Dust-temperature SED details for the gray body integration and L_FIR band definition
- Gas-to-dust ratio value used
- Details of nu2GC selection and M_BH from Onoue et al.
- Which archive products or scripts were used (pipeline vs manual)

## Analysis recipe

1. **Image cubes and continuum**: Calibrate and clean with CASA; uv continuum subtraction; bin to 50 km/s  
  > "All images were reconstructed with the CASA task `clean` (gain = 0.1, weighting = briggs, robust = 0.5)." (2 Observations and data reduction)
   - software: CASA
   - parameter: briggs robust 0.5; 0.1 arcsec pixels  
  > "The pixel scale of all maps in this paper is set to 0$\ensuremath{''}$.1." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract [CII] line properties**: Single Gaussian fit of continuum-subtracted spectrum in 1.5 arcsec aperture; L_[CII] via standard equation  
  > "We fit each continuum-subtracted spectrum with a single Gaussian profile to extract the redshift" (3.1)
   - software: CASA
   - parameter: 1.5 arcsec diameter circular aperture  
  > "we decided to measure the rest-frame FIR properties with a common 1$\ensuremath{''}$.5 diameter circular aperture." (3 Results)
   - assumption: H0=70, OmegaM=0.3, OmegaL=0.7  
  > "$H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}$ = 0.3, and $\Omega_{\rm \Lambda}$ = 0.7" (1 Introduction)
   - fitting: single Gaussian; double Gaussian tested for J2216-0016 (reduced chi2 1.05 vs 1.24)  
  > "the resultant reduced $\chi^2$ is 1.05 (degree of freedom [^6], d.o.f. = 14), which is improved over the single-Gaussian fit" (3.5)
   - validation: _not stated_
3. **Derive SFR from [CII]**: De Looze et al. 2011 relation  
  > "SFR}_{\rm [C\,\emissiontype{II}]}$/$M_\odot$ yr$^{-1}$ = 1.0 $\times$ 10$^{-7}$ ($L_{\rm [C\,\emissiontype{II}]}$/$L_\odot$)$^{0.98}$" (3.1)
   - assumption: Kroupa IMF; young stars heat [CII]; AGN contribution neglected; dispersion ~0.3 dex not in errors  
  > "This relation, with a dispersion of $\sim 0.3$ dex (this is not included in the errors of the derived SFR), is calibrated with the Kroupa initial mass function" (3.1)
   - fitting: _not stated_
   - validation: Compared with TIR-based SFR  
  > "the above TIR-based SFR (SFR$_{\rm TIR}$) are systematically larger than the \[C \]-based SFR" (3.2)
4. **FIR luminosity, SFR_TIR and dust mass**: Optically thin gray body to 1.2 mm flux; extend to TIR (8-1000 um); SFR=1.49e-10 L_TIR; Mdust from kappa  
  > "we first adopted an optically thin gray body spectrum model with dust temperature $T_d$ = 47 K and emissivity index $\beta$ = 1.6" (3.2)
   - parameter: Td=47 K and 35 K, beta=1.6, kappa0=0.4 cm2/g at 250 GHz  
  > "$\kappa_0 = 0.4$ cm$^2$ g$^{-1}$" (3.2)
   - assumption: No CMB correction for Td >~ 35 K; star formation accounts for all TIR  
  > "We thus do not make any correction to the observed submm fluxes in this study" (3.2)
   - fitting: _not stated_
   - validation: Td=35 K gives SFR_TIR closer to SFR_[CII]  
  > "The SFR$_{\rm TIR}$ now agrees better with SFR$_{\rm [C\,\emissiontype{II}]}$ for J0859+0022, J1152+0055, and J1202-0057" (3.2)
5. **Measure source sizes**: 2D Gaussian fit to [CII] moment-0 and continuum maps in image plane, 3 sigma clipping, native resolution  
  > "applying a two-dimensional Gaussian fit to both the \[C \] integrated intensity and the continuum maps, using the CASA task `IMFIT`" (3.3)
   - software: CASA imfit
   - fitting: imfit 2D Gaussian  
  > "was estimated by applying a two-dimensional Gaussian fit to both the \[C \] integrated intensity and the continuum maps, using the CASA task `IMFIT`." (Spatial extent of the star-forming region)
   - validation: [CII] and continuum sizes compared  
  > "We found good consistency between the \[C \]-based sizes and continuum-based sizes within the uncertainties" (3.3)
6. **Search for companion emitters**: CLUMPFIND on continuum-subtracted cubes, peak S/N>=5; continuum emitters at S/N>=5  
  > "We used the `CLUMPFIND` software (cite: 1994ApJ...428..693W) to search for line emitters other than the HSC quasars themselves with a peak $S/N \geq 5$." (3.4.1)
   - software: CLUMPFIND
   - parameter: Delta S = 1 sigma, S_start = 3 sigma; 43 MHz binning  
  > "The relevant parameters were $\Delta~S = 1\sigma$ and $S_{\rm start} = 3\sigma$" (3.4.1)
   - fitting: _not stated_
   - validation: Rejected candidates without S/N>=3 in adjacent channels  
  > "we rejected candidates that do not show $S/N \geq 3$ emission in any of the channels adjacent to the peak ones" (3.4.1)
7. **Dynamical mass and comparison with MS and MBH-Mdyn**: Thin-disk Mdyn=1.16e5 vcirc^2 D; i from axis ratio; compare with nu2GC and local relation  
  > "$i$ = cos$^{-1}$($a_{\rm min}$/$a_{\rm maj}$)" (4.3)
   - parameter: vcirc=0.75 FWHM/sin i; D=1.5 a_maj  
  > "$v_{\rm circ}$ = 0.75 FWHM$_{\rm [C\,\emissiontype{II}]}$/$\sin i$" (4.3)
   - assumption: Mdyn used as surrogate for M*; Eddington-limited accretion for BH mass of two quasars  
  > "hereafter we use the above $M_{\rm dyn}$ as a surrogate for $M_*$" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: Calibration, clean imaging, immoments, imfit  
  > "(CASA) package (cite: 2007ASPC..376..127M) version 4.7 in the standard manner" (2 Observations and data reduction)
- **CLUMPFIND** : Line emitter search  
  > "We used the `CLUMPFIND` software (cite: 1994ApJ...428..693W)" (3.4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_[CII] range | (3.8-10.2)e8 | not stated | Lsun | 2 | $L_{\rm [C\,\emissiontype{II}]} = (3.8-10.2) \times 10^8~L_\odot$ |
| J2216-0016 [CII] flux | 1.05 | 0.08 | Jy km/s | 2 | 1.05 $\pm$ 0.08 |
| [CII] FWHM range | 192-356 | not stated | km/s | 2 | The line FWHM ranges from 192 to 356 km s$^{-1}$ |
| SFR_[CII] | 25-67 | not stated | Msun/yr | 3 | The derived SFRs (25–67 $M_\odot$ yr$^{-1}$) |
| 1.2 mm continuum flux density | 136-246 | not stated | uJy | 2 | $f_{\rm 1.2mm}$ ($\mu$Jy) / 157 $\pm$ 23 / 189 $\pm$ 32 / 136 $\pm$ 27 / 246 $\pm$ 12 |
| L_FIR (Td=35 K) | 1.2-2.0e11 | not stated | Lsun | 4 | $L_{\rm FIR} = (1.2-2.0) \times 10^{11}~L_\odot$ |
| SFR_TIR (Td=35 K) | 23-40 | not stated | Msun/yr | 4 | $\simeq 23-40~M_\odot ~{\rm yr}^{-1}$ |
| L_[CII]/L_FIR | (2.2-8.7)e-3 | not stated | dimensionless | 4 | $\simeq (2.2-8.7) \times 10^{-3}$ |
| Mdyn | (1.4-8.2)e10 | not stated | Msun | 7 | $\simeq (1.4-8.2) \times 10^{10}~M_\odot$ |
| J2216-0016 [CII] size major axis | 5.2 | 0.8 | kpc | 5 | (5.2 $\pm$ 0.8) kpc $\times$ (2.5 $\pm$ 0.7) kpc |
| ODR fit of log L[CII]/LFIR vs log LFIR | intercept 3.84, slope -0.56 | 0.57, 0.05 | dimensionless | 7 | \log_{\rm 10} L_{\rm [C\,\emissiontype{II}]}/L_{\rm FIR} = (3.84 \pm 0.57) - (0.56 \pm 0.05) ~\log_{\rm 10} L_{\rm FIR} |

## Qualitative findings

- No continuum or [CII] emitters near the quasars within the FoV; one likely lower-redshift line emitter (possibly CO(5-4), z_photo=1.32) found 13.2 arcsec from J2216-0016  
  > "We did not find any continuum or line emitter physically close to the HSC quasars within the nominal FoVs, except for one likely lower-redshift weak line emitter." (6 Summary)

## Claim tuples

- H: Low-luminosity HSC quasar hosts have lower SFR and FIR/[CII] luminosity than luminous quasars | E: [CII] and 1.2 mm continuum measurements with ALMA | R: L_[CII]=(3.8-10.2)e8 Lsun, SFR ~23-40 Msun/yr | F: Fainter by an order of magnitude, LIRG-like | **supported**
- H: L_[CII]/L_FIR shows a deficit like luminous quasars | E: Compare ratios with local galaxies | R: ratios (2.2-8.7)e-3 | F: Consistent with local star-forming galaxies | **supported**
- H: HSC quasar hosts are on or below the z~6 star-forming main sequence | E: Place SFR vs Mdyn (as M*) against nu2GC and observed MS | R: All on or below MS | F: They appear to be transforming into quiescent galaxies | **partially**
- H: Low-luminosity quasars follow the local MBH-Mdyn relation | E: Compile MBH and Mdyn; compare to local relation and nu2GC | R: Less luminous quasars roughly consistent with local relation | F: Consistent with merger-induced co-evolution; sample small | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane fitting for sizes chosen for consistency with previous quasar host studies and low S/N  
  > "This method (i.e., image-plane fitting) is consistent with those used in the previous submm studies on quasar host galaxies" (3.3)
- Alternative: uv-plane size fitting rejected due to insufficient S/N  
  > "such a method only applies for data with decent $S/N$ (cite: 2015ApJ...810..133I), which is not the case for our work." (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Mdyn has large unconstrained systematic uncertainty; sources only marginally resolved  
  > "Keeping the existence of such large *unconstrained* systematic uncertainty in mind" (4.3)
- Caveat (inferred, ours): Td fixed rather than fitted from a single continuum band
- Caveat (inferred, ours): Mdyn as M* surrogate with assumed inclinations from poorly resolved axis ratios
- Caveat (inferred, ours): MBH of two quasars assumes Eddington accretion (lower limit)
- Caveat (inferred, ours): Small sample of four

## Reproducibility

- Data public (paper): Cycle 4 ALMA data cited by project ID  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01423.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel ranges and moment velocity ranges
- Missing: Clean masks/thresholds
- Missing: SED integration details
- Missing: MBH values from unpublished paper
- Data volume (inferred): ~50-150 GB raw for four Band 6 execution sets
- Score (inferred): 3/5, Data public and recipe mostly specified, but several imaging and analysis details are missing and some inputs are unpublished.
- Rediscovery candidate: yes, Public data, clear CASA recipe and numeric results (fluxes, sizes, luminosities).

## Links

- Method: (cite: 2011MNRAS.416.2712D) ([CII]-SFR relation)
- Method: (cite: 2010ApJ...714..699W) (Mdyn procedure)
- Companion: (cite: 2016ApJ...828...26M) (Discovery of the HSC quasars)
- Related: SHELLQs
- Related: Subaru HSC survey

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 67,
  "rate": 0.705
 },
 "evidence_ok": true
}
```
