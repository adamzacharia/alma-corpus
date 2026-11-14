# Significant gas-to-dust ratio asymmetry and variation in the disk of HD 142527 and the indication of gas depletion

`2015PASJ...67..122M` | Publications of the Astronomical Society of Japan 2015 | first author: Muto, Takayuki | arXiv: 1509.03736 | DOI: 10.1093/pasj/psv098

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How are gas and dust distributed in the dust-bright northern and dust-faint southern parts of the HD 142527 disk, and what is the gas-to-dust ratio?  
  > "In this paper, we investigate how gas and dust are distributed in the dust-bright northern part of the disk and in the dust-faint southern part." (abstract)
- Target **HD 142527**: coordinates RA=J2000 15h56m41.9, DEC=J2000 -42d19m23.3  
  > "ALMA Band 7 Cycle 0 observations of HD 142527 (RA=J2000 15h56m41.9, DEC=J2000 -42d19m23.3)" (2.1 Observation and Data Reduction); "the age is 5 Myr if we adopt $d=140~\mathrm{pc}$ considering the association to Sco OB2" (Introduction); z/distance d = 140 pc  
  > "ALMA Band 7 Cycle 0 observations of HD 142527 (RA=J2000 15h56m41.9, DEC=J2000 -42d19m23.3)" (2.1 Observation and Data Reduction); "the age is 5 Myr if we adopt $d=140~\mathrm{pc}$ considering the association to Sco OB2" (Introduction); distance from association to Sco OB2 (Fukagawa06; Verhoeff11; Mendigutia14)  
  > "ALMA Band 7 Cycle 0 observations of HD 142527 (RA=J2000 15h56m41.9, DEC=J2000 -42d19m23.3)" (2.1 Observation and Data Reduction); "the age is 5 Myr if we adopt $d=140~\mathrm{pc}$ considering the association to Sco OB2" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00318.S
- bands: Band 7 (Cycle 0), continuum 336 GHz  
  > "ALMA Band 7 Cycle 0 observations of HD 142527" (2.1 Observation and Data Reduction)
- frequencies and spectral setup: four spectral windows, 469 MHz bandwidth, 3840 channels each, centred 330.588, 329.331, 342.883, 342.400 GHz; channel spacing 122 kHz (0.12 km/s), effective resolution ~0.2 km/s  
  > "four separate spectral windows with 469 MHz of bandwidth and 3840 channels each, and their central frequencies are 330.588, 329.331, 342.883 and 342.400 GHz" (2.1 Observation and Data Reduction)
- continuum bandwidth: 1.8 GHz at 336 GHz  
  > "treated as a single data set of 336 GHz in central frequency and 1.8 GHz in bandwidth" (2.1 Observation and Data Reduction)
- arrays: _not stated_
- configurations: extended array, maximum baseline about 480 m  
  > "carried out in the extended array configuration with a maximum baseline of about 480 m" (2.1 Observation and Data Reduction)
