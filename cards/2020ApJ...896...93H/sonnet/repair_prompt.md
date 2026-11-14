# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...896...93H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#  Large Population of ALMA Galaxies at $z>6$\
with Very High $88\mathrm{\mu m}$ to $158\mathrm{\mu m}$ Flux Ratios:\
Evidence of Extremely High Ionization Parameter or PDR Deficit?

## Abstract

We present our new ALMA observations targeting 88$\mu$m, 158$\mu$m, 122$\mu$m, and dust continuum emission for three Lyman break galaxies at $z=6.0293-6.2037$ identified in the Subaru/Hyper Suprime-Cam survey. We clearly detect and lines from all of the galaxies at $4.3-11.8\sigma$ levels, and identify multi-band dust continuum emission in two of the three galaxies, allowing us to estimate infrared luminosities and dust temperatures simultaneously. In conjunction with previous ALMA observations for six galaxies at $z>6$, we confirm that all the nine $z=6-9$ galaxies have high / ratios of $L_\mathrm{[OIII]}/L_\mathrm{[CII]}\sim3-20$, $\sim10$ times higher than $z\sim0$ galaxies. We also find a positive correlation between the / ratio and the Ly$\alpha$ equivalent width (EW) at the $\sim90\%$ significance level. We carefully investigate physical origins of the high / ratios at $z=6-9$ using Cloudy, and find that high density of the interstellar medium, low C/O abundance ratio, and the cosmic microwave background attenuation are responsible to only a part of the $z=6-9$ galaxies. Instead, the observed high / ratios are explained by $10-100$ times higher ionization parameters or low photodissociation region (PDR) covering fractions of $0-10\%$, both of which are consistent with our observations. The latter scenario can be reproduced with a density bounded nebula with PDR deficit, which would enhance the Ly$\alpha$, Lyman continuum, and $\mathrm{C^+}$ ionizing photons escape from galaxies, consistent with the /-Ly$\alpha$ EW correlation we find.

# Introduction

Understanding properties of the interstellar medium (ISM) is important for galaxy formation. The metallicity in the gas-phase (hereafter metallicity) can be a tracer of the past star formation history including gas inflow and outflow, because heavy elements produced in stars through star formation activities are returned into the ISM (cite: 2019A&ARv..27....3M). The ionization parameter, $q_\mathrm{ion}$, is also an important quantity that characterizes the ionization state in the ISM, defined by $$\begin{equation}
q_\mathrm{ion}=\frac{Q_0}{4\pi R^2_\mathrm{s} n_\mathrm{H}},
\end{equation}$$ in unit of $\mathrm{cm\ s^{-1}}$, where $Q_0$ and $n_\mathrm{H}$ are the hydrogen ionizing photon production rate and hydrogen density, respectively. $R_\mathrm{s}$ is the Strömgren radius defined by $$\begin{equation}
Q_\mathrm{0}=\frac{4}{3}R^3_\mathrm{s}n^2_\mathrm{H}\alpha_\mathrm{B}\epsilon,
\end{equation}$$ where $\alpha_\mathrm{B}$ and $\epsilon$ are the case B recombination rate and the volume filling factor, respectively. The ionization parameter is sometimes normalized by the light speed $c$, $$\begin{equation}
U_\mathrm{ion}=\frac{q_\mathrm{ion}}{c}.
\end{equation}$$ The ionization parameter can be also related to the escape fraction of ionizing photons that is key for cosmic reionization physics (cite: 2014MNRAS.442..900N).

Nebular emission lines are powerful tools to investigate the ISM properties of galaxies. Spectroscopic observations for rest-frame optical lines reveal that galaxies at $z\sim2-3$ have lower metallicities (cite: 2008A&A...488..463M), higher ionization parameters (cite: 2014MNRAS.442..900N), and higher densities (cite: 2015MNRAS.451.1284S; 2016ApJ...816...23S; 2017ApJ...835...88K), compared to local galaxies. However, it is difficult to study the ISM properties of higher redshift galaxies, especially at $z>5$, because commonly-used rest-frame optical emission lines, such as H$\alpha$, H$\beta$, $\lambda\lambda$4959,5007, and $\lambda\lambda$3726,3729 are redshifted out from the atmospheric window in the near-infrared, and ground-based telescopes cannot observe these lines. Although rest-frame ultraviolet (UV) metal lines such as 1907, Ciii\]1909 are used to study $z\sim6-8$ galaxies (cite: 2015MNRAS.454.1393S; 2015MNRAS.450.1846S; 2017MNRAS.464..469S), these lines are typically weak and not always detected (cite: 2018PASJ...70S..15S; 2018MNRAS.479.1180M). Broad-band photometry with the *Spitzer* Space Telescope gives some constraints on the rest-frame optical lines at $z>4$ (cite: 2016ApJ...821..122F; 2016ApJ...823..143R; 2018ApJ...859...84H), but this method can be used only for galaxies in limited redshift ranges. Spectroscopy for strong nebular lines is important for understanding the ISM properties of high redshift galaxies, but we need to wait for the launch of the James Webb Space Telescope for the rest-frame optical lines of $z>5$ galaxies.

Far-infrared (FIR) emission lines studied with Atacama Large Millimeter/Submillimeter Array (ALMA) are alternative tools to study the ISM of high redshift galaxies. Previous ALMA observations report surprisingly weak \[Cii\]158$\mu\mathrm{m}$ emission in Ly$\alpha$ emitters (LAEs) at $z\sim6-7$ compared to local galaxies with similar star formation rates (SFRs), known as the deficit (e.g., (cite: 2014ApJ...792...34O; 2015A&A...574A..19S; 2016MNRAS.462L...6K)). On the other hand, some Lyman break galaxies (LBGs) detected by ALMA at $z\sim5-7$ have \[Cii\] luminosity to SFR ratios ($L_{[\mathrm{CII}]}/SFR$) comparable to local galaxies (cite: 2015Natur.522..455C; 2016ApJ...829L..11P). This difference of the $L_{[\mathrm{CII}]}/SFR$ ratio may include key information of an evolution of the ISM properties from low redshift to high redshift. Based on these observations, (cite: 2018ApJ...859...84H) have identified an anti-correlation between $L_\mathrm{[CII]}/SFR$ and the Ly$\alpha$ equivalent width (EW), $\mathrm{EW^0_{Ly\alpha}}$, which is also reported in (cite: 2018MNRAS.478.1170C) and (cite: 2019ApJ...881..124M). Since the Ly$\alpha$ EW well correlates with the Ly$\alpha$ photon escape fraction (cite: 2017MNRAS.466.1242S; 2018ApJ...859...84H; 2019A&A...623A.157S), this anti-correlation indicates that the strength of the emission is related to the Ly$\alpha$ photon escape from galaxies.

The 88$\mu$m emission line is predicted to be detectable from $z>6$ galaxies with ALMA (cite: 2014ApJ...780L..18I), and indeed detected (cite: 2016Sci...352.1559I; 2017ApJ...837L..21L; 2017A&A...605A..42C; 2018Natur.557..392H; 2019ApJ...874...27T; 2019PASJ...71...71H), including the most distant emission line galaxy at $z=9.1096$ (cite: 2018Natur.557..392H). Given the high success rate of ALMA \[Oiii\] observations, the \[Oiii\] line is one of the most useful tracers for ISM properties at $z\gtrsim6$. Since \[Oiii\] has an ionization potential ($35.1\ \mathrm{eV}$) higher than \[Cii\] ($11.3\ \mathrm{eV}$), the \[Oiii\]/ ratio is useful to investigate ionization state. However, the number of galaxies with both \[Oiii\] and \[Cii\] observations is limited; for LBGs and LAEs currently only six galaxies are reported ((cite: 2016Sci...352.1559I; 2017ApJ...837L..21L; 2017A&A...605A..42C; 2018Natur.557..392H; 2019PASJ...71...71H; 2019ApJ...874...27T; 2019MNRAS.487L..81L; 2020MNRAS.493.4294B)).

ALMA observations have also begun to reveal complex nature of dust-obscured star formation in high redshift universe. Dust obscuration is usually quantified by the IR to UV luminosity ratio ($IRX=L_\mathrm{IR}/L_\mathrm{UV}$) as a function of the UV slope $\beta_\mathrm{UV}$ (IRX-$\beta_\mathrm{UV}$). Local starburst galaxies show a correlation between IRX and $\beta_\mathrm{UV}$ (cite: 1999ApJ...521...64M; 2000ApJ...533..682C), which is known as the Calzetti IRX-$\beta_\mathrm{UV}$ relation. (cite: 2012ApJ...755..144T) modified the Calzetti IRX-$\beta_\mathrm{UV}$ relation considering the aperture effect in the photometry in UV. The Small Magellanic Cloud (SMC) shows lower IRX values than the Calzetti relation, known as the SMC IRX-$\beta_\mathrm{UV}$ relation (cite: 1998ApJ...508..539P). *Herschel* and ALMA observations reveal that $z\sim2-5$ galaxies follow the Calzetti or SMC IRX-$\beta_\mathrm{UV}$ curves (cite: 2017MNRAS.472..483F; 2018ApJ...853...56R; 2018MNRAS.476.3991M; 2018MNRAS.479.4355K). On the other hand at $z>5$, some galaxies show IRX values significantly lower than these relations (cite: 2015Natur.522..455C; 2016ApJ...833...72B; 2017ApJ...845...41B), implying significant evolution of dust properties from $z\sim0$ to $z>5$ (cite: 2010A&A...523A..85G). There are several possibilities for the physical origin of the low IRX values in high redshift galaxies. One of the most important caveats is that dust temperatures are not determined in most of the galaxies at $z>5$, as discussed in several studies (cite: 2016ApJ...833...72B; 2017ApJ...847...21F; 2018MNRAS.477..552B). Since these galaxies are often observed in one single FIR band, the dust temperature ($T_\mathrm{dust}$) is usually assumed to local galaxy values to derive the IR luminosity. However, (cite: 2017ApJ...847...21F) point out that dust temperatures of high redshift galaxies could be significantly higher, which increases $L_\mathrm{IR}$ up to 0.6 dex with the higher dust temperature by $\Delta T_\mathrm{dust}=+40\ \mathrm{K}$, possibly resolving the tension between the models and observations (cite: 2019PASJ...71...71H; 2019ApJ...874...27T; 2019MNRAS.487L..81L). Additionally, using cosmological zoom in simulations (cite: 2017MNRAS.471.4128P), (cite: 2018MNRAS.477..552B) shows that 20% of the dust mass can be responsible for up to 80% of the IR luminosity, because of the high ($\sim$70 K) dust temperature due to the compactness and intense radiation field typical of high redshift galaxies. Thus we need to simultaneously constrain dust temperatures and IR luminosities with multi-band dust continuum observations.

In this study, we present our new ALMA observations targeting \[Oiii\]88$\mu$m, \[Cii\]158$\mu$m, \[Nii\]122$\mu$m, and multi-band dust continuum emission in three LBGs at $z\sim6$ that are identified in the Subaru/Hyper Suprime-Cam survey (cite: 2018PASJ...70S...4A). Optical spectroscopic observations have already detected Ly$\alpha$ emission lines in these galaxies (cite: 2018PASJ...70S..35M). In conjunction with previous ALMA observations for $z>5$ galaxies and Cloudy model calculations, we study ISM properties of the high redshift galaxies.

