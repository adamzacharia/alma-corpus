# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A.203S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Multi-scale radiative-transfer model of the protoplanetary disc DoAr 44

We aim to construct a comprehensive global multi-scale kinematic equilibrium radiative-transfer model for the pre-transitional disc of DoAr 44 (Haro 1-16, V2062 Oph) in the Ophiuchus star-forming region. This model integrates diverse observational datasets to describe the system, spanning from the accretion region to the outer disc. Our analysis utilises a large set of observational data, including ALMA continuum complex visibilities, VLTI/GRAVITY continuum squared visibilities, closure phases, and triple products, as well as VLT/UVES and VLT/X-shooter H$\alpha$ spectra. Additionally, we incorporated absolute flux measurements from ground-based optical observatories, Spitzer, IRAS, the Submillimeter Array, the IRAM, or the ATCA radio telescopes. These data sets were used to constrain the structure and kinematics of the object through radiative-transfer modelling. Our model reveals that the spectral line profiles are best explained by an optically thin spherical inflow/outflow within the co-rotation radius of the star, exhibiting velocities exceeding 380 km/s. The VLTI near-infrared interferometric observations are consistent with an inner disc extending from 0.1 to 0.2 au. The ALMA sub-millimetre observations indicate a dust ring located between 36 and 56 au, probably related to the CO$_2$ condensation line. The global density and temperature profiles derived from our model provide insight into an intermediate disc, located in the terrestrial planet-forming zone, which has not yet been spatially resolved.

# Introduction

Protoplanetary discs are reservoirs of gas and dust surrounding young stellar objects and the birthplace of planets. Understanding them is necessary to understand the formation of exoplanetary systems and our own solar system. Various disc morphologies have been suggested based on the broad band spectral energy distribution, and now are being directly imaged either via sub-mm-observations or adaptive optics (cite: andrews2018disk; avenhaus2018disks). Presumably, the youngest of these discs have monotonically decreasing density profiles, with a large inner cavity opening later, most probably due to the influence of forming ice-giants, creating so-called transitional discs (cite: van2023transition), before dispersing a few millions of years later (cite: li2016lifetimes). However, matter is still flowing through these cavities, as evidenced by the high accretion rates (cite: van2023transition).

An intermediate phase has been identified (cite: epsaillat2007), called the pre-transitional phase, where the young star is surrounded by an inner disc, encircled by a large, optically thin cavity, followed by an extended dust ring exhibiting mm-emission.

The object DoAr 44 (Haro 1–16, V2062 Oph), located in the Ophiuchus star formation region, is one of these pre-transitional discs with a high water vapour luminosity in the inner disc (cite: salyk2015detection), 40 times more than the structurally very similar disc PDS 70 (cite: perotti2023water), where planet formation is confirmed by direct imaging by the Hubble Space Telescope (HST) (cite: zhou2021hubble), ALMA (cite: benisty2021circumplanetary) and VLT/SPHERE (cite: keppler2018discovery). DoAr 44 has been investigated by VLTI/GRAVITY (cite: bouvier2020probing), revealing a disc-like structure in the 0.2–1.5 au region, VLT/SPHERE (cite: arce2023radio), showing the disc extending beyond 15 au, and also ALMA Bands 3, 4, 6, 7 and 8 at resolutions up to $\approx 25$ mas in Band 6 and 7 (cite: cieza2021ophiuchus; arce2023radio), in both continuum and spectral lines, investigating the region from 5–80 au, revealing a narrow dust ring with a brim around 47 au.

A series of other works were devoted to this pre-transitional disc. For example, (cite: ricci2010dust) performed a 3.3 mm continuum survey of the $\varrho$-Ophiuchi region, including DoAr 44, using the Australian Telescope Compact Array (ATCA), measuring the spectral indices between the 1.3 mm and 3.3 mm fluxes. They concluded that the spectral indices of Ophiuchus sources are not statistically different from the sources in the Taurus/Auriga star-forming region, which they surveyed using the Plateau de Bure Interferometer (PdBI) in a previous study (cite: ricci2010dust2), but differ significantly from the interstellar medium.

(cite: 2010ApJ...723.1241A) then performed an interferometric survey using the Submillimeter Array (SMA) at 40 au resolution in the Ophiuchus star-forming region. They tried fitting the surface density profile using the common (cite: 1974MNRAS.168..603L) prescription: $$\begin{equation}
    \Sigma = \Sigma_0 \left(\frac{R}{R_c}\right)^\gamma \exp \left[ -\left(\frac{R}{R_c}\right)^{2-\gamma} \right]\,,
\end{equation}$$ where $\Sigma_0,R_c, \gamma$ are parameters. However, for several discs they found a poor fit, which could be explained by the fact that these discs (DoAr 44, SR 21, SR 24 and WSB 60) had a large central cavity. This was the first *spatially* resolved observation of the cavities predicted by SED modelling. They continued their investigation of transitional discs with an additional SMA study (cite: 2011ApJ...732...42A), finding that the dust in the cavity has been depleted by 4–6 orders of magnitude with respect to the (cite: 1974MNRAS.168..603L) profile.

(cite: espaillat2010unveiling) modelled Infrared Telescope Facility (IRTF) 2.1–5.0 micron spectra of DoAr 44 with $R = 1500$ resolving power, and also Spitzer spectra, using analytical temperature prescriptions. They derived a higher accretion rate of $\dot{M} = 9.3\times10^{-9} {\,M_\odot\,}{\rm yr^{-1}}$.

(cite: bouvier2020probing) obtained K-band (2 – 2.4 μm) continuum and Br$\gamma$ line visibilites of DoAr 44 from VLTI/GRAVITY. They concluded that the Br$\gamma$ emission is located inward of the continuum emission, suggesting that the optically thin gas flows, where the line emission is created, are located within the truncation radius. They used the (cite: Lazareff) visibility models, using a point source, an elliptical Gaussian in place of the disc and a “halo”. This halo represents all the incoherent emission from outside regions. They found the contribution of the ellipse to be $27\,\%$, the star $67\,\%$, and the halo $6\,\%$.

(cite: bouvier2020investigating) also performed multicolour photometry from the Las Cumbres Observatory Global Telescope Network (LCOGT) and spectroscopy using the Canada France Hawaii Telescope (CFHT). They found a rotation period of $P = 2.96\,$days, a stellar inclination of $i = (30 \pm 5)^\circ$, which is in agreement with the inclination of the ellipse modeling (supposedly) the inner rim seen by VLTI. From their H$\alpha$, H$\beta$, Pa$\beta$, Br$\gamma$ spectra, they conclude that the spectral line profiles are best explained as a combination of funnel flows along magnetic field lines and disc winds, similar to the ones described by radiative transfer models by (cite: kurosawa2011multidimensional), where the “funnel” flows cross the line of sight. For some spectral lines, this behaviour is periodic (He I), and for others, they report a more complicated chaotic variability (Br$\gamma$). (cite: bouvier2020investigating) derived an accretion rate of $\dot{M} = 6.5\times10^{-9} {\,M_\odot}\,{\rm yr^{-1}}$.

