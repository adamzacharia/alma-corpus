# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...878..113H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Modelling the Spatial Distribution and Origin of CO Gas in Debris Disks

## Abstract

The detection of gas in debris disks raises the question of whether this gas is a remnant from the primordial protoplanetary phase, or released by the collision of secondary bodies. In this paper we analyze ALMA observations at 1-1.5" resolution of three debris disks where the $^{12}$CO(2-1)  rotational line was detected: HD 131835, HD 138813, and HD 156623. We apply the iterative Lucy-Richardson deconvolution technique to the problem of circumstellar disks to derive disk geometries and surface brightness distributions of the gas. The derived disk parameters are used as input for thermochemical models to test both primordial and cometary scenarios for the origin of the gas. We favor a secondary origin for the gas in these disks and find that the CO gas masses ($\sim 3\times10^{-3}$  M$_\oplus$) require production rates ($\sim 5\times 10^{-7}$ M$_{\oplus}$ yr$^{-1}$) similar to those estimated for the bona-fide gas rich debris disk $\beta$ Pic.

# Introduction

Young debris disks trace the final stage of the planet formation process. Most debris disks have been discovered because of their excess emission at infrared wavelengths due to orbiting dust (cite: aumann1984; Oudmaijer1992; mannings1998). This dust can be sustained by collisional cascades involving solids in a wide size distribution from $\mu$m- to km-sized bodies, triggered by the growth of Pluto-sized bodies within the disc, by secular or resonant interactions with planets in the system, and/or by planetesimals born in high velocity orbits (cite: wyatt2008; wyatt2015). Imaging of such systems provides important insights on the architecture of young planetary systems (cite: hughes2018).

Observations of gas in debris disks have been more challenging. Molecular gas was detected in only a few debris disks in early infrared and millimeter/sub-millimeter observations. This led to the traditional view that debris disks are gas-poor, and that therefore the atmospheres of gas- and ice-giant planets must have formed in the primordial disk phase (cite: zuckerman95; dent2005; hales2014; moor2015). With the advent of ALMA, sensitivity limits improved by several orders of magnitude compared to earlier surveys and now cold gas in the form of carbon monoxide has been detected in a growing number of debris disks. Most of them are younger than 50 Myr, with a few exceptions such as Fomalhaut at an age of 440 Myr (cite: moor2011; Lieman2016; marino2016; kral2017; pericaud2017; moor2017; matra2017b; marino2017).

The origin of this gas is a matter of ongoing debate. For massive disks, shielding could prevent the CO from being photo-dissociated and could explain the persistence of primordial gas even at these advanced ages (cite: Kospal13). These disks have been called hybrid disks, because their dust content is of secondary origin while at least a large fraction of the gas could be a remnant from the protoplanetary disk phase (cite: Kospal13; moor2015; moor2017). (cite: kral2018), however, showed that massive disks can also be sustained by cometary collisions if enough atomic carbon (from dissociated CO) is accumulated, resulting in a layer that shields CO (i.e. shielded secondary disks). In other cases, such as $\beta$ Pic and HD 181327, low gas densities result in CO lifetimes shorter than the orbital period and thus the CO must be re-supplied by collisional activity (cite: Dent2014; marino2016). In cases where the observed CO emission is asymmetric, this has been used to argue in favor of this interpretation (cite: Dent2014; greaves2016; matra2017b).

The incidence rate of CO gas is significantly higher around intermediate mass stars than around later spectral types. (cite: Lieman2016) used ALMA to search for dust continuum and CO emission toward disks around a sample of 23 B, A, F, and G-type stars with ages between 11 and 17 Myr. Three sources were detected in CO, all corresponding to A type stars, making the detection rate 3/7 for A stars and 0/16 for FGK stars. Newly discovered gas-rich systems confirm the prevalence of gas around A-type stars. (cite: moor2017) estimated an incidence ratio 11/16 around A stars compared to $~\sim$7% in FG-type stars. The disks around A stars are also on average two orders of magnitude brighter than the gas disks around FGK stars (cite: hughes2018).

