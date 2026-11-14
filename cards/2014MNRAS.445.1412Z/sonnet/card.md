# Two physical regimes for the giant H II regions and giant molecular clouds in the Antennae galaxies

`2014MNRAS.445.1412Z` | Monthly Notices of the Royal Astronomical Society 2014 | first author: Zaragoza-Cardiel, J. | arXiv: 1409.1251 | DOI: 10.1093/mnras/stu1847

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do the physical properties of GMCs (ALMA CO(3-2)) and HII regions (GHaFaS Halpha) in the Antennae compare, and do they show two regimes (external pressure vs gravity dominated)?  
  > "We have measured, and compared, their basic physical properties (radius, velocity dispersion, luminosity)." (abstract)
- Target **Antennae galaxies (Arp 244, NGC 4038/4039)**: coordinates _not stated_; z/distance 22 Mpc  
  > "Assuming a distance to the Antennae of $22\mathrm{Mpc}$ (cite: 2008AJ....136.1482S)" (2.1 ALMA observations); distance from Schweizer et al. 2008  
  > "Assuming a distance to the Antennae of $22\mathrm{Mpc}$ (cite: 2008AJ....136.1482S)" (2.1 ALMA observations)

## Data provenance

- ALMA projects: 2011.0.00876.S, 2011.0.00003.SV
- bands: Band 7 CO(3-2) (Science Verification Band 7 per URL)  
  > "We present two sets of observations of the Antennae: data cubes of emission in H$\alpha$ from the ionized component of the interstellar medium, and of emission in the CO(3-2) line" (2.1 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 to 402 m (Early Science)  
  > "baselines from $21$ to $402$ m" (2.1 ALMA observations)
- angular resolution: ~0.6x1.1 arcsec (SV); ~0.4x0.7 arcsec (ES)  
  > "synthesized beam $\sim 0.6\rm{arcsec}\times 1.1\rm{arcsec}$ for the Science Verification data, synthesized beam $\sim 0.4\rm{arcsec}\times 0.7\rm{arcsec}$ for the Early Science data" (2.1 ALMA observations)
- max recoverable scale: structures >420 pc (ES) and >354 pc (SV) not detected  
  > "Larger than $420$pc structures for Early Science and larger than $354$pc structures for Science Verification are not detected due to the lack of short and zero spacing." (2.1 ALMA observations)
- sensitivity: 1-channel rms 3 mJy/beam (SV), 2 mJy/beam (ES), 10 km/s channels  
  > "$l_{\mathrm{rms}}=3\thinspace\mathrm{mJy/beam}$ for the Science Verification data and $l_{\mathrm{rms}}=2\thinspace\mathrm{mJy/beam}$ for the Early Science data" (2.1 ALMA observations)
- time on source: 3 h (Early Science)  
  > "The total on source time is $3$ h with 14 to 24 antennas and baselines from $21$ to $402$ m." (2.1 ALMA observations)
- observing dates: Early Science: 2012 July to November  
  > "The Early Science mosaic is derived from a series of observations from 2012 July to November." (2.1 ALMA observations)
- pi or archival as stated: SV data and Cycle 0 Early Science archive data  
  > "The first two mosaics of the observations in the CO(3-2) line are from the ALMA Science Verification programme" (2.1 ALMA observations)
- Line: CO 3-2 (345.796 GHz)
- Other facility **GHaFaS on WHT**: Halpha Fabry-Perot data cube of HII regions, 0.9 arcsec seeing, 8 km/s resolution  
  > "The seeing limited angular resolution of $0.9 \rm{arcsec}$, $96pc$ at the assumed distance of $22\mathrm{Mpc}$" (2.2 GHaFaS observations)
- Other facility **HST archival**: Halpha F658N and Hbeta F487N images for dust extinction correction  
  > "we used archival *HST* data of The Antennae galaxies with narrow band filters in H$\alpha$ F658N, and H$\beta$ F487N" (3.1.1)
- Other facility **ACAM on WHT**: Halpha image for flux calibration of GHaFaS  
  > "A continuum-subtracted and flux-calibrated ACAM (auxiliary-port camera) H$\alpha$ image was used to perform the flux calibration of the GH$\alpha$FaS data." (2.2 GHaFaS observations)
- External data: SMA CO(3-2) GMC catalogue of the Antennae, for comparison  
  > "shows the mass-radius relation for molecular clouds (blue) compared with data of the Antennae from (cite: 2012ApJ...745...65U) (green)" (4 Results) [from Ueda et al. 2012 (cite: 2012ApJ...745...65U)]
- External data: M51 GMC properties incl. virial parameter  
  > "We have added the GMCs detected in (cite: 2014ApJ...784....3C) for M51 since they estimated the virial parameter." (5 Gravitationally bound regime) [from Colombo et al. 2014 (cite: 2014ApJ...784....3C)]
- External data: Milky Way GMC properties  
  > "we were obliged to use the results of the GMC’s in the Milky Way from (cite: 2010ApJ...723..492R)" (4.3) [from Roman-Duval et al. 2010]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used reduced Early Science mosaic from the archive  
  > "We have used the reduced mosaic published in the archive where the raw data have been corrected for atmospheric effects, and flux, bandpass, phase, and amplitude calibrations have been applied." (2.1 ALMA observations)
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
- primary beam correction: Applied to SV and ES mosaics  
  > "We then corrected the Science Verification and the Early Science mosaics for the primary beam response." (2.1 ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 3 mJy/beam (SV), 2 mJy/beam (ES) per 10 km/s channel  
  > "with a channel size of $10\mathrm{km/s}$ in both cases" (2.1 ALMA observations)

### Inherited from earlier work

- Science Verification data description  
  > "The Science Verification data have been described in (cite: 2012A&A...538L...9H)." (2.1 ALMA observations) [from (cite: 2012A&A...538L...9H)]
- Fabry-Perot data processing  
  > "For details of the data processing of the Fabry-Perot data we refer the reader to (cite: 2010MNRAS.407.2519B)." (2.2 GHaFaS observations) [from (cite: 2010MNRAS.407.2519B)]
- Molecular mass from CO luminosity and alpha_CO=4.8, as in Wei et al.  
  > "As in (cite: 2012ApJ...750..136W), the molecular gas mass was estimated from the CO luminosity following (cite: 1992ApJ...398L..29S)" (3.2) [from (cite: 2012ApJ...750..136W)]
- Bootstrap error method  
  > "We have followed the procedure (the bootstrapping method) explained in (cite: 2006PASP..118..590R) to derive the errors in the measured properties." (3.3 Uncertainties) [from (cite: 2006PASP..118..590R)]
- Luminosity-sigma envelope method  
  > "We follow the method of (cite: 2005A&A...431..235R) to estimate the envelope." (5) [from (cite: 2005A&A...431..235R)]

### Not stated but needed to reproduce (our reading)

- Exact SV and ES calibrated product file names and versions
- Dendrogram parameters beyond 4 sigma (min_delta, min_npix numbers)
- Whether SV and ES cubes were regridded or merged
- Exact mosaic pointing/field coordinates
- Weighted-fit/error treatment details for the double linear fit
- Mass-function binning

## Analysis recipe

1. **Prepare cubes and moment maps**: Primary-beam correct archival ALMA mosaics; build moment maps masked at 4 x rms  
  > "The velocity and velocity dispersion maps have been masked in order to consider only locations where the line is stronger than a minimum detectable value: $4\times l_{\mathrm{rms}}$." (2.1 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify regions and measure size, sigma_v, flux**: Dendrogram (bijection paradigm) on ALMA and GHaFaS cubes; second moments give R=1.91*sqrt(sig_maj sig_min)  
  > "The radius, assuming a spherical region, is $R=\eta\sqrt{\sigma_{\mathrm{maj}}\thinspace\sigma_{\mathrm{min}}}$, where $\eta=1.91$." (3 Properties of HII regions and GMCs)
   - software: astrodendro
   - parameter: T_edge = 4 x l_rms  
  > "The value of $T_{\mathrm{edge}}$ adopted here is $T_{\mathrm{edge}}=4\times l_{\mathrm{rms}}$." (3 Properties of HII regions and GMCs)
   - fitting: _not stated_
   - validation: Bootstrapping errors; regions with size error >20% removed (leaving 201 HII regions, 89 GMCs)  
  > "After removing the regions most affected by the noise, the number of H regions is 201 and the number of GMCs is 89." (3.3 Uncertainties)
3. **Derive GMC masses and virial parameters**: CO luminosity (Solomon 1992) times alpha_CO, with factors 1.8 and 1.36; alpha_vir=5 sigma^2 R/(G M)  
  > "assuming $\alpha_{\mathrm{CO}}=4.8\thinspace M_{\odot} (\mathrm{K}\thinspace \mathrm{km}\thinspace \mathrm{s}^{-1}\thinspace \mathrm{pc}^2)^{-1}$" (3.2)
   - assumption: D=22 Mpc, CO(1-0)/CO(3-2)=1.8, helium factor 1.36, spherical clouds  
  > "we have applied a factor of 1.36 in order to take into account helium and heavier elements" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive HII region properties**: Dust-correct Halpha with HST Balmer decrement pixel by pixel; ionized mass M=1.57e-17 sqrt(L R^3); SFR via Kennicutt 2009; subtract natural (3 km/s) and thermal (9.1 km/s) widths  
  > "Assuming case B recombination the intrinsic Balmer line ratio is $L_{{\mathrm H\alpha}}/L_{{\mathrm H\beta}}=2.87$" (3.1.1)
   - assumption: Calzetti curve K(Ha)=3.33, K(Hb)=4.60; spherical uniform density; T=1e4 K  
  > "$K({\mathrm H\alpha}) = 3.33$ and $K({\mathrm H\beta}) = 4.60$" (3.1.1)
   - fitting: _not stated_
   - validation: SFR compared with Brandl et al. 2009  
  > "compatible with our SFR estimated for the brightest H regions" (3.1.2)
5. **Fit mass-radius relations and find regime break**: Error-weighted linear fit for GMCs; double linear fit with free transition for HII regions  
  > "Here we have performed a double linear fit to the ionized gas mass-radius relation, keeping as a fit coefficient the transition between one linear fit and another one." (4.2)
   - fitting: _not stated_
   - validation: Compared with MW, M51 and Ueda et al. data  
  > "Fig. [2] (a) shows the mass-radius relation for molecular clouds (blue) compared with data of the Antennae from (cite: 2012ApJ...745...65U) (green)." (Results)
6. **Test gravity vs pressure dominance**: L_Ha-sigma_v envelope fit (minimum sigma per luminosity bin), shifted envelope criterion L>Lenv/40, virial parameter vs mass  
  > "we consider that region is close to the envelope if $L_{{\mathrm H\alpha}}>\frac{L_{{\mathrm H\alpha}\thinspace \mathrm{env}}}{40}$" (5)
   - fitting: linear in log-log  
  > "We have assumed, for simplicity, that the regions lying on the envelope follow a linear relation in the log-log plane" (Gravitationally bound regime)
   - validation: HII region age from Halpha equivalent width shows no age difference between regimes  
  > "We can see that the age ranges for two populations of H regions are the same." (5.1)

## Software

- **astrodendro** : dendrograms to derive properties of HII regions and GMCs  
  > "We used DENDROGRAM, a PYTHON package to compute dendrogramsof astronomical data" (3)
- **Astropy** : general analysis  
  > "This research made use of ASTROPY, a community-developed core textscpython package for astronomy" (Acknowledgements)
- **APLpy** : plotting  
  > "APLPY, an open-source plotting package for textscpython" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of GMCs | 142 | not stated | dimensionless | 2 | enabling us to identify 142 giant molecular clouds (GMCs) and 303 H regions |
| Number of HII regions | 303 | not stated | dimensionless | 2 | enabling us to identify 142 giant molecular clouds (GMCs) and 303 H regions |
| GMC mass-radius slope | 2.62 | 0.10 | dimensionless | 5 | \log(M_{\mathrm{mol}})=(2.4\pm0.4)+(2.62\pm0.10)\log(R_{\mathrm{CO}}) |
| HII region slope, low-mass regime | 1.8 | 0.3 | dimensionless | 5 | (1.6\pm0.4)+(1.8\pm0.3)\log(R_{HII}) |
| HII region slope, high-mass regime | 3.7 | 0.2 | dimensionless | 5 | (-1.7\pm0.5)+(3.7\pm0.2)\log(R_{HII}) |
| HII transition mass | log M=5.4 | not stated | log Msun | 5 | The transition at $\log(R_{\mathrm{HII}})=1.92$ corresponds to a transition at $\log(M_{\mathrm{HII}})=5.4$ |
| GMC mass function break | log M~6.7 | not stated | log Msun | 5 | We find a break in the molecular gas mass function at $\log(M_{\mathrm{mol}})\sim6.7$ |
| Envelope fit | beta1=2.3, beta0=38.0 | not stated | dimensionless | 6 | The result is $\beta_1=2.3$, $\beta_0=38.0$ |
| Ionized gas fraction | ~0.05 | not stated | dimensionless | 5 | the ionized gas to total gas fraction is $\sim 0.05$ |

## Qualitative findings

- HII regions are ~6 Myr old in both regimes; no obvious correlation of regime with location  
  > "The H regions are around $6 \mathrm{Myr}$ old." (5.1)

## Claim tuples

- H: GMC surface density is constant with size | E: Mass-radius fit of ALMA GMCs | R: slope 2.62±0.10 | F: Surface density increases with radius, unlike previous studies | **supported**
- H: HII regions show two regimes | E: Double linear fit of M_HII-R | R: slopes 1.8 and 3.7, break at log M=5.4 | F: Density decreases with mass below and increases above the break | **supported**
- H: Regimes differ by dominant binding force | E: Virial parameter and L-sigma envelope | R: alpha_vir decreases with mass | F: Gravity dominates at high mass, external pressure at low mass | **partially**

## Reasoning

- Why this data: ALMA and GHaFaS have comparable angular and spectral resolutions  
  > "The two sets of observations have comparable angular and spectral resolutions" (abstract)
- Why this method: _not stated_
- Alternative: Age evolution as explanation of the two populations rejected using Halpha equivalent width  
  > "Thus, H region ages do not play an important role in the scaling relations of the two regimes in the Antennae." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of short and zero spacings; alpha_CO uncertain; no low-mass GMCs detected  
  > "There is a conflict for the value of $\alpha_{\mathrm{CO}}$ in the Antennae" (3.2)
- Caveat (inferred, ours): alpha_CO choice strongly affects mass-radius slope
- Caveat (inferred, ours): Inhomogeneous sensitivity/resolution and resolution-limited sizes bias the slope
- Caveat (inferred, ours): Combining MW, M51 and Antennae data for GMC regime claim
- Caveat (inferred, ours): Ionized gas mass as proxy for total gas in virial parameters

## Reproducibility

- Data public (paper): ALMA data from public archive/SV; reduced Halpha cube available through CDS  
  > "The reduced H$\alpha$ data cube and the derived moment maps are available through CDS." (2.2 GHaFaS observations)
- Products in archive: _not stated_
- Missing: Dendrogram parameters
- Missing: Exact archive product versions
- Missing: Fit implementation details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 5/5, Public data and clear formulas, but dendrogram settings and fitting details are missing.
- Rediscovery candidate: yes, Public ALMA data, clear recipe, numeric results (slopes, breaks), though some parameters missing.

## Links

- Method: Rosolowsky et al. 2008 (cite: 2008ApJ...679.1338R) (dendrogram method)
- Method: Rosolowsky & Leroy 2006 (cite: 2006PASP..118..590R) (property extraction and bootstrap errors)
- Companion: Wei et al. 2012 (cite: 2012ApJ...750..136W) (SMA/PdBI GMC study of the Antennae)
- Companion: Ueda et al. 2012 (cite: 2012ApJ...745...65U) (SMA CO(3-2) GMCs in the Antennae)
- Related: ALMA Science Verification Antennae Band 7

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 47,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