- baselines: _not stated_
- angular resolution: continuum 0.47''x0.40'' (PA 59.9); 13CO 0.50''x0.42'' (PA 57.4); C18O 0.50''x0.42'' (PA 60.6)  
  > "$0.47\ensuremath{''} \times 0.40\ensuremath{''} = 60~\mathrm{AU}\times 56\mathrm{AU}$ ($PA=59.9^{\circ}$)" (2.1 Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.13 mJy/beam continuum; 6.1 (13CO) and 8.3 (C18O) mJy/beam per 0.12 km/s channel  
  > "The rms noise is 0.13 mJy beam$^{-1}$ for the continuum whereas it is 6.1 and 8.3 mJy beam$^{-1}$ in the 0.12 km s$^{-1}$ wide channels" (2.1 Observation and Data Reduction)
- time on source: 3.0 h after flagging  
  > "The on-source integration after flagging aberrant data was 3.0 h." (2.1 Observation and Data Reduction)
- observing dates: six scheduling blocks, June to August 2012  
  > "six scheduling blocks during the period from June to August 2012" (2.1 Observation and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 13CO J=3-2 (not stated)
- Line: C18O J=3-2 (not stated)
- External data: Stellar Teff = 6250 K and R = 3.8 Rsun; stellar mass 2.2 Msun  
  > "The star is assumed to have the effective temperature of $T_{\rm eff} = 6250~\mathrm{K}$ and the radius of $R = 3.8~R_{\odot}$ (cite: Verhoeff11)" (3.1 Dust Distribution Models) [from (cite: Verhoeff11)]
- External data: 13CO and C18O fractional abundances 9e-7 and 1.35e-7  
  > "The fractional abundance of $^{13}$CO and C$^{18}$O is assumed to be $9 \times 10^{-7}$ and $1.35 \times 10^{-7}$ (cite: Qi11)." (3.2 Gas Distribution Models) [from (cite: Qi11)]
- External data: Dust composition abundances consistent with solar elemental abundance  
  > "which are consistent with solar elemental abundance (cite: Anders89)" (3.1 Dust Distribution Models) [from (cite: Anders89)]

## Processing

### Calibration

- pipeline or manual: CASA reduction with self-calibration on continuum, solution applied to lines; same as Fukagawa13  
  > "Self-calibration was performed for the continuum to improve the sensitivity and image fidelity, and the final gain solution was also applied to $^{13}$CO and C$^{18}$O data." (2.1 Observation and Data Reduction)
- casa version: CASA 3.4  
  > "Common Astronomy Software Applications (CASA) version 3.4" (2.1 Observation and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: performed on continuum; solution applied to lines  
  > "Self-calibration was performed for the continuum to improve the sensitivity and image fidelity" (2.1 Observation and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we adopted in this study the Briggs weighting with a robust parameter of 0.5" (2.1 Observation and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: model: image-plane using line-free channels, checked against uv-plane subtraction on simulated data  
  > "The continuum emission is subtracted on the image by using line-free channels" (3.2 Gas Distribution Models)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.47''x0.40'' continuum; 0.50''x0.42'' lines  
  > "$0.50\ensuremath{''} \times 0.42\ensuremath{''} = 70\mathrm{AU}\times 59\mathrm{AU}$ ($PA=57.4^{\circ}$)" (2.1 Observation and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and reduction (bandpass, gain) done as in Fukagawa13; only the final weighting differs  
  > "Further details on bandpass and gain calibrations are described in (cite: Fukagawa13)." (2.1 Observation and Data Reduction) [from (cite: Fukagawa13)]
- M1 moment method for radiative transfer  
  > "We solved the zeroth and first order moment equations of the radiative transfer (M1 method, see (cite: Kanno13))." (3.1 Dust Distribution Models) [from (cite: Kanno13)]
- Dust size distribution a^-3.5 with amax 1 mm  
  > "power-law size distribution of $\propto a^{-3.5}$ with the maximum size of $a_{\max}=1~\mathrm{mm}$ (cite: Nomura05)" (3.1 Dust Distribution Models) [from (cite: Nomura05)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, reference antenna, and calibrator names
- Line-free channel ranges for continuum subtraction and moment-map clipping thresholds
- Dust optical constants/opacity tables and the radiative transfer (M1) code, not public
- Model code for ray tracing and moment computation
- Flagging details and the Fukagawa13 calibration specifics
- Position angles and widths of radial profile extraction beyond given sectors

## Analysis recipe

1. **Fit radial continuum profiles**: Gaussian fits to averaged surface brightness in north (PA 11-31) and south (PA 211-231) sectors  
  > "The averaged surface brightness profiles $I(r)$ in $PA=11^{\circ}-31^{\circ}$ and $211^{\circ}-231^{\circ}$ are fitted by" (2.2 Results of Dust Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive kinematic parameters from P-V diagram**: Keplerian fit to major-axis P-V diagram, chi2 minimisation  
  > "The best-fitted parameters obtained by $\chi^2$-minimization are in good agreement between $^{13}$CO and C$^{18}$O." (Details on 13CO and C18O results)
   - parameter: stellar mass fixed within 2.2 +/- 0.3 Msun; free: systemic velocity, centre, inclination  
  > "whereas the central stellar mass is fixed in the range of $2.2 \pm 0.3$ $M_{\odot}$ (Verhoeff et al., 2011)" (Details on 13CO and C18O results)
   - fitting: chi2 minimisation  
  > "The best-fitted parameters obtained by $\chi^2$-minimization are in good agreement between $^{13}$CO and C$^{18}$O." (Details on 13CO and C18O results)
   - validation: _not stated_
3. **Model dust distribution**: Axisymmetric Gaussian dust ring in thermal and hydrostatic equilibrium; M1 radiative transfer then ray tracing, convolved with beam, parameters (Sigma_d0, r_d, w_d) iterated by hand to match north and south profiles  
  > "We iterate this procedure until the given set of parameters $(\Sigma_{d,0},r_d,w_d)$ reproduces the observed profiles shown in figure" (3.1 Dust Distribution Models)
   - software: M1 radiative transfer code
   - parameter: 226 wavelengths 0.1 um-3.16 mm; grid 30-410 AU, |z|<=120 AU, 2 AU resolution; 128x128 rays; inclination 27 deg  
  > "We use 226 colors in the wavelength range of $0.1~\mu\mathrm{m} \le \lambda \le 3.16~\mathrm{mm}$" (3.1 Dust Distribution Models)
   - assumption: Dust amax=1 mm, kappa_a=2.9 cm2/g at 870 um, isotropic scattering, gas temperature = dust temperature, stellar heating only, Teff 6250 K  
  > "Our opacity at 870 $\mu$m has values of $\kappa_a = 2.9$ cm$^2$/g" (3.1 Dust Distribution Models)
   - fitting: Manual parameter search  
  > "The parameters that give a reasonable fit to observations are searched manually." (6.1 Summary of Gas and Dust Distribution)
   - validation: Sensitivity tests of north optically thick case in appendix  
  > "The details of the parameter search for the north profiles are summarized in appendix" (Results of Dust Distribution)
4. **Model gas distribution**: Gas density = xi(r) x dust density; parametric Sigma_g (r^-1 power law with r_c, r_out, f_in, f_out); LTE line ray tracing, channel maps convolved, moments 0 and 1 compared by eye  
  > "Local thermal equilibrium (LTE) is assumed to calculate the level population" (3.2 Gas Distribution Models)
   - software: CASA simulator
   - parameter: Keplerian rotation for 2.2 Msun; channel step 0.06 km/s over +/-4.5 km/s; thermal line width  
  > "We construct the model channel maps from $-4.5$ km s$^{-1}$ to 4.5 km s$^{-1}$ with respect to the systemic velocity with 0.06 km s$^{-1}$ step" (3.2 Gas Distribution Models)
   - assumption: 13CO abundance 9e-7, C18O 1.35e-7, no scattering of line emission  
  > "The fractional abundance of $^{13}$CO and C$^{18}$O is assumed to be $9 \times 10^{-7}$ and $1.35 \times 10^{-7}$ (cite: Qi11)." (3.2 Gas Distribution Models)
   - fitting: Grid of Sigma0, r_c, r_out, f_in, f_out explored sequentially, by eye  
  > "The parameters that give a reasonable fit to observations are searched manually." (6.1 Summary of Gas and Dust Distribution)
   - validation: uv-plane continuum subtraction with CASA simulator agrees within a few percent; P-V diagram comparison  
  > "the resultant line profiles agree with those obtained with the image-based continuum subtraction within a few percent" (3.2 Gas Distribution Models)
5. **Compute masses and gas-to-dust ratio**: Integrate reference models over disk within 400 AU; compare gas and dust surface densities  
  > "when integrated over the disk within 400 AU" (6.2.3 Total Amount of Gas and Dust)
   - fitting: _not stated_
   - validation: Compared with Perez14 and Verhoeff11 masses  
  > "(cite: Verhoeff11) obtained the dust mass of $1\times 10^{-3} \thinspace M_\odot$ from their SED modeling." (Total Amount of Gas and Dust)

## Software

- **CASA** 3.4: calibration, imaging, and simulated observations of models  
  > "Common Astronomy Software Applications (CASA) version 3.4" (2.1 Observation and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| North continuum peak brightness | 1.2 | not stated | Jy/arcsec2 | 1 | / $11-31^{\circ}$ (North profile) / 1.2 / 152 / 51 / |
| South continuum peak brightness | 0.050 | not stated | Jy/arcsec2 | 1 | / $211-231^{\circ}$ (South profile) / 0.050 / 174 / 51 / |
| Disk inclination | 26.5 | +2.2/-1.7 | deg | 2 | the system inclination angle is estimated as $i = 26.5^{+2.2}_{-1.7}$ degrees |
| Systemic velocity | 3.72 | 0.02 | km/s (vLSR) | 2 | $3.72 \pm 0.02$ km s$^{-1}$ in $v_{\mathrm{LSR}}$ |
| North dust model (Sigma_d0, r_d, w_d) | 0.6 g/cm2, 173 AU, 27 AU | not stated | mixed | 3 | /        $r_{d}~[\mathrm{AU}]$        /  173  /         196          / |
| South dust model (Sigma_d0, r_d, w_d) | 8.45e-3 g/cm2, 196 AU, 34 AU | not stated | mixed | 3 | /        $w_{d}~[\mathrm{AU}]$        /  27   /          34          / |
| Dust surface density contrast north/south | ~70 | not stated | dimensionless | 3 | the amount of dust particles is $\sim 70$ times more at the peak of the north profiles than at the peak of the south profile |
| Gas model Sigma0 north / south | 0.845 / 0.2325 | factor ~2 | g/cm2 | 4 | / $\Sigma_0~[\mathrm{g~cm}$$^{-2}]$ /   0.845   /  0.2325   / |
| Gas-to-dust ratio at dust peak, south / north | ~30 / ~3 | not stated | dimensionless | 5 | The gas-to-dust ratio is $\sim 30$ at the peak of the dust emission in the southern part of the disk, while it reaches $\sim 3$ in the northern peak. |
| Dust mass north / south | 3.5e-3 / 7e-5 | not stated | Msun | 5 | $M_{\rm dust}=3.5\times 10^{-3} \thinspace M_\odot$ for the north profile and $M_{\rm dust} = 7 \times 10^{-5} \thinspace M_\odot$ for the south profile |
| Gas mass north / south (within 400 AU) | 1.8e-2 / 5.7e-3 | factor ~2-3 | Msun | 5 | $M_{\rm gas} = 1.8 \times 10^{-2} \thinspace M_\odot$ and $M_{\rm gas} = 5.7 \times 10^{-3} \thinspace M_\odot$ |
| Overall gas-to-dust mass ratio | ~10-30 | not stated | dimensionless | 5 | the overall gas-to-dust ratio is inferred to be $\sim 10-30$ |

## Qualitative findings

- Gas emission is much more azimuthally symmetric and radially extended than dust; tenuous gas remains inside ~100 AU and outside ~250 AU.  
  > "Compared to the dust, the gas distribution is more extended in the radial direction." (abstract)

## Claim tuples

- H: Is the gas-to-dust ratio uniform at 100 in the disk? | E: Compare uniform-ratio models with 13CO and C18O moment 0/1 profiles | R: Uniform ratio 100 fails at inner radii and at dust peak | F: Gas-to-dust ratio varies with radius and azimuth | **supported**
- H: How asymmetric are dust and gas? | E: Separate north and south axisymmetric models | R: Dust contrast ~70, gas ~3-10 | F: Dust is strongly concentrated in the north; gas is much more symmetric | **supported**
- H: Is the disk gas-depleted? | E: Integrated model gas and dust masses | R: Overall gas-to-dust ratio ~10-30 with factor 2-3 uncertainty | F: Gas depletion may already be under way | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Axisymmetric north and south models used because a fully azimuthal model would be very complex  
  > "since the model that fully accounts for the azimuthal asymmetry can be very complex" (3 Method of Modeling)
- Alternative: Gaussian gas profiles and exponential taper rejected: Gaussian falls too fast; exponential gives too much moment 0 at large radii  
  > "This indicates that the gas surface density should decrease more rapidly than exponential profiles at outer radii." (5.5 Outer Radius of Dense Gas)
- How they decided it was enough: _not stated_
- Limitation (authors): _not stated_
- Caveat (inferred, ours): No formal fit or error estimates; by-eye parameter search
- Caveat (inferred, ours): Results depend on assumed dust opacity (amax 1 mm), CO abundance and gas=dust temperature
- Caveat (inferred, ours): Optically thick 13CO/C18O and continuum subtraction produce artefacts
- Caveat (inferred, ours): Axisymmetric north/south models ignore azimuthal structure

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00318.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Radiative transfer (M1) code and dust opacity tables
- Missing: Self-calibration and line-free channel details
- Missing: Moment-map clipping thresholds
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and well-described parametric models, but custom code, manual fitting and missing calibration details limit reproduction.
- Rediscovery candidate: no, Main results rely on unreleased radiative transfer code and manual fitting.

## Links

- Method: (cite: Kanno13) (M1 radiative transfer method)
- Companion: (cite: Fukagawa13) (Earlier ALMA analysis of same data; calibration)
- Companion: (cite: Perez14) (Comparison of gas mass in cavity and total)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 45,
  "rate": 0.616
 },
 "evidence_ok": true
}
```
