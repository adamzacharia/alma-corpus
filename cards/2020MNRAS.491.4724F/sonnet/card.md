# A3COSMOS: the dust attenuation of star-forming galaxies at z = 2.5-4.0 from the COSMOS-ALMA archive

`2020MNRAS.491.4724F` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Fudamoto, Yoshinobu | arXiv: 1910.12885 | DOI: 10.1093/mnras/stz3248

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: How do the IRX-beta and IRX-stellar mass relations of star-forming galaxies at z=2.5-4.0 behave, using ALMA archival continuum data in COSMOS?  
  > "we update our previous studies on the IRX-$\beta$ and the IRX-$M_{\ast}$ relationship of star forming galaxies at $z=2.5-4.0$ using individual FIR flux measurements for 1512 galaxies" (1 Introduction)
- Target **COSMOS field star-forming galaxies at z=2.5-4.0 (1512)**: coordinates _not stated_; z/distance z=2.5-4.0, median z_ph=2.95  
  > "using the photometric redshifts from the COSMOS2015 catalogue" (3 Star Forming Galaxy Sample Selection); distance from COSMOS2015 photometric redshifts  
  > "using the photometric redshifts from the COSMOS2015 catalogue" (3 Star Forming Galaxy Sample Selection)

## Data provenance

- ALMA projects: 2015.1.00379.S
- bands: ALMA band 6 and band 7  
  > "We made use of all the ALMA archival band 6 and band 7 observations in the COSMOS field" (2.1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.5-1.8 arcsec, median 1.1 arcsec  
  > "synthesised beam sizes of $0.5^{\prime\prime} - 1.8^{\prime\prime}$ with median beam size of $1.1^{\prime\prime}$" (2.1)
- max recoverable scale: _not stated_
- sensitivity: median RMS 126 uJy/beam (std 91)  
  > "the median continuum sensitivity has an RMS of $126\,\rm{\mu Jy/beam}$" (2.1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **COSMOS2015 catalogue**: photometric redshifts, stellar masses, SFRs, photometry for beta/L_UV  
  > "Stellar masses are also taken from the COSMOS2015 catalogue" (3 Star Forming Galaxy Sample Selection)
- Other facility **Chandra**: X-ray AGN exclusion  
  > "we exclude galaxies that have counterparts in the deep Chandra X-ray catalogue of (cite: Civano2016)." (3)
- Other facility **Herschel**: stacked FIR fluxes to validate SED  
  > "we performed a stacking analysis of the *Herschel* images in two different mass bins" (Appendix)
- External data: IR SED template for z~3 galaxies (alpha_dale=1.7, logM 10.25-10.75)  
  > "we use the empirical SED template that was previously derived for $z\sim3$ galaxies by (cite: AlvarezMarquez2016)." (3.2) [from (cite: AlvarezMarquez2016)]
- External data: Main-sequence relation vs redshift  
  > "The main-sequence (MS) relation as a function of redshift is taken from (cite: Schreiber2015)" (3.4) [from (cite: Schreiber2015)]
- External data: Chandra X-ray catalogue  
  > "deep Chandra X-ray catalogue of (cite: Civano2016)" (3) [from (cite: Civano2016)]

## Processing

### Calibration

- pipeline or manual: QA2 scriptForPI.py scripts with the CASA version specified  
  > "all the data are calibrated using the script released by the QA2 analyst for each PI project (i.e. $\rm{scriptForPI.py}$)" (2.1)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=2 (natural), CLEAN stop S/N=4, to primary beam 0.2  
  > "Briggs weighting scheme with a stopping threshold of $S/N=4$ and a robustness parameter of 2 (i.e. natural weighting)" (2.1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to RMS  
  > "after applying primary beam corrections" (2.1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data acquisition, imaging, source extraction, FIR photometry  
  > "All the steps of our data acquisition, imaging, source extraction, and FIR continuum photometry are fully described in our data release paper (cite: Liu2018)" (2) [from (cite: Liu2018)]
- Aperture-flux stacking method  
  > "we decided to opt for the simplest solution and to follow (cite: Mclure2018)" (3.5) [from (cite: Mclure2018)]
- Herschel stacking and clustering correction  
  > "using the same method and clustering correction as in (cite: Magnelli2014)" (Appendix) [from (cite: Magnelli2014)]

### Not stated but needed to reproduce (our reading)

- A3COSMOS catalogue version and exact list of images/pointings
- Numerical SED template file
- Stacking uncertainty/upper-limit method details
- Exact starburst/MS SFR formula parameters
- ZEBRA+ configuration

## Analysis recipe

1. **Sample selection**: Select COSMOS2015 galaxies at z=2.5-4.0 with dz/(1+z)<0.2 in ALMA pointings within half primary beam, beam minor axis >0.5"; remove X-ray and IRAC AGN  
  > "we only select galaxies with accurately determined photometric redshifts, $\delta_{\rm{z_{\rm{ph}}}}/(1.0+z_{\rm{ph}}) < 0.2$" (3)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive L_IR from ALMA flux**: Scale redshifted SED template to ALMA flux, integrate 8-1000 um; 3 sigma upper limits for non-detections  
  > "We redshift this SED template to the $z_{\mathrm{ph}}$ of each galaxy and rescale it to the measured ALMA flux." (3.2)
   - software: GALFIT
   - assumption: Fixed z~3 SED template; +-0.2 dex systematic  
  > "we find a systematic spread of $\pm0.2\,\rm{dex}$ on $L_{\rm{IR}}$" (3.2)
   - fitting: _not stated_
   - validation: Compared with other templates and Herschel stacks  
  > "The validity of our baseline SED is, however, confirmed by stacks of far-IR fluxes from our galaxy sample." (Appendix)
3. **Measure beta and L_UV**: SED fitting of COSMOS2015 photometry; beta over 1500-2500 A, median of marginalised PDF; L_UV at 1600 A  
  > "we calculate $\beta$ over the wavelength range of $1500<\lambda<2500\,$Å" (3.3)
   - software: ZEBRA+
   - assumption: Calzetti and SMC extinction curves  
  > "we assumed two sets of extinction curves of local star forming galaxies (cite: Calzetti2001) and that measured for the SMC (cite: Gordon2003)" (3.3)
   - fitting: chi2-based marginalised PDF  
  > "we derive a marginalised probability distribution function of $\beta$ for each individual galaxy based on the $\chi^2$ values of each template" (3.3 $L_{\rm{UV}}$ and $\beta$ Measurements)
   - validation: beta-Mstar relation agrees with McLure2018  
  > "this relation is in excellent agreement with (cite: Mclure2018)" (3.3)
4. **Total SFR and MS/starburst classification**: Kennicutt1998 SFR_UV+SFR_IR; starburst if SFR >3x Schreiber2015 MS  
  > "we defined galaxies as starbursts when they have SFR three times larger than the MS at their photometric redshift" (3.4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Stacking**: 2 arcsec aperture flux per galaxy with dirty-beam area correction, RMS-weighted stacks in bins of beta and mass  
  > "We measure the ALMA flux of each galaxy within an aperture with a fixed radius of 2 arcsec." (3.5)
   - fitting: Linear fit to detected stacks for IRX-Mstar  
  > "The linear fit to the detected stacked data points (the first three green diamonds) results in the following equation for the IRX-$M_{\ast}$ relation:" (4.2 IRX-$M_{\ast}$ Relation)
   - validation: Visibility-domain stack of 61 spec-z galaxies  
  > "we employed a stacking method in the visibility domain, as described in (cite: Lindroos2015)" (4.2.1)

## Software

- **CASA** : calibration (version per QA2 script)  
  > "we used the appropriate version of CASA as specified by the scripts" (2.1)
- **GALFIT** : ALMA photometry on deconvolved images  
  > "The photometry from the ALMA images is obtained using GALFIT" (2.1)
- **LePhare** : COSMOS2015 stellar masses  
  > "estimated using the $\rm{LePhare}$ SED fitting code" (2.2)
- **ZEBRA+** : UV slope and L_UV SED fitting  
  > "The photometry is then fitted using the code ZEBRA+" (3.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Final sample size | 1512 | not stated | galaxies | 1 | Our final sample then includes 1512 galaxies at $z=2.5-4.0$ |
| ALMA >3 sigma detections | 172 | not stated | galaxies | 2 | 172 galaxies out of this sample are detected at more than 3$\sigma$ with ALMA |
| IRX scatter, massive galaxies | 0.27 | not stated | dex | 5 | The random scatter around the mean relation is only $\sigma_\mathrm{IRX}\sim 0.27\,\rm{dex}$ |
| IRX-Mstar slope | 1.64 | 0.13 | dimensionless | 5 | \rm{log\,IRX} = (1.64 \pm 0.13)\times \rm{log\,}M_{\ast} - (16.18\pm 1.35 \pm0.2) |
| Spec-z stack flux density | 56 | 9 | uJy/beam | 5 | with a flux density of $56\pm9\,\rm{\mu Jy/beam}$ |

## Qualitative findings

- Massive galaxies follow M99 IRX-beta; starbursts offset ~0.5 dex higher  
  > "while starbursts are generally offset by $\sim0.5\,{\rm dex}$ to larger IRX values" (abstract)

## Claim tuples

- H: Do massive z~3 galaxies follow the local IRX-beta relation? | E: Individual detections and stacks in beta bins | R: Stacks follow M99 with 0.27 dex scatter | F: No evolution for massive galaxies | **supported**
- H: Is IRX-Mstar steeper than previously reported? | E: Stacks in mass bins, spec-z check | R: Slope 1.64; low-mass IRX lower by >=0.5 dex | F: Little dust at logM<10; possible evolution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): IR SED shape/dust temperature could change slope; low-mass stacks only upper limits  
  > "Systematic changes of the dust temperature or SED shapes as a function of stellar mass could affect the slope" (5)
- Caveat (inferred, ours): Photometric redshifts and single fixed SED drive L_IR
- Caveat (inferred, ours): Heterogeneous archival depth and serendipitous sources

## Reproducibility

- Data public (paper): Public archival ALMA data  
  > "In this section, we present our sample obtained from the public ALMA archive in the COSMOS field." (2)
- Products in archive: _not stated_
- Missing: A3COSMOS catalogue access details
- Missing: SED template file
- Data volume (inferred): hundreds of GB for ~1500 pointings; catalogue-based reproduction far smaller
- Score (inferred): 3/5, Public data and clear recipe, but relies on external catalogues and inherited processing.
- Rediscovery candidate: no, Depends on A3COSMOS processing and external catalogues, with incomplete stacking details.

## Links

- Method: (cite: Liu2018) (A3COSMOS data processing and photometry)
- Method: (cite: Mclure2018) (stacking approach)
- Companion: (cite: Fudamoto2018) (pilot study)
- Related: A3COSMOS
- Related: COSMOS2015

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
 "obscore_codes_not_in_card": [
  "2011.0.00064.S",
  "2011.0.00097.S",
  "2011.0.00539.S",
  "2012.1.00076.S",
  "2012.1.00323.S",
  "2012.1.00523.S",
  "2012.1.00536.S",
  "2012.1.00978.S",
  "2013.1.00034.S",
  "2013.1.00118.S",
  "2013.1.00151.S",
  "2013.1.00208.S",
  "2013.1.00276.S",
  "2013.1.00668.S",
  "2013.1.00815.S",
  "2013.1.00884.S",
  "2013.1.01258.S",
  "2013.1.01292.S",
  "2015.1.00026.S",
  "2015.1.00055.S",
  "2015.1.00122.S",
  "2015.1.00137.S",
  "2015.1.00260.S",
  "2015.1.00299.S",
  "2015.1.00388.S",
  "2015.1.00540.S",
  "2015.1.00568.S",
  "2015.1.00664.S",
  "2015.1.00704.S",
  "2015.1.00928.S",
  "2015.1.01074.S",
  "2015.1.01105.S",
  "2015.1.01111.S",
  "2015.1.01171.S",
  "2015.1.01212.S",
  "2015.1.01495.S",
  "2016.1.00478.S",
  "2016.1.00624.S",
  "2016.1.00735.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