|  | J1211-0118 | J0235-0532 | J0217-0208 |
|:--:|:--:|:--:|:--:|
| R.A. | 12:11:37.112 | 02:35:42.412 | 02:17:21.603 |
| decl. | $-$01:18:16.500 | $-$05:32:41.623 | $-$02:08:52.778 |
| $M_\mathrm{UV}$ \[AB mag\] | $-22.8$ | $-22.8$ | $-23.3$ |
| $L_\mathrm{UV}$ \[$L_\odot$\] | $2.7\times10^{11}$ | $2.9\times10^{11}$ | $4.3\times10^{11}$ |
| $EW^0_\mathrm{Ly\alpha}$ \[$\mathrm{\AA}$\] | $6.9\pm0.8$ | $41\pm2$ | $15\pm1$ |
| $\beta_\mathrm{UV}$ | $-2.0\pm0.5$ | $-2.6\pm0.6$ | $-0.1\pm0.5$ |
| $z_\mathrm{[OIII]}$ | $6.0295\pm0.0009$ | $6.0906\pm0.0009$ | $6.2044\pm0.0013$ |
| $z_\mathrm{[CII]}$ | $6.0291\pm0.0008$ | $6.0894\pm0.0010$ | $6.2033\pm0.0009$ |
| $z_\mathrm{sys}$ | $6.0293\pm0.0002$ | $6.0901\pm0.0006$ | $6.2037\pm0.0005$ |
| $z_\mathrm{Ly\alpha}$ | $6.0339\pm0.0008$ | $6.0918\pm0.0002$ | $6.2046\pm0.0006$ |
| $\Delta v_\mathrm{Ly\alpha}\ [\mathrm{km\ s^{-1}}]$ | $196\pm35$ | $71\pm26$ | $37\pm32$ |
| $[$Oiii$]$ integrated flux \[Jy km s$^{-1}$\] | $2.69\pm0.40\ (6.7\sigma)$ | $2.10\pm0.18\ (11.8\sigma)$ | $4.57\pm1.06\ (4.3\sigma)$ |
| $[$Cii$]$ integrated flux \[Jy km s$^{-1}$\] | $1.42\pm0.15\ (9.5\sigma)$ | $0.43\pm0.07\ (5.9\sigma)$ | $1.36\pm0.20\ (6.7\sigma)$ |
| $[$Nii$]$ integrated flux \[Jy km s$^{-1}$\] | $<0.66\ (3\sigma)$ | $<0.90\ (3\sigma)$ | $<0.45\ (3\sigma)$ |
| $\mathrm{FWHM_{[OIII]}}$ \[km s$^{-1}$\] | $194\pm123$ | $389\pm117$ | $374\pm162$ |
| $\mathrm{FWHM_{[CII]}}$ \[km s$^{-1}$\] | $170\pm98$ | $270\pm135$ | $316\pm117$ |
| $L_\mathrm{[OIII]}\ [L_\odot]$ | $(4.8\pm0.7)\times10^{9}$ | $(3.8\pm0.3)\times10^{9}$ | $(8.5\pm2.0)\times10^{9}$ |
| $L_\mathrm{[CII]}\ [L_\odot]$ | $(1.4\pm0.1)\times10^{9}$ | $(4.3\pm0.7)\times10^{8}$ | $(1.4\pm0.2)\times10^{9}$ |
| $L_\mathrm{[NII]}\ [L_\odot]$ | $<8.3\times10^{8}$ | $<1.2\times10^{9}$ | $<6.2\times10^{8}$ |
| $L_\mathrm{[OIII]}/L_\mathrm{[CII]}$ | $3.4\pm0.6$ | $8.9\pm1.7$ | $6.0\pm1.7$ |
| $L_\mathrm{[OIII]}/L_\mathrm{[NII]}$ | $>5.8$ | $>3.2$ | $>13.8$ |
| $S_{\nu,160}$ \[$\mu$Jy\] | $220\pm51\ (4.3\sigma)$ | $<101\ (3\sigma)$ | $239\pm79\ (3.0\sigma)$ |
| $S_{\nu,120}$ \[$\mu$Jy\] | $382\pm72\ (5.3\sigma)$ | $<162\ (3\sigma)$ | $310\pm43\ (7.1\sigma)$ |
| $S_{\nu,90}$ \[$\mu$Jy\] | $<826\ (3\sigma)$ | $<394\ (3\sigma)$ | $<606\ (3\sigma)$ |
| $L_\mathrm{IR}$ \[$L_\odot$\] | $3.2^{+18.7}_{-1.7}\times10^{11}$ | $<2.5\times10^{11}\ (3\sigma)$ | $1.4^{+2.5}_{-0.3}\times10^{11}$ |
| $T_\mathrm{dust}$ \[K\] | $38^{+34}_{-12}$ | $\dots$ | $25^{+19}_{-5}$ |
| $M_\mathrm{dust}$ \[$M_\odot$\] | $3.0^{+10.5}_{-2.3}\times10^{7}$ | $<6.9\times10^{6}\ (3\sigma)$ | $1.9^{+73.5}_{-1.6}\times10^{8}$ |
| $SFR_\mathrm{tot}$ \[$M_\odot\ \mathrm{yr^{-1}}$\] | $86$ | $54$ | $96$ |
| $SFR_\mathrm{UV}$ \[$M_\odot\ \mathrm{yr^{-1}}$\] | $51$ | $54$ | $80$ |
| $SFR_\mathrm{IR}$ \[$M_\odot\ \mathrm{yr^{-1}}$\] | $34$ | $<27$ | $16$ |

: Summary of Observational Results of Our Targets