(cite: 2018ApJ...863...44A) studied discs around T Tauri stars (the DARTTS-S survey), using the VLT/SPHERE/IRDIS instrument, operating between 0.9–2.3 microns, in the differential polarimetric imaging mode, with a coronagraph obscuring $0.1''$ around the central star. These images can be seen in Figures [11](#fig:multi).A and [11](#fig:multi).B, showing the scattered light from the surface of the disc. Surprisingly, they found no correlation of the scattered light, either to the stellar mass or to mm-fluxes.

(cite: casassus2018inner) focused on the misalignment of the inner and outer discs of DoAr 44. This is somewhat visible in the radio continuum, but it is very apparent in the polarimetric images. They estimated a tilt of $30^\circ$ of the inner disc with respect to the outer disc using radiative transfer modelling.

(cite: casassus2019) construct a parametric radiative transfer model of DoAr 44, accounting for the shadowing caused by the misaligned inner disc. They derive outer disc dust temperatures of 36 – 48 K with the cooler temperatures being in the nodal regions, shadowed by the inner disc. They derive a surface density of $\Sigma = \SI{ <13}{\centi \meter^2 \gram^{-1}}$ and an aspect ratio of 0.08 at the inner rim of the outer ring.

(cite: arce2023radio) studied these same SPHERE images together with the ALMA Band 6 images from ODISEA and new Band 7 images, specifically of the DoAr 44 system. They derived a relative inclination of $21^\circ$.

(cite: leiendecker2022dust) performed a study of DoAr 44, together with the better known system HD 163296. They estimated a dust mass of 0.3 $M_{\rm Jupiter}$, corresponding to 21.5 $M_{\rm Jupiter}$ mass of gas. They tried explaining the ring morphology in alternative scenarios, such as a break-up of two large bodies. They also estimated the mass of a hypothetical planet needed to clear the inner disc at $0.5 \textrm{ to } 1.6\, M_{\rm Jupiter}$.

In this work, we aim at constructing a global model of the system DoAr 44 informed by a wide range of observables.

# Archival observations

Several archival observations of DoAr 44 are available, including H$\alpha$ spectra, VLTI interferometry, ALMA visibilities, and spectral energy distribution measurements.

## H$\alpha$ spectroscopy

To constrain the physical properties of the accretion region around the star, all available H$\alpha$ datasets from the ESO Archive were utilized. This includes 11 spectra from the VLT/ESPRESSO (program ID 111.250K), 3 spectra from VLT/UVES (program ID 69.C-0481) and a single spectrum taken by VLT/X-shooter (program ID 085.C-0764).

The VLT/ESPRESSO observations have a 2600 s exposition time and have a spectral resolution of $R = 140\,000$. The signal to noise ratio (SNR) in the continuum around H$\alpha$ is better than ${\rm SNR} \gtrsim 50$, and reach ${\rm SNR} \approx 200$ in the center of the spectral line profile. Further details can be found in Tab. [1](#tab:halfa).

| Instrument |    $R$ |   SNR |       Date | $t ~(s)$ |
|:-----------|-------:|------:|-----------:|:---------|
| UVES       |  66320 |  87.1 | 2020-10-20 | 900      |
| UVES       |  66320 |  77.7 | 2020-10-20 | 1260     |
| UVES       |  51690 |  55.2 | 2020-10-20 | 1800     |
| ESPRESSO   | 140000 |    69 | 2023-05-05 | 2600     |
| ESPRESSO   | 140000 |  72.9 | 2023-05-05 | 2600     |
| ESPRESSO   | 140000 |  61.4 | 2023-05-05 | 2600     |
| ESPRESSO   | 140000 |  42.8 | 2023-05-30 | 2600     |
| ESPRESSO   | 140000 |  66.5 | 2023-05-05 | 2600     |
| ESPRESSO   | 140000 |  81.1 | 2023-05-05 | 2600     |
| ESPRESSO   | 140000 |    70 | 2023-05-05 | 2600     |
| ESPRESSO   | 140000 |  73.5 | 2023-05-05 | 2600     |
| ESPRESSO   | 140000 |  39.8 | 2023-05-30 | 2600     |
| ESPRESSO   | 140000 |  64.1 | 2023-05-30 | 2600     |
| ESPRESSO   | 140000 |  63.2 | 2023-05-05 | 2600     |
| X-shooter  |  18340 | 300.3 | 2014-05-15 | 1120     |

: Parameters of the VLT observations of the H$\alpha$ spectrum of DoAr 44.

Table notes: $R$ denotes the spectral resolution, SNR the signal to noise ratio, and $t$ the exposure time.

The H$\alpha$ emission is extremely variable, changing from 6 to 12 times above the continuum emission, displaying single-, double-, triple-, and even quadruple-peaked profiles. This behaviour is extremely complicated, and is related to the detailed geometry and kinematics of the accretion funnel flows and accretion shocks, and the superposition of emission and absorption components (cite: bouvier2020investigating).

For this reason, a mean profile was computed (see Fig. [1](#fig:comb)), corresponding approximately to an axially-symmetric mean state of the system.

A piece-wise linear interpolation has been performed in 200 equidistant points in the range 654.5 to 658.0 nm for all the datasets, and a point-wise average and standard deviation from this average has been computed. This standard deviation from the mean spectrum has been treated as the denominator in the $\chi^2$ minimization, as our model will not capture the temporal variability of the system.

![](img/spectra_combined.png)

## VLTI interferometry

To constrain the spatial extent of the inner accretion region, we utilized archival VLTI/GRAVITY interferometric data of DoAr 44 (cite: bouvier2020probing). The reduction was performed using the Gravity Pipeline in EsoReflex (cite: freudling2013automated), to obtain the calibrated squared visibilities $V^2$ and closure phases arg$T^3$. The data was taken on the 22nd of June 2020 using the Unit Telescopes in the K-band ($\approx \SI{2}{\micro \meter}$). The uv-space coverage, together with the squared visibilities are shown in Fig. [2](#fig:VLTI).

![](img/reduced_VLTI_vis.png)

![](img/VLTI_uvdist_reduced.png)

## ALMA interferometry

To constrain the dimensions and temperature of the outer disc, the newest continuum Band 7 (870 μm) ALMA interferometric data was used (project code 2019.1.00532.S, observation date 2021-08-19, (cite: arce2023radio)). The minimum and maximum recoverable scales of the observations are 0.023" and 0.56" respectively, with a total 4390 s of integration time. The squared visibilities for both polarizations are shown in Fig. [3](#fig:XXYY). The CLEANed image can be seen in [11](#fig:multi).H.

A second high-resolution observation in ALMA Band 6 (project code 2018.1.00028.S, observation date 2020-11-30, (cite: cieza2021ophiuchus)) was also taken in consideration when modelling the intermediary disc. This observation can be seen in [11](#fig:multi).G.

Other ALMA observations, listed in Table [\[tab:ALMA_observations\]](#tab:ALMA_observations) have been used as total flux measurements, that is, as data points in the SED.

![](img/ALMA_xx_yy.png)

| Project code   | Band | Frequency (GHz)   | Release date | minRS  | maxRS | t (s) |     |
|:---------------|-----:|:------------------|:-------------|:-------|:------|:------|:----|
| 2019.1.01111.S |    3 | 89.533 – 105.476  | 2022-08-13   | 0.251" | 3.80" | 490   |     |
| 2021.1.00378.S |    4 | 137.034 – 152.977 | 2023-08-16   | 0.210" | 3.94" | 73    |     |
| 2018.1.00028.S |    6 | 216.008 – 233.992 | 2020-11-30   | 0.026" | 0.64" | 2830  |     |
| 2012.1.00158.S |    7 | 329.093 – 343.083 | 2015-08-19   | 0.229" | 1.98" | 2056  |     |
| 2019.1.00532.S |    7 | 342.417 – 356.969 | 2022-06-08   | 0.168" | 2.70" | 2570  |     |
| 2019.1.00532.S |    7 | 342.423 – 356.969 | 2023-09-06   | 0.023" | 0.56" | 4391  |     |
| 2021.1.00378.S |    8 | 397.050 – 412.995 | 2023-09-01   | 0.154" | 2.36" | 113   |     |

Table notes: The value of minRS corresponds to the minimum recoverable scale, i.e., the angular resolution, and the value maxRS denotes the maximum recoverable scale. The integration time is seconds is denoted by $t$.

## Spectral energy distribution

The measurements of the SED were taken from the following surveys, publications and catalogues, using mostly Vizier (cite: ochsenbein2000vizier):

- XMM-Newton, $\SI{344}{\nano \meter}$ (cite: page2012xmm);

- ASAS-SN catalogue, $\SI{444}{\nano \meter}$ – $\SI{2.16}{\micro \meter}$ (cite: jayasinghe2018asas);

- SkyMapper catalogue, $\SI{497}{\nano \meter}$, $\SI{604}{\nano \meter}$ (cite: SkyMapper);

- Gaia satellite, $\SI{505}{\nano \meter}$, $\SI{673}{\nano \meter}$ (cite: gaia2018vizier; gaia2020);

- AAVSO Photometric All Sky Survey (APASS), $\SI{482}{\nano \meter}$ – $\SI{763}{\nano \meter}$ (cite: 2016yCat.2336....0H);

- Sloan Digital Sky Survey (SDSS), $\SI{482}{\nano \meter}$, $\SI{763}{\nano \meter}$ (cite: york2000sloan);

- Pan-STARRS survey, $\SI{613}{\nano \meter}$ – $\SI{960}{\nano \meter}$ (cite: kaiser2002pan);

- 2MASS, $\SI{1.65}{\micro \meter}$, $\SI{2.16}{\micro \meter}$ (cite: skrutskie2006two);

- Wide-field Infrared Survey Explorer (WISE), $\SI{3.35}{\micro \meter}$, $\SI{11.6}{\micro \meter}$ (cite: wright2010wide);

- Spitzer/IRAC, $\SI{3.6}{\micro \meter}$ – $\SI{7.8}{\micro \meter}$ (cite: fazio2004infrared);

- Spitzer/MIPS, $\SI{70}{\micro \meter}$ (cite: rieke2004multiband);

- IRAS satellite, $\SI{11.6}{\micro \meter}$, $\SI{61}{\micro \meter}$ (cite: neugebauer1984infrared);

- AKARI satellite, $\SI{18}{\micro \meter}$, $\SI{90}{\micro \meter}$ (cite: 2010A&A...519A..83T);

- Herschel/PACS, $\SI{100}{\micro \meter}$, $\SI{160}{\micro \meter}$ (cite: billot2006herschel);

- Herschel/SPIRE, $\SI{250}{\micro \meter}$, $\SI{350}{\micro \meter}$ (cite: griffin2010herschel);

- JCMT, $\SI{850}{\micro \meter}$ (cite: 2013ApJ...773..168M);

- ATCA, $\SI{3}{\milli\meter}$ (cite: ricci2010dust).

Moreover the integrated ALMA photometry was used, together with the interferometric observations described below. The X-ray data from (cite: montmerle1983einstein) were not used, as the X-ray emission is formed under non-LTE conditions, which is outside the approximations of our models.

# Simple analytic models

Before we begin constructing radiative-transfer models, it will be useful to construct a few simple analytic models to act as benchmarks for our later work. With these analytic models, we aim to approximately describe the observed interferometric visibilities. These models are as follows:

1.  A homogeneous ellipse described by $\alpha, \beta, \omega$, together with a point source and a background halo for the VLTI/GRAVITY visibilities, to model the inner disc.

2.  A narrow elliptical ring with a background halo for the ALMA visibilities, to model the outer disc.

Similar models were used by (cite: Lazareff) to model VLTI/PIONIER visibilities of about 50 Herbig AeBe discs. The introduction of a halo allows us to lower the visibility at short baselines that are not sampled by the VLTI. However, this contribution is not merely a mathematical aid, but is directly observed by coronagraphic instruments, such as the VLT/SPHERE – see Figure [11](#fig:multi). The two models can be described as follows: $$\begin{align}
\label{eq:analmod}
    V_1(u, v) &= \frac{f_{\rm s} + f_{\rm c} \mu_{\rm e}(u, v;  \alpha, \beta, \omega)}{f_{\rm h} + f_{\rm e} + f_{\rm s}}, \\
    V_2(u, v) &= \sqrt{A + B\mu_\delta^2(u, v; \alpha, \beta, \omega)}\,,
\end{align}$$ where the visibility of an ellipse, describing the circumstellar disc, is: $$\begin{equation}
    \mu_{\rm c} (u, v; \alpha, \beta, \omega) = \frac{2 J_1\left(2\pi \sqrt{\alpha^2 u'^2 + \beta^2 v'^2} \right)}{2\pi \sqrt{\alpha^2 u'^2 + \beta^2 v'^2}}\,,
\end{equation}$$ and of a $\delta$-ring is: $$\begin{equation}
        \mu_{\rm \delta}(u, v; \alpha, \beta, \omega) = J_0\left(2\pi \sqrt{u'^2 \alpha^2 + v'^2 \beta^2}\right)\,,
\end{equation}$$ with the rotated aperture-plane coordinates given by: $$\begin{equation}
\begin{pmatrix}
u' \\
v'
\end{pmatrix}
=
\begin{pmatrix}
\cos\omega & +\sin\omega \\
-\sin\omega & \cos\omega
\end{pmatrix}
\begin{pmatrix}
u \\
v
\end{pmatrix}\,.
\end{equation}$$ The parameters $f_{\rm c}, f_{\rm h}, f_{\rm s}$ denote the fractional contributions of the circumstellar disc, the halo and the star. The coordinates $u, v$ and the angular sizes $\alpha$ and $\beta$ are dimensionless, that is, given in cycles per baseline and in radians, respectively. As the separations of the telescopes (or antennas) is much larger than the wavelength that we are observing, we commonly use dimensionless units such as M$\lambda$ to denote $10^6$ cycles per baseline. Best-fit parameters are estimated in Tables [2](#tab:modelB) and [3](#tab:modelC).

|      Parameter      | value | $\sigma$ |
|:-------------------:|:-----:|:--------:|
|   $\alpha$ (mas)    | 1.243 |   0.2    |
|    $\beta$ (mas)    | 1.663 |   0.3    |
| $\omega$ $(^\circ)$ |  147  |    2     |
|     $f_{\rm s}$     | 0.68  |   0.1    |
|     $f_{\rm c}$     | 0.24  |   0.1    |
|     $f_{\rm h}$     | 0.072 |  0.005   |

: Best-fit parameters of the homogeneous ellipse model suitable for the VLTI measurements of the accretion region.

Table notes: The linear scale of the accretion region is 0.24 au.

|       Parameter        | value | $\sigma$ |
|:----------------------:|:-----:|:--------:|
|     $\alpha$ (mas)     |  329  |    1     |
|     $\beta$ (mas)      |  304  |    1     |
|  $\omega$ $(^\circ)$   |  156  |    2     |
| $A ~( 10^5 \rm{Jy}^2)$ | 3.721 |  0.003   |
| $B ~( 10^5 \rm{Jy}^2)$ | 3.827 |  0.012   |

: Best-fit parameters of the elliptical $\delta$-ring model, suitable for the ALMA visibilities.

Table notes: The $A$ and $B$ parameters were used to rescale the visibilities in physical units (Jy) into a unit-less quantity for further analysis.

These analytic models were used as a benchmark for the more complex radiative-transfer models, providing the angular extent of the observed structures as a guide. Also, they provided a way to deal with the fully resolved component in the VLTI observations, and with the fact that the ALMA observations are in physical and not in relative units. The interferometric quantities were rescaled in the following way: $$\begin{align}
    V^2_{ \rm VLTI,new} &=\frac{1}{e^2} V^2_{\rm VLTI}\,,\\
    T_{3\,,\rm VLTI,new} &=\frac{1}{e^3} T_{3\,,\rm VLTI}\,,\\
    V^2_{\rm ALMA,new} &=-A + \frac{1}{B} V^2_{\rm ALMA}\,,
\end{align}$$ where $e = 0.928$ from the homogeneous ellipse model, and $A, B$ are taken from the elliptical $\delta$-ring model. The best-fit parameters and their uncertainties (68% confidence intervals of the marginalized posterior distributions) were obtained via a MCMC simulation with an uninformative prior. In each case, two solutions were obtained for two position angles separated by $180^\circ$, and only the solution with $\omega < 180^\circ$ was considered. Initial simulations were performed with 32 walkers and $10^4$ steps. The marginalized posteriors were used as a starting value for the next iteration: these new simulations ran with 64 walkers for a total of $10^5$ steps, with a $30\%$ burn-in phase. All simulations were implemented using the `emcee` package (cite: foreman2013emcee).

From all these models, we infer an inclination of the inner accretion region at $i_{\rm in} = 40^\circ\pm 3 ^\circ$ and of the outer disc at $i_{\rm out} = 22^\circ\pm 1^\circ$. The positions angles seem to be somewhat aligned, at $\omega_{\rm in} = 147^\circ\pm 2^\circ$ for the inner accretion region and $\omega_{\rm out} = 156^\circ\pm 2^\circ$ for the outer disc.

The misalignment $\xi$ can be calculated, for example, using the spherical law of cosines: $$\cos \xi = \cos i_{\rm in} \cos i_{\rm out}  + \sin i_{\rm in} \sin i_{\rm out} \cos(\Delta \omega) = 18.5 ^\circ\pm 4 ^\circ\,.$$

For comparison, (cite: bohn2022probing) investigated the inner and outer disc misalignment of a series of protoplanetary discs, including DoAr 44, also based on VLTI/GRAVITY and ALMA interferometry. For DoAr 44, they derived an inner disc inclination of $i_{\rm in} = \left(25.67^{+7.91}_{-9.71}\right) ^\circ$ and an outer disc inclination of $i_{\rm out} = \left(23.20^{+1.98}_{-1.58}\right) ^\circ$.

(cite: casassus2018inner) used VLT/SPHERE/IRDIS polarimetric measurements and ALMA Band 7 continuum measurements to derive a misalignment of $\xi = 30^\circ\pm 5 ^\circ$.

(cite: bouvier2020probing) derived an inner disc inclination of $i_{\rm in} = 34^\circ\pm 2 ^\circ$ based on VLTI/GRAVITY interferometric visibilities, with a position angle of $\omega_{\rm in} = 140^\circ\pm 3^\circ$.

(cite: arce2023radio) derived outer disc inclinations for two high-resolution ALMA Band 6 and Band 7 observations, $i_{\rm out} = 21.8^\circ\pm0.3^\circ$. Alternatively, they derive an outer disc inclination of $24.4^\circ\pm0.4^\circ$ using H-band polarised intensity images from VLT/SPHERE/IRDIS. They derive an inner-outer misalignment of $\xi = \left(21.4^{+6.7}_{-8.3}\right)^\circ$.

In conclusion, our results are in agreement for the outer inclination (1 sigma), as well as for the new value of misalignment. The inner inclination is more uncertain, as the differences between models seem to be of the order of 2 sigma.

# `Pyshellspec` radiative-transfer models

The primary tool used to create radiative transfer models for this work, `Pyshellspec`, was developed by (cite: pyshellspec2018) and (cite: pyshellspec) and to model the $\beta$ Lyræ A system. `Pyshellspec` generates various observables, such as interferometric visibilities and closure phases, based on synthetic images generated by `Shellspec`, a long-characteristics radiative-transfer code by (cite: shellspec2004). `Shellspec` is used for modelling binary stars moving within circumstellar matter (i.e., gas and dust), and includes a series of parametrically defined objects, such as stars, rings, discs, jets or spherical shells, which shall be later described.

The radiative-transfer equation is integrated along the line of sight: $$\begin{equation}
    {\rm d} I_\nu = (\epsilon_\nu - \chi_\nu I_\nu) {\rm d}x\,,
\end{equation}$$ where $\epsilon_\nu, \chi_\nu$ are the total emissivity and the total opacity of the medium, $I_\nu$ is the specific monochromatic intensity, and ${\rm d} x$ is measured along the ray.

The total opacity is given as the sum of the absorption opacity $\kappa_\nu$ and the scattering opacity $\sigma_\nu$: $$\begin{equation}
     \chi_\nu = \kappa_\nu + \sigma_\nu\,.
\end{equation}$$ `Shellspec` allows the user to include into $\kappa_\nu$ the following sources of absorption opacity:

- Spectral line opacity,

- HI (neutral hydrogen) bound-free opacity,

- HI free-free opacity,

- H$^-$ (negative hydrogen ion) bound-free opacity,

- H$^-$ free-free opacity,

- Mie absorption on dust,

and the following sources of scattering opacity:

- Thompson (i.e., low-energy Compton) scattering on free electrons,

- Rayleigh scattering on neutral hydrogen,

- Mie scattering on dust.

The dust opacities are summed over all the included dust species that are located in a cold enough region, allowing for dust condensation.

The total emissivity is calculated as the sum of the thermal emissivity and the emission due to scattering: $$\begin{equation}
    \epsilon_\nu = \epsilon^{\rm th}_\nu + \epsilon^{\rm sc}_\nu = B_\nu(T) \kappa_\nu + \epsilon^{\rm sc}_\nu\,,
\end{equation}$$ where $B_\nu$ is the Planck function. One limitation is that `Pyshellspec` is a single-scattering radiative-transfer tool. That means that the stellar light scattered off the disc is accounted for in the synthetic image. We tested models with and without scattering opacity. The absorptive term leads a decrease of the SED at mid-infrared wavelengths, however, this should be at least partly compensated by the emissive term, scattering thermal radiation from other directions, if it is accounted for and if the intensity is approximately isotropic. According to these tests, we consider our nominal models as good approximations.

For the evaluation of the goodness of fit, a standard $\chi^2$ metric is defined: $$\begin{equation}
    \chi^2 = \chi^2_{\rm SPE} + \chi^2_{\rm V2} + \chi^2_{\rm CP} + \chi^2_{\rm T3} + \chi^2_{\rm SED}\,,
\end{equation}$$ where $\chi^2_{\rm SPE}$ is the $\chi^2$ contribution from the spectroscopic data, $\chi^2_{\rm V2}$ the squared visibilities, $\chi^2_{\rm CP}$ the closure phases, $\chi^2_{\rm T3}$ the triple product amplitudes, and $\chi^2_{\rm SED}$ the SED. These are defined as: $$\begin{align}
    \chi^2_{\rm SPE} &= \sum_{i = 1}^{N_{\rm SPE}} \left(\frac{I^i_{\lambda\,, \rm obs} - I^i_{\lambda\,, \rm syn}}{\sigma_i}\right)^2\,, \\
    \chi^2_{\rm V2} &= \sum_{i = 1}^{N_{\rm V2}} \left(\frac{|V^i_{\rm obs}|^2 - |V^i_{\rm syn}|^2}{\sigma_i}\right)^2 \\
    \chi^2_{\rm CP} &= \sum_{i = 1}^{N_{\rm CP}} \left(\frac{ \mathrm{arg}\,(T_3^i)_{\rm obs} -\mathrm{arg}\,(T_3^i)_{\rm syn} }{\sigma_i}\right)^2\,,\\
    \chi^2_{\rm T3} &= \sum_{i = 1}^{N_{\rm T3}} \left(\frac{ |T_3|^i_{\rm obs} -|T_3|^i_{\rm syn} }{\sigma_i}\right)^2\,,\\
    \chi^2_{\rm SED} &= \sum_{i = 1}^{N_{\rm SED}} \left(\frac{ F^i_{\lambda \,, \rm obs} - F^i_{ \lambda \,, \rm syn} }{\sigma_i}\right)^2\,,
\end{align}$$ where $I_{\lambda\,,{\rm obs}}$ and $I_{\lambda\,,{\rm syn}}$ denote the observed and synthetic monochromatic intensities, respectively, $V$ the visibilities, ${\rm arg}\,T_3$ the closure phases, $|T_3|$ the triple product amplitudes, and $F_{\lambda}$ the monochromatic fluxes.

However, the total $\chi^2$ was not optimised globally, as this is exceedingly difficult. The only contribution optimised globally was $\chi^2_{\rm SED}$, while the other contributions were optimised separately for the accretion region, the inner disc, and the outer disc.

Our model comprises three main parts:

1.  the accretion region, described in our model using a star, a shell of infalling gas and a hot innermost disc (up to 0.1 au),

2.  an intermediary disc (0.2 - 1 au), and

3.  the outer disc (40 - 60 au).

The discs and the spherical shell were modelled using `Shellspec`’s `DISC` and `SHELL` objects, respectively.

## The central star

The simplest element in our model is the central star. A synthetic stellar spectrum is provided as a boundary condition. This stellar spectrum was obtained by interpolation in the PHOENIX grid (cite: husser2013new), similarly to that in (cite: nemravova2016xitauri). The interpolation was performed in the 3-dimensional parameter space of the effective temperature $T_{\rm eff}$, the (logarithm of) surface gravity $\log g$ and the metallicity $Z$. The stellar parameters were set according to previously published works (cite: andrews2009protoplanetary; bouvier2020probing),

$r_\star = 2.0\,R_\odot$, $T_\star = 4750\,{\rm K}$, $M_\star = 1.4\,M_\odot$.

## The `DISC` object

The primary object used to model discs in `shellspec` is the `DISC`. The disc is parameterized by the following equations:

$$\begin{align}
\Sigma(R) &= \Sigma(R_{\rm innb}) \left(\frac{R}{R_{\rm innb}}\right)^{e_{\rm densnb}}, \\
H(R) &= R \frac{c_s(R)}{v(R)}, \\
c_s(R) &= \sqrt{\frac{\gamma k_{\rm B} T(R)}{\mu}}, \\
T(R) &= T_{\rm nb} \left(\frac{R}{R_{\rm innb}}\right)^{e_{\rm tempnb}}, \\
\varrho_{\rm dstnb} &= Z \varrho_{\rm nb}.
\end{align}$$ where:

- $\Sigma(R_{\rm innb})$, $R_{\rm innb}$, and $e_{\rm densnb}$ describe the surface density, inner radius, and density power-law exponent, respectively.

- $H(R)$ represents the disc’s scale height.

- $v(R)$ denotes the Keplerian velocity.

- $c_s$ is the speed of sound, with $\gamma = c_p / c_v$ (the ratio of specific heats) and $\mu$ (the mean molecular weight).

- $T(R)$ describes the temperature profile, parametrized by $T_{\rm nb}$ (the temperature normalization) and $e_{\rm tempnb}$ (the temperature exponent).

- $\varrho_{\rm dstnb}$ represents the dust density in the protoplanetary disc, linked to the gas density $\varrho_{\rm nb}$ through a constant (solar) metallicity $Z = 0.0122$ (cite: ASPLUND20061).

The model accounts for scattering and absorption opacities due to dust particles of various sizes and mineral compositions. A mix of 90% water ice and 10% forsterite is used as a proxy for the actual mineralogical composition. This is a slightly higher ratio than the traditional 80 % ices to 20 % refractory materials (cite: Dodson-Robinson_2011; pontoppidan2014volatiles). Detailed dust evolution modelling suggests that virtually all dust grains in the outer disc are covered in ice (cite: krijt2016tracing), impacting its optical properties (cite: kohler2015dust; ysard2018optical). We account for this fact using an increased water ice content.

## The `SHELL` object

The velocity $v(r)$, density and temperature profiles in the `SHELL` are described as follows: $$\begin{equation}
    v(r)=v_0\left(1-\frac{r_{\rm csh}}{r}\right)^{e_{\rm velsh}}\,,
\end{equation}$$ $$\begin{equation}
    \rho(r)=\varrho_{\rm sh} \left(\frac{r_{\rm insh}}{r}\right)^2 \frac{v(r_{\rm insh})}{v(r)}\,,
\end{equation}$$ $$\begin{equation}
    T(r) =T_{\rm sh}=\rm{const.}\,,
\end{equation}$$ where $r_{\rm csh}, r_{\rm insh},e_{\rm denssh}$ are parameters. The shell is truncated at an outer radius $r_{\rm outsh}$. To obtain a contribution to the opacity due to Thompson scattering, the electron number density is computed using the Saha equation based on the local densities and the temperature, with the assumption of LTE.

## Accretion region model

The geometry that best replicates the observables is the following: a central star, surrounded by a spherical shell of hot gas, surrounded by a disc. The geometry of the disc was taken from the MCMC analysis of the analytic models, the inclination of $i = 40^\circ$ is fixed, together with the position angle of 147$^\circ$. The comparison of the spectroscopic and interferometric VLT+VLTI measurements with our synthetic data is shown in Figure [4](#fig:inner_shell_disc_model).

A search for the best-fit was performed on a sub-space of the parameter space that was identified (via trial and error) as being spanned by the most relevant parameters:

1.  $R_{\rm outsh}$, the outer radius,

2.  $v(R_{\rm insh})$, the velocity at the inner boundary,

3.  $e_{\rm velsh}$, the exponent of the power-law describing the velocity field of the shell,

4.  $T_{\rm sh}$, the (constant) temperature,

5.  $\varrho_{\rm sh}$, the density at the inner boundary.

The $R_{\rm insh}$ had to be fixed slightly above the stellar surface (for not to cause a collision with the `STAR` object).

The central star dominates the flux contribution in the optical domain. The star is surrounded by an envelope of optically thin, hot ($\approx \SI{9000}{\kelvin}$) gas, with a density of ($\approx \SI{2e-13}{\gram \per \cubic \centi \meter}$). This envelope extends up to about 0.1 au, where it encounters the innermost disc, and is responsible for the majority of the H$\alpha$ emission. The radial velocity of the gas in this envelope reaches $v = \SI{385}{\kilo \meter \per \second}$ The inner rim of this disc is the main source of near-infra-red continuum radiation, and is responsible for the observed VLTI/Gravity visibilities.

The model was fitted to the VLTI/Gravity observations, the VLT $H\alpha$ spectra. The respective normalized $\chi^2$ contributions are $\chi^2_{\rm SPE} / N_{\rm SPE} = 0.98$ and $\chi^2_{\rm V2} / N_{\rm V2} = 1.5$. The best-fit values of these parameters are listed in Tab. [4](#tab:bestfit).

From the density and velocity of the gas in the accretion envelope shell, we derive an accretion rate of: $$\begin{equation}
    \dot{M} = (6.1\pm 0.2)\cdot10^{-8}\,M_\odot\, {\rm yr}^{-1}\,,
\end{equation}$$ which is surprisingly similar to the result obtained by (cite: bouvier2020investigating).

As the temperatures and spatial scales of this accretion region clearly do not account for the SED at mm-wavelengths and ALMA visibilities, we must model the cold outer disc.

![](img/acc_reg.png)

## Outer disc model

To account for the ALMA visibilities and CLEANed images, we were forced to introduce a cavity. A scan over a variety of parameters (particle size, temperature, density, inner radius, outer radius) fitting the $\chi_{\rm V2}^2 + \chi^2_{\rm SED}$ was performed. The constraint on the total area of the disc is given primarily from the ALMA interferometry, where the inner and outer boundaries are visible (up to the background RMS level, the dust extends up to $\approx 80$ au, see Fig. [11](#fig:multi)). The density profile was simplified to a power-law, and the complex “ring-within-a-ring" morphology was not fitted in detail.

In our model, the outer disc extends from 40 au to 60 au, with the mid-plane dust density of $\SI{1e-14}{\gram \per \cubic \centi \meter}$ at the inner boundary. The dust is given by a mix of water ice and forsterite, in a ratio of 90 % and 10 %, with particle sizes of $a = \SI{1}{\micro \meter}$. The mid-plane temperature at the 40 au inner boundary is $\SI{60}{\kelvin}$, and decreases as a power-law with an exponent of $-0.5$.

The aspect ratio $H/r$ is 0.08 for the inner region of the outer disc (40 au), in agreement with (cite: casassus2018inner), which then gradually increases to 0.10 in the outermost regions (60 au). By integrating the vertical density profile, we obtain the dust surface density of the order of $\Sigma_{\rm dust} \gtrsim 0.5\,{\rm g}\,{\rm cm}^{-2}$. By integrating over the radial direction, we obtain the dust mass of $$\begin{multline}
M_{\rm dust} = \int_{R_{\rm in nb}} ^{R_{\rm outnb}} 2 \pi r \Sigma_{\rm dust}(r) {\rm d} r= \\ = \int_{R_{\rm in nb}} ^{R_{\rm outnb}} 2 \pi r \varrho_{\rm dstnb} r \sqrt{\frac{r}{GM}} \sqrt{\frac{\gamma k_{\rm B} T(r)}{\mu}} {\rm d} r \gtrsim 100 M_{\rm Earth}\,.
\end{multline}$$ This is still a lower limit though, as the outer disc in our model is optically thick: the best-fit dust density estimations do not have a clear upper limit from fitting the SED, as various optically thick solutions appear very similar; see Fig. [6](#fig:dust_comparisons_systematic)).

For comparison, (cite: cieza2021ophiuchus) assumed a single value of temperature of $T = 20\,{\rm K}$ and derived $M_{\rm dust} = 54\,M_{\rm Earth}$ for DoAr 44, which is again a lower limit. Our model requires an optically thick outer disc in the $\SI{870}{\micro \meter}$ continuum, which is necessary to explain the SED and the sub-mm spectral index of $\alpha\approx 2$. The work (cite: arce2023radio) also suggests that the disc is optically thick, based on the well-constrained spectral index.

(cite: leiendecker2022dust) derived a dust mass of $84^{+7.0}_{-3.5}\,M_{\rm Earth}$ for the outer disc, based on ALMA Band 6 observations. Their mid-plane temperatures are around $30\,{\rm K}$, and they increase with increasing height above the mid-plane. On the contrary, our model is vertically isothermal, and requires about 50 – 60 K in the outer regions, in order to account for the Spitzer/MIPS ($\SI{70}{\micro \meter}$) and Herschel/PACS ($\SI{100}{\micro \meter}$) far infrared fluxes.

![](img/ALMA_IF.png)

![](img/dust_comparisons_systematic.png)

## Intermediate disc model

A model consisting of the innermost region and the outer disc is enough to account for the spectra, interferometric observables and the SED measurements in the visible to near-IR, as well as the sub-mm and mm regions. However, a deficit in the SED is present in the mid-IR, which has to be compensated for by introducing a warm intermediary region in the 0.2 – 1 au range. We modelled this region using a `DISC` object, and its parameters can be found in Tab. [4](#tab:bestfit). The global density and temperature profiles can also be found in Tab. [4](#tab:bestfit).

The temperature at the inner edge reaches 1000 K, and drops to 380 K at the outer edge. (cite: salyk2015detection) detected a large water-vapour luminosity originating from DoAr 44 using the Gemini-North telescope, and deduced the temperature of this water vapour to $T \approx \SI{450}{\kelvin}$. In our model, these temperatures are reached precisely in this intermediate disc.

It appears that this intermediate disc region has been imaged, but unresolved, by the ODISEA programme in Band 6 (cite: cieza2021ophiuchus) – see Fig. [11](#fig:multi).H. However, the dimensions of this intermediate disc are not constrained by interferometry or other spatially resolved methods. This means that there exists a large set of acceptable models of this region, extending up to 5 – 7 au.

| Parameter | Object | Best-fit | $\sigma$ | Unit |
|:---|:---|---:|---:|:---|
| $r_\star$ | `STAR` | 2.0 | 0.2 | $R_\odot$ |
| $T_\star$ | `STAR` | 4750 | 150 | K |
| $M_\star$ | `STAR` | 1.4 | 0.2 | $M_\odot$ |
| $r_{\rm insh}$ | `SHELL` | 3 | 0.1 | $R_\odot$ |
| $r_{\rm outsh}$ | `SHELL` | 22 | 1 | $R_\odot$ |
| $v_{\rm sh}$ | `SHELL` | 385 | 5 | km s^−1^ |
| $\varrho_{\rm sh}$ | `SHELL` | $1.8\cdot10^{-13}$ | $3\cdot10^{-14}$ | $\si{ \gram \per \centi \meter \cubed}$ |
| $T_{\rm sh}$ | `SHELL` | 9100 | 200 | K |
| $e_{\rm velsh}$ | `SHELL` | 1 | 0.1 | 1 |
| $r_{\rm innb1}$ | `DISC` | 16.5 | 3 | $R_\odot$ |
| $r_{\rm outnb1}$ | `DISC` | 35 | 5 | $R_\odot$ |
| $\varrho_{\rm nb1}$ | `DISC` | $1.0\cdot10^{-8}$ | $3\cdot10^{-9}$ | $\si{ \gram \per \centi \meter \cubed}$ |
| $T_{\rm nb1}$ | `DISC` | 1900 | 200 | K |
| $e_{\rm dennb1}$ | `DISC` | -0.5 | 0.1 | 1 |
| $e_{\rm tmpnb1}$ | `DISC` | -0.7 | 0.1 | 1 |
| $r_{\rm innb2}$ | `DISC` | 43 | 10 | $R_\odot$ |
| $r_{\rm outnb2}$ | `DISC` | 215 | 20 | $R_\odot$ |
| $\varrho_{\rm nb2}$ | `DISC` | $6\cdot10^{-10}$ | $1\cdot10^{-10}$ | $\si{ \gram \per \centi \meter \cubed}$ |
| $T_{\rm nb2}$ | `DISC` | 1000 | 20 | K |
| $e_{\rm dennb2}$ | `DISC` | -1.3 | 0.1 | 1 |
| $e_{\rm tmpnb2}$ | `DISC` | -0.6 | 0.1 | 1 |
| $r_{\rm innb3}$ | `DISC` | 8600 | 200 | $R_\odot$ |
| $r_{\rm outnb3}$ | `DISC` | 12900 | 200 | $R_\odot$ |
| $\varrho_{\rm dstnb3}$ | `DISC` | $1\cdot10^{-14}$ | \* | $\si{ \gram \per \centi \meter \cubed}$ |
| $T_{\rm nb3}$ | `DISC` | 60 | 10 | K |
| $e_{\rm dennb3}$ | `DISC` | -2.5 | 0.1 | 1 |
| $e_{\rm tmpnb3}$ | `DISC` | -0.8 | 0.1 | 1 |
| Global model | $\chi^2_{\rm SED}$ | 7022 | $N_{\rm SED}$ | 128 |
| Accretion region | $\chi^2_{\rm SPE}$ | 201 | $N_{\rm SPE}$ | 200 |
| Accretion region | $\chi^2_{\rm V2,VLTI}$ | 8648 | $N_{\rm IF,VLTI}$ | 512 |
| Accretion region | $\chi^2_{\rm CP}$ | 170 | $N_{\rm CP}$ | 416 |
| Outer disc | $\chi^2_{\rm V2,ALMA}$ | 18689 | $N_{\rm V2,ALMA}$ | 3886 |

:  Best-fit parameters of the global model.

Table notes: Model parameters are separated into parameters belonging to the 1. star, 2. shell, 3. innermost disc, 4. intermediary disc, 5. outer disc. (\*) The dust density of the outer disc is only given as a lower bound. The $\chi^2_{\rm SED}$ is computed based on the global model, whereas the other contributions were calculated in the separate components.

![](img/SED_combined.png)

![](img/temp_dens_profile.png)

# Discussion

We shall now discuss the broader implications of our global model of DoAr 44 for the disc geometry, condensation of solids, and planet formation.

## What is the geometry of the accretion region?

As discussed in Sect. [2.1](#Halpha), the detailed geometry of the inner accretion region is variable on the scale of days, and is most likely connected to magnetic funnel flows, described in (cite: bessolaz2008accretion; takasao2018three; bouvier2020investigating). We have modelled the inner optically thin matter responsible for the averaged H$\alpha$ emission using axially symmetric conical shapes, but optimising always resulted in large opening angles, or a spherically symmetric shell of gas.

Around this optically thin shell of gas, we include an optically thick innermost disc to explain the VLTI/GRAVITY visibilities. In our model, the innermost disc appears to be misaligned by about $(18.5 \pm 4)^\circ$ with respect to the outer disc. The topic of misaligned protoplanetary discs has gained significant attention in recent years, as these discs could produce exoplanets on highly inclined orbits, which are now readily observed using the Rossiter-McLaughlin effect (cite: zak2024).

A variety of mechanisms to produce a misaligned disc have been identified, e.g., compact stellar binaries (cite: nixon2013), using an outside perturbing companion (cite: dogan2015), stellar fly-bys (cite: nealon2019) or oblique infall (cite: kuffmeier2021). In our case, we can rule out the presence of a compact binary within the inner disc from the VLTI/GRAVITY observations, no infall is currently observed with ALMA, and no planetary companions have been confirmed, so the origin of this misalignment remains uncertain.

## Does the observed ring coincide with a condensation line of a volatile, or must it be caused by an exoplanet?

The overall temperature profile in our model predicts around 50 – 60 K around the distance of 48 au, in order to account for far-infrared continuum radiation. This relatively high temperature of layers emitting the respective radiation, e.g., compared to (cite: leiendecker2022dust), prevents condensation of certain solids (cite: martin2014thermal).

The scientific literature on solar system comets, which originate from these cold outer regions, is a good guide with respect to the expected chemical composition. The major volatiles found in comets are H$_2$O, CO, CO$_2$, CH$_4$, and NH$_3$, with water ice being typically the most abundant (cite: mumma2011chemical). The comet’s composition is often given with respect to the water ice content. CO can contribute up to 30 % of the mass of the water ice, CO$_2$ up to 10 %, and the other chemicals generally contribute less than 1 % (cite: 1998A&A...330..375G). Different ratios were obtained for example by Rosetta orbiting 67P/Churyumov-Gerasimenko, where CO$_2$ formed 7.5 % and CO 3 % (cite: 10.1093/mnras/stad3005). These ratios might be lower than what we expect in the outer disc, as 67P/Churyumov-Gerasimenko is a periodic comet, which effectively loses highly volatile ices during every perihelion passage.

Water ice does not seem like a good candidate for the condensation line at this distance. Given the temperature profile from our models, the water ice line occurs somewhere between 4–6 au, somewhat similar to the $\approx 3$ au water ice line distance in our early solar system.

The condensation of carbon monoxide is not responsible for the continuum emission at this distance, because its condensation temperature should be 23 to 28 K (cite: Zhang_2013).

However, we cannot exclude the possibility that CO is condensed in the mid-plane, which could be colder than 50 to 60 K, but the mid-plane is inaccessible due to optical thickness.

Possibly, carbon dioxide could be transitioning from the gaseous to the solid state at the peak emission radius in DoAr 44. However, we must proceed with caution: solid CO$_2$ is associated with mid-IR bands, which would be in the range observed by the Spitzer/IRS instrument. These CO$_2$ bands around $\SI{15}{\micro \meter}$ are often observed around YSOs (cite: cook2011thermal). Due to the complicated nature of the silicate spectral features that overlap with the possibly present solid CO$_2$ feature, we have decided to refrain from further interpretations.

The possibility of other solids, forming the ring in DoAr 44, seems improbable due to the total dust mass in the outer disc. There is probably more than $100\, M_{\rm Earth}$ of dust in the outer disc, which means it cannot be composed of some rare chemical.

## The planet formation mass budget

According to the outer disc model, depending mainly on the representative particle size, ranging from fine $\SI{1e-2}{\micro \meter}$ to coarser $\SI{1e2}{\micro \meter}$, we obtain the lower limit of dust mass, $M_{\rm dust} > 100\, M_{\rm Earth}$.

Coincidentally, such a value is similar to what is commonly presumed for our own solar system ( ${\approx}130\,M_{\rm Earth}$, (cite: brovz2021early)), but the latter is for the whole dust disc, not a narrow ring. This leads us to think that the ring structure at 48 au, seen in the ALMA data, might very well be an analogue of the Kuiper belt in our own solar system, which currently extends from about 30 au to about 55 au, and presumably had around 15 – 20 $M_{\rm Earth}$ in planetesimals (cite: Nesvorny_2018ARA&A..56..137N).

Extrapolating the outer disc surface density to the inner disc, using the (cite: hayashi_mmsn) surface density exponent of $\Sigma \propto r^{-1.5}$, we obtain a hypothetical amount of solids in the cavity from 6 to 40 au around $225\, M_{\rm Earth}$; using a shallower exponent of $-1.0$, the result changes to ${\approx}150\,M_{\rm Earth}$ (see also Fig. [8](#fig:rho_and_T)). This suggests that former, "Class I" disc of DoAr 44 was more massive than in our solar system and that the cavity should contain more, or more massive planets.

# Conclusions

In this work, we present the first global radiative-transfer model of the protoplanetary disc DoAr 44, based on VLT/UVES and VLT/X-shooter spectra, VLTI/GRAVITY squared visibilities, triple product amplitudes and closure phases, ALMA interferometry, and a variety of spectral energy distribution measurements, spanning from the near ultraviolet to millimetre wavelengths. From this model, we have concluded the following:

1.  The geometry of the inner accretion region can be described using a shell of gas, heated to about 9 000 K, surrounding the young star. This gas is moving at speeds up to $\SI{385}{\kilo \meter\,\second^{-1}}$. This shell is surrounded by an innermost disc ($16\,R_\odot$ to $35\,R_\odot$, i.e., 0.07 to 0.16 au), which is responsible for the VLTI/GRAVITY K-band visibilities.

2.  The accretion rate is already low, $\dot{M} = (6.1 \pm 0.2)\cdot10^{-8}\,M_\odot\, {\rm yr}^{-1}$, but not negligible.

3.  The continuum dust emission in the outer disc extends from about ($36\pm1$) au to about $(60\pm4)$ au. A large part of the emission is localized in a narrow ring centered at ($48\pm1$) au. The temperature in this region is about 60 K. The observations are not compatible with a monotonic density profile, and a large central cavity must be present. This cavity was likely cleared by forming ice/gas planets.

4.  The ring at ($48\pm1$) au does not correspond to the condensation line of water ice or carbon monoxide due to high temperature (50 – 60 K). The only possible condensation line that could cause such a ring is carbon dioxide.

5.  The dust mass present in the outer disc is more than $100\,M_{\rm Earth}$, according to the integral of the surface density profile.

6.  An intermediate disc, for the moment unresolved by ALMA, extending from 0.2 to 1 au or beyond, must be present, according to the SED constraints. From this region, the observed water vapour emission probably originates.

# Acknowledgements

We would like to thank the anonymous referee for their time and care, which helped improve this work. We would also like to thank S. Casassus for help with the interpretation of some ALMA measurements.

This work has been supported by the Czech Science Foundation (grant no. 25-16507S).

This paper makes use of the following ALMA data sets: ADS/JAO.ALMA#2019.1.00532.S, ADS/JAO.ALMA#2019.1.01111.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

Based on data obtained from the ESO Science Archive Facility with DOI(s): <https://doi.eso.org/10.18727/archive/21>, <https://doi.eso.org/10.18727/archive/50>, <https://doi.eso.org/10.18727/archive/71>.

Based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programme(s) 69.C-0481, 093.C-0658, 085.C-0764.

This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

78 natexlab

(ref: andrews2018disk) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJ Letters, 869, L41

(ref: andrews2009protoplanetary) Andrews, S. M., Wilner, D., Hughes, A., Qi, C., & Dullemond, C. 2009, ApJ, 700, 1502

(ref: 2011ApJ...732...42A) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, , 732, 42

(ref: 2010ApJ...723.1241A) Andrews, S. M., Wilner, D. J., Hughes, A. M., Qi, C., & Dullemond, C. P. 2010, , 723, 1241

(ref: arce2023radio) Arce-Tord, C., Casassus, S., Dent, W. R., et al. 2023, MNRAS, 526, 2077

(ref: ASPLUND20061) Asplund, M., Grevesse, N., & Jacques Sauval, A. 2006, Nuclear Physics A, 777, 1, special Isseu on Nuclear Astrophysics

(ref: avenhaus2018disks) Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, ApJ, 863, 44

(ref: 2018ApJ...863...44A) Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, , 863, 44

(ref: benisty2021circumplanetary) Benisty, M., Bae, J., Facchini, S., et al. 2021, ApJ Letters, 916, L2

(ref: SkyMapper) Bessell, M., Bloxham, G., Schmidt, B., et al. 2011, , 123, 789

(ref: bessolaz2008accretion) Bessolaz, N., Zanni, C., Ferreira, J., Keppens, R., & Bouvier, J. 2008, A&A, 478, 155

(ref: billot2006herschel) Billot, N., Agnèse, P., Auguères, J.-L., et al. 2006, in Space Telescopes and Instrumentation I: Optical, Infrared, and Millimeter, Vol. 6265, SPIE, 81–92

(ref: bohn2022probing) Bohn, A., Benisty, M., Perraut, K., et al. 2022, Astronomy & Astrophysics, 658, A183

(ref: bouvier2020investigating) Bouvier, J., Alecian, E., Alencar, S. H. P., et al. 2020a, A&A, 643, A99

(ref: bouvier2020probing) Bouvier, J., Perraut, K., Le Bouquin, J.-B., et al. 2020b, A&A, 636, A108

(ref: brovz2021early) Brož, M., Chrenko, O., Nesvorný, D., & Dauphas, N. 2021, Nat Astronomy, 5, 898

(ref: pyshellspec) Brož, M., Mourard, D., Budaj, J., et al. 2021, A&A, 645, A51

(ref: shellspec2004) Budaj, J. & Richards, M. T. 2004, Contributions of the Astronomical Observatory Skalnate Pleso, 34, 167

(ref: casassus2018inner) Casassus, S., Avenhaus, H., Pérez, S., et al. 2018, MNRAS, 477, 5104

(ref: 2023MNRAS.526.1545C) Casassus, S., Cieza, L., Cárcamo, M., et al. 2023, , 526, 1545

(ref: casassus2019) Casassus, S., Pérez, S., Osses, A., & Marino, S. 2019, Monthly Notices of the Royal Astronomical Society: Letters, 486, L58

(ref: cieza2021ophiuchus) Cieza, L. A., González-Ruilova, C., Hales, A. S., et al. 2021, MNRAS, 501, 2934

(ref: cook2011thermal) Cook, A., Whittet, D., Shenoy, S., et al. 2011, ApJ, 730, 124

(ref: Dodson-Robinson_2011) Dodson-Robinson, S. E. & Salyk, C. 2011, ApJ, 738, 131

(ref: dogan2015) Doğan, S., Nixon, C., King, A., & Price, D. J. 2015, , 449, 1251

(ref: epsaillat2007) Espaillat, C., Calvet, N., D’Alessio, P., et al. 2007, , 670, L135

(ref: espaillat2010unveiling) Espaillat, C., D’Alessio, P., Hernández, J., et al. 2010, ApJ, 717, 441

(ref: fazio2004infrared) Fazio, G., Hora, J., Allen, L., et al. 2004, ApJ Supplement Series, 154, 10

(ref: foreman2013emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: freudling2013automated) Freudling, W., Romaniello, M., Bramich, D., et al. 2013, A&A, 559, A96

(ref: gaia2018vizier) Gaia Collaboration. 2018, VizieR Online Data Catalog, I/345

(ref: gaia2020) Gaia Collaboration. 2020, VizieR Online Data Catalog, I/350

(ref: 1998A&A...330..375G) Greenberg, J. M. 1998, , 330, 375

(ref: griffin2010herschel) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3

(ref: hayashi_mmsn) Hayashi, C. 1981, Progress of Theoretical Physics Supplement, 70, 35

(ref: 2016yCat.2336....0H) Henden, A. A., Templeton, M., Terrell, D., et al. 2016

(ref: husser2013new) Husser, T.-O., Wende-von Berg, S., Dreizler, S., et al. 2013, A&A, 553, A6

(ref: jayasinghe2018asas) Jayasinghe, T., Kochanek, C., Stanek, K., et al. 2018, MNRAS, 477, 3145

(ref: kaiser2002pan) Kaiser, N., Aussel, H., Burke, B. E., et al. 2002, in Survey and Other Telescope Technologies and Discoveries, Vol. 4836, SPIE, 154–164

(ref: keppler2018discovery) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44

(ref: kohler2015dust) Köhler, M., Ysard, N., & Jones, A. P. 2015, Astronomy & Astrophysics, 579, A15

(ref: krijt2016tracing) Krijt, S., Ciesla, F. J., & Bergin, E. A. 2016, The Astrophysical Journal, 833, 285

(ref: kuffmeier2021) Kuffmeier, M., Dullemond, C. P., Reissl, S., & Goicovic, F. G. 2021, , 656, A161

(ref: kurosawa2011multidimensional) Kurosawa, R., Romanova, M. M., & Harries, T. J. 2011, MNRAS, 416, 2623

(ref: Lazareff) Lazareff, B., Berger, J. P., Kluska, J., et al. 2017, , 599, A85

(ref: leiendecker2022dust) Leiendecker, H., Jang-Condell, H., Turner, N. J., & Myers, A. D. 2022, ApJ, 941, 172

(ref: li2016lifetimes) Li, M. & Xiao, L. 2016, ApJ, 820, 36

(ref: 1974MNRAS.168..603L) Lynden-Bell, D. & Pringle, J. E. 1974, , 168, 603

(ref: martin2014thermal) Martı́n-Doménech, R., Caro, G. M., Bueno, J., & Goesmann, F. 2014, Astronomy & Astrophysics, 564, A8

(ref: 2013ApJ...773..168M) Mohanty, S., Greaves, J., Mortlock, D., et al. 2013, , 773, 168

(ref: montmerle1983einstein) Montmerle, T., Koch-Miramond, L., Falgarone, E., & Grindlay, J. E. 1983, ApJ, 269, 182

(ref: pyshellspec2018) Mourard, D., Brož, M., Nemravová, J. A., et al. 2018, A&A, 618, A112

(ref: mumma2011chemical) Mumma, M. J. & Charnley, S. B. 2011, Annual Review of Astronomy and Astrophysics, 49, 471

(ref: nealon2019) Nealon, R., Cuello, N., & Alexander, R. 2019, Monthly Notices of the Royal Astronomical Society, 491, 4108

(ref: nemravova2016xitauri) Nemravová, J., Harmanec, P., Brož, M., et al. 2016, A&A, 594, A55

(ref: Nesvorny_2018ARA&A..56..137N) Nesvorný, D. 2018, , 56, 137

(ref: neugebauer1984infrared) Neugebauer, G., Habing, H., Van Duinen, R., et al. 1984, ApJ, 278, L1

(ref: nixon2013) Nixon, C., King, A., & Price, D. 2013, Monthly Notices of the Royal Astronomical Society, 434, 1946

(ref: ochsenbein2000vizier) Ochsenbein, F., Bauer, P., & Marcout, J. 2000, A&A Supplement Series, 143, 23

(ref: page2012xmm) Page, M., Brindle, C., Talavera, A., et al. 2012, MNRAS, 426, 903

(ref: perotti2023water) Perotti, G., Christiaens, V., Henning, T., et al. 2023, Nat, 620, 516

(ref: pontoppidan2014volatiles) Pontoppidan, K. M., Salyk, C., Bergin, E. A., et al. 2014, Protostars and Planets VI, 363

(ref: ricci2010dust) Ricci, L., Testi, L., Natta, A., & Brooks, K. 2010a, A&A, 521, A66

(ref: ricci2010dust2) Ricci, L., Testi, L., Natta, A., et al. 2010b, A&A, 512, A15

(ref: rieke2004multiband) Rieke, G., Young, E., Engelbracht, C., et al. 2004, ApJ Supplement Series, 154, 25

(ref: 10.1093/mnras/stad3005) Rubin, M., Altwegg, K., Berthelier, J.-J., et al. 2023, MNRAS, 526, 4209

(ref: salyk2015detection) Salyk, C., Lacy, J. H., Richter, M. J., et al. 2015, ApJ Letters, 810, L24

(ref: skrutskie2006two) Skrutskie, M., Cutri, R., Stiening, R., et al. 2006, AJ, 131, 1163

(ref: takasao2018three) Takasao, S., Tomida, K., Iwasaki, K., & Suzuki, T. K. 2018, ApJ, 857, 4

(ref: 2010A&A...519A..83T) Takita, S., Kataza, H., Kitamura, Y., et al. 2010, , 519, A83

(ref: van2023transition) van der Marel, N. 2023, The European Physical Journal Plus, 138, 225

(ref: 2016A&A...585A..58V) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, , 585, A58

(ref: wright2010wide) Wright, E. L., Eisenhardt, P. R., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: york2000sloan) York, D. G., Adelman, J., Anderson Jr, J. E., et al. 2000, AJ, 120, 1579

(ref: ysard2018optical) Ysard, N., Jones, A., Demyk, K., Boutéraon, T., & Koehler, M. 2018, Astronomy & Astrophysics, 617, A124

(ref: zak2024) Zak, J., Bocchieri, A., Sedaghati, E., et al. 2024, A&A, 686, A147

(ref: Zhang_2013) Zhang, K., Pontoppidan, K. M., Salyk, C., & Blake, G. A. 2013, The Astrophysical Journal, 766, 82

(ref: zhou2021hubble) Zhou, Y., Bowler, B. P., Wagner, K. R., et al. 2021, AJ, 161, 244

# Additional figures

![](img/SDH.png)

![](img/delta_ring_corrected_units.png)

![](img/multiple_panels_2.png)

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[2]",
  "value": "Use Pyshellspec/Shellspec with a central STAR (interpolated PHOENIX spectrum), a spherical SHELL of hot gas, and an innermost DISC to fit VLT Halpha spectra and VLTI/GRAVITY visibilities, and derive the mass accretion rate.",
  "failed_quote": "From the density and velocity of the gas in the accretion envelope shell, we derive an accretion rate of: $\\dot{M} = (6.1\\pm 0.2)\\cdot10^{-8}\\,M_\\odot\\, {\\rm yr}^{-1}\\,,$"
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Scan parameters of outer DISC (40-60 au) to fit ALMA Band 7 visibilities and SED, add warm intermediate DISC (0.2-1 au) to fit mid-IR SED deficit, and integrate vertical and radial density profiles to obtain outer disc dust mass.",
  "failed_quote": "By integrating over the radial direction, we obtain the dust mass of $M_{\\rm dust} = \\int_{R_{\\rm in nb}} ^{R_{\\rm outnb}} 2 \\pi r \\Sigma_{\\rm dust}(r) {\\rm d} r= \\dots \\gtrsim 100 M_{\\rm Earth}\\,.$"
 }
]
```
