# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019A%26A...627A..53H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The Close AGN Reference Survey (CARS).

# Introduction

Quantifying the direct impact of active galactic nuclei (AGN) for galaxy evolution across cosmic time remains one of the big observational challenges. The enormous energy released by AGN has long been thought to suppress star formation through dissipation of their energy in the interstellar medium of their host galaxies (cite: Silk:1998; King:2003; Gaspari:2017b). Indeed, state-of-the-art numerical simulations and analytic models require some sort of energetic AGN feedback mechanisms in order to reproduce observed galaxy properties at the high-mass end (cite: Benson:2003; Bower:2006; Cattaneo:2006; Croton:2006; Somerville:2008; Dave:2011; Genel:2014; Crain:2015). In those models, AGN feedback is often separated into a “radio mode” (also known as “maintenance mode") and a ”quasar-mode“ (”ejective mode"). The radio-mode AGN feedback describes the dissipation of mechanical energy from powerful radio jets. The energy heats the hot gas in halos of galaxies or galaxy groups/clusters such that condensation of gas is prevented and only a low cold gas content is maintained, limiting the ability for ongoing star formation. This mode of AGN feedback has been well established observationally in massive galaxy clusters and groups that host radio galaxies at their centers (cite: Fabian:2012; Gaspari:2013). The quasar-mode feedback instead is thought to remove a significant fraction of the gas from host galaxies of luminous AGN through fast radiatively-driven winds released from the accretion disc (cite: Feruglio:2015; Tombesi:2015; Bieri:2017).

Evidence for fast winds exceeding 10 000 $\mathrm{km\,s}^{-1}$ have been observed close to the AGN accretion disc through X-ray and UV spectroscopy (cite: Pounds:2003; Gibson:2009; Tombesi:2010; Tombesi:2010b). Whether those radiatively-driven AGN winds are energetic enough to expand out to galaxy scale is still a matter of great debate and intensive ongoing investigation. In particular, the optical emission lines of the ionized gas phase have been extensively explored because they systematically show blue-shifted broad wings in their line shapes which are most pronounced in the \[O iii\] $\lambda\lambda 4960,5007$ optical emission lines (cite: Heckman:1981; Whittle:1985a; Mullaney:2013; Zakamska:2016; Woo:2016; Harrison:2016b; Bischetti:2017). These asymmetric optical line shapes have been interpreted as a common signature of fast bi-conical AGN-driven outflows where the receding side is obscured by dust from the host galaxy (cite: Pogge:1988a; Bae:2016). Such biconical outflows have indeed been spatially resolved in several nearby AGN host galaxies with *Hubble* (cite: Schmitt:2003b; Crenshaw:2000; Das:2006; Fischer:2013; Revalski:2018) and ground-based spectroscopy (cite: Pogge:1988a; Storchi-Bergmann:1992; Riffel:2013; Cresci:2015b; Mingozzi:2019).

An increasing number of AGN have been targeted either with long-slit or integral-field unit (IFU) spectrographs (cite: Humphrey:2010; Greene:2011; Husemann:2013a; Liu:2013b; Harrison:2014; Husemann:2014; Liu:2014; Carniani:2015; McElroy:2015; Perna:2015; Carniani:2016; Kakkad:2016; Karouzos:2016; Leung:2017; Rupke:2017; Sun:2017; Kang:2018) to spatially map the ionized gas kinematics using the rest-frame optical emission lines. Although there is a clear trend emerging that the \[O iii\] outflow velocity is systematically increasing with AGN luminosity (cite: Fiore:2017; Perna:2017; Woo:2017; DiPompeo:2018), the associated ionized gas kinetic energies can be uncertain by a few orders of magnitude because electron densities $n_\mathrm{e}$ and detailed outflow geometries are usually unconstrained (cite: Harrison:2018). Another uncertain aspect of ionized gas outflows is their physical size. Some studies reported ubiquitous outflow sizes of several kpc scales (cite: Harrison:2014; McElroy:2015; Liu:2013b; Liu:2013), but recently much lower outflow sizes of $<$1 kpc were reported in several studies (cite: Husemann:2016c; Villar-Martin:2016; Tadhunter:2018; Baron:2019). The difference may partially be explained due to the effect of beam smearing in seeing-limited observations (cite: Husemann:2016c).

Furthermore, it has been realized that the cold gas phase may actually dominate the total mass outflow rate budget (cite: Morganti:2005; Feruglio:2010; Cicone:2014; Morganti:2015; Fiore:2017; Veilleux:2017). While many observations have been naturally biased towards gas-rich starburst galaxies hosting AGN (cite: Sturm:2011; Spoon:2013; Veilleux:2013), a more systematic search on cold gas outflows are currently being conducted (cite: Fluetsch:2019). Nevertheless, the investigation of the cold gas phase in AGN host galaxies still lags behind the ionized gas phase as argued in (cite: Cicone:2018), because extinsive multi-wavelength observations are required to obtain the full outflow rate budget in the different gas phases. This limits a robust assessment on the nature of AGN-driven outflows and prevents to distinguish different theoretical predictions of energy-driven or momentum-driven outflows (cite: Ostriker:2010; King:2011; Faucher-Giguere:2012; Costa:2014).

Despite the radio-quiet classification of most AGN being studied so far, they are not radio silent and may host low-luminosity radio jets on various scales from several tens of pc to a few kpc (cite: Kukula:1998; Blundell:1998; Ulvestad:2005; Leipski:2006b; Doi:2013). High turbulent velocities in all gas phases have often been associated even with those low-luminosity jets (cite: Ferruit:1999; Leipski:2006a; Fu:2009; Husemann:2013a; Tadhunter:2014; Villar-Martin:2014; Cresci:2015; Harrison:2015; Villar-Martin:2017) and numerical simulation have shown that even the highly collimated jets can actually lead to large scale outflows when propagating through a clumpy high-density ISM (cite: Sutherland:2007; Wagner:2012; Mukherjee:2018). Usually, outflow energetics are compared to AGN luminosity, jet power, or even star formation rate to determine the powering mechanisms in individual sources. All of these comparisons suffer from systematic measurement uncertainties as summarized by (cite: Wylezalek:2018b). Another complication is that a fast-moving plasma is necessarily creating radio emission itself (cite: Zakamska:2014; Hwang:2018) which may mimic low-luminosity radio jet characteristics.