This paper is organized as follows. In Section [2](#ss_target), we describe our targets and optical spectroscopy already conducted. Our ALMA observations are presented in Section [3](#ss_alma). We present our results for the FIR emission lines and dust continuum emission in Sections [4](#ss_line) and [5](#ss_dust), respectively. In Section [6](#ss_dis), we discuss our results based on model calculations by Cloudy. Section [7](#ss_summary) summarizes our findings. Throughout this paper we use the recent Planck cosmological parameter sets constrained with the temperature power spectrum, temperature-polarization cross spectrum, polarization power spectrum, low-$l$ polarization, CMB lensing, and external data (cite: 2016A&A...594A..13P): $\Omega_\mathrm{m}=0.3089$, $\Omega_\Lambda=0.6911$, $\Omega_\mathrm{b}=0.049$, and $h=0.6774$. We assume a (cite: 2003PASP..115..763C) initial mass function (IMF) with lower and upper mass cutoffs of $0.1\mathrm{M_\odot}$ and $100\mathrm{M_\odot}$, respectively. All magnitudes are in the AB system (cite: 1983ApJ...266..713O), and are corrected for Galactic extinction (cite: 1998ApJ...500..525S).

# Target Selection

We select targets for our ALMA observations from the Subaru/Hyper Suprime-Cam Subaru strategic program (HSC-SSP) survey datasets (cite: 2018PASJ...70S...4A). The Subaru/HSC survey is a photometric survey with optical broad band filters $grizy$ and several narrow-band filters. The HSC survey has three layers, UltraDeep, Deep, and Wide, with different combinations of area and depth (see (cite: 2018PASJ...70S...4A) for details). LBGs at $z\sim4-7$ are selected from the HSC datasets with the dropout selection technique (cite: 2016ApJ...828...26M; 2018PASJ...70S..35M; 2018ApJS..237....5M; 2019arXiv190807910M; 2018PASJ...70S..10O; 2018PASJ...70S..11H; 2018PASJ...70S..12T), and some of the LBGs are spectroscopically confirmed (cite: 2016ApJ...828...26M; 2018PASJ...70S..35M; 2018ApJS..237....5M; 2019arXiv190807910M; 2018PASJ...70S..10O).

As the first step to understand ISM properties of high redshift galaxies, we select three luminous LBGs, J1211-0118, J0235-0532, and J0217-0208 as targets for ALMA observations (Table [\[tab_prop\]](#tab_prop)). All targets are spectroscopically confirmed with Ly$\alpha$ in the SHELLQs project (cite: 2018PASJ...70S..35M), and their redshifts, $6.0<z_\mathrm{Ly\alpha}<6.3$, are suitable for ALMA Band 6, 7, and 8 observations targeting 158$\mu$m, 122$\mu$m, and 88$\mu$m, respectively. J1211-0118 shows a weak Ly$\alpha$ emission line with a rest-frame Ly$\alpha$ equivalent width (EW) of $EW^0_\mathrm{Ly\alpha}=6.9\pm0.8\ \mathrm{\AA}$. J0235-0532 and J0217-0208 show strong Ly$\alpha$ emission lines with $EW^0_\mathrm{Ly\alpha}=41\pm2$, and $15\pm1\ \mathrm{\AA}$, respectively. The broad dynamical range of the Ly$\alpha$ EW makes our targets representative in terms of Ly$\alpha$ emission. The spectroscopic data also indicate that the targets do not have broad Ly$\alpha$ ($>400\ \mathrm{km\ s^{-1}}$) nor Nv emission lines. J0235-0532 and J0217-0208 exhibit large Ly$\alpha$ luminosities of $L_\mathrm{Ly\alpha}>10^{43}\ \mathrm{erg\ s^{-1}}$, powerful enough to be associated with AGNs as suggested by (cite: 2016ApJ...823...20K) at $z\sim2$, while a spectroscopic study by (cite: 2018PASJ...70S..15S) do not find signatures of AGN activitity (e.g., Civ emission) in such luminous LAEs at $z\sim6-7$. NIR spectroscopy is important for understanding possible AGN activities in J0235-0532 and J0217-0208.

![](fig_snapshot_aplpy_lines_nat.pdf)

# ALMA Observations and Data Reduction

The three LBGs at $z\sim6$ were observed during ALMA cycle 5 (ID: #2017.1.00508.S, PI: Y. Harikane) at Bands 6, 7, and 8 for \[Cii\]158$\mu$m, \[Nii\]122$\mu$m, and \[Oiii\]88$\mu$m, between 2018 April 3rd and 2018 June 22nd. The antenna configurations were C43-1, C43-2, and C43-3, achieving the beam sizes of $\sim0.$$''$$6-1.$$''$$1$ and the maximum recoverable scales of $6-7\ensuremath{''}$. We used four spectral windows (SPWs) with 1.875 GHz bandwidths in the Frequency Division Mode and the total band width of 7.5 GHz. The velocity resolution was set to $\sim3-5\ \mathrm{km\ s^{-1}}$. One of the SPWs was centered on the \[Cii\], \[Nii\], or \[Oiii\] line frequency expected from the redshift of the Ly$\alpha$ emission.

The data were reduced and calibrated using the Common Astronomy Software (cite: 2007ASPC..376..127M) pipeline version 5.1.1 in the general manner with scripts provided by the ALMA observatory. Using the task `CLEAN`, we produced images and cubes with the natural weighting without taper to maximize point-source sensitivities. To generate a pure dust continuum image, we collapsed all SPWs except for one SPW where the \[Cii\], \[Nii\], or \[Oiii\] line is located, i.e., the continuum is taken at $\gtrsim600\ \mathrm{km\ s^{-1}}$ from the line center. To create a pure line image, we subtracted continuum using the off-line channels in the line cube with the CASA task `uvcontsub`.

![](fig_snapshot_aplpy_overplot_line_nat.pdf)

![](fig_spectra_CII_OIII_NII.pdf)

# FIR Emission Lines

## Line Detections and Upper limits

Figure [1](#fig_snap_line) displays the \[Oiii\]88$\mu$m, 158$\mu$m, and 122$\mu$m emission lines of our three targets. These moment 0 maps were made with the CASA task `immoments`, integrating over $600\ \mathrm{km\ s^{-1}}$ covering most of the velocity range of the line emission ($>1.5\times \mathrm{FWHM}$) This wavelength range is comparable to previous studies for luminous galaxies (cite: 2016Sci...352.1559I; 2017ApJ...851..145M; 2019PASJ...71...71H). We calculate the signal-to-noise ratios (SNRs) of the emission lines using $0.$$''$$7$-diameter circular aperture, by randomly placing apertures on the image and adopting the rms as the noise level. The and emission lines are clearly detected in all of our targets at the $4.3-11.8\sigma$ significance levels. In addition, the emission in J1211-0118 and J0217-0208 are spatially well resolved. The emission are not detected in our three targets. For all three emission lines for the three targets, total fluxes are measured on the $600\ \mathrm{km\ s^{-1}}$-integrated maps in $2\ensuremath{''}$-radius circular apertures, which can cover the area where spatially extended emission may exist like the 158$\mu$m halos around $z\sim6$ galaxies reported by (cite: 2019arXiv190206760F). Note that the maximum recoverable scales of our data, $6-7\ensuremath{''}$, are larger than the typical size of the halo, $\sim2\ensuremath{''}$.

In Figure [2](#fig_offset_line), we compare spatial distributions of the and with the rest-UV emission including Ly$\alpha$. We plot the peak pixel positions of the and emission with uncertainties with crosses in Figure [2](#fig_offset_line). We estimate the uncertainties of the peak positions using Monte Carlo simulations. In each dataset of the target and the emission line, we add artificial sky noises to pixels following a Gaussian random distribution with a standard deviation equal to the $1\sigma$ noise of the data, and re-measure the peak positions. We make a series of 1000 simulations for each dataset, and estimate the uncertainties of the peak positions. We find that the peak positions of and agree within $2\sigma$ uncertainties in all of our galaxies.

![](fig_OIII_SFR.pdf)

![](fig_CII_SFR.pdf)

Figure [3](#fig_spec) shows spectra around the frequencies of the \[Oiii\]88$\mu$m, 158$\mu$m, and 122$\mu$m lines. We simply fit each spectrum with a single Gaussian profile and the rest-frame \[Oiii\]88$\mu$m, \[Cii\]158$\mu$m, or \[Nii\]122$\mu$m frequency (1900.5369, 3393.0062, or 2459.3801 GHz, respectively[^1]), which delivers the redshift and full width at half maximum (FWHM). The obtained redshifts and FWHMs are summarized in Table [\[tab_prop\]](#tab_prop). We find that the redshifts based on the \[Oiii\] and lines are consistent within $1\sigma$ uncertainties. The FWHMs are $170-390\ \mathrm{km\ s^{-1}}$. The FWHMs of the \[Oiii\] lines seem to be larger than those of the lines, but they are comparable within $1\sigma$ uncertainties (cite: 2019MNRAS.487.1689P). We adopt SNR-weighted means of the \[Oiii\] and redshifts as the systemic redshifts of our targets. The systemic redshifts of J1211-0118, J0235-0532, and J0217-0208 are $z_\mathrm{sys}=6.0293$, $6.0901$, and $6.2037$, respectively. The Ly$\alpha$ redshifts measured from the optical spectroscopy are slightly redshifted from the systemic redshifts, because of the resonant scattering of Ly$\alpha$. The Ly$\alpha$ velocity offsets are $40-200\ \mathrm{km\ s^{-1}}$, comparable to previous results (cite: 2013ApJ...765...70H; 2014ApJ...788...74S; 2014ApJ...795...33E; 2019PASJ...71...71H).

Based on the total fluxes and the systemic redshifts, we calculate luminosities of the emission lines. Table [\[tab_prop\]](#tab_prop) summarized the calculated and luminosities of and upper limits for . Our targets have some of the highest and luminosities seen in $z>6$ LBGs and LAEs.

## $L_\mathrm{[OIII]}$-SFR and $L_\mathrm{[CII]}$-SFR Relations

![](fig_OIIICII_SFR.pdf)

![](fig_OIIICII_Lbol.pdf)

![](fig_snapshot_aplpy_lines_velocitymap_CII158_nat.pdf)

We compare \[Oiii\]88$\mu$m and \[Cii\]158$\mu$m luminosities of our targets with previous studies for LBGs and LAEs given SFRs. We usually plot the (and ) luminosity as a function of SFR, because C$^+$ (O$^{2+}$) ionizing photons are made by massive stars recently formed. The left panel of Figure [4](#fig_L_SFR) shows the \[Oiii\] luminosities as a function of SFR. For our three targets, these SFRs are total SFRs from UV and IR luminosities that are estimated in Section [5.2](#ss_LIR_Td). We also plot relations for $z\sim0$ local starburst galaxies (local SBs) and low-metallicity dwarf galaxies (low-$Z$ dwarfs) from (cite: 2014A&A...568A..62D), and results of $z=6-9$ galaxies in the literature (cite: 2016Sci...352.1559I; 2017ApJ...837L..21L; 2017A&A...605A..42C; 2018Natur.557..392H; 2019ApJ...874...27T; 2019PASJ...71...71H), summarized in Table [\[tab_lite\]](#tab_lite). The luminosities of our targets are comparable to or higher than the relation for the low-metallicity dwarf galaxies of (cite: 2014A&A...568A..62D). Other $z=6-9$ galaxies are comparable to either of the local relations. The $z=6-9$ galaxies do not show any deficit relative to the local $L_\mathrm{[OIII]}$-SFR relations unlike the case. In the left panel of Figure [4](#fig_L_SFR), we plot the following fitting function for the results of $z=6-9$ galaxies as the red dashed line: $$\begin{equation}
\mathrm{log}(L_\mathrm{[OIII]}/[L_\odot])=0.97\times\mathrm{log}(SFR/[M_\odot\ \mathrm{yr^{-1}}])+7.4 .
\end{equation}$$

The right panel of Figure [4](#fig_L_SFR) displays the luminosities as a function of the SFR. We also plot relations for $z\sim0$ galaxies and results for $z=5-9$ galaxies in the literature summarized in Table [\[tab_lite\]](#tab_lite). In contrast to the luminosities, all of our targets are located below the $L_\mathrm{[CII]}$-SFR relation of $z\sim0$ low-metallicity dwarf galaxies. We find that J1211-0118 and J0217-0208 follow the relation for $z\sim0$ starburst galaxies, and the luminosity of J0235-0532 is 0.3 dex lower than that relation. The relatively low luminosity of J0235-0532 with the strong Ly$\alpha$ emission ($EW_{Ly\alpha}^0=41\ \mathrm{\AA}$) is consistent with the anti-correlation between $L_\mathrm{[CII]}/SFR$ and $\mathrm{EW^0_{Ly\alpha}}$ reported in (cite: 2018ApJ...859...84H). The red dashed line in the right panel of Figure [4](#fig_L_SFR) is the fitting function for the results of $z=6-9$ galaxies: $$\begin{equation}
\mathrm{log}(L_\mathrm{[CII]}/[L_\odot])=1.6\times\mathrm{log}(SFR/[M_\odot\ \mathrm{yr^{-1}}])+6.0 ,
\end{equation}$$ which is comparable to a fitting function for a combination of the ALMA Large Program to INvestigate C$^+$ at Early Times (ALPINE) data at $z=4-6$ and $z\sim6-9$ galaxies in (cite: 2020arXiv200200979S).

## $L_\mathrm{[OIII]}/L_\mathrm{[CII]}$ Ratios

We plot the / luminosity ratio as a function of the SFR and the bolometric luminosities in Figure [5](#fig_OIIICII), following previous studies (cite: 2019MNRAS.487L..81L; 2019PASJ...71...71H; 2019PASJ...71..109H; 2020MNRAS.493.4294B). We also plot results of $z=6-9$ galaxies in the literature and local galaxies studied in the Dwarf Galaxy Survey (cite: 2013PASP..125..600M; 2014A&A...568A..62D; 2015A&A...578A..53C) and the Great Observatories All-sky LIRG Survey (cite: 2010ApJ...715..572H; 2017ApJ...846...32D). We find that our targets and other $z=6-9$ galaxies show systematically higher / ratios compared to local galaxies, which is consistent with previous results (cite: 2016Sci...352.1559I; 2019MNRAS.487L..81L). In Figure [5](#fig_OIIICII), we plot the following fitting functions for the results of $z=6-9$ galaxies as the red dashed lines: $$\begin{eqnarray}
\mathrm{log}(L_\mathrm{[OIII]}/L_\mathrm{[CII]})&=&-0.20\times\mathrm{log}(SFR/[M_\odot\ \mathrm{yr^{-1}}])+1.3,\nonumber\\ \\
\mathrm{log}(L_\mathrm{[OIII]}/L_\mathrm{[CII]})&=&-0.59\times\mathrm{log}(L_\mathrm{bol}/[L_\odot])+7.7.
\end{eqnarray}$$ We will discuss the origin of the high / ratios in Section [6.1](#ss_dis_OIIICII).

## Velocity Fields

We investigate kinematic properties of our targets using emission, which are detected with high signal to noise ratios and are spatially well resolved in J1211-0118 and J0217-0208. With the CASA task `immoments`, we create flux-weighted velocity (i.e., moment 1) maps and velocity dispersion (i.e., moment 2) maps of emission of our targets. We only use pixels with $>2\sigma$ detections. Figure [6](#fig_vmap) shows the velocity and dispersion maps. The velocity maps of J1211-0118 clearly shows a $\sim220$ km s$^{-1}$ velocity gradient. We also identify a gradient of $\sim250$ km s$^{-1}$ in J0217-0208. The velocity dispersions ($\sigma_\mathrm{tot}\simeq \mathrm{FWHM}/2.35$) are $\sim70$, $\sim110$, and $\sim130$ km s$^{-1}$ for J1211-0118, J0235-0532, and J0217-0208, respectively. Given the low angular resolution of the observations, there are various interpretations of the velocity gradients. A rotating galaxy disk would be one interpretation.

![](fig_snapshot_aplpy_dust_nat.pdf)

We apply an observational criterion for the classification of rotation- and dispersion-dominated systems, $\Delta v_\mathrm{obs}/2\sigma_\mathrm{tot}=0.4$, where $\Delta v_\mathrm{obs}$ and $\sigma_\mathrm{tot}$ are the full observed velocity gradient and the velocity dispersions (cite: 2009ApJ...706.1364F). We find that $\Delta v_\mathrm{obs}/2\sigma_\mathrm{tot}=1.6$ and $0.96$ for J1211-0118 and J0217-0208, respectively, indicating that these two galaxies are consistent with rotation dominated systems. These values ($\Delta v_\mathrm{obs}/2\sigma_\mathrm{tot}>0.4$) are contrast to those of other systems that are interpreted as galaxy mergers (cite: 2019ApJ...881L..23B).

# Dust Continua

## Detections and Upper limits

Figure [7](#fig_snap_dust) shows the continuum emission maps of our targets. We calculate the SNRs of the dust continuum using $0.$$''$$7$-diameter circular aperture, by randomly placing apertures on the image and adopting the rms as the noise level. We detect dust continuum emission at $\sim120\ \mu\mathrm{m}$ from J1211-0118 and J0217-0208 at $5.3\sigma$ and $7.1\sigma$ significance levels, respectively. We also identify dust continua of J1211-0118 and J0217-0208 at $\sim160\ \mu\mathrm{m}$, which are useful to constrain dust temperatures of these galaxies (see Section [5.2](#ss_LIR_Td)). We do not detect dust continuum emission from J0235-0532. We compare spatial positions and morphologies of these dust continuum emission with the rest-UV emission in Figure [8](#fig_offset_dust). In J1211-0118 and J0217-0208, the peak positions of the dust emission overlap with the rest-UV counterparts, given the uncertainties of the peak determination.

![](fig_snapshot_aplpy_overplot_dust_nat.pdf)

![](fig_fit_dustcont_wl_panel.pdf)

## $L_\mathrm{IR}$ and $T_\mathrm{dust}$ Estimates

We estimate IR luminosities, $L_\mathrm{IR}$, by integrating the modified black body radiation over $8-1000\ \mu$m. We fit the observed fluxes with the modified black body by varying the IR luminosity and dust temperatures, $T_\mathrm{dust}$. We fix the dust emissivity to $\beta_\mathrm{d}=1.5$, but the effect of this assumption is not significant for our conclusions. For example, if we change the dust emissivity in $1<\beta_\mathrm{d}<3$, the IR luminosity varies only $<0.1$ dex. The CMB heating and attenuation effects are included following formulae by (cite: 2013ApJ...766...13D). In the fitting, we require that the dust temperature must be higher than the CMB temperature at the redshift of the galaxy ($\sim 20\ \mathrm{K}$ at $z\sim 6$).

Figure [9](#fig_fit_mbb) shows the dust spectral energy distributions (SEDs) and the best-fit models for our targets. We obtain IR luminosities and dust temperatures of $(L_\mathrm{IR}, T_\mathrm{dust})=(3.2^{+18.7}_{-1.7}\times10^{11}\ L_\odot, 38^{+34}_{-12}\ \mathrm{K})$ and ($1.4^{+2.5}_{-0.3}\times10^{11}\ L_\odot, 25^{+19}_{-5}\ \mathrm{K})$, for J1211-0118 and J0217-0208, respectively. These IR luminosities ($L_\mathrm{IR}>10^{11}\ L_\odot$) correspond to luminous infrared galaxies (LIRGs) in local universe. These dust temperatures are comparable to other $z>6$ galaxies (cite: 2017MNRAS.466..138K; 2019PASJ...71...71H) and theoretical simulations (cite: 2018MNRAS.477..552B). Although the IR luminosity is degenerate with the dust temperature, shown in the error contours in Figure [9](#fig_fit_mbb), the IR luminosities range in $1.1\times10^{11}<L_\mathrm{IR}/L_\odot<7.9\times10^{12}$ and $1.0\times10^{11}<L_\mathrm{IR}/L_\odot<2.2\times10^{12}$ for J1211-0118 and J0217-0208, respectively, within the $1\sigma$ confidence regions in the error contours. For J0235-0532, we obtain the $3\sigma$ upper limit of $L_\mathrm{IR}\times T_\mathrm{dust}<1.3\times10^{13}\ L_\odot\mathrm{K}$. Since we want to compare our observations with previous studies including (cite: 2019PASJ...71...71H), who assume $T_\mathrm{dust}=50\ \mathrm{K}$ for galaxies without continuum detections, we adopt $L_\mathrm{IR}<2.5\times10^{11}\ L_\odot$ assuming $T_\mathrm{dust}=50\ \mathrm{K}$ as the fiducial value for J0235-0532.

## IRX-$\beta_\mathrm{UV}$ Relation

We investigate whether our targets follow the known IRX-$\beta$ relations, or show IRX values below the relations. We estimate the UV slope $\beta$ using the Subaru/HSC photometry and spectroscopic properties of the Ly$\alpha$ emission lines. Based on the HSC $z$ and $y$ band magnitudes, redshifts, and Ly$\alpha$ EWs, we estimate the UV spectral slope to be $\beta_\mathrm{UV}=-2.0\pm0.5$, $-2.6\pm0.6$, and $-0.1\pm0.5$ for J1211-0118, J0235-0532, and J0217-0208, respectively. Note that the HSC $z$ and $y$ bands correspond to the rest-frame wavelength of $1300-1500\ \mathrm{\AA}$.

![](fig_IRX_beta.pdf)

![](fig_OIIISFR_qion_cloudy.pdf)

![](fig_CIISFR_qion_cloudy.pdf)

![](fig_OIIICII_qion_cloudy.pdf)

Figure [10](#fig_IRX) shows the IRX values of our targets as a function of the UV slope $\beta_\mathrm{UV}$. We find that J1211-0118 follows the Calzetti IRX-$\beta_\mathrm{UV}$ relation, similar to A1689-zD1 (cite: 2015Natur.519..327W), A2744-YD4 (cite: 2017ApJ...837L..21L; 2019MNRAS.487L..81L), and B14-65666 (cite: 2019PASJ...71...71H). The upper limit of J0235-0532 is consistent with both the Calzetti, Takeuchi, and SMC relations. The IRX value of J0217-0208 is lower than the SMC relation, even if the IR luminosity is $L_\mathrm{IR}=2.2\times10^{12}\ L_\odot$ (the dashed error bar). Note that the wavelength ranges used to derive $\beta_\mathrm{UV}$ differ from our sample and the others compared here (see also (cite: 2019PASJ...71...71H)); NIR imaging data are necessary to estimate $\beta_\mathrm{UV}$ in the same wavelength ranges as the other studies.

There are several possibilities for the physical origins of the low IRX value of J0217-0208. One is the geometry effect (cite: 2017ApJ...847...21F). Depending on the geometry and the viewing angle of the observer, the dust clouds might be spatially offset from the line-of-sight and the UV light can escape from the galaxy without being attenuated, which would cause the low IRX value. AGN activity also can explain the offset in the IRX-$\beta_\mathrm{UV}$ plot. (cite: 2018A&A...617A.131S) show that quasars have lower IRX values given the UV slope, similar to $z\sim5-6$ galaxies in (cite: 2015Natur.522..455C), because UV slopes of AGNs are redder than those of galaxies in $M_\mathrm{UV}\gtrsim-24\ \mathrm{mag}$. (cite: 2017MNRAS.471.5018F) suggest that the high fraction of dust locked inside the molecular gas without internal illumination can explain the low IRX value.

## Dust Mass

Based on the observed fluxes at $\sim160\ \mu\mathrm{m}$ and the estimated temperatures, we estimate the dust masses in our targets. Assuming a dust mass absorption coefficient $\kappa=\kappa_0(\nu/\nu_0)^{\beta_\mathrm{d}}$, where $\kappa_0=10\ \mathrm{cm^2\ g^{-1}}$ at 250 $\mu$m (cite: 1983QJRAS..24..267H), we estimate the dust masses to be $M_\mathrm{dust}=3.0^{+10.5}_{-2.3}\times10^{7}\ M_\odot$, $<6.9\times10^{6}\ M_\odot\ (3\sigma)$, and $1.9^{+73.5}_{-1.6}\times10^{8}\ M_\odot$ for J1211-0118, J0235-0532, and J0217-0208, respectively. Using an empirical relation between the UV magnitude and stellar mass for $z\sim6$ LBGs (cite: 2016ApJ...825....5S), the stellar masses of our targets are estimated to be $\sim3\times10^{10}\ M_\odot$. The inferred dust-to-stellar mass ratios are $\mathrm{log}(M_\mathrm{dust}/M_*)\sim-3.0$, $<-3.6$, and $-2.2$ for J1211-0118, J0235-0532, and J0217-0208, respectively. These dust-to-stellar mass ratios are relatively lower than the value for B14-65666 at $z=7$ (cite: 2019PASJ...71...71H), but within the range observed in $z\sim0$ galaxies (cite: 2015A&A...582A.121R). These ratios can be reproduced by the supernova and AGB star model with grain growth in (cite: 2015MNRAS.451L..70M). Note that our ALMA data probes 90, 120, and 160 $\mu$m in the rest-frame. Since the longest wavelength corresponds to $\sim$20 K in the Wien law, comparable to the CMB temperature, no more cooler dust exists unless the CMB radiation was shielded. On the other hand, dust emission with the CMB temperature ($\sim 20\ \mathrm{K}$ at $z\sim 6$) cannot be detected with interferometers like ALMA (cite: 2013ApJ...766...13D). In the case that there is dust whose temperature is $\sim 20\ \mathrm{K}$ in the targeted galaxies, such dust would be missed in observations presented here, causing a large uncertainty in dust mass estimates.

# Discussion

## Origin of High $L_\mathrm{[OIII]}/L_\mathrm{[CII]}$ Ratios at $z=6-9$

In Section [4.3](#ss_OIIICII), we find that the /\[Cii\] ratios of the $z=6-9$ galaxies are systematically higher than those of $z\sim0$ galaxies. In order to discuss the origin of the high /\[Cii\] ratios of the $z=6-9$ galaxies, we conduct model calculations including both Hii regions and photodissociation regions (PDRs) using Cloudy (cite: 1998PASP..110..761F; 2017RMxAA..53..385F) version 17.01, following (cite: 2011A&A...526A.149N; 2012A&A...542L..34N). We include PDRs because \[Cii\] emission mainly comes from PDRs (cite: 2019A&A...626A..23C). We assume a pressure-equilibrium gas cloud with a plain-parallel geometry that is characterized by certain hydrogen gas densities at the ionization front ($n_\mathrm{H}$), metallicity ($Z$), and ionization parameters $U_\mathrm{ion}$. Here we examine gas clouds with $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=0.5$, $2.0$, and $3.0$, and $Z=0.05$, $0.2$, and $1.0\ Z_\odot$ for $-4.0\leq\mathrm{log}U_\mathrm{ion}\leq-0.5$ with a step of 0.5. Note that with the very high $U_\mathrm{ion}$ value such as $\mathrm{log}U_\mathrm{ion}=-0.5$, the high pressure would squash the ionized gas (cite: 2012ApJ...757..108Y). The input continuum is a spectrum of a burst star formation model with an age of 1 Myr and (cite: 1955ApJ...121..161S) IMF with lower and upper mass cutoffs of $1\ M_\odot$ and $100\ M_\odot$ for binary populations, calculated with the BPASS v2.1 model (cite: 2017PASA...34...58E). The stellar metallicity is equal to the gas metallicity. The relative chemical composition of the gas cloud is scaled to the solar elemental abundance ratios except for helium, which follows an equation in (cite: 2004ApJS..153...75G). The nitrogen abundance is also scaled to the solar abundance, although it is possible that the nitrogen abundance ratio changes due to its secondary element nature. Orion-type graphite and silicate grains are included. Calculations are stopped at the depth of $A_\mathrm{V}=100\ \mathrm{mag}$ to cover the whole emitting regions, following (cite: 2005ApJS..161...65A).

In the left panel of Figure [11](#fig_cl_OIII_CII_qion), we plot $L_\mathrm{[OIII]}/SFR$ ratios as a function of the ionization parameter. The SFRs of the models are derived from H$\alpha$ luminosities using Equation (2) of (cite: 1998ARA&A..36..189K), and are converted to values in the (cite: 2003PASP..115..763C) IMF by multiplying by $0.63$. The uncertainty of the conversion in (cite: 1998ARA&A..36..189K) is roughly $\sim30\%$ ($0.1\ \mathrm{dex}$), which does not affect our conclusions. The $L_\mathrm{[OIII]}/SFR$ ratio increases with increasing ionization parameter, because more ionizing photons are used to produce $\mathrm{O^{2+}}$. Since the critical density of the \[Oiii\]88$\mu$m is 510 cm$^{-3}$ for collision with electrons, the ratio decreases with increasing the density from $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=2.0$ to $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=3.0$. Also, the ratio decreases with decreasing metallicity at $0.05<Z/Z_\odot<1.0$, because the lower abundance of the oxygen in the Hii regions.

The middle panel of Figure [11](#fig_cl_OIII_CII_qion) shows $L_\mathrm{[CII]}/SFR$ ratios as a function of the ionization parameter. The $L_\mathrm{[CII]}/SFR$ ratio decreases with increasing ionization parameter, because the volume of PDRs decreases due to the larger Hii regions with more ionizing photons, and more $\mathrm{C}^{+}$ are ionized to $\mathrm{C}^{2+}$ (cite: 2019MNRAS.489....1F). We find that higher hydrogen densities also make lower $L_\mathrm{[CII]}/SFR$ ratios, because the density in PDRs is higher than that in Hii regions in the constant pressure assumption, and it exceeds the critical density of \[Cii\]158$\mu$m for hydrogen, 2800 cm$^{-3}$. The ratio does not strongly change with metallicity. As discussed in (cite: 2006ApJ...644..283K), the carbon abundance is proportional to the metallicity, $Z$, while the PDR column density is proportional to $1/Z$, as long as shielding of FUV photons is dominated by dust (assuming a constant dust-to-metal ratio) and the gas column density is large enough. Since the emission mainly comes from PDRs, the luminosity does not strongly depend on the metallicity ($L_\mathrm{[CII]}\propto Z\times1/Z=\mathrm{constant}$, see also (cite: 2019MNRAS.487.1689P; 2019MNRAS.489....1F)).

We also show calculated /\[Cii\] ratios as a function of the ionization parameter in the right panel of Figure [11](#fig_cl_OIII_CII_qion). The ratio increases with increasing ionization parameter or metallicity. The ratio also increases with increasing the density from $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=0.5$ to $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=2.0$.

![](fig_OIIISFR_CIISFR_cloudy_panels.pdf)

Since the SFR is an important parameter describing the amount of ionizing photons, we need to compare both the line luminosities and SFRs of the observations with the models. Thus we compare $L_\mathrm{[OIII]}/SFR$ and $L_\mathrm{[CII]}/SFR$ ratios of the $z=6-9$ galaxies with $z\sim0$ galaxies in the left panel of Figure [12](#fig_cl_OIIISFR_CIISFR). Our targets (J1211-0118, J0235-0532, and J0217-0208), MACS0416-Y1, B14-65666, and BDF-3299 are located in a region of $6.3<\mathrm{log}(L_\mathrm{[CII]}/SFR)<7.3$ and $7.2<\mathrm{log}(L_\mathrm{[OIII]}/SFR)<8.0$. These galaxies (“ detected galaxies”) have $\sim0.3-1\ \mathrm{dex}$ lower $L_\mathrm{[CII]}/SFR$ ratios than $z\sim0$ galaxies with similar $L_\mathrm{[OIII]}/SFR$ ratios. On the other hand, MACS1149-JD1, A2744-YD4, and SXDF-NB1006-2 are in $\mathrm{log}(L_\mathrm{[CII]}/SFR)<6.3$ and $6.6<\mathrm{log}(L_\mathrm{[OIII]}/SFR)<7.4$. The $L_\mathrm{[CII]}/SFR$ ratios of these galaxies (“ undetected galaxies”) are $>1\ \mathrm{dex}$ lower than $z\sim0$ galaxies with similar $L_\mathrm{[OIII]}/SFR$ ratios.

![](fig_OIIISFR_CIISFR_cloudy_panels_shift_UionCpdr.pdf)

![](fig_OIIISFR_CIISFR_cloudy_panels_shift_onlyNh.pdf)

We plot results of the model calculations for $L_\mathrm{[OIII]}/SFR$ and $L_\mathrm{[CII]}/SFR$ ratios in the right panel of Figure [12](#fig_cl_OIIISFR_CIISFR). Based on these calculations, we discuss the following eight possibilities explaining the observational properties (i.e., $L_\mathrm{[OIII]}/SFR$, $L_\mathrm{[CII]}/SFR$, and high /\[Cii\]) of the $z=6-9$ galaxies compared to the $z\sim0$ galaxies:

- Higher ionization parameter ($U_\mathrm{ion}$)\
  Several studies suggest higher ionization parameters in higher redshift galaxies, compared to $z\sim0$ galaxies ($\mathrm{log}U_\mathrm{ion}\simeq-3.1$, e.g., (cite: 2014MNRAS.442..900N)). As shown in Figures [11](#fig_cl_OIII_CII_qion) and [12](#fig_cl_OIIISFR_CIISFR), with increasing $U_\mathrm{ion}$, $L_\mathrm{[OIII]}/SFR$ increases while $L_\mathrm{[CII]}/SFR$ decreases. Thus high ionization parameters can explain the $L_\mathrm{[OIII]}/SFR$ and $L_\mathrm{[CII]}/SFR$ ratios of both detected and undetected galaxies at $z=6-9$. For example, as shown in the left panel of Figure [13](#fig_cl_Uion_Cpdr), $2.0\ \mathrm{dex}$ ($1.0\ \mathrm{dex}$) higher ionization parameter can reproduce the $>1\ \mathrm{dex}$ ($0.3-1\ \mathrm{dex}$) systematic offsets of $L_\mathrm{[CII]}/SFR$ seen in the undetected (detected) galaxies at $z=6-9$, compared to the $z\sim0$ galaxies, if we fix the metallicity and density. Thus high ionization parameters would be an origin of the high /\[Cii\] ratios of the $z=6-9$ galaxies. The high ionization parameters in $z=6-9$ galaxies are possibly made by young (bursty) or low-metallicity stellar populations with more ionizing photons, or compact sizes of galaxies with high SFR surface densities (cite: 2015ApJS..219...15S), as predicted by theoretical simulations (cite: 2017MNRAS.467.1300V; 2018MNRAS.481L..84M). The high SFR surface density could ionize C$^+$ to C$^2+$ and make the Hii regions overlapping each other like Figure [15](#fig_punch)b, increasing (decreasing) the volume of the Hii regions (PDRs). Observations for local starburst galaxies also report a positive correlation between the /\[Cii\] ratio and the dust temperature (cite: 2017ApJ...846...32D; 2018ApJ...869L..22W), possibly due to high ionization parameters in high /\[Cii\] galaxies. Theoretical simulations of (cite: 2019MNRAS.487.1689P) and (cite: 2019MNRAS.489....1F) suggest that the burst of star formation enhance the ionization parameter and make the deficit, although it is not known whether the simulations also quantitatively reproduce the observed high /\[Cii\] ratios.

- Lower gas metallicity ($Z$)\
  Evolution of the mass-metallicity relation suggests lower metallicities in higher redshift galaxies (cite: 2008A&A...488..463M). Figures [11](#fig_cl_OIII_CII_qion) and [12](#fig_cl_OIIISFR_CIISFR) indicate that with decreasing metallicity, only the $L_\mathrm{[OIII]}/SFR$ ratio decreases, while the $L_\mathrm{[CII]}/SFR$ ratio does not significantly change. As discussed in the previous paragraph, the luminosity from the PDR does not strongly depend on the metallicity, as long as shielding of FUV photons is dominated by dust and the gas column density is large enough. Thus changing the metallicity cannot reproduce the systematic offsets seen in $L_\mathrm{[CII]}/SFR$ of the $z=6-9$ galaxies.

- Higher density ($n_\mathrm{H}$)\
  Several spectroscopic studies report high electron densities in high redshift galaxies (cite: 2015MNRAS.451.1284S; 2016ApJ...816...23S; 2017ApJ...835...88K). As shown in Figures [11](#fig_cl_OIII_CII_qion) and [12](#fig_cl_OIIISFR_CIISFR), both $L_\mathrm{[OIII]}/SFR$ and $L_\mathrm{[CII]}/SFR$ ratios decrease with increasing the hydrogen density due to the collisional de-excitation. Since the $L_\mathrm{[OIII]}/SFR$ ratios of the $z=6-9$ galaxies are comparable to $z\sim0$, higher densities cannot reproduce both $L_\mathrm{[OIII]}/SFR$ and $L_\mathrm{[CII]}/SFR$ of the $z=6-9$ galaxies simultaneously (Figure [14](#fig_cl_onlynH)). More precisely, if we increase the density from $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=0.5$ to $2.0$, $L_\mathrm{[OIII]}/SFR$ does not significantly change, while the $L_\mathrm{[CII]}/SFR$ ratio decreases by $\sim1\ \mathrm{dex}$, because the density in PDRs reaches the critical density of . Thus as shown in Figure [14](#fig_cl_onlynH), the increase of the density from $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=0.5$ to $2.0$ can reproduce a part of the $z=6-9$ galaxies, but cannot reproduce the $<1\ \mathrm{dex}$ lower $L_\mathrm{[CII]}/SFR$ ratios of some of the $z=6-9$ galaxies. If we increase the density from $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=2.0$ to $3.0$, both the $L_\mathrm{[CII]}/SFR$ and $L_\mathrm{[OIII]}/SFR$ ratios decreases by $\sim1\ \mathrm{dex}$. As shown in Figure [14](#fig_cl_onlynH), the increase of the density to $\mathrm{log}(n_\mathrm{H}/[\mathrm{cm^{-3}}])=3.0$ can not reproduce some of the $L_\mathrm{[OIII]}/SFR$ ratios of the $z=6-9$ galaxies (e.g., MACS1149-JD1). In order to explain the properties of $z=6-9$ galaxies with only the increase of the density alone, we need much higher density in PDRs with relatively lower density in Hii regions. However, theoretical simulations (cite: 2005ApJ...623..917H; 2010ApJ...716.1191W) predict weaker contrat of the density between Hii regions and PDRs than the constant pressure assumption used in our calculations (cite: 2019A&A...626A..23C).

- Lower $\mathrm{C/O}$ ratio\
  Spectroscopic studies suggest that the C/O abundance ratios of high redshift galaxies are lower than the solar abundance ratio (cite: 2016ApJ...826..159S). Since and luminosities depend on the carbon and oxygen abundances, respectively, lower C/O ratios of $z=6-9$ galaxies may explain the lower $L_\mathrm{[CII]}/SFR$ ratio. (cite: 2016ApJ...826..159S) report that C/O abundance ratio of $z\sim2$ galaxies is $\sim50\%$ of the solar abundance ratio. (cite: 2017MNRAS.464..469S) also suggest a $\sim50\%$ solar abundance ratio for a $z=7.7$ galaxy. The low C/O ratio would be due to young stellar population in high redshift galaxies. Oxygen is mainly produced by core-collapse supernovae (SNe), and therefore has the shortest formation timescales (cite: 2019A&ARv..27....3M). On the other hand, carbon has contributions from both core-collapse and type-Ia SNe and from AGB stars, and its average formation timescale is longer than that of oxygen. Thus the low C/O ratio indicates young stellar age with the ongoing production of carbon. The lowest C/O would be $\mathrm{C/O}\simeq0.1(\mathrm{C/O})_\odot$ based on theoretical calculations (cite: 2019A&ARv..27....3M) and observations (cite: 2016ApJ...832..171T; 2017MNRAS.467..802C). We conduct model calculations again with 50% and 10% solar abundance ratio, $[\mathrm{C/O}]=-0.3$ and $-1.0$, with fixing the oxygen abundance. We find that the $L_\mathrm{[OIII]}/SFR$ ratio does not change, while the $L_\mathrm{[CII]}/SFR$ ratio decreases by 0.3 dex and 0.9 dex, for $[\mathrm{C/O}]=-0.3$ and $-1.0$, respectively. $[\mathrm{C/O}]=-0.3$ would explain the 0.3 dex lower $L_\mathrm{[CII]}/SFR$ ratio for a part of the detected galaxies at $z=6-9$. For the undetected galaxies, $[\mathrm{C/O}]=-1.0$ cannot reproduce the $>1\ \mathrm{dex}$ lower $L_\mathrm{[CII]}/SFR$ ratio. Therefore, low C/O ratios would reproduce a part of the $z=6-9$ galaxies, but not all of them. Note that theoretical simulations in (cite: 2020arXiv200101853A) also indicate that low C/O ratios partly contribute to the observed high /\[Cii\] ratios.

  ![](fig_punch.pdf)

  ![](fig_punch_combination.pdf)

- Lower PDR covering fraction ($C_\mathrm{PDR}$)\
  emission comes from Hii regions, while emission mainly comes from PDRs (cite: 2006ApJ...644..283K; 2019A&A...626A..23C). Thus the covering fraction of the PDR (and the neutral Hi gas) with respect to the Hii region, $C_\mathrm{PDR}$, is an important parameter to determine the luminosity and the /\[Cii\] ratio. Following (cite: 2019A&A...626A..23C), we define the PDR covering fraction, $C_\mathrm{PDR}$, as a fraction of the number of sightlines with PDRs to that with Hii regions, $$\begin{equation}
  C_\mathrm{PDR}=\frac{\mathrm{No.\ of\ sightlines\ with\ PDRs}}{\mathrm{No.\ of\ sightlines\ with\ {H\textsc{ii}}\ regions}}.
  \end{equation}$$ $C_\mathrm{PDR}$ is a parameter varying from zero to unity that corresponds to a linear scaling of the PDR intensities. If $C_\mathrm{PDR}=1$, all of the Hii regions are covered with PDRs (cases (a) and (b) in Figure [15](#fig_punch)). If $C_\mathrm{PDR}=0$, none of the Hii regions are covered with PDRs (density-bounded, case (c) in Figure [15](#fig_punch)).

  For galaxies with $Z\sim0.05Z_\odot$, the fraction of emission that comes from Hii regions is $\sim1\%$ (cite: 2019A&A...626A..23C). As shown in the right panel of Figure [13](#fig_cl_Uion_Cpdr), if we consider an extreme case of $C_\mathrm{PDR}=0$, the luminosity decreases by $\sim99\%$ ($-2\ \mathrm{dex}$), which can explain the systemically lower $L_\mathrm{[CII]}/SFR$ ratios of the $z=6-9$ galaxies compared to the $z\sim0$ galaxies. Thus the lower PDR covering fraction could be an origin of the high /\[Cii\] ratio of high redshift galaxies. The low PDR covering fraction may be due to compact sizes of galaxies or outflow, consistent with observational evidence of higher outflow velocity in higher redshift galaxies (cite: 2017ApJ...850...51S; 2019arXiv190403106S). These low $C_\mathrm{PDR}$ galaxies may allow a significant escape of Lyman continuum photons like a density-bounded nebula (cite: 2014MNRAS.442..900N), and can be important contributors for the cosmic reionization.

- CMB attenuation effect\
  At $z=6-9$, the CMB radiation affects FIR emission lines from galaxies, because the CMB temperature is around $20-30\ \mathrm{K}$, sometimes comparable to excitation temperatures of the emission lines (cite: 2013ApJ...766...13D; 2014ApJ...784...99G; 2015ApJ...813...36V; 2015MNRAS.453.1898P; 2017MNRAS.465.2540P; 2018A&A...609A.130L). The CMB effect does not have a significant impact on emission from Hii regions (e.g., ) due to its high excitation temperature, but becomes important for emission from PDRs, such as in diffuse PDRs. The high temperature of the CMB can heat the $\mathrm{C^+}$ gas, while the CMB represents a strong background. As a result the emission appears to be weaker, so called the CMB attenuation. Recent calculations by (cite: 2018A&A...609A.130L) show that emission is significantly attenuated by the CMB (cite: 2014ApJ...784...99G). However, as discussed in (cite: 2019MNRAS.487L..81L), the maximum effect of the CMB attenuation is $\sim0.5\ \mathrm{dex}$. Thus the CMB attenuation effect explains the 0.3-0.5 dex lower $L_\mathrm{[CII]}/SFR$ ratio of a part of the detected galaxies, but cannot explain the $>1.0$ dex lower ratio of the undetected galaxies at $z=6-9$.

- Spatially extended halo\
  (cite: 2019arXiv190206760F) detect spatially extended halos around galaxies at $z=5-7$. Such halos could be missed in the flux measurements, resulting in the lower $L_\mathrm{[CII]}/SFR$ ratios of the $z=6-9$ galaxies. However, we use the $2\ensuremath{''}$-radius apertures for the flux measurements, which cover the total flux of the halo. In addition, this effect is not enough to explain the low $L_\mathrm{[CII]}/SFR$ ratios in other studies. For example, if the emission flux is measured in a $\sim0.$$''$$7$-diameter aperture, comparable to beam sizes in (cite: 2016Sci...352.1559I) and (cite: 2019MNRAS.487L..81L), the total flux is underestimated only up to $\sim0.6\ \mathrm{dex}$, assuming the radial profile of the halo in (cite: 2019arXiv190206760F). Thus the extended halo cannot explain the low $L_\mathrm{[CII]}/SFR$ ratios of the $z=6-9$ galaxies.

- Inclination effect\
  (cite: 2019MNRAS.487.3007K) suggest that inclination effects are responsible for some of the non-detections of emission in $z>6$ galaxies. Mock ALMA simulations in (cite: 2019MNRAS.487.3007K) show that is detected at $>5\sigma$ when seen face-on, while in the edge-on case it remains undetected because the larger intrinsic FWHM ($\sim600\ \mathrm{km\ s^{-1}}$) pushes the line peak flux below the detection limit. However, in this case, the emission line is also difficult to be detected, resulting no significant change in the / ratio. In addition, the observed FWHMs of the emission lines are $200-400\ \mathrm{km\ s^{-1}}$, not as large as $600\ \mathrm{km\ s^{-1}}$ predicted in (cite: 2019MNRAS.487.3007K). Thus the inclination effect cannot explain the high / ratio of $z=6-9$ galaxies.

Based on these discussions, we conclude that A) higher ionization parameter or E) lower PDR covering fraction can explain the properties of the $z=6-9$ galaxies including the high /\[Cii\] ratios and low $L_\mathrm{[CII]}/SFR$ ratios. Figure [15](#fig_punch) illustrates these cases. Compared to the $z\sim0$ galaxies (case (a)), we need the $\times100$ higher ionization parameter (case (b)), or very low PDR covering fraction ($C_\mathrm{PDR}=0$) like a density-bounded nebula (case (c)). The middle of these two cases, i.e., $\times\sim10$ higher $U_\mathrm{ion}$ and $C_\mathrm{PDR}\sim0.1$, is also possible (Figure [16](#fig_punch_combination)). We find that C) higher density, D) lower $\mathrm{C/O}$ ratio, and F) CMB attenuation effect can reproduce only a part of the $z=6-9$ galaxies, but these effects cannot explain all of the $z=6-9$ galaxies with and observations by itself. The combination of two of these effects can reproduce the observed properties of the $z=6-9$ galaxies.

## /\[Nii\] Ratios and Ionization parameters

Figure [17](#fig_cl_OIINII_qion) shows the 88$\mu$m/122$\mu$m ratio as a function of the ionization parameter from our Cloudy calculations. Since the critical densities of 122$\mu$m and 88$\mu$m are similar (310 and 510 cm$^{-3}$, respectively), the / ratio is not sensitive to the electron density, but sensitive to the ionization parameter, due to the different ionization potential between $\mathrm{O^{2+}}$ and $\mathrm{N^+}$. Figure [17](#fig_cl_OIINII_qion) also indicates that the / ratio becomes lower with higher metallicity due to less high energy photons ionizing $\mathrm{O}^+$ to $\mathrm{O}^{2+}$. The N/O abundance ratio is assumed to be the solar abundance ratio. This assumption is reasonable as long as we are focusing on galaxies with $Z<0.23\ Z_\odot$ (cite: 2002ApJS..142...35K). Here we discuss whether the non-detections of in our targets are consistent with high $U_\mathrm{ion}$ or low $C_\mathrm{PDR}$ scenarios suggested by the high / ratio in Section [6.1](#ss_dis_OIIICII). The observed / ratios are $>5.8$, $>3.2$, and $>13.8$ for J1211-0118, J0235-0532, and J0217-0208, respectively, corresponding to ionization parameters of $\mathrm{log}U_\mathrm{ion}>-3.1$. This is consistent with the high $U_\mathrm{ion}$ scenario ($\mathrm{log}U_\mathrm{ion}>-3$), and the low $C_\mathrm{PDR}$ scenario with fixed $U_\mathrm{ion}=-3$. Note that the / ratio also depends on the excitation temperature, because the 88$\mu$m line is the lower transition ($^3P_1\rightarrow^3P_0$) while the 122$\mu$m line is the upper transition ($^3P_2\rightarrow^3P_1$). Nonetheless, recent ALMA observations report weak 205$\mu$m ($^3P_1\rightarrow^3P_0$) lines in LBGs at $z\sim 5$ probably due to high ionization parameters (cite: 2016ApJ...832..151P; 2019ApJ...882..168P), consistent with our results.

![](fig_OIIINII_qion_cloudy.pdf)

![](fig_CII_SFR_EW_log.pdf)

![](fig_OIIICII_EWLya.pdf)

## Correlations with Ly$\alpha$ and Physical Interpretations

(cite: 2018ApJ...859...84H) report the anti-correlation between the $L_\mathrm{[CII]}/SFR$ ratio and the Ly$\alpha$ EW, indicating the deficit in LAEs. Our targets show a good anti-correlation with $(L_\mathrm{[CII]}/SFR, EW^0_\mathrm{Ly\alpha})=(1.6\times10^7,6.9)$, $(1.5\times10^7,15)$, and $(0.8\times10^7,41)$ in units of $(L_\odot/(M_\odot\ \mathrm{yr}^{-1}), \mathrm{\AA})$ for J1211-0118, J0217-0208, and J0235-0532, respectively. Including the results of our targets and the literature, we find that the anti-correlation holds with the $99.6\%$ significance level with the Kendall’s tau test (see the left panel of Figure [18](#fig_CIISFR_EW)). In the left panel of Figure [18](#fig_CIISFR_EW), we also plot the following power-law function: $$\begin{equation}
\label{eq_CIISFR_EW}
\mathrm{log}(L_\mathrm{[CII]}/SFR)=-0.44\times\mathrm{log}EW^\mathrm{0,int}_\mathrm{Ly\alpha}+7.5.
\end{equation}$$ In order to investigate whether this anti-correlation is made by a selection effect in which high $EW^0_\mathrm{Ly\alpha}$ galaxies tend to be less luminous (less massive) galaxies, we calculate median SFRs of galaxies in $EW^\mathrm{0,int}_\mathrm{Ly\alpha}$ bins. The calculated median SFRs are $21$, $26$, and $18\ M_\odot\ \mathrm{yr^{-1}}$ for $EW^\mathrm{0,int}_\mathrm{Ly\alpha}<10\ \mathrm{\AA}$, $10\ \mathrm{\AA}<EW^\mathrm{0,int}_\mathrm{Ly\alpha}<50\ \mathrm{\AA}$, and $50\ \mathrm{\AA}<EW^\mathrm{0,int}_\mathrm{Ly\alpha}$, respectively. Because the SFR values are not significantly different, the anti-correlation would not be explained by the selection effect.

Recently (cite: 2020arXiv200200979S) studied the $L_\mathrm{[CII]}/SFR-EW^0_\mathrm{Ly\alpha}$ relation using the ALPINE sample, and reported a weaker dependence of $L_\mathrm{[CII]}/SFR$ on $EW^0_\mathrm{Ly\alpha}$ with a slope of $-0.11$ in Equation ([\[eq_CIISFR_EW\]](#eq_CIISFR_EW)) compared to our result. They discussed that the difference between their result and our result can be explained by the sample difference, their use of a single IMF, a consistent use of calibrated SFRs (no SED-based SFRs) following (cite: 2019ApJ...881..124M), and/or an adoption of conservative line widths to derive $L_\mathrm{[CII]}$ upper limits. Regarding the IMF, all of the SFRs used in this study are based on the (cite: 2003PASP..115..763C) IMF and corrected for the IMF differences. To check whether the difference in the $L_\mathrm{[CII]}/SFR-EW^0_\mathrm{Ly\alpha}$ relations is due to the methods of estimating SFRs or deriving $L_\mathrm{[CII]}$ upper limits, we calculate the significance level of the anti-correlation from our sample in two cases of using SFRs in (cite: 2019ApJ...881..124M), and excluding upper limit data. We find that the anti-correlation is significant with the $99.5\%$ and $99.4\%$ significance levels (with slopes of $-0.50$ and $-0.36$ in Equation ([\[eq_CIISFR_EW\]](#eq_CIISFR_EW))) in these two cases, respectively, indicating that the difference of the method cannot explain the difference in the $L_\mathrm{[CII]}/SFR-EW^0_\mathrm{Ly\alpha}$ relations. We also calculate the significance using our sample without correction for IGM absorption in (cite: 2018ApJ...859...84H), and find that the anti-correlation still holds at the $95\%$ level (with a slope of $-0.28$). These results indicate that the difference of the $L_\mathrm{[CII]}/SFR-EW^0_\mathrm{Ly\alpha}$ relation in this study and (cite: 2020arXiv200200979S) is due to the sample difference. One possible explanation is a difference of redshifts in the samples. Our galaxies are mainly at $z>6$, while the ALPINE sample in (cite: 2020arXiv200200979S) is based on galaxies at $z=4-6$. The other possible explanation is a difference of specific SFRs. Our galaxy sample contains all of the results reported, while the ALPINE sample is selected to be located on the star-formation main sequence, which could miss galaxies with high specific SFRs such as LAEs (cite: 2010MNRAS.402.1580O; 2016ApJ...817...79H; 2018ApJ...859...84H).

The right panel of Figure [18](#fig_CIISFR_EW) shows the /\[Cii\] ratios as a function of the Ly$\alpha$ EW. We find that galaxies with higher $EW^\mathrm{0,int}_\mathrm{Ly\alpha}$ tend to have higher /\[Cii\] ratios at the $\sim90\%$ significance level (cite: 2019PASJ...71...71H). As discussed in Section [6.1](#ss_dis_OIIICII), high /\[Cii\] ratios would be due to high ionization parameters or low PDR covering fraction. In the high ionization parameter case, the intense radiation field would ionize $\mathrm{C^{+}}$ and neutral hydrogen in PDRs, decreasing the emissivity and Hi column density, and increasing the transmission of Ly$\alpha$. In the low PDR covering fraction case, Ly$\alpha$ photons directly escape from Hii regions that are not covered by PDRs. Thus, the origin of the deficit in LAEs would be the high ionization parameter or low PDR covering fraction.

The low PDR covering fraction would also enhance the Lyman continuum photon escape from galaxies at the reionization epoch. Indeed, recently (cite: 2019arXiv190901368W) report that $z\sim0$ galaxies with weak emission are Lyman continuum leakers. Since the ionization potential of Sii is 10.4 eV, less than that of Hii (13.6 eV), most of the emission come from PDRs. Thus weak emission would be signposts of the low PDR covering fraction, resulting the Lyman continuum leakage. Because the ionization potential of Cii is 11.3 eV, less than 13.6 eV, the weak emission will be also signposts of the Lyman continuum leakage. Therefore, the $z=6-9$ galaxies with low $L_\mathrm{[CII]}/SFR$ (and high $L_\mathrm{[OIII]}/L_\mathrm{[CII]}$) would be Lyman continuum leakers, significantly contributing to reionization.

# Summary

In this paper, we present our new ALMA observations targeting three LBGs at $z\sim6$, J1211-0118, J0235-0532, and J0217-0208, which are identified in the Subaru/HSC survey, and are already spectroscopically confirmed with Ly$\alpha$. In conjunction with the previous ALMA observations for $z>5$ galaxies, we study 88$\mu$m, 158$\mu$m, 122$\mu$m, and dust continuum emission, and examine their relations with SFRs and rest-UV properties such as the UV slope $\beta$ and the Ly$\alpha$ EWs. We then discuss the physical origins of the observed properties based on the model calculations with Cloudy. Our major findings are summarized as below.

1.  We detect and emission lines from all of our targets at the $4.3-11.8\sigma$ significance levels. The redshifts derived from the and lines are consistent within $1\sigma$ uncertainties, and Ly$\alpha$ emission lines are redshifted from the and redshifts by $\Delta v_\mathrm{Ly\alpha}\simeq40-200\ \mathrm{km\ s^{-1}}$. The emission are not detected at $>3\sigma$ in our targets.

2.  The luminosities of our targets are comparable to or higher than the $L_\mathrm{[OIII]}-SFR$ relation of $z\sim0$ low metallicity dwarf galaxies. The luminosities are lower than those of the dwarf galaxies, and comparable to the local starburst galaxies. As a result, our galaxies show $\sim10$ times higher / ratios than local galaxies, similar to other $z=6-9$ galaxies in the literature.

3.  In J1211-0118 and J0217-0208, the emission are spatially well resolved, and show velocity gradients of $\Delta v_\mathrm{obs}\sim220-250\ \mathrm{km\ s^{-1}}$. The ratios of the velocity gradient to the velocity dispersion are $\Delta v_\mathrm{obs}/2\sigma_\mathrm{tot}>0.4$, indicating that J1211-0118 and J0217-0208 are consistent with rotation supported systems.

4.  We identify dust continuum emission at $120\ \mathrm{\mu m}$ and $160\ \mathrm{\mu m}$ in J1211-0118 and J0217-0208, but not in J0235-0532. We fit the observed continuum fluxes and upper limits with the modified black body, and obtain the IR luminosities of $L_\mathrm{IR}\sim10^{11}\ L_\odot$, and the dust temperatures of $T_\mathrm{dust}\sim30-40\ \mathrm{K}$ for J1211-0118 and J0217-0208. We also obtain the upper limit of $L_\mathrm{IR}<2.5\times10^{11}\ L_\odot$ with $T_\mathrm{dust}<50\ \mathrm{K}$ for J0235-0532.

5.  J1211-0118 follows the Calzetti IRX-$\beta_\mathrm{UV}$ relation, and the upper limit of J0235-0532 is consistent with both the Calzetti, Takeuchi, and SMC relations. The IRX value of J0217-0208 is lower than the SMC IRX-$\beta$ relation, which would be due to the geometry effect, AGN activity, or the high molecular gas fraction.

6.  Based on the Cloudy calculations, we discuss the physical origins of the high / ratios and low $L_\mathrm{[CII]}/SFR$ ratios of the $z=6-9$ galaxies compared to the $z\sim0$ galaxies. We find that the properties of the $z=6-9$ galaxies can be explained by $\times10-100$ higher ionization parameters or low PDR covering fractions of $0-10\%$ like a density bounded nebula, possibly due to the young stellar populations, compact sizes of the $z=6-9$ galaxies, or outflow, consistent with our observations. The low PDR covering fraction would enhancing the Ly$\alpha$, Lyman continuum, and $\mathrm{C^+}$ ionizing photon escapes from galaxies. Higher hydrogen density, lower $\mathrm{C/O}$ ratio, and the CMB attenuation effect can reproduce a part of the $z=6-9$ galaxies, but not all of the $z=6-9$ galaxies with and observations by itself, and the combination of these effects is needed.

7.  Including our new observations, we find the anti-correlation between $L_\mathrm{[CII]}/SFR$ and $EW^{0,\mathrm{int}}_\mathrm{Ly\alpha}$ at the $>95\%$ significance level. We also identify the correlation between the / ratio and the Ly$\alpha$ EW at the $\sim90\%$ significance level. These relations indicate that the origin of the deficit in LAEs would be the high ionization parameters or low PDR covering fractions, which make the Ly$\alpha$ and Lyman continuum photons escape easier.

# Acknowledgments

We thank the anonymous referee for a careful reading and valuable comments that improved the clarity of the paper. We thank Daisuke Iono, Thomas Greve, Chris Matzner, Tomonari Michiyama, Kentaro Nagamine, Daniel Schaerer, Masayuki Umemura, and Hidenobu Yajima for their useful comments and discussions.

This paper makes use of the following ALMA data: ADS/JAO.ALMA #2017.1.00508.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The Hyper Suprime-Cam (HSC) collaboration includes the astronomical communities of Japan and Taiwan, and Princeton University. The HSC instrumentation and software were developed by the National Astronomical Observatory of Japan (NAOJ), the Kavli Institute for the Physics and Mathematics of the Universe (Kavli IPMU), the University of Tokyo, the High Energy Accelerator Research Organization (KEK), the Academia Sinica Institute for Astronomy and Astrophysics in Taiwan (ASIAA), and Princeton University. Funding was contributed by the FIRST program from Japanese Cabinet Office, the Ministry of Education, Culture, Sports, Science and Technology (MEXT), the Japan Society for the Promotion of Science (JSPS), Japan Science and Technology Agency (JST), the Toray Science Foundation, NAOJ, Kavli IPMU, KEK, ASIAA, and Princeton University.

The Pan-STARRS1 Surveys (PS1) have been made possible through contributions of the Institute for Astronomy, the University of Hawaii, the Pan-STARRS Project Office, the Max-Planck Society and its participating institutes, the Max Planck Institute for Astronomy, Heidelberg and the Max Planck Institute for Extraterrestrial Physics, Garching, The Johns Hopkins University, Durham University, the University of Edinburgh, Queen’s University Belfast, the Harvard-Smithsonian Center for Astrophysics, the Las Cumbres Observatory Global Telescope Network Incorporated, the National Central University of Taiwan, the Space Telescope Science Institute, the National Aeronautics and Space Administration under Grant No. NNX08AR22G issued through the Planetary Science Division of the NASA Science Mission Directorate, the National Science Foundation under Grant No. AST-1238877, the University of Maryland, and Eotvos Lorand University (ELTE).

This paper makes use of software developed for the Large Synoptic Survey Telescope. We thank the LSST Project for making their code available as free software at http://dm.lsst.org.

This work is supported by World Premier International Research Center Initiative (WPI Initiative), MEXT, Japan. Y. Harikane acknowledges support from the Advanced Leading Graduate Course for Photon Science (ALPS) grant and the JSPS KAKENHI grant No. 16J03329 and 19J01222 through the JSPS Research Fellowship for Young Scientists. A.K. Inoue was supported by the JSPS KAKENHI grant No. 17H01114 and by the NAOJ ALMA grant No. 2016-01A. Y. Matsuoka was supported by the JSPS KAKENHI grant No. 17H04830 and the Mitsubishi Foundation grant No. 30140. T. Nagao was supported by the JSPS KAKENHI grant No. 16H03958 and 19H00697. Y. Matsuda acknowledges support from the JSPS grants 17H04831, 17KK0098 and 19H00697. L. Vallini acknowledges funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie Grant agreement No. 746119.

+:--------------:+:-----------------:+:---------------------------------:+:-------------------------:+:----------------------:+:------------------------:+:----------:+
| Name           | $z_\mathrm{spec}$ | $L_\mathrm{[CII]}$                | $L_\mathrm{[OIII]}$       | $SFR_\mathrm{tot}$     | $EW_\mathrm{Ly\alpha}^0$ | Ref.       |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| \(1\)          | \(2\)             | \(3\)                             | \(4\)                     | \(5\)                  | \(6\)                    | \(7\)      |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| LBGs & LAEs                                                                                                                                                         |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| MACS1149-JD1   | 9.110             | $<4.0\times10^{6}$                | $(7.4\pm1.6)\times10^{7}$ | $4.2^{+0.8}_{-1.1}$    | $10$                     | H18a, L19  |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| A2744-YD4      | 8.382             | $<2.0\times10^{7}$                | $(7.0\pm1.7)\times10^{7}$ | $12.9^{+11.1}_{-6.0}$  | $10.7\pm2.7$             | L17a,19    |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| MACS0416-Y1    | 8.312             | $(1.4\pm0.2)\times10^{8}$         | $(1.2\pm0.3)\times10^{9}$ | $57.0^{+175.0}_{-0.2}$ | $<16.7$                  | Tam19, B20 |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| SXDF-NB1006-2  | 7.215             | $<8.4\times10^{7}$                | $(9.9\pm2.1)\times10^{8}$ | $219^{+105}_{-176}$    | $>15.4$                  | I16        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| B14-65666      | 7.168             | $(1.1\pm0.1)\times10^{9}$         | $(3.4\pm0.4)\times10^{9}$ | $200^{+82}_{-38}$      | $3.7_{-1.1}^{+1.7}$      | H19, F16   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| BDF-3299       | 7.109             | $(4.9\pm0.6)\times10^{7}$         | $(1.8\pm0.2)\times10^{8}$ | $5.4$                  | $38.8$                   | C17, M15   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| J0217-0208     | 6.204             | $(1.4\pm0.2)\times10^{9}$         | $(8.5\pm2.0)\times10^{9}$ | $96$                   | $15\pm1$                 | This work  |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| J0235-0532     | 6.090             | $(4.3\pm0.7)\times10^{8}$         | $(3.8\pm0.3)\times10^{9}$ | $54$                   | $41\pm2$                 | This work  |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| J1211-0118     | 6.029             | $(1.4\pm0.1)\times10^{9}$         | $(4.8\pm0.7)\times10^{9}$ | $86$                   | $6.9\pm0.8$              | This work  |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| z8-GND-5296    | 7.508             | $<3.5\times10^{8}$                | $\dots$                   | $14.7$                 | $8$                      | S15, F12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| A1689-zD1      | 7.5               | $<8.9\times10^{7}$                | $\dots$                   | $11.7^{+4.1}_{-2.2}$   | $<27$                    | W15        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| COSMOS13679    | 7.154             | $(7.4\pm1.7)\times10^{7}$         | $\dots$                   | $15.1$                 | $15$                     | P16        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| BDF-521        | 7.109             | $<6.0\times10^{7}$                | $\dots$                   | $5.6$                  | $64$                     | M15, V11   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| IOK-1          | 6.965             | $<3.4\times10^{7}$                | $\dots$                   | $15.1\pm0.9$           | $43$                     | O14, O12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| COS-3018555981 | 6.854             | $(4.7\pm0.5)\times10^{8}$         | $\dots$                   | $19.2\pm1.6$           | $<2.9$                   | S17, L17   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| SDF46975       | 6.844             | $<5.8\times10^{7}$                | $\dots$                   | $14.5$                 | $43$                     | M15, O12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| COS-2987030247 | 6.816             | $(3.6\pm0.5)\times10^{8}$         | $\dots$                   | $22.7\pm2.0$           | $16.2^{+5.2}_{-5.5}$     | S17, L17   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| RXJ1347-1145   | 6.765             | $(1.5^{+0.2}_{-0.4})\times10^{7}$ | $\dots$                   | $8.5^{+5.9}_{-1.0}$    | $26\pm4$                 | B16        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| NTTDF6345      | 6.701             | $(1.9\pm0.3)\times10^{8}$         | $\dots$                   | $9.4$                  | $15$                     | P16        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| UDS16291       | 6.638             | $(7.2\pm1.7)\times10^{7}$         | $\dots$                   | $10.0$                 | $6$                      | P16        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| COSMOS24108    | 6.629             | $(1.0\pm0.2)\times10^{8}$         | $\dots$                   | $18.3$                 | $27$                     | P16        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| CR7            | 6.604             | $(2.0\pm0.4)\times10^{8}$         | $\dots$                   | $28.4\pm1.3$           | $211\pm20$               | M17, So15  |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| Himiko         | 6.595             | $(1.2\pm0.2)\times10^{8}$         | $\dots$                   | $19.2\pm1.3$           | $78^{+8}_{-6}$           | C18, O13   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| UDS4821        | 6.561             | $<6.8\times10^{7}$                | $\dots$                   | $13$                   | $48$                     | C17        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HCM6A          | 6.56              | $<6.5\times10^{7}$                | $\dots$                   | $6.3$                  | $25.1$                   | K13, H02   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| MASOSA         | 6.543             | $<6.6\times10^{7}$                | $\dots$                   | $9.5_{-1.3}^{+2.5}$    | $145^{+50}_{-43}$        | M19        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| VR7            | 6.529             | $(4.8\pm0.4)\times10^{8}$         | $\dots$                   | $34.0_{-1.3}^{+3.2}$   | $34^{+4}_{-4}$           | M19        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| COSMOS20521    | 6.36              | $<4.8\times10^{7}$                | $\dots$                   | $14$                   | $10$                     | C17        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| GOODS3203      | 6.27              | $<1.2\times10^{8}$                | $\dots$                   | $18$                   | $5$                      | C17        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| CLM1           | 6.176             | $(2.4\pm0.3)\times10^{8}$         | $\dots$                   | $37\pm4$               | $50$                     | W15, C03   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| BDF2203        | 6.12              | $(1.3\pm0.3)\times10^{8}$         | $\dots$                   | $16$                   | $3$                      | C17        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| WMH5           | 6.076             | $(6.6\pm0.8)\times10^{8}$         | $\dots$                   | $43\pm5$               | $13\pm4$                 | W15, W13   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| NTTDF2313      | 6.07              | $<4.5\times10^{7}$                | $\dots$                   | $12$                   | $0$                      | C17        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| A383-5.1       | 6.029             | $(8.9\pm3.1)\times10^{6}$         | $\dots$                   | $2.0$                  | $138$                    | K16, St15  |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| WMH13          | 5.985             | $(1.1\pm0.2)\times10^{8}$         | $\dots$                   | $24.9$                 | $27$                     | F19        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ1            | 5.690             | $(2.5\pm1.9)\times10^{8}$         | $\dots$                   | $24^{+6}_{-3}$         | $5.3^{+2.6}_{-4.1}$      | C15, M12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| NB816-S-61269  | 5.684             | $(2.1\pm0.5)\times10^{8}$         | $\dots$                   | $14.4$                 | $93.3$                   | F19        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ2            | 5.670             | $(3.6\pm3.4)\times10^{8}$         | $\dots$                   | $25^{+5}_{-2}$         | $6.9\pm2.0$              | C15        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ10           | 5.659             | $(1.3\pm0.4)\times10^{9}$         | $\dots$                   | $169^{+32}_{-27}$      | $24.5^{+9.2}_{-11.0}$    | C15, M12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ9            | 5.548             | $(1.6\pm0.3)\times10^{9}$         | $\dots$                   | $67^{+30}_{-20}$       | $14.4^{+6.8}_{-5.4}$     | C15, M12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ3            | 5.546             | $(4.7\pm3.0)\times10^{8}$         | $\dots$                   | $18^{+8}_{-3}$         | $<3.6$                   | C15        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ4            | 5.540             | $(9.5\pm4.8)\times10^{8}$         | $\dots$                   | $51^{+54}_{-18}$       | $10.2^{+0.9}_{-4.4}$     | C15, M12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ6            | 5.290             | $(1.4\pm0.6)\times10^{9}$         | $\dots$                   | $49^{+44}_{-12}$       | $8.0^{+12.1}_{-7.3}$     | C15, M12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ7            | 5.250             | $(5.5\pm3.0)\times10^{8}$         | $\dots$                   | $21^{+5}_{-2}$         | $9.8\pm5.5$              | C15        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| HZ8            | 5.148             | $(2.6\pm1.1)\times10^{8}$         | $\dots$                   | $18^{+5}_{-2}$         | $27.1^{+12.9}_{-14.7}$   | C15, M12   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| SMGs                                                                                                                                                                |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| SPT0311-58-E   | 6.900             | $(5.4\pm0.5)\times10^{9}$         | $(6.9\pm0.7)\times10^{9}$ | $540\pm175$            | $\dots$                  | M18        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| SPT0311-58-W   | 6.900             | $(1.0\pm0.2)\times10^{10}$        | $(5.7\pm1.1)\times10^{9}$ | $2900\pm1800$          | $\dots$                  | M18        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| J2100-SB       | 6.0806            | $(1.8\pm0.9)\times10^{9}$         | $(2.9\pm0.1)\times10^{9}$ | $284\pm30$             | $\dots$                  | W18        |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+
| COSMOS-AzTEC-1 | 4.342             | $(6.3\pm0.6)\times10^{9}$         | $(2.2\pm0.7)\times10^{9}$ | $1169^{+11}_{-274}$    | $\dots$                  | Tad18,19   |
+----------------+-------------------+-----------------------------------+---------------------------+------------------------+--------------------------+------------+

: Summary of High Redshift Galaxies with ALMA Observations

Table notes: (1) Object Name. (2) Redshift determined with Ly$\alpha$, Lyman break, rest-frame UV absorption lines, \[Cii\]158$\mathrm{\mu m}$, or \[Oiii\]88$\mathrm{\mu m}$. (3) \[Cii\]158$\mathrm{\mu m}$ luminosity or its $3\sigma$ upper limit in units of $L_\odot$. (4) \[Oiii\]88$\mathrm{\mu m}$ luminosity in units of $L_\odot$. (5) Total SFR ($=SFR_\mathrm{UV}+SFR_\mathrm{IR}$) in units of $M_\odot\ \mathrm{yr^{-1}}$. (6) Rest-frame Ly$\alpha$ EW not corrected for the inter-galactic medium (IGM) absorption in units of $\mathrm{\AA}$. (7) Reference (B17: (cite: 2017ApJ...836L...2B), B20: (cite: 2020MNRAS.493.4294B), C03: (cite: 2003A&A...405L..19C), C15: (cite: 2015Natur.522..455C), C17: (cite: 2017A&A...605A..42C), C18a: (cite: 2018ApJ...854L...7C), C18b: (cite: 2018MNRAS.478.1170C), F13: (cite: 2013Natur.502..524F), F16: (cite: 2016ApJ...822...46F), F19: (cite: 2019arXiv190206760F), H02: (cite: 2002ApJ...568L..75H), H18a: (cite: 2018Natur.557..392H) H19: (cite: 2019PASJ...71...71H) I16: (cite: 2016Sci...352.1559I), K13: (cite: 2013ApJ...771L..20K), K16: (cite: 2016MNRAS.462L...6K), L17a: (cite: 2017ApJ...837L..21L), L17b: (cite: 2017ApJ...851...40L), L19: (cite: 2019MNRAS.487L..81L) M12: (cite: 2012ApJ...760..128M), M15: (cite: 2015MNRAS.452...54M), M17: (cite: 2017ApJ...851..145M), M18: (cite: 2018Natur.553...51M), M19: (cite: 2019ApJ...881..124M), O12: (cite: 2012ApJ...744...83O), O13: (cite: 2013ApJ...778..102O), O14: (cite: 2014ApJ...792...34O), P16: (cite: 2016ApJ...829L..11P), S12: (cite: 2012ApJ...752..114S), Sc15: (cite: 2015A&A...574A..19S), So15: (cite: 2015ApJ...808..139S), St15: (cite: 2015MNRAS.450.1846S), S17: (cite: 2017arXiv170604614S), Tad18: (cite: 2018Natur.560..613T), Tad19: (cite: 2019ApJ...876....1T), Tam19: (cite: 2019ApJ...874...27T), V11: (cite: 2011ApJ...730L..35V), W13: (cite: 2013AJ....145....4W), Wa15: (cite: 2015Natur.519..327W), Wi15: (cite: 2015ApJ...807..180W), W18: (cite: 2018ApJ...869L..22W)).

natexlab

(ref: 2005ApJS..161...65A) Abel, N. P., Ferland, G. J., Shaw, G., & van Hoof, P. A. M. 2005, ApJS, 161, 65

(ref: 2018PASJ...70S...4A) Aihara, H., Arimoto, N., Armstrong, R., et al. 2018, PASJ, 70, S4

(ref: 2020arXiv200101853A) Arata, S., Yajima, H., Nagamine, K., Abe, M., & Khochfar, S. 2020, arXiv e-prints, arXiv:2001.01853

(ref: 2019ApJ...881L..23B) Bañados, E., Novak, M., Neeleman, M., et al. 2019, ApJL, 881, L23

(ref: 2020MNRAS.493.4294B) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294

(ref: 2017ApJ...845...41B) Barisic, I., Faisst, A. L., Capak, P. L., et al. 2017, ApJ, 845, 41

(ref: 2018MNRAS.477..552B) Behrens, C., Pallottini, A., Ferrara, A., Gallerani, S., & Vallini, L. 2018, MNRAS, 477, 552

(ref: 2016ApJ...833...72B) Bouwens, R. J., Aravena, M., Decarli, R., et al. 2016, ApJ, 833, 72

(ref: 2017ApJ...836L...2B) Bradač, M., Garcia-Appadoo, D., Huang, K.-H., et al. 2017, ApJL, 836, L2

(ref: 2000ApJ...533..682C) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: 2015Natur.522..455C) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455

(ref: 2018ApJ...854L...7C) Carniani, S., Maiolino, R., Smit, R., & Amorı́n, R. 2018a, ApJL, 854, L7

(ref: 2017A&A...605A..42C) Carniani, S., Maiolino, R., Pallottini, A., et al. 2017, A&A, 605, A42

(ref: 2018MNRAS.478.1170C) Carniani, S., Maiolino, R., Amorin, R., et al. 2018b, MNRAS, 478, 1170

(ref: 2003PASP..115..763C) Chabrier, G. 2003, PASP, 115, 763

(ref: 2017MNRAS.467..802C) Cooke, R. J., Pettini, M., & Steidel, C. C. 2017, MNRAS, 467, 802

(ref: 2015A&A...578A..53C) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, A&A, 578, A53

(ref: 2019A&A...626A..23C) Cormier, D., Abel, N. P., Hony, S., et al. 2019, A&A, 626, A23

(ref: 2003A&A...405L..19C) Cuby, J.-G., Le Fèvre, O., McCracken, H., et al. 2003, A&A, 405, L19

(ref: 2013ApJ...766...13D) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: 2014A&A...568A..62D) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: 2017ApJ...846...32D) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32

(ref: 2017PASA...34...58E) Eldridge, J. J., Stanway, E. R., Xiao, L., et al. 2017, PASA, 34, e058

(ref: 2014ApJ...795...33E) Erb, D. K., Steidel, C. C., Trainor, R. F., et al. 2014, ApJ, 795, 33

(ref: 2016ApJ...821..122F) Faisst, A. L., Capak, P., Hsieh, B. C., et al. 2016, ApJ, 821, 122

(ref: 2017ApJ...847...21F) Faisst, A. L., Capak, P. L., Yan, L., et al. 2017, ApJ, 847, 21

(ref: 1998PASP..110..761F) Ferland, G. J., Korista, K. T., Verner, D. A., et al. 1998, PASP, 110, 761

(ref: 2017RMxAA..53..385F) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385

(ref: 2017MNRAS.471.5018F) Ferrara, A., Hirashita, H., Ouchi, M., & Fujimoto, S. 2017, MNRAS, 471, 5018

(ref: 2019MNRAS.489....1F) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1

(ref: 2013Natur.502..524F) Finkelstein, S. L., Papovich, C., Dickinson, M., et al. 2013, Nature, 502, 524

(ref: 2009ApJ...706.1364F) Förster Schreiber, N. M., Genzel, R., Bouché, N., et al. 2009, ApJ, 706, 1364

(ref: 2017MNRAS.472..483F) Fudamoto, Y., Oesch, P. A., Schinnerer, E., et al. 2017, MNRAS, 472, 483

(ref: 2019arXiv190206760F) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, arXiv e-prints, arXiv:1902.06760

(ref: 2016ApJ...822...46F) Furusawa, H., Kashikawa, N., Kobayashi, M. A. R., et al. 2016, ApJ, 822, 46

(ref: 2010A&A...523A..85G) Gallerani, S., Maiolino, R., Juarez, Y., et al. 2010, A&A, 523, A85

(ref: 2014ApJ...784...99G) González-López, J., Riechers, D. A., Decarli, R., et al. 2014, ApJ, 784, 99

(ref: 2004ApJS..153...75G) Groves, B. A., Dopita, M. A., & Sutherland, R. S. 2004, ApJS, 153, 75

(ref: 2016ApJ...817...79H) Hagen, A., Zeimann, G. R., Behrens, C., et al. 2016, ApJ, 817, 79

(ref: 2018PASJ...70S..11H) Harikane, Y., Ouchi, M., Ono, Y., et al. 2018a, PASJ, 70, S11

(ref: 2018ApJ...859...84H) Harikane, Y., Ouchi, M., Shibuya, T., et al. 2018b, ApJ, 859, 84

(ref: 2019PASJ...71..109H) Hashimoto, T., Inoue, A. K., Tamura, Y., et al. 2019a, PASJ, 71, 109

(ref: 2013ApJ...765...70H) Hashimoto, T., Ouchi, M., Shimasaku, K., et al. 2013, ApJ, 765, 70

(ref: 2018Natur.557..392H) Hashimoto, T., Laporte, N., Mawatari, K., et al. 2018, Nature, 557, 392

(ref: 2019PASJ...71...71H) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019b, PASJ, 71, 71

(ref: 1983QJRAS..24..267H) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: 2005ApJ...623..917H) Hosokawa, T., & Inutsuka, S.-i. 2005, ApJ, 623, 917

(ref: 2010ApJ...715..572H) Howell, J. H., Armus, L., Mazzarella, J. M., et al. 2010, ApJ, 715, 572

(ref: 2002ApJ...568L..75H) Hu, E. M., Cowie, L. L., McMahon, R. G., et al. 2002, ApJL, 568, L75

(ref: 2014ApJ...780L..18I) Inoue, A. K., Shimizu, I., Tamura, Y., et al. 2014, ApJL, 780, L18

(ref: 2016Sci...352.1559I) Inoue, A. K., Tamura, Y., Matsuo, H., et al. 2016, Science, 352, 1559

(ref: 2013ApJ...771L..20K) Kanekar, N., Wagg, J., Chary, R. R., & Carilli, C. L. 2013, ApJL, 771, L20

(ref: 2017ApJ...835...88K) Kashino, D., Silverman, J. D., Sanders, D., et al. 2017, ApJ, 835, 88

(ref: 2006ApJ...644..283K) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, ApJ, 644, 283

(ref: 1998ARA&A..36..189K) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189

(ref: 2002ApJS..142...35K) Kewley, L. J., & Dopita, M. A. 2002, ApJS, 142, 35

(ref: 2016MNRAS.462L...6K) Knudsen, K. K., Richard, J., Kneib, J.-P., et al. 2016, MNRAS, 462, L6

(ref: 2017MNRAS.466..138K) Knudsen, K. K., Watson, D., Frayer, D., et al. 2017, MNRAS, 466, 138

(ref: 2019MNRAS.487.3007K) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2019, MNRAS, 487, 3007

(ref: 2016ApJ...823...20K) Konno, A., Ouchi, M., Nakajima, K., et al. 2016, ApJ, 823, 20

(ref: 2018MNRAS.479.4355K) Koprowski, M. P., Coppin, K. E. K., Geach, J. E., et al. 2018, MNRAS, 479, 4355

(ref: 2018A&A...609A.130L) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: 2017ApJ...851...40L) Laporte, N., Nakajima, K., Ellis, R. S., et al. 2017a, ApJ, 851, 40

(ref: 2017ApJ...837L..21L) Laporte, N., Ellis, R. S., Boone, F., et al. 2017b, ApJL, 837, L21

(ref: 2019MNRAS.487L..81L) Laporte, N., Katz, H., Ellis, R. S., et al. 2019, MNRAS, 487, L81

(ref: 2013PASP..125..600M) Madden, S. C., Rémy-Ruyer, A., Galametz, M., et al. 2013, PASP, 125, 600

(ref: 2018MNRAS.479.1180M) Mainali, R., Zitrin, A., Stark, D. P., et al. 2018, MNRAS, 479, 1180

(ref: 2019A&ARv..27....3M) Maiolino, R., & Mannucci, F. 2019, A&ARv, 27, 3

(ref: 2008A&A...488..463M) Maiolino, R., Nagao, T., Grazian, A., et al. 2008, A&A, 488, 463

(ref: 2015MNRAS.452...54M) Maiolino, R., Carniani, S., Fontana, A., et al. 2015, MNRAS, 452, 54

(ref: 2012ApJ...760..128M) Mallery, R. P., Mobasher, B., Capak, P., et al. 2012, ApJ, 760, 128

(ref: 2015MNRAS.451L..70M) Mancini, M., Schneider, R., Graziani, L., et al. 2015, MNRAS, 451, L70

(ref: 2018Natur.553...51M) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51

(ref: 2016ApJ...828...26M) Matsuoka, Y., Onoue, M., Kashikawa, N., et al. 2016, ApJ, 828, 26

(ref: 2018PASJ...70S..35M) —. 2018a, PASJ, 70, S35

(ref: 2018ApJS..237....5M) Matsuoka, Y., Iwasawa, K., Onoue, M., et al. 2018b, ApJS, 237, 5

(ref: 2019arXiv190807910M) —. 2019, arXiv e-prints, arXiv:1908.07910

(ref: 2017ApJ...851..145M) Matthee, J., Sobral, D., Boone, F., et al. 2017, ApJ, 851, 145

(ref: 2019ApJ...881..124M) Matthee, J., Sobral, D., Boogaard, L. A., et al. 2019, ApJ, 881, 124

(ref: 2018MNRAS.476.3991M) McLure, R. J., Dunlop, J. S., Cullen, F., et al. 2018, MNRAS, 476, 3991

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 1999ApJ...521...64M) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64

(ref: 2018MNRAS.481L..84M) Moriwaki, K., Yoshida, N., Shimizu, I., et al. 2018, MNRAS, 481, L84

(ref: 2012A&A...542L..34N) Nagao, T., Maiolino, R., De Breuck, C., et al. 2012, A&A, 542, L34

(ref: 2011A&A...526A.149N) Nagao, T., Maiolino, R., Marconi, A., & Matsuhara, H. 2011, A&A, 526, A149

(ref: 2014MNRAS.442..900N) Nakajima, K., & Ouchi, M. 2014, MNRAS, 442, 900

(ref: 1983ApJ...266..713O) Oke, J. B., & Gunn, J. E. 1983, ApJ, 266, 713

(ref: 2010MNRAS.402.1580O) Ono, Y., Ouchi, M., Shimasaku, K., et al. 2010, MNRAS, 402, 1580

(ref: 2012ApJ...744...83O) Ono, Y., Ouchi, M., Mobasher, B., et al. 2012, ApJ, 744, 83

(ref: 2018PASJ...70S..10O) Ono, Y., Ouchi, M., Harikane, Y., et al. 2018, PASJ, 70, S10

(ref: 2014ApJ...792...34O) Ota, K., Walter, F., Ohta, K., et al. 2014, ApJ, 792, 34

(ref: 2013ApJ...778..102O) Ouchi, M., Ellis, R., Ono, Y., et al. 2013, ApJ, 778, 102

(ref: 2017MNRAS.471.4128P) Pallottini, A., Ferrara, A., Bovino, S., et al. 2017a, MNRAS, 471, 4128

(ref: 2017MNRAS.465.2540P) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2017b, MNRAS, 465, 2540

(ref: 2015MNRAS.453.1898P) Pallottini, A., Gallerani, S., Ferrara, A., et al. 2015, MNRAS, 453, 1898

(ref: 2019MNRAS.487.1689P) Pallottini, A., Ferrara, A., Decataldo, D., et al. 2019, MNRAS, 487, 1689

(ref: 2019ApJ...882..168P) Pavesi, R., Riechers, D. A., Faisst, A. L., Stacey, G. J., & Capak, P. L. 2019, ApJ, 882, 168

(ref: 2016ApJ...832..151P) Pavesi, R., Riechers, D. A., Capak, P. L., et al. 2016, ApJ, 832, 151

(ref: 2016ApJ...829L..11P) Pentericci, L., Carniani, S., Castellano, M., et al. 2016, ApJL, 829, L11

(ref: 1998ApJ...508..539P) Pettini, M., Kellogg, M., Steidel, C. C., et al. 1998, ApJ, 508, 539

(ref: 2016A&A...594A..13P) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13

(ref: 2018ApJ...853...56R) Reddy, N. A., Oesch, P. A., Bouwens, R. J., et al. 2018, ApJ, 853, 56

(ref: 2015A&A...582A.121R) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2015, A&A, 582, A121

(ref: 2016ApJ...823..143R) Roberts-Borsani, G. W., Bouwens, R. J., Oesch, P. A., et al. 2016, ApJ, 823, 143

(ref: 1955ApJ...121..161S) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: 2016ApJ...816...23S) Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2016, ApJ, 816, 23

(ref: 2018A&A...617A.131S) Saturni, F. G., Mancini, M., Pezzulli, E., & Tombesi, F. 2018, A&A, 617, A131

(ref: 2015A&A...574A..19S) Schaerer, D., Boone, F., Zamojski, M., et al. 2015, A&A, 574, A19

(ref: 2020arXiv200200979S) Schaerer, D., Ginolfi, M., Bethermin, M., et al. 2020, arXiv e-prints, arXiv:2002.00979

(ref: 1998ApJ...500..525S) Schlegel, D. J., Finkbeiner, D. P., & Davis, M. 1998, ApJ, 500, 525

(ref: 2012ApJ...752..114S) Shibuya, T., Kashikawa, N., Ota, K., et al. 2012, ApJ, 752, 114

(ref: 2015ApJS..219...15S) Shibuya, T., Ouchi, M., & Harikane, Y. 2015, ApJS, 219, 15

(ref: 2014ApJ...788...74S) Shibuya, T., Ouchi, M., Nakajima, K., et al. 2014, ApJ, 788, 74

(ref: 2018PASJ...70S..15S) Shibuya, T., Ouchi, M., Harikane, Y., et al. 2018, PASJ, 70, S15

(ref: 2015MNRAS.451.1284S) Shimakawa, R., Kodama, T., Steidel, C. C., et al. 2015, MNRAS, 451, 1284

(ref: 2017arXiv170604614S) Smit, R., Bouwens, R. J., Carniani, S., et al. 2017, ArXiv e-prints, arXiv:1706.04614

(ref: 2019A&A...623A.157S) Sobral, D., & Matthee, J. 2019, A&A, 623, A157

(ref: 2015ApJ...808..139S) Sobral, D., Matthee, J., Darvish, B., et al. 2015, ApJ, 808, 139

(ref: 2017MNRAS.466.1242S) Sobral, D., Matthee, J., Best, P., et al. 2017, MNRAS, 466, 1242

(ref: 2016ApJ...825....5S) Song, M., Finkelstein, S. L., Ashby, M. L. N., et al. 2016, ApJ, 825, 5

(ref: 2015MNRAS.454.1393S) Stark, D. P., Walth, G., Charlot, S., et al. 2015a, MNRAS, 454, 1393

(ref: 2015MNRAS.450.1846S) Stark, D. P., Richard, J., Charlot, S., et al. 2015b, MNRAS, 450, 1846

(ref: 2017MNRAS.464..469S) Stark, D. P., Ellis, R. S., Charlot, S., et al. 2017, MNRAS, 464, 469

(ref: 2016ApJ...826..159S) Steidel, C. C., Strom, A. L., Pettini, M., et al. 2016, ApJ, 826, 159

(ref: 2019arXiv190403106S) Sugahara, Y., Ouchi, M., Harikane, Y., et al. 2019, arXiv e-prints, arXiv:1904.03106

(ref: 2017ApJ...850...51S) Sugahara, Y., Ouchi, M., Lin, L., et al. 2017, ApJ, 850, 51

(ref: 2018Natur.560..613T) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613

(ref: 2019ApJ...876....1T) Tadaki, K.-i., Iono, D., Hatsukade, B., et al. 2019, ApJ, 876, 1

(ref: 2012ApJ...755..144T) Takeuchi, T. T., Yuan, F.-T., Ikeyama, A., Murata, K. L., & Inoue, A. K. 2012, ApJ, 755, 144

(ref: 2019ApJ...874...27T) Tamura, Y., Mawatari, K., Hashimoto, T., et al. 2019, ApJ, 874, 27

(ref: 2018PASJ...70S..12T) Toshikawa, J., Uchiyama, H., Kashikawa, N., et al. 2018, PASJ, 70, S12

(ref: 2016ApJ...832..171T) Trainor, R. F., Strom, A. L., Steidel, C. C., & Rudie, G. C. 2016, ApJ, 832, 171

(ref: 2017MNRAS.467.1300V) Vallini, L., Ferrara, A., Pallottini, A., & Gallerani, S. 2017, MNRAS, 467, 1300

(ref: 2015ApJ...813...36V) Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36

(ref: 2011ApJ...730L..35V) Vanzella, E., Pentericci, L., Fontana, A., et al. 2011, ApJL, 730, L35

(ref: 2018ApJ...869L..22W) Walter, F., Riechers, D., Novak, M., et al. 2018, ApJL, 869, L22

(ref: 2019arXiv190901368W) Wang, B., Heckman, T. M., Leitherer, C., et al. 2019, arXiv e-prints, arXiv:1909.01368

(ref: 2015Natur.519..327W) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327

(ref: 2015ApJ...807..180W) Willott, C. J., Carilli, C. L., Wagg, J., & Wang, R. 2015, ApJ, 807, 180

(ref: 2013AJ....145....4W) Willott, C. J., McLure, R. J., Hibon, P., et al. 2013, AJ, 145, 4

(ref: 2010ApJ...716.1191W) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191

(ref: 2012ApJ...757..108Y) Yeh, S. C. C., & Matzner, C. D. 2012, ApJ, 757, 108

[^1]: http://www.cv.nrao.edu/php/splat/

</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Rotation vs dispersion criterion",
  "failed_quote": "$\\Delta v_\\mathrm{obs}/2\\sigma_\\mathrm{tot}=0.4$ ... (cite: 2009ApJ...706.1364F)"
 }
]
```