In this work, we focus on the analysis and modelling of the brightest CO detections in (cite: Lieman2016): HD 131835, HD 138813, and HD 156623. Because of their large CO luminosities, they have been singled out as hybrid disk candidates (cite: moor2017). A description of the selection criteria, the full source list, main observational results and analysis of the continuum data were presented in (cite: Lieman2016). Section [2](#sample) describes our target sample. In Section [3.3](#modelling) we apply the Lucy-Richardson deconvolution technique to the case of circumstellar disks to infer the CO surface brightness distributions. In Section [4](#gasmass) we compare the observations to primordial and cometary origin models for the gas. In Section [5](#discussion) we discuss our results and Section [6](#conclusion) presents our conclusions.

# CO Rich Debris Disks in Sco-Cen

A summary of the ALMA $^{12}$CO(2-1)  observations of 23 luminous debris disks in the Scorpius-Centaurus Association was presented in (cite: Lieman2016). In this paper we focus on the 3 CO-rich disks that were detected at sufficient signal-to-noise ratios in order to model their line intensity profiles (HD 131835, HD 138813, and HD 156623). Table [\[tbl:co\]](#tbl:co) lists the main observational results of these 3 targets, and Figure [1](#fig:coline2) shows the resulting 1.3 mm continuum and $^{12}$CO(2-1)  integrated intensity maps after CLEANing (cite: Lieman2016) . The velocity resolution of the cubes is 0.32 km s$^{-1}$, and the spatial resolution of each image is shown in Table [\[tbl:co\]](#tbl:co).

HD 131835 (HIP 73145) is a well-studied, $\sim$16 My old A4V star located in the Upper Centaurus Lupus (UCL) moving group, known to harbor a $L_{\rm IR}/L_{*}\sim 2 \times 10^{-3}$ debris disk (cite: rizzuto2011; pecaut2012; moor2015). The dust disk has been resolved at near-, mid-infrared, and millimeter wavelengths showing the dust extends from $\sim$35 au out to at least 150 au (cite: hung2015a; hung2015b; Lieman2016; feldt2017). The near-IR VLT/SPHERE observations resolve at least three sub-structures (sub-rings) within the main dust ring, located at 35, 66 and 98 au (cite: feldt2017). The total dust mass has been derived using different methods, providing values ranging from 0.03 M$_\oplus$to 7.5 M$_\oplus$(cite: hung2015b; Lieman2016; feldt2017), comparable to massive debris disks from other surveys (cite: roccatagliata2009; thureau2014).

HD 131835 was the only object detected in the $^{12}$CO J=$3-2$ single dish survey of (cite: moor2015), out of a sample of 20, 10-40 Myr old, A- to G-type stars. (cite: moor2015) showed the $^{12}$CO(3-2) APEX spectra could be reproduced by a ring-like disk extending from 35 au to $\sim$120 au radii. The $^{12}$CO(3-2) line is used to derive a total CO mass of 5.2$\times 10^{-4}$ M$_\oplus$, assuming the gas is in local thermodynamic equilibrium (LTE). (cite: moor2017) and (cite: kral2018) derive total CO gas masses of 3.0-6.0$\times 10^{-2}$ M$_\oplus$  using observations of the optically thin C$^{18}$O(3-2) line. New ALMA observations of neutral carbon detect 3$\times 10^{-3}$ M$_\oplus$$\,$ of C$^0$ located within 40 to 200 au from the star (cite: kral2018).

HD 138813 (HIP 76310) is an A0V star member of the 11 Myr old Upper Scorpius association (cite: pecaut2012), host to a $L_{\rm
  IR}/L_{*}\sim 2.1 \times 10^{-4}$ debris disk (cite: dahm2009). It was the only A-type star detected in the 1.2 mm single-dish survey of (cite: mathews2012), from which they derive a dust mass of 1.1  M$_\oplus$. Gas line emission was neither detected with *Herschel* PACS nor JCMT in the survey of (cite: mathews2013). The ALMA images are able to resolve a ring-like disk, with inner radius and width of 70 and 80 AU respectively, and a total dust mass of $\sim
8.3\times 10^{-3}$  M$_\oplus$, smaller than the previous estimate from (cite: mathews2012). (cite: kral2017) estimate a total CO gas mass of 7.4$\times10^{-4}$  M$_\oplus$ based on the integrated line fluxes from (cite: Lieman2016) and relaxing the assumption of LTE.

HD 156623 (HIP 84881) is also an A-type star member of the Upper Scorpius association, with infrared excesses detected in *IRAS* and *WISE* (cite: rizzuto2011). Prior to the (cite: Lieman2016) survey, little was known about this star and its circumstellar environment. The ALMA 1.3 mm images are able to resolve the outer radius of the disk at $\sim 150$ AU, but do not resolve an inner edge. (cite: kral2017) estimate a total CO gas mass of 2.0$\times10^{-3}$  M$_\oplus$.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Beam size | P.A. | $\sigma_\mathrm{line}$ | $\sigma_\mathrm{int}$ | $S_\mathrm{CO}$ | S/N |
|  | (arcsec) | (deg) | (mJy beam$^{-1}$) | (mJy beam$^{-1}$ km s$^{-1}$) | (mJy km s$^{-1}$) |  |
| HD 131835 | $1.42\times 1.21$ | 28 | 10.1 | 16 | 798 $\pm$ 35 | 22.5 |
| HD 138813 | $1.02\times 0.71$ | 81 | 7.3 | 14 | 1406 $\pm$ 78 | 18.0 |
| HD 156623 | $1.32\times 0.87$ | 87 | 5.9 | 11 | 1183 $\pm$ 37 | 32.3 |

: Measured CO J=2-1 Integrated Intensities

Table notes: Summary of ALMA $^{12}$CO(2-1) observational results from (cite: Lieman2016). The columns list (1) Source name, (2) full-width-at-half-maximum beam size of the ALMA observations, (3) position angle of the beam, (4) rms in the CO J=2-1 spectral images per 0.32 km s$^{-1}$ channel, (5) rms in the CO J=2-1 integrated intensity images measured in an annulus between 4 and 8$''$ centered on the stellar position. The CO was integrated between velocities of 3 and 12 km s$^{-1}$ (HD 131835), 5 and 10.6 km s$^{-1}$ (HD 138813), and 0.5 and 8.2 km s$^{-1}$ (HD 156623). (6) Integrated CO J=2-1 intensity measured in the ALMA images. An aperture radius of 2$''$ was used for HD 131835, HD 138813, and HD 156623. (7) Signal to noise ratio of the measured CO integrated intensity.

# Modeling

In order to investigate the possible origins of the CO gas, we must first characterize its spatial location within the disk. In this section we implement a method that allows to derive the surface brightness distribution of the gas in spatial scales smaller than the angular resolution, by taking advantage of the *a priori* knowledge of the gas kinematics. This information is generally available in many astrophysical problems (e.g. galactic rotation curves), and in the particular case of circumstellar disks the gas can be well described by a keplerian velocity field (cite: hughes2008; Kospal13; Dent2014).

## Lucy-Richardson Deconvolution

The ‘Lucy-Richardson Deconvolution’ is an iterative rectification method for observed distributions, presented independently by (cite: richardson1972) and (cite: lucy1974). This method attempts to restore the *original* distribution from an *observed* distribution, in which the observed distribution corresponds to a *degraded* version of the original distribution. The key to this method is that the original distribution can be recovered if sufficient *a priori* information about the degrading process is available. Examples of degrading processes are the spatial distortion by an instrumental point spread function (PSF), instrumental broadening of spectral lines (equivalent to a velocity PSF), additive noise, or other more complex processes (cite: zech2013; stock2015; zorec2016).

The use of *a priori* kinematical information for deriving CO emissivity distribution in galaxies was demonstrated over twenty years ago by (cite: scoville1983). By applying the (cite: lucy1974) iterative rectification scheme, (cite: scoville1983) derived a de-projected emissivity distribution that successfully reproduced the observed line intensity profiles (in their case, the velocity field of the galaxy was known *a priori* via optical line studies). The advantage of this method is that it does not need any previous assumption on the surface brightness distribution (e.g. whether it is a power-law or other functional form), and that it converges relatively fast (typically in less than ten iterations).

In the case of astrophysical disks (circumstellar or galactic), the observed line intensity profiles result from the (double) convolution between the spatial and velocity PSFs, with the intrinsic emissivity distribution. If $x$ and $y$ are the linear displacement coordinates parallel and perpendicular to the disk’s major axis, we consider a point *(x,y)* located at distance R from the center of a circumstellar disk. If the velocity field is known at all points (e.g. Keplerian), $\rho(R)$ is the axisymmetric emissivity distribution and $i$ the disk inclination angle, then in the case where there is no instrumental broadening the measured intensity in that pencil beam point is:

$$\begin{equation}
\label{eqn1}
  J(x,y;v)=\frac{\rho(R)}{\cos i}\delta(v-v_{x,y})
\end{equation}$$

where $v_{x,y}$ is the Keplerian velocity at position *(x,y)*. In reality, the observed line intensity profiles correspond to convolution of the emissivity distribution $\rho(R)$ with the instrumental PSF:

$$\begin{equation}
\label{eqn2}
  I(x,y;v) = \int \int \int J(\epsilon,\eta,w)\,P(x,y,v|\epsilon,\eta,w)\,d\epsilon\,d\eta\,dw.
\end{equation}$$

Converting integration variables to polar coordinates ($\epsilon=R\cos\theta$ and $\eta~=~R\sin\theta\cos~i$), Equation [\[eqn2\]](#eqn2) can be written as

$$\begin{equation}
\label{eqn3}
$  I(x,y;v) = \int \int \int J(\epsilon,\eta,w)\,P(x,y,v|R\cos \theta,R\sin \theta \cos i,v_{R,\theta})\,R\,dR\,d\theta $
\end{equation}$$

The instrumental PSF consists of two terms, the spatial PSF $P_s$ and the velocity spread function $P_v$. The spatial component of the instrumental PSF is written as

$$\begin{equation}
\label{eqn4}
P_s(x,y|\epsilon,\eta)=\frac{1}{2\pi\sigma_s^2}\exp\left[\frac{(x-\epsilon)^2+(y-\eta)^2}{2\sigma_s^2}\right],
\end{equation}$$

where $\sigma_s^2$ is computed taking into account the FWHM of the minor and major axis of the observed PSF, as well as its positions angle in the sky. The velocity-broadening PSF takes the form:

$$\begin{equation}
\label{eqn5}
P_v(v|w)=\frac{1}{\sqrt{2\pi\sigma_v}}\exp\left[\frac{(v-w)^2}{2\sigma_v}\right]
\end{equation}$$

The dispersion of the velocity PSF, $\sigma_v$, is given by the thermal and non-thermal line widths added in quadrature (cite: Hughes2010),\
$$\begin{equation}
\label{eqn6}
\sigma_v(r)=\sqrt{\frac{2k_BT(r)}{m} + \xi^2},
\end{equation}$$

where $k_B$ is Boltzmann’s constant, $T(r)$ is the local disk temperature, $m$ is the average mass per particle, and $\xi$ is a velocity broadening term adjusted to match the instrumental spectral resolution. No turbulence has been assumed. The local disk temperature $T(r)$ is computed assuming that $T_{gas}(r)=T_{dust}(r)$ and that the dust grains are in thermal equilibrium with the stellar radiation, i.e:

$$\begin{equation}
\label{eqn7}
T(r)=\Big(\frac{L_*}{16\pi \sigma R^2}\Big)^{1/4},
\end{equation}$$

where $L_*$ is the stellar luminosity and $\sigma$ is the Stefan-–Boltzmann constant. The velocity broadening due to Keplerian rotation is estimated by assuming a geometrically flat, azimuthally symmetric circumstellar disk viewed at inclination angle $i$, in polar coordinates

$$\begin{equation}
\label{eqn8}
v_{r,\theta}=\sqrt{\frac{GM_*}{R}}\cos \theta \sin i . 
\end{equation}$$

The double convolution Kernel $\Pi(x_k,y_k;v_l|R_j)$ is defined as the convolution between the spatial PSF $P_s$ and the velocity spread function $P_v$ (cite: scoville1983),\
$$\begin{equation}
\label{eqn9}
$ \Pi(x,y;v|R)=\frac{1}{2\pi}\int_0^{2\pi}P_s(x,y|R\cos \theta,R\sin \theta \cos i)P_v(v|v_{R,\theta})d\theta.$
\end{equation}$$

By combining ([\[eqn1\]](#eqn1)), ([\[eqn3\]](#eqn3)) and ([\[eqn9\]](#eqn9)), the predicted intensity profile at any given position can be calculated from

$$\begin{equation}
\label{eqn10}
I^n(x_k,y_k;v_l)=2\pi\sum_{J=1}^{n_R} R_J \rho^n(R_J)\Pi(x_k,y_k;v_l|R_j)\Delta R.
\end{equation}$$

Note that the $I^n(x_k,y_k;v_l)$ is integrated over an area corresponding to the instrumental beam. (cite: scoville1983) showed that for an axisymmetric disk, the de-projected emissivity distribution $\rho(r)$, can be derived on scales much finer than the instrumental spatial resolution by iterating:

$$\begin{equation}
\label{eqn11}
\rho^{n+1}(R)=\rho^n(R)\frac{\sum_{k=1}^{n_B} \sum_{l=1}^{n_v} \left [ \frac{\widetilde{I}(x_k,y_k;v_l)}{I^n(x_k,y_k;v_l)}\right ] \Pi(x_k,y_k;v_l|R_j)}{\sum_{k=1}^{n_B}\sum_{l=1}^{n_v} \Pi(x_k,y_k;v_l|R_j)},
\end{equation}$$

where $\widetilde{I}(x_k,y_k;v_l)$ is the observed intensity at position $(x_k,y_k)$ and velocity v$_l$, and $I^n(x_k,y_k;v_l)$ is the theoretical line intensity profile that would be observed given the surface brightness distribution $\rho^n(r)$. The positions and velocities $x_k$, $y_k$ and $v_l$ sampled at a total of $n_B$ positions and $n_v$ channels, respectively. The radial emissivity distribution $\rho(r)$ is computed at $n_R$ discrete points spaced by $\Delta R$. The separation $\Delta R$ can be much finer than the nominal spatial resolution.

Starting with a constant surface brightness distribution $\rho^0(r)=1$, the theoretical line intensity profile is calculated using Equation [\[eqn10\]](#eqn10) and $\rho^0$ at $n_B$ positions, and the reduced $\chi^2$ between the observed and theoretical line intensity profiles is computed as

$$\begin{equation}
\label{eqn12}
\chi^2=\frac{\sum_{j=1}^{n_B}\sum_{v=1}^{n_v}(\widetilde{I}_{j,v} - I^n_{j,v})^2}{\sigma^2},
\end{equation}$$

where $\sigma$ corresponds to the RMS noise per channel in the observations. We adopt a grid that samples every $1/3$ of the beam to prevent over-sampling and avoid excessive computational time. For all sources the sampled area is limited to a circular region centered at the stellar position of 2 arcseconds in radius.\
We iterate Equation [\[eqn11\]](#eqn11) until the reduced $\chi^2$ reaches a value less than unity or when the fractional change in the reduced $\chi^2$ is less than 1$\%$ (which was found to be a good criteria for convergence of the parameters).

This approach allows to derive quickly (generally less than 10 iterations) the surface brightness distribution of the disk that provides the best fit to the models in comparison to other more time-consuming methods (cite: isella2009; tazzari2016). In Figure [2](#fig:lineprofiles) we show an example of the observed $\widetilde{I}(x,y;v)$ and modeled $I^n(x,y;v)$ line profiles for the best-fit model for HD 138813 (see Section [3.3](#modelling)).

![](fig2.pdf)

## Disk modeling and parameter-space search

In our modeling approach we adopt a Bayesian method to obtain probability distribution functions of the model free parameters. The parameter search is performed using the Python package *emcee* (cite: foreman2013), which uses the affine-invariant implementation of MCMC to run simultaneously several Markov chains to map the posterior probability distribution. By using many walkers, and by proposing new models based on the relative positioning of the *walkers*, *emcee* is effective at handling posterior probability density functions (PDF) with strong degeneracies.

|                                  | HD 131835 | HD 138813 | HD 156623 |
|:---------------------------------|:---------:|:---------:|:---------:|
| Stellar parameters               |           |           |           |
| L$_{\star}$ (L$_{\odot}$) $^{a}$ |   11.0    |   20.4    |   13.3    |
| M$_{\star}$ (M$_{\odot}$) $^{b}$ |   1.77    |    2.2    |    2.2    |
| Distance (pc)$^{c}$              |   133.7   |   137.5   |   111.8   |
|                                  |           |           |           |
| Spectra                          |           |           |           |
| $n_B$                            |    71     |    172    |    113    |
| $n_v$                            |    33     |    21     |    35     |
| v$_1$ ( km s$^{-1}$) $^{d}$      |    2.0    |    4.6    |   -1.0    |
| v$_2$ ( km s$^{-1}$) $^{d}$      |   12.0    |   11.0    |   10.0    |
| dv ( km s$^{-1}$)                |   0.32    |   0.32    |   0.32    |
| $\Delta R$ (arcsec) $^{e}$       |    0.1    |    0.1    |    0.1    |

: Fixed Model Parameters

Table notes: $^{(a)}$ Luminosities are derived using the values in (cite: kral2017) scaled by the difference in distance between Hipparcos and Gaia DR2. $^{(b)}$ Stellar mass for HD 131835 is taken from (cite: moor2015), and from (cite: hernandez2005) for HD 138813. For HD 156623 the same mass as HD 138813 is assumed. $^{(c)}$ Distances are obtained from the second data release (DR2) of Gaia (cite: gaia2018). $^{(d)}$ v$_1$ and v$_2$ denote the velocity range used for the fitting. $^{(e)}$ $\Delta R$ corresponds to the radial sampling of the surface brightness distribution.

Our disk model is defined by the disk’s position angle *$\theta$*, inclination *i*, central velocity *v$_r$*, as well as the gas surface brightness distribution $\rho(r)$. In addition two extra parameters, *$\Delta\alpha$* and *$\Delta\delta$*, are added to find the exact centroid position of the disk (cite: tazzari2016). Table [\[tbl:fix\]](#tbl:fix) shows the fixed model parameters for each system.

At each iteration, the position of a given walker in the parameter space (i.e. one set of model parameters) defines a disk model, for which the best-fit surface brightness distribution is found by Lucy-Richardson deconvolution as described in [3.1](#lucy). The $\chi^2$ of this model is computed using its surface brightness distribution, and the resultant $\chi^2$ value is used to compute the PDF. The next iteration will consider the PDF computed by all walkers in order to define the move to the next point in parameter space. In this manner, the walkers interact with each other and the PDF can be sampled fast and efficiently.

Typically the MCMC chains are let to evolve during the

*burn-in* phase, during which 1000 walkers sample a broad range of the parameter space in order to locate the maximum of the posterior probability. This is achieved in between 100 to 400 steps. After the burn-in phase, 800 to 1000 more iterations are allowed in order to further sample the posterior probability around the global maximum. After the removal of the burn-in steps, the posterior probability provides information on the marginal distributions of the free parameters (i.e. the uncertainties on the derived free parameters). The advantage of this method is that it can be fully parallelized. Using 24 processors in parallel we were able to sample 1200 iterations of the 1000 individual chains in a week of processing time.

## Modeling results

The MCMC search through Lucy-Richardson deconvolution model fitting method was run for each of the three gas disks. Figure [3](#fig_corner_76310) shows the staircase plots of the chains obtained for HD 138813 after the MCMC fitting process. The MCMC staircase plots for HD 131835 and HD 156623 are presented in Section [7](#lucyappendix) of the Appendix. In Table [\[tbl:mod\]](#tbl:mod) we show the best-fit parameters for each disk. The uncertainties on the individual parameters are estimated by fitting a Gaussian to the marginalized distributions (corresponding to the diagonal panels of the staircase plots). Figure [4](#fig:emissivity) shows the CO surface brightness distribution computed from the best-fit model of each disk.

Figure [5](#fig:hd76310-residual) shows the comparison between the data and model for the HD 138813 disk, together with the resulting residuals in both integrated intensity (moment 0) and velocity dispersion (moment 1) maps. It can be seen from the residual maps that the models provide reasonable fit to the observations, with no residuals above 5-$\sigma$ level (15% of the peak flux). Data, model and residual plots for HD 131835 and HD 156623 are presented in Section [7](#lucyappendix) of the Appendix.

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Source | Inclination | PA ($^{\circ}$) | v$_r$ | $\Delta\alpha$ | $\Delta\delta$ |
|  | (deg) | (deg) | (km s$^{-1}$) | (arcsec) | (arcsec) |
| HD 131835 | 68.6 $\pm$1.6 | 57.7 $\pm$6.2 | 7.26 $\pm$0.06 | 0.03$\pm$0.06 | -0.02$\pm$0.06 |
| HD 138813 | 29.0 $\pm$0.3 | 49.6 $\pm$0.8 | 7.75 $\pm$0.01 | -0.08$\pm$0.01 | 0.03$\pm$0.01 |
| HD 156623 | 31.8 $\pm$0.5 | 94.1 $\pm$2.8 | 4.20 $\pm$0.03 | 0.05$\pm$0.02 | 0.01$\pm$0.02 |

: Best-fit Model Parameters

Table notes: The uncertainties in the derived parameters correspond to 1$\sigma$ and are obtained by a fitting a Gaussian to the marginalized distributions, after correcting for the number of correlated pixels within one beam.

![](fig6.pdf)

HD 131835 is the most studied of the targets within our sample. (cite: moor2015) was able to model the $^{12}$CO(3-2) APEX spectra assuming the gas extends from 35 au (cite: hung2015b), and varying the outer radius to fit the single dish data. For their best fit model, (cite: moor2015) measure a systemic velocity of 7.2 km s$^{-1}$ in the Local Standard of Rest (LSR) frame. The systemic velocity we derive is identical to the one measured by (cite: moor2015). This value of the system’s velocity is also consistent with the stellar radial velocity measured in the optical by (cite: Rebollido). They measure a heliocentric radial velocity of v$_{\rm Helio}=$2.6$\pm$1.4 km s$^{-1}$, which corresponds 6.4$\pm$1.4 km s$^{-1}$ after converting to v$_{\rm LSR}$. This is also consistent with the estimation of the systemic velocity from the \[CI\] line data by (cite: kral2018), who derive a heliocentric velocity of 3.57$\pm$0.1  km s$^{-1}$, which corresponds to a v$_{\rm
   LSR}$ of 7.37 $\pm$0.1 km s$^{-1}$. The radial velocities derived for HD 138813 and HD 156623 are also consistent with radial velocities measured in the optical. (cite: Rebollido) find radial velocities of 7.7$\pm$2.0 km s$^{-1}$ and 4.6 $\pm$1.5 km s$^{-1}$ for HD 138813 and HD 156623 respectively (v$_{\rm LSR}$).

The inclination and position angles adopted in the models from (cite: moor2015) were fixed to the values derived from Gemini/GPI observations (cite: hung2015b). More recently (cite: feldt2017) refined the inclination and PA of the near-IR dust disk to 72$^{\circ}$.6$\pm_{-0.6}^{0.5}$ and 60$^{\circ}$.3$\pm_{-0.2}^{0.2}$, respectively. (cite: kral2018) fit an inclination of 76.95$^{3.1}_{2.4}$ to the \[CI\] line data. The inclination angle of 68.6 $\pm$1.6 we derive is consistent within 1.7$\sigma$ with the values from the infrared images and also from the ALMA CI data (cite: kral2018). For comparison, we compute the inclination of the 1.3mm continuum dust disk by performing a gaussian fitting of the 1.3mm data. Using CASA task `imfit` to fit in the image plane we derive an inclination angle of 69.8$\pm$0.7, whereas fitting in the visibility domain we obtain an inclination angle of 66.4$\pm$0.2 (Using CASA task `uvmodelfit`). The scatter seen in the continuum inclination could be indicative of the limitations of the data or that there are systematics affecting the derivation on the inclination angle and thus the formal errors quoted for the inclination of the gas disk could be underestimated. Differences between the inclinations derived by millimeter and scattered light images are not uncommon. (cite: loomis2017) reported differences of $\sim$15$^{\circ}$ in the disk around AA Tau, which could be attributed to a warp in the inner regions of the disk. Discrepancies in the inclinations of the gas and dust disks measured in the millimeter have also been reported, as is the case of $\beta$ Pictoris in which the CO is more clumpy than the dust and is located 5 au above the midplane more closely aligned with an inner disk and to the orbit of the planet $\beta$ Pic $b$ (cite: matra2017a). There are no previous measurements of the disk inclinations for the HD 138813 and HD 156623 disks. Higher resolution images of the HD 131835 system are necessary to investigate the presence of clumps, warps or other asymmetries in the gas disk.

It is interesting to note that similar to the inner and outer radii used by (cite: moor2015) to fit the $^{12}$CO(3-2) APEX data, our modelling of the $^{12}$CO(2-1) line derives a surface brightness distribution which is also confined to a region between 50-150 au. This is also similar to the extension of the CI disk (cite: kral2018). To quantify how much the assumption of T$_{\tt gas}$=T$_{\tt dust}$ could affect the determination of the emissivity distribution we experimented using a temperature profile (T(r) $\propto$ r$^{-p}$ with p=0.4) that yields temperatures of $\sim$100 K in the inner 20 au, similar to the ones used in the models of (cite: kral2017). We find that this does not affect the determination of a cavity in the CO, while the derived disk parameters remain consistent within 2-3 sigma.

Figure [6](#diskradii) shows the comparison between the location of the dust and gas disks for all three targets. The inner and outer radii of the dust emission are taken from (cite: Lieman2016), while the location of the gas correspond to the emissivity profiles from Figure [4](#fig:emissivity). The dust and gas ring around HD 131835 are both confined to a $\sim$100 au ring. In Figure [6](#diskradii) we have also marked the location of the two brightest dust rings seen in the near-IR with SPHERE (cite: feldt2017). The two near-IR dust rings roughly coincide with the peak of the CO emission, which could suggest a common origin. Similarly to HD 131835, HD 138813 shows a ring-like structure in dust (cite: Lieman2016), and also in $^{12}$CO according to our modelling of the ALMA data. The CO surface brightness from HD 156623 is found to be centrally peaked. Since the inner radius of the dust disk was unresolved at 1.3 mm, thus it is not possible to conclude whether the peak gas emission resides inside a dust cavity or if it is mixed with the dust. Most of the gas (20 to 60$\%$ of the peak surface brightness), however, appears to be co-located with the dust.

# Gas Mass and Origin

We next attempt to determine the mass of CO implied by the observed emission. We first present simple estimates and then discuss results obtained using detailed thermochemical models where the temperature, density and chemical structure are calculated in a self-consistent manner by solving for hydrostatic pressure equilibrium coupled with thermal balance. We consider both proposed origins of the gas, one in which the gas is a primordial relic from the protoplanetary disk stage, and another where the gas is produced by secondary collisions in a debris disk (cite: moor2011; moor2017; zuckerman2012; kral2017).

#### Estimate of optically thin LTE mass limit

A simple CO mass estimate can be made by assuming that the emission is in LTE and optically thin. The fractional population of the J=2 level is $N_{2}/N_{CO} = (2J+1) e^{-16.6/T}/{Z(T)}$ where $Z(T)~\sim
T/2.762$ is the rotational partition function for CO (cite: Hollenbach1979). For a mean line luminosity of $\sim
  10^{-9}$ L$_{\odot}$ as observed (a flux of 1 Jy km s$^{-1}$ from a disk at 100 pc gives a line luminosity $\sim 2\times\,10^{-9}$ L$_{\odot}$), and with a transition probability $A_{21}=6.91\times10^{-7}$ s$^{-1}$, we can estimate the total number of CO molecules from the total line luminosity $L_{21} = N_{2} A_{21}
\Delta E_{21}$ giving a CO mass

$$\begin{equation}
{\rm M}_{CO}^{LTE, \tau<1} = 1.25 \times
10^{22}\ (\frac{L_{21}}{10^{-9}{\rm L}_{\odot}}) \ T \ e^{16.6/T}
\quad g
\label{mcothin}
\end{equation}$$ and a minimum mass M$_{CO}^{min}$ of $5.6\times10^{23}$ g or $10^{-4}$ M$_{\oplus}$ if all the gas is at $\sim 16.6$K (corresponding to the upper energy level of the CO(2-1) line).

Deviating from any of the assumptions made above on the optical depth, LTE conditions or temperature would result in a mass higher than M$_{CO}^{min}$ to reproduce the observed emission. From Eq. [\[mcothin\]](#mcothin), the mass derived is seen to increase for gas temperatures both higher and lower than 16.6K. ($\sim 3$M$_{CO}^{min}$ for 5 K and $\sim 5$M$_{CO}^{min}$ for 200K).

#### Estimate of mass required for LTE

The fact that we have spatially resolved emission maps allows us to estimate a density from the mass and place constraints on the validity of the LTE assumption. For the two scenarios considered, we assume that H$_2$ is the main collision partner for primordial gas and that electrons are the main colliders for secondary origin gas (H atoms from photodissociation of water could be abundant, but these collision rates are lower and electrons dominate, e.g., see (cite: matra2017a). For thermally populated levels, the collider gas density needs to be higher than the critical density ($n_{crit}=A/\gamma \sim 10^4$ cm$^{-3}$ for H$_2$ (cite: yang2010), and $\sim$100 cm$^{-3}$ for e$^-$ (cite: Dickinson1977)) everywhere in the disk.

From the radial intensity distribution fits (Section [3.3](#modelling), Figure [4](#fig:emissivity)) and from the emission maps, the CO disk radius is $\sim$ 200 au. Assuming a constant disk thickness of 10 au (cite: jewitt1996; trujillo2001), the disk volume is $\sim 10^6$ au$^3$.

The mass needed for LTE can be estimated with a simple constant density assumption as $\sim n_{crit} \times$volume; the primordial origin scenario therefore requires a CO disk mass of $\sim 2\times
10^{23}$g (for $n(CO)\sim 1.4\times 10^{-4} n(H_2)$). This limit is similar to that made with the optically thin assumption above, and LTE is likely a valid assumption for the primordial gas disk. The total disk mass in this case (H$_2$+CO) is expected to be at least $\sim
0.01$ M$_{\oplus}$. In the case of secondary origin gas, densities are low enough that LTE may be difficult to attain. Emission is therefore likely to be sub-thermal and Eq. [\[mcothin\]](#mcothin) therefore likely to underestimate the true disk mass (cite: matra2015).

#### Estimate of mass limits imposed by CO photodissociation

As noted in previous work (cite: Kospal13; moor2015; kral2017), survival of CO against photodissociation could impose stricter constraints on the mass needed to explain the observed line fluxes, especially for the secondary origin scenario. For an ambient interstellar field (cite: habing1968), the lifetime of a CO molecule is $\sim
120$ years (cite: visser2009). A rough order of magnitude estimate of the column densities available for shielding in the two origin scenarios with masses for emission in LTE as described above yield $N_{H_2} \sim
10^{18}$ cm$^{-2}$ (primordial, $n_{H_2}\sim 10^4$ cm$^{-3}$) and $N_{CO} \sim 10^{16}$ cm$^{-2}$ (cometary, $n_{CO}\sim 100$ cm$^{-3}$ ); at these column densities UV shielding of CO by H$_2$ and CO self-shielding are not very efficient (cite: visser2009). Primordial gas disk masses need to be $\sim 10^4$ higher, $\sim 25$M$_{\oplus}$, for CO to be shielded and survive for the age of the system. For the secondary origin scenario, the CO is only marginally self-shielded and the estimated CO mass yields lifetimes $\sim 2500$ years; but since there is continuous CO production, the mass in this case depends on the replenishment rate with lower disk masses requiring higher replenishment rates.

To summarize, we find that simple estimates using spatial information from the resolved emission maps and typical CO line luminosities yield plausible masses of a few tens of a M$_{\oplus}$ of H$_2$ (and $\sim$ few $10^{-3}$ M$_{\oplus}$ of CO) for a primordial gas disk and $\gtrsim 10^{-3}$ M$_{\oplus}$ of CO (depending on the CO production rate) for cometary gas to explain the observed emission. While the above estimates are informative, the emission is quite sensitive to the various simplifying assumptions made; the disk temperature structure and CO photo-chemistry need to be solved for a more accurate determination of the disk mass and to infer implications for the origin scenarios. Moreover, CO is likely optically thick at these estimated densities affecting the interpreted mass.

We next use thermochemical models (see Appendix B) that solve for gas temperature and chemistry, consider gas line emission with non-LTE radiative transfer and fit the observed $^{12}$CO(2-1) line emission to calculate disk masses.

## Modeling gas of primordial origin

In these models, we assume typical values for all input parameters and only vary the gas mass to match the observed CO emission. We set initial disk elemental abundances as in the interstellar medium(cite: jenkins2009). These values are typical of protoplanetary disk gas with the elemental C abundance relative to H equal to $1.4\times10^{-4}$. The dust mass, grain size and radial extent are from the SED modeling of (cite: Lieman2016). The dust distribution is kept fixed. We adopt double power laws to describe the surface density distribution of gas, $$\begin{equation}
\Sigma(r)=\begin{cases}
\Sigma_0 \big( \frac{r}{R_{0}}\big)^{p_{1}} \quad \phantom{\infty}\text{for}\,\, R_{min}<r<R_0   \\
\Sigma_0 \big( \frac{r}{R_{0}}\big)^{p_{2}} \quad \phantom{\infty}\text{for}\,\, R_{0}<r<R_{max} \\
      \end{cases}
      \label{eqn14}
\end{equation}$$ where $\Sigma_0$ is the surface density at $R_0$. We vary the surface density distribution of gas, and set the local gas/dust mass ratio accordingly. From the Lucy-Richardson modeling, the inclination and radial extent of the gas disk is also constrained and the only free parameters are the radial dependence of the surface density profile and the integrated gas mass of the disk. We note that while the Lucy-Richardson modeling gives the emissivity profile, this does not directly correspond to a surface density, especially when the CO emission becomes optically thick. Gas heating, cooling and chemistry that result from the adopted surface density distribution are all then calculated by the models (for model details see Appendix B). The surface density profile ($\Sigma_0,R_0,p_1,p_2$) is then varied as described below until the synthetic model line emission profile matches the observed line emission.

We initially fit the integrated flux by varying the total disk mass in the range 0.1 - 35M$_{\oplus}$ in steps of 5M$_{\oplus}$, to narrow down the mass range. We then fit the spatially integrated velocity line profile by varying the disk mass in increments of 0.1M$_{\oplus}$, and then select the best fit models for a more detailed analysis as follows. The surface density exponents p$_1$ and p$_2$ were varied manually between -5 and +5 using different step sizes, and then fine-tuned using steps of 0.05.

The model data is used to generate synthetic CO line emission data cubes using LIME (cite: brinch2010), with non-LTE radiative transfer and considering o-H$_2$, p-H$_2$, H and $e^-$ as collision partners (cite: Dickinson1977; yang2010; walker2015). The synthetic data cubes are then processed through CASA[^1] version 5.1.0 (cite: 2007ASPC..376..127M) to compare emission in each velocity channel. The model images were processed through the CASA task simobserve to create synthetic visibilities, using the same integration time, spectral setup and antenna configuration used for the observations as well as injecting the appropriate amount of thermal noise. The resulting model visibilities were then imaged using the same clean parameters used for the real data.

The integrated spectra for the best fit models are compared to the $^{12}$CO(2–1) data in Figure [7](#intspec-pa). We obtain total H$_2$ disk masses of 8.1, 7.2 and 10.4 M$_{\oplus}$, and total CO masses of $5.0\times 10^{-3}$,$4.2\times 10^{-3}$ and $3.8\times 10^{-3}$ M$_{\oplus}$ for HD 131835, HD 138813 and HD 156623 respectively. The simulated channel maps for the primordial origin model for HD 138813 are compared to the data in Figure [8](#chanmap-pa-76310).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Star | Model | R$_{0}$ | $\Sigma_0$ | R$_{min}$ | R$_{max}$ | p$_{1}$ | p$_{2}$ |
|  |  | (au) | (g/cm$^2$) | (au) | (au) |  |  |
| HD 131835 | Primordial | 80 | 9.8$\times10^{4}$ | 50 | 250 | -1.5 | -2.5 |
|  | Secondary | 90 | 1.1$\times10^{5}$ | 50 | 250 | -1.0 | -4.0 |
|  |  |  |  |  |  |  |  |
| HD 138813 | Primordial | 65 | 7.5$\times 10^{4}$ | 5 | 210 | -1.5 | -2.7 |
|  | Secondary | 65 | 1.0$\times 10^{5}$ | 5 | 210 | -0.5 | -4.0 |
|  |  |  |  |  |  |  |  |
| HD 156623 | Primordial | 10 | 2.5$\times 10^{3}$ | 5 | 160 | -0.5 | -0.5 |
|  | Secondary | 10 | 9.2$\times 10^{6}$ | 5 | 160 | -0.5 | -0.5 |

: Surface density parameters of primordial and secondary models

Table notes: Surface density distributions correspond to double power laws; $\Sigma(r)=\Sigma_0 (r/R_0)^{p_1}$ for $R_{min}<r<R_0$ and $\Sigma(r)=\Sigma_0 (r/R_0)^{p_2}$ for $R_{0}<r<R_{max}$. Here $\Sigma(r)$ refers to the total mass surface density of all species.

Heating, cooling and photochemistry in the disk around HD 138813 are described in more detail below; the other two disks are similar in their chemical and physical structure and not discussed. Heating mechanisms considered include collisions with dust, X-rays and cosmic rays, UV grain heating, H$_2$ vibrational heating, H$_2$ formation heating, exothermic chemical reactions and photo-reactions such as the ionization of carbon; cooling is by dust collisions, and several ionic, atomic and molecular lines. Since disk mass is being inferred using only the CO J=2-1 line, we need only concern ourselves with heating in the regions where CO resides. None of the three stars have any detected X-rays, we therefore assumed an X-ray luminosity of $10^{27}$ erg s$^{-1}$, typical of A stars (cite: Feigelson2011). At this level, X-rays do not contribute significantly to the heating. Dust collisions are important in the regions with dust (73-161 au for HD 138813). At typical model gas densities, drag may be sufficient to retain dust grains smaller than the blow-out size (see Appendix C), but we do not consider any small dust population that can be retained to heat the gas (cite: Lieman2016). We assume that a small fraction ($<$1%) of the grains are spatially co-located with the gas outside the main dust belt (this may be possible because of gas drag). We note that such small amounts of dust are still consistent with the SED fitting used to determine dust parameters. Photoelectric grain heating (due to FUV photons) in the absence of very small grains and Polycyclic Aromatic Hydrocarbons (PAHs) is not very significant, and here dust heating is only due to relatively large $\sim 1\mu$m grains (cite: Kamp2001). The other main heating mechanisms are UV pumping, H$_2$ formation and cosmic rays (we use $\zeta_{CR}\sim
10^{-16}$ s$^{-1}$). The cosmic ray rate in the Galaxy could be as high as $10^{-15}$ s$^{-1}$ (cite: Indriolo2012; Neufeld2017). If we assume $\zeta_{CR} \gtrsim 10^{-16}$ s$^{-1}$, then cosmic ray heating typically dominates gas heating. In this case, cosmic rays provide the necessary heating (to excite the CO line) and there is no need to assume that there is any small dust that gets dragged along with the gas. Figure [9](#heat) shows the dominant heating in the disk multiplied by the CO number density to emphasize the regions where CO is present. The main coolants in the disk are CO rotational emission and \[OI\] fine structure emission. The resulting temperature and density structure is shown in Figure [10](#disksDensTemptructure). The gas surface density parameters of the best fit models are presented in Table [\[plaws\]](#plaws).

![](fig9.pdf)

Heating by dust in the $67-147$ au region results in an increase in the temperature and therefore higher pressure leading to a more vertically extended disk. Outside the dust belt, the gas temperature is quite low, and in general insufficient to excite the J=2–1 line of CO in the outer disk.

Since the primordial origin disk is optically thick in CO, the resulting emission is relatively insensitive to mass and depends on the disk temperature structure. Uncertainties in disk heating mechanisms translate to the calculated gas temperature, and could potentially result in different disk mass estimates for the same line emission flux. However, the disk mass also affects the chemistry and the amount of CO in the disk. H$_2$, CH, C and CO have significant cross-sections in the 11.3-13.6eV energy range and absorb incident UV flux to shield and preserve CO deeper in the disk, with H$_2$ shielding being the most effective. As discussed earlier, the column densities required are such that the implied masses for CO to survive are high. An additional complication is the paucity of dust in the disk. We assumed that there was dust at the 1% level distributed through the disk; not only does this provide some additional heating to raise the gas temperature outside the dust belt, but also enables formation of molecular hydrogen that can shield CO. Increasing this dust fraction affects the SED-fitting, while lowering it increases the required mass due to inefficient H$_2$ formation (and CO-shielding). As discussed previously, increasing the cosmic ray ionization rate could also lead to more gas heating. Therefore, although we could drive the disk to lower masses with an increase in gas temperature especially in the outer disk and still reproduce the observed emission, the limiting mass necessary for self-shielding makes it very unlikely that the primordial disk mass can be significantly lower than calculated from the models.

Disk masses higher than derived from the modeling are not ruled out. Decreasing the heating in the disk, for example, by lowering the cosmic ray rate and/or reducing the dust density, lowers the gas temperature (note that increasing the gas mass reduces the effective cross-section of dust per H nucleus and decreases the gas temperature even as the dust mass is unchanged). Lower temperatures in a more massive disk are consistent with the observed emission as well, and this degeneracy cannot be broken with only one CO transition observed.[^2] However, disk masses cannot be considerably higher than derived here because then the densities become high enough for gas drag to prevent radiation pressure from removing grains in the debris collisional cascade, (see Appendix C). Lack of removal of grains (which is size-independent as both forces depend on grain area) will result in an accumulation of small grains making the dust disk optically thick and inconsistent with the debris disk classification.

## Modeling gas of secondary origin

In the cometary model, CO may be released by thermal and UV desorption of ices from dust grains (cite: grigorieva2007), or by high velocity impacts of larger bodies (cite: zuckerman2012). In the latter case, the heat generated by the impact would release CO into the gas phase, and the initial temperature of the CO gas would be set by the energetics of the collision which heat the gas. If CO is sublimated from dust, the gas that is released is expected to be approximately at the temperature of the dust grain. After desorption, the gas will initially expand and cool adiabatically and radiatively and will be heated further out in the flow by photo and chemical processes (cite: rodgers2002). A full and accurate treatment of the gas temperature requires a chemo-dynamical model, possibly including impact collision modeling, and is beyond the scope of this work. Here for simplicity, we assume that the gas temperature is equal to the local dust temperature. However, we fully solve for the chemical evolution of the gas; we assume that at the start of the simulation CO and H$_2$O are released in a 1:10 ratio (cite: mumma2011), and our initial abundances are such that all the gas is in CO and H$_2$O. We consider different initial surface density distributions of the gas and solve for time-dependent chemical evolution of the disk after the CO and H$_2$O are released. We use the same chemical network as described in Appendix B, but now only solve for the dust temperature and set the gas temperature equal to it. For low initial surface densities, molecules are rapidly photodissociated unless there is a sufficient self-shielding. The disk surface density at $t=0$ is increased to a point where a column of CO is built up that can explain the observed CO emission. We typically run the chemical model up to times of  2 Myr. The best fit cometary gas masses are $4.6 \times 10^{-3},
 3.1\times 10^{-3}$ and $2.45\times 10^{-3}$ M$_{\oplus}$ for CO alone (with total gas content being $\sim 15$ higher) for the disks around HD 131835, HD 138813 and HD 156623. The CO masses derived are higher than the minimum mass optically thin estimate, and almost meet the mass needed for LTE. The temperature of the gas is higher than $\sim
 20$K through most of the disk, and in the outer disk, densities are low enough that n-LTE conditions (collisions with neutrals and electrons) result in sub-thermal emission. The gas surface density parameters of the best fit models are presented in Table [\[plaws\]](#plaws).

Figure [11](#intspec-ca) compares the integrated spectra for best fit models of cometary origin to the $^{12}$CO(2–1) data (cite: Lieman2016). The models have been used to generate synthetic spectra using LIME, and then through CASA to produce simulated visibilities and channel map images comparable to the $^{12}$CO(2–1) ALMA data. The simulated channel maps from the secondary origin model for HD 138813 are compared to the data in Figure [12](#chanmap-ca-76310).

As pointed out by previous studies (cite: zuckerman2012; Kospal13; Dent2014; kral2017), simple estimates suggest that CO survival against photodissociation is limited to $\sim 120$ years; a continuous replenishment of CO by cometary collisions or outgassing is therefore needed to explain the observed emission. For the best fit disk masses, the CO column densities are high enough ($10^{16-17}$ cm$^{-2}$ at $\sim 80$au) for self-shielding of CO and shielding by other C-species to reduce the photodissocation rate by $\sim$ 2 orders of magnitude. The CO photo-dissociation rate in the disk is moreover not constant, and can decrease in time due to an increase in the gas opacity (cite: kral2018) built up in the disk as CO is destroyed with time (which however also reduces self-shielding), and this can be calculated from the chemical disk model. CO is also re-formed in the gas phase due to the abundance of O-species (from the destruction of H$_2$O) which further lowers the net CO destruction rate. In order to maintain a column of gas that can shield CO against UV photons, the production rate needs to be equal to the net destruction rate. We estimate this by considering the initial mass of the disk (at $t=0$), the timescale $t_f$ taken to reach the final mass of CO needed to explain the emission, and therefore the production rate $\sim (M(t=0) - M(t_f))/t_f$. Models with higher initial disk masses lead to higher $t_f$ as is to be expected, and give approximately the same production rates. We note that disks with total gas masses (including water released by collisions) of $\sim 4
\times 10^{-2}$  M$_\oplus$ are needed to obtain CO masses $\sim 3\times
10^{-3}$ as derived here, and imply a replenishment rate of $\sim
1.6\times 10^{14}$ g s$^{-1}$ ($8\times 10^{-7}$ M$_{\oplus}$ yr$^{-1}$) to retain the minimum mass of CO needed. Given that to capture the true evolution of the secondary gas disk, one needs to consider chemistry with hydrodynamical flow, we do not attempt any more detailed estimates of the production rate.

# Discussion

Based on the above modeling of the CO J=2-1 line alone, we find that both the primordial and cometary disk scenarios are seemingly consistent with the ALMA data.

Primordial gas indicates the survival of small amounts of H$_2$ gas long past the main planet formation epochs. While current theories of disk evolution (cite: Alexander2014; Gorti2015) predict a very rapid inside-out dispersal of the entire disk when the disk masses become too low, it is nevertheless possible for disk lifetimes to exceed the $\sim 2\times10^7$ year system ages if the disks have a very low viscosity and low mass loss rates. If disk evolution proceeds such that by a few Myr, most of the dust has been incorporated into larger bodies including planets, leaving $10^{-2}$ M$_{\oplus}$ masses of dust and nearly 1000 times as much gas, the low abundances of small dust (cite: Alexander2014; Gorti2015), and the low X-ray luminosities of these stars may result in the disk surviving to the so-called hybrid stage. However, we argue that such a scenario is unlikely. As shown in Appendix C, for disks with masses $\gtrsim
5$M$_{\oplus}$, gas densities become too high, and collisional coupling of gas and dust grains due to gas drag becomes important. For secondary dust generated by collisions, small dust grains in the cascade are retained and would quickly render the disk optically thick. These disks would then no longer be classified as debris disks. All three disks modeled here are estimated to have larger H$_2$ masses (a few tens of M$_{\oplus}$) in the primordial scenario and are therefore inconsistent with the hybrid disk picture. A similar conclusion on the effects of gas drag was recently made (cite: kral2018) even for disks of secondary origin, and hence considerably lower mass. Further, a primordial origin for disks

does not explain why most of the CO-bright debris disks should be preferentially detected around stars lying within a relatively narrow range of spectral type and mass (cite: pericaud2017).

We prefer the secondary origin scenario for the three disks in this study, as also argued by (cite: kral2017; kral2018). The partial co-location of both gas and dust in 2 out of the 3 targets argues in favor of a cometary origin for the gas. The gas surface density distribution we derive for HD 131835 is consistent with that obtained from MCMC fits to CI data (cite: kral2018), where most of the emission is confined to a ring located at $\sim$90 au with a 80 au width. (cite: kral2018) further constrain the range of allowed masses by considering the CO mass derived by (cite: moor2017) using observations of the optically thin C$^{18}$O(3-2) line, which is dependent on other assumptions in their model on viscous spreading and gas production scenarios. The CO gas mass that we derive for the cometary production for HD 131835 is about an order of magnitude lower, but we note the CI line optically thick and hence more sensitive to temperature than mass. It is likely that the gas temperature is closer to the CO thermal desorption temperature of $\sim 20$K and not as high as the dust temperature as we have assumed; in this case the inferred CO masses can be higher. In future work, we plan a multi-line analysis that includes isotope chemistry and a thermal balance calculation to better constrain the mass of the cometary gas disk.

For the CO mass estimated, we find that the required replenishment rates are only slightly higher than that for $\beta$ Pic; (cite: Dent2014) estimate $2.3\times 10^{-7}$ M$_{\oplus}$ yr$^{-1}$ whereas the implied rate of production for these debris disks is about a factor of a few higher. Note that if the CO gas temperature is lower than the dust temperature, and instead close to the grain thermal desorption value of 20K, then the required production rate is $1.6\times 10^{-7}$ M$_{\oplus}$ yr$^{-1}$ and lower than that for $\beta$ Pic. Our rates are also in reasonable agreement with (cite: kral2018), despite the differences in modeling approach (they do not explicitly solve for the chemistry or ionization, while we do not consider viscous spreading or include a production rate in our models).

(cite: kral2018) propose that accumulation of atomic carbon over time results in a layer that shields CO, and that dissociated CO piles up as atomic carbon prolonging the lifetime of CO. Although we do consider the effects of molecular gas opacity and self-shielding in our models and, contrary to (cite: kral2018), further solve the chemical network to model the CO emission, we do not consider the viscous time evolution of the disk.

We however also find that solving for disk chemistry results in CO lifetimes that are long enough to somewhat mitigate the issue of high cometary collision rates previously inferred. It is possible that the true CO production rate required is even lower that what we estimate because of the following. The photodissociation rate of CO is sensitive to the column density profile which determines the self-shielding and gas opacity factors; a clumpy distribution of outgassing comets is likely to be more effective at shielding CO. Gas is also likely to entrain smaller dust particles than considered here, which are more efficient at attenuating UV photons, reducing the destruction of CO even further.

The fact that the dust and CO gas disks are only partially co-located in the disks may weaken the secondary origin scenario (Figure [6](#diskradii)), unless the CO disk viscously spreads after it has been generated (cite: matra2017a). If disks are indeed MRI-active and accrete efficiently (cite: kral2016), then the viscous timescales could be short enough that the gas disk does not remain co-spatial with the dust on release (cite: kral2018).

Interestingly, the stellar spectral types are such that the UV flux in the energy range required for desorption (cite: Fayolle2011) is high relative to the energy range ($11.26-13.6$ eV) required for CO photodissociation. For later spectral types, there are not enough photons to desorb CO while for earlier spectral types there are too many that dissociate CO. However, a normal interstellar field (Habing field G$_0=1$, compared to G$_0=2000$ at 1au for HD 138813) begins to dominate at $r>45$ au and unless these disks are in an unusually low ambient UV field ($G_0<0.2$), the change in stellar photon flux going from $\sim 8$ eV to $\sim 11$eV may not be that important. Debris disks are however quite dusty, and scattering of UV photons even at $\sim 1-2$% efficiency (ignored in this paper) could keep the stellar radiation field dominant out to $\sim 100$ au where the gas is located. While gas around an M dwarf was recently detected by (cite: matra2019) who suggest that higher CO production rates from collisional cascades for more luminous stars coupled with sensitivity issues may be responsible for the CO detection bias, the ultraviolet spectrum may play an additional role. The UV spectra of M dwarfs are often flare-driven and the flare spectra are in fact found to resemble A star spectra (cite: kowalski2013).

# Conclusions

We have applied the Lucy-Richardson deconvolution technique to derive the $^{12}$CO(2–1) surface brightness distribution around three gas rich debris disks detected with ALMA. The derived disk parameters in conjunction with detailed thermochemical models are used to test whether the observed gas is a primordial fossil from the protoplanetary disk phase, or produced by cometary collisions. We find that while both scenarios can reproduce the observed emission, the primordial scenario is unlikely. We conclude that gas drag may dominate small dust dynamics at the few tens of M$_{\oplus}$ disk masses of H$_2$ needed to explain the observed CO emission, and that this small dust would not keep a primordial disk optically thin in continuum emission as observed. Several lines of reasoning favor the secondary origin scenario: in at least 2 of the 3 disks observed, the gas and dust are spatially co-located, the production rates we derive are only slightly higher than those derived in disks of clear secondary origin such as $\beta$ Pic, and the different photon energies needed for desorption and photodissociation may explain the higher detection rates of gas around A stars.

# Acknowledgments

We thank the anonymous referee for reading the paper carefully and providing thoughtful comments which improved the quality of this publication. JMC acknowledges support from the National Aeronautics and Space Administration under Grant No. 15XRP15-20140 issued through the Exoplanets Research Program. AMH acknowledges support from NSF grant AST-1412647. UG was supported by NASA grants NNH13ZDA017C (NAI CAN 7) and NNX14AR91G (Astrophysics Data Analysis Program). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00688.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

# Software

Common Astronomy Software Applications (cite: 2007ASPC..376..127M), LIME (cite: brinch2010), Astropy (cite: 2013A&A...558A..33A), EMCEE (cite: foreman2013)

(ref: Alexander2014) Alexander, R., Pascucci, I., Andrews, S., Armitage, P., & Cieza, L. 2014, Protostars and Planets VI, 475

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, AA33

(ref: aumann1984) Aumann, H. H., Gillett, F. C., Beichman, C. A., et al. 1984, ApJL, 278, L23

(ref: booth2016) Booth, M., Jordán, A., Casassus, S., et al. 2016, MNRAS, 460, L10

(ref: brinch2010) Brinch, C., & Hogerheijde, M. R. 2010, A&A, 523, A25

(ref: carpenter2006) Carpenter, J. M., Mamajek, E. E., Hillenbrand, L. A., & Meyer, M. R. 2006, ApJL, 651, L49

(ref: cataldi2018) Cataldi, G., Brandeker, A., Wu, Y., et al. 2018, ApJ, 861, 72

(ref: dahm2009) Dahm, S. E., & Carpenter, J. M. 2009, AJ, 137, 4024

(ref: dent2005) Dent, W. R. F., Greaves, J. S., & Coulson, I. M. 2005, MNRAS, 359, 663

(ref: Dent2014) Dent, W. R. F., Wyatt, M. C., Roberge, A., et al. 2014, Science, 343, 1490

(ref: Dickinson1977) Dickinson, A. S., Phillips, T. G., Goldsmith, P. F., Percival, I. C., & Richards, D. 1977, A&A, 54, 645

(ref: Fayolle2011) Fayolle, E. C., Bertin, M., Romanzin, C., et al. 2011, ApJL, 739, L36

(ref: Feigelson2011) Feigelson, E. D., Getman, K. V., Townsley, L. K., et al. 2011, ApJS, 194, 9

(ref: feldt2017) Feldt, M., Olofsson, J., Boccaletti, A., et al. 2017, A&A, 601, A7

(ref: foreman2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: Gong2017) Gong, M., Ostriker, E. C., & Wolfire, M. G. 2017, ApJ, 843, 38

(ref: Glassgold1997) Glassgold, A. E., Najita, J., & Igea, J. 1997, ApJ, 480, 344

(ref: Gorti2004) Gorti, U., & Hollenbach, D. 2004, ApJ, 613, 424

(ref: Gorti2008) Gorti, U., & Hollenbach, D. 2008, ApJ, 683, 287

(ref: Gorti2011) Gorti, U., Hollenbach, D., Najita, J., & Pascucci, I. 2011, ApJ, 735, 90

(ref: Gorti2015) Gorti, U., Hollenbach, D., & Dullemond, C. P. 2015, ApJ, 804, 29

(ref: greaves2016) Greaves, J. S., Holland, W. S., Matthews, B. C., et al. 2016, MNRAS, 461, 3910

(ref: grigorieva2007) Grigorieva, A., Thébault, P., Artymowicz, P., & Brandeker, A. 2007, A&A, 475, 755

(ref: habing1968) Habing, H. J. 1968, , 19, 421

(ref: hales2014) Hales, A. S., De Gregorio-Monsalvo, I., Montesinos, B., et al. 2014, AJ, 148, 47

(ref: hernandez2005) Hernández, J., Calvet, N., Hartmann, L., et al. 2005, AJ, 129, 856

(ref: Hollenbach2009) Hollenbach, D., & Gorti, U. 2009, ApJ, 703, 1203

(ref: Hollenbach1979) Hollenbach, D., & McKee, C. F. 1979, ApJS, 41, 555

(ref: hughes2008) Hughes, A. M., Wilner, D. J., Kamp, I., & Hogerheijde, M. R. 2008, ApJ, 681, 626-635

(ref: Hughes2010) Hughes, A. M., Wilner, D. J., Andrews, S. M., Qi, C., & Hogerheijde, M. R. 2011, ApJ, 727, 85

(ref: hughes2018) Hughes, A. M., Duchêne, G., & Matthews, B. C. 2018, ARA&A, 56, 541

(ref: hung2015a) Hung, L.-W., Fitzgerald, M. P., Chen, C. H., et al. 2015, ApJ, 802, 138

(ref: hung2015b) Hung, L.-W., Duchêne, G., Arriaga, P., et al. 2015, ApJL, 815, L14

(ref: Indriolo2012) Indriolo, N., & McCall, B. J. 2012, ApJ, 745, 91 (ref: isella2009) Isella, A., Carpenter, J. M., & Sargent, A. I. 2009, ApJ, 701, 260

(ref: jenkins2009) Jenkins, E. B. 2009, ApJ, 700, 1299

(ref: jewitt1996) Jewitt, D., Luu, J., & Chen, J. 1996, AJ, 112, 1225

(ref: Kamp2001) Kamp, I., & van Zadelhoff, G.-J. 2001, A&A, 373, 641

(ref: kowalski2013) Kowalski, A. F., Hawley, S. L., Wisniewski, J. P., et al. 2013, ApJS, 207, 15

(ref: kral2016) Kral, Q., & Latter, H. 2016, MNRAS, 461, 1614

(ref: kral2017) Kral, Q., Matrà, L., Wyatt, M. C., & Kennedy, G. M. 2017, MNRAS, 469, 521

(ref: kral2018) Kral, Q., Marino, S., Wyatt, M. C., Kama, M., & Matra, L. 2018, arXiv:1811.08439

(ref: Kenyon08) Kenyon, S. J., & Bromley, B. C. 2008, ApJS, 179, 451

(ref: Kospal13) Kóspál, Á., Moór, A., Juhász, A., et al. 2013, ApJ, 776, 77

(ref: Lieman2016) Lieman-Sifry, J., Hughes, A. M., Carpenter, J. M., et al. 2016, ApJ, 828, 25

(ref: loomis2017) Loomis, R. A., Öberg, K. I., Andrews, S. M., & MacGregor, M. A. 2017, ApJ, 840, 23

(ref: Lyons2005) Lyons, J. R., & Young, E. D. 2005, Nature, 435, 317

(ref: lucy1974) Lucy, L. B. 1974, AJ, 79, 745

(ref: mannings1998) Mannings, V., & Barlow, M. J. 1998, ApJ, 497, 330

(ref: marino2016) Marino, S., Matrà, L., Stark, C., et al. 2016, MNRAS, 460, 2933

(ref: marino2017) Marino, S., Wyatt, M. C., Panić, O., et al. 2017, MNRAS, 465, 2595

(ref: mathews2012) Mathews, G. S., Williams, J. P., Ménard, F., et al. 2012, ApJ, 745, 23

(ref: mathews2013) Mathews, G. S., Pinte, C., Duchêne, G., Williams, J. P., & Ménard, F. 2013, A&A, 558, A66

(ref: matra2015) Matrà, L., Panić, O., Wyatt, M. C., & Dent, W. R. F. 2015, MNRAS, 447, 3936

(ref: matra2017a) Matrà, L., Dent, W. R. F., Wyatt, M. C., et al. 2017, MNRAS, 464, 1415

(ref: matra2017b) Matrà, L., MacGregor, M. A., Kalas, P., et al. 2017, ApJ, 842, 9

(ref: matra2019) Matrà, L., Öberg, K. I., Wilner, D. J., Olofsson, J., & Bayo, A. 2019, AJ, 157, 117

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: moor2011) Moór, A., Ábrahám, P., Juhász, A., et al. 2011, ApJL, 740, L7

(ref: moor2015) Moór, A., Henning, T., Juhász, A., et al. 2015, ApJ, 814, 42

(ref: moor2017) Moór, A., Curé, M., Kóspál, Á., et al. 2017, ApJ, 849, 123

(ref: mumma2011) Mumma, M. J., & Charnley, S. B. 2011, ARA&A, 49, 471

(ref: Neufeld2017) Neufeld, D. A., & Wolfire, M. G. 2017, ApJ, 845, 163

(ref: Oudmaijer1992) Oudmaijer, R. D., van der Veen, W. E. C. J., Waters, L. B. F. M., et al. 1992, A&AS, 96, 625

(ref: pecaut2012) Pecaut, M. J., Mamajek, E. E., & Bubar, E. J. 2012, ApJ, 746, 154

(ref: pericaud2017) Péricaud, J., Di Folco, E., Dutrey, A., Guilloteau, S., & Piétu, V. 2017, A&A, 600, A62

(ref: Rebollido) Rebollido, I., Eiroa, C., Montesinos, B., et al. 2018, A&A, 614, A3

(ref: richardson1972) Richardson, W. H. 1972, Journal of the Optical Society of America (1917-1983), 62, 55

(ref: rizzuto2011) Rizzuto, A. C., Ireland, M. J., & Robertson, J. G. 2011, MNRAS, 416, 3108

(ref: roccatagliata2009) Roccatagliata, V., Henning, T., Wolf, S., et al. 2009, A&A, 497, 409

(ref: rodgers2002) Rodgers, S. D., & Charnley, S. B. 2002, MNRAS, 330, 660

(ref: scoville1983) Scoville, N. Z., Young, J. S., & Lucy, L. B. 1983, ApJ, 270, 443

(ref: Slettebak1975) Slettebak, A. 1975, ApJ, 197, 137

(ref: smith84) Smith, B. A., & Terrile, R. J. 1984, Science, 226, 1421

(ref: stock2015) Stock, D., Meyer, S., Sarli, E., et al. 2015, A&A, 584, A63

(ref: tazzari2016) Tazzari, M., Testi, L., Ercolano, B., et al. 2016, A&A, 588, A53

(ref: thureau2014) Thureau, N. D., Greaves, J. S., Matthews, B. C., et al. 2014, MNRAS, 445, 2558

(ref: trujillo2001) Trujillo, C. A., Jewitt, D. C., & Luu, J. X. 2001, AJ, 122, 457

(ref: visser2009) Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323

(ref: walker2015) Walker, K. M., Song, L., Yang, B. H., et al. 2015, ApJ, 811, 27

(ref: Wyatt2007) Wyatt, M. C., Smith, R., Su, K. Y. L., et al. 2007, ApJ, 663, 365

(ref: wyatt2008) Wyatt, M. C. 2008, ARA&A, 46, 339

(ref: wyatt2015) Wyatt, M. C., Panić, O., Kennedy, G. M., & Matrà, L. 2015, Ap&SS, 357, 103

(ref: yang2010) Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C. 2010, ApJ, 718, 1062

(ref: zech2013) Zech, G. 2013, Nuclear Instruments and Methods in Physics Research A, 716, 1

(ref: zorec2016) Zorec, J., Frémat, Y., Domiciano de Souza, A., et al. 2016, A&A, 595, A132

(ref: zuckerman95) Zuckerman, B., Forveille, T., & Kastner, J. H. 1995, Nature, 373, 494

(ref: zuckerman2012) Zuckerman, B., & Song, I. 2012, ApJ, 758, 77

# Lucy-Richardson MCMC results for HD 131835 and HD 156623

Figures [13](#fig_corner_73145) and  [14](#fig_corner_84881) show the MCMC results from the Lucy-Richardson deconvolution for HD 131835 and HD 156623 (Section  [3.3](#modelling)). Figures [15](#fig:hd73145-residual) and  [16](#fig:hd84881-residual) show the comparison between the corresponding best-fit models and the ALMA data.

# Thermochemical model details

The disk models used here were first developed for modeling gas in debris disks (cite: Gorti2004) and later extended to apply to all gaseous protoplanetary disks in general (cite: Gorti2008; Hollenbach2009; Gorti2011; Gorti2015). We briefly summarize the main aspects of the models here and refer the reader to the original papers for more details.

The models assume azimuthal symmetry and solve for the density and temperature structure and chemistry in a self-consistent iterative manner, and calculate the gas and dust temperatures separately. They include heating, photoionization and photodissociation of gas species due to EUV, FUV, X-rays and cosmic rays, thermal energy exchange by gas-dust collisions, grain photoelectric heating of gas by FUV incident on PAHs and very small grains, and heating due to UV pumping of H$_2$ and exothermic chemical reactions. Cooling of gas is by line emission from ions, atoms and moleules. The chemical network is constructed to include the chemistry of the main gas cooling species, $\sim 120$ species made of H, He, C, N, O, Ne, S, Mg, Fe, Si and Ar with $\sim$ 800 chemical and photochemical reactions (cite: Gorti2011). Grain surface chemistry is not treated explicitly, it is assumed that ices form at grain temperatures below the freeze-out temperatures of relevant species (e.g., CO, H$_2$O, CH$_4$) and include thermal desorption and photodesorption.

Gas and dust are treated independently and the models allow for their different spatial distributions. A mixture of dust chemical compositions and a range of grain size distributions can be treated. Here we have assumed that all dust is comprised of silicates and the grain size distribution is determined from the SED fitting (cite: Lieman2016). Gas opacities at each spatial location $(r,z)$ are calculated by dividing the FUV band into 9 bins including Lyman alpha, and absorption cross sections in each band are calculated by integrating the stellar spectrum with the photo-cross sections from the LAMDA[^3] database for all available chemical species. Dust radiative transfer is usually treated using a 1+1D construct, but is simple for the optically thin disks modeled here. Line radiative transfer (for calculating cooling in the thermochemical models) uses an escape probability formalism, explicitly computes the level populations of all coolants and is a full, non-LTE treatment. We note that the model results in this work are subsequently processed through the nLTE code LIME to generate emission maps for comparison with the ALMA data.

The main model inputs are the stellar parameters (mass, spectrum, high energy flux), the dust disk parameters (constrained by the continuum emission and SED fitting) and the gas surface density distribution. Since the former are known or previously determined, the surface density distribution, and hence mass, is the only variable in our modeling. Each profile thus generates a unique disk density, temperature and chemical density distribution as a function of spatial location $(r,z)$; this is then compared with the ALMA data to find the best fit model disk mass.

# Drag force vs radiation pressure

Assuming an infinite collisional cascade as in (cite: Wyatt2007) with sizes ranging from the smallest sub-micron dust to km sizes, the resulting grain size distribution is such that the area/mass ratio is highest in the smallest grains. In a debris disk devoid of gas, the smallest grains are subject to removal by radiation pressure. In the presence of gas, however, the increased collisional coupling of small grains to gas molecules could result in their retention (in disks around A-stars, gravity begins to be become important for grains larger than $\sim 5\mu m$, e.g., (cite: wyatt2008)). For gas drag to be larger than radiation pressure, $$\begin{equation}
\frac{8\sqrt{2}\pi}{3} \rho_{gas} a^2 c_s \Delta v >
 \frac{L_* Q a^2}{4 \pi r^2 c}
\end{equation}$$ where the term on the left is the Epstein drag force and the right term is the force due to radiation pressure. Here, $\rho_{gas}, c_s$ are the gas density and thermal speed, $a$ is the grain size, $Q$ its absorption coefficient, $L_*$ the stellar luminosity, $r$ the distance to the star and $c$ the speed of light. Note that both forces depend on the grain area. Assuming that the relative velocity between the gas and dust $\Delta v \sim c_s$, and that $Q\sim 1$, the number density required for retaining collisionally generated dust is $$\begin{equation}
n_{gas} (r) > 1.4\times 10^{10} \left(\frac{{\rm au}}{r}\right)^2 \left(\frac{20\ {\rm K}}{T_{gas}}\right) \left(\frac{L_*}{10 L_{\odot}}\right) \ {\rm \ cm}^{-3}
\end{equation}$$ While $Q\sim1$ is valid for micron-sized grains at wavelengths where the stellar flux dominates, smaller sub-micron grains may have smaller values of $Q$ and may be retained at densities lower than above. The density can be easily integrated to give required dust masses ($M_{disk} = \int 2\pi r dr \int dz\ \rho_{gas}$) for disks of $\sim 200$ au radii as in the present sample and by assuming a vertical extent $h/r\sim 0.1$; we therefore estimate that primordial disks with masses $M_{disk} \gtrsim 5$M$_{\oplus}$ of H$_2$ will begin to retain small dust grains as they are not removed by radiation pressure and remain collisionally coupled to the gas. The dust generated by collisional cascades in such massive disks would accumulate until the disk becomes optically thick, and they would no longer resemble debris disks.

[^1]: <http://casa.nrao.edu/>

[^2]: Non-detections of \[OI\] and \[CII\] with Herschel PACS (cite: mathews2013; moor2015) are not very useful constraints on disk mass, as the flux upper limits are a factor of $\sim$ 100 or more higher than calculated fluxes from the best-fit models for these lines.

[^3]: Leiden Atomic and Molecular Database, https://home.strw.leidenuniv.nl/ moldata/

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "free: PA, inclination, v_r, offsets; stop when reduced chi2<1 or change <1%",
  "failed_quote": "We iterate Equation [\\ref{eqn11}] until the reduced $\\chi^2$ reaches a value less than unity or when the fractional change in the reduced $\\chi^2$ is less than 1$\\%$"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "manual grid fit to integrated spectra and channel maps",
  "failed_quote": "(no quote given)"
 }
]
```