| Band | Instrument | FoV | Sampling | Beam | $t_\mathrm{exp}$ | $1\sigma$ limit |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| X-ray | *Chandra*/HRC-I | $30\ensuremath{'}\times30\ensuremath{'}$ | 0.13$''$ | 0.4$''$ | 661 min | $1\times10^{-6}$ counts s$^{-1}$ arcsec$^{-2}$ |
| H$\alpha$ | VLT/MUSE | $1\ensuremath{'}\times1\ensuremath{'}$ | 0.2$''$ | $0.7\ensuremath{''}\times0.7\ensuremath{''}$ | 15 min | $5\times10^{-18}\,\mathrm{erg\,s}^{-1}\,\mathrm{cm}^{-2}\mathrm{arcsec}^{-2}$ |
| $[O iii]$ | VLT/MUSE | $1\ensuremath{'}\times1\ensuremath{'}$ | 0.2$''$ | $0.6\ensuremath{''}\times0.6\ensuremath{''}$ | 15 min | $7.5\times10^{-18}\,\mathrm{erg\,s}^{-1}\,\mathrm{cm}^{-2}\mathrm{arcsec}^{-2}$ |
| $J$ band | Gemini-N/NIFS | $3\ensuremath{''}\times3\ensuremath{''}$ | 0.1$''$ | $0.4\ensuremath{''}\times0.4\ensuremath{''}$ | 60 min | $0.3\times10^{-16}\,\mathrm{erg\,s}^{-1}\,\mathrm{cm}^{-2}\mathrm{arcsec}^{-2}$ |
| $K$ band | Gemini-N/NIFS | $3\ensuremath{''}\times3\ensuremath{''}$ | 0.1$''$ | $0.4\ensuremath{''}\times0.4\ensuremath{''}$ | 60 min | $0.8\times10^{-17}\,\mathrm{erg\,s}^{-1}\,\mathrm{cm}^{-2}\mathrm{arcsec}^{-2}$ |
| $B$ | SOAR/SOI | $5.3\ensuremath{'}\times5.3\ensuremath{'}$ | 0.15$''$ | 1.0$''$ | 20 min | 21.9 mag(AB)/pix |
| $V$ | SOAR/SOI | $5.3\ensuremath{'}\times5.3\ensuremath{'}$ | 0.15$''$ | 1.0$''$ | 20 min | 20.9 mag(AB)/pix |
| $R$ | SOAR/SOI | $5.3\ensuremath{'}\times5.3\ensuremath{'}$ | 0.15$''$ | 1.0$''$ | 20 min | 21.5 mag(AB)/pix |
| $J$ | CAHA2.2m/PANIC | $15\ensuremath{'}\times15\ensuremath{'}$ | 0.45$''$ | 1.7$''$ | 76 min | 25.2 mag(AB)/pix |
| $H$ | CAHA2.2m/PANIC | $15\ensuremath{'}\times15\ensuremath{'}$ | 0.45$''$ | 1.5$''$ | 84 min | 24.9 mag(AB)/pix |
| $K_s$ | CAHA2.2m/PANIC | $15\ensuremath{'}\times15\ensuremath{'}$ | 0.45$''$ | 1.1$''$ | 75 min | 24.5 mag(AB)/pix |
| CO(1-0) | ALMA | $50\ensuremath{''}$ | 0.2$''$ | $0.64\ensuremath{''}\times0.55\ensuremath{''}$ | 104 min | $0.21$ mJy/beam/50$\mathrm{km\,s}^{-1}$ |
| L | VLA (CnB config) | $32\ensuremath{'}$ | 1.5$''$ | $10.0\ensuremath{''}\times5.4\ensuremath{''}$ | 90 min | $21.5\,\mu$Jy/beam |
| H I | VLA (CnB config) | $32\ensuremath{'}$ | 1.5$''$ | $10.0\ensuremath{''}\times5.4\ensuremath{''}$ | 90 min | $0.4$ mJy/beam/50$\mathrm{km\,s}^{-1}$ |
| X | VLA (A config) | $4.5\ensuremath{'}$ | 0.04$''$ | $0.4\ensuremath{''}\times0.2\ensuremath{''}$ | 40 min | $12.5\,\mu$Jy/beam |

It is clear that only extensive multi-wavelength observations of AGN host galaxies will improve our understanding about the nature of AGN-driven outflows and the impact on their host galaxies. We therefore started the **C**lose **A**GN **R**eference **S**urvey (cite: Husemann:2017b) which aims to map the host galaxies of almost 40 nearby ($0.01 < z < 0.06$) unobscured (type 1) AGN host galaxies at all wavelength from radio to X-rays. The CARS sample of AGN is drawn from the Hamburg/ESO survey (cite: Wisotzki:2000) and focuses on the sub-sample of the most luminous optically-selected AGN at those redshift which has previously targeted for single-dish observations of CO(1-0) as described in (cite: Bertram:2007). By combining optical and near-IR IFU spectroscopy, radio and sub-mm interferometry and multi-band imaging of the entire galaxies we will characterize many aspects of the AGN feedback paradigm, enabling a better understanding of the conditions of star formation in AGN host galaxies, quenching via AGN-driven outflows, and the galaxy-scale (im)balance of AGN feeding vs. feedback as described in the chaotic cold accretion model (cite: Gaspari:2017; Gaspari:2018).

In this paper we present an in-depth multi-wavelength study of the CARS galaxy HE 1353$-$1917 (, $13^\mathrm{h}56^\mathrm{m}36.7s$ $-19\ensuremath{^\circ}31\ensuremath{'}45\ensuremath{''}$) at redshift $z=0.035$. This AGN host galaxy appears as an edge-on disc-like galaxy where the AGN ionization cones are directly intercepting the galaxy disc. It is therefore a unique test case to study the process of AGN feedback in detail and to highlight the power of our multi-wavelength approach in constraining the AGN outflow energetics and its putative connection to its host galaxy.

Throughout this paper we assume $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M = 0.3$, and $\Omega_{\Lambda} = 0.7$. In this cosmology, 1$''$ corresponds to 0.697 kpc at the redshift of HE 1353$-$1917 ($z=0.035$), where the associated luminosity distance is 153.9 Mpc.

# The CARS multi-wavelength data set

As part of the CARS survey we have acquired a large number of multi-wavelength observations for HE 1353$-$1917 from X-rays to radio which are complemented by archival and literature data. Specifically, we obtained optical integral-field spectroscopy with the Multi Unit Spectroscopic Explorer (cite: Bacon:2010; Bacon:2014a) at the Very Large Telescope under programme 095.B-0015(A) (PI: Husemann) and near-IR (NIR) integral-field spectroscopy with the Near-Infrared Integral Field Spectrometer (cite: McGregor:2003) at Gemini North as a Fast Turnaround project (Program ID GN-2017A-FT-10, PI: J. Scharwächter). Deep optical ($B$, $V$ and $R$ bands) and NIR images ($J$, $H$ and $K_s$ bands) were taken with the 4.1 m Southern Astrophysical Research (SOAR) Telescope using the SOAR Optical Imager (SOI; (cite: Walker:2003)) and with the 2.2m telescope at the Calar Alto Observatory using the Panoramic Near-Infrared Camera (cite: Baumeister:2008), respectively, under programmes SOAR/NOAO 2016A-0006 (PI: G. Tremblay) and CAHA F15-2.2-014 (PI: B. Husemann). $^{12}$CO(1–0) line mapping was obtained with ALMA for HE 1353$-$1917 in the two configurations C40-5 and C40-2 as part of programme 2016.1.00952.S (PI: G. Tremblay). Radio observations were taken with the Karl G. Jansky Very Large Array (VLA) at $X$-band (10 GHz) in A configuration and at $L$-band (1.4 GHz) in CnB configuration under programmes 16B-084 (PI: Pérez-Torres) and 16A-102 (PI: Pérez-Torres), respectively. Finally, a deep X-ray spectrum with 62 ksec integration time was taken with *XMM-Newton* (ObsID: 0803510201, PI: Krumpe) and a high-resolution X-ray image with *Chandra X-ray Observatory* as part of the Guaranteed Time Observation (GTO) program 19700783 (PI: Kraft).

The basic characteristics of our multi-wavelength observations in terms of field-of-view, spatial resolution and depth are provided in Table [\[table:ObsRef\]](#table:ObsRef). All details of the observations and the data reduction are fully described in the appendix from Sects. [6.1](#sect:MUSE_appendix) to [6.9](#sect:chandra_appendix). Furthermore, we collected archival data from the Wide-field Infrared Survey Explorer (cite: Wright:2010) satellite at 3.4, 4.6, 12 and 22 $\mu$m mid-IR (MIR) bands (see Sect. [7.1](#sect:WISE_appendix)), from *Herschel* (cite: Pilbratt:2010) with the instruments PACS (cite: Poglitsch:2010) at 70 and 160 $\mu$m and SPIRE (cite: Griffin:2010) at 250, 350 and 500 $\mu$m (see Sect. [7.2](#sect:Herschel_appendix)), from the Panoramic Survey Telescope and Rapid Response System (cite: Chambers:2016) in the $g,r,i,z,y$ filters (see Sect. [7.3](#sect:PNASTARRS_appendix)), and from the Galaxy Evolution Explorer (cite: Martin:2005) in the 1350–1750Å (FUV channel) and 1750–2750Å (NUV channel) bands (see Sect. [7.4](#sect:GALEX_appendix)). A first visual impression of the processed multi-wavelength data is given in Fig. [1](#fig:overview).

![](Fig1.pdf)

# Analysis and Results

## Broad-band SED fitting

We first measure a reliable stellar mass and star formation rate (SFR) for HE 1353$-$1917 based on our multi-wavelength photometry. The overall spectral-energy distribution from the FIR to the UV bands is listed in Table [1](#tab:SED). We employ a template fitting approach to model the broad-band SED. A Bayesian approach is used byAGNFITTER (cite: CalistroRivera:2016) to decompose the total SED into the stellar, AGN and dust emission contribution. We ran AGNFITTER with 150 walkers, 3 burn-in sets, of 3000 samples followed by 12000 MCMC samples to infer the distribution of parameters. The broad-band SED and 100 representative MCMC samples are shown in Fig. [2](#fig:SED_fit).

![](Fig2.pdf)

From the posterior probability distributions derived by AGNFITTER we infer a stellar mass of $M_* = (2.5\pm0.5)\times10^{10}M_\ensuremath{\odot}$ and a star formation rate of $\mathrm{SFR}=2.3\pm0.1 M_\ensuremath{\odot}\,\mathrm{yr}^{-1}$. Due to the strong hot dust component from the AGN torus, AGNFITTER infers the SFR by integrating only the starburst component over the 8-1000$\mu$m FIR band as described in (cite: CalistroRivera:2016). Considering the inferred stellar mass we compute a specific star formation rate (sSFR) of $\log(\mathrm{sSFR}/[\mathrm{yr}^{-1}])=-10.0\pm0.1$. Given the molecular gas content, the derived SFR leads to a gas depletion time scale of $t_\mathrm{dep}=(1.6\pm0.2)\times 10^9$ yr as expected from normal star forming galaxies (cite: Leroy:2008; Bigiel:2011).

|      Band       | Instrument | $f_\mathrm{tot}$ \[mJy\] |
|:---------------:|:----------:|:------------------------:|
|       FUV       |   GALEX    |     $0.054\pm0.009$      |
|       NUV       |   GALEX    |     $0.180\pm0.006$      |
|        B        |  SOAR/SOI  |      $1.68\pm0.09$       |
|        g        | Pan-STARRS |      $2.17\pm0.04$       |
|        V        |  SOAR/SOI  |      $3.04\pm0.16$       |
|        R        |  SOAR/SOI  |      $4.33\pm0.06$       |
|        r        | Pan-STARRS |       $4.90\pm0.1$       |
|        i        | Pan-STARRS |      $6.39\pm0.13$       |
|        z        | Pan-STARRS |      $8.34\pm0.17$       |
|        y        | Pan-STARRS |      $10.0\pm0.20$       |
|        J        | CAHA/PANIC |       $14.3\pm0.8$       |
|        H        | CAHA/PANIC |       $19.6\pm1.1$       |
|       Ks        | CAHA/PANIC |       $20.4\pm1.1$       |
|       W1        |    WISE    |       $11.0\pm1.1$       |
|       W2        |    WISE    |       $13.1\pm1.3$       |
|       W3        |    WISE    |       $49.0\pm4.9$       |
|       W4        |    WISE    |       $82.7\pm8.3$       |
|  PACS/70$\mu$m  |  Herschel  |        $204\pm17$        |
| PACS/160$\mu$m  |  Herschel  |        $659\pm82$        |
| SPIRE/250$\mu$m |  Herschel  |        $444\pm52$        |
| SPIRE/350$\mu$m |  Herschel  |        $215\pm82$        |
| SPIRE/500$\mu$m |  Herschel  |        $85\pm15$         |

: Spatially-integrated multi-band SED of HE 1353-1917

## Deblending of AGN and host galaxy light

### IFU spectroscopy

We also have to decompose the optical and NIR IFU spectroscopic data from MUSE and NIFS into an AGN and a host galaxy component. To do that we use the fact that the emission from the AGN appears as a point source at all wavelength while the host galaxy necessarily is an extended component. Thus, the first step in the decomposition process is to estimate the PSF for the data. While MUSE covers a large wavelength range leading to wavelength dependent PSF, the PSF for the separate $J$ and $K$ band NIFS observations will be assumed to be constant for the respective band. Following the prescription of (cite: Jahnke:2004b) we empirically obtain the PSF from the intensity distribution of the broad AGN emission lines using our own software QDEBLEND${}^{\mathrm{3D}}$ (cite: Husemann:2013a; Husemann:2014). We reconstruct the PSF in the optical MUSE data from the broad H$\beta$, H$\alpha$ and the O i $\lambda 4448$, which we interpolate in wavelength pixel-by-pixel using a 2 order polynomial after normalizing the brightest pixel to 1. The $J$ and $K$ band observations with NIFS cover the prominent broad Pa$\beta$ and Br$\gamma$ emission, respectively, which are used to construct the PSF for each band without the need to interpolate.

Following the iterative AGN-host galaxy deblending scheme presented in (cite: Husemann:2013a) we initially construct an AGN cube from the brightest AGN spectrum and the wavelength depended PSF. After subtracting the AGN from the original cube, the residual cube contains the host galaxy signal. However, even the brightest AGN spectrum in the initial cubes has a host galaxy contribution which causes an AGN over-subtraction at the center of the galaxy. We mitigate this effect by iteratively subtracting the residual host galaxy spectrum from the initial AGN spectrum taking into account the surface brightness distribution. Given the large field-of-view (FoV) and relatively low spatial resolution of the MUSE data, we use the measured surface brightness profile from the broad-band photometry to interpolate the brightness of the galaxy spectrum towards the nucleus, but assume a constant surface brightness of the host on the very small scales probed by the NIFS data.

![](Fig3.pdf)

We stop the iterative process after 6 and 4 iterations for MUSE and NIFS, respectively, at which the changes are less than 1%. In Fig. [3](#fig:decomp) we show the decomposed spectra from MUSE and NIFS within an aperture of 3$''$ and 1$''$, respectively, which confirm that the host galaxy spectra are free from any remaining broad line components. Based on the recovered PSF we estimate a spatial resolution due to the seeing of $\sim$0.7$''$ full-width-at-half-maximum (FWHM) at the H$\alpha$ wavelength for the MUSE observations and $\sim$0$.\!\!^{\prime\prime}$4 for the NIFS observations.

## AGN parameters

Basic AGN parameters are determined by fitting the emission lines in the nuclear spectrum of HE 1353$-$1917 (Fig. [4](#fig:AGN_fit)). The nuclear spectrum was obtained from the MUSE datacube by integrating an aperture of 2$''$ radius centered on the AGN position. A stellar continuum datacube was subtracted beforehand which we constructed by fitting stellar population synthesis model spectra to the QSO-deblended datacube as described below in Sect. [3.4](#sect:line_measurements). The remaining pure AGN continuum was subtracted by fitting a power-law to the continuum sampled at four different rest wavelength ranges (4700–4732 Å, 5070–5100 Å, 5630–5650 Å, and 6810–6870 Å). Emission lines in the nuclear spectrum were modeled by simultaneously fitting the two wavelength regions around H$\beta$ and H$\alpha$ with a set of Gaussian line profiles together with an Fe ii template from (cite: Kovacevic:2010). During the fit, all narrow permitted and forbidden lines were kinematically tied to each other in velocity and line width, assuming instrumental spectral resolutions of $R_\mathrm{S}=1800$ and 2500 in the wavelength regions around H$\beta$ and H$\alpha$, respectively.

The broad H$\beta$ and H$\alpha$ lines were modeled using the superposition of two broad Gaussian components. Two components are needed to capture the extended blue wings of the broad H$\alpha$ line. Both components for the broad H$\beta$ and H$\alpha$ line were forced to share the same kinematics. A two component model can, however, not capture the full line asymmetry of the broad line as seen in the residuals of Fig. [4](#fig:AGN_fit). Those deviations do however not affect the FWHM estimates of the full line profile beyond the systematic errors. For Fe ii, the line width and velocity shift were tied to the broad Balmer lines during the fit. We used the narrowest Fe ii templates from (cite: Kovacevic:2010) and convolved these with Gaussian kernels to adjust the line width during the fit. To further constrain the fit, we used fixed flux ratios of 3.05 and 2.948 for \[N ii\] $\lambda 6583$/\[N ii\] $\lambda 6548$ and \[O iii\] $\lambda 5007$/\[O iii\] $\lambda 4959$, respectively (see discussion in (cite: Schirmer:2013)).

From the best-fit model we infer a broad Balmer line width of $\mathrm{FWHM}_\mathrm{BLR}=(5820\pm80)\,\mathrm{km\,s}^{-1}$ and $\sigma_{BLR}=(3990\pm180)\,\mathrm{km\,s}^{-1}$. The measured continuum flux at the rest-frame wavelength of 5100Å is $f_{5100}=(10.5\pm0.1)\times10^{-16}\,\mathrm{erg}\,\mathrm{s}^{-1}\,\mathrm{cm}^{-2}\,\mathrm{\AA}^{-1}$ and the broad Balmer emission-line fluxes are $f_{\mathrm{H}\beta}=(4.1\pm0.2)\times10^{-14}\,\mathrm{erg}\,\mathrm{s}^{-1}\,\mathrm{cm}^{-2}$ and $f_{\mathrm{H}\alpha}=(29.5\pm0.2)\times10^{-14}\,\mathrm{erg}\,\mathrm{s}^{-1}\,\mathrm{cm}^{-2}$. Here, we estimate the single-epoch BH mass using the broad H$\alpha$ line luminosity and FWHM as calibrated by (cite: Woo:2015) $$\begin{equation}
 M_\mathrm{BH}=1.12\left(\frac{\mathrm{FWHM}_{\mathrm{H}\alpha}}{1000\,\mathrm{km\,s}^{-1}}\right)^{2.06}\left(\frac{L_{\mathrm{H}\alpha}}{10^{42}\,\mathrm{erg\,s}^{-1}}\right)^{0.46}10^{6.544}M_\odot
\end{equation}$$ This yields a BH mass for HE1353-1917 of $M_\mathrm{BH}=(1.36\pm0.04)\times10^8\,M_\odot$ based on our measurements. However, the uncertainties on single-epoch BH masses are dominated by systematics so that a typical error of 0.4 dex is assumed (cite: Vestergaard:2006; Denney:2009) for high S/N measurements as in this case.

![](Fig4.pdf)

The bolometric AGN luminosities can be estimated from various indicators. Adopting a bolometric correction factor of $\sim10$ for the continuum luminosity at 5100Å (cite: Richards:2006) and the conversion from the broad H$\alpha$ to continuum luminosity reported by (cite: Greene:2005) we estimate a bolometric luminosity of $L_\mathrm{bol}=(2.0\pm0.2)\times10^{44}\mathrm{erg}\,\mathrm{s}^{-1}$. This estimate from the optical line emission of the BLR is fully consistent with the estimated bolometric luminosity from our deep X-ray observations. Considering our BH mass estimate we computed an Eddington ratio of $\log(L_\mathrm{bol}/L_\mathrm{Edd})=-1.9\pm0.4$, so the BH is accreting close to $\sim$1% of its Eddington limit.\

![](Fig5.pdf)

## Spatially-resolved multi-phase emission-line measurements

### Ionized gas phase

To obtain clean measurements of the ionized-gas emission lines in the optical MUSE IFU spectra, we first have to subtract the stellar continuum properly avoiding any influence of absorption lines on emission-line fluxes. Modelling the stellar continuum and subsequent emission-line analysis is implemented in PYPARADISE (cite: Husemann:2016a; Weaver:2018), which is a Python version of the stellar population synthesis fitting code PARADISE (cite: Walcher:2015) to which emission-line fitting capabilities are added. The stellar and emission-line modelling is done in two subsequent steps. First, PYPARADISE fits the continuum spectrum as a linear super-position of a template library of stellar or stellar population spectra after convolving them with a Gaussian line-of-sight velocity distribution (LOSVD). Second, the best-fit stellar continuum models are subtracted from the original spectra and the emission-lines are modelled as Gaussian functions.

A key feature of PYPARADISE is that the input spectra and the template library spectra are initially normalized by a running mean where emission lines or strong sky line residuals are masked and linearly interpolated. In this way, we minimize systematic effects caused by wavelength-dependent flux calibration issues or low-frequency residuals after the AGN subtraction. Below we briefly describe the underlying algorithm and its application to our MUSE data after AGN-host galaxy deblending.

PYPARADISE determines the best-fit LOSVD and linear combination of normalized spectral templates independently based on an MCMC algorithm and a non-negative linear least square fitting, respectively, in an iterative scheme. First, the algorithm infers an initial guess on the LOSVD based on a single spectrum drawn from the template library. Second, the previously determined best-fit LOSVD is applied to all spectra in the template library to obtain the best-fit non-negative linear combination of template spectra excluding masked spectral regions contaminated by emission lines or sky line residuals. This best-fit linear combination of spectra is used as the input spectrum for further iterations and the two step process of estimating LOSVD and linear combination is repeated. The final best-fit spectrum is then denormalized and subtracted from the original spectrum.

Afterwards emission lines are then measured subsequently in the residual spectrum. Given the spectral coverage of MUSE and redshift of HE 1353$-$1917, we focus on modelling the H$\beta$, \[O iii\] $\lambda\lambda 4960,5007$, \[O ii\] $\lambda 6300$, H$\alpha$, \[N ii\] $\lambda\lambda 6545,6583$ and \[S ii\] $\lambda\lambda 6717,6731$ emission lines. All the emission lines are modelled as a system of Gaussians with a common LOS velocity and velocity dispersion taking into account the wavelength-dependent spectral resolution of MUSE as derived by (cite: Bacon:2017). In addition, the line ratios of the \[O iii\] $\lambda\lambda 4960,5007$ and \[N ii\] doublets $\lambda\lambda 6545,6583$ are fixed to their theoretical values (cite: Storey:2000).

![](Fig6.pdf)

Since the S/N of the stellar continuum is much lower than that of the emission-lines in the MUSE cube of HE 1353$-$1917, we apply a Voronoi binning (cite: Cappellari:2003) to increase the S/N to a minimum of 20 in the stellar continuum in the wavelength range $7000\AA<\lambda<7100\AA$. The emission lines are then modelled again per spaxel after repeating the spectral synthesis modelling with PYPARADISE but now fixing the previously estimated LOSVD parameters of the corresponding Voronoi bin used for the continuum fitting. Given that some of the important emission lines, e.g. H$\beta$, are often too weak in a single spaxel, we also perform the emission-line fitting after binning the original cube by $8\times8$ spaxel ($1.6\ensuremath{''}\times1.6\ensuremath{''}$). Uncertainties for all parameters are estimated using a Monte-Carlo approach where the stellar continuum and emission lines fitting are repeated 40 times after each spectrum is modulated randomly within the error of each spectral pixel.

The resulting LOS velocity $v_\mathrm{LOS}$, velocity dispersion $\sigma$ and flux maps are shown in the first two rows of Fig. [5](#fig:maps). As expected the stellar and ionized gas kinematics reveal a clear rotational pattern along the major axis of the nearly edge-on disc galaxy. The unexpected features for this galaxy are the quite extended filamentary structures of ionized gas outside of the disc. The LOS velocity of the filaments shows that the gas rotates in the same sense as the galaxy disc, which already suggests that the ionized gas is linked to the galaxy disc. Furthermore, we detect exceptionally high velocity dispersion in the ionized gas about 1.3$''$ (900 pc) south-west of the AGN position. Understanding the origin of both features is the main topic and driver for the following analysis of this paper.

### Cold molecular and atomic gas phase

From the cleaned ALMA datacube we created a zeroth moment (integrated intensity) map, a first moment (mean velocity) map, and a second moment (velocity dispersion) map of the detected CO(1-0) line emission using a masked moment technique (cite: Dame:2011). A copy of the clean data cube was Gaussian-smoothed spatially (with a FWHM equal to that of the synthesized beam), and then smoothed (using a 4 channel FWHM Gaussian) in velocity. A three-dimensional mask was then defined by selecting all pixels above a fixed flux threshold of 3 times the RMS noise in this new cube. The moment maps were then created using the original un-smoothed cubes within the masked regions only, without any threshold.

The resulting moment maps are shown in the third row of Fig. [5](#fig:maps). Strong molecular gas emission is detected from the disc of the galaxy. The velocity dispersion (second moment) map of this source also shows the typical X-shaped structure of a beam-smeared gas rotating regularly, apart from two hot spots in the south-west and north-east of the nucleus of the galaxy, at the same location as that found in the ionised gas. The origin of these features will be discussed more in Sect. [3.6](#sect:gas_kin).

After integrating all the CO(1-0) emission, we obtain a cold gas mass of $M_\mathrm{H2}=(3.6\pm0.3)\times10^9\mathrm{M}_\odot$ adopting a Galactic conversion factor of $\alpha_\mathrm{CO}=4.35\,\mathrm{M}_\odot(\mathrm{K\,km\,s}^{-1}\,\mathrm{pc}^{-2})^{-1}$. Our estimate is slightly higher than the single-dish measurements from the IRAM-30m telescope of $M_\mathrm{H2}=(2.7\pm0.2)\times10^9\mathrm{M}_\odot$ reported by (cite: Bertram:2007). The discrepancy is mainly caused by the large extent of the source with respect to the IRAM beam ($\sim$22$''$) so that the integrated signal would need to be corrected by the primary beam response. This correction can only be applied to the ALMA data where the CO(1-0) flux distribution is properly resolved with two different baselines to cover the diffuse extended emission with maximum recoverable scale of $20\ensuremath{''}$.

Based on the integrated H i line flux (see Sect. [6.7](#sect:VLA_HI)) we estimate a at total atomic gas mass of $M_\mathrm{H i}=(1.3\pm0.2)\times10^{10}M_\ensuremath{\odot}$ following the prescription of (cite: Koenig:2009). The inferred atomic gas mass is fully consistent with the upper limit previously reported by (cite: Koenig:2009) for this source using the single-dish Effelsberg telescope. Unfortunately, the S/N is not sufficient to make proper moment maps as in the case of the CO data, but at least we present the peak flux morphology in Fig. [1](#fig:overview) which confirms that the atomic gas is aligned with disc.

### Warm-molecular gas phase

Warm-molecular gas emission in the NIFS $\sim 3\ensuremath{''} \times 3\ensuremath{''}$ FoV is traced via the near-infrared rovibrational H$_2$ \[1-0 S(1)\] $\lambda$21218Å line. Based on the QSO-deblended NIFS data cubes, we derived emission-line maps for the H$_2$ \[1-0 S(1)\] and narrow Br$\gamma$ component in the $K$-band as well as Pa$\beta$ and \[Fe ii\] $\lambda$12570Å in the $J$-band as shown in Fig. [6](#fig:NIFS_maps). Those emission lines were fitted with a Gaussian line profile together with a constant continuum. We also convolved the line widths with the instrumental resolutions of $R_\mathrm{S} \sim 5290$ and $R_\mathrm{S} \sim 6040$ in the $K$- and $J$-bands, respectively.

Fig. [6](#fig:NIFS_maps) shows that all emission lines in the central $\sim 3\ensuremath{''} \times 3\ensuremath{''}$ of HE1353-1917 originate mainly from two emission regions located in the galaxy disc at about 0.8$''$ ($\sim 0.6$ kpc) to the north-east and south-west of the nucleus. The emission from the narrow component of the hydrogen recombination lines (i.e. Br$\gamma$ in the $K$-band and Pa$\beta$ in the $J$-band) is found to be co-spatial with the H$_2$ emission. The NIFS data also reveal a deficiency of H$_2$ or narrow-line hydrogen recombination emission within a 0.3$''$ (0.2 kpc) region (radius) around the nucleus. The nuclear region is instead dominated by the PSF from the broad Br$\gamma$ and Pa$\beta$ emission associated with the AGN broad-line region (see Fig. [3](#fig:decomp)) and decomposed during the QSO-host deblending step.

Interestingly, a comparison with the radio continuum map shows that the southern emission peak is nearly co-spatial with the putative radio jet. Also the kinematics reveal a velocity gradient along the jet axis which is not following a pure rotational pattern of the galaxy disc (Fig. [6](#fig:NIFS_maps)). Hence, the excitation of H$_2$ and \[Fe ii\] together with potentially non-gravitational motions of the gas may be directly linked to the impact of an AGN-driven radio jet on the cold gas disc. The enhanced radio emission on the southern approaching side may be explained either by Doppler boosting of a relativistic jet (cite: Laing:1988; Cohen:2007) or by an intrinsic asymmetry of a bi-polar jet.

## Emission-line diagnostics

### Ongoing star formation and extended NLR

![](Fig7.pdf)

A key analysis from the IFU spectroscopy is to discriminate various ionization sources of the ionized gas throughout the galaxy and beyond. In the case of AGN host galaxies, we do expect a mix of ionization from ongoing star formation, AGN photoionization and potentially from shocks due to AGN-driven or starburst-driven outflows. Various optical emission-line ratios are usually employed to discriminate between different ionization mechanisms (cite: Baldwin:1981; Veilleux:1987; Kewley:2006; Stasinska:2008). We show the \[O iii\]/H$\beta$ vs. \[N ii\]/H$\alpha$ diagnostic diagram for HE 1353$-$1917 in Fig. [7](#fig:BPT_diagram) (top left panel) with the distance from the nucleus indicated as a color gradient. While the QSO-host deblending algorithm already takes out artificial mixing of light from the bright nucleus with the surrounding galaxy, there is an additional mixing between ionization from star formation and the extended NLR.

To disentangle the varying contribution of ionization by young stars and the AGN we use a modified version of the algorithm presented in (cite: Davies:2016). The basic idea is that all measured extinction-corrected emission-line fluxes can be modelled as a linear superposition of a characteristic emission-line basis spectrum for the AGN photoionized and classical H ii regions. While two basis spectra are sufficient to disentangle the ionization close to the nucleus, the line ratios change across the galaxy due to a radial gradient in gas-phase metallicity. Hence, we expand the method of (cite: Davies:2016) by considering a sample of H II basis spectra across the H ii sequence from SDSS and an empirical set of basis spectra for the AGN ionization taken from the MUSE data itself. The optimal combination for each spaxel is then determined through a Markov Chain Monte Carlo approach which also provides estimates on the uncertainty on the SF fraction due to the possible combination of basis spectra combined with the intrinsic errors on the emission-line ratios.

In Fig. [7](#fig:BPT_diagram) (top right) we present the estimated SF fraction across the classical BPT diagram. While we compute the AGN fraction for the mixing region within the disc of galaxy ranging from 0 to 1, we set all spaxel regions to an AGN faction of 1 that are well outside the edge-on disc galaxy area. Those spaxels correspond to the AGN ionization cones which are illuminating gas above the main body of the galaxy where a contribution from H ii region can be neglected. Those regions indeed keep a high \[O iii\]/H$\beta$ ratio while the \[N ii\]/H$\alpha$ ratio is decreasing. This is characteristic for a decreasing metallicity (cite: Groves:2006; Husemann:2011) rather than a mixing with H ii regions.

Combining the spatially-resolved extinction-corrected H$\alpha$ flux with the SF fraction estimates, we obtain a total H$\alpha$ flux of $f_{\mathrm{H}\alpha}=(5.5\pm0.1)\times10^{-14}\mathrm{erg}\,\mathrm{s}^{-1}\mathrm{cm}^{-2}$. This H$\alpha$ flux corresponds to a luminosity of $L_{\mathrm{H}\alpha}=(1.55\pm0.03)\times10^{41}\,\mathrm{erg}\,\mathrm{s}^{-1}$ which leads to a H$\alpha$-based SFR estimate of $\mathrm{SFR}_{\mathrm{H}\alpha}=1.23\pm0.03\,\mathrm{M}_\ensuremath{\odot}\mathrm{yr}^{-1}$. Similarly, we estimate an integrated extinction-corrected \[O iii\] luminosity from the ENLR as $L_{[O iii]}=(1.15\pm0.01)\times10^{42}\,\mathrm{erg}\,\mathrm{s}^{-1}$, with an extension that seems to be limited by the MUSE FoV and exceeds 35$''$ or 25 kpc in projection. Hence, the AGN phase has already been lasting for at least 0.1 Myr given the light travel time across the entire ENLR.

### Gas-phase metallicity along the galaxy disc and extended NLR

The gas-phase metallicity is an important diagnostic as it provides a record of the metal enrichment history of galaxies. Since the weak auroral \[O iii\] $\lambda4363$ emission line is outside the wavelength range covered by MUSE we can only use strong-line methods to infer the gas-phase metallicity of the ionized gas. The N2 index (N2=$\log$(\[N ii\] $\lambda6583$/H$\alpha$ flux ratio) or the O3N2 index (O3N2=$\log${(O iii$\lambda5007$/H$\beta$)/(N ii$\lambda6583$/H$\alpha$)} flux ratio) have been empirically calibrated as a proxy for the oxygen abundance of H ii regions in star-forming galaxies (cite: Pettini:2004; Marino:2013). In the case of HE 1353$-$1917 we cannot directly apply those metallicity indicators, because a significant part of the galaxy is contaminated by strong AGN ionization due to the orientation of the ionization cone. Although variations in the \[N ii\] $\lambda6583$/H$\alpha$ line ratio have been attributed to changes in the metallicity even for AGN-ionized gas clouds based on photo-ionization models (cite: Storchi-Bergmann:1998; Groves:2006), there may also be a dependence on AGN luminosity as highlighted by (cite: Stern:2013).

An alternative metallicity diagnostic is the N2S2 index (N2S2=$\log$(\[N ii\]$\,\lambda6583$/\[S ii\] $\lambda\lambda6717,6731$)) which is a proxy for the N/O abundance (cite: Sabbadin:1977; Viironen:2007) which in turn is also correlated with the O/H abundance (cite: Alloin:1979; Perez-Montero:2009). The advantage of the N2S2 index is that it correlates well with the metallicity even for the AGN photo-ionized ENLR, similar to the N2 index, but does not exhibit a strong dependence on the AGN luminosity as discussed by (cite: Stern:2013). While (cite: Stern:2013) provides a calibration of N2S2 to the oxygen abundance scale established by (cite: Tremonti:2004), we independently correlate the N2S2 index with the oxygen abundance as inferred by the O3N2 index of (cite: Pettini:2004) based on the line ratios of 2300 star-forming galaxies from the SDSS DR7 value-added catalog (cite: Brinchmann:2004), $$\begin{equation}
 12+\log{\mathrm{O/H}} = 8.658 + 0.34\times \mathrm{N2S2}  - 0.312\times \mathrm{N2S2}^2
\end{equation}$$ This exercise is necessary to compare our results for HE 1353$-$1917 with those of (cite: Sanchez:2014) as the absolute calibration of the O/H abundance is significantly dependent on the used empirical calibration (cite: Kewley:2008).

![](Fig8.pdf)

In Fig. [8](#fig:N2S2_metallicity) we show the O/H abundance based on the N2S2 index as a function of galacto-centric distance in units of kpc and normalized to the effective radius of the galaxy disc. We extract pseudo long-slits along the major axis of the galaxy and the ENLR of the putative AGN-ionization cone (see Fig. [7](#fig:BPT_diagram)), which allow us to measure the gas-phase metallicity out to 15 kpc or 2.5 effective radii. We find an error-weighted slope of $\alpha_\mathrm{[O/H]}=-0.043\pm0.006\,\mathrm{dex}\,r_\mathrm{eff}^{-1}$ and $\alpha_\mathrm{[O/H]}=-0.036\pm0.011\,\mathrm{dex}\,r_\mathrm{eff}^{-1}$ for the O/H gradients along the galaxy disc and the ENLR, respectively, with an absolute zero-point of $12+\log([\mathrm{O/H}])=8.703\pm0.006$ in both cases. The errors are derived by bootstrapping where we fit the relation 1000 times for a random selection of half the data points and then compute the standard deviations for the slope and zero-point. Due to the narrow width of the pseudo-long slit the metallicity measurements along the disc and the ENLR are totally independent already after 5$''$ (3.5 kpc) away from the nucleus. The measured gradients are consistent with the characteristic O/H gradients of undisturbed disc galaxies which are $\alpha_\mathrm{[O/H]}=-0.1\pm0.09\mathrm{dex}\,r_\mathrm{eff}^{-1}$ (cite: Sanchez:2014). The central metallicity as expected from the mass–metallicity relation of galaxies is $12+\log(\mathrm{[O/H]})_\mathrm{PP04\,O3N2}=8.72\pm0.10$ for our measured stellar mass of HE 1353$-$1917 following the calibration of (cite: Kewley:2008).

The consistency checks above shows that our metallicity estimates based on the N2S2 index provide reliable measurements even in the case of dominating AGN-ionization. Most importantly, it highlights the fact that the gas illuminated by the AGN above the galaxy’s disc plane shares the same radial metallicity dependence seen in the ionized gas within the galaxy’s disc. This is an important piece of evidence which suggests that the gas illuminated by the AGN has been driven out *vertically* from the disc plane likely by stellar feedback through stellar mass loss and supernova explosions rather than originating from the galaxy centre through AGN outflows.

![](Fig9.pdf)

## Multi-phase gas kinematics

### CO(1-0) kinematic modelling and dynamical mass

The cold gas kinematics as shown in Fig. [5](#fig:maps) seems to be dominated by classical rotational motion of a disc galaxy. Hence, we model the ALMA CO observation directly with the KINematic Molecular Simulation (cite: Davis:2013; Davis:2013b) software tool[^2] taking the beam size and velocity binning into account. As an input for the model we perform a multi-Gaussian expansion (cite: Emsellem:1994; Cappellari:2002) to our $K_s$ band image observed with PANIC to determine the deprojected mass model assuming a linear mass-to-light ratio gradient (M/L) which is a free parameter for the fitting. The MGE parameters are listed in Table [2](#mgetable). We neglect the unresolved MGE component at the galaxy centre, which arises from the AGN. We assume a truncated exponential disc for the CO surface brightness distribution with the scale radius ($r_\mathrm{exp}$) and the inner truncation radius ($r_\mathrm{trunc}$) as free parameters together with the position angle ($\mathrm{PA}_\mathrm{disc}$), inclination ($i_\mathrm{disc}$), the intrinsic velocity dispersion ($\sigma_\mathrm{cold}$), systemic velocity ($v_\mathrm{sys}$) and the kinematic center ($x_\mathrm{kin},y_\mathrm{kin}$) of the disc.

![](Fig10.pdf)

|                             |                              |             |
|:---------------------------:|:----------------------------:|:-----------:|
|   $\log_{10}$ I$_j$$^{a}$   | $\log_{10}$ $\sigma_j$$^{b}$ | $q_j$$^{c}$ |
| $[L_{\odot,K_s}$ pc$^{-2}]$ |          \[arcsec\]          |             |
|       214091.0$^{*}$        |             0.25             |    0.529    |
|           4156.4            |             1.15             |    0.669    |
|            886.5            |             3.80             |    0.390    |
|           1752.9            |             6.51             |    0.100    |
|            109.9            |            10.13             |    0.950    |
|            977.7            |            10.22             |    0.129    |

: MGE parametrization of the galaxies $K_s$ band light profile.

Table notes:

|            Parameter            |                   Value                   |
|:-------------------------------:|:-----------------------------------------:|
|   $\mathrm{PA}_\mathrm{disc}$   |      $29.1\ensuremath{^\circ}\pm0.5$      |
|        $i_\mathrm{disc}$        | $85.4\ensuremath{^\circ}\ _{-0.4}^{+0.1}$ |
|     $\sigma_\mathrm{cold}$      |     $7.0\pm1.8\,\mathrm{km\,s}^{-1}$      |
| M/L$_{Ks}(R=0\ensuremath{''})$  |               $1.18\pm0.07$               |
| M/L$_{Ks}(R=15\ensuremath{''})$ |               $1.45\pm0.08$               |
|      $v_\mathrm{sys,opt}$       |     $10449\pm3\,\mathrm{km\,s}^{-1}$      |
|        $r_\mathrm{exp}$         | $5.8\ensuremath{''}\pm0.\ensuremath{''}$  |
|       $r_\mathrm{trunc}$        | $3.1\ensuremath{''}\pm0.1\ensuremath{''}$ |

: Best-fit CO(1-0) kinematic model parameters and 1$\sigma$ errors

In Fig. [9](#fig:CO_model) we show the CO input maps, model maps and residuals for the best-fit model parameters listed in Table [3](#tab:kin_parameters). Our model is indeed a very good description of the data where the residual in the flux distribution naturally originates from the clumpiness of the gas in the disc. This gas is not distributed with a simple exponentially declining profile, instead shows a central flux deficit within a truncation radius of $r_\mathrm{trunc}=3.1\ensuremath{''}\pm0.1\ensuremath{''}$. The residuals in velocity along the minor axis are caused by the high inclination and corresponding line-of-sight superposition related to the thickness of the disc and the beam size. With a maximum projected LOS velocity of $v_\mathrm{LOS}=240\,\pm\,5\,\mathrm{km\,s}^{-1}$ at $R=17.2$$''$ (12.65 kpc) away from the galaxy centre, we obtain a dynamical mass of $M_\mathrm{dyn}(R<=12.65\,\mathrm{kpc})= 0.6\times(v_\mathrm{rad}/\sin(i))^2R/G=(1.0\pm0.3)\times10^{11}M_\ensuremath{\odot}$ following the prescription of (cite: Lequeux:1983) for disc galaxies. Compared to a stellar mass of $M_*=(2.5\pm0.5)\times10^{10}M_\ensuremath{\odot}$, a molecular gas mass of $M_\mathrm{H_2}=(3.6\pm0.3)\times10^9\mathrm{M}_\odot$ and the atomic gas $M_\mathrm{HI}=(1.3\pm0.2)\times10^{10}M_\ensuremath{\odot}$, we estimate a dark matter fraction of $M_\mathrm{DM}/M_\mathrm{dyn}$ of $\approx$60% within 2.1 effective radii. This dark matter fraction is fairly typical for spiral galaxies of this mass (cite: Salucci:1991; Martinsson:2013).

![](Fig11.pdf)

A striking feature in the cold gas kinematics are two well-defined regions on both sides of the nucleus which exhibit a significantly higher velocity dispersion than our kinematic model predicts. To understand the nature and properties of this region we reconstruct the multi-phase position-velocity diagram (PVD) along the major axis of the galaxy (Fig. [10](#fig:pV-diagram)) based on the CO(1-0), H${}_2[1-0 \mathrm{S}(1)]$ and ionized gas kinematic maps. We find that the LOS velocity profile of the ionized and molecular gas matches exactly along the disc at nearly all radii. This shows that also the ionized gas kinematics are determined pre-dominantly by gravitational motions. However, the LOS velocity and, in particular, the velocity dispersion most strongly deviates from the kinematical model *in all gas phases* about 1.5$''$–2.0$''$ away from the center on both sides. The warm molecular gas, which typically arises in strong shocks, is only detected at the location of those two “hot spots” supporting the notion that it is indeed a special region within the galaxy. Most importantly, we detect an extra-ordinary high velocity dispersion in the ionized gas phase at the same location, but only on one side of the galaxy centre. Given the high inclination and dust content of the disc, we assume that we cannot see the optical emission lines of the ionized gas on the other side of the nucleus due to the high obscuration.

It might be possible to explain the elevated velocity dispersion in the molecular gas by adding an additional point-like mass in the centre or a circum-nuclear bar. However, the significantly stronger deviations in the warm and ionized gas phase, as clearly visible in the PVD and velocity dispersion diagram (Fig. [10](#fig:pV-diagram)) and the kinematic maps (Fig. [5](#fig:maps)), cannot be explained by gravitational motion and appear symmetrically offset from the nucleus. Hence, we disfavor a simple gravitational induced scenario and conclude that we are detecting the signature of a fast bipolar multi-phase outflow driven by the AGN.

### Multi-phase kinematics of the bipolar outflow

The velocity dispersion maps shown in Fig. [11](#fig:outflow_maps) (left panels) reveal the exact location of regions with a high velocity dispersion. Those kinematic features have already been seen in PVD along the major axis of the disc (Fig. [10](#fig:pV-diagram)). All the different gas phases show a higher dispersion about $\sim$1.2$''$ or $\sim$900 pc south-west of the nucleus. A similar region is on the opposite side north-east of the nucleus. It appears much weaker in the optical \[OIII\] than in the H$\alpha$ emission line, because it is the receding side of the outflow and obscured by the foreground dust screen of the disc. We extract a co-added spectrum within an aperture of 0.8$''$ radius for both high dispersion regions. The spectra for the south-west and north-east region are shown in the right panels of Fig. [11](#fig:outflow_maps). All optical lines as well as the CO(1-0) line exhibit a prominent broad wing on the blue and red side, respectively. The lack of a broad wing in the NIR lines is likely caused by the limited sensitivity given the peak flux ratio of the narrow-to-broad components seen in the CO(1-0) lines.

+---------------------------------+---------------------------------------------------------------------------------------------------+---------+---------------------------------------------------------------------------------------------------+------------------------------------+------------------------------------+------------------------------------+
|                                 | narrow core                                                                                       |         | broad wing                                                                                        |                                    |                                    |                                    |
+:================================+:=======================:+:==================================:+:==================================:+:=======:+:=======================:+:==================================:+:==================================:+:==================================:+:==================================:+:==================================:+
| 2-4 Line                        | $f_\mathrm{line}$$^{a}$ | $v_\mathrm{line}$                  | $\sigma_\mathrm{line}$             |         | $f_\mathrm{line}$$^{a}$ | $v_\mathrm{line}$                  | $\sigma_\mathrm{line}$             | $v_{10}$                           | $W_{80}$                           | $v_\mathrm{max}$                   |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
|                                 |                         | \[$\mathrm{km}\,\mathrm{s}^{-1}$\] | \[$\mathrm{km}\,\mathrm{s}^{-1}$\] |         |                         | \[$\mathrm{km}\,\mathrm{s}^{-1}$\] | \[$\mathrm{km}\,\mathrm{s}^{-1}$\] | \[$\mathrm{km}\,\mathrm{s}^{-1}$\] | \[$\mathrm{km}\,\mathrm{s}^{-1}$\] | \[$\mathrm{km}\,\mathrm{s}^{-1}$\] |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| south west region                                                                                                                                                                                                                                                                                                                                                |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{H}\beta$               | $6.2\pm0.2$             | $-60\pm10$                         | $143\pm3$                          |         | $4.0\pm0.2$             | $-310\pm20$                        | $360\pm30$                         | $-550\pm30$                        | $680\pm30$                         | $1040\pm50$                        |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[OIII]\ }\lambda$5007Å | $56.7\pm0.9$            | $-60\pm10$                         | $143\pm3$                          |         | $29.2\pm0.6$            | $-310\pm20$                        | $360\pm30$                         | $-510\pm20$                        | $640\pm20$                         | $1040\pm60$                        |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{H}\alpha$              | $37.3\pm0.4$            | $-80\pm10$                         | $143\pm3$                          |         | $20.3\pm0.5$            | $-350\pm20$                        | $360\pm30$                         | $-560\pm20$                        | $660\pm20$                         | $1080\pm60$                        |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[NII]\ }\lambda$6548Å  | $11.7\pm0.2$            | $-80\pm10$                         | $143\pm3$                          |         | $8.1\pm0.1$             | $-350\pm20$                        | $360\pm30$                         | $-600\pm20$                        | $710\pm30$                         | $1080\pm60$                        |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[SII]\ }\lambda$6717Å  | $12.3\pm0.2$            | $-90\pm10$                         | $143\pm3$                          |         | $5.2\pm0.8$             | $-440\pm60$                        | $360\pm30$                         | $-590\pm70$                        | $680\pm60$                         | $1170\pm80$                        |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[SII]\ }\lambda$6730Å  | $10.1\pm0.3$            | $-90\pm10$                         | $143\pm3$                          |         | $7.1\pm0.6$             | $-440\pm60$                        | $360\pm30$                         | $-690\pm70$                        | $770\pm60$                         | $1170\pm80$                        |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| Pa$\beta$                       | $5.0\pm0.1$             | $70\pm10$                          | $97\pm3$                           |         | ...                     | ...                                | ...                                | ...                                | ...                                | ...                                |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{H}_2$ \[1-0 S(1)\]     | $2.8\pm0.1$             | $-20\pm10$                         | $144\pm7$                          |         | ...                     | ...                                | ...                                | ...                                | ...                                | ...                                |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| CO(1-0)                         | $0.66\pm0.04$           | $-40\pm10$                         | $25\pm1$                           |         | $0.30\pm0.09$           | $-160\pm20$                        | $70\pm30$                          | $-190\pm30$                        | $180\pm30$                         | $290\pm50$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
|                                 |                         |                                    |                                    |         |                         |                                    |                                    |                                    |                                    |                                    |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{H}\beta$               | $4.2\pm0.3$             | $60\pm10$                          | $66\pm3$                           |         | $<2.0$                  | $160\pm10$                         | $180\pm20$                         | $163\pm4$                          | $190\pm20$                         | $530\pm30$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[OIII]\ }\lambda$5007Å | $37.8\pm0.8$            | $60\pm10$                          | $66\pm3$                           |         | $11.5\pm0.8$            | $160\pm10$                         | $180\pm20$                         | $213\pm5$                          | $250\pm10$                         | $530\pm30$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{H}\alpha$              | $17.2\pm0.7$            | $70\pm10$                          | $66\pm3$                           |         | $17.6\pm0.7$            | $120\pm10$                         | $180\pm20$                         | $280\pm10$                         | $340\pm20$                         | $490\pm30$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[NII]\ }\lambda$6548Å  | $4.2\pm0.2$             | $70\pm10$                          | $66\pm3$                           |         | $6.2\pm0.2$             | $120\pm10$                         | $180\pm20$                         | $300\pm10$                         | $370\pm30$                         | $490\pm30$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[SII]\ }\lambda$6717Å  | $4.1\pm0.3$             | $70\pm10$                          | $66\pm3$                           |         | $5.6\pm0.5$             | $120\pm20$                         | $180\pm20$                         | $300\pm20$                         | $360\pm30$                         | $490\pm40$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{[SII]\ }\lambda$6730Å  | $3.4\pm0.3$             | $70\pm10$                          | $66\pm3$                           |         | $4.7\pm0.4$             | $120\pm20$                         | $180\pm20$                         | $300\pm20$                         | $360\pm30$                         | $490\pm40$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| Pa$\beta$                       | $3.7\pm0.1$             | $180\pm10$                         | $77\pm30$                          |         | ...                     | ...                                | ...                                | ...                                | ...                                | ...                                |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| $\mathrm{H}_2$ \[1-0 S(1)\]     | $2.1\pm0.1$             | $170\pm10$                         | $97\pm4$                           |         | ...                     | ...                                | ...                                | ...                                | ...                                | ...                                |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
| CO(1-0)                         | $0.32\pm0.07$           | $70\pm10$                          | $25\pm3$                           |         | $0.37\pm0.10$           | $130\pm40$                         | $100\pm30$                         | $220\pm30$                         | $190\pm50$                         | $330\pm70$                         |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+
|                                 |                         |                                    |                                    |         |                         |                                    |                                    |                                    |                                    |                                    |
+---------------------------------+-------------------------+------------------------------------+------------------------------------+---------+-------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+------------------------------------+

Table notes:

![](Fig12.png)

We modelled the emission lines as a superposition of two Gaussian profiles when applicable. We force doublet lines to be fixed in their theoretical flux ratios and coupled the velocity dispersion of all lines for the two distinct kinematic systems to avoid degeneracies in the solution. The parameters for the best-fit model are listed in Table [\[tab:outflow\]](#tab:outflow) for the south-west and north-east nucleus. The velocity of the core component is in all cases very close to the corresponding LOS velocity of the stars that we used as a reference. The velocity dispersion of the core component varies between $\sigma_\mathrm{core}\sim$60–140$\,\mathrm{km\,s}^{-1}$ (corrected for spectral resolution) for the ionized and warm-molecular gas phases, but much lower for the cold molecular gas as expected. The wing components are systematically blueshifted by about $-300\,\mathrm{km\,s}^{-1}$ and $-160\,\mathrm{km\,s}^{-1}$ on the south-west side and redshifted by about $140\,\mathrm{km\,s}^{-1}$ and $100\,\mathrm{km\,s}^{-1}$ on the north-east side for the ionized and molecular gas, respectively. The ionized gas velocity dispersion of $365\pm27\,\mathrm{km\,s}^{-1}$ on the south-west side is significantly higher than the stellar velocity dispersion of $\sigma_*=239\pm19\,\mathrm{km\,s}^{-1}$ (in the same aperture) and the broad component of cold molecular gas with $67\pm25\,\mathrm{km\,s}^{-1}$. Those extreme ionized gas kinematics cannot be easily explained solely by gravitational motions and are a rather clear signature of a kpc-scale AGN-driven outflow.

Strikingly, the different gas phases are not exactly co-spatial after properly co-registering point-like AGN continuum emission of the various observations as seen in Fig. [11](#fig:outflow_maps). The warm-molecular gas as probed by H$_2$ \[1-0 S(1)\] is mainly excited at the location of the radio emission of the jet in the south-west region and the putative counter-jet in the north-east region. The high-dispersion molecular gas peaks are located at a slightly larger distance from the nucleus whereas the very fast ionized gas appears closer to the nucleus and slightly offset vertically from the disc plane. This suggests that the AGN-driven outflow is pushing on the cold gas in the disc with a stratification of excitation and speed as the shock front is passing the cold gas clouds which disrupts the front side of the clouds as sketched in Fig. [12](#fig:Cartoon). The gas inside the shock front is much warmer than the cold gas outside where the ionized gas is flowing around the thin and dense cold gas disc and diverted outside of the plane of the galaxy following the path of less resistance. In the following we will estimate the outflow energetics of the different gas phases to quantify the driving mechanisms of the outflow and to predict the potential damage to the galaxy.

+------------------+---------------------------------------------------------------------------------------------------------------------+---+----------------------------------------------------------------------------------------------------------------+
|                  | cone geometry                                                                                                       |   | shell geometry                                                                                                 |
+:=================+:===============:+:===============:+:===============:+:=======:+:===============:+:===============:+:===============:+:=:+:===============:+:===============:+:===============:+:==:+:===============:+:===============:+:===============:+
| 2-8              | ionized                                             |         | molecular                                           |   | ionized                                             |    | molecular                                           |
+------------------+-----------------+-----------------+-----------------+---------+-----------------+-----------------+-----------------+---+-----------------+-----------------+-----------------+----+-----------------+-----------------+-----------------+
| 2-4              | $\log(\dot{M})$ | $\log(\dot{p})$ | $\log(\dot{E})$ |         | $\log(\dot{M})$ | $\log(\dot{p})$ | $\log(\dot{E})$ |   | $\log(\dot{M})$ | $\log(\dot{p})$ | $\log(\dot{E})$ |    | $\log(\dot{M})$ | $\log(\dot{p})$ | $\log(\dot{E})$ |
+------------------+-----------------+-----------------+-----------------+---------+-----------------+-----------------+-----------------+---+-----------------+-----------------+-----------------+----+-----------------+-----------------+-----------------+
| $v_\mathrm{br}$  | $-0.24$         | $32.80$         | $40.12$         |         | $1.89$          | $34.85$         | $41.85$         |   | $-0.02$         | $33.02$         | $40.34$         |    | $2.11$          | $35.07$         | $42.07$         |
+------------------+-----------------+-----------------+-----------------+---------+-----------------+-----------------+-----------------+---+-----------------+-----------------+-----------------+----+-----------------+-----------------+-----------------+
| $v_\mathrm{max}$ | $0.28$          | $33.84$         | $41.32$         |         | $2.23$          | $35.53$         | $42.72$         |   | $0.50$          | $34.06$         | $41.54$         |    | $2.26$          | $35.43$         | $42.56$         |
+------------------+-----------------+-----------------+-----------------+---------+-----------------+-----------------+-----------------+---+-----------------+-----------------+-----------------+----+-----------------+-----------------+-----------------+
| $v_\mathrm{10}$  | $0.41$          | $33.83$         | $41.19$         |         | $2.42$          | $35.50$         | $42.49$         |   | $0.64$          | $34.05$         | $41.41$         |    | $2.64$          | $35.73$         | $42.72$         |
+------------------+-----------------+-----------------+-----------------+---------+-----------------+-----------------+-----------------+---+-----------------+-----------------+-----------------+----+-----------------+-----------------+-----------------+
| $W_\mathrm{80}$  | $0.50$          | $34.02$         | $41.49$         |         | $2.40$          | $35.47$         | $42.44$         |   | $0.72$          | $34.24$         | $41.71$         |    | $2.62$          | $35.69$         | $42.66$         |
+------------------+-----------------+-----------------+-----------------+---------+-----------------+-----------------+-----------------+---+-----------------+-----------------+-----------------+----+-----------------+-----------------+-----------------+
|                  |                 |                 |                 |         |                 |                 |                 |   |                 |                 |                 |    |                 |                 |                 |
+------------------+-----------------+-----------------+-----------------+---------+-----------------+-----------------+-----------------+---+-----------------+-----------------+-----------------+----+-----------------+-----------------+-----------------+

Table notes: Units for mass outflow rates ($\dot M$) are $M_{\ensuremath{\odot}}\,\mathrm{yr}^{-1}$, for the momentum injection rates ($\dot p$) are dyne, and for energy injection rates ($\dot E$) are $\mathrm{erg\,s}^{-1}$. We do not provide the formal measurement errors here since they are significantly smaller than the spread implied by the different asummptions.

### Outflow energetics and mass outflow rates

As a first step we compute the outflowing ionized gas mass from the extinction-corrected H$\alpha$ luminosity ($L_{\mathrm{H}\alpha}$) and the electron density $(n_\mathrm{e})$ with $$\begin{equation}
 M_\mathrm{ion} = 3.4\times10^6\left(\frac{100\mathrm{cm}^{-2}}{n_\mathrm{e}}\right)\times\left(\frac{L_{\mathrm{H}\alpha}}{10^{41}\mathrm{erg\,s}^{-1}}\right) M_\ensuremath{\odot}
\end{equation}$$ as described in (cite: Husemann:2016a) following (cite: Osterbrock:2006). From the H$\alpha$/H$\beta$ Balmer decrement we infer an optical LOS attenuation, adopting a Milky Way-like attenuation curve (cite: Cardelli:1989), of $A_{V,\mathrm{core}}=2.3\pm0.1$ mag $A_{V,\mathrm{wing}}=1.8\pm0.2$ mag in the south-west side for the core and outflow component, respectively. The corresponding values for the north-east side are $A_{V,\mathrm{core}}=1.2\pm0.3$ mag $A_{V,\mathrm{wing}}>3.5$ mag, which highlights the severe extinction along the LOS for the broad component at optical wavelengths and weak signature in the \[OIII\] line on the north-east side of the nucleus. Based on the measured attenuations, we obtained extinction-corrected H$\alpha$ luminosities of $\log(L_{\mathrm{H}\alpha,\mathrm{core}}/[\mathrm{erg\,s}^{-1}])=40.79\pm0.04$ and $\log(L_{\mathrm{H}\alpha,\mathrm{wing}}/[\mathrm{erg\,s}^{-1}])=40.34\pm0.06$ on the south-west side and $\log(L_{\mathrm{H}\alpha,\mathrm{core}}/[\mathrm{erg\,s}^{-1}])=40.05\pm0.08$ and $\log(L_{\mathrm{H}\alpha,\mathrm{wing}}/[\mathrm{erg\,s}^{-1}])>40.85$ on the north-east side. Here, we face the issue that the luminosity of the wing component is highly uncertain on the North side due to the severe extinction. The electron density can be estimated from the \[S ii\] $\lambda\lambda$6717,6731 doublet line (cite: Osterbrock:2006), which is often the greatest obstacle to robustly measure the outflowing ionized gas mass as discussed in (cite: Harrison:2018), (cite: Kakkad:2018) and (cite: Rose:2018). Here, we are able to robustly deblend the \[S ii\] doublet into a narrow and broad component for both the south-west and north-east region. We measure an $\mathrm{S2}$=\[S ii\]$\lambda$6717/\[S ii\]$\lambda$6731 ratio of $\mathrm{S2}_\mathrm{core}=1.21\pm0.04$ and $\mathrm{S2}_\mathrm{wing}=0.73\pm0.12$ for the core and wing components in the south-west region, respectively, and $\mathrm{S2}_\mathrm{core}=1.20\pm0.14$ and $\mathrm{S2}_\mathrm{wing}=1.19\pm0.15$ for the north-east region. Assuming an electron temperature of $T_e\sim10\,000$ K, we estimate electron densities of $n_\mathrm{e,core}=198_{-41}^{+45}\mathrm{cm}^{-2}$ and $n_\mathrm{e,wing}=1500_{-670}^{+1700}\mathrm{cm}^{-2}$ for the south-west region and $n_\mathrm{e,core}=185_{-111}^{+172}\mathrm{cm}^{-2}$ and $n_\mathrm{e,wing}=214_{-130}^{+175}\mathrm{cm}^{-2}$ for the north-east region. Hence, we obtain ionized gas masses of $M_\mathrm{ion,core}=\left(1.1_{-0.2}^{+0.35}\right)\times10^{6}M_\ensuremath{\odot}$ and $M_\mathrm{ion,wing}=\left(0.5_{-0.3}^{+0.4}\right)\times10^{5}M_\ensuremath{\odot}$ in the south-west region and $M_\mathrm{ion,core}=\left(1.9_{-0.9}^{+2.5}\right)\times10^{5}M_\ensuremath{\odot}$ in the north-east region. Since the wing component of H$\beta$ remains undetected due to extreme obscuration towards the north-east region, we can only compute a lower limit on the ionized gas mass of $M_\mathrm{ion,wing}>1.1\times10^{6}M_\ensuremath{\odot}$ by applying the same extinction correction to the H$\alpha$ wing component as for the south-west region.

![](Fig13.pdf)

Based on the ro-vibrational H$_2$ \[1-0 S(1)\] NIR emission line we estimate the warm molecular gas mass following the prescription of (cite: Mezcua:2015), which assumes a temperature of 2000 K, a transition probability of $A=3.47\times10^{-7}\,\mathrm{s}^{-1}$ and population fraction of $f=0.0122$. The leads to a mass conversion of $$\begin{equation}
 M_\mathrm{warm} = 5.088\times10^{13}\left(\frac{D_L}{\mathrm{Mpc}}\right)^2\left(\frac{f_{\mathrm{H}_2\mathrm{\,[1-0 S(1)]}}}{\mathrm{erg\,s\,cm}^{-2}}\right)M_\ensuremath{\odot}
\end{equation}$$ Although the H$_2$ \[1-0 S(1)\] shows only one kinematic component in our NIFS observations, it is most likely associated with the outflow as the kinematics are close to those of the molecular gas wing component. We estimate warm-molecular gas outflow masses of $M_\mathrm{warm}=370\pm37 M_\ensuremath{\odot}$ for the south-west region and $M_\mathrm{warm}=250\pm25 M_\ensuremath{\odot}$ under the assumption stated above. Since those gas masses are orders of magnitude less than the outflowing ionized and molecular gas masses, the warm-molecular gas does not significantly contribute to outflow energetics and mass outflow rate budgets. We therefore ignore this gas-phase for the discussion of the outflow energy budget in the following.

We estimate the cold molecular gas from the CO luminosity following the prescription of (cite: Davis:2015): $$\begin{equation}
 M_\mathrm{mol} = 3.93\times10^{-17}X_\mathrm{CO}\left(\frac{D_L}{\mathrm{Mpc}}\right)^2\left(\frac{f_\mathrm{CO(1-0)}}{\mathrm{Jy\,km\,s}^{-1}}\right)
\end{equation}$$ for which we choose a conversion factor of $X_{\rm CO}=2\times10^{20}\,\mathrm{cm}^{-2}(\mathrm{K\,km\,s}^{-1}\mathrm{pc}^2)^{-1}$ as a typical value for massive spiral galaxies like our Milky Way in the nearby Universe. This yields molecular gas masses of $M_\mathrm{mol,core}=(1.8\pm0.11)\times10^8M_\odot$ and $M_\mathrm{mol,winge}=(0.84\pm0.25)\times10^8M_\odot$ for the south-west region and $M_\mathrm{mol,core}=(0.9\pm0.2)\times10^8M_\odot$ and $M_\mathrm{mol,wing}=(1.0\pm0.3)\times10^8M_\odot$ for the north-east region. However, the conversion factor is the greatest source of systematic uncertainties and the conditions of the gas in the fast moving clouds is still matter of debate with a lower limit provided by optically-thin gas at a temperature of T$_{ex}=30$ K corresponding to X$_{\rm CO}$= 1.6$\times 10^{19}\,\mathrm{cm}^{-2}(\mathrm{K\,km\,s}^{-1}\mathrm{pc}^2)^{-1}$. While several studies have found significantly higher conversion factors for the outflowing molecular gas (cite: Cicone:2018b; Walter:2017; Zschaechner:2018) also optically-thin conditions have been reported (cite: Dasyra:2016; Oosterloo:2017). Hence, our molecular gas estimates for the putative outflows could be at most an order of magnitude lower and represent a hard lower limit.

Mass outflow rates have often be computed using the assumption of a homogeneously filled cone (cite: Fiore:2017) with a size $R_\mathrm{out}$ which leads to $$\begin{equation}
 \dot M_\mathrm{out,cone} = 3\times \left(\frac{v_\mathrm{out}}{100\,\mathrm{km\,s}^{-1}}\right)\left(\frac{M_\mathrm{out}}{10^7M_\ensuremath{\odot}}\right)\left(\frac{1\,\mathrm{kpc}}{R_\mathrm{out}}\right) \,M_\ensuremath{\odot}\,\mathrm{yr}^{-1}
\end{equation}$$ where $v_\mathrm{out}$ is the outflow velocity for which different measurements have been assumed in the literature, which strongly depends on which part of the line shape is assumed to be participating in the outflow. A maximum velocity was defined by (cite: Rupke:2013) to be $v_\mathrm{max} = v_\mathrm{broad}+2\times\sigma_\mathrm{broad}$ instead of $v_\mathrm{broad}$ alone for the bulk motion of the broad component. Alternatively, non-parametric line shape measurements of the entire line shape have been used to define $v_{10}$, the velocity containing 10% of the line flux, and $W_{80}$, the width of the line between 10 and 90% of the line flux. We list all those outflow velocity parameters in Table [3](#tab:kin_parameters). While for $v_\mathrm{max}$ and $v_\mathrm{broad}$ only the mass in the broad component is considered, $v_{10}$ and $W_{80}$ are often used with the gas mass inferred from the entire line shape.

In the specific case of HE 1353$-$1917 it seems that a filled cone geometry is not a good assumption because our spatially-resolved kinematic mapping suggests an expanding shell-like shock front scenario that is propagating through the galaxy. In this case the mass outflow rate can be described as $$\begin{equation}
 \dot M_\mathrm{out,shell} = \left(\frac{v_\mathrm{out}}{100\,\mathrm{km\,s}^{-1}}\right)\left(\frac{M_\mathrm{out}}{10^6M_\ensuremath{\odot}}\right)\left(\frac{100\,\mathrm{pc}}{\Delta R}\right) \,M_\ensuremath{\odot}\,\mathrm{yr}^{-1}
\end{equation}$$ which implicitly represents the localized outflow rate at the shell distance from the nucleus independent of the outflow opening angle. The shell-thickness $\Delta R$ cannot be directly measured from our observations of HE 1353-1917 at our given spatial resolution. For the outflow energy in Table [\[tab:energetics\]](#tab:energetics) we adopt a thickness of $\Delta R=200$ pc, but parametrize the thickness within a range of 20 and 500 pc in Fig. [13](#fig:energetics). In addition to the mass outflow rate we also compute the momentum injection rate $\dot p_\mathrm{out}=v_\mathrm{out}\dot M_\mathrm{out}$ and kinetic energy injection rate as $\dot E_\mathrm{kin}=0.5v^2_\mathrm{out}\dot M_\mathrm{out}$. The turbulent motion is implicitly considered in all outflow velocity definitions except for $v_\mathrm{br}$ for which we add $\sigma_\mathrm{br}$ in quadrature to be comparable.

We visualize the results in Fig. [13](#fig:energetics) for $\dot M_\mathrm{out}$, $\dot p_\mathrm{out}$ and $\dot E_\mathrm{kin}$ for the shell and cone geometry, various outflow velocities and the ionized and total gas phases. Since there is a one order of magnitude systematic uncertainty on the molecular gas mass depending on the actual $X_\mathrm{CO}$ factor in the outflow we show them as bands in all panels. To separate the ionized gas and total gas mass is important for various reasons, 1) most observations of AGN are only able to measure the ionized gas energetics, 2) the molecular and ionized gas have different kinematics, and 3) it is unclear what fraction of the broad component in the molecular gas is caused by an outflow or governed by internal galaxy structure, such as a circumnuclear ring. This already tells us that even with our high-quality measurements computation of outflow energetics is hard and strongly model dependent. While we have taken out the uncertainty on the electron density for the ionized gas, the definition of outflow velocity, geometry and $X_\mathrm{CO}$ still leads to order of magnitude uncertainties.

Nevertheless, we can draw some solid conclusions from the data. The total mass outflow rate already exceeds the total SFR independent of $X_\mathrm{CO}$ or geometry. The total mass-loading factor $\eta=\dot M/\mathrm{SFR}$ therefore ranges between $\sim$1–30, if the molecular gas is indeed outflowing. Given that the outflow is still confined to the central kpc, the mass-loading factor would further increase by at least an order of magnitude if the SFR would be taken from the same region. Compared to the ionized gas the molecular phase clearly dominates $\dot M_\mathrm{out}$ even at much lower speed, which implies $\eta<1$ (for the total SFR) for the ionized gas phase alone for all cases when the shell thickness is $\Delta R>100$ pc. The difference in the momentum injection rate $\dot p_\mathrm{out}$ and the kinetic energy injection $\dot E_\mathrm{out}$ is significantly reduced between the ionized and molecular outflow due to the higher outflow velocity of the ionized gas phase. Our observations are consistent with $\dot p_\mathrm{out}\sim L_\mathrm{bol}/c$ only for the cone geometry, if $X_\mathrm{CO}$ is on the low side, and for the ionized gas phase if $\Delta R>300$ pc. For the shell geometry we find $\dot p_\mathrm{out}> L_\mathrm{bol}/c$ if $\Delta R<100\,pc$  independent of $X_\mathrm{CO}$. A caveat here is that the covering factor of the spherical AGN luminosity is significantly smaller than 1. Assuming a vertical height of $\pm250$ pc for the outflow at 1 kpc distance means that the covering factor is only 25%, which would imply a momentum boost for radiation pressure only of $>1$ for the total $\dot p_\mathrm{out}$ in all cases.

Only $\sim 1\%$ of the total bolometric luminosity is required to explain the estimated kinetic energy injection rates $\dot E_\mathrm{kin}$ in the outflow for all cases where $\Delta R>300$ pc. Taking into account the covering factor would bring this to 4%. Hence, the AGN radiation may indeed be able to drive the outflow if such a fraction of the luminosity can be efficiently transferred to the gas in the disc. However, we also see a radio jet impinging on the gas disc. We convert the inferred radio luminosity at 1.4 GHz from our VLA observations at 10 GHz to a kinetic jet power of $\log(P_\mathrm{jet}/[\mathrm{erg\,s}^{-1}])=43.3$ based on the calibration by (cite: Cavagnolo:2010), which is nearly equal to $0.1L_\mathrm{bol}$. The radio jet alone would therefore also be able to mechanically drive the outflow with just 10% of coupling efficiency as seen in Fig. [13](#fig:energetics).

# Discussion

## The origin of the large extended narrow-line region

One of the most prominent feature seen in the MUSE data is the extended narrow-line region (ENLR) where AGN photoionized gas can be traced out several tens of kpc to the limits of the MUSE FoV. The two-side geometry combined with a prior on the AGN orientation through the type 1 AGN classification implies that the geometry of the ENLR is driven by the opening angle and orientation of the AGN ionization cone fully consistent in line with the unification model of AGN (cite: Antonucci:1993; Urry:1995). However, various ENLR studies usually find that the ENLR is bound to the galaxy in the majority of cases as the AGN illuminates primarily the ISM (cite: Bennert:2002; Schmitt:2003b; Netzer:2004; Husemann:2013a; Hainline:2013; Husemann:2014). There is only a minority of cases reported where the ENLR significantly reaches beyond the galaxy which have been explained by the illumination of gas accretion flows from the environment (cite: Husemann:2011; Johnson:2018), gas debris or filaments due to past or ongoing galaxy interaction (cite: Villar-Martin:2010; daSilva:2011; Husemann:2016a; Storchi-Bergmann:2018; Villar-Martin:2018), or large-scale gas outflows (cite: Greene:2012; Liu:2013).

For HE 1353$-$1917 we have presented a number of measurements that let us draw a conclusive picture for the origin of the ionized gas a few kpc above the galaxy disc. The gas kinematics show that the ENLR shares the same direction of the angular momentum vector as the gas and stars of the disc without any signatures of counter-rotation. The LOS velocity amplitude on both sides of the ENLR is slightly smaller than that of the gas in the disc at the same radial distance along the plane. This could in principle be a signature of an additional velocity component (like an outflow) or simply an inclination effect since the ionization cone cannot be fully perpendicular to our line-of-sight given that we observe an unobscured AGN nucleus.

Additionally, the metallicity gradients along the galaxy disc and along the ENLR ionization cone axis are in good agreement. This is evidence against an outflow scenario because the metal enriched gas from the center would be ejected so that we would expect a significant increase of metals along the ENLR with respect to the galaxy disc. That the ENLR follows the metallicity gradient of the disc strongly suggests that the material in the ENLR was expelled nearly vertically from the disc and thereby retains a similar metallicity pattern as well as the same angular momentum as a function of radius. Hence, the AGN-illuminated gas above the plane is tightly connected to the disc properties as a function of radius. Stellar mass loss and supernova-driven winds is a natural explanation for the coupled similar kinematics and metal enrichment. However, the velocity dispersion in the extra-planar gas is much smaller than in typical starburst-driven winds (cite: Ho:2014; Ho:2016). This means that the outflow is significantly weaker or that the gas is already falling back after a short burst in star formation a few Myr ago. Both scenarios agree with the small amount of illuminated ionized gas $10^5M_\ensuremath{\odot}$ and the unusual star formation activity in the disc.

## Origin of the compact ring-like gas structure

Another striking feature in our data is the enhancement of velocity dispersion in the cold gas and shocked-heated H$_2$ gas in two symmetric regions around the nucleus (Fig. [11](#fig:outflow_maps)), which also resembles a ring-like structure seen edge-on. Such a ring-like structure is tentatively supported by a deficit of ionized gas (Br$\gamma$, Pa$\alpha$, or \[FeII\]) seen in the high-angular resolution Gemini observations (Fig. [6](#fig:NIFS_maps)). This is not affacted by the AGN subtraction as the PSF is significantly narrower than the apparent diameter of the ring. Given the orientation of the ionized gas outflow and the edge-on nature of this galaxy, there are several scenarios that may cause such a ring structure.

HE 1353$-$1917 is one of the few cases, such as NGC 1068 (cite: Garcia-Burillo:2014; Gallimore:2016) or NGC 5643 (cite: Alonso-Herrero:2018; Cresci:2015b), where the ionization cones and jet axis are directly intercepting the cold gas of the galaxy. Hence, one potential scenario is that the AGN-driven outflow has been pushing the gas outwards for some time. This scenario is attractive to support the impact of AGN outflow, since a multi-phase outflow and a radio jet within the depleted gas disc is clearly detected. However, this scenario assumes that the cold gas disc was initially homogenous and reaching down to the cricumnuclear scales of a few pc.

Alternatively, the outflow is impinging on a pre-existing nuclear ring with a diameter of 2.3$''$ or 1.6 kpc seen edge-on. The position-velocity diagram of Fig. [10](#fig:pV-diagram) indeed can be interpreted as a typical signature for a nuclear ring rather than a pure outflow. The velocity signature of a ring is a straight and steep line in the center, as can be seen in our own Milky-Way central molecular zone for example (cite: Yusef-Zadeh:2009), with a ring of 200 pc radius. Other examples of edge-on rings are M82 (cite: Neininger:1998) or NGC 4565 (cite: Yim:2014). Obviously, it is more easy to identify nuclear rings when not edge-on, like in NGC 1433 (cite: Combes:2013), NGC 1068 (cite: Garcia-Burillo:2014) or NGC 1097 (cite: Martin:2015).

These rings are thought to be due to the gravity torques of a bar, driving gas toward the centre, where it accumulates transiently into a ring at the inner Lindbald resonance of the bar (cite: Buta:1996). The ring is then massive, and produces some kinematic decoupling with a characteristic feature in PVDs. When the barred galaxies are associated to a low-luminosity AGN (Seyfert, LINER), it is frequent to see also a molecular outflow, as revealed in the references above. Weak outflows are usually not the origin of such ring structure, which pre-existed the nuclear activity. However, we cannot detect a bar due to the inclination of the galaxy so we cannot test if the ring is matching with the expected Lindbald resonance. Alternatively, the turbulent regime at the galaxy centre with a turbulent Taylor number of ${\rm Ta_t} \equiv v_{\rm rot}/\sigma_v < 1$ will lead to inelastic collisions of gas clouds enhancing their condensation fostering rapid feeding of the BH (cite: Gaspari:2017). Whether the molecular gas in the ring has already being pushed outwards by the outflow or acts as a stiff barrier for the outflow given its mass and density is still unclear at this point. In the following section we assume nevertheless that most of the high dispersion in the molecular phase is associated with an outflow to compute the associated outflow energetics.

## The powering source of the multi-phase gas outflow

In contrast to the large ENLR on tens of kpc scales, the prominent multi-phase gas outflow in HE 1353$-$1917 is confined to the inner $\sim$1 kpc from the nucleus. This is a large size for the outflow compared to what we find in other CARS targets (Singha et al. in prep.). HE 1353$-$1917 is therefore an ideal laboratory to understand the driving mechanisms for this outflow as we could make relatively precise estimations of the outflow energetics from our multi-wavelength observations. One big question is whether these outflows are radiatively driven by the AGN radiation or mechanically driven by a jet even in radio-quiet AGN (cite: Wylezalek:2018b).

![](Fig14.pdf)

Considering the energetics of the outflow in comparison to the AGN bolometric luminosity and the jet power as shown in Fig. [13](#fig:energetics) it seems that both the AGN and the radio jet are capable of powering the outflow. Yet, the jet power is already highly directional and the size of the jet exactly matches with the location of the warm molecular gas and the turbulent molecular gas. Since only a fraction of the AGN luminosity would impact the disc, the dissipation of the radiation into kinetic energy would need to be much more efficient than 1% to power the entire multi-phase outflow. Indeed, the orientation of the jet axis such that it almost exactly intercepts the gas disc is uncommon which makes HE 1353$-$1917 a rare case. However, similar examples have been reported before such as IC 5063 (cite: Kulkarni:1998; Morganti:2013; Tadhunter:2014; Morganti:2015; Dasyra:2015; Dasyra:2016; Oosterloo:2017), 3C 293 (cite: Emonts:2005; Mahony:2013; Mahony:2016) or NGC 3079 (cite: Duric:1988; Irwin:1992; Veilleux:1994; Cecil:2001; Middelberg:2007). In all cases, high turbulent velocities have been found at the hot spots of radio jets.

A spatial coincidence of radio jet morphology and velocity dispersion of the ionized gas has already been reported for spatially-resolved spectroscopy of more luminous radio-quiet AGN (cite: Husemann:2013a; Villar-Martin:2017) and powerful compact radio sources (cite: Roche:2016), but it has been correctly proposed that the fast moving plasma itself can lead to radio emission that mimics jet activity (cite: Zakamska:2014; Hwang:2018). In the case of HE 1353$-$1917 we can rule out that the ionized plasma is creating the radio emission because the high-velocity ionized gas traced by \[O iii\] is significantly displaced compared to the observed jet-like radio emission. Hence, we think that the radio jet is transferring its energy and momentum to the ambient medium through an extended shock front which creates turbulence in a dense clumpy interstellar medium. Such a great impact of the radio jet has been observationally shown in many cases (cite: Villar-Martin:1999b; ODea:2002; Nesvadba:2006; Holt:2008; Guillard:2012; Villar-Martin:2014; Harrison:2015; Santoro:2018; Tremblay:2018) and theoretically supported through detailed hydrodynamic simulations (cite: Krause:2007; Sutherland:2007; Wagner:2011; Wagner:2012; Cielo:2018; Mukherjee:2018). As we discussed in Sect. [3.6](#sect:gas_kin), the jet power alone is sufficient to energetically drive the outflow because only a small fraction of the AGN luminosity would impact the thin disc of the galaxy implying conversion efficiencies of more than 10% of $L_\mathrm{bol}$. (cite: Hopkins:2010b) proposed a two-stage process for efficient radiation-driven outflows. They describe a scenario in which an initial weak wind in the hot gas phase, possibly initiated by an accretion disc wind or a radio jet, creates additional turbulence in the surrounding medium so that massive gas clouds will subsequently expand and disperse. This expansion of gas clouds would significantly increase their apparent cross-section with respect to incident radiation field of the AGN. Such a two-stage process may increase the coupling efficiency by an order of magnitude. While we cannot directly confirm this process with our observations, the close alignment of the jet axis and the ionization cone greatly suggest that the outflow is driven jointly by both mechanical and radiative energy with an unknown ratio of the two. The open question is whether the same powerful outflow could have developed without the fast radio jet impacting the cold gas directly given its unique orientation.

Recent compilations of ionized (cite: Fiore:2017) and molecular (cite: Fluetsch:2019) outflows found a significant correlation with outflow kinetic power and AGN luminosity. (cite: Fiore:2017) assumed a conical outflow geometry with $v_\mathrm{max}$ as the outflow velocity, while (cite: Fluetsch:2019) used the average thin shell approximation that is systematically smaller by a factor of 3. In Fig. [14](#fig:outflows_literature) we compare the literature measurements re-computed for a conical outflow geometry with our conical outflow measurements for HE 1353$-$1917 using $v_\mathrm{max}$ as in Table [\[tab:energetics\]](#tab:energetics). We find that the mass outflow rates and kinetic power of the outflow measured for HE 1353$-$1917 is fully consistent with the clear trends between outflow energetics and AGN luminosity as found in previous studies. While we argue that a conical geometry is an inappropriate description for the outflow it is still valid for a homogenous relative comparison between different sample measurements where spatial information is limited. Although this could be taken as evidence that the outflow must be driven by the AGN luminosity, the fact that the radio jet clearly contributes to the AGN outflow cautions against this simple interpretation. Since the radio luminosity correlates with optical AGN luminosity even for radio-quiet AGN the relative contribution to the outflow is not clear and is not sufficiently probed in the current literature. Statistically, (cite: Mullaney:2013) and (cite: Villar-Martin:2014) argued for a significant role of radio jets in driving ionized gas outflows whereas (cite: Woo:2016) attributes this to simple sample selection effects. Only spatially-resolved mapping of the multi-phase outflows in relation to radio jet morphology and AGN ionization cones as presented here will be able to disentangle the relative importance of both mechanisms as discussed in (cite: Wylezalek:2018b).

![](Fig15.pdf)

## Implications for AGN feedback

The direct suppression of star formation caused by large-scale AGN-driven winds is one potential mechanism to regulate the growth of massive galaxies. While the cold gas in disc galaxies is hard to destroy when the outflow expands perpendicular to the disc (cite: Gabor:2014), the outflow in HE 1353$-$1917 is orientated such that it is directly impacting the cold gas disc. Hence, we would expect the efficiency of negative AGN feedback, i.e. suppression of star formation, to be maximized at the given outflow energy. In Fig. [15](#fig:mass_SFR) we compare the sSFR and the associated cold gas depletion time ($t_\mathrm{dep}$) of HE 1353$-$1917 with the overall distribution of local non-AGN galaxies from SDSS (cite: Brinchmann:2004) and the COLDGASS survey (cite: Saintonge:2011). We find that HE 1353$-$1917 is nearly matching galaxies in the star-forming main sequence pointing against negative AGN feedback caused by the outflow.

However, we also find a significant difference between the sSFR based on the FIR and H$\alpha$-based SFR tracers where the FIR-based sSFR is closer to the star-forming main sequence than the H$\alpha$-based SFR. The difference is a factor of 2, which is significant considering the measurement errors. As pointed out by (cite: Hayward:2014), the FIR-based SFRs may over-predict the SFR in galaxies undergoing star formation suppression, because the FIR emission is excited by stars with life times of up to $\sim$100 Myr and may not react on SFR changes on much smaller timescales. Here, we also compute the SFR based on the AGN core subtracted 1.4GHz radio luminosity and the radio-SFR calibration by (cite: Bell:2003). The SFR range between 2.8 $M_\ensuremath{\odot}\,\mathrm{yr}^{-1}$ and 10 $M_\ensuremath{\odot}\,\mathrm{yr}^{-1}$ for an assumed range in spectral index of $-1.2<\alpha<-0.5$. This suggest that the SFR has remained nearly constant till a few tens of Myr as probed by radio emission. Since the H$\alpha$ line can only be excited by stars with life times of up to $\sim$Myr it is much more sensitive to more rapid SFR variations than the FIR or the radio. This timescale effect has been detected in merging galaxies where the SFR is enhanced on small timescale at close galaxy separation which is only recovered in H$\alpha$ and not in the longer timescales SFR tracers (cite: Davies:2015). Considering a time scale of at most a few Myr years for the AGN phase in HE 1353$-$1917 and the associated impact on the surrounding medium, it is plausible that the difference in the SFR is caused by the same timescale effect. On the contrary, the H$\alpha$ luminosity may be particularly prone to the systematics of dust extinction given the edge-on view we have on HE1353$-$1917, which may also cause the discrepancy in the SFRs.

In any case, the impact of the current powerful AGN-driven outflow in HE 1353$-$1917 on *the total* SFR and star formation efficiency is small and nearly indistinguishable from the parent population of non-AGN galaxies. This is in agreement with several works finding that AGN host galaxies have similar star formation properties as their non-AGN counterparts (cite: Harrison:2012b; Husemann:2014; Xu:2015; Balmaverde:2016; Vaddi:2016; Zhang:2016; Suh:2017; Rosario:2018; Shangguan:2018), while others report a significant decrease in the SFR (cite: Farrah:2012; Mullaney:2015; Shimizu:2015; Wylezalek:2016) for different kind of AGN samples.

# Summary and conclusions

In this paper we presented an extensive spatially-resolved multi-wavelength investigation of the edge-on disc galaxy HE 1353$-$1917 hosting a luminous AGN. The observations offer unique insights into the interaction of an AGN with its host galaxy. Our main results can be summarized as follows:

- HE 1353$-$1817 reveals a large biconical ENLR which extends about 25 kpc nearly parallel to the galaxy disc. Considering the kinematics and the metallicity of the ionized gas we conclude that the gas likely originated from the galaxy disc and was vertically lifted by stellar mass loss and supernovae on several Myr timescales. Without the illumination by the AGN such low-density diffuse gas would be a neutral gas phase and undetectable at optical wavelengths.

- A fast multi-phase outflow about $\sim$1 kpc away from the nucleus is detected in the ionized gas ($v_\mathrm{max}\sim1000$km/s) and molecular gas ($v_\mathrm{max}\sim300$km/s). This region of the outflow appears as a distinct feature in the PVD and is coincident with jet-like radio emission at 10 GHz as detected with the VLA. Warm molecular emission is also directly associated with the radio jet location. This co-location implies that the ISM is heated directly through a fast moving shock, which is hitting the dense, cold gas disc of the galaxy. The cold gas has possibly formed a ring structure dynamically at this radius, created through a bar or other internal mechanisms, such as chaotic cold accretion.

- Despite the great uncertainties in computing outflow energetics, we can confirm that the molecular gas phase would dominate the mass outflow rate if a ring structure is not dominating the observed cold gas kinematics. In the most pessimistic case the mass outflow rate is $\dot M>2M_\odot\,\mathrm{yr}^{-1}$ and may be as high as $\dot M\sim200M_\odot\,\mathrm{yr}^{-1}$ implying a mass loading factor greater than unity.

- It is unclear whether the momentum injection rate of the outflow is consistent with $\dot p = L_\mathrm{bol}/c$ or requires a momentum boost as suggested for many other AGN-driven outflows. However, the power in the radio jet is sufficient to drive the outflow alone, so that the outflow is not necessarily radiatively driven. While indeed 5% of the total AGN luminosity would be sufficient to power the outflow as well, the geometric covering factor of the AGN radiation field intercepting the gas disc is almost an order of magnitude lower which implies that the radiation alone may not be able to power the outflow.

- The ionized and molecular mass outflow rates and the associated kinetic outflow power for HE 1353$-$1917 is fully in line with previous trends with AGN luminosity as found in larger samples of AGN host galaxies.

- The host galaxy of HE 1353$-$1917 is still on the star-forming main sequence based on FIR and radio continuum diagnostics which would not imply strong negative or positive feedback by the outflow. However, we detect a mild reduction in the SFR by a factor of 2 when estimated from the extinction-corrected and ionization-corrected H$\alpha$ luminosity. It is unclear at this point if this implies a recent reduction of the SFR in the last 5 Myr (H$\alpha$) compared to 100 Myr (FIR) or if a large fraction of the H$\alpha$ luminosity is missed by the high attenuation of dust due to edge-on orientation of the galaxy.

Our study of HE 1353$-$1917 demonstrates the unique potential of CARS to unravel the details of multi-phase AGN-driven outflows, their driving mechanism and impact on the host galaxies. This single-object study shows how the different observations can be combined to provide a complete picture of the galaxy characteristics. While it is difficult to make general conclusions for the overall AGN population from a single object study, there are a few important points to be drawn from this initial investigation, which will drive further studies from the overall CARS sample.

A striking feature is the orientation of the AGN ionization cones and the radio jet axis which directly intercept the cold gas disc of this galaxy. This orientation effect certainly maximizes the efficiency of the AGN to drive a massive outflow that already reaches out to distance of 1 kpc from the nucleus. The direct spatial coincidence of the radio jet with the fast outflow suggests a dominant role of the jet power in driving the outflow which is confirmed based on the outflow energetics. Nevertheless, the impact of the outflow on the SFR is still very mild and may at most affect the central kpc at very recent times. Whether AGN feedback can significantly reduce the molecular gas content and SFR of the entire disc on longer timescales is unclear at this point.

Considering that the outflow rates and energetics of HE 1353$-$1917 are in agreement with estimates for larger AGN samples from the literature, we may pose the question whether the previous trends with AGN luminosity can be considered as unambiguous evidence for radiatively-driven AGN outflows. Systematic investigations of the connection between small-scale low-power radio jets and the multi-phase outflows are still lacking for many existing samples. One of the primary goals of CARS is therefore to systematically explore the relative role of jets and radiation as the powering mechanisms of AGN-driven outflows and its impact on star formation.

# Acknowledgements

We thank the referee for providing very valuable comments which significantly improved the quality of the manuscript. MK acknowledges support from DLR grant 50OR1802. GRT acknowledges support from the NASA through Einstein Postdoctoral Fellowship Award Number PF-150128, issued by the Chandra X-ray Observatory Center, which is operated by the Smithsonian Astrophysical Observatory for and on behalf of NASA under contract NAS8-03060. MG is supported by the Lyman Spitzer Jr. Fellowship (Princeton University) and by NASA Chandra grants GO7-18121X/GO8-19104X. SMC acknowledges support from the Australian Research Council (DP190102714). We thank Alex Markowitz for helpful discussions on the RGS data in the context of warm absorbers. The work of SAB, CPO and MS was supported by a generous grant from the Natural Sciences and Engineering Research Council of Canada.

Based on observations collected at the European Organization for Astronomical Research in the Southern Hemisphere under ESO programme 095.B-0015(A).Based on observations obtained at the Gemini Observatory, which is operated by the Association of Universities for Research in Astronomy, Inc., under a cooperative agreement with the NSF on behalf of the Gemini partnership: the National Science Foundation (United States), National Research Council (Canada), CONICYT (Chile), Ministerio de Ciencia, Tecnología e Innovación Productiva (Argentina), Ministério da Ciência, Tecnologia e Inovação (Brazil), and Korea Astronomy and Space Science Institute (Republic of Korea). Based on observations obtained at the Southern Astrophysical Research (SOAR) telescope, which is a joint project of the Ministério da Ciência, Tecnologia, Inovações e Comunicações (MCTIC) do Brasil, the U.S. National Optical Astronomy Observatory (NOAO), the University of North Carolina at Chapel Hill (UNC), and Michigan State University (MSU). Based on observations collected at the German-Spanish Astronomical Center, Calar Alto, jointly operated by the Max-Planck-Institut für Astronomie Heidelberg and the Instituto de Astrofísica de Andalucía (CSIC). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00952.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work is based on observations obtained with XMM-Newton, an ESA science mission with instruments and contributions directly funded by ESA Member States and NASA. The VLA is operated by the National Radio Astronomy Observatory, a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. *Herschel* is an ESA space observatory with science instruments provided by European-led Principal Investigator consortia and with important participation from NASA. This publication makes use of data products from the Wide-field Infrared Survey Explorer, which is a joint project of the University of California, Los Angeles, and the Jet Propulsion Laboratory/California Institute of Technology, funded by the National Aeronautics and Space Administration. This research has made use of the NASA/IPAC Infrared Science Archive, which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration. The Pan-STARRS1 Surveys (PS1) and the PS1 public science archive have been made possible through contributions by the Institute for Astronomy, the University of Hawaii, the Pan-STARRS Project Office, the Max-Planck Society and its participating institutes, the Max Planck Institute for Astronomy, Heidelberg and the Max Planck Institute for Extraterrestrial Physics, Garching, The Johns Hopkins University, Durham University, the University of Edinburgh, the Queen’s University Belfast, the Harvard-Smithsonian Center for Astrophysics, the Las Cumbres Observatory Global Telescope Network Incorporated, the National Central University of Taiwan, the Space Telescope Science Institute, the National Aeronautics and Space Administration under Grant No. NNX08AR22G issued through the Planetary Science Division of the NASA Science Mission Directorate, the National Science Foundation Grant No. AST-1238877, the University of Maryland, Eotvos Lorand University (ELTE), the Los Alamos National Laboratory, and the Gordon and Betty Moore Foundation. This work is based in part on observations made with the Galaxy Evolution Explorer (GALEX). GALEX is a NASA Small Explorer, whose mission was developed in cooperation with the Centre National d’Etudes Spatiales (CNES) of France and the Korean Ministry of Science and Technology. GALEX is operated for NASA by the California Institute of Technology under NASA contract NAS5-98034.

254 natexlab

(ref: Alloin:1979) Alloin, D., Collin-Souffrin, S., Joly, M., & Vigroux, L. 1979, A&A, 78, 200

(ref: Alonso-Herrero:2018) Alonso-Herrero, A., Pereira-Santaella, M., Garcı́a-Burillo, S., et al. 2018, ApJ, 859, 144

(ref: Antonucci:1993) Antonucci, R. 1993, ARA&A, 31, 473

(ref: Arnaud:1996) Arnaud, K. A. 1996, in Astronomical Data Analysis Software and Systems V, Vol. 101, 17

(ref: Bacon:2010) Bacon, R., Accardo, M., Adjali, L., et al. 2010, SPIE Conf. Ser., 7735, 8

(ref: Bacon:2017) Bacon, R., Conseil, S., Mary, D., et al. 2017, A&A, 608, A1

(ref: Bacon:2014a) Bacon, R., Vernet, J., Borisova, E., et al. 2014, The Messenger, 157, 13

(ref: Bae:2016) Bae, H.-J. & Woo, J.-H. 2016, ApJ, 828, 97

(ref: Baldwin:1981) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5

(ref: Balmaverde:2016) Balmaverde, B., Marconi, A., Brusa, M., et al. 2016, A&A, 585, A148

(ref: Baron:2019) Baron, D. & Netzer, H. 2019, MNRAS, 482, 3915

(ref: Baumeister:2008) Baumeister, H., Alter, M., Cárdenas Vázquez, M. C., et al. 2008, in Proc. SPIE, Vol. 7014, Ground-based and Airborne Instrumentation for Astronomy II, 70142R

(ref: Bell:2003) Bell, E. F., McIntosh, D. H., Katz, N., & Weinberg, M. D. 2003, ApJS, 149, 289

(ref: Bennert:2002) Bennert, N., Falcke, H., Schulz, H., Wilson, A. S., & Wills, B. J. 2002, ApJL, 574, L105

(ref: Benson:2003) Benson, A. J., Bower, R. G., Frenk, C. S., et al. 2003, ApJ, 599, 38

(ref: Bertram:2007) Bertram, T., Eckart, A., Fischer, S., et al. 2007, A&A, 470, 571

(ref: Bianchi:2014) Bianchi, L., Conti, A., & Shiao, B. 2014, Advances in Space Research, 53, 900

(ref: Bieri:2017) Bieri, R., Dubois, Y., Rosdahl, J., et al. 2017, MNRAS, 464, 1854

(ref: Bigiel:2011) Bigiel, F., Leroy, A. K., Walter, F., et al. 2011, ApJL, 730, L13

(ref: Bischetti:2017) Bischetti, M., Piconcelli, E., Vietri, G., et al. 2017, A&A, 598, A122

(ref: Blundell:1998) Blundell, K. M. & Beasley, A. J. 1998, MNRAS, 299, 165

(ref: Bower:2006) Bower, R. G., Benson, A. J., Malbon, R., et al. 2006, MNRAS, 370, 645

(ref: Brinchmann:2004) Brinchmann, J., Charlot, S., White, S. D. M., et al. 2004, MNRAS, 351, 1151

(ref: Buta:1996) Buta, R. & Combes, F. 1996, , 17, 95

(ref: CalistroRivera:2016) Calistro Rivera, G., Lusso, E., Hennawi, J. F., & Hogg, D. W. 2016, ApJ, 833, 98

(ref: Cappellari:2002) Cappellari, M. 2002, MNRAS, 333, 400

(ref: Cappellari:2003) Cappellari, M. & Copin, Y. 2003, MNRAS, 342, 345

(ref: Cardelli:1989) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245

(ref: Carniani:2015) Carniani, S., Marconi, A., Maiolino, R., et al. 2015, A&A, 580, A102

(ref: Carniani:2016) Carniani, S., Marconi, A., Maiolino, R., et al. 2016, A&A, 591, A28

(ref: Cattaneo:2006) Cattaneo, A., Dekel, A., Devriendt, J., Guiderdoni, B., & Blaizot, J. 2006, MNRAS, 370, 1651

(ref: Cavagnolo:2010) Cavagnolo, K. W., McNamara, B. R., Nulsen, P. E. J., et al. 2010, ApJ, 720, 1066

(ref: Cecil:2001) Cecil, G., Bland-Hawthorn, J., Veilleux, S., & Filippenko, A. V. 2001, ApJ, 555, 338

(ref: Chambers:2016) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, ArXiv e-prints \[\]

(ref: Cicone:2018) Cicone, C., Brusa, M., Ramos Almeida, C., et al. 2018a, Nature Astronomy, 2, 176

(ref: Cicone:2014) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: Cicone:2018b) Cicone, C., Severgnini, P., Papadopoulos, P. P., et al. 2018b, ApJ, 863, 143

(ref: Cielo:2018) Cielo, S., Bieri, R., Volonteri, M., Wagner, A. Y., & Dubois, Y. 2018, MNRAS, 477, 1336

(ref: Cohen:2007) Cohen, M. H., Lister, M. L., Homan, D. C., et al. 2007, ApJ, 658, 232

(ref: Combes:2013) Combes, F., Garcı́a-Burillo, S., Casasola, V., et al. 2013, A&A, 558, A124

(ref: Costa:2014) Costa, T., Sijacki, D., & Haehnelt, M. G. 2014, MNRAS, 444, 2355

(ref: Crain:2015) Crain, R. A., Schaye, J., Bower, R. G., et al. 2015, MNRAS, 450, 1937

(ref: Crenshaw:2000) Crenshaw, D. M. & Kraemer, S. B. 2000, ApJL, 532, L101

(ref: Cresci:2015) Cresci, G., Mainieri, V., Brusa, M., et al. 2015a, ApJ, 799, 82

(ref: Cresci:2015b) Cresci, G., Marconi, A., Zibetti, S., et al. 2015b, A&A, 582, A63

(ref: Croton:2006) Croton, D. J., Springel, V., White, S. D. M., et al. 2006, MNRAS, 365, 11

(ref: daSilva:2011) da Silva, R. L., Prochaska, J. X., Rosario, D., Tumlinson, J., & Tripp, T. M. 2011, ApJ, 735, 54

(ref: Dame:2011) Dame, T. M. 2011, ArXiv e-prints \[\]

(ref: Das:2006) Das, V., Crenshaw, D. M., Kraemer, S. B., & Deo, R. P. 2006, AJ, 132, 620

(ref: Dasyra:2015) Dasyra, K. M., Bostrom, A. C., Combes, F., & Vlahakis, N. 2015, ApJ, 815, 34

(ref: Dasyra:2016) Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016, A&A, 595, L7

(ref: Dave:2011) Davé, R., Oppenheimer, B. D., & Finlator, K. 2011, MNRAS, 415, 11

(ref: Davies:2015) Davies, L. J. M., Robotham, A. S. G., Driver, S. P., et al. 2015, MNRAS, 452, 616

(ref: Davies:2016) Davies, R. L., Groves, B., Kewley, L. J., et al. 2016, MNRAS, 462, 1616

(ref: Davis:2013) Davis, T. A., Alatalo, K., Bureau, M., et al. 2013a, MNRAS, 429, 534

(ref: Davis:2013b) Davis, T. A., Bureau, M., Cappellari, M., Sarzi, M., & Blitz, L. 2013b, Nature, 494, 328

(ref: Davis:2015) Davis, T. A., Rowlands, K., Allison, J. R., et al. 2015, MNRAS, 449, 3503

(ref: Denney:2009) Denney, K. D., Peterson, B. M., Dietrich, M., Vestergaard, M., & Bentz, M. C. 2009, ApJ, 692, 246

(ref: DiPompeo:2018) DiPompeo, M. A., Hickox, R. C., Carroll, C. M., et al. 2018, ApJ, 856, 76

(ref: Doi:2013) Doi, A., Asada, K., Fujisawa, K., et al. 2013, ApJ, 765, 69

(ref: Duric:1988) Duric, N. & Seaquist, E. R. 1988, ApJ, 326, 574

(ref: Emonts:2005) Emonts, B. H. C., Morganti, R., Tadhunter, C. N., et al. 2005, MNRAS, 362, 931

(ref: Emsellem:1994) Emsellem, E., Monnet, G., & Bacon, R. 1994, A&A, 285, 723

(ref: Fabian:2012) Fabian, A. C. 2012, ARA&A, 50, 455

(ref: Farrah:2012) Farrah, D., Urrutia, T., Lacy, M., et al. 2012, ApJ, 745, 178

(ref: Faucher-Giguere:2012) Faucher-Giguère, C.-A. & Quataert, E. 2012, MNRAS, 425, 605

(ref: Ferruit:1999) Ferruit, P., Wilson, A. S., Falcke, H., et al. 1999, MNRAS, 309, 1

(ref: Feruglio:2015) Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99

(ref: Feruglio:2010) Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155

(ref: Fiore:2017) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: Fischer:2013) Fischer, T. C., Crenshaw, D. M., Kraemer, S. B., & Schmitt, H. R. 2013, ApJS, 209, 1

(ref: Fluetsch:2019) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: Fu:2009) Fu, H. & Stockton, A. 2009, ApJ, 690, 953

(ref: Gabor:2014) Gabor, J. M. & Bournaud, F. 2014, MNRAS, 441, 1615

(ref: Gallimore:2016) Gallimore, J. F., Elitzur, M., Maiolino, R., et al. 2016, ApJL, 829, L7

(ref: Garcia-Burillo:2014) García-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: Gaspari:2013) Gaspari, M., Brighenti, F., & Ruszkowski, M. 2013, Astronomische Nachrichten, 334, 394

(ref: Gaspari:2018) Gaspari, M., McDonald, M., Hamer, S. L., et al. 2018, ApJ, 854, 167

(ref: Gaspari:2017b) Gaspari, M. & Sądowski, A. 2017, ApJ, 837, 149

(ref: Gaspari:2017) Gaspari, M., Temi, P., & Brighenti, F. 2017, MNRAS, 466, 677

(ref: Genel:2014) Genel, S., Vogelsberger, M., Springel, V., et al. 2014, MNRAS, 445, 175

(ref: Gibson:2009) Gibson, R. R., Jiang, L., Brandt, W. N., et al. 2009, ApJ, 692, 758

(ref: Greene:2005) Greene, J. E. & Ho, L. C. 2005, ApJ, 630, 122

(ref: Greene:2011) Greene, J. E., Zakamska, N. L., Ho, L. C., & Barth, A. J. 2011, ApJ, 732, 9

(ref: Greene:2012) Greene, J. E., Zakamska, N. L., & Smith, P. S. 2012, ApJ, 746, 86

(ref: Griffin:2010) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3

(ref: Groves:2006) Groves, B. A., Heckman, T. M., & Kauffmann, G. 2006, MNRAS, 371, 1559

(ref: Guillard:2012) Guillard, P., Ogle, P. M., Emonts, B. H. C., et al. 2012, ApJ, 747, 95

(ref: Hainline:2013) Hainline, K. N., Hickox, R., Greene, J. E., Myers, A. D., & Zakamska, N. L. 2013, ApJ, 774, 145

(ref: Harrison:2012b) Harrison, C. M., Alexander, D. M., Mullaney, J. R., et al. 2012, ApJL, 760, L15

(ref: Harrison:2016b) Harrison, C. M., Alexander, D. M., Mullaney, J. R., et al. 2016, MNRAS, 456, 1195

(ref: Harrison:2014) Harrison, C. M., Alexander, D. M., Mullaney, J. R., & Swinbank, A. M. 2014, MNRAS, 441, 3306

(ref: Harrison:2018) Harrison, C. M., Costa, T., Tadhunter, C. N., et al. 2018, Nature Astronomy, 2, 198

(ref: Harrison:2015) Harrison, C. M., Thomson, A. P., Alexander, D. M., et al. 2015, ApJ, 800, 45

(ref: Hayward:2014) Hayward, C. C., Lanz, L., Ashby, M. L. N., et al. 2014, MNRAS, 445, 1598

(ref: Heckman:1981) Heckman, T. M., Miley, G. K., van Breugel, W. J. M., & Butcher, H. R. 1981, ApJ, 247, 403

(ref: Ho:2014) Ho, I.-T., Kewley, L. J., Dopita, M. A., et al. 2014, MNRAS, 444, 3894

(ref: Ho:2016) Ho, I.-T., Medling, A. M., Bland-Hawthorn, J., et al. 2016, MNRAS, 457, 1257

(ref: Holt:2008) Holt, J., Tadhunter, C. N., & Morganti, R. 2008, MNRAS, 387, 639

(ref: Hopkins:2010b) Hopkins, P. F. & Elvis, M. 2010, MNRAS, 401, 7

(ref: Humphrey:2010) Humphrey, A., Villar-Martı́n, M., Sánchez, S. F., et al. 2010, MNRAS, 408, L1

(ref: Husemann:2016a) Husemann, B., Bennert, V. N., Scharwächter, J., Woo, J.-H., & Choudhury, O. S. 2016a, MNRAS, 455, 1905

(ref: Husemann:2014) Husemann, B., Jahnke, K., Sánchez, S. F., et al. 2014, MNRAS, 443, 755

(ref: Husemann:2016c) Husemann, B., Scharwächter, J., Bennert, V. N., et al. 2016b, A&A, 594, A44

(ref: Husemann:2017b) Husemann, B., Tremblay, G., Davis, T., et al. 2017, The Messenger, 169, 42

(ref: Husemann:2011) Husemann, B., Wisotzki, L., Jahnke, K., & Sánchez, S. F. 2011, A&A, 535, A72

(ref: Husemann:2013a) Husemann, B., Wisotzki, L., Sánchez, S. F., & Jahnke, K. 2013, A&A, 549, A43

(ref: Hwang:2018) Hwang, H.-C., Zakamska, N. L., Alexandroff, R. M., et al. 2018, MNRAS, 477, 830

(ref: Ibanez:2012) Ibáñez, J.-M., Garcı́a Segura, A. J., Storz, C., et al. 2012, in Proc. SPIE, Vol. 8451, Software and Cyberinfrastructure for Astronomy II, 84511E

(ref: Irwin:1992) Irwin, J. A. & Sofue, Y. 1992, ApJL, 396, L75

(ref: Jahnke:2004b) Jahnke, K., Kuhlbrodt, B., & Wisotzki, L. 2004, MNRAS, 352, 399

(ref: Johnson:2018) Johnson, S. D., Chen, H.-W., Straka, L. A., et al. 2018, ApJ, 869, L1

(ref: Kakkad:2018) Kakkad, D., Groves, B., Dopita, M., et al. 2018, A&A, 618, A6

(ref: Kakkad:2016) Kakkad, D., Mainieri, V., Padovani, P., et al. 2016, A&A, 592, A148

(ref: Kang:2018) Kang, D. & Woo, J.-H. 2018, ApJ, 864, 124

(ref: Karouzos:2016) Karouzos, M., Woo, J.-H., & Bae, H.-J. 2016, ApJ, 819, 148

(ref: Kauffmann:2003) Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055

(ref: Kewley:2002) Kewley, L. J. & Dopita, M. A. 2002, ApJS, 142, 35

(ref: Kewley:2008) Kewley, L. J. & Ellison, S. L. 2008, ApJ, 681, 1183

(ref: Kewley:2006) Kewley, L. J., Groves, B., Kauffmann, G., & Heckman, T. 2006, MNRAS, 372, 961

(ref: King:2003) King, A. 2003, ApJL, 596, L27

(ref: King:2011) King, A. R., Zubovas, K., & Power, C. 2011, MNRAS, 415, L6

(ref: Koenig:2009) König, S., Eckart, A., Garcı́a-Marı́n, M., & Huchtmeier, W. K. 2009, A&A, 507, 757

(ref: Kovacevic:2010) Kovačević, J., Popović, L. Č., & Dimitrijević, M. S. 2010, ApJS, 189, 15

(ref: Krause:2007) Krause, M. & Alexander, P. 2007, MNRAS, 376, 465

(ref: Kukula:1998) Kukula, M. J., Dunlop, J. S., Hughes, D. H., & Rawlings, S. 1998, MNRAS, 297, 366

(ref: Kulkarni:1998) Kulkarni, V. P., Calzetti, D., Bergeron, L., et al. 1998, ApJL, 492, L121

(ref: Laing:1988) Laing, R. A. 1988, Nature, 331, 149

(ref: Leipski:2006a) Leipski, C. & Bennert, N. 2006, A&A, 448, 165

(ref: Leipski:2006b) Leipski, C., Falcke, H., Bennert, N., & Hüttemeister, S. 2006, A&A, 455, 161

(ref: Lequeux:1983) Lequeux, J. 1983, A&A, 125, 394

(ref: Leroy:2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: Leung:2017) Leung, G. C. K., Coil, A. L., Azadi, M., et al. 2017, ApJ, 849, 48

(ref: Liu:2014) Liu, G., Zakamska, N. L., & Greene, J. E. 2014, MNRAS, 442, 1303

(ref: Liu:2013) Liu, G., Zakamska, N. L., Greene, J. E., Nesvadba, N. P. H., & Liu, X. 2013a, MNRAS, 430, 2327

(ref: Liu:2013b) Liu, G., Zakamska, N. L., Greene, J. E., Nesvadba, N. P. H., & Liu, X. 2013b, MNRAS, 436, 2576

(ref: Magnier:2016) Magnier, E. A., Schlafly, E. F., Finkbeiner, D. P., et al. 2016, ArXiv e-prints \[\]

(ref: Mahony:2013) Mahony, E. K., Morganti, R., Emonts, B. H. C., Oosterloo, T. A., & Tadhunter, C. 2013, MNRAS, 435, L58

(ref: Mahony:2016) Mahony, E. K., Oonk, J. B. R., Morganti, R., et al. 2016, MNRAS, 455, 2453

(ref: Marconi:2004) Marconi, A., Risaliti, G., Gilli, R., et al. 2004, MNRAS, 351, 169

(ref: Marino:2013) Marino, R. A., Rosales-Ortega, F. F., Sánchez, S. F., et al. 2013, A&A, 559, A114

(ref: Martin:2005) Martin, C. L. 2005, ApJ, 621, 227

(ref: Martin:2015) Martín, S., Kohno, K., Izumi, T., et al. 2015, A&A, 573, A116

(ref: Martinsson:2013) Martinsson, T. P. K., Verheijen, M. A. W., Westfall, K. B., et al. 2013, A&A, 557, A131

(ref: McElroy:2015) McElroy, R., Croom, S. M., Pracy, M., et al. 2015, MNRAS, 446, 2186

(ref: McGregor:2003) McGregor, P. J., Hart, J., Conroy, P. G., et al. 2003, in Proc. SPIE, Vol. 4841, Instrument Design and Performance for Optical/Infrared Ground-based Telescopes, ed. M. Iye & A. F. M. Moorwood, 1581–1591

(ref: McMullin:2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mezcua:2015) Mezcua, M., Prieto, M. A., Fernández-Ontiveros, J. A., et al. 2015, MNRAS, 452, 4128

(ref: Middelberg:2007) Middelberg, E., Agudo, I., Roy, A. L., & Krichbaum, T. P. 2007, MNRAS, 377, 731

(ref: Mingozzi:2019) Mingozzi, M., Cresci, G., Venturi, G., et al. 2019, A&A, 622, A146

(ref: Mommert:2017) Mommert, M. 2017, Astronomy and Computing, 18, 47

(ref: Morganti:2013) Morganti, R., Frieswijk, W., Oonk, R. J. B., Oosterloo, T., & Tadhunter, C. 2013, A&A, 552, L4

(ref: Morganti:2015) Morganti, R., Oosterloo, T., Oonk, J. B. R., Frieswijk, W., & Tadhunter, C. 2015, A&A, 580, A1

(ref: Morganti:2005) Morganti, R., Tadhunter, C. N., & Oosterloo, T. A. 2005, A&A, 444, L9

(ref: Mukherjee:2018) Mukherjee, D., Bicknell, G. V., Wagner, A. Y., Sutherland, R. S., & Silk, J. 2018, MNRAS, 479, 5544

(ref: Mullaney:2015) Mullaney, J. R., Alexander, D. M., Aird, J., et al. 2015, MNRAS, 453, L83

(ref: Mullaney:2013) Mullaney, J. R., Alexander, D. M., Fine, S., et al. 2013, MNRAS, 433, 622

(ref: Neininger:1998) Neininger, N., Guelin, M., Klein, U., Garcia-Burillo, S., & Wielebinski, R. 1998, A&A, 339, 737

(ref: Nesvadba:2006) Nesvadba, N. P. H., Lehnert, M. D., Eisenhauer, F., et al. 2006, ApJ, 650, 693

(ref: Netzer:2004) Netzer, H., Shemmer, O., Maiolino, R., et al. 2004, ApJ, 614, 558

(ref: Noll:2014) Noll, S., Kausch, W., Kimeswenger, S., et al. 2014, A&A, 567, A25

(ref: ODea:2002) O’Dea, C. P., de Vries, W. H., Koekemoer, A. M., et al. 2002, AJ, 123, 2333

(ref: Oh:2018) Oh, K., Koss, M., Markwardt, C. B., et al. 2018, ApJS, 235, 4

(ref: Oosterloo:2017) Oosterloo, T., Raymond Oonk, J. B., Morganti, R., et al. 2017, A&A, 608, A38

(ref: Osterbrock:2006) Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei (2nd. ed. by D.E. Osterbrock and G.J. Ferland. Sausalito, CA: University Science Books, 2006)

(ref: Ostriker:2010) Ostriker, J. P., Choi, E., Ciotti, L., Novak, G. S., & Proga, D. 2010, ApJ, 722, 642

(ref: Perez-Montero:2009) Pérez-Montero, E. & Contini, T. 2009, MNRAS, 398, 949

(ref: Perna:2015) Perna, M., Brusa, M., Cresci, G., et al. 2015, A&A, 574, A82

(ref: Perna:2017) Perna, M., Lanzuisi, G., Brusa, M., Mignoli, M., & Cresci, G. 2017, A&A, 603, A99

(ref: Pettini:2004) Pettini, M. & Pagel, B. E. J. 2004, MNRAS, 348, L59

(ref: Pilbratt:2010) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1

(ref: Pogge:1988a) Pogge, R. W. 1988, ApJ, 328, 519

(ref: Poglitsch:2010) Poglitsch, A., Waelkens, C., Geis, N., et al. 2010, A&A, 518, L2

(ref: Pounds:2003) Pounds, K. A., Reeves, J. N., King, A. R., et al. 2003, MNRAS, 345, 705

(ref: Revalski:2018) Revalski, M., Dashtamirova, D., Crenshaw, D. M., et al. 2018, ApJ, 867, 88

(ref: Richards:2006) Richards, G. T., Lacy, M., Storrie-Lombardi, L. J., et al. 2006, ApJS, 166, 470

(ref: Riffel:2013) Riffel, R. A., Storchi-Bergmann, T., & Winge, C. 2013, MNRAS, 430, 2249

(ref: Roche:2016) Roche, N., Humphrey, A., Lagos, P., et al. 2016, MNRAS, 459, 4259

(ref: Rosario:2018) Rosario, D. J., Burtscher, L., Davies, R. I., et al. 2018, MNRAS, 473, 5658

(ref: Rose:2018) Rose, M., Tadhunter, C., Ramos Almeida, C., et al. 2018, MNRAS, 474, 128

(ref: Rupke:2017) Rupke, D. S. N., Gültekin, K., & Veilleux, S. 2017, ApJ, 850, 40

(ref: Rupke:2013) Rupke, D. S. N. & Veilleux, S. 2013, ApJL, 775, L15

(ref: Sabbadin:1977) Sabbadin, F., Minello, S., & Bianchini, A. 1977, A&A, 60, 147

(ref: Saintonge:2011) Saintonge, A., Kauffmann, G., Kramer, C., et al. 2011, MNRAS, 415, 32

(ref: Salucci:1991) Salucci, P., Ashman, K. M., & Persic, M. 1991, ApJ, 379, 89

(ref: Sanchez:2014) Sánchez, S. F., Rosales-Ortega, F. F., Iglesias-Páramo, J., et al. 2014, A&A, 563, A49

(ref: Santoro:2018) Santoro, F., Rose, M., Morganti, R., et al. 2018, A&A, 617, A139

(ref: Schirmer:2013) Schirmer, M., Diaz, R., Holhjem, K., Levenson, N. A., & Winge, C. 2013, ApJ, 763, 60

(ref: Schmitt:2003b) Schmitt, H. R., Donley, J. L., Antonucci, R. R. J., et al. 2003, ApJ, 597, 768

(ref: Shangguan:2018) Shangguan, J., Ho, L. C., & Xie, Y. 2018, ApJ, 854, 158

(ref: Shimizu:2015) Shimizu, T. T., Mushotzky, R. F., Meléndez, M., Koss, M., & Rosario, D. J. 2015, MNRAS, 452, 1841

(ref: Silk:1998) Silk, J. & Rees, M. J. 1998, A&A, 331, L1

(ref: Skrutskie:2006) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163

(ref: Somerville:2008) Somerville, R. S., Hopkins, P. F., Cox, T. J., Robertson, B. E., & Hernquist, L. 2008, MNRAS, 391, 481

(ref: Soto:2016) Soto, K. T., Lilly, S. J., Bacon, R., Richard, J., & Conseil, S. 2016, MNRAS, 458, 3210

(ref: Spoon:2013) Spoon, H. W. W., Farrah, D., Lebouteiller, V., et al. 2013, ApJ, 775, 127

(ref: Stasinska:2008) Stasińska, G., Vale Asari, N., Cid Fernandes, R., et al. 2008, MNRAS, 391, L29

(ref: Stern:2013) Stern, J. & Laor, A. 2013, MNRAS, 431, 836

(ref: Storchi-Bergmann:2018) Storchi-Bergmann, T., Dall’Agnol de Oliveira, B., Longo Micchi, L. F., et al. 2018, ApJ, 868, 14

(ref: Storchi-Bergmann:1998) Storchi-Bergmann, T., Schmitt, H. R., Calzetti, D., & Kinney, A. L. 1998, AJ, 115, 909

(ref: Storchi-Bergmann:1992) Storchi-Bergmann, T., Wilson, A. S., & Baldwin, J. A. 1992, ApJ, 396, 45

(ref: Storey:2000) Storey, P. J. & Zeippen, C. J. 2000, MNRAS, 312, 813

(ref: Sturm:2011) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: Suh:2017) Suh, H., Civano, F., Hasinger, G., et al. 2017, ApJ, 841, 102

(ref: Sun:2017) Sun, A.-L., Greene, J. E., & Zakamska, N. L. 2017, ApJ, 835, 222

(ref: Sutherland:2007) Sutherland, R. S. & Bicknell, G. V. 2007, ApJS, 173, 37

(ref: Tadhunter:2014) Tadhunter, C., Morganti, R., Rose, M., Oonk, J. B. R., & Oosterloo, T. 2014, Nature, 511, 440

(ref: Tadhunter:2018) Tadhunter, C., Rodrı́guez Zaurı́n, J., Rose, M., et al. 2018, MNRAS, 478, 1558

(ref: Tombesi:2010) Tombesi, F., Cappi, M., Reeves, J. N., et al. 2010a, A&A, 521, A57

(ref: Tombesi:2015) Tombesi, F., Meléndez, M., Veilleux, S., et al. 2015, Nature, 519, 436

(ref: Tombesi:2010b) Tombesi, F., Sambruna, R. M., Reeves, J. N., et al. 2010b, ApJ, 719, 700

(ref: Tremblay:2018) Tremblay, G. R., Combes, F., Oonk, J. B. R., et al. 2018, ApJ, 865, 13

(ref: Tremonti:2004) Tremonti, C. A., Heckman, T. M., Kauffmann, G., et al. 2004, ApJ, 613, 898

(ref: Ulvestad:2005) Ulvestad, J. S., Antonucci, R. R. J., & Barvainis, R. 2005, ApJ, 621, 123

(ref: Urry:1995) Urry, C. M. & Padovani, P. 1995, PASP, 107, 803

(ref: Vaddi:2016) Vaddi, S., O’Dea, C. P., Baum, S. A., et al. 2016, ApJ, 818, 182

(ref: Veilleux:2017) Veilleux, S., Bolatto, A., Tombesi, F., et al. 2017, ApJ, 843, 18

(ref: Veilleux:1994) Veilleux, S., Cecil, G., Bland-Hawthorn, J., et al. 1994, ApJ, 433, 48

(ref: Veilleux:2013) Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, ApJ, 776, 27

(ref: Veilleux:1987) Veilleux, S. & Osterbrock, D. E. 1987, ApJS, 63, 295

(ref: Verner:1996) Verner, D. A., Ferland, G. J., Korista, K. T., & Yakovlev, D. G. 1996, ApJ, 465, 487

(ref: Vestergaard:2006) Vestergaard, M. & Peterson, B. M. 2006, ApJ, 641, 689

(ref: Viironen:2007) Viironen, K., Delgado-Inglada, G., Mampaso, A., Magrini, L., & Corradi, R. L. M. 2007, MNRAS, 381, 1719

(ref: Villar-Martin:2016) Villar-Martı́n, M., Arribas, S., Emonts, B., et al. 2016, MNRAS, 460, 130

(ref: Villar-Martin:1999b) Villar-Martı́n, M., Binette, L., & Fosbury, R. A. E. 1999, A&A, 346, 7

(ref: Villar-Martin:2018) Villar-Martı́n, M., Cabrera-Lavers, A., Humphrey, A., et al. 2018, MNRAS, 474, 2302

(ref: Villar-Martin:2017) Villar-Martı́n, M., Emonts, B., Cabrera Lavers, A., et al. 2017, MNRAS, 472, 4659

(ref: Villar-Martin:2014) Villar Martı́n, M., Emonts, B., Humphrey, A., Cabrera Lavers, A., & Binette, L. 2014, MNRAS, 440, 3202

(ref: Villar-Martin:2010) Villar-Martı́n, M., Tadhunter, C., Pérez, E., et al. 2010, MNRAS, 407, L6

(ref: Wagner:2011) Wagner, A. Y. & Bicknell, G. V. 2011, ApJ, 728, 29

(ref: Wagner:2012) Wagner, A. Y., Bicknell, G. V., & Umemura, M. 2012, ApJ, 757, 136

(ref: Walcher:2015) Walcher, C. J., Coelho, P. R. T., Gallazzi, A., et al. 2015, A&A, 582, A46

(ref: Walker:2003) Walker, A. R., Boccas, M., Bonati, M., et al. 2003, The SOAR Optical Imager

(ref: Walter:2017) Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, ApJ, 835, 265

(ref: Waters:2016) Waters, C. Z., Magnier, E. A., Price, P. A., et al. 2016, ArXiv e-prints \[\]

(ref: Weaver:2018) Weaver, J., Husemann, B., Kuntschner, H., et al. 2018, A&A, 614, A32

(ref: Weilbacher:2012) Weilbacher, P. M., Streicher, O., Urrutia, T., et al. 2012, SPIE Conf. Ser., 8451

(ref: Weilbacher:2014) Weilbacher, P. M., Streicher, O., Urrutia, T., et al. 2014, in Astronomical Society of the Pacific Conference Series, Vol. 485, Astronomical Data Analysis Software and Systems XXIII, ed. N. Manset & P. Forshay, 451

(ref: Whittle:1985a) Whittle, M. 1985, MNRAS, 213, 1

(ref: Wilms:2000) Wilms, J., Allen, A., & McCray, R. 2000, ApJ, 542, 914

(ref: Wisotzki:2000) Wisotzki, L., Christlieb, N., Bade, N., et al. 2000, A&A, 358, 77

(ref: Woo:2016) Woo, J.-H., Bae, H.-J., Son, D., & Karouzos, M. 2016, ApJ, 817, 108

(ref: Woo:2017) Woo, J.-H., Son, D., & Bae, H.-J. 2017, ApJ, 839, 120

(ref: Woo:2015) Woo, J.-H., Yoon, Y., Park, S., Park, D., & Kim, S. C. 2015, ApJ, 801, 38

(ref: Wright:2010) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: Wylezalek:2018b) Wylezalek, D. & Morganti, R. 2018, Nature Astronomy, 2, 0181

(ref: Wylezalek:2016) Wylezalek, D. & Zakamska, N. L. 2016, MNRAS, 461, 3724

(ref: Xu:2015) Xu, L., Rieke, G. H., Egami, E., et al. 2015, ApJ, 808, 159

(ref: Yim:2014) Yim, K., Wong, T., Xue, R., et al. 2014, AJ, 148, 127

(ref: Yusef-Zadeh:2009) Yusef-Zadeh, F., Hewitt, J. W., Arendt, R. G., et al. 2009, ApJ, 702, 178

(ref: Zakamska:2014) Zakamska, N. L. & Greene, J. E. 2014, MNRAS, 442, 784

(ref: Zakamska:2016) Zakamska, N. L., Hamann, F., Pâris, I., et al. 2016, MNRAS, 459, 3144

(ref: Zhang:2016) Zhang, Z., Shi, Y., Rieke, G. H., et al. 2016, ApJL, 819, L27

(ref: Zschaechner:2018) Zschaechner, L. K., Bolatto, A. D., Walter, F., et al. 2018, ApJ, 867, 111

# Multi-wavelength data processing

## MUSE observations

HE 1353$-$1917 was observed with MUSE in the WFM-NOAO-N configuration during the night of June 20, 2015. The MUSE $1\ensuremath{'}\times1\ensuremath{'}$ field-of-view (FoV) is large enough to cover the entire optical extent of this edge-on disc-like galaxy. Three individual exposures with 300 s on-source integration time were taken including small dither offsets and 90$\ensuremath{^\circ}$ field rotation to reduce systematics. The observations were carried out with thin cirrus clouds passing and excellent seeing conditions with $0.6''$ (FWHM) as measured by the slow guiding system (SGS) within MUSE. As part of the standard calibration plan, a sequence of bias frames, arc lamp and continuum lamp exposures were taken at the end of the night and the standard star EG 153 was observed at the beginning of the night. In addition, a snapshot continuum lamp exposure was taken within an hour of the target observation to improve the temperature-dependent illumination correction across the MUSE FoV. A set of twilight exposures are available from the beginning of the previous night.

We reduced the data with standard MUSE pipeline (cite: Weilbacher:2012; Weilbacher:2014), which performs all the reduction steps till the creation of the flux-calibrated science cube. The process includes bias subtraction, wavelength calibration, flat-field correction, illumination correction across the field, sky subtraction, flux calibration and correction for differential atmospheric refraction before the reconstruction of the cube. Sky subtraction is performed based on the collapsed spectrum within the blank sky areas of the FoV. We further suppress the residuals of sky lines adopting a PCA analysis of the individual sky spectra in the blank sky area. Our custom-made PCA processing is similar but not identical to the PCA sky subtraction algorithm ZAP (cite: Soto:2016) and will be released with the CARS survey presentation article (Husemann et al. in prep.). The final cube has a spatial sampling of $0.2\ensuremath{''}$ and covers the wavelength range $4750\AA<\lambda<9300\AA$ at a spectral resolution of $\sim$2.5Å.

## Gemini NIFS observations

Near-infrared IFU data of the central $\sim 3\ensuremath{''}\times 3\ensuremath{''}$ were obtained with NIFS at Gemini-North as a Fast Turnaround project on 2017 April 6 and 7. The NIFS data were taken under natural seeing and non-photometric (CC70) conditions. The spectra cover the near-infrared $J$- and $K$-bands at spectral resolutions of $\sim$ 6040 and 5290, respectively. The data for each band were observed using 6 dithered on-source exposures of 600 s. Telluric standard stars (of type A0V) were observed at a similar airmass immediately before and after the science exposures, respectively.

he data for HE1353-1917 and the telluric calibration stars were reduced using standard tasks included in the Gemini IRAF Package (Version 1.14). The object exposures were interleaved with off-target sky exposures for sky subtraction. The object and sky exposures were flat-fielded and rectified spatially and spectrally. These data products were used as input to perform the sky subtraction using `Skycorr` (cite: Noll:2014). In order to correct for telluric absorption features, each sky-subtracted on-source exposure was divided by the telluric standard star spectrum observed closest in time and normalized by a black body spectrum of $T=9480$ K corresponding to the A0V stellar type. Hydrogen absorption lines, intrinsic to A0V stars, were deblended from the telluric spectra beforehand. The science data were flux calibrated based on the telluric standard stars by assuming their corresponding 2MASS $J$- and $K$-band fluxes. The six calibrated science data cubes per band were aligned by using the galaxy nucleus as a reference, median-combined, and binned to $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}1 \times 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}1$ pixels.

Given the non-photometric conditions, we compared the reconstructed $J$ and $K$ broad-band flux within a diameter of $3''$ from the NIFS datacubes with the corresponding flux in our PANIC NIR images (see Sect. [6.4](#sect:PANIC)). While the $K$ band flux agrees within the errors, we find a systemic offset in the $J$ band flux of 0.76. We multiplied the $J$ band NIFS data with this factor to correct for this empirically measured offset with respect to the 2MASS photometric system.

## SOAR optical imaging observations

We observed HE 1353$-$1917 with SOI (cite: Walker:2003) at the SOAR telescope using its set of Bessel $B$, $V$, and $R$ filters on 18 February 2016 as part of a follow-up imaging run for CARS. We integrated for 1200 s per filter over a four-point dither pattern. The data were reduced and combined with the `mscred` package in iraf. The three-color composite is shown in the top left panel of Fig. [1](#fig:overview).

From the reduced images we infer integrated magnitudes for HE 1353$-$1917 within an elliptical aperture ($r_\mathrm{major}=21.1\ensuremath{''}$ and $r_\mathrm{minor}=5.6\ensuremath{''}$) covering the entire galaxy. The resulting brightnesses are $m_B=15.88\pm0.05$ mag(AB), $m_V=15.2\pm0.01$ mag(AB), and $m_R=14.81\pm0.01$ mag(AB). The errors represent the zero-point uncertainties inferred from the standard star fields.

## PANIC Near-IR imaging observations

Deep NIR $JHKs$ images of HE 1353$-$1917 were obtained during the nights of 6-9 March 2017 with the PANIC at the 2.2m telescope of the Calar Alto Observatory. The target galaxy was positioned in the center of quadrant 1 of PANIC which offers the best cosmetics of the detector mosaic. A sequence of 16 dithered exposure with offsets of 1.5$'$ in between were obtained to aid background subtraction. The effective exposure times are 4600 s, 5000 s and 4500 s for the $J$, $H$ and $Ks$ filter, respectively, after removing bad frames due to clouds or satellite stripes. The observing conditions were overall good with a seeing in the range of 1–2$''$. The data was reduced with the dedicated Pipeline for PANIC (cite: Ibanez:2012) which performs dark subtraction, flat-fielding, background subtraction based on dithered exposures, astrometry based on star catalogs and co-addition of frames. We then use the software PhotometryPipeline (cite: Mommert:2017) to determine the zero-points for each co-added images based on cross-match with the 2MASS catalog (cite: Skrutskie:2006). We infer total brightnesses of $m_J=12.60\pm0.06$ mag(Vega), $m_H=11.82\pm0.06$ mag(Vega), and $m_{Ks}=11.30\pm0.06$ mag(Vega) within the same elliptical aperture as used for the SOAR images.

## ALMA observations

The $^{12}$CO(1–0) line in HE 1353$-$1917 was observed with ALMA on both the 3rd November and the 24th of December 2016 for 70.56 and 34.23 minutes in configurations C40-5 and C40-2, respectively. Combining these observations gives us sensitivity to emission on scales up to 22$.\!\!^{\prime\prime}$6. An 1850 MHz correlator window was placed over the $^{12}$CO(1–0) line, yielding a continuous velocity coverage of $\approx$3000 km s$^{-1}$ with a raw velocity resolution of $\approx$1 km s$^{-1}$. Three 2 GHz wide low-resolution correlator windows were simultaneously used to detect continuum emission.

The raw ALMA data were calibrated using the standard ALMA pipeline, as provided by the ALMA regional centre staff. Additional flagging was carried out where necessary to improve the data quality. Amplitude and bandpass calibration were performed using Ganymede and the quasar J1337-1257. J1400-1858 was used as the phase calibrator. We then used the `Common Astronomy Software Applications` (cite: McMullin:2007) package to combine and image the visibility files of the two tracks, producing a three-dimensional RA-Dec-velocity data cube (with velocities determined with respect to the rest frequency of the $^{12}$CO(1-0) line). In this work we primarily use data with a channel width of 50  km s$^{-1}$, and pixels of 0$.\!\!^{\prime\prime}$2 were chosen in order to approximately Nyquist sample the synthesized beam.

The data presented here were imaged using Briggs weighting with a robust parameter of 0.5, yielding a synthesized beam of 0$.\!\!^{\prime\prime}$64 $\times$ 0$.\!\!^{\prime\prime}$55 at a position angle of 71$^{\circ}$ (a physical resolution of 476 $\times$ 409 pc$^2$). Continuum emission was detected, measured over the full line-free bandwidth, and then subtracted from the data in the $uv$ plane using the `CASA` task `uvcontsub`. The achieved continuum root-mean square (RMS) noise is 9.3 $\mu$Jy. The continuum-subtracted dirty cubes were cleaned in regions of source emission (identified interactively) to a threshold equal to the RMS noise of the dirty channels. The clean components were then added back and re-convolved using a Gaussian beam with a FWHM equal to that of the dirty beam. This produced the final, reduced, and fully calibrated $^{12}$CO(1–0) data cubes, with RMS noise levels of 0.21 mJy beam$^{-1}$ in each 50 km s$^{-1}$ channel.

## VLA radio 10 GHz radio continuum

We observed HE 1353$-$1917 on 22 December 2016 with the VLA at X-band in the A configuration. The observations were centered at 10.0 GHz, with a synthesized bandwidth of 4 GHz (from 8 up to 12 GHz). We used the source 3C 286 for bandpass and absolute flux density calibration purposes. For phase calibration purposes, we used the nearby, bright sources J1357$-$1744. The total on-source time was approximately 40 min. We calibrated and imaged the data using the `CASA`, applying standard procedures. The resulting cleaned image with a spatial resolution of about 0.2$''$ is shown as contours in Fig. [1](#fig:overview). It reveals an apparently one-sided jet-like radio morphology with a size of about 1$''$. The peak flux density at the synthesized frequency of 10 GHz is of 241.1 $\mu$Jy/beam, and the total flux density is of about 728.6 $\mu$Jy, which are highly significant given an off-source rms of $12.5\,\mu$Jy/beam. The total radio flux at 10 GHz corresponds to a radio luminosity of $L_{10\mathrm{GHz}}=2.0\times10^{21}\,\mathrm{W Hz}^{-1}$ which corresponds to 1.4 GHz radio luminosities ranging from $L_{1.4\,\mathrm{GHz}}=5.3\times10^{21}\,\mathrm{W\,Hz}^{-1}$ to $L_{1.4\,\mathrm{GHz}}=2.5\times10^{22}\,\mathrm{W\,Hz}^{-1}$ considering a likely range of $-1.2<\alpha<-0.5$ spectral indices.

## VLA 1.7 GHz radio continuum and H I line

We observed HE 1353$-$1917 on 30 April 2016 with the VLA at L-band in the CnB configuration. The observations consist of 6 continuum sub-bands with $64\times2$ MHz channels each corresponding to a synthesized bandwidth of 730 MHz (from 1.2 up to 2.1 GHz with some gaps in between due to RFI). One sub-band with $512\times15.6$ kHz was set for line mapping centered on the redshifted H I. 3C 286 was used again as a bandpass and absolute flux density calibrator while Phase calibration was performed using the bright source J1351$-$1449. The total on-source time was approximately 90 min. The data was calibrated with `CASA` applying standard routines. The cleaned continuum and H I images have a spatial resolution of about $10.0\ensuremath{''}\times5.4\ensuremath{''}$ and are shown in Fig. [1](#fig:overview). Furthermore, continuum emission was detected and measured over the full H I line-free bandwidth and subsequently subtracted from the data in the $uv$ plane using the `CASA` task `uvcontsub`.

We detect spatially extended continuum emission from the host galaxy with a peak flux density of 3.8 mJy/beam with an off-source rms if $21.5\,\mu$Jy/beam. The integral flux density is 9.4 mJy which corresponds to a 1.4 GHz luminosity of $L_{1.4\,\mathrm{GHz}}=2.1\times10^{22}\,\mathrm{W\,Hz}^{-1}$ assuming a radio spectral index of $\alpha=-0.8$. Also extended H i emission was detected associated with the host galaxy of HE1353$-$1917 despite a non-detection with the Effelsberg radio telescope as reported by (cite: Koenig:2009). The integrated H i line spectrum over 2$'$ as obtained from the VLA is shown in Fig. [16](#fig:CO_HI_profile). We detect the H i line at $5\sigma$ significance with the right shape and a total line flux of $f_{\mathrm{H i}}=2.4\pm0.5\,\mathrm{Jy\,km\,s}^{-1}$.

![](Fig16.pdf)

## XMM-Newton X-ray observations

HE 1353$-$1917 was observed with *XMM-Newton* on 2017 August 8 with the EPIC cameras and RGS for 62 ksec. The spectra were extracted with the `SAS` package (16.1.0) and the `HEASOFT` (v6.21) using the standard setting for point sources. Since the small window mode was used, pile-up is not affecting the observations. We created a standard source and background spectrum in PN, MOS1, and MOS2. The spectra are grouped with a minimum binning of 20 counts. Standard source reductions procedures are also used for the RGS data.

We fit the X-ray spectra using `Xspec` version 12.9.1e (cite: Arnaud:1996) in the 0.3–12 keV energy range. We use the cosmic abundances of (cite: Wilms:2000) and the photoelectric absorption cross sections provided by (cite: Verner:1996). The best-fit model yields Galactic absorption-corrected fluxes of $f_\mathrm{0.5-2\,keV}=(3.40\pm0.02) \times 10^{-12}$ erg cm$^{-2}$ s$^{-1}$ and $f_\mathrm{2-10\,keV}=(5.97\pm0.03) \times 10^{-12}$ erg cm$^{-2}$ s$^{-1}$, which corresponds to rest-frame luminosities of $L_\mathrm{0.5-2\,keV}=(9.50\pm0.06) \times 10^{42}$ erg s$^{-1}$ and $L_\mathrm{2-10\,keV}=(1.69\pm0.01) \times 10^{43}$ erg s$^{-1}$. Using (cite: Marconi:2004) we estimate $L_{\rm bol}/L_{\rm 2-10\,keV}\sim 10$. Thus, we estimate a bolometric luminosity of $L_{\rm bol} = (1.7\pm0.6) \times 10^{44}$ erg s$^{-1}$.

![](Fig17.pdf)

HE 1353$-$1917 is also detected in the 105-month *Swift*-BAT All-sky hard X-ray Survey (cite: Oh:2018) with a total 14-195 keV flux of $f_{14-195~\mathrm{keV}}=1.39^{+0.34}_{-0.19}\times10^{-11}$ erg s$^{-1}$cm$^{-2}$ and a photon index of $\gamma=2.1^{+0.6}_{-0.5}$ (both quoting 90% confidence levels). This hard X-ray flux corresponds to a luminosity of $\log (L_{14-195~\mathrm{keV}}/[\mathrm{erg\,s}^{-1}]) = 43.5$.

## *Chandra* X-ray Observatory observations

We also observed HE 1353$-$1917 with the *Chandra X-ray Observatory*’s High Resolution Camera (HRC) as part of Guaranteed Time Observation (GTO) program 19700783 (PI: Kraft). The galaxy’s nucleus was placed on the nominal aim point of the HRC-I detector for the 39.62 ksec observation, imaging the source with the sharpest point spread function available to *Chandra* ($0.4\ensuremath{''}$ FWHM). Beyond the nuclear point source, which contains $\sim$15 000 counts in the 0.5–7 keV band, there is a $\sim$2$\sigma$ enhancement in total counts over the background level that forms a linear streak extending $\sim$6$''$ southwest of the nucleus (see Fig. [18](#fig:chandra), left panel). The number of counts in this feature is $\sim$0.4% of the total counts found in the nuclear PSF. The feature also happens to align exactly along the $U$-axis of the HRC-I detector, and therefore shares many characteristics with the well-known HRC “ghost image” artifact [^3]. Especially in the absence of any supporting multi-wavelength evidence it is most likely that this feature is indeed a detector artifact.

In search of any extended emission superposed on the nuclear point source, we extracted the radial profile of X-ray surface brightness from a series of 15 concentric annuli centered on the observation’s photo-centroid. Using the best-fit *XMM-Newton* X-ray spectrum (see Sect. [6.8](#sect:XMM_appendix)) as an input, we simulated the observation’s PSF using the Chandra Ray Tracer (`ChaRT`) and `marx` tools[^4]. We compared the radial profile extracted from the data with that from the modeled point spread function (Fig. [18](#fig:chandra), right panel) finding no evidence for any broadening from extended emission superposed upon the PSF.

![](Fig18.pdf)

There is, however, a semicircular arc, $\sim2\ensuremath{''}$ SW of the nucleus, along which we find a $\sim$10 count excess over the local semi-azimuthal average (see Fig. [19](#fig:chandra_excess)). Depending on the comparison aperture used, this feature represents only a $\sim$1.3–2$\sigma$ excess over the background-plus-PSF-wing level, and therefore cannot be ruled out as a background fluctuation. Nevertheless, the arc-like structure imposed by the excess counts is exactly co-spatial with the rim of the multiphase outflow discussed in this paper (compare, for example, the WCS-matched red circles in both panels of Fig. [19](#fig:chandra_excess)). If there is indeed an expanding hot cocoon or bubble draped about the rim of the cooler phases of the outflow, the faint semicircular arc arrangement of X-ray counts detected by *Chandra*/HRC are exactly where one would expect them to be. This feature is not consistent with any known HRC PSF artifact, and we have run a series of deep `ChaRT` ray tracing simulations to ensure that it might not be a subtle effect of, e.g., misaligned mirror pairs. The location and arrangement of these excess counts is therefore too compelling a coincidence to ignore, and certainly motivation for a deeper future observation with *Chandra*. While we in no way claim that this $<$2$\sigma$ feature is real, we suggest it is *possible* that we have detected signal from a hot bubble associated with the outflow. A significantly deeper observation with *Chandra* is certainly required to confirm this possibility.

![](Fig19.pdf)

# Archival multi-band data

## Mid-IR imaging with WISE

The Wide-field Infrared Survey Explorer (cite: Wright:2010) satellite performed an all-sky survey in three mid-IR pass bands at 3.4, 4.6, 12 and 22 $\mu$m at a spatial resolution of 6.1$''$, 6.4$''$, 6.5$''$, and 12.0$''$, respectively. We retrieved the *WISE* cut-out images centered on HE 1353$-$1917 from the NASA/IPAC Infrared Science Archive. The images in the first three bands are shown in Fig. [1](#fig:overview) in which the disc contribution below the bright AGN are well recognized even at the relatively low spatial resolution.

Additionally, we retrieve the single-frame PSF images that we use as template for modelling the images. Estimation of physical fluxes from the *WISE* images is performed following the *WISE* Photometric calibration following (cite: Wright:2010) and explained in section IV.h.i of the explanatory supplement[^5] in that paper.

## Far-IR imaging with Herschel

Far-IR imaging of HE 1353$-$1017 was obtained with *Herschel* (cite: Pilbratt:2010) with the instruments PACS (cite: Poglitsch:2010) at 70 and 160 $\mu$m and SPIRE (cite: Griffin:2010) at 250, 350 and 500 $\mu$m. The observations were taken in January 2012 as part of the programme “Determining the bolometric luminosities of AGN” (PI: R. Mushotzky) with the Observation IDs 1342237734, 1342237735, and 1342236189. We retrieve the public data through the *Herschel* science archive[^6]. The PSF increased with wavelength from $\sim$9 $''$ to $\sim$36 $''$ over the entire wavelength range. We therefore only show the PACS images in Fig. [1](#fig:overview) for which the spatial resolution is still sufficient to resolve the galaxy.

We performed simple aperture photometry of this isolated source to obtain integrated FIR fluxes for the galaxy. The galaxy is well detected in all band with $>5\sigma$ significance. We infer integrated 70 and 160 $\mu$m PACS fluxes of $204\pm18$ mJy and $659\pm82$ mJy, respectively. In the three SPIRE bands we measure integrated 250, 350 and 500 $\mu$m fluxes of $444\pm53$ mJy, $215\pm32$ mJy and $85\pm17$ mJy, respectively.

## Optical imaging from Pan-STARRS

The Panoramic Survey Telescope and Rapid Response System (cite: Chambers:2016) also covered HE 1353$-$1917 in the $g,r,i,z,y$ filters. From the Pan-STARRS data release 1[^7], we retrieved the fully processed and stacked cut-out image (cite: Waters:2016). The sampling of the images is 0.25$''$ with integration times of 792 s, 1372 s, 1639 s, 1080 s, and 1160 s for the $g$, $r$, $i$, $z$, $y$ filters, respectively. Adopting the same elliptical aperture as for the SOAR images, we obtained brightnesses of $m_g=15.55$ mag(AB), $m_r=14.67$ mag(AB), $m_i=14.39$ mag(AB), $m_z=14.10$ mag(AB) and $m_y=13.90$mag(AB) with a photometric error of roughly $0.02$ mag (cite: Magnier:2016).

## UV photometry with GALEX

The Galaxy Evolution Explorer (cite: Martin:2005) has performed an all-sky imaging survey (AIS) in two UV bands, 1350–1750Å (FUV channel) and 1750–2750Å (NUV channel). The AIS data is shallow with a sensitivity down to $m_\mathrm{AB}\lesssim20.5$ mag. The resolution implied by the point-spread function in the two bands is $4.9\ensuremath{''}$ and $4.2\ensuremath{''}$ in the NUV and FUV channel, which means that the images of HE 1353$-$1917 are dominated by the point-like emission of the AGN. From the GALEX Release 6/7 photometric catalogs (cite: Bianchi:2014) we retrieved the UV photometry for HE 1353$-$1917 in the two bands. With a total integration time per band of 225 s in the NUV and 114 s in the FUV, the reported fluxes are $0.180\pm0.006$ mJy in the NUV and $0.054\pm0.009$ mJy in the FUV channel.

[^1]: *Lyman Spitzer Jr.* Fellow

[^2]: freely available at <https://github.com/TimothyADavis/kinms>

[^3]: <http://cxc.harvard.edu/proposer/POG/html/chap7.html>

[^4]: <http://cxc.harvard.edu/ciao/threads/psf.html>

[^5]: <http://wise2.ipac.caltech.edu/docs/release/allsky/expsup/>

[^6]: <http://www.cosmos.esa.int/web/herschel/science-archive>

[^7]: available at <http://panstarrs.stsci.edu>

</paper>

## Items to check

```json
[
 {
  "path": "claims[0].evidence[0]",
  "value": "Fast bipolar multi-phase outflow, ~1 kpc scale",
  "failed_quote": "we conclude that we are detecting the signature of a fast bipolar multi-phase outflow driven by the AGN"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "sampler and priors not stated",
  "failed_quote": "(no quote given)"
 }
]
```
