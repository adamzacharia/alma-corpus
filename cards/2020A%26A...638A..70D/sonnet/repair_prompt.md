# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...638A..70D\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The Massive and Distant Clusters of *WISE* Survey

The Massive and Distant Clusters of WISE Survey (MaDCoWS) provides a catalog of high-redshift ($0.7\lesssim z\lesssim 1.5$) infrared-selected galaxy clusters. However, the verification of the ionized intracluster medium, indicative of a collapsed and nearly virialized system, is made challenging by the high redshifts of the sample members. The main goal of this work is to test the capabilities of the Atacama Compact Array (ACA; also known as the Morita Array) Band 3 observations, centered at about 97.5 GHz, to provide robust validation of cluster detections via the thermal Sunyaev–Zeldovich (SZ) effect. Using a pilot sample that comprises ten MaDCoWS galaxy clusters, accessible to ACA and representative of the median sample richness, we infer the masses of the selected galaxy clusters and respective detection significance by means of a Bayesian analysis of the interferometric data. Our test of the *Verification with the ACA – Localization and Cluster Analysis* (VACA LoCA) program demonstrates that the ACA can robustly confirm the presence of the virialized intracluster medium in galaxy clusters previously identified in full-sky surveys. In particular, we obtain a significant detection of the SZ effect for seven out of the ten VACA LoCA clusters. We note that this result is independent of the assumed pressure profile. However, the limited angular dynamic range of the ACA in Band 3 alone, short observational integration times, and possible contamination from unresolved sources limit the detailed characterization of the cluster properties and the inference of the cluster masses within scales appropriate for the robust calibration of mass–richness scaling relations.

# Introduction

Galaxy cluster richness has long been demonstrated to provide an observationally inexpensive proxy for cluster mass (cite: Rykoff2012; Andreon2015; Saro2015; Geach2017; Rettura2018; Gonzalez2019). Being practically independent of the specific dynamical state of galaxy clusters, properly calibrated mass–richness relations play a key role in obtaining mass estimates in lieu of data that could directly probe the mass distribution of a cluster. For cluster candidates discovered through optical and infrared selection criteria such as richness, it is essential to verify that the observed galaxy overdensities cannot be ascribed to spurious effects (e.g., line-of-sight projection of galaxies belonging to different haloes). Central to this aim is confirming the presence of a hot X-ray emitting intracluster medium (ICM) heated by gravitational infall and nearly in virial equilibrium. X-ray confirmation, which has been the traditional tool for probing the ICM, becomes exceedingly difficult and observationally challenging at high redshift due to cosmological dimming. We note, however, that at $z\gtrsim1$ the dimming is expected to weaken due to evolution in the X-ray luminosity for a given mass (cite: Churazov2015).

The thermal Sunyaev–Zeldovich (SZ) effect (cite: Sunyaev1972) offers an alternative, redshift-independent way to confirm the presence of the ICM. Here we provide a first test of the capabilities of the 7-meter Atacama Compact Array (cite: Iguchi2009), or Morita Array, in providing an SZ confirmation of cluster candidates identified in wide-field surveys. In particular, we consider a first pilot sample of the observational program, *Verification with the ACA – Localization and Cluster Analysis* (VACA LoCA), aimed at providing cluster verification and localization of the intracluster gas of galaxy clusters selected from the Massive and Distant Clusters of WISE (cite: Wright2010) Survey (cite: Gonzalez2019).

