# ALMA constraints on the faint millimetre source number counts and their contribution to the cosmic infrared background

`2015A&A...584A..78C` | Astronomy and Astrophysics 2015 | first author: Carniani, S. | arXiv: 1502.00640 | DOI: 10.1051/0004-6361/201525780

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, cosmology
- Question: What are the faint (sub-mJy) number counts of millimetre sources at 1.1 and 1.3 mm from deep ALMA maps, and what fraction of the cosmic infrared background do they resolve?  
  > "We used imaging from ALMA with a sensitivity down to 7.8 $\mu$Jy/beam (rms), which enabled us to achieve some of the faintest continuum detections at 1.1 mm and 1.3 mm with flux densities down to 60 $\mu$Jy." (abstract)
- Target **BDF-3299, BDF-521, SDF-46975 (Lyα emitters z~6-7) and other deep Band 6/7 fields**: coordinates _not stated_; z/distance z~6-7 for the Lyα targets; counts sources have unknown redshift  
  > "who targeted three Ly$\alpha$ emitters at z$\sim$6-7: BDF-3299, BDF-521 and SDF-46975" (2 Observations and data reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.A.00040.S, 2012.1.00374.S, 2012.1.00719.S, 2011.1.00115.S, 2011.1.00243.S, 2011.0.00767.S, 2012.1.00142.S, 2012.1.00523.S
- bands: Bands 6 and 7  
  > "For our analysis we focused on observations in Bands 6 and 7, since these are some of the deepest observations available." (2 Observations and data reduction)
- frequencies and spectral setup: four spectral windows; mean frequency 225-295 GHz  
  > "The correlator of each observation was configured to provide four independent spectral windows" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: BDF-3299 max 1270 m; BDF-521 17-1284 m; SDF-46975 max 422 m; SXDF-NB1006-2 ~558 m  
  > "In the extended configuration of 17-1284 m baseline for BDF-521, 29 12m antennae were used and 40 12m antennae with a maximum baseline of 422 m for SDF-46975." (2 Observations and data reduction)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 7.8 to 52.1 μJy/beam rms in 18 continuum maps  
  > "achieving a sensitivity in the range between 7.8 $\mu$Jy/beam (which is the deepest ALMA observation at this wavelength and three times deeper than data used in previous studies) and 52.1 $\mu$Jy/beam." (2 Observations and data reduction)
- time on source: BDF-3299 ~5.2 hr; BDF-521 83 min; SDF-46975 121 min; Capak fields ~20 min each; SXDF-NB1006-2 106 min  
  > "The total on-source integration time was $\sim$5.2 hr." (2 Observations and data reduction); "The total on source observing time was about 83 min and 121 min, respectively, for the two targets." (2 Observations and data reduction)
- observing dates: BDF-3299 Oct-Nov 2013 and Apr 2014; Capak data Nov 2013; SXDF-NB1006-2 3-4 May 2014  
  > "The target was observed on May 3-4, 2014 with a maximum baseline of $\sim$ 558 m." (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **AzTEC (bright-end counts, literature)**: 1.1 mm bright SMG counts from Scott et al. 2012 used for Schechter fit and integrated counts  
  > "We also show the number counts of bright (S \> $1$ mJy) SMGs obtained by (cite: Scott:2012) at 1.1 mm with AzTEC." (4.1 Differential number counts)
- External data: Bright-end 1.1 mm number counts (two faintest bins excluded)  
  > "However, the two faintest bins in the latter data are not considered when comparing models or when fitting analytic functions" (4.1 Differential number counts) [from (cite: Scott:2012)]
- External data: SMG SED: beta = 2.0, T = 35 K  
  > "We adopted a spectral index $\beta = 2.0$ and dust temperature T = 35 K from (cite: Greve:2012)" (3 Source extraction) [from (cite: Greve:2012)]
- External data: CIB from COBE: 25 (+22/-13) Jy/deg2 at 1.1 mm and 17 (+16/-9) at 1.3 mm  
  > "$25_{-13}^{+22}$ Jy deg$^{-2}$ at 1.1 mm and $17_{-9}^{+16}$ Jy deg$^{-2}$ at 1.3 mm" (4.5 Cosmic infrared background) [from (cite: Fixsen:1998)]
- External data: Faint 1.3 mm counts from ALMA for comparison  
  > "At 1.3 mm, the differential number counts of (cite: Hatsukade:2013) (orange symbols), which are obtained from sources with S/N$\geq4$, are consistent with our results within the uncertainties" (4.1 Differential number counts) [from (cite: Hatsukade:2013)]
- Simulation/model as data: Model number-count predictions from Hayward 2013, Shimizu 2012, Bethermin 2012, Cai 2013 compared with observed counts  
  > "We compared the differential and integrated number counts to the theoretical results obtained by recent simulations and semianalytical models." (4.2 Comparison with models)
- Simulation/model as data: Simulated blank-field ALMA observations (300 simobserve maps) used to test spurious detections  
  > "We simulated 300 continuum maps changing each time the parameter seed with a random value" (6 ALMA noise fluctuations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.2.1  
  > "All ALMA data were reduced using the CASA v4.2.1 package." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The typical flux uncertainties in the millimeter regime are $\sim10\%$." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "The continuum maps were cleaned using the CASA task clean with WEIGHTING = “natural”" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural  
  > "The continuum maps were cleaned using the CASA task clean with WEIGHTING = “natural”" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 1 arcsec diameter mask on main target (larger if extended)  
  > "Around all of these sources we placed a 1$''$ diameter mask ($\sim$ ALMA beam), since most of the main targets were non-spatially resolved." (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: all line-free channels of the four spectral windows used for continuum  
  > "The continuum maps were extracted using all the line-free channels of the four spectral windows." (2 Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 7.8-52.1 μJy/beam  
  > "(2) rms measured in each continuum map before primary beam correction." (Table 1)

### Inherited from earlier work

- Further details of the archival ALMA observations are in the original papers  
  > "Further details on the ALMA observations are summarised in those papers." (2 Observations and data reduction) [from (cite: Willott:2013); (cite: Ota:2014); (cite: MacGregor:2013); (cite: Ouchi:2013)]
- Number counts estimated at two wavelengths following prior ALMA count work  
  > "Following the prescription of (cite: Hatsukade:2013) and (cite: Ono:2014), we estimated the number counts at two different wavelengths: 1.1 mm and 1.3 mm." (4.1 Differential number counts) [from (cite: Hatsukade:2013); (cite: Ono:2014)]
- Alternative flux-boosting correction from Hogg & Turner Eq. 4  
  > "we show (with crosses and dashed error bars) the differential number counts by correcting for a boost factor that is estimated from Equation (4) of (cite: Hogg:1998)" (4.1 Differential number counts) [from (cite: Hogg:1998)]

### Not stated but needed to reproduce (our reading)

- Source-extraction code and the exact Gaussian-fitting tool used for 2D source fitting are not named
- Image size, cell size, clean threshold and iterations for each map
- Which line channels were flagged as line-free in each field
- Manual data-weight rescaling factors for BDF fields
- Precise source flux catalogue (positions, fluxes, S/N) for all 50 sources
- Binning edges and the counts per bin; Schechter fit weighting details
- Pipeline vs manual calibration of archival data and calibrator choices for most fields
- Cosmic variance tool inputs beyond those listed (field geometry)

## Analysis recipe

1. **Reduce and image continuum maps**: CASA reduction, data weights rescaled for some fields, continuum imaged from line-free channels with natural weighting  
  > "In the case of BDF-3299, BDF-521 and SDF-46975, the data weights were manually re-scaled as a function of integration time and channel width." (2 Observations and data reduction)
   - software: CASA
   - parameter: natural weighting; extraction within two primary beams (~20 arcsec diameter)  
  > "The source extraction was performed within an area as large as two primary beams that has a diameter of about 20”, before correcting for the primary beam attenuation." (3.1 Source catalogue)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract sources and set the detection threshold**: 2D Gaussian fit candidates with S/N>3.5 and size consistent with beam (at most 1.5x beam); negative-map test and blank-field simulations used to assess spurious sources  
  > "the size of the 2D Gaussian fitting the putative source must be consistent, within the errors, with the beam size of the selected map (or at most marginally resolved, within 1.5 times the beam size)." (3.1 Source catalogue)
   - software: CASA simobserve
   - parameter: S/N>3.5; 50 sources detected  
  > "In the 18 continuum maps, we detected 50 sources with S/N in the range 3.5-38.4, and none of them appear to be marginally resolved." (3.1 Source catalogue)
   - fitting: _not stated_
   - validation: maps multiplied by -1 to count negative sources; 300 simulated blank-field maps  
  > "The number of negative sources is equal to those of positive ones at any S/N" (6 ALMA noise fluctuations)
3. **Completeness and effective survey area**: Inject artificial sources, 1000 iterations per map, 4-8 per simulation, in 0.05-1 mJy; recovered if S/N>=3.5; A_survey = sum C_i A_i  
  > "we iterated the procedure of inserting artificial sources for each continuum map 1000 times, using four to eight artificial sources in each simulation for each field." (3.2 Completeness and survey area)
   - fitting: _not stated_
   - validation: _not stated_
4. **Flux boosting correction**: Inject sources with S/N 3-8 in maps not corrected for primary beam, 10^4 repeats, boost = S_out/S_in vs S/N  
  > "We repeated this simulation for each ALMA continuum map $10^4$ times." (3.3 Flux boosting)
   - parameter: boost ~1.09 at S/N=3.5  
  > "At S/N = 3.5, the boost fraction is $\simeq$1.09" (3.3 Flux boosting)
   - fitting: _not stated_
   - validation: Compared with Hogg & Turner Eq. 4 prescription using Schechter prior; slopes consistent  
  > "the slopes obtained with this correction factor are consistent with those obtained using a boost factor estimated in Sec." (4.1 Differential number counts)
5. **Scale fluxes to 1.1 and 1.3 mm**: Modified blackbody scaling; sources with lambda<1.2 mm scaled to 1.1 mm, others to 1.3 mm  
  > "using a modified blackbody with values typical of SMGs at z=2" (3 Source extraction)
   - parameter: beta = 2.0, T = 35 K, z=2; errors tested over 1<z<6, 20<T<60 K, 1.5<beta<2  
  > "we vary the SED properties in the following ranges: $1< z< 6$, 20 $<$T $<$60 K, $1.5< \ \beta< 2$." (7 Flux error)
   - assumption: SMG-like SED for all faint sources  
  > "Since we do not yet know either the spectral energy distributions (SEDs) or the redshifts of our faint mm sources" (3 Source extraction)
   - fitting: _not stated_
   - validation: flux error <18% per source  
  > "the error on the flux associated with each source is always less than 18%" (4.1 Differential number counts)
6. **Differential number counts with uncertainties**: Sum of (1-f_c)/A_survey in bins of dLogS=0.2, scaled to 1; f_c = negative/positive ratio at source S/N; errors from Poisson (Gehrels), cosmic variance (Moster tool), completeness/boosting  
  > "Therefore, the contribution of each source to the number counts is (1-$f_{\rm c}$) divided by its respective effective survey area $A_{\rm survey}(S)$." (4.1 Differential number counts)
   - software: Moster et al. 2011 cosmic variance tool
   - parameter: cosmic variance with z=3.5, dz=3, M*=10^10.5 Msun  
  > "We assume a mean redshift of $z=3.5$, a redshift bin size of $dz = 3,$ and a stellar mass of 10$^{10.5}$ $\mathrm{M}_{\odot}$" (4.1 Differential number counts)
   - fitting: _not stated_
   - validation: Poisson errors dominate; counts from within one primary beam consistent  
  > "the uncertainty on logarithmic differential number counts is completely dominated by the Poisson errors." (4.1 Differential number counts)
7. **Fit Schechter function**: chi2 minimisation of three-parameter Schechter function, separately at 1.1 and 1.3 mm, using this work plus literature counts  
  > "The three free parameters were then derived by $\chi^2$ minimisation." (4.3 Source counts parametrisation with a Schechter function)
   - fitting: chi2 minimisation  
  > "The three free parameters were then derived by $\chi^2$ minimisation." (4.3 Source counts parametrisation with a Schechter function)
   - validation: reduced chi2 0.9 (1.1 mm) and 1.1 (1.3 mm)  
  > "The reduced $\chi^2$ are 0.9 at 1.1 mm and 1.1 at 1.3 mm" (4.3 Source counts parametrisation with a Schechter function)
8. **Integrate counts and compare with CIB**: Integrate dN/dS * S above S_lim; compare to COBE CIB of Fixsen 1998; convert 60 μJy at 1.3 mm to L_IR and SFR  
  > "The integrated counts down to $S_{\rm limit} = 0.1$ mJy at 1.1 mm and to $S_{\rm limit} = 0.06$ mJy at 1.3 mm are $17^{+10}_{-5}$ Jy deg$^{-2}$ and $13^{+6}_{-3}$ Jy deg$^{-2}$ respectively." (4.5 Cosmic infrared background)
   - assumption: 1.3 mm flux corresponds to redshift-independent IR luminosity for 0.5<z<15; SFR from Kennicutt & Evans 2012  
  > "at 1.3mm a given observed flux density corresponds to an IR-luminosity (hence a SFR) that is nearly independent of redshift" (4.5 Cosmic infrared background)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: data reduction, clean imaging, simobserve simulations  
  > "All ALMA data were reduced using the CASA v4.2.1 package." (2 Observations and data reduction)
- **simobserve** CASA v4.2.1: synthetic blank-field observations  
  > "We used the simobserve CASA v.4.2.1 task to produce synthetic interferometric observations of a blank field" (6 ALMA noise fluctuations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of detected sources | 50 | not stated | sources | 2 | In the 18 continuum maps, we detected 50 sources with S/N in the range 3.5-38.4 |
| Total survey area at 1.1 mm | ~9.5e-4 | not stated | deg^2 | 1 | ${\rm \sim9.5\times10^{-4} 
 \ deg^2}$ at 1.1 mm and ${\rm \sim6.6\times10^{-4} \  deg^2}$ at 1.3 mm |
| Flux boost at S/N=3.5 | 1.09 | not stated | dimensionless | 4 | At S/N = 3.5, the boost fraction is $\simeq$1.09 |
| Schechter 1.1 mm: phi* | (2.7±0.9)e3 | 0.9e3 | deg^-2 | 7 | /  1.1 mm   /  $(2.7\pm0.9)\times10^{3}$  /    $2.6\pm0.4$    / $-1.81\pm0.14$ / |
| Schechter 1.1 mm: S* and alpha | S*=2.6 mJy, alpha=-1.81 | 0.4 mJy; 0.14 | mJy; dimensionless | 7 | /  1.1 mm   /  $(2.7\pm0.9)\times10^{3}$  /    $2.6\pm0.4$    / $-1.81\pm0.14$ / |
| Schechter 1.3 mm: phi*, S*, alpha | phi*=(1.8±0.4)e3 deg^-2, S*=1.7±0.2 mJy, alpha=-2.08±0.11 | as given | deg^-2; mJy; dimensionless | 7 | /  1.3 mm   /  $(1.8\pm0.4)\times10^{3}$  /    $1.7\pm0.2$    / $-2.08\pm0.11$ / |
| Integrated flux density resolved at 1.1 mm (S>0.1 mJy) | 17 | +10/-5 | Jy deg^-2 | 8 | $17^{+10}_{-5}$ Jy deg$^{-2}$ and $13^{+6}_{-3}$ Jy deg$^{-2}$ respectively |
| Integrated flux density resolved at 1.3 mm (S>0.06 mJy) | 13 | +6/-3 | Jy deg^-2 | 8 | $17^{+10}_{-5}$ Jy deg$^{-2}$ and $13^{+6}_{-3}$ Jy deg$^{-2}$ respectively |
| SFR at 60 μJy at 1.3 mm | 40 | not stated | Msun/yr | 8 | corresponds to a total IR luminosity $\rm L(8-1000\mu m)=6~\times10^{44}~erg~s^{-1}$, corresponding to a $\rm
SFR=40~M_{\odot}~yr^{-1}$ |

## Qualitative findings

- Integrated counts flatten at the faintest fluxes, consistent with models, suggesting most of the CIB is resolved  
  > "Such flattening of the number counts, fully consistent with the models, suggests that we are actually resolving most of the CIB at our faint fluxes." (4.5 Cosmic infrared background)

## Claim tuples

- H: Faint mm number counts can be measured with ALMA down to ~60 μJy | E: Source extraction in 18 deep Band 6/7 maps with completeness, boosting and spurious corrections | R: 50 sources at S/N>3.5; counts down to 60 μJy at 1.3 mm and 100 μJy at 1.1 mm; upper limits at 30 and 40 μJy | F: Counts flatten at faint fluxes and are flatter than earlier ALMA results | **supported**
- H: The counts follow a Schechter function | E: chi2 fit at 1.1 and 1.3 mm | R: alpha≈-1.8 and -2.1, reduced chi2 0.9 and 1.1 | F: Fits observed range but extrapolation to fainter fluxes is not trustworthy | **partially**
- H: Faint sources resolve a large fraction of the CIB | E: Integrate counts and compare with COBE CIB | R: 17 and 13 Jy/deg2 at 1.1 and 1.3 mm | F: At least 50% of the CIB is resolved, probably much more; sources with SFR<40 Msun/yr contribute <50% at 1.3 mm | **supported**

## Reasoning

- Why this data: Only continuum maps with rms <=50 μJy/beam selected to probe sub-mJy counts  
  > "We selected only continuum maps in Bands 6 and 7 with sensitivity $\leq~50\ \mu$Jy/beam" (2 Observations and data reduction)
- Why this method: Splitting maps into 1.1 and 1.3 mm groups minimises flux extrapolation errors  
  > "we split the number counts into two different wavelength ranges so as to reduce the flux errors associated to each detected source" (7 Flux error)
- Alternative: Scaling all maps to a common 1.15 mm wavelength rejected because flux errors approach 30%  
  > "the flux errors approach 30% at 1.1 mm" (7 Flux error)
- How they decided it was enough: _not stated_
- Limitation (authors): CIB uncertainties prevent a precise resolved fraction; no source redshifts or SEDs  
  > "we are not able to exactly determine the fraction of CIB resolved." (4.5 Cosmic infrared background)
- Caveat (inferred, ours): Fields are mostly targeted around high-z LAEs/QSOs, possibly biasing counts through clustering despite masking
- Caveat (inferred, ours): Single SED assumption for scaling fluxes
- Caveat (inferred, ours): Low-significance (S/N 3.5) detections with fc from negative counts
- Caveat (inferred, ours): Disagreement with lensing-cluster counts of Fujimoto et al. unresolved

## Reproducibility

- Data public (paper): Archival public ALMA data used; codes listed in acknowledgements  
  > "we analysed public archival ALMA data to increase the number of detections at intermediate flux densities." (2 Observations and data reduction)
- Products in archive: _not stated_
- Missing: Source extraction code/tool and parameters
- Missing: Imaging parameters (cell, size, thresholds)
- Missing: Source catalogue
- Missing: Per-field calibration details
- Data volume (inferred): ~100-300 GB raw for 18 fields from 8 projects
- Score (inferred): 3/5, Public data and a clear counting recipe, but extraction tool and imaging details are missing.
- Rediscovery candidate: yes, Data public, the pipeline is described and results are numeric, though some imaging settings are missing.

## Links

- Method: (cite: Hogg:1998) (flux boosting prescription)
- Method: (cite: Moster:2011) (cosmic variance tool)
- Companion: (cite: Maiolino:2015) (source of the deepest ALMA data)
- Related: Hatsukade et al. 2013 ALMA counts
- Related: Ono et al. 2014 ALMA counts
- Related: AzTEC survey (Scott et al. 2012)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00115.S",
  "2011.1.00243.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00115.S",
  "2011.0.00243.S"
 ],
 "codes_printed_but_missing": [
  "2011.1.00767.S"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 54,
  "rate": 0.607
 },
 "evidence_ok": true
}
```
