# Dark matter dynamics in Abell 3827: new data consistent with standard cold dark matter

`2018MNRAS.477..669M` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Massey, Richard | arXiv: 1708.04245 | DOI: 10.1093/mnras/sty630

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: galaxy_clusters_and_sz, high_z_galaxies, other
- Question: Is the dark matter of Abell 3827's central galaxies offset from their stars, once new ALMA and MUSE data improve lensed image identifications?  
  > "The inferred distribution of dark matter is consistent with being centered on the galaxies, as expected by $\Lambda$CDM." (abstract)
- Target **Abell 3827**: coordinates RA=22h 01' 49.1'', Dec=-59d 57' 15''  
  > "Two properties of galaxy cluster Abell 3827 (RA=$22$h $01\ensuremath{'}$ $49.1\ensuremath{''}$, Dec=$-59^\circ$ $57\ensuremath{'}$ $15\ensuremath{''}$, $z$=0.099," (Introduction); z/distance z=0.099 (cluster); background spiral z=1.24145  
  > "Two properties of galaxy cluster Abell 3827 (RA=$22$h $01\ensuremath{'}$ $49.1\ensuremath{''}$, Dec=$-59^\circ$ $57\ensuremath{'}$ $15\ensuremath{''}$, $z$=0.099," (Introduction); distance from (cite: depla07; car10; ws11); (cite: mas15)  
  > "Two properties of galaxy cluster Abell 3827 (RA=$22$h $01\ensuremath{'}$ $49.1\ensuremath{''}$, Dec=$-59^\circ$ $57\ensuremath{'}$ $15\ensuremath{''}$, $z$=0.099," (Introduction)

## Data provenance

- ALMA projects: 2016.1.01201.S
- bands: Band 3  
  > "The band 3 data sample frequencies $89.9$-$93.8$ GHz and $101.8$-$105.6$ GHz with spectral resolution $15.6$ MHz ($47.8$ km/s)." (2.2 ALMA integral field spectroscopy)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 44 12 m antennae, C40-6  
  > "Observations were conducted with 44 12 m antennae in the C40-6 configuration." (2.2 ALMA integral field spectroscopy)
- baselines: _not stated_
- angular resolution: ~0.48''x0.39'' natural; ~0.87''x0.82'' tapered  
  > "This yielded a synthesised beam of $\sim$$0.48\ensuremath{''}\times0.39\ensuremath{''}$" (2.2 ALMA integral field spectroscopy)
- max recoverable scale: _not stated_
- sensitivity: 0.08 mJy/beam per 31.3 MHz channel; 0.15 mJy/beam tapered  
  > "a $1\sigma$ noise level of 0.08 mJy/beam for each $31.3$ MHz channel" (2.2 ALMA integral field spectroscopy)
- time on source: 5.2 hour observation  
  > "we obtained a 5.2 hour observation of Abell 3827" (2.2 ALMA integral field spectroscopy)
- observing dates: October 2016  
  > "In October 2016, we obtained a 5.2 hour observation" (2.2 ALMA integral field spectroscopy)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.5 GHz (observed 102.8 GHz))
- Other facility **VLT/MUSE**: IFU spectroscopy, [OII] narrow-band image and velocities  
  > "we obtained a $4$ hour integration of Abell 3827 using the Multi-Unit Spectroscopic Explorer (MUSE)" (2.3 VLT/MUSE integral field spectroscopy)
- Other facility **HST**: F336W, F606W, F814W, F160W imaging used for lens modelling  
  > "In this paper, we exclusively use the HST imaging." (2.1 Pre-existing imaging)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.7.2  
  > "Data were reduced using CASA software v4.7.2" (2.2 ALMA integral field spectroscopy)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2056-4714 (flux and bandpass)  
  > "Flux and bandpass calibration were obtained from J2056$-$4714, and the phase calibrator was J2208$-$6325." (2.2 ALMA integral field spectroscopy)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN with channel averaging, natural weighting  
  > "Spectral data cubes were created using the CLEAN algorithm, with channel averaging and natural weighting to maximise sensitivity." (2.2 ALMA integral field spectroscopy)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: second cube with (u,v) taper  
  > "we created a second spectral cube with a $(u,v)$ taper applied" (2.2 ALMA integral field spectroscopy)
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

- Foreground subtraction of HST imaging and lenstool priors follow earlier work  
  > "As described in (cite: tay17), we reveal the background lensed galaxy by fitting and subtracting foreground emission" (2.1 Pre-existing imaging); "priors identical to those in (cite: tay17)" (3.2.1 LENSTOOL) [from (cite: tay17)]

### Not stated but needed to reproduce (our reading)

- taper scale (uv taper value)
- CLEAN threshold, mask, cell and image size
- how moment maps/CO images used for image identification were made
- ALMA flux scale uncertainty and calibration details
- lenstool configuration files and image-identification weights

## Analysis recipe

1. **Make ALMA CO(2-1) cubes**: CLEAN imaging in CASA, natural weighting plus tapered cube  
  > "Spectral data cubes were created using the CLEAN algorithm, with channel averaging and natural weighting to maximise sensitivity." (2.2 ALMA integral field spectroscopy)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify multiple images using ALMA/MUSE/HST**: Compare CO velocity/flux and MUSE velocities to identify Ao5 as bulge image  
  > "Our ALMA data show that the feature south of N1 is at the same systemic velocity and similar CO(2-1) flux as the source’s central bulge." (3.1 Strong lens image identifications)
   - software: MuSCADeT
   - fitting: _not stated_
   - validation: _not stated_