The paper is structured as follows. An overview of the observational details of the VACA LoCA cluster sample is provided in Sect. [2](#sec:data:aca). In Sect. [3](#sec:analysis) we briefly discuss the modeling technique employed for inferring the cluster masses. The results of our analysis, comprising estimates of mass and detection significance for all the VACA LoCA clusters, are presented in Sect. [4](#sec:res). A summary of the work is then given in Sect. [5](#sec:conclusion).

All results discussed in this paper were derived in the framework of a spatially flat $\Lambda$CDM cosmological model, with $\Omega_{\mathrm{m}}=0.30$, $\Omega_{\Lambda}=0.70$, and $H_0=70.0~\mathrm{km\,s^{-1}\,Mpc^{-1}}$. In this cosmology, 1 arcsecond corresponds to $8.01~\mathrm{kpc}$ at the average redshift $z\simeq1$ of the VACA LoCA clusters. The best-fit estimates and uncertainties of any of the model parameters correspond respectively to the $50{\mathrm{th}}$ percentile and 68% credibility interval of the corresponding marginalized posterior probability distributions.

# ACA observations

(cite: Gonzalez2019) reports a preliminary, low-scatter mass–richness scaling relation for the MaDCoWS cluster sample based on the infrared richness estimates from observations with the Infrared Array Camera (cite: Fazio2004) on the *Spitzer Space Telescope* and masses derived from the SZ signal measured by the Combined Array for Research in Millimeter-wave Astronomy[^1] (CARMA; see (cite: Brodwin2015; Gonzalez2015; Decker2019)). In order to improve the calibration of the mass–richness correlation, the VACA LoCA observations were devised to target a sample of ten MaDCoWS galaxy clusters observable by ACA and representative of the median sample richness.

The ACA observations of the selected MaDCoWS clusters were carried out between May and October 2017 as part of ALMA Cycle 4 operations (project ID: 2016.2.00014.S, PI: M. Brodwin). In order to reach a target continuum sensitivity of around $80~\mathrm{\mu Jy}$, the integration time on source for each of the pointings amounts to an average of $2.6~\mathrm{hours}$.

The overall frequency band was tuned to cover the range $89.5-105.5~\mathrm{GHz}$, using four Band 3 spectral windows in continuum mode with centers at approximately $90.5$, $92.5$, $102.5$, and $104.5~\mathrm{GHz}$. This provided a good trade-off between probing the SZ signal spectrum near its minimum (i.e., maximum amplitude of the negative spectral distortion) and probing the largest scales accessible by ACA Band 3 data. The resulting dynamic range of $uv$ (Fourier space) distances in the ACA observations of the MaDCoWS clusters span, on average, between $2.64$ and $17.23~\mathrm{k\lambda}$, corresponding respectively to angular scales from $1.30~\mathrm{arcmin}$ to $11.97~\mathrm{arcsec}$ (we refer to Table [\[tab:obsdata\]](#tab:obsdata) for further observational details).

We perform the calibration of all the data in the Common Astronomy Software Application (cite: McMullin2007) package version 4.7.2 using the standard calibration pipelines provided at data delivery. A direct inspection of the reduced data sets did not highlight any significant issue with the calibration. We hence adopt the nominal value of $5\%$ for the fiducial uncertainty on the ACA absolute calibration[^2].

All the interferometric images presented in this work are generated using the `tclean` task in `CASA` version 5.6.1. To better highlight the SZ features in the maps, we do not correct for the primary beam attenuation. The fields are cut off at the standard 0.2 gain level of the ACA antenna pattern. As our study is entirely performed on the raw interferometric data, we note that the ACA maps are included for display purposes only. No deconvolution is performed to reduce the effects of sidelobes on the reconstructed “dirty” maps.

![](figures/figure01.pdf)

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Cluster ID | Obs. date | On-source time | Noise RMS | $uv$ range | Resolution | MRS |
|  |  | (hours) | (mJy) | ($\mathrm{k\lambda}$) | (arcsec) | (arcmin) |
|  | 2017-08-27 | $2.78$ | $0.061$ | $1.70-17.20$ | $17.8\times 12.4$ | $2.02$ |
|  | 2017-09-03 | $3.15$ | $0.055$ | $1.91-17.03$ | $18.2\times 10.6$ | $1.80$ |
|  | 2017-07-27 | $3.05$ | $0.087$ | $1.75-14.69$ | $17.2\times 11.4$ | $1.96$ |
|  | 2017-05-09 | $2.08$ | $0.069$ | $2.13-16.51$ | $19.4\times  9.5$ | $1.61$ |
|  | 2017-09-07 | $2.14$ | $0.081$ | $2.52-17.22$ | $19.9\times  9.6$ | $1.36$ |
|  | 2017-05-08 | $3.07$ | $0.061$ | $2.09-13.67$ | $16.7\times 13.2$ | $1.64$ |
|  | 2017-08-18 | $2.46$ | $0.071$ | $1.74-17.19$ | $17.9\times  9.9$ | $1.98$ |
|  | 2017-09-03 | $3.09$ | $0.066$ | $1.73-16.30$ | $17.0\times  9.6$ | $1.99$ |
|  | 2017-08-03 | $1.37$ | $0.101$ | $1.87-16.41$ | $19.3\times 10.9$ | $1.84$ |
|  | 2017-08-19 | $2.61$ | $0.062$ | $1.54-14.98$ | $18.5\times  9.6$ | $2.23$ |
|  |  |  |  |  |  |  |

# Analysis technique

Spatial filtering due to the incomplete sampling of the Fourier modes of the observed sky may represent a severe challenge in the analysis of radio-interferometric measurements of galaxy clusters. The issue is in fact twofold: first, the sparse coverage of the Fourier plane results in poor constraints for some angular scales within the range probed by the interferometer; second, the shortest baseline achievable is essentially determined by the shadowing limit, when one antenna is in front of another as seen from the source. This sets a hard upper limit on the maximum recoverable scale (MRS) of the observation. This high-pass filtering effect is evident in the case of astrophysical objects covering large angular scales such as galaxy clusters, whose SZ signal often extends well beyond the field of view of current millimeter and submillimeter facilities that provide subarcminute resolution (see, e.g., (cite: Basu2016) and (cite: DiMascolo2019b), or (cite: Mroczkowski2019) for a broader review). To provide a sense of the net effects of ACA filtering on the SZ signal from a galaxy cluster, in Fig. [2](#fig:filtered) we compare the model and filtered SZ profiles for a cluster with a mass of $2.5\cdot10^{14}~\mathrm{M_{\odot}}$ at a redshift $z=1.00$.

![](figures/figure02.pdf)

While the missing flux issue is commonly solved by means of deconvolution techniques (at the expense of introducing correlation in the image-space noise), it is possible to include short spacings only by complementing the interferometric data with external information on larger scales (e.g., from single-dish telescopes). However, these large-scale observations should have sensitivities comparable to the corresponding interferometric measurements, a condition that is difficult to realize in the case of SZ data.

In order to circumvent any of the above challenges, we perform a Bayesian forward-modeling analysis directly on the visibilities of the ACA MaDCoWS sample. This allows us to infer the cluster masses from the raw interferometric data, accounting for the exact sampling function of the visibility plane, and providing a strong leverage on possible contamination from unresolved (point-like) sources.

An extensive discussion of the modeling methodology and the implementation is provided in (cite: DiMascolo2019a; DiMascolo2019b).

## Estimating cluster masses

Hydrodynamic simulations (cite: Nagai2007) have shown that the pressure distribution of the electrons within the ICM can be reasonably described as $$\begin{equation}
  P_{\mathrm{e}}(\xi) = P_{500}\times p(\xi),
  \label{eq:a10}
\end{equation}$$ where the scaled pressure profile $p(\xi)$ is defined by a generalized Navarro-Frenk-White (gNFW) profile, $$\begin{equation}
  p(\xi) = P_{0}~\xi^{-c}\left[\left(1+\xi^a\right)\right]^{(c-b)/a}.
  \label{eq:gnfw}
\end{equation}$$ Here, $P_{0}$ acts as a simple normalization factor. The parameters $a$, $b$, and $c$ are respectively the radial slopes at intermediate, large, and small scales with respect to a scale radius $r_{s}$, while $\xi=r/r_{\mathrm{s}}$ is the radial distance $r$ from the pressure centroid in units of $r_{s}$.

Following (cite: Arnaud2010), the scaling parameter $P_{500}$ is defined as $$\begin{equation}
  P_{500}(M_{500},z) = 1.65\cdot10^{-3} \, E(z)^{8/3} \, \left[\frac{M_{500}}{3\cdot10^{14}M_{\odot}}\right]^{2/3+a_{\textsc{p}}(\xi)}\mathrm{keV~cm^{-3}}
  \label{eq:p500}
,
\end{equation}$$ where $E(z)$ is the ratio of the Hubble constant at redshift $z$ to its present value $H_{0}$, and $M_{500}$ is the mass enclosed within the radius $r_{500}$ at which the average cluster density is $500\times$ the critical density $\rho_{\mathrm{c}}(z)$ of the Universe at the redshift of the cluster. Under the assumption of spherical symmetry, the radius $r_{500}$ can be easily expressed as a function of a given mass $M_{500}$ and redshift $z$ as $$\begin{equation}
  r_{500}(M_{500},z) = \left[\frac{3}{4\pi}\frac{M_{500}}{500\rho_{\mathrm{c}}(z)}\right]^{1/3}.
  \label{eq:r500}
\end{equation}$$ This can then be related to the scale radius $r_{\mathrm{s}}$ of the normalized gNFW profile in Eq. [\[eq:gnfw\]](#eq:gnfw) by adding a concentration parameter $c_{500}$ as $r_{\mathrm{s}} = r_{500}/c_{500}$. Finally, the running slope $a_{\textsc{p}}(\xi)$ is introduced to account for any departure from self-similarity in the innermost regions of galaxy clusters, $$\begin{equation}
  a_{\textsc{p}}(\xi) = a_{0}/[1+8\xi^3]
  \label{eq:ap}
\end{equation}$$

In our analysis, the self-similarity deviation parameter $a_{0}$, the pressure normalization $P_{0}$, the concentration parameter $c_{500}$, and the gNFW slopes $a$, $b$, and $c$ are kept fixed. The parameters $a_{0}$, $P_{0}$, and $c_{500}$ are degenerate with the mass parameter $M_{500}$, and unconstrained fittings would significantly affect the recovery of the cluster masses. On the other hand, test fittings with free gNFW slopes have shown that all three parameters $a$, $b$, and $c$ would remain entirely unconstrained, and would undergo strong degeneracies with any of the other gNFW parameters and mass $M_{500}$. This is a direct consequence of the limited dynamic range of angular scales probed by ACA which, in combination with the modest sensitivity of the VACA LoCA observations, limits the information available for reconstructing pressure profiles for the individual fields.

Hence, we set the above gNFW parameters alternatively to the best-fit values reported in (cite: Arnaud2010) for the universal pressure profile, or for the subsamples of cool-core and morphologically disturbed clusters. For a comparison, we additionally consider gNFW parameters derived in (cite: Planck2013V) from the joint fit of the *XMM-Newton*- and *Planck*-selected sample of galaxy clusters, as well as the high-redshift *Chandra* gNFW model by (cite: McDonald2014). The different set of parameters adopted in our analysis is summarized in Table [1](#tab:gnfw).

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
|  | universal | cool core | disturbed | *Planck* | MD14 |
| $P_{0}$ | $8.40$ | $3.25$ | $3.20$ | $6.41$ | $3.47\substack{+1.09\\-0.67}$ |
| $c_{500}$ | $1.18$ | $1.13$ | $1.08$ | $1.81$ | $2.59\substack{+0.37\\-0.38}$ |
| $a$ | $1.05$ | $1.22$ | $1.41$ | $1.33$ | $2.27\substack{+0.89\\-0.40}$ |
| $b$ | $5.49$ | $5.49$ | $5.49$ | $4.13$ | $3.48\substack{+0.60\\-0.39}$ |
| $c$ | $0.31$ | $0.77$ | $0.38$ | $0.31$ | $0.15\substack{+0.13\\-0.15}$ |
| $a_{0}$ | $0.22$ | $0.22$ | $0.22$ | $0.00$ | $0.22$ |
|  |  |  |  |  |  |

: Best-fit parameters of the gNFW pressure models from (cite: Arnaud2010), (cite: Planck2013V), and (cite: McDonald2014).

At each iteration of the posterior sampling, we then compute the expected thermal SZ signal by integrating the pressure model defined in Eq. [\[eq:a10\]](#eq:a10) for a given value of $M_{500}$ and redshift $z$. The resulting variation in the CMB surface brightness in a direction $\bm{x}$ on the plane of the sky and at a frequency $\nu$ is (cite: Sunyaev1972) $$\begin{equation}
  \delta i_{\mathrm{t\textsc{sz}}}(\bm{x},\nu) \propto g_{\mathrm{t\textsc{sz}}}(\nu) \, {\textstyle\int} P_{\mathrm{e}}(\bm{x},\ell)\,\mathrm{d}\ell.
  \label{eq:tsz}
\end{equation}$$ The integral along the line-of-sight coordinate $\ell$ is computed from $0$ up to the fiducial value of $5 r_{500}$ (cite: Arnaud2010). The factor $g_{\mathrm{t\textsc{sz}}}(\nu,T_{\mathrm{e}})$ represents the frequency scaling of the non-relativistic thermal SZ effect (cite: Sunyaev1972). For simplicity, we neglect any temperature-dependent corrections arising from the fully relativistic treatment of the thermal SZ effect. The ACA observations cover a frequency band that is not broad enough, or deep enough, to constrain any relativistic contribution to the SZ spectrum, and hence to get direct constraints on the average temperature of the electron populations within the observed clusters (cite: Challinor1998; Itoh1998; Sazonov1998). Further, the correction to the non-relativistic thermal signal for the ACA MaDCoWS clusters is expected[^3] to be on average less than $\sim5\%$. Although this will bias the reconstructed masses systematically to lower values, the effect will be at most on the same order as the flux uncertainties discussed in Sect. [2](#sec:data:aca), and well within the modeling statistical uncertainties (see Sect. [4](#sec:res) below).

Similarly, the ACA frequency coverage is not wide enough to retrieve any information about the bulk velocities of the observed clusters (or parts of them). Therefore, we assume any contributions from a possible kinetic SZ component (cite: Sunyaev1980) to be subdominant with respect to the thermal effect, and we neglect it in our analysis.

## Unresolved sources

Contamination from point-like radio sources may limit and significantly affect the reconstruction of a cluster model from SZ observations (cite: Gobat2019; Mroczkowski2019). In order to assess the level at which the unresolved flux might have contributed to the estimates of the masses of VACA LoCA clusters, we perform blind searches of point-like components over the entire fields of view of the ACA observations and simultaneously with the SZ analysis. We assume the unresolved components to be described by a Dirac-$\delta$ model with flat spectrum over the entire ACA band. The long-baseline data range, most sensitive to the signal from compact sources, is the least densely parsed region of the visibility plane (see Fig. [1](#fig:uvdata)). This results in high noise on the smaller angular scales, hence limiting the possibility of constraining the spectral properties of the unresolved sources in the observed fields. The point-like model thus simplifies to (cite: DiMascolo2019a) $$\begin{equation}
    V(\bm{u},\nu) = i_{\textsc{ps}}e^{2\pi j\bm{u}\cdot\bm{x}_{\textsc{ps}}},
  \label{eq:pts}
\end{equation}$$ given a set of interferometric data with visibility coordinates $\bm{u}$. The position $\bm{x}_{\textsc{ps}}$ and the source flux $i_{\textsc{ps}}$ are left free to vary.

Due to the limited information provided by the ACA data about the population of unresolved sources in the VACA LoCA fields, here we consider them as nuisance model components and generally marginalize over them. A future analysis with higher resolution, multi-frequency observations will be key for their proper characterization.

## Parameter priors

The comparison of cluster positions identified through the MaDCoWS search and the galaxy distribution centroids measured by *Spitzer* are found to deviate by $\sigma_{\mathrm{RA}}=14.3~\mathrm{arcsec}$ in right ascension and $\sigma_{\mathrm{Dec}}=15~\mathrm{arcsec}$ in declination (cite: Gonzalez2019). We thus assume normal priors with standard deviations of $\sigma_{\mathrm{ra}}$ and $\sigma_{\mathrm{Dec}}$ on the right ascension and declination coordinates of the cluster centroids, respectively.

The mass parameter $M_{500}$ and the redshift $z$ are heavily degenerate as they both enter in the determination of the pressure model through the pressure normalization $P_{500}$ and the scale radius $r_{500}$. In order to alleviate the degeneracy, we adopt split-normal priors (cite: Wallis2014) on the redshifts $z$ based on the photometric constraints on the cluster members from *Spitzer* (cite: Gonzalez2019). When fitting the gNFW profile from (cite: McDonald2014), the gNFW parameters were also assigned split-normal priors, with standard deviations given by the respective parameter uncertainties in Table [1](#tab:gnfw).

To account for the ACA flux uncertainties in the recovered masses (Sect. [2](#sec:data:aca)), we introduce a normalization hyperparameter, as detailed in (cite: DiMascolo2019a). In particular, we consider a scaling parameter characterized by a normal prior distribution with unitary mean value and standard deviation equal to the inherent calibration uncertainty.

Finally, we assume wide uninformative priors on all the point source parameters apart from the position. For the blind search, this is bound to vary uniformly within the region defined by the first null of the ACA primary beam. Data-free runs for each of the analyzed data sets (cite: DiMascolo2019a; DiMascolo2019b) have shown no biases in the parameter inference related to choice in the prior distributions.

# Results and discussion

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Cluster ID | $z_{\mathrm{phot}}$ | $\lambda$ | $r_{500}$ | $\theta_{500}$ | $Y_{\mathrm{sph}}(<r_{500})$ | $Y_{\mathrm{cyl}}(<r_{500})$ | $M_{500}$ | $\sigma_{\mathrm{eff}}$ |
|  | – | – | (Mpc) | (arcmin) | $10^{-5}~\mathrm{Mpc^2}$ | $10^{-5}~\mathrm{Mpc^2}$ | $(10^{14}~M_{\odot})$ | – |
|  |  |  |  |  |  |  |  |  |
|  | $1.05\substack{+0.04\\-0.05}$ | $49\pm7$ | $0.67\substack{+0.09\\-0.08}$ | $1.38\substack{+0.03\\-0.21}$ | $2.13\substack{+0.01\\-0.66}$ | $2.34\substack{+0.01\\-0.72}$ | $2.57\substack{+0.30\\-0.30}$ | $7.77$ |
|  | $1.08\substack{+0.03\\-0.04}$ | $53\pm7$ | $0.57\substack{+0.02\\-0.03}$ | $1.17\substack{+0.05\\-0.07}$ | $1.04\substack{+0.25\\-0.26}$ | $1.15\substack{+0.27\\-0.29}$ | $1.78\substack{+0.20\\-0.29}$ | $5.32$ |
| $^{a}$ | $1.10\substack{+0.05\\-0.05}$ | $58\pm7$ | $0.55\substack{+0.04\\-0.05}$ | $1.11\substack{+0.08\\-0.08}$ | $0.97\substack{+0.40\\-0.33}$ | $1.07\substack{+0.44\\-0.37}$ | $1.66\substack{+0.31\\-0.38}$ | $4.26$ |
|  |  |  | $0.58\substack{+0.04\\-0.04}$ | $1.19\substack{+0.08\\-0.09}$ | $1.48\substack{+0.54\\-0.49}$ | $1.63\substack{+0.59\\-0.53}$ | $2.13\substack{+0.40\\-0.49}$ |  |
|  | $1.31\substack{+0.03\\-0.05}$ | $53\pm7$ | $0.56\substack{+0.02\\-0.03}$ | $1.10\substack{+0.05\\-0.05}$ | $1.51\substack{+0.38\\-0.25}$ | $1.66\substack{+0.41\\-0.27}$ | $2.24\substack{+0.36\\-0.52}$ | $3.81$ |
|  | $1.08\substack{+0.04\\-0.05}$ | $41\pm6$ | $0.59\substack{+0.03\\-0.03}$ | $1.20\substack{+0.08\\-0.07}$ | $1.22\substack{+0.39\\-0.29}$ | $1.34\substack{+0.42\\-0.32}$ | $1.95\substack{+0.31\\-0.31}$ | $4.53$ |
|  | $1.02\substack{+0.07\\-0.06}$ | $41\pm7$ | $0.67\substack{+0.04\\-0.04}$ | $1.40\substack{+0.09\\-0.08}$ | $2.29\substack{+0.50\\-0.43}$ | $2.52\substack{+0.55\\-0.48}$ | $2.75\substack{+0.32\\-0.32}$ | $6.99$ |
| $^{a}$ | $1.16\substack{+0.05\\-0.05}$ | $50\pm7$ | $0.57\substack{+0.05\\-0.05}$ | $0.94\substack{+0.11\\-0.05}$ | $1.19\substack{+0.45\\-0.40}$ | $1.32\substack{+0.49\\-0.44}$ | $1.86\substack{+0.34\\-0.52}$ | $5.35$ |
|  |  |  | $0.55\substack{+0.05\\-0.05}$ | $1.09\substack{+0.06\\-0.05}$ | $1.43\substack{+0.64\\-0.56}$ | $1.58\substack{+0.71\\-0.62}$ | $2.04\substack{+0.42\\-0.56}$ |  |
|  |  |  |  |  |  |  |  |  |
|  | $1.26\substack{+0.05\\-0.08}$ | $29\pm5$ | $0.30^{+0.05}$ | $0.59^{+0.10}$ | $0.04^{+0.06}$ | $0.05^{+0.07}$ | $0.30^{+0.18}$ | – |
| $^{b}$ | $1.09\substack{+0.04\\-0.04}$ | $51\pm7$ | $0.49\substack{+0.04\\-0.07}$ | $0.99\substack{+0.09\\-0.14}$ | $0.49\substack{+0.18\\-0.29}$ | $0.54\substack{+0.19\\-0.32}$ | $1.17\substack{+0.27\\-0.38}$ | $2.40$ |
|  | $1.01\substack{+0.06\\-0.07}$ | $38\pm6$ | $0.59\substack{+0.05\\-0.04}$ | $1.22\substack{+0.08\\-0.12}$ | $1.01\substack{+0.40\\-0.43}$ | $1.11\substack{+0.44\\-0.48}$ | $1.82\substack{+0.34\\-0.42}$ | $1.26$ |
|  |  |  |  |  |  |  |  |  |

Table notes:

A summary of the masses of the VACA LoCA pilot sample is presented in Table [\[tab:masses\]](#tab:masses). The results presented in previous MaDCoWS papers (cite: Brodwin2015; Decker2019; Gonzalez2019) were derived adopting the universal profile by (cite: Arnaud2010) to describe the electron pressure distribution. For consistency, we report here only the masses estimated under the same assumption. A discussion of the impact of model choice on the inferred masses is presented in Sect. [4.4](#sec:res:mass).

We quantify the detection significance of the SZ signal in the VACA LoCA observations by comparing the log-evidence of the full modeling runs $\mathcal{Z}_1$ with those considering only the point source model component $\mathcal{Z}_0$ by means of the Jeffreys scale[^4] (cite: Jeffreys1961). To get a more immediate handle on the significance of each detection, we report in Table [\[tab:masses\]](#tab:masses) the number of effective standard deviations $\sigma_{\mathrm{eff}}$ between the model with and without an SZ component. This can be computed as $\sigma_{\mathrm{eff}}\simeq\sqrt{2\Delta\log{\mathcal{Z}}}$ given a log-Bayes factor $\Delta\log{\mathcal{Z}}=\log{(\mathcal{Z}_1/\mathcal{Z}_0)}$ (cite: Trotta2008). This differs from the approach taken in the CARMA SZ follow-up papers (cite: Brodwin2015; Gonzalez2015; Decker2019) in that it is more statistically robust, as it properly accounts for the change between different models in the number of parameters and respective priors. We note that $\sigma_{\mathrm{eff}}$ is to be interpreted in a merely heuristic manner, as we are not accounting for the different degrees of freedom or prior volumes between the models. According to the Jeffreys criterion, introduced above, a value of $\sigma_{\mathrm{eff}}\gtrsim3$ is indicative of a robust detection.

Overall, we significantly detect the SZ effect toward seven out of the ten clusters of the VACA LoCA sample, while the presence of SZ signal is only weakly favored for and . Conservatively, we consider these two clusters as being undetected. Nevertheless, it is worth noting that, according to the Jeffreys criterion, the detection significance of provides moderately significant statistical support for the presence of SZ signal (cite: Jeffreys1961; Trotta2008). For the single case of , the analysis favors the model without the SZ component, thus resulting in a clear non-detection. Reported in Table [\[tab:masses\]](#tab:masses) is the estimated upper limit for the cluster mass.

![](figures/figure03.pdf)

As for the analyses presented in (cite: Brodwin2015), (cite: Gonzalez2015), and (cite: Decker2019) of the CARMA data, the fitting of the ACA data is performed entirely in $uv$-space. Along with the advantages discussed in Sect. [3](#sec:analysis), this provides an approach to cluster detection in interferometric SZ data that avoids the drawbacks of image-space analysis, in particular the biased reconstructions produced by the `CLEAN` algorithm. For a comparison, we show in Fig. [3](#fig:imdirt:mooj0129) the dirty image of the most significant detection in our sample, . The peak of the SZ decrement has an amplitude of $-0.24~\mathrm{mJy~beam^{-1}}$, corresponding to a statistical significance of $4.06\sigma$, which is lower than the cluster detection $\sigma_{\mathrm{eff}}=7.77$ (Table [\[tab:masses\]](#tab:masses)). This is not surprising, as $\sigma_{\mathrm{eff}}$ is a measure of the significance of the total SZ signal. However, in addition to the resolved SZ signal, the reason for this discrepancy also resides in the fact that the interferometric images are affected by heavily correlated noise. As a consequence, the resulting fluctuations may attenuate the measured signal and limit the confidence of its detection. On the other hand, side lobes further contaminate interferometric images. This is generally solved by applying `CLEAN`-like deconvolution techniques to the data (cite: Hoegbom1974; Thompson1986). However, these techniques are specifically devised to reduce the effects of the incomplete sampling of the visibility plane on the overall quality of the reconstructed image, and would not provide any serious improvement in the significance of the observed SZ signal. It is worth noting that any deconvolved image would still provide a heavily high-pass filtered view of the very core of a galaxy cluster, as ACA does not measure the SZ signal on scales larger than the maximum recovered scale (Table [\[tab:obsdata\]](#tab:obsdata)).

Another important remark is that the dirty map shown in Fig. [3](#fig:imdirt:mooj0129) is generated only after subtraction from the visibility data of the most significant point-like sources detected by our modeling algorithm, allowing for a cleaner identification of the SZ signal in the cluster image. In fact, the presence of very bright compact sources may completely hide any SZ effect component, as either their signal would be superimposed on the one from the galaxy cluster or the side lobes would be blended with the SZ feature.

## Mass–richness relation

![](figures/figure04.pdf)

Figure [4](#fig:massrich) shows a comparison of the mass–richness scaling for the VACA LoCA sample and the CARMA measurements previously reported by (cite: Gonzalez2019). Although there is good consistency between our estimates and the MaDCoWS mass–richness scaling, the VACA LoCA mass–richness distribution is systematically below the expected correlation. We quantify the average scaling by fitting the VACA LoCA data points with a linear function, with the slope constrained to that of the mass–richness scaling in (cite: Gonzalez2019) but with a free normalization parameter (which translates to an offset in the logarithmic relation). We find that the VACA LoCA cluster masses are downscaled by a factor of $0.56\substack{+0.13\\-0.05}$ with respect to the CARMA-derived mass–richness scaling when considering all the VACA LoCA clusters. The resulting scatter of the ACA masses with respect to the reconstructed relation is $\sigma
  \vcenter{
    \Let@ \restore@math@cr \default@tag
    \baselineskip\fontdimen 10 \scriptfont\tw@
    \advance\baselineskip\fontdimen 12 \scriptfont\tw@
    \lineskip\thr@@\fontdimen 8 \scriptfont\thr@@
    \lineskiplimit\lineskip
    \ialign{\hfil$\m@th\scriptstyle##$&$\m@th\scriptstyle{}##$\hfil\crcr
      &\,\textsc{aca}\\&\log{M}|\lambda\crcr
    }
  }
=0.25\substack{+0.06\\-0.02}$, broader than the scatter observed in the CARMA measurements. However, if we exclude all the non-detections from the analysis, the scatter decreases to a value comparable with the CARMA measurement, $\sigma
  \vcenter{
    \Let@ \restore@math@cr \default@tag
    \baselineskip\fontdimen 10 \scriptfont\tw@
    \advance\baselineskip\fontdimen 12 \scriptfont\tw@
    \lineskip\thr@@\fontdimen 8 \scriptfont\thr@@
    \lineskiplimit\lineskip
    \ialign{\hfil$\m@th\scriptstyle##$&$\m@th\scriptstyle{}##$\hfil\crcr
      &\,\textsc{aca}\\&\log{M}|\lambda\crcr
    }
  }
=0.14\substack{+0.02\\-0.01}$, while the relative normalization remains statistically consistent with the previous estimate ($0.61\substack{+0.15\\-0.06}$). This suggests that the non-detections are major actors in the increase of the measured scatter, possibly representing outliers from the mass–richness relation (either due to properties inherent to the clusters themselves or as a result of modeling issues). The observed deviation from the nominal mass–richness relation may imply an overall systematic in the cluster mass estimates. On the other hand, a joint fit of the CARMA and VACA LoCA samples provides an overall scatter of $\sigma
  \vcenter{
    \Let@ \restore@math@cr \default@tag
    \baselineskip\fontdimen 10 \scriptfont\tw@
    \advance\baselineskip\fontdimen 12 \scriptfont\tw@
    \lineskip\thr@@\fontdimen 8 \scriptfont\thr@@
    \lineskiplimit\lineskip
    \ialign{\hfil$\m@th\scriptstyle##$&$\m@th\scriptstyle{}##$\hfil\crcr
      &\,\textsc{joint}\\&\log{M}|\lambda\crcr
    }
  }
=0.16\substack{+0.04\\-0.02}$. It may thus be possible that a scatter intrinsic to the mass–richness distribution or arising due to the limited size of studied sample may dominate the calibration of the mass–richness relation. Further observations of the SZ footprint of galaxy clusters spanning a broader richness range will be key to improving the current constraints on the MaDCoWS mass–richness scaling relation.

![](figures/figure05.pdf)

The fact that ACA can only provide a high-pass filtered view of the SZ signal (coupled with possible deviations from the fiducial average pressure profile; see discussion below) may be among the main causes of the slight discrepancy of the VACA LoCA masses with respect to the scaling relation obtained using SZ measurements from CARMA. In fact, CARMA probed the SZ signal out to scales larger the $r_{500}$ values of the observed clusters, hence accessing spatial information crucial to mass determination within a cosmologically relevant overdensity. In contrast, though the ACA observations have improved sensitivity on subarcminute scales, the reconstructed masses are derived by extrapolating the assumed pressure profile from the very core regions of the clusters. In order to assess whether filtering effects play a major role in biasing the cluster masses low, we re-run the modeling by forcing the model mass $M_{500}$ to be equal to the value expected from the mass–richness relation by (cite: Gonzalez2019), and fit for the normalization $P_0$ by assuming a wide uninformative prior. Once again, to be consistent with previous studies, we only consider the universal profile case. If the mass–richness relation provides an unbiased estimate of the cluster masses for the measured richnesses, we should then expect the respective SZ model to describe the ACA $uv$ data well, and the inferred estimates of $P_0$ to be consistent with the nominal value in Table [1](#tab:gnfw). To facilitate interpretation, we limit the analysis here to the clusters with a single SZ feature with a strong significance. As shown in Fig. [5](#fig:pnorm), the results are in qualitative agreement with the overall low-mass trend observed in the mass–richness distribution of the VACA LoCA sample cluster. Nevertheless, it is not possible to highlight any evident systematic effect common to all the data points. We thus conclude that the interferometric filtering is unlikely to play a major role in biasing our mass reconstruction to lower masses.

This of course presumes that the universal pressure model by (cite: Arnaud2010) can successfully describe the electron pressure distribution of such systems. However, departures from self-similarity, for example due to an actual evolution of the average pressure profile with the cluster redshift (cite: McDonald2014) or the disturbed state of any of the studied clusters, may significantly affect the mass reconstruction (cite: Ruppin2019b).

## Multiple SZ features

![image](figures/figure06a.pdf)\
![image](figures/figure06b.pdf)

The marginalized posterior distribution for the centroids of the galaxy clusters and manifest a clear bimodal behavior (top and bottom panels of Fig. [6](#fig:bimodal), respectively). We checked that they are dependent neither on the assumed prior on the position of the cluster centroid nor on the inclusion of point-like model components.

It may be possible that the individual posterior modes are actually related to distinct SZ components. These may arise, for example, due to the presence of a cluster pair in an early to mid merging phase (the situation is similar, in terms of cluster masses and of separation, to the merging system 1E 2216.0-0401/1E 2215.7-0404; (cite: Akamatsu2016)). In such cases, however, the electron pressure distribution will deviate significantly from the average gNFW models adopted in our analysis (cite: Wik2008; Sembolini2014; Yu2015; Ruppin2019c). In particular, we expect the resulting pressure distribution to be shallower than for the case of a relaxed cluster, hence resulting in an SZ signal more affected by the interferometric short-spacing filtering (see discussion in Sect. [3](#sec:analysis)). Similarly, non-thermal effects may play a central role in providing pressure support to the system (cite: Battaglia2012; Shi2015; Biffi2016; Ansarifard2020). As a consequence, we might expect the reconstructed masses to be greatly biased toward values lower than the true ones.

On the other hand, the elongation observed in the marginalized posterior probability for the cluster centroid may be a consequence of the combined effect of an elliptical geometry of the core region of the ICM and residual contributions from unresolved sources (see discussion in Sect. [4.3](#sec:res:pts) below). In any case, the non-regular electron pressure distribution would indicate that the clusters may be highly disturbed, again inducing a potential bias in the reconstructed masses.

![image](figures/figureA3_MOO_J0917-0700.pdf)\
![image](figures/figureA3_MOO_J2146-0320.pdf)

Additional hints about the potential presence of merger activity in the two clusters come from the analysis of the distribution of their member galaxies. In Figure [7](#fig:irac), we show *Spitzer*/IRAC color-selected galaxy overdensities (a description of the specific color-selection strategy employed here can be found in (cite: Gonzalez2019), and is based on the works by (cite: Wylezalek2013; Wylezalek2014)). For both clusters a significant elongation is observed in the galaxy density distribution. In the specific case of , the eastern component, the broader and more massive of the two SZ features, sits on the most prominent peak of the galaxy distribution, while the second SZ feature is significantly displaced with respect to the main galaxy overdensity structure. This may be related to the case in which a subcluster (in this case, the western one) has undergone an off-axis collision at a large impact parameter with the main cluster (the eastern SZ component). The two mass components should then be interpreted as highlighting a disturbed and elongated cluster morphology, rather than the presence of separate subclusters. On the other hand, the agreement in both the orientation and position of the SZ model and galaxy overdensity in supports the original hypothesis of an early to mid-stage, almost edge-on merger, in which the subclusters are still able to partially retain the respective intracluster gas in their potential well.

Unfortunately, the low spatial resolution of the available ACA data does not allow for a proper characterization of the dynamical state of the two systems, and the above arguments can only provide a speculative scenario that may explain the inferred SZ morphology. Additional observations will thus be necessary to shed a definitive light on cluster structures and to help understand whether the multiple SZ features belong to separate physical components.

## Unresolved sources

As already briefly mentioned in the previous section, a possible systematic effect that may prevent the proper estimation of the cluster masses from the modeling of ACA data is any residual contamination from emissions that have not been accounted for. Along with radio synchrotron sources, we expect dusty galaxies to contribute to the overall confusion noise (cite: DiMascolo2019a). However, although we were able to locate and constrain a number of unresolved components, the lack of high-resolution data (e.g., from the main 12-meter array) may in fact have limited the identification to the brightest end of the source population contaminating the SZ signal.

On the other hand, the poor resolution and sensitivity do not allow us to separate with reasonable confidence the SZ effect from any possible diffuse radio components. Studies by (cite: Moravec2019; Moravec2020) show that a large fraction of the sources belonging to the population of radio-loud AGNs within the MaDCoWS clusters exhibit extended morphologies. In this regard, external data may be key to complementing information about radio contaminants. Unfortunately, the available radio surveys offer only partial coverage of the VACA LoCA sample.

In particular, we first checked the NRAO VLA Sky Survey (cite: Condon1998) for possible radio components. The inspection of the NVSS images of the VACA LoCA fields, however, does not highlight any significant radio sources, point-like or diffuse.

We further inspect the VLA Faint Images of the Radio Sky at Twenty-Centimeters (cite: Becker1995) survey, which provides coverage for only five sources from the VACA LoCA pilot sample. One low-significance source is found in each of the and fields, both coinciding with bright point-like sources identified by the blind search over the ACA data (Sect. [3.2](#sec:analysis:pts)).

![](figures/figure07.pdf)

More recently, the Very Large Array Sky Survey (cite: Lacy2020) completed its first epoch of observations covering the entire sky north of $\delta=-40$ in S Band (2-4 GHz), which offers the advantage of sharing the same sky coverage as the full MaDCoWS sample but at much higher resolution than NVSS. The first epoch maps reach a depth of $\approx 120~\mu$Jy RMS on average. Surprisingly, the only sources we were able to confirm at $>3\sigma$ significance are those also seen in the FIRST data on and .

The FIRST and VLASS images of the field are the only ones to show the presence of a clear radio source within any of the VACA LoCA clusters. This exhibits a double-lobed feature, identified by (cite: vanVelzen2015) as belonging to the radio jets from a central FR II radio galaxy. It corresponds to a strong radio source detected near the center of the ACA field, which may be the cause of the inferred mass well below the value predicted from MaDCoWS mass–richness scaling relation. Although we model all possible contributions from unresolved radio emission from the central regions of the cluster, any residual contributions (e.g., from extended structures) may still limit our ability to retrieve an accurate estimate of the cluster mass. Unfortunately, the resolution of the ACA observation of does not allow us to determine whether the model describes the signal from the central galaxy, the radio lobes, or a blend of these two forms of emission (see Fig. [8](#fig:vlass)).

To get a sense of whether the contamination from the extended radio lobes may contribute substantially to limiting the statistical significance of the SZ signal from , we scale the integrated flux measured in the VLASS image to the central frequency of the VACA LoCA data, $\nu_{\textsc{aca}}=97.5~\mathrm{GHz}$. We assume the radio lobes exhibit a typical synchrotron spectrum with average spectral index of $\alpha=-0.85$, appropriate for this redshift range (cite: vanVelzen2015), and account for both the VLASS and ACA broadband spectral coverage. The fluxes integrated over the eastern and western lobes in the VLASS data are respectively $i_{\textsc{vlass}}=6.35~\mathrm{mJy}$ and $i_{\textsc{vlass}}=6.11~\mathrm{mJy}$, corresponding to $i_{\textsc{aca}}=0.32~\mathrm{mJy}$ and $i_{\textsc{aca}}=0.31~\mathrm{mJy}$ at the central frequency of our ACA observations. As indicated by the contours in Fig. [8](#fig:vlass), the ACA observations do not resolve the individual radio lobes, and these will manifest in the interferometric image of as an unresolved emission with a flux density of $0.60~\mathrm{mJy}$. On the other hand, the peak of the SZ signal expected in the case that the cluster mass exactly follows the MaDCoWS mass–richness relation would be around $-0.45~\mathrm{mJy~beam^{-1}}$. Furthermore, the sum of the extrapolated lobe flux and the SZ signal is consistent with the amplitude of the point source component identified by the blind search, $i_{\textsc{ps}}=0.20\substack{+0.06\\-0.04}~\mathrm{mJy}$. Under the assumption of a spatial correspondence of the radio source and the SZ centroid, this implies that most of the SZ signal from the cluster core could be entirely dominated by the emission of the radio lobes and, in turn, dim the measured flux from the radio source. Since the ACA is capable of probing the SZ signal from only the innermost radii of (see Fig. [2](#fig:filtered)), the above estimates further confirm that the radio contamination may have been critical in biasing the mass reconstruction low. This combines with the fact that a higher mass would correspond to a more extended and hence more severely filtered SZ signal. We note, however, that the above discussion is only approximate, as we do not have information on the real spectral index over the range of frequencies covered by the ACA observation. Again, the proper characterization of the radio source within with data at higher angular resolution will be crucial to improving the constraints on the cluster mass.

## Dependence on the assumed pressure model

![](figures/figure08.pdf)

As already mentioned in Sect. [3.1](#sec:analysis:sz), we further test the mass reconstruction against different versions of the gNFW pressure profiles. In Fig. [9](#fig:masssigma), we provide a direct comparison of the masses and respective effective significance levels for the VACA LoCA clusters with significant detections. The full list with the estimates of the cluster masses for all the profiles considered in Table [1](#tab:gnfw) can be found in Table [\[tab:app:masses\]](#tab:app:masses).

![](figures/figure09.pdf)

Not unexpectedly, the specific value for the cluster mass is highly dependent on the specific profile assumed to describe the pressure distribution. As shown in the $uv$ radial profile of Fig. [10](#fig:uvprof:mooj0129), most of the SZ flux is not probed by ACA, making it sensitive only to the pressure distribution within the inner region of galaxy clusters. This can also be inferred by comparing the values for the MRS in each observation to $2 \times \theta_{500}$ using Tables [\[tab:obsdata\]](#tab:obsdata) and [\[tab:masses\]](#tab:masses), respectively. This effect couples with the primary beam attenuation of the edges of the ACA fields, which drives the characteristic radius of the gNFW profile to be on the same of order of the antenna pattern half width half maximum, and thus affecting the mass reconstruction. As a result, the model based on the gNFW parameterization from (cite: McDonald2014) and for the morphologically disturbed sample in (cite: Arnaud2010) present masses systematically higher than the other profiles, as a direct consequence of their flatter radial trend at small radii. Conversely, the strongly peaked cool-core profile by (cite: Arnaud2010) allows us to easily fit low-mass (and, then, very compact) cluster models to the observed SZ signal. Nevertheless, as we were not able to infer any of the parameters defining the gNFW pressure profile in Eq. [\[eq:gnfw\]](#eq:gnfw), the small scatter in the effective significance for each of the different pressure models does not allow us to select or rule out any of the mass estimates.

![](figures/figure10.pdf)

The impossibility of discriminating between different gNFW scenarios is an immediate consequence of the limited sensitivity of the ACA observations we are analyzing, along with the lack of information on large angular scales. Figure [10](#fig:uvprof:mooj0129) shows the $uv$ radial plot for the different gNFW best-fit models for the most significantly detected cluster of the VACA LoCA sample, . Although they all succeed in describing the long baseline data, they also present a non-negligible scatter over angular scales larger than the maximum recovered scale in the observation. As discussed in (cite: DiMascolo2019a) and (cite: Perrott2019), the joint analysis of interferometric measurements and lower-resolution, single-dish observations provides a straightforward solution for improving the reconstruction of models of the SZ signal from galaxy clusters. Cosmic microwave background experiments designed to detect clusters at arcminute resolution, such as the Atacama Cosmology Telescope (cite: Hilton2018) or the South Pole Telescope (cite: Bleem2015; Bleem2020) could fulfill the needs of complementary large-scale data, and the VACA LoCA clusters are comparable in mass to some of the high-redshift systems detected by those surveys (see Fig. [11](#fig:massredshift)). However, the publicly available data do not cover the portion of the sky comprising the VACA LoCA fields.

Additionally, (cite: Gonzalez2019) compares the *Planck* mass-redshift relation to the masses inferred for the entire MaDCoWS sample, and finds that they predominantly lie below the mass selection function of *Planck*. For the VACA LoCA sample of MaDCoWS clusters, we find that no useful constraint on the integrated Compton parameter $Y$ can be obtained from the *Planck* maps, due to beam dilution and limited sensitivity. In all but the most extreme case the integrated SZ signal for each clusters would fall within a single 10$'$ resolution element of *Planck*. Extrapolating the fits to the VACA LoCA sample, each member should have an average Compton $Y$ value $\langle Y \rangle \lesssim 1.6\times10^{-6}$ over an area of 100 square arcminutes, while the RMS noise level in the *Planck* maps is $\approx 1.7 \times 10^{-6}$ on average (cite: Planck2015_XXII). This indicates that the most massive clusters in VACA LoCA may be on the order of $1\sigma$ significance in the *Planck* maps, while the rest are well below that, and even a stacked measurement using the ten members of the pilot sample would be marginal.

It is worth noting that the small range of inferred $\sigma_{\mathrm{eff}}$ implies that ACA is able to provide robust detections of the SZ signal from the VACA LoCA sample clusters independent of assumptions about the underlying pressure electron distribution.

# Conclusions

In this work, we analyze a pilot sample of ACA observations of ten high-redshift galaxy clusters representative of the typical richness of the MaDCoWS catalog. This has been mainly aimed at directly testing the capability of the ACA in ALMA Band 3 for measurements of the SZ signal from high-redshift systems. In summary, our main findings are the following:

- The ACA can provide robust and relatively straightforward validation of galaxy cluster identifications through the detection of the SZ signal from the intracluster gas. We note that the on-source integration times are typically $\lesssim 3$ hours per target. More importantly, the detection significance is not affected by the specific choice of pressure distribution model.\

- The limited sensitivity and angular dynamic range probed by the observations limit the accuracy of the mass estimates. The mass estimates within $r_{500}$ are strongly dependent on the specific choice of pressure model, as the maximum recoverable scale in the observations is smaller than the typical radius within which one would like to probe the integrated SZ signal, $\theta_{500}$ (see Tables [\[tab:obsdata\]](#tab:obsdata) and [\[tab:masses\]](#tab:masses), respectively).\

- Related to the point above, a thorough characterization of the cluster dynamical state cannot be achieved, as the ACA angular resolution and limited sensitivity do not constrain small-scale features in the ICM within the observed galaxy clusters. However, the analysis does reveal two potentially exciting merging cluster candidates that merit more detailed follow-up.\

- The $uv$-space analysis of ACA data is crucial for separating the SZ signal from unresolved sources of contamination. However, the reconstruction of a proper and exhaustive model is limited by the above-mentioned sensitivity, resolution, and maximum recoverable scale.

Data at higher angular resolution than ACA (e.g., from the ALMA 12-meter array) would provide a dramatic improvement in the identification and characterization of point-like sources populating the cluster fields. Furthermore, multi-frequency coverage of the cluster fields would provide fundamental insight into, and better constraints on, the spectral properties of any contaminant source, and thus better disentangle its signal from the underlying SZ effect.

On the other hand, as discussed in Sect. [4.4](#sec:res:mass), the possibility of complementing interferometric observations with single-dish measurements of the same targets will be key to gaining a better description of the electron pressure distribution out to large scales, and hence a more accurate reconstruction of the cluster masses. However, the scales recoverable with current SZ survey instruments are limited to greater than 1 arcminute at 90 GHz, leaving a gap with little to no overlap in Fourier modes probed in such joint analyses (cite: DiMascolo2019a). An exciting advance could be obtained using a future large single-dish telescope with at least three times the size of the ACA and ALMA primary mirrors and a wide ($>1^\circ$) field of view, such as the Atacama Large Aperture Submillimeter Telescope (cite: Klaassen2019).

Finally, ALMA Bands 1 (cite: DiFrancesco2013; Huang2016) and 2 (cite: Yagoubov2020) will further increase the maximum recoverable scale over the next few years, and thus the sensitivity of ALMA and the ACA to diffuse, low surface brightness signals on arcminute scales.

# Acknowledgments

We thank the anonymous referee for the thoughtful suggestions and comments that helped improving this work. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.2.00014.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. EC and RS acknowledge partial support by the Russian Science Foundation grant 19-12-00369. The work of PRME and DS was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA.

68 natexlab

(ref: Akamatsu2016) Akamatsu, H., Gu, L., Shimwell, T. W., et al. 2016, A&A, 593, L7

(ref: Andreon2015) Andreon, S. 2015, A&A, 582, A100

(ref: Ansarifard2020) Ansarifard, S., Rasia, E., Biffi, V., et al. 2020, A&A, 634, A113

(ref: Arnaud2010) Arnaud, M. et al. 2010, A&A, 517, A92

(ref: Basu2016) Basu, K., Sommer, M., Erler, J., et al. 2016, ApJL, 829, L23

(ref: Battaglia2012) Battaglia, N., Bond, J. R., Pfrommer, C., & Sievers, J. L. 2012, ApJ, 758, 74

(ref: Becker1995) Becker, R. H., White, R. L., & Helfand, D. J. 1995, ApJ, 450, 559

(ref: Biffi2016) Biffi, V., Borgani, S., Murante, G., et al. 2016, ApJ, 827, 112

(ref: Bleem2020) Bleem, L. E., Bocquet, S., Stalder, B., et al. 2020, ApJS, 247, 25

(ref: Bleem2015) Bleem, L. E., Stalder, B., de Haan, T., et al. 2015, ApJS, 216, 27

(ref: Bocquet2019) Bocquet, S., Dietrich, J. P., Schrabback, T., et al. 2019, ApJ, 878, 55

(ref: Brodwin2015) Brodwin, M., Greer, C. H., Leitch, E. M., et al. 2015, ApJ, 806, 26

(ref: Bulbul2019) Bulbul, E., Chiu, I. N., Mohr, J. J., et al. 2019, ApJ, 871, 50

(ref: Challinor1998) Challinor, A. & Lasenby, A. 1998, ApJ, 499, 1

(ref: Churazov2015) Churazov, E., Vikhlinin, A., & Sunyaev, R. 2015, MNRAS, 450, 1984

(ref: Condon1998) Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693

(ref: Decker2019) Decker, B., Brodwin, M., Abdulla, Z., et al. 2019, ApJ, 878, 72

(ref: DiFrancesco2013) Di Francesco, J., Johnstone, D., Matthews, B. C., et al. 2013, arXiv e-prints, arXiv:1310.1604

(ref: DiMascolo2019a) Di Mascolo, L., Churazov, E., & Mroczkowski, T. 2019a, MNRAS, 487, 4037

(ref: DiMascolo2019b) Di Mascolo, L., Mroczkowski, T., Churazov, E., et al. 2019b, Astronomy and Astrophysics, 628, A100

(ref: Fazio2004) Fazio, G. G., Hora, J. L., Allen, L. E., et al. 2004, ApJS, 154, 10

(ref: Geach2017) Geach, J. E. & Peacock, J. A. 2017, Nature Astronomy, 1, 795

(ref: Gobat2019) Gobat, R., Daddi, E., Coogan, R. T., et al. 2019, A&A, 629, A104

(ref: Gonzalez2015) Gonzalez, A. H., Decker, B., Brodwin, M., et al. 2015, ApJL, 812, L40

(ref: Gonzalez2019) Gonzalez, A. H., Gettings, D. P., Brodwin, M., et al. 2019, ApJS, 240, 33

(ref: Hasselfield2013) Hasselfield, M., Hilton, M., Marriage, T. A., et al. 2013, JCAP, 2013, 008

(ref: Hilton2018) Hilton, M., Hasselfield, M., Sifón, C., et al. 2018, ApJS, 235, 20

(ref: Hoegbom1974) Högbom, J. A. 1974, A&AS, 15, 417

(ref: Huang2019) Huang, N., Bleem, L. E., Stalder, B., et al. 2020, AJ, 159, 110

(ref: Huang2016) Huang, Y. D. T., Morata, O., Koch, P. M., et al. 2016, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9911, The Atacama Large Millimeter/sub-millimeter Array band-1 receiver, 99111V

(ref: Iguchi2009) Iguchi, S., Morita, K.-I., Sugimoto, M., et al. 2009, PASJ, 61, 1

(ref: Itoh1998) Itoh, N., Kohyama, Y., & Nozawa, S. 1998, ApJ, 502, 7

(ref: Itoh2004) Itoh, N. & Nozawa, S. 2004, A&A, 417, 827

(ref: Jeffreys1961) Jeffreys, H. 1961, Theory of Probability, 3rd edn. (Oxford, England: Oxford)

(ref: Klaassen2019) Klaassen, P., Mroczkowski, T., Bryan, S., et al. 2019, in BAAS, Vol. 51, 58

(ref: Lacy2020) Lacy, M., Baum, S. A., Chandler, C. J., et al. 2020, PASP, 132, 035001

(ref: Marriage2011) Marriage, T. A., Acquaviva, V., Ade, P. A. R., et al. 2011, ApJ, 737, 61

(ref: McDonald2014) McDonald, M., Benson, B. A., Vikhlinin, A., et al. 2014, ApJ, 794, 67

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Moravec2019) Moravec, E., Gonzalez, A. H., Stern, D., et al. 2019, ApJ, 871, 186

(ref: Moravec2020) Moravec, E., Gonzalez, A. H., Stern, D., et al. 2020, ApJ, 888, 74

(ref: Mroczkowski2019) Mroczkowski, T., Nagai, D., Basu, K., et al. 2019, Space Sci. Rev., 215, 17

(ref: Nagai2007) Nagai, D., Kravtsov, A. V., & Vikhlinin, A. 2007, ApJ, 668, 1

(ref: Perrott2019) Perrott, Y. C., Javid, K., Carvalho, P., et al. 2019, MNRAS, 486, 2116

(ref: Planck2013V) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2013, A&A, 550, A131

(ref: Planck2016XXVII) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016a, A&A, 594, A27

(ref: Planck2015_XXII) Planck Collaboration, Aghanim, N., Arnaud, M., et al. 2016b, A&A, 594, A22

(ref: Rettura2018) Rettura, A., Chary, R., Krick, J., & Ettori, S. 2018, ApJ, 867, 12

(ref: Ruppin2019b) Ruppin, F., Mayet, F., Macı́as-Pérez, J. F., & Perotto, L. 2019a, MNRAS, 490, 784

(ref: Ruppin2020) Ruppin, F., McDonald, M., Brodwin, M., et al. 2020, ApJ, 893, 74

(ref: Ruppin2019c) Ruppin, F., Sembolini, F., De Petris, M., et al. 2019b, A&A, 631, A21

(ref: Rykoff2012) Rykoff, E. S., Koester, B. P., Rozo, E., et al. 2012, ApJ, 746, 178

(ref: Saro2015) Saro, A., Bocquet, S., Rozo, E., et al. 2015, MNRAS, 454, 2305

(ref: Sazonov1998) Sazonov, S. Y. & Sunyaev, R. A. 1998, Astronomy Letters, 24, 553

(ref: Sembolini2014) Sembolini, F., De Petris, M., Yepes, G., et al. 2014, MNRAS, 440, 3520

(ref: Shi2015) Shi, X., Komatsu, E., Nelson, K., & Nagai, D. 2015, MNRAS, 448, 1020

(ref: Sunyaev1980) Sunyaev, R. A. & Zeldovich, I. B. 1980, MNRAS, 190, 413

(ref: Sunyaev1972) Sunyaev, R. A. & Zeldovich, Y. B. 1972, Comments on Astrophysics and Space Physics, 4, 173

(ref: Thompson1986) Thompson, A. R., Moran, J. M., & Swenson, G. W. 1986, Interferometry and synthesis in radio astronomy

(ref: Trotta2008) Trotta, R. 2008, Contemporary Physics, 49, 71

(ref: vanVelzen2015) van Velzen, S., Falcke, H., & Körding, E. 2015, MNRAS, 446, 2985

(ref: Wallis2014) Wallis, K. F. 2014, Statist. Sci., 29, 106

(ref: Wik2008) Wik, D. R., Sarazin, C. L., Ricker, P. M., & Rand all, S. W. 2008, ApJ, 680, 17

(ref: Wright2010) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: Wylezalek2013) Wylezalek, D., Galametz, A., Stern, D., et al. 2013, ApJ, 769, 79

(ref: Wylezalek2014) Wylezalek, D., Vernet, J., De Breuck, C., et al. 2014, ApJ, 786, 17

(ref: Yagoubov2020) Yagoubov, P., Mroczkowski, T., Belitsky, V., et al. 2020, A&A, 634, A46

(ref: Yu2015) Yu, L., Nelson, K., & Nagai, D. 2015, ApJ, 807, 12

# Mass estimates

Table [\[tab:app:masses\]](#tab:app:masses) reports the inferred cluster masses when employing the different gNFW models proposed in (cite: Arnaud2010), (cite: Planck2013V), and (cite: McDonald2014). A summary of the profile parameters is provided in Table [1](#tab:gnfw).

+:----------:+:-----------------------------:+:---------:+:-----------------------------:+:-----------------------:+:-----------------------------:+:-----------------------:+:-----------------------------:+:-----------------------:+:-----------------------------:+:-----------------------:+:-----------------------------:+:-----------------------:+
| Cluster ID | $z_{\mathrm{phot}}$           | $\lambda$ | $M_{500}$                     | $\sigma_{\mathrm{eff}}$ | $M_{500}$                     | $\sigma_{\mathrm{eff}}$ | $M_{500}$                     | $\sigma_{\mathrm{eff}}$ | $M_{500}$                     | $\sigma_{\mathrm{eff}}$ | $M_{500}$                     | $\sigma_{\mathrm{eff}}$ |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | –                             | –         | $(10^{14}~M_{\odot})$         | –                       | $(10^{14}~M_{\odot})$         | –                       | $(10^{14}~M_{\odot})$         | –                       | $(10^{14}~M_{\odot})$         | –                       | $(10^{14}~M_{\odot})$         | –                       |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            |                               |           | universal                                               | cool-core                                               | disturbed                                               | *Planck*                                                | (cite: McDonald2014)                                    |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            |                               |           |                               |                         |                               |                         |                               |                         |                               |                         |                               |                         |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.05\substack{+0.04\\-0.05}$ | $49\pm7$  | $2.57\substack{+0.30\\-0.30}$ | $7.77$                  | $2.09\substack{+0.24\\-0.29}$ | $8.07$                  | $3.47\substack{+0.32\\-0.40}$ | $7.63$                  | $2.75\substack{+0.32\\-0.38}$ | $7.85$                  | $3.72\substack{+1.28\\-1.11}$ | $7.12$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.08\substack{+0.03\\-0.04}$ | $53\pm7$  | $1.78\substack{+0.20\\-0.29}$ | $5.32$                  | $1.51\substack{+0.21\\-0.24}$ | $5.71$                  | $2.09\substack{+0.24\\-0.38}$ | $5.35$                  | $1.66\substack{+0.31\\-0.31}$ | $5.58$                  | $2.14\substack{+0.94\\-0.74}$ | $5.24$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.10\substack{+0.05\\-0.05}$ | $58\pm7$  | $1.66\substack{+0.31\\-0.38}$ | $4.26$                  | $1.48\substack{+0.22\\-0.32}$ | $4.49$                  | $1.93\substack{+0.49\\-0.67}$ | $3.68$                  | $1.55\substack{+0.38\\-0.45}$ | $4.20$                  | $1.77\substack{+0.85\\-0.93}$ | $3.41$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            |                               |           | $2.13\substack{+0.40\\-0.49}$ |                         | $1.83\substack{+0.26\\-0.38}$ |                         | $2.67\substack{+0.56\\-0.84}$ |                         | $2.13\substack{+0.49\\-0.60}$ |                         | $2.67\substack{+1.39\\-1.47}$ |                         |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.31\substack{+0.03\\-0.05}$ | $53\pm7$  | $2.24\substack{+0.36\\-0.52}$ | $3.81$                  | $1.74\substack{+0.24\\-0.36}$ | $3.82$                  | $3.16\substack{+0.66\\-0.87}$ | $3.40$                  | $2.24\substack{+0.62\\-0.57}$ | $3.78$                  | $6.76\substack{+3.89\\-3.42}$ | $4.35$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.08\substack{+0.04\\-0.05}$ | $41\pm6$  | $1.95\substack{+0.31\\-0.31}$ | $4.53$                  | $1.58\substack{+0.22\\-0.22}$ | $5.42$                  | $2.29\substack{+0.37\\-0.37}$ | $5.09$                  | $1.91\substack{+0.35\\-0.39}$ | $5.27$                  | $2.40\substack{+0.94\\-0.83}$ | $4.25$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.02\substack{+0.07\\-0.06}$ | $41\pm7$  | $2.75\substack{+0.32\\-0.32}$ | $6.99$                  | $2.24\substack{+0.31\\-0.26}$ | $6.80$                  | $3.55\substack{+0.74\\-0.41}$ | $6.98$                  | $2.88\substack{+0.66\\-0.53}$ | $7.04$                  | $4.37\substack{+1.91\\-1.81}$ | $6.94$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.16\substack{+0.05\\-0.05}$ | $50\pm7$  | $1.86\substack{+0.34\\-0.52}$ | $5.35$                  | $1.58\substack{+0.27\\-0.34}$ | $5.55$                  | $2.58\substack{+0.56\\-0.66}$ | $5.73$                  | $1.95\substack{+0.47\\-0.61}$ | $5.62$                  | $5.13\substack{+4.57\\-3.29}$ | $5.94$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            |                               |           | $2.04\substack{+0.42\\-0.56}$ |                         | $1.67\substack{+0.31\\-0.40}$ |                         | $3.49\substack{+0.78\\-1.14}$ |                         | $2.29\substack{+0.69\\-0.79}$ |                         | $4.44\substack{+2.52\\-3.39}$ |                         |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            |                               |           |                               |                         |                               |                         |                               |                         |                               |                         |                               |                         |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.26\substack{+0.05\\-0.08}$ | $29\pm5$  | $0.30^{+0.18}$                | –                       | $0.29\substack{+0.17\\-0.20}$ | $0.83$                  | $0.27\substack{+0.16\\-0.16}$ | $0.88$                  | $0.27\substack{+0.18\\-0.18}$ | $0.61$                  | $0.32^{+0.22}$                | –                       |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.09\substack{+0.04\\-0.04}$ | $51\pm7$  | $1.17\substack{+0.27\\-0.38}$ | $2.40$                  | $0.94\substack{+0.21\\-0.35}$ | $2.54$                  | $1.33\substack{+0.34\\-0.61}$ | $2.54$                  | $0.90\substack{+0.32\\-0.44}$ | $2.53$                  | $1.52\substack{+0.86\\-0.92}$ | $2.23$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            | $1.01\substack{+0.06\\-0.07}$ | $38\pm6$  | $1.82\substack{+0.34\\-0.42}$ | $1.26$                  | $1.56\substack{+0.26\\-0.38}$ | $1.34$                  | $1.62\substack{+0.43\\-0.52}$ | $1.59$                  | $2.06\substack{+0.51\\-0.50}$ | $1.23$                  | $2.27\substack{+1.10\\-1.26}$ | $1.35$                  |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+
|            |                               |           |                               |                         |                               |                         |                               |                         |                               |                         |                               |                         |
+------------+-------------------------------+-----------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+-------------------------------+-------------------------+

# $uv$ plots and dirty images

We provide here the $uv$ radial plots of the data and respective gNFW models for all the VACA LoCA clusters (Fig. [12](#fig:app:uvprof)). As discussed in Sect. [4](#sec:res), all the model profiles show a fairly good agreement with data over the range of probed angular scales, while being affected by a large scatter at short baselines due to the lack of large-scale information. and clearly manifest positive modes on small $uv$ scales, while the data points for are positively offset with respect to the models. These may arise due to off-center SZ components unaccounted for by the model, or due to extended (positive) emission. However, in the case of the discrepancy is on the order of 1$\sigma$. On the other hand, the SZ signal from both and show a complex structure (see Sect. [4.2](#sec:res:multi)), and deviations from a gNFW model are not unexpected.

To get a more immediate sense of the reconstructed models, we show in Fig. [13](#fig:app:imdirty) the dirty images of VACA LoCA observations. As there are no sensible differences between the model and residual dirty images generated with different gNFW models, we consider here only the case of a universal pressure profile (cite: Arnaud2010). We again note that all the images reported here are for illustrative purposes only, and were not used in our analysis.

# *Spitzer*/IRAC galaxy overdensities

For comparison, we show in Fig. [14](#fig:app:overlays) the SZ model contours for all the VACA LoCA clusters with either a firm or a marginal detection of their SZ signature overlaid on the maps of their respective color-selected galaxy density distributions from *Spitzer*/IRAC (see Sect. [4.2](#sec:res:multi) and Figure [7](#fig:irac)). For the sake of clarity, we do not plot the secondary negative lobes arising due to the non-Gaussian pattern of the interferometric beam.

![](figures/figureA1.pdf)

![image](figures/figureA2_MOO_J0129-1641.pdf)\
![image](figures/figureA2_MOO_J0345-2913.pdf)\
![image](figures/figureA2_MOO_J0917-0700.pdf)

![image](figures/figureA2_MOO_J1139-1706.pdf)\
![image](figures/figureA2_MOO_J1223+2420.pdf)\
![image](figures/figureA2_MOO_J1342-1913.pdf)

(continued from Fig. [13](#fig:app:imdirty))

![image](figures/figureA2_MOO_J1414+0227.pdf)\
![image](figures/figureA2_MOO_J2146-0320.pdf)\
![image](figures/figureA2_MOO_J2147+1314.pdf)

(continued from Fig. [13](#fig:app:imdirty))

![image](figures/figureA3_MOO_J0129-1641.pdf) ![image](figures/figureA3_MOO_J0345-2913.pdf) ![image](figures/figureA3_MOO_J0917-0700.pdf)\
![image](figures/figureA3_MOO_J1139-1706.pdf) ![image](figures/figureA3_MOO_J1223+2420.pdf) ![image](figures/figureA3_MOO_J1342-1913.pdf)\
![image](figures/figureA3_MOO_J1414+0227.pdf) ![image](figures/figureA3_MOO_J2146-0320.pdf) ![image](figures/figureA3_MOO_J2147+1314.pdf)\

[^1]: <http://www.mmarray.org>

[^2]: <https://almascience.nrao.edu/documents-and-tools/cycle4/alma-technical-handbook>

[^3]: The average relativistic correction reported in the text is computed employing the formulation by (cite: Itoh2004). The average electron temperature is inferred from the core-excised temperature-redshift-mass scaling relation in (cite: Bulbul2019). To keep a conservative upper limit, we consider an extreme case of a galaxy cluster with the same mass as the most massive object identified in the MaDCoWS survey (cite: Ruppin2020) at a redshift equal to the highest value in the ACA sample.

[^4]: As a reference, we consider a cluster to be significantly detected if the corresponding model has a Bayes factor $\mathcal{Z}_1/\mathcal{Z}_0$ higher than 100.

</paper>

## Items to check

```json
[
 {
  "path": "data.max_recoverable_scale.evidence[0]",
  "value": "MRS 1.36-2.23 arcmin across fields (Table 1)",
  "failed_quote": "Resolution & MRS"
 }
]
```
