# From kpcs to the central parsec of NGC 1097: feeding star formation and a black hole at the same time

`2019MNRAS.485.3264P` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Prieto, M. Almudena | arXiv: 1902.09370 | DOI: 10.1093/mnras/stz579

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation, agn_and_quasars
- Question: How are the star clusters, star formation history and dust-gas filaments in the circumnuclear ring of NGC 1097 connected to the feeding of the ring and the black hole?  
  > "A panchromatic view of the star forming ring and feeding process in the central kpc of the galaxy NGC 1097 is presented." (abstract)
- Target **NGC 1097**: coordinates _not stated_; z/distance 14.5 Mpc  
  > "A distance to NGC 1097 of 14.5 Mpc (Tully 1988) is used, 1 arcsec = 70 pc." (Introduction); distance from Tully 1988  
  > "A distance to NGC 1097 of 14.5 Mpc (Tully 1988) is used, 1 arcsec = 70 pc." (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (88 GHz)  
  > "archived ALMA data in band 3 (centred at 88 GHz)" (Multiwavelength dataset)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2.2 x 1.5 arcsec^2 beam  
  > "The HCN line-map has a beam resolution of $\sim 2.2 \times 1.5\, \rm{arcsec^2}$" (Multiwavelength dataset)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "The set is further complemented with archived ALMA data in band 3" (Multiwavelength dataset)
- Line: HCN J=1-0 (88.6 GHz)
- Other facility **HST (WFC3, NICMOS)**: UV to near-IR continuum and Halpha/Paalpha images  
  > "The sources are *Hubble Space Telescope* (*HST*) images from Wide-Field Camera 3 (WFC3)" (Multiwavelength dataset)
- Other facility **VLT NACO and VISIR**: J, H, Ks, L-band AO images and 11.88/18.72 micron images  
  > "ESO-Very Large Telescope (VLT) data from the Adaptive-Optics-assisted NACO camera in J-, H- , Ks- and L-bands from Prieto et al. (2005)" (Multiwavelength dataset)
- Other facility **Chandra**: X-ray image shown, not analysed  
  > "the deepest available X-rays Chandra image of the central kpc of the galaxy is shown on top of the HST-UV image in Fig. 1" (Multiwavelength dataset)
- External data: Molecular gas mass of ring ~1e9 Msun, ring rotation ~350 km/s, CO clouds and column densities  
  > "The amount of gas stored in the ring is found $\rm M_{\rm H_{2}} \sim 10^9\, \rm{M_\odot}$ (as derived from the HCN gas, Hsieh et al. 2011)." (6.2 Build up of the ring stellar mass) [from Hsieh et al. 2011]
- External data: VISIR 11 and 18 micron images  
  > "diffraction-limited, line-free VISIR images in narrow-band continuum filters centred at $11.88\, \rm{\ensuremath{\mu}m}$ and $18.72\, \rm{\ensuremath{\mu}m}$ from Reunanen et al. (2010)" (Multiwavelength dataset) [from Reunanen et al. (2010)]
- Simulation/model as data: Charlot & Bruzual SSP models, solar metallicity, Kroupa IMF, used for cluster SED fits  
  > "Ages and masses were determined by SED fits using Charlot & Bruzual latest update of their Single Stellar Population (SSP) models." (4 Cluster properties)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: HCN line map extracted from the archive calibrated data cube  
  > "the HCN(1-0) 88.6 GHz line map from the calibrated data cube in the archive was extracted" (Multiwavelength dataset)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Registration of HST and VLT images  
  > "The achieved registration precision is $\sim$ 30 mas (see Mezcua et al. 2015 for details)." (Multiwavelength dataset) [from Mezcua et al. 2015]
- Extinction map procedure  
  > "The creation of the Av map follows the procedure outlined in e.g. Prieto et al. (2014)." (5 The network of dust filaments) [from Prieto et al. (2014)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction, CASA version, and moment-map construction for HCN
- Noise level and flux scale of the HCN map
- Registration offsets used for the ALMA map
- How the HCN gas mass was obtained, and whether CO was used

## Analysis recipe

1. **Extract cluster photometry and fit SEDs for age and mass**: Aperture photometry of 247 clusters, chi^2 SED fits with Charlot & Bruzual SSPs for 171 UV-detected clusters  
  > "Cluster’s SED fitting was done via a $\chi^2$ minimisation. Free parameters in the fit are the cluster mass, age, and continuum dust extinction." (4 Cluster properties)
   - parameter: aperture radius 0.15 arcsec, background annulus 0.2-0.3 arcsec  
  > "Cluster photometry in the 0.3 – 5$\, \rm{\ensuremath{\mu}m}$ region was done in an aperture radius r = $0.15\ensuremath{''}$" (3.2 Clusters size)
   - assumption: Solar metallicity, Kroupa IMF  
  > "The models used are based on solar metallicity," (4 Cluster properties)
   - fitting: chi^2 minimisation  
  > "Cluster’s SED fitting was done via a $\chi^2$ minimisation." (4 Cluster properties)
   - validation: Compared with stochastic IMF models and median age of 10 best fits  
  > "the assigned age to each cluster is the median of its 10 best fits ranked by their $\chi^2$" (4.1 Recurrent star formation in the ring)
2. **Locate proto-clusters relative to ALMA HCN clouds**: Compare VISIR 18 micron point sources with HCN(1-0) peaks; grey body fit for temperature  
  > "the location of these sources just coincides with the emission peak of an equivalent number of ALMA / HCN(1-0) molecular clouds resolved in the ring" (4.2 The proto-cluster population)
   - parameter: beta = 1.6  
  > "Assuming a standard dust emissivity with a power law exponent $\beta = 1.6$" (4.2 The proto-cluster population)
   - fitting: grey black-body fit to 11-18 micron SED  
  > "An estimate of their temperature is inferred from fitting a grey black-body to their $11$–$18\, \rm{\ensuremath{\mu}m}$ SED." (4.2 The proto-cluster population)
   - validation: _not stated_
3. **Build extinction map and estimate streamer mass inflow**: I/B image ratio converted to Av, then N_H, density, filling factor and cylinder flow rate  
  > "a mass arrival rate $\dot{M}_{\rm entrance-ring}$ $\sim > 3\, \rm M_\odot \, yr^{-1}$ is found." (6.2.1 Arrival mass)
   - assumption: N_H/A_V = 2e21 cm^-2 mag^-1; filament depth equals width  
  > "$N_{\rm H} / A_V = 2 \times 10^{21}\, \rm{cm^{-2}\,mag^{-1}}$ (Savage & Mathis 1979)" (6.2 Build up of the ring stellar mass)
   - fitting: _not stated_
   - validation: Extinction maps from other band ratios gave consistent results  
  > "Extinction maps based on other continuum image ratios, namely VLT/NACO Ks-band- and HST/WFC3 F814W-, F438W-, and F336W- images yielded consistent results" (5 The network of dust filaments)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of star clusters identified | 247 | not stated | clusters | 1 | a total of 247 individually resolved star clusters detected above a 3 sigma level |
| Current SFR in ring | 1.8 | not stated | Msun/yr | 0 | $SFR = 1.8\, \rm{M_\odot \, yr^{-1}} \times ~F({\rm Pa\alpha})_{\rm corr} |
| Gas depletion time | 5e8 | not stated | yr | 0 | $10^9\, \rm{M_\odot} / 1.8\, \rm{M_\odot \, yr^{-1}} \sim 5\times 10^8 yr$ |
| Streamer arrival mass rate | >~3 | not stated | Msun/yr | 3 | a mass arrival rate $\dot{M}_{\rm entrance-ring}$ $\sim > 3\, \rm M_\odot \, yr^{-1}$ is found. |
| Filament filling factor | 0.02 | not stated | dimensionless | 3 | $ff_{\rm lane} \sim 3~\rm{filaments} \times (25 / 280)^2 \sim 0.02$ |
| Proto-cluster grey-body temperature | <~150 | not stated | K | 2 | yields a temperature, $T \lesssim 150\, \rm{K}$ for most of the sources |
| Toomre Q of ring | 0.9-0.6 | not stated | dimensionless | 0 | Substituting values results in Q $\sim$ 0. 9 - 0.6 |

## Qualitative findings

- Ring star formation is intermittent, with bursts at ~4 Myr and older ones separated by 20-30 Myr  
  > "The ring is a place of intermittent star bursts over the last 100 Myr." (abstract)

## Claim tuples

- H: Is gas availability the sole driver of star formation in the ring? | E: Compare cluster mass formed in 100 Myr with that expected from the current SFR and gas mass | R: Cluster mass <~1e7 Msun, under 1% of ring gas, an order of magnitude below expectation | F: Gas availability is not the sole driver; the rate of dense gas accumulation may be key | **partially**
- H: Do dust filaments feed the ring and nucleus? | E: Extinction map and streamer inflow estimate | R: Filaments under 25 pc wide run along the bar; estimated inflow >~3 Msun/yr | F: Streamers can supply the SFR and nuclear infall | **supported**

## Reasoning

- Why this data: HCN selected as a high-density tracer and strong line in the ring  
  > "This line was selected for being a high density tracer and among the strongest molecular line in the ring" (Multiwavelength dataset)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mass inflow estimate is crude and depends on approximations  
  > "A crude estimate of the arrival mass rate through the streamers at the entrance to the ring can be derived" (6.2.1)
- Caveat (inferred, ours): ALMA data used only qualitatively at 2 arcsec resolution
- Caveat (inferred, ours): Single-aperture SED fits with coarse age grid
- Caveat (inferred, ours): Inflow estimate rests on assumed geometry, density and velocity
- Caveat (inferred, ours): Gas mass taken from the literature, not measured here

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Calibrated cube taken from the ALMA archive  
  > "from the calibrated data cube in the archive was extracted" (Multiwavelength dataset)
- Missing: Cluster catalogue and photometry
- Missing: Exact HCN map extraction and registration
- Missing: SSP fitting code details
- Data volume (inferred): small (<5 GB for the ALMA part)
- Score (inferred): 3/5, ALMA use is minor and descriptive. Most of the analysis is HST/VLT based and several steps are lightly specified.
- Rediscovery candidate: no, ALMA is a minor component and the recipe is incomplete.

## Links

- Method: Prieto et al. (2014) (Extinction map procedure)
- Method: Mezcua et al. 2015 (Image registration)
- Companion: Reunanen et al. (2010) (VISIR mid-IR images)
- Companion: Hsieh et al. 2011 (CO and HCN gas properties)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00108.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 30,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