3. **Parametric lens model**: lenstool MCMC with PIEMD cluster halo plus Hernquist and PISP galaxy components  
  > "The parameters’ posterior probability distribution function (PDF) is explored by a Markov Chain Monte Carlo (MCMC) iteration" (3.2.1 LENSTOOL)
   - software: lenstool
   - parameter: chain samples PDF 100,000 times; positional uncertainty 0.5'' for Ao6, Ao7 and 0.15'' for others  
  > "We assume statistical uncertainty of 0.5$''$ on the location of Ao6 and Ao7" (3.2.1 LENSTOOL)
   - assumption: Stellar mass from Galfit F606W, BC03, Chabrier IMF, solar metallicity, burst at z=3  
  > "assuming a (cite: cha03) initial mass function, solar metallicity, and a single burst of star formation at redshift $z_{\mathrm f}\!=\!3$" (3.2.1 LENSTOOL)
   - fitting: MCMC, runmode=3, flat prior 2'' either side of stars  
  > "the location and amount of each galaxy’s dark matter is given a flat prior $2\ensuremath{''}$ either side of its stars" (3.2.1 LENSTOOL)
   - validation: Compared with grale; tested in blind analysis  
  > "Both have been tested in a blind analysis of strong lensing data for which the true mass distribution is known" (3.2 Mass model)
4. **Free-form lens model**: grale genetic algorithm on ~1300 Plummer spheres, 20 runs averaged  
  > "We run twenty mass reconstructions with different random seeds." (3.2.2 GRALE)
   - software: grale
   - fitting: _not stated_
   - validation: rms across runs gives statistical error  
  > "their rms provides an estimate of statistical error" (3.2.2 GRALE)

## Software

- **CASA** v4.7.2: ALMA reduction and imaging  
  > "Data were reduced using CASA software v4.7.2" (2.2 ALMA integral field spectroscopy)
- **lenstool** v6.8.1: parametric mass model  
  > "First, we use lenstool v6.8.1" (3.2 Mass model)
- **grale** : free-form mass model  
  > "Second, we use grale (cite: lie06)." (3.2 Mass model)
- **MuSCADeT** : foreground subtraction in HST  
  > "using the MuSCADeT method (cite: muscadet)" (2.1 Pre-existing imaging)
- **esorex** v1.0: MUSE reduction  
  > "Data were reduced using v1.0 of the esorex pipeline" (2.3 VLT/MUSE integral field spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| lenstool best-fit rms | 0.13 | not stated | arcsec | 3 | This model achieves $\langle$rms$\rangle_i$=$0.13\ensuremath{''}$ |
| N1 dark matter offset | 0.54 | +0.22/-0.23 | kpc | 3 | $0.29^{+0.12}_{-0.13}$ arcseconds or $0.54^{+0.22}_{-0.23}$ kpc |
| (sigma/m)cos(i) | 0.68 | +0.28/-0.29 | cm^2/g | 3 | $(\sigma/m)\cos{(i)}=0.68^{+0.28}_{-0.29}$ cm${^2}$/g |
| luminosity-weighted [OII] amplification | 144 | not stated | dimensionless | 3 | the luminosity-weighted amplification of its \[Oii\] emission is $\mu=144$ |

## Qualitative findings

- ALMA CO(2-1) was key to identifying a new bulge image Ao5, correcting an earlier identification  
  > "Our new data indicate that this identification was incorrect." (3.1 Strong lens image identifications)

## Claim tuples

- H: Is N1's dark matter significantly offset from its stars? | E: Lens modelling with lenstool and grale using new image identifications | R: ~2 sigma offset in lenstool, vanishing when combined with grale and systematics | F: No statistically significant offset, consistent with CDM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Earlier identification of point source south of N1 as image of knot Aa rejected  
  > "Our new data indicate that this identification was incorrect." (3.1 Strong lens image identifications)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic biases up to ~0.21'' and degeneracies prevent concluding any offset is significant  
  > "we cannot here conclude that any offset is physically significant" (4 Results)
- Caveat (inferred, ours): ALMA CO detection is low S/N; image identifications partly subjective
- Caveat (inferred, ours): Mass estimates depend linearly on unconstrained r_cut

## Reproducibility

- Data public (paper): All data available from telescope archives  
  > "All data are available from the telescopes’ archives." (Acknowledgments)
- Products in archive: _not stated_
- Missing: lenstool input files
- Missing: ALMA imaging parameters
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and image positions listed, but lens model inputs and imaging details are incomplete.
- Rediscovery candidate: no, The ALMA role is minor, and the main results depend on a complex lens modelling pipeline with incomplete settings.

## Links

- Method: (cite: tay17) (foreground subtraction and lenstool priors)
- Companion: (cite: mas15) (previous Abell 3827 analysis with reported offset)
- Related: HST GO-12817
- Related: VLT programmes 295.A-5018, 294.A-5014

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 35,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
