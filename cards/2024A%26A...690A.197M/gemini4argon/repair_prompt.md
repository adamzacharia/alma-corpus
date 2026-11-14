# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...690A.197M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. main ©ESO 2023
November 30, 2023

## **The ALMA-CRISTAL survey**

### **Widespread dust-obscured star formation in typical star-forming galaxies at** z = 4 − 6


Ikki Mitsuhashi, [1][,][ 2] Ken-ichi Tadaki, [3] Ryota Ikeda, [4][,][ 2] Rodrigo Herrera-Camus, [5] Manuel Aravena, [6] Ilse De Looze, [7][,][ 8]
Natascha M. Förster Schreiber, [9] Jorge González-López, [10][,][ 6] Justin Spilker, [11] Roberto J. Assef, [6] Rychard Bouwens, [12]
Loreto Barcos-Munoz, [13][,][ 14] Jack Birkin, [11] Rebecca A. A. Bowler, [15] Gabriela Calistro Rivera, [16] Rebecca Davies, [17][,][ 18]
Elisabete Da Cunha, [18][,][ 19] Tanio Díaz-Santos, [6][,][ 20][,][ 21] Andrea Ferrara, [22] Deanne Fisher, [17] Lilian L. Lee, [9] Juno Li, [18][,][ 19]
Dieter Lutz, [9] Monica Relaño, [23][,][ 24] Thorsten Naab, [25] Marco Palla, [26][,][ 7] Ana Posses, [6] Manuel Solimano, [6] Linda Tacconi, [9]
Hannah Übler, [27][,][ 28] Stefan van der Giessen, [7][,][ 12][,][ 25] and Sylvain Veilleux [29]


_(A_ ffi _liations can be found after the references)_


Received -; accepted 

**ABSTRACT**


We present the morphological parameters and global properties of dust-obscured star formation in typical star-forming galaxies at _z_ = 4–6. Among
26 galaxies composed of 20 galaxies observed by the Cycle-8 ALMA Large Program, CRISTAL, and six galaxies from archival data, we have
individually detected rest-frame 158µm dust continuum emission from 19 galaxies, nine of which are reported for the first time. The derived farinfrared luminosities are in the range log 10 _L_ IR [ _L_ ⊙ ] =10.9–12.4, an order of magnitude lower than previously detected massive dusty star-forming
galaxies (DSFGs). The average relationship between the fraction of dust-obscured star formation ( _f_ obs ) and the stellar mass is consistent with
previous results at _z_ = 4–6 in a mass range of log 10 _M_ ∗ [ _M_ ⊙ ] ∼ 9.5–11.0 and show potential evolution from _z_ = 6–9. The individual _f_ obs exhibits a
significant diversity, and it shows a correlation with the spatial offset between the dust and the UV continuum, suggesting the inhomogeneous dust
reddening may cause the source-to-source scatter in _f_ obs . The effective radii of the dust emission are on average ∼1.5 kpc and are ∼ 2 times more
extended than the rest-frame UV. The infrared surface densities of these galaxies (Σ IR ∼ 2.0 × 10 [10] _L_ ⊙ kpc [−][2] ) are one order of magnitude lower
than those of DSFGs that host compact central starbursts. On the basis of the comparable contribution of dust-obscured and dust-unobscured star
formation along with their similar spatial extent, we suggest that typical star-forming galaxies at _z_ = 4–6 form stars throughout the entirety of their
disks.


**Key words.** galaxies:high-redshift – galaxies: ISM – dust, extinction



**1.** **Introduction**


In recent decades, star formation activity of galaxies at _z_ ≳ 4
has been progressively studied through their rest-frame ultraviolet (UV) emissions (e.g., Steidel et al. 1999; Daddi et al. 2004;
Bouwens et al. 2004b, 2007). Because the rest-frame UV continuum emission traces massive young stars that have a short (∼100
Myr) lifetime, they are used to estimate star formation rates
(SFRs) through the empirical relations (e.g., Kennicutt 1998;
Kennicutt & Evans 2012). The _Hubble_ _Space_ _Telescope_ ( _HST_ )
provides us with high spatial resolution images covering the restframe UV emissions of galaxies at _z_ ≳ 4. The spatial extent
of the star formation is a fundamental parameter for studying
galaxy evolution (e.g., Shen et al. 2003), and has been actively
explored since the advent of the _HST_ (e.g., Lilly et al. 1998;
Bouwens et al. 2004a; Ferguson et al. 2004; Daddi et al. 2005;
Trujillo et al. 2006; Toft et al. 2007). One of the most surprising
results from these studies is that the rest-frame UV effective radii
of galaxies decreases with increasing redshift (e.g., Hathi et al.
2008; Oesch et al. 2010; van der Wel et al. 2014; Shibuya et al.
2016).

The UV emission is highly sensitive to absorption by interstellar dust, and the absorbed energy is re-emitted as thermal dust continuum radiation at far-infrared (FIR) wavelengths.
Therefore, dust continuum emission is an important tracer to
study obscured star formation. In the past decade, Atacama
Large Millimeter/Sub-Millimeter Array (ALMA) observations
have provided valuable insights into the spatially-resolved properties of high-redshift galaxies, helping us to understand the un


derlying physical mechanisms driving their morphological evolution. For instance, submillimeter morphologies of dusty starforming galaxies (DSFGs) have been well-explored thanks to
the high spatial resolution achieved with ALMA (e.g., Ikarashi
et al. 2015; Hodge et al. 2016; Fujimoto et al. 2017; Gullberg
et al. 2019). DSFGs show intense dust-obscured star formation
(Casey et al. 2014,, for review). The observed compact starforming region compared with the stellar distribution (e.g., Chen
et al. 2015; Tadaki et al. 2020a) suggest that they are in process
of the forming bulge (e.g., Simpson et al. 2015; Nelson et al.
2019; Ikeda et al. 2022) or to be progenitor of compact quiescent
galaxies (Toft et al. 2014; Barro et al. 2016). The exploration of
DSFGs at _z_ < 3 is critical as dust obscures the majority of star
formation activity within the redshift range of 1 < _z_ < 3 (Magnelli et al. 2009, 2011; Moutard et al. 2020).
At redshift exceeding _z_  - 3, dust-obscured star formation
may also be significant, (e.g., Rowan-Robinson et al. 2016;
Gruppioni et al. 2020; Algera et al. 2023) although it has remained uncertain despite extensive efforts (e.g., Bouwens et al.
2012; Dudzeviˇci¯ut˙e et al. 2020; Zavala et al. 2021; Casey et al.
2021; Fujimoto et al. 2023). Recent ALMA deep observations
have been used to study the dust-obscured star formation activity of galaxies at _z_ ≳ 4, which are originally selected by their
bright UV emissions (e.g., Watson et al. 2015; Laporte et al.
2017; Fujimoto et al. 2020; Bakx et al. 2021; Laporte et al.
2021; Fudamoto et al. 2021; Schouws et al. 2022). Owing to
negative _K_ -correction and the redshift evolution of the dust temperature ( _T_ dust ) and star formation activities (e.g., Schreiber et al.
2018; Speagle et al. 2014), it is possible to detect dust continuum


Article number, page 1 of 22

_A&A proofs:_ manuscript no. main



emission from galaxies at higher redshift in the frequency coverage of ALMA (see Blain et al. 2002; Casey et al. 2014). The
dust continuum detection of relatively low-mass galaxies such
as _M_ ∗ ∼ 10 [10] _M_ ⊙ have been increased especially at _z_ ≳ 4 (e.g.,
Watson et al. 2015; Laporte et al. 2017; Bowler et al. 2018; Bakx
et al. 2021; Laporte et al. 2021; Fudamoto et al. 2021; Bowler
et al. 2022; Schouws et al. 2022; Inami et al. 2022; Bouwens
et al. 2022; Ferrara et al. 2022; Sommovigo et al. 2022b). Inami
et al. (2022) found that a significant fraction of the star formation
activity in bright Lyman-break galaxies with the stellar mass of
_M_ ∗ ∼ 10 [9][.][5] _M_ ⊙ at _z_ ∼ 7 is obscured by dust (see also Bouwens
et al. 2022; Ferrara et al. 2022; Sommovigo et al. 2022b; Algera et al. 2023), consistent with predictions from cosmological
galaxy simulations (e.g., Cullen et al. 2017).
Since the individual detection of the dust continuum from
_z_ ≳ 4 galaxies, there have been extensive efforts to understand
the role of dust-obscured star formation in the internal structure of UV-bright galaxies. For instance, Bowler et al. (2022)
revealed the spatial correlation between dust continuum detection and redder colors (see also, Bowler et al. 2018). However,
spatially-resolved observations of dust emission from the galaxies with _M_ ∗ ∼ 10 [10] _M_ ⊙ remain challenging even with ALMA
(e.g., Fujimoto et al. 2020; Ginolfi et al. 2020a; Inami et al. 2022;
Hygate et al. 2023) and are still limited (e.g., Herrera-Camus
et al. 2021; Béthermin et al. 2023; Devereaux et al. 2023).
In this paper, we investigate dust-obscured star formation activity and the spatial extent of dust emission in 26 normal, representative star-forming galaxies at _z_ = 4–6 by utilizing data from
the ALMA Large Program, [C ii] Resolved ISM in STar-forming
galaxies with ALMA (CRISTAL) and some archival data. With
the ancillary data set including deep _HST_ images, we examine
distributions of the dust-obscured and unobscured star-forming
regions in the early Universe. The paper is organized as follows:
Section 2 provides an overview of the CRISTAL survey sample
and data products. Section 3 describes the method of size measurements for the ALMA and _HST_ data, and reports the results
of the size measurements and associated physical properties. In
Section 4, we discuss the physical origin of the dust distribution and the morphological evolution of the CRISTAL galaxies.
A summary of this study is presented in Section 5. Throughout this paper, we assume a flat universe with the cosmological
parameters of Ω M = 0.3, Ω Λ = 0.7, σ 8 = 0.8, and _H_ 0 = 70
km s [−][1] Mpc [−][1] .


**2.** **Observation and Data**


_2.1._ _The ALMA CRISTAL survey_


CRISTAL is an ALMA Cycle-8 large program (2021.1.00280.L;
PI: Rodrigo Herrera-Camus, see Herrera-Camus et al. in prep).
CRISTAL aims to spatially resolve the [C ii] line and rest-frame
158µm dust continuum emissions of typical star-forming galaxies at _z_ ∼4–6. The parent sample of CRISTAL is composed of
75 galaxies whose [C ii] emission is detected in the ALPINE survey (ALMA Large Program to Investigate C [+] at Early Times;
2017.1.00428.L; PI: O. Le Fèvre Le Fèvre et al. 2020) with the
spatial resolution of ∼ 1 [′′] . For the CRISTAL program, we selected targets based on spectral energy distribution (SED) modeling with LePhare (Faisst et al. 2020b; Béthermin et al. 2020),
with the following criteria: (1) the specific SFR is within a factor of 3 from the star formation main sequence at each redshift
(Speagle et al. 2014), (2) _HST_ images are available, (3) stellar
mass is larger than log 10 _M_ ∗ [ _M_ ⊙ ] ≥ 9.5. All galaxies are located
in the COSMOS or GOODS-S field and ∼ 80% of the galaxies are covered by the ongoing (or planned) _JWST_ observations
such as the COSMOS-Web treasury program (Casey et al. 2022),
PRIMER program (Dunlop et al. 2021) or some GTO programs
(e.g., ID1286). The mass-selected UV-bright galaxies provide a
census of the gas, dust, and stars of typical star-forming galax

Article number, page 2 of 22



ies on a kiloparsec scale with a combination of high-resolution
ALMA and _HST_ / _JWST_ observations.
In addition, we added six galaxies in the COSMOS field
(HZ4, HZ7, HZ10, DC818760, DC873756, VC8326, see also
Capak et al. 2015; Faisst et al. 2020b; Béthermin et al. 2023;
Devereaux et al. 2023) referred to as the CRISTAL+ galaxies (corresponding to CRISTAL-20, 21, 22, 23, 24, 25, respectively) because they have ALMA data with similar spatial resolution and sensitivity as the CRISTAL (2018.1.01359.S and
2019.1.01075.S; PI: Manuel Aravena, 2018.1.01605.S; PI: Rodrigo Herrera-Camus, 2019.1.00226.S; PI: Edo Ibar). Also, we
exclude one galaxy (CRISTAL-18) because it does not exhibit
clear [C ii] and dust continuum detections possibly due to misestimation of [C ii] frequency. Hence, the CRISTAL extended
sample is composed of 24 target fields with available sensitive
ALMA [C ii] plus dust continuum imaging ≲ 0.3 [′′] . Details of
the survey design and observation setup are presented in HerreraCamus et al. (in prep).


_2.2._ _Properties of the CRISTAL galaxies_


To uniformly estimate galaxy-integrated physical properties of
the CRISTAL galaxies including several serendipitously detected sources in both [C ii] and dust continuum (see Section
3.1), and confirm the robustness of the physical parameter estimations in the individual SED fitting code, we perform multiwavelength SED fitting using the CIGALE code (Boquien et al.
2019).
We cross-match positions of the CRISTAL galaxies to
publicly available photometric catalogs in COSMOS (COSMOS2015 catalog, Laigle et al. 2016) [1] and GOODS-S fields
(ASTRODEEP catalog, Merlin et al. 2021). All of the CRISTAL
galaxies have counterparts within 1 [′′] . The model SEDs are generated with stellar population synthesis models of Bruzual &
Charlot (2003) under a Chabrier (2003) initial mass function
with a range of 0.1–100 _M_ ⊙ assuming exponentially declining
star formation histories (SFHs). We adopt Calzetti et al. (2000)
dust attenuation law and CLOUDY (Ferland et al. 1998) nebular
emission line template. Details of the fitting and parameter range
are summarized in the Appendix.
We derive stellar masses and SFRs averaging the SFH over
the last 100 Myr (SFR SED ) from the best-fit SED models. Figure 1 shows the relation between stellar mass and SFR for the
CRISTAL galaxies. We also perform SED fitting for all galaxies
at _z_ = 4 − 6 in the COSMOS2015 catalog with the exact same
setup as for the CRISTAL galaxies. CRISTAL galaxies have stellar masses of log 10 _M_ ∗ [ _M_ ⊙ ] ≳ 9.5, which are consistent with the
results from LePhare code in the ALPINE program within the
1σ uncertainty. A comparison with the star formation main sequence at _z_ = 5 (Speagle et al. 2014) indicates that CRISTAL
galaxies are a representative population of star-forming galaxies
at this epoch. Note that the estimated parameters of CRISTAL01 might be uncertain due to the contamination of _Spitzer_ band
photometry by a nearby bright source (see Figure 1). The stellar mass estimation will be improved by _JWST_ data in the future (Li et al. in prep) as most of the CRISTAL galaxies have
_JWST_ /NIRCam coverage as described in Section 2.1. We also
note that CRISTAL-24 is located below the main sequence due
to small SFR SED . Since SFR estimated from UV and IR radiation (SFR UV + SFR IR ) is ∼ 1.3 dex higher than SFR SED, SFR SED
derived from optical to NIR photometry appears to be underestimated due to the degeneracy of dust extinction and stellar age
(see Figure B.1). The stellar masses and SFRs for the CRISTAL
galaxies are summarized in Herrera-Camus et al. (in prep).


1 We find there are spatial offsets between the detected position in the
COSMOS2015 catalog and the latest the COSMOS catalog (Weaver
et al. 2022). For our target galaxies, COSMOS2015 catalog shows better
identifications.

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6



**Fig.** **1.** SFR vs stellar mass with _z_ = 5 main-sequence parameterization (Speagle et al. 2014) and comparison _z_ = 4–6 galaxies in the
COSMOS catalog (Laigle et al. 2016). Pink squares are primary targets of the CRISTAL program and blue squares are serendipitously detected galaxies and additional CRISTAL+ galaxies (see Section 2.1).
The sources whose dust continuum is detected with S/N > 4 are marked
with crosses. The CRISTAL galaxies are located within ±0.5 dex of the
star formation main sequence at _z_ = 5, suggesting they are representative populations at this epoch.


_2.3._ _Observation and Data products_


CRISTAL observations cover a wide range of spatial frequencies
in the _uv_ plane with a combination of extended (C43-4/5/6) and
compact (C43-1/2) array configurations to achieve not only highresolution (∼ 0.3 [′′], corresponding to ∼ 1.9 kpc in physical scale
at _z_ = 5) but also a large maximum recoverable scale (∼ 4.5 [′′],
corresponding to ∼ 28.3 kpc in physical scale at _z_ = 5). We determine the spectral frequency coverages by centering [C ii] frequency derived from the integrated [C ii] spectral line profile in
the ALPINE survey. Observations were carried out from November 2021 to April 2023. Details of the calibration, reduction, and
data products will be presented in Herrera-Camus et al. (in prep).
In addition to the CRISTAL observations taken in two array configurations, all CRISTAL galaxies have archival observations (2012.1.00978.S, 2012.1.00523.S, and 2017.1.00428.L).
As these archival data typically cover shorter spatial frequency
ranges in the _uv_ plane compared with the CRISTAL observations, adding these archival data improves the sensitivities, especially to extended emissions. We use the archive data by combining visibilities with the CASA/concat task.


**3.** **Analysis and Results**


_3.1._ _Dust continuum detected galaxies_


In this paper, we focus on the dust continuum emission of
CRISTAL galaxies. We exclude visibility data in the frequency
range corresponding to the [C ii] emission line. To ensure avoiding the contamination of [C ii] lines to the dust continuum,
we exclude ±0.45 GHz, which correspond to ±400 km s [−][1] and
±450 km s [−][1] for _z_ = 4.5 and 5.5 respectively, from the [C ii]
central frequencies since broad component of [C ii] emission
lines could reach ∼ 250 km s [−][1] in FWHM/2 (Ginolfi et al.



2020b). Next, we make multi-frequency synthesis (continuum)
images with CASA task tclean to look at their signal-to-noise
ratio (S/N). Here we did not apply clean algorithm (i.e., dirty
images) and primary beam correction to perform a consistent
comparison between noises and signals (c.f., JvM correction,
Czekala et al. 2021, Gonzalez-Lopez et al. in prep). To avoid
low S/N for extended emission in galaxies and investigate how
well the extended emission of galaxies is recovered, we create
low-resolution images with _uv_ taper of 0.25 [′′], 0.5 [′′], 1.0 [′′], and
2.0 [′′] as well as high-resolution images with natural weighting.
In all images with different resolutions, we pick maximum fluxes
in dust continuum images within a circle of radius 0.5 [′′] around
the position of previous [C ii] detection. The noise is estimated
by calculating 3σ clipped root-mean-square (RMS) values of all
pixels within the Field-of-View (FoV) where the primary beam
correction value is between 0.9 and 0.5 to avoid the impact of
the target galaxy for sure. Typical RMSs are 10–20 µJy beam [−][1] .
In the vicinity of the main targets, we serendipitously found
2 sources with - 8σ [C ii] detection, - 4σ dust continuum
detection, and _HST_ detection (CRISTAL-01b and 07c). We include these galaxies in the main analysis. Please refer to HererraCamus et al. (in prep) for more detail on serendipitous [C ii]
and dust detections around CRISTAL galaxies. In a total of 26
extended CRISTAL samples (18 original CRISTAL targets, 6
CRISTAL+ galaxies, and 2 serendipitously detected galaxies in
original CRISTAL fields), we found that 7, 8, and 11 galaxies
have dust continuum emissions with S/N < 4, 4 ≤ S/N < 6.5,
and S/N ≥ 6.5 respectively.
We show thumbnails of the dust-detected CRISTAL galaxies in Figure 2. The dust-detected galaxies tend to have
higher stellar masses (log 10 _M_ ∗ [ _M_ ⊙ ] ≳ 9.7) and SFRs
(log 10 SFR [ _M_ ⊙ yr [−][1] ] ≳ 1.5). The median stellar mass and SFR
of the dust-detected and undetected sample are log 10 _M_ ∗ [ _M_ ⊙ ] =
10.1, log 10 SFR [ _M_ ⊙ yr [−][1] ] = 1.8 and log 10 _M_ ∗ [ _M_ ⊙ ] = 9.5,
log 10 SFR [ _M_ ⊙ yr [−][1] ] = 1.4, respectively. The detection rate is
89% (16/18) in a stellar mass range of log 10 _M_ ∗ [ _M_ ⊙ ] > 9.7 (Figure 1). Our detections of faint galaxies in the dust continuum
down to the stellar mass of _M_ ∗ ∼ 10 [9][.][5] _M_ ⊙ provide new insight
into the dust-obscured star formation activities of less massive
galaxies.


_3.2._ _Dust size measurement_


In this section, we characterize the spatial extent of the restframe 158µm dust continuum emissions in the CRISTAL galaxies. In principle, it is possible to measure the size of galaxies
by deconvolving an image with a clean beam. However, reconstructed images through the Fourier transform of the visibility
data and non-linear clean algorithm strongly depend on the _uv_
coverage of visibilities and its weight, which could lead to systematic uncertainties. Moreover, as about one-third of CRISTAL
galaxies lack high S/N (S/N ≳ 5) in the dust continuum images, image-based analysis may make measurements uncertain.
To achieve homogenous size measurements and to utilize full
information from the observations, we directly measure the effective radii of dust continuum emission from the visibility data.
Recent high-resolution ALMA observations revealed that
DSFGs are generally consistent with Sérsic profile (Sérsic 1963)
with the index of _n_ ∼ 1 (e.g., Hodge et al. 2016; Gullberg et al.
2019). Even for fainter sources, Tadaki et al. (2020a) suggest that
their surface density profiles are better characterized by an exponential profile with _n_ = 1 than a Gaussian profile with _n_ = 0.5.
Therefore we fit a 2D exponential profile ( _n_ = 1) by using UVMultifit (Martí-Vidal et al. 2014).
The observed visibilities are presented as a combination of
amplitude and phase from all sources within the FoV. Hence, to
extract information specific to the target galaxy, it is necessary
to subtract contributions from other continuum sources within


Article number, page 3 of 22

_A&A proofs:_ manuscript no. main


**Fig. 2.** Thumbnails of the dust detected CRISTAL galaxies. The background images are _HST_ /F160W images. The natural-weighted and naturalweighted+0.5 [′′] -Tapered rest-frame 158 µm dust continuums are also shown in red and blue contours, respectively. An average beam size of
natural-weighted continuum images is 0.46 [′′] = 2.9 kpc. The contour levels are shown every 1σ within 3–9σ and every 2σ from 9σ, respectively.
For CRISTAL-22, for every 2σ from 3σ. The source ID, redshift, S/N, and morphological classification based on the _HST_ images are also shown
in each panel.



the FoV especially when they are close to the target. Sources
more than 2 [′′] apart from the target galaxy are subtracted using
the CASA tclean task. We clean down to 1.5σ by applying 2 [′′]
masks from the source position to extract the clean component of
the nearby sources and subtract them from the observed visibilities with CASA task uvsub. Note that there is no significant difference if we conduct the two-component fitting to take into account the other continuum sources. When we clearly find the existence of a second component in the residual map after subtracting the best-fit single component with S/N > 10 (CRISTAL-22),
we use the results of the two-component fitting. As the CRISTAL
galaxies typically do not have high S/N (S/N - 5) in the dust
emission (Table 1), the axis ratio ( _q_ ) is not well constrained in
most galaxies. Thus, we measure the effective radii of the dust
emission by assuming a circular exponential disk with a fixed
value of _q_ = 0. We create residual maps from the visibilities
where the best-fit model is subtracted in the _uv_ plane.
Figure 3 shows an example of a dirty map, a residual map,
and a real part of the observed visibilities as a function of _uv_ distance. Because there is no peak above ∼ 3σ in the residual maps,
the exponential disk model seems to successfully represent the
spatial distribution of dust emission. Thanks to the observations
in the extended array configurations, we successfully capture a
decline of the real part of the visibilities that clearly suggests the
dust continuum from the source is spatially resolved. A signal at


Article number, page 4 of 22



the real part with increasing _uv_ distance is the reciprocal of the
spatial extent at an image plane since the Fourier transform of
the profile in the image plane is a profile in the visibility plane.
All of the original, model, and residual maps are shown in the
Appendix.
To check the goodness of the visibility fitting, we compare
the flux densities of dust continuum emission estimated from the
visibility fitting and those from the low-resolution image (Figure
4). Here we make the images with a beam size of 3.0 [′′] by applying CASA/imsmooth to the 2.0 [′′] -tapered images to transform the
resolution of each source to a common beam size and to make
sure that all of the flux densities are included within a single
beam. Then we measured source flux densities with the same
method used in Section 3.1. We find the visibility fitting recovers the flux densities well in various sources from the brightest
to the faintest among the CRISTAL galaxies, except for a very
extended source (CRISTAL-21). The inconsistency of flux densities in CRISTAL-21 likely originates from extrapolation of the
best-fit model toward the short _uv_ distance regime due to a low
sensitivity at ≤ 50 kλ. When the additional 2 [′′] -taper is applied to
CRISTAL-21, we find a better match with the visibility-based estimation. To maintain consistency between the detected and undetected galaxies in the dust continuum, hereafter we use the flux
densities and 1σ uncertainties estimated from the low-resolution
(i.e., tapered) images.

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


**Fig. 3.** An example of the fitting in the visibility plane. **left:** The observed and residual (observed - best-fit model) dirty map of the dust continuum
emission. The synthesized beam is shown in the bottom left. The black contour shows every 1σ from ±3σ. **right:** The real part of the observed
visibilities as a function of _uv_ distances with different binning scales. The best-fit exponential disk model and its 1σ uncertainty are shown in a red
solid line and shaded area respectively.



**Fig. 4.** Comparison of the flux density estimated from UVMultifit and
Taper images, color-coded by the source S/N. The black solid line and
dashed lines indicate a one-to-one relation and ±0.3 dex. We see the
visibility fitting recovered the fluxes of the sources in lower resolution
images well within the 1-σ errors, except for CRISTAL-21 (see text).


We summarize the fluxes measured in visibilities via UVMultifit and low-resolution images in Table 1. Since about half
of the CRISTAL galaxies range 4.4 < S/N < 5.5 in the dust
continuum images (see Table 1), we conduct a Monte Carlo simulation and a stacking analysis to confirm the validity of the size
measurement in Appendix. We do not find any systematic offset
regardless of the source S/N in the Monte Carlo simulation and
there is no clear difference between the stacked size and the average of the individual sizes in the stacking analysis. Therefore
we conclude that the fitting results are reliable.


_3.3._ _FIR luminosity_


Because most of the CRISTAL galaxies have only single band
ALMA detections in the dust continuum, it is not possible to
estimate properties such as dust temperature ( _T_ dust ) and emis


sivity (β dust ), which are crucial in determining the shape of the
FIR SED. Béthermin et al. (2017) presented best-fit Draine &
Li (2007) dust emission model for stacked fluxes of the mainsequence galaxies at _z_ ∼ 4 with _Spitzer_, _Herschel_, LABOCA,
and AzTEC data (see also Béthermin et al. 2015). This bestfit FIR SED agrees with the stacked fluxes of _z_ = 4–6 mainsequence galaxies with SFR SED - 10 _M_ ⊙ yr [−][1] (Béthermin et al.
2020), corresponding to the modified blackbody with the dust
temperature _T_ dust ∼ 42 K. Indeed, some CRISTAL galaxies have
rest-frame 110 and 200 µm observations and show a consistent
_T_ dust estimation with the assumption of _T_ dust ∼ 42 K (Faisst
et al. 2020a), while there exists a variation in the FIR SED with
the range of dust temperatures of _T_ _d_ ∼ 30–60 K. Sommovigo
et al. (2022a) apply the physically-motivated model to characterize _T_ dust validated in Sommovigo et al. (2021) for the _z_ ∼ 5
galaxies that is partly overlapping with the CRISTAL galaxies.
The derived average _T_ dust is 48 ± 8 K, and is broadly consistent with the assumption of 42 K. Because our CRISTAL galaxies share similar SFRs with the galaxies studied in Béthermin
et al. (2020), we use the best-fit FIR SED presented in Béthermin et al. (2017) to estimate the total IR (8–1000 µm) luminosities of the CRISTAL galaxies. We calculate the total FIR luminosities of the CRISTAL galaxies by converting the measured
dust continuum fluxes at the rest-frame 158 µm using a scaling
factor described Béthermin et al. (2020, ν _L_ ν=158µm / _L_ IR = 0.133).
The resulting _L_ IR of CRISTAL galaxies fall within a range of
log 10 _L_ IR [ _L_ ⊙ ] = 10.9–12.4.


Figure 5 shows the total infrared luminosity against the circularized effective radius (left) or the surface infrared luminosity
≡comparison, we show the results of diΣ IR = _L_ IR /2π _r_ _e_ [2],dust [(right)] [of] [dust] ff [continuum] erent galaxy populations, [emission.] [As] [a]
namely sub-millimeter galaxies (SMGs) at _z_ ∼ 2.5 (Gullberg
et al. 2019), lensed SMGs at _z_ ∼ 3–6 (Spilker et al. 2016), DSFGs at _z_ = 4–6 (Riechers et al. 2014; De Breuck et al. 2014;
Hodge et al. 2015; Gómez-Guijarro et al. 2018; Casey et al.
2019; Tadaki et al. 2020b) and DSFGs at _z_ ∼ 2 (Tadaki et al.
2020a). The comparison galaxies are mainly starburst galaxies
above the main sequence at the corresponding epochs, and their
FIR luminosities are derived by some templates of FIR SEDs
(e.g., Wuyts et al. 2008; da Cunha et al. 2015) or modified blackbody fitting with the typical dust temperature _T_ dust = 30–50 K.
Solid and dashed lines indicate a series of _r_ _e_ and _L_ IR each cor

Article number, page 5 of 22

_A&A proofs:_ manuscript no. main



responding to the median infrared surface densities (Σ IR ) of the
respective sample, as indicated by the matching color.
The median values of Σ IR are 2.0 × 10 [12] _L_ ⊙ kpc [−][2] for lensed
SMGs, 9.8 × 10 [11] _L_ ⊙ kpc [−][2] for SMGs at _z_ ∼ 2.5, 1.6 ×
10 [12] _L_ ⊙ kpc [−][2] for SMGs at _z_ = 4–6, and 1.6 × 10 [11] _L_ ⊙ kpc [−][2]
for DSFGs at _z_ = 2. The median Σ IR of the CRISTAL galaxies is 2.0 × 10 [10] _L_ ⊙ kpc [−][2] and ∼10 times smaller than that of the
central compact star-forming regions of DSFGs or SMGs (Figure 5 right), and similar to that of the extended dust continuum
component of the SMGs reported in the stacked spatial distribution (Gullberg et al. 2019, Σ IR ∼ 5 × 10 [10] _L_ ⊙ kpc [−][2] ) that is
considered to be disk components. Our representative population of galaxies at _z_ ∼4–6 seems to undergo moderate star formation with a lower Σ IR than those of DSFGs, except for some
galaxies (CRISTAL-22 and 24) showing the high Σ IR those are
comparable with DSFGs and SMGs. Interestingly, Ferrara et al.
(2022) analytically derive the _L_ IR and dust distribution radius
of the REBELS (Reionization Era Bright Emission Line Survey; Bouwens et al. 2022) galaxies at _z_ ∼ 7. They find a more
compact distribution ( _r_ _d_ ∼ 0.3 kpc) and a similar _L_ IR with the
CRISTAL galaxies (log 10 _L_ IR [ _L_ ⊙ ] ∼ 11.8), which results in a
higher Σ IR (log 10 Σ IR [ _L_ ⊙ kpc [−][2] ] ∼ 12.1) than our measurements.
Direct measurement of the dust continuum distribution by the
future ALMA high-resolution observations for _z_ - 6 galaxies
will enable us to compare our results with that of the galaxies at
_z_ - 6.


_3.4._ _Rest-frame UV size measurement_


To compare the spatial extent of the dust-obscured and unobscured star formation, we measure the rest-frame UV sizes of the
CRISTAL galaxies. In this section, we summarize the size measurements of the rest-frame UV emission observed with _HST_ .
Because all of the CRISTAL galaxies have WFC3/F160W
coverage and 1.6 µm corresponds to rest-frame ∼2400–3000 Å
in the redshifts of the CRISTAL galaxies ( _z_ = 4.4–5.7), we constantly use images from WFC3/F160W observation to measure
the rest-frame UV sizes of the CRISTAL galaxies.
We measure the _HST_ size based on two-dimensional (2D)
surface-brightness profile fitting with GALFIT (Peng et al.
2002). First, we make a point-spread function (PSF) in the same
manner as previous studies (e.g., Skelton et al. 2014). We selected point sources (i.e., stars) based on the following criteria:
(1) ratios of fluxes with 2.0 [′′] apertures and 0.5 [′′] apertures are
in a range of 1.2 and 1.4 based on the tight flux correlation in
the point source. (2) S/Ns are greater than 7500. We exclude the
point sources if they have nearby sources within 3 [′′] . Because the
central position of the point source does not necessarily correspond to the central position of the pixel, we reproject the 2D
point source profile with a linear interpolation to the central position derived from 2D Gaussian fitting. Then we obtain the PSF
by stacking these reprojected stellar profiles after normalizing
with the total flux of each source. We also create _sigma_ and _mask_
images to estimate the weight of individual pixels and exclude
neighboring objects of the target galaxy from the fittings. The
_sigma_ images are made from drizzle weight maps and _mask_ images are produced from segmentation maps from SExtractor
with a parameters of detect_minarea=5, detect_thresh=2, detect_nthresh=16 and deblend_mincont=0.0001. We input the
_sigma_, _mask_, and PSF to GALFIT and fit a single Sérsic profile
to the 2D surface-brightness profile of each galaxy. Here we fix
_n_ = 1 to perform fair comparisons with the dust size measurement. Note that there is no systematic difference if we do not fix
the Sérsic index except for CRISTAL-25, showing a large Sérsic
index in the best-fit model (see Figure D.1). Finally we obtain an
effective radius along the major axis _r_ _e_ [major],UV [and axis ratio] _[ q]_ [, and]
convert them to the circularized effective radius _r_ _e_,UV through


Article number, page 6 of 22



_r_ ratio as a free parameter, we fix the axis ratio to unity as in the _e_,UV ≡ _r_ _e_ [major],UV √ _q_ . If the fitting does not converge with the axis
size measurement in the dust continuum. The original, model,
and residual maps are shown in Appendix. For CRISTAL-22,
we only measure the size of the main component by masking the
second component because the latter is too faint and the fitting
does not converge (see Figure 2).
In Figure 6, we compare measured sizes of the dust-obscured
star formation derived from rest-frame 158 µm dust continuum
observations by ALMA and the dust-unobscured star formation derived from rest-frame UV continuum observations by
_HST_ /WFC3 F160W. The dust-obscured star formation appears
to be on average ∼ 2 times more spatially extended than the
dust-unobscured star formation. We discuss the spatial extent of
the dust and UV emissions in Sec 4.3.1.
The measured dust and rest-frame UV sizes are summarized
in Table 1.


**4.** **Discussion**


_4.1._ _Fraction of obscured star formation_


The obscured fraction of star formation ( _f_ obs ) is defined by the
ratio of the dust-obscured star formation detected in rest-frame
IR continuum emission to the total star formation rates accounting for dust-unobscured star formation observable in rest-frame
UV continuum emission as following:


SFR IR
_f_ obs = (1)
SFR UV + SFR IR


In general, the obscured fractions show a positive correlation
with the stellar masses of the galaxies (e.g., Whitaker et al. 2017;
Reddy et al. 2018) as well as some studies presenting the same
trend in IR excess (IRX; log 10 _L_ IR / _L_ UV ), which is a similar quantity with _f_ obs as an indicator of the obscured star formation (e.g.,
Pannella et al. 2009, 2015; Bouwens et al. 2016; Dunlop et al.
2017; McLure et al. 2018; Bouwens et al. 2020). Based on the
results in Whitaker et al. (2017), the obscured fractions do not
exhibit any clear evolution from _z_ ∼ 2.5 to _z_ ∼ 0 in the average
obscured fraction of _f_ obs = 0.8 (for Dale & Helou 2002 template)
or 0.6 (for Magdis et al. 2012 and Béthermin et al. 2015 template). Recent ALMA studies suggest a possible decrease in the
mass dependence of _f_ obs at a high mass range ( _M_ ∗ ≳ 10 [10] _M_ ⊙ ) at
_z_ - 4 (Fudamoto et al. 2020b,a; Inami et al. 2022; Algera et al.
2023).
In order to confirm if similar trends can be observed in our
data, we calculate the average obscured fraction of the sample
binned by their stellar masses. We divide the sample into three
ranges with log 10 _M_ ∗ [ _M_ ⊙ ] = [9.3 : 9.8], [9.8: 10.2] and [10.2:
10.9] so that the number of galaxies in each bin is similar. For
the stacking analysis, we make the images with the taper scale of
2 [′′] after shifting the phase center of the image to the central position of the [C ii] emission (Ikeda et al. in prep.). Then we apply
the CASA/imsmooth to unify the beam size to 3 [′′] following the
flux measurements in Section 3.2 and perform median stacking
of the images. We take into account the redshift difference of the
target galaxies by multiplying the factor of (1 + _z_ )/ _d_ _L_ [2] [to the im-]
age because our calculation from _S_ 158µm to _L_ IR is proportional to
the reciprocal of the factor. Note that the offset between the dust
continuum and [C ii] emission does not impact the result because the typical offset (∼ 0.2 [′′] ) is much smaller than 3 [′′] beam
size. We confirm that the results do not change significantly if we
adopt the inverse _L_ UV weight following Fudamoto et al. (2020a).
The infrared luminosity is derived from a peak flux of the dust
continuum as in section 3. We calculate the median _L_ UV of the
galaxies obtained from the best-fit SEDs in each bin. Then we
convert them into SFR UV or SFR IR following Madau & Dickinson (2014). Figure 7 (left) illustrates the average _f_ obs in each

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


**Fig.** **5.** Total infrared luminosities and **(left)** effective radii and **(right)** surface infrared lumnosities for CRISTAL galaxies, SMGs at _z_ ∼ 2.5
(Gullberg et al. 2019), lensed SMGs at _z_ ∼ 3–6 (Spilker et al. 2016), SMGs at _z_ = 4–6 (Riechers et al. 2014; De Breuck et al. 2014; Hodge
et al. 2015; Gómez-Guijarro et al. 2018; Casey et al. 2019; Tadaki et al. 2020b) and DSFGs at _z_ ∼ 2 (Tadaki et al. 2020a). Solid and dashed lines
show the median Σ IR for each sample. CRISTAL galaxies show ∼10 times smaller Σ IR than that of DSFGs or SMGs, and are less extreme galaxies
compared with DSFGs.


a bright UV continuum and emission lines, it likely led to missing obscured dusty galaxies (e.g., Franco et al. 2018; Yamaguchi
et al. 2019). We find our results have a very good agreement
with the results at _z_ = 4.5 and _z_ = 5.5 from the ALPINE survey
(Fudamoto et al. 2020a), and _z_ = 6–9 from the REBELS survey (Algera et al. 2023). Compared with the another results at
_z_ = 6.5–7.7 from the REBELS survey (Bowler et al. 2023), our
results are indicate slightly lower _f_ obs at _M_ ∗ < 10 [10] _M_ ⊙ . Bowler
et al. (2023) discussed that the the effect of scatter in the obscuration or the clumpy morphology of their target galaxies may
cause such a difference.
Figure 7 (right) shows the obscured fraction of the individual
galaxies as a function of the stellar mass. The CRISTAL galaxies
show a large diversity of _f_ obs = 0.2–0.9. Since we utilized the
same scaling factor as Fudamoto et al. (2020a) to convert _S_ 158µm
into _L_ IR (Béthermin et al. 2020), lower values of _f_ obs suggest
smaller _S_ 158µm . Some CRISTAL galaxies show smaller _f_ obs than
galaxies individually detected in Fudamoto et al. (2020a), with
a median _f_ obs in Fudamoto et al. (2020a) of 0.70 compared to
0.61 in our work, respectively. The smaller values of _f_ obs are
consistent with those stacking analyses (Fudamoto et al. 2020a;
Algera et al. 2023). By utilizing the coverage of the wide range
_f_ obs, we discuss the variation of _f_ obs in the next section.



**Fig. 6.** Size comparison of the dust continuum ( _r_ _e_,dust ) and the UV continuum ( _r_ _e_,UV ). The black solid and dashed lines indicate the size ratios
of the UV and dust continuum. An average size ratio of the CRISTAL
galaxies ( _r_ _e_,dust / _r_ _e_,UV ∼ 1.8) are shown in the red solid line. The green
shaded region shows the size ratio predicted in illustrious TNG50 simulation (Popping et al. 2022). Overall, CRISTAL galaxies possibly have
a more extended distribution in dust thermal emission than in UV radiation, and it is contrary to the expectation from the simulation.


stellar mass bin ( _f_ obs - _M_ ∗ ). Our results support that the obscured
fraction at the range of _M_ ∗ < 10 [10] _M_ ⊙ does not show clear evolution from _z_ = 0–2.5 (Magdis et al. (2012) and Béthermin et al.
(2015)) to _z_ ∼ 5. On the other hand, we find the possible evolution of the obscured fraction from _z_ ∼ 5 to _z_ ∼ 0–2.5 at the range
of _M_ ∗ - 10 [10] _M_ ⊙, and that implies a build-up of dust in massive
galaxies. Note that as our sample selection is originally based on



_4.2._ _Origin of the spread in_ _f_ obs _-_ _M_ ∗ _plane_


In Figure 7 (right), we found a large spread in the _f_ obs - _M_ ∗ relation across galaxies in our sample. As more than 30% of the
galaxies deviate from the average relationship derived from the
stacking analysis, even when considering 1σ errors, the variance
is not likely to come from the measurement errors. Such a variation has been reported in ALMA observations toward UV-bright
galaxies at _z_ - 4 (Fudamoto et al. 2020a; Inami et al. 2022).
They investigated the relationship between UV continuum slope
(β UV ) and IRX. Previous studies predict that the scatter could be
caused by dust grain type (e.g., Ferrara et al. 2017), dust geometry (e.g., Witt & Gordon 2000), stellar populations (e.g., Popping et al. 2017a), stellar or dust assembly (e.g., Popping et al.
2017b), spatial decoupling of UV and IR emission due to galactic interaction or dust-enshrouded nuclear starbursts (e.g., Howell et al. 2010), and inclination (e.g., Wang et al. 2018). As it is


Article number, page 7 of 22

_A&A proofs:_ manuscript no. main


**Table 1.** Dust continuum properties of the CRISTAL galaxies


ID log 10 _M_ ∗ S/N _S_ uv _[a]_ _S_ tap _[b]_ log 10 _L_ IR _f_ obs _r_ _e_,dust _r_ _e_,UV _[c]_ class _[d]_

[ _M_ ⊙ ] [mJy] [mJy] [ _L_ ⊙ ] [arcsec] [arcsec]

**CRISTAL main sample**
CRISTAL-01a 10.65 ± 0.50 - - ≤ 0.251 ≤ 11.54 ≤ 0.426 - 0.154 ± 0.007 multiple
CRISTAL-02 10.30 ± 0.28 9.3 0.405 ± 0.075 0.362 ± 0.055 11.80 [+] − [0] 0 [.] . [06] 07 [0][.][629] − [+][0] 0 [.] . [105] 122 [0][.][326][ ±][ 0][.][076] - _[e]_ multiple
CRISTAL-03 10.40 ± 0.29 4.8 0.044 ± 0.014 0.037 ± 0.016 10.86 [+] − [0] 0 [.] . [16] 25 [0][.][210] − [+][0] 0. [.] 122 [077] ≤ 0.369 _[f]_ 0.173 ± 0.007 single
CRISTAL-04a 10.15 ± 0.29 7.6 0.174 ± 0.043 0.164 ± 0.035 11.36 − [+] 0 [0] . [.] 10 [08] [0][.][587] − [+][0] 0 [.] . [130] 162 [0][.][130][ ±][ 0][.][072] [0][.][154][ ±][ 0][.][007] [multiple]
CRISTAL-05 10.16 ± 0.35 6.7 0.141 ± 0.044 0.122 ± 0.026 11.36 − [+] 0 [0] . [.] 11 [08] [0][.][574] − [+][0] 0 [.] . [129] 161 [0][.][244][ ±][ 0][.][105] [0][.][061][ ±][ 0][.][003] single
CRISTAL-06a 10.09 ± 0.30 13.1 0.280 ± 0.051 0.254 ± 0.029 11.55 − [+] 0 [0] . [.] 05 [05] [0][.][794] − [+][0] 0. [.] 122 [109] [0][.][310][ ±][ 0][.][071] [0][.][214][ ±][ 0][.][010] [multiple]
CRISTAL-07ab 10.00 ± 0.33 4.5 0.078 ± 0.037 0.085 ± 0.019 11.16 − [+] 0 [0] . [.] 11 [09] [0][.][331] − [+][0] 0 [.] . [071] 089 [0][.][201][ ±][ 0][.][153] [0][.][146][ ±][ 0][.][008] [multiple]
CRISTAL-08 9.85 ± 0.36 - - ≤ 0.073 ≤ 10.99 ≤ 0.363 - 0.380 ± 0.012 single
CRISTAL-09 9.84 ± 0.39 4.5 0.083 ± 0.032 0.080 ± 0.036 11.18 − [+] 0 [0] . [.] 26 [16] [0][.][463] − [+][0] 0. [.][189] 302 [0][.][104][ ±][ 0][.][079] [0][.][028][ ±][ 0][.][002] single
CRISTAL-10 9.99 ± 0.31 4.4 0.122 ± 0.058 0.101 ± 0.026 11.29 − [+] 0 [0] . [.] 13 [1] [0][.][333] − [+][0] 0 [.] . [08] 104 [0][.][405][ ±][ 0][.][226] - _[e]_ multiple
CRISTAL-11a 9.68 ± 0.33 4.6 0.137 ± 0.055 0.095 ± 0.051 11.11 [+] − [0] 0 [.] . [19] 33 [0][.][542] − [+][0] 0 [.] . [265] 475 [0][.][116][ ±][ 0][.][091] [0][.][066][ ±][ 0][.][004] single
CRISTAL-12 9.30 ± 0.47 - - ≤ 0.029 ≤ 10.73 ≤ 0.535 - - _[g]_ single
CRISTAL-13 9.65 ± 0.34 6.6 0.137 ± 0.039 0.120 ± 0.037 11.23 − [+] 0 [0] . [.] 16 [12] [0][.][621] − [+][0] 0 [.] . [196] 268 [0][.][092][ ±][ 0][.][070] [0][.][056][ ±][ 0][.][023] [multiple]
CRISTAL-14 9.53 ± 0.38 - - ≤ 0.044 ≤ 10.77 ≤ 0.364 - 0.054 ± 0.011 single
CRISTAL-15 9.69 ± 0.33 - - ≤ 0.046 ≤ 10.81 ≤ 0.275 - - _[e]_ single
CRISTAL-16 9.60 ± 0.39 - - ≤ 0.037 ≤ 10.85 ≤ 0.386 - 0.250 ± 0.020 single
CRISTAL-17 9.51 ± 0.40 - - ≤ 0.035 ≤ 10.83 ≤ 0.362 - - _[g]_ single
CRISTAL-19 9.51 ± 0.36 5.5 0.093 ± 0.038 0.078 ± 0.022 11.13 − [+] 0 [0] . [.] 15 [11] [0][.][572] − [+][0] 0. [.][165] 220 [0][.][262][ ±][ 0][.][153] [0][.][097][ ±][ 0][.][009] single
**CRISTAL** + **sample**
CRISTAL-20 10.11 ± 0.35 13.8 0.157 ± 0.025 0.144 ± 0.015 11.43 [+] − [0] 0 [.] . [04] 05 [0][.][459] − [+][0] 0 [.] . [049] 055 [0][.][251][ ±][ 0][.][054] [0][.][060][ ±][ 0][.][002] single
CRISTAL-21 10.11 ± 0.32 4.9 0.528 ± 0.219 0.201 ± 0.046 11.54 − [+] 0 [0] . [.] 11 [09] [0][.][613] − [+][0] 0 [.] . [148] 187 [1][.][160][ ±][ 0][.][499] [0][.][062][ ±][ 0][.][003] single
CRISTAL-22ab _[h]_ 10.35 ± 0.37 22.9 1.522 ± 0.074 1.343 ± 0.158 12.42 − [+] 0 [0] . [.] 05 [05] [0][.][927] − [+][0] 0 [.] . [140] 158 [0][.][150][ ±][ 0][.][011] [0][.][129][ ±][ 0][.][008] [multiple]
CRISTAL-23a 10.55 ± 0.29 12.2 1.142 ± 0.211 0.831 ± 0.087 12.07 − [+] 0 [0] . [.] 05 [04] [0][.][847] − [+][0] 0. [.][111] 123 [0][.][486][ ±][ 0][.][093] [0][.][091][ ±][ 0][.][006] [multiple]
CRISTAL-24 10.53 ± 0.08 22.3 1.201 ± 0.100 1.236 ± 0.092 12.24 − [+] 0 [0] . [.] 03 [03] [0][.][956] − [+][0] 0 [.] . [094] 102 [0][.][204][ ±][ 0][.][028] [0][.][105][ ±][ 0][.][020] single
CRISTAL-25 10.90 ± 0.32 7.8 0.501 ± 0.137 0.402 ± 0.065 11.75 − [+] 0 [0] . [.] 08 [06] [0][.][681] − [+][0] 0 [.] . [123] 145 [0][.][320][ ±][ 0][.][116] [0][.][131][ ±][ 0][.][004] single
**serendipitously detected sources**
CRISTAL-01b 9.81 ± 0.34 4.4 0.449 ± 0.165 0.340 ± 0.066 11.67 [+] − [0] 0 [.] . [08] 09 [0][.][715] − [+][0] 0 [.] . [156] 190 [0][.][331][ ±][ 0][.][153] [0][.][095][ ±][ 0][.][005] [multiple]
CRISTAL-07c 10.21 ± 0.35 7.0 0.160 ± 0.045 0.123 ± 0.024 11.32 − [+] 0 [0] . [.] 09 [08] [0][.][683] − [+][0] 0 [.] . [148] 181 [0][.][139][ ±][ 0][.][077] [0][.][143][ ±][ 0][.][015] single


**Notes.** [(] _[a]_ [)] rest frame 158µm fluxes measured with UVMultifit. [(] _[b]_ [)] rest frame 158µm fluxes measured with tapered images (see Section 3.2).
4-σ upper limits are shown if source S/N < 4. [(] _[c]_ [)] circularized _HST_ /F160W size with fixing sèrsic index to unity. [(] _[d]_ [)] classification based on the
_HST_ /F160W image. [(] _[e]_ [)] galfit does not converge due to the existence of multiple sources having similar brightness. [(] _[f]_ [)] 1-σ upper limit of the size.
( _g_ ) no clear counterpart or low S/N in _HST_ /F160W image. ( _h_ ) _S_ uv indicate total flux of main+sub components, and _r_ _e_,dust / _r_ _e_,UV are the effective
radius of the main component (See Figure 2).



difficult to demonstrate the dependence of dust/stellar properties
such as grain type, geometry, or assembly based on our ALMA
observations, we discuss the potential correlation between _f_ obs
and morphology. We note that no correlation is identified between _f_ obs and the stellar ages derived from SED fitting obtained
in Section 2.2.


4.2.1. inhomogeneous dust reddening


The first possible explanation for the variation in the obscured
fraction is inhomogeneous dust reddening, such as a global spatial offset between dust-enshrouded and dust-free star-forming
regions. Recently, Bowler et al. (2022) discussed the impact
of the spatial distribution of rest-UV and IR emission on the
UV-IR energy balance at _z_ ∼ 7 (see also Inami et al. 2022).
They found a correlation between a redder UV slope and a peak
of FIR emission detected in ALMA and suggest that inhomogeneous dust reddening might be responsible for variations in


Article number, page 8 of 22



the spatially-integrated IRX-β UV relation (see also, Vallini et al.
2015; Behrens et al. 2018).
In Figure 8, we show the distance from our best-fit _f_ obs   - _M_ ∗
relation (∆ _f_ obs ) as a function of the spatial offset of the central
position between the UV and dust continuum. We find a negative
correlation between ∆ _f_ obs and the spatial offset within 1σ uncertainty of the correlation coefficient of ρ corr = −0.58 [+] − [0] 0 [.] . [30] 20 [with] [a]
_p_ -value of 0.082. This correlation suggests that the decoupling
of UV and IR emissions contributes to the escape of UV photons
from interstellar space, and makes the variation on the obscured
fraction.
What causes the spatial offset between UV- and IR-bright
star-forming regions? Numerical simulations incorporating radiative transfer suggest that galactic interaction or feedback are
possible mechanisms to decouple UV- and IR-bright regions
(e.g., Yajima et al. 2011; Safarzadeh et al. 2017; Arata et al.
2019; Liang et al. 2021). For the feedback case, it is expected that
galaxies with higher sSFR will tend to show larger peak offsets
because star formation-driven outflows are more prevalent (e.g.,

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


**Fig.** **7.** **(left)** The relationship between the obscured fraction and the stellar mass from stacking analysis. Black solid and dashed lines show the
results from Whitaker et al. (2017) with two different dust emission templates of Dale & Helou (2002) template (D02) and Magdis et al. (2012)
and Béthermin et al. (2015) template (M12, B15). The obscured fraction increases as a function of the stellar mass, and the trend has a good
agreement with the results at _z_ ∼ 5 from the ALPINE survey (Fudamoto et al. 2020a) and those at _z_ ∼ 6–9 from the REBELS survey (Algera
et al. 2023), while another result at _z_ ∼ 6.5–7.7 from the REBELS survey (Bowler et al. 2023) show an opposite trend with slightly higher _f_ obs at
_M_ ∗ < 10 [10] _M_ ⊙ . **(right)** The obscured fraction of the individual galaxies as a function of the stellar masses. The diamonds and squares correspond
to the two classifications of single and multiple. We also show the results of the galaxies detected in the dust continuum at _z_ ∼ 5 (Fudamoto
et al. 2020a). Our observations capture the galaxies with smaller _f_ obs compared with previous _z_ ∼ 5 galaxies individually detected thanks to deep
observations. There is a significant variation in _f_ obs - _M_ ∗ relation from galaxy to galaxy.



Fujimoto et al. 2020; Faisst et al. 2020b). We divide the sample into two groups within sSFR < 4 Gyr [−][1] and sSFR > 4 Gyr [−][1]
based on the total (IR+UV) SFR and compare the peak offset between UV and IR. There is no clear difference in the peak offset
between the two groups, 0.150 ± 0.046 [′′] for the galaxies within
sSFR < 4 Gyr [−][1] and 0.150 ± 0.038 [′′] for sSFR > 4 Gyr [−][1] .
For the merger case, we expect a larger spatial offset in the
“multiple” sample than the “single” sample because the galaxies classified as “multiple” correspond to a kind of early-stage
merger. However, the peak offset between UV and IR does not
exhibit a systematic offset between “multiple” (0.145 ± 0.048 [′′] )
and “single” (0.155 ± 0.041 [′′] ). Therefore the interaction is not
likely to primary cause of the decoupling. While the merger activity does not generate the decoupling of the dust-obscured and
unobscured star-forming regions, it may accelerate the obscured
star formation. In Figure 7, we plot our result separately for single (isolated) and multiple (merging) galaxies. Most highly obscured galaxies tend to have high total SFRs and show merging signatures in _HST_ images. Also, The average obscured fraction and SFR of the multiple galaxy sample (⟨ _f_ obs ⟩ multiple =
0.43 [+] − [0] 0 [.] . [03] 03 [,] [⟨] [log] [10] [SFR [] _[M]_ [⊙] [yr] [−][1] []][⟩] [multiple] [=] [1][.][97] [+] − [0] 0 [.] . [60] 54 [)] [is] [higher]
than that of the single galaxy samples (⟨ _f_ obs ⟩ single = 0.34 [+] − [0] 0 [.] . [03] 03 [,]
⟨ log 10 SFR [ _M_ ⊙ yr [−][1] ]⟩ single = 1.58 [+] − [0] 0 [.] . [10] 11 [). Our results suggest that]
galaxy interactions may boost not only the star formation activities but also the obscured fraction within almost the same stellar
mass range, and the mixture of the different merger stages and
isolated disks leads to the variety in _f_ obs - _M_ ∗ plane.
Another potential physical reason for the displacement is a
multiphase structure of the ISM, for which one-zone ISM models assumed in the IRX-β (or _f_ obs - _M_ ∗ ) relation cannot be applied. As discussed in Ferrara et al. (2022), _molecular_ _index_



_I_ m (= _F_ 158 / _F_ 1500 /(β − β int )) might represent a good indicator
of such a multi-phase ISM structure. We test the hypothesis by
comparing the UV-dust spatial offset and _I_ m under the assumption of β int = −2.41 following Inami et al. (2022), but we do
not find a clear correlation between them (ρ corr = −0.218 − [+] 0 [0] . [.] 234 [262]
with a _p_ -value of 0.401). This result is mainly due to the small
measured values of the UV-dust offset compared to Inami et al.
(2022). Interestingly, though, CRISTAL-24 shows a very high
_I_ m of ∼ 5000 with a relatively blue UV slope β = −1.55. An inconsistent SFR SED and SFR UV+IR in CRISTAL-24 described in
Section 2.2 may indicate multi-phase and component nature of
the CRISTAL-24.


4.2.2. concentration of the star-forming regions


Since we do not find clear dependence on the potential interactions or UV-dust offsets, we will now compare _f_ obs with the
compactness of the star-forming regions. Whitaker et al. (2017)
indicate that the spatial extent of the star-forming region affects
the obscured fraction (see also, Smail et al. 2021). Howell et al.
(2010) mention that dust-enshrouded central starburst may lead
to a diversity of the obscured fraction. We derive the compactness of the dust-obscured star-forming region as Σ IR computed
from infrared luminosities and effective radii of the dust continuum. We also check the dependence of ∆ _f_ obs on the size ratiotherebetweenis no clearUV andcorrelationdust emissionbetween( _r_ _e_, ∆ dust _f_ obs / _r_ _e_ and,UV ).theWesizefindratiothat
(ρ corr −0.11 − [+] 0 [0] . [.] 27 [28] [with a] _[ p]_ [-value of 0.693 respectively) but][ Σ] [IR] [ has]
potential correlation with _f_ obs (ρ corr = 0.30 − [+] 0 [0] . [.] 26 [22] [with a] _[ p]_ [-value of]
0.245). Enhancement of the dust-obscured star formation activity could relate to the concentration of the young, active dust

Article number, page 9 of 22

_A&A proofs:_ manuscript no. main



enshrouded star formation regions, which may be accelerated by
unstable disks with high gas mass fraction (Dekel et al. 2009;
Tacconi et al. 2013; Scoville et al. 2017; Dessauges-Zavadsky
et al. 2020). Since starbursts induced by the galaxy interaction
could concentrate the gas and dust into the central parts of galaxies (e.g., Barnes & Hernquist 1996), it may accelerate the dust
obscuration of the galaxy and could explain the positive trend
between the obscured fraction and Σ IR or merging signatures.


4.2.3. inclination


Both observations (e.g., Leslie et al. 2018) and simulations (e.g.,
Jonsson et al. 2010) studies suggest that an apparent UV-IR energy balance can be affected by a viewing angle of disk galaxies i.e., inclination. There is a systematic offset of ∼ 0.5 dex in
IRX values between edge-on and face-on galaxies (Wang et al.
2018). While the inclinations are calculated from the axis ratios,
the axis ratios of the UV continua may not be a proper indicator of an inclination due to severe dust attenuation. We do not
find a correlation between the axis ratio of the UV continuum
and ∆ _f_ obs (ρ corr = −0.09 [+] − [0] 0 [.] . [28] 27 [with] [a] _[p]_ [-value] [of] [0.761).] [More-]
over, only a few CRISTAL galaxies have constraints on the axis
ratios in dust emission. The current data quality is not sufficient
to discuss the possibility that inclinations explain the variation in
_f_ obs . It is worth noting that two galaxies with relatively large _f_ obs
(> 0.7) have axis ratios of ∼ 0.2 − 0.3 in the dust emission, suggesting that an edge-on view of disk galaxies may make the obscured fraction higher. Also, note that the axis ratio of [Cii] emission also possibly correlates with ∆ _f_ obs with ρ corr = −0.35 − [+] 0 [0] . [.] 22 [27]
and a _p_ -value of 0.203, where the axis ratio of [Cii] is measured
with the similar way as this work (Ikeda et al. in prep). Future
_JWST_ observations will unveil rest-frame optical light distribution, which traces stellar mass distributions. It will allow us to
investigate the inclination dependence of _f_ obs toward high redshift galaxies (e.g., Cochrane et al. 2023).


4.2.4. Caveat


One caveat of our analysis is that we use the single template
of FIR SEDs for all CRISTAL galaxies. Therefore we do not
take into account variation of _T_ dust or β dust characterizing FIR
SEDs. If actual _T_ dust of the galaxies having low (high) _f_ obs are
larger (smaller) than that of the FIR SED used in this work
( _T_ dust ∼ 40K, see Béthermin et al. 2020), the spread of _f_ obs becomes smaller. A variation of _T_ _d_ ∼ 20 K changes infrared luminosities with ∆ _L_ IR ∼ 0.25 dex and the obscured fractions with
∆ _f_ obs ∼ 0.15. Since we find a potential correlation between Σ IR
and _f_ obs, the galaxies with high (low) _f_ obs can have higher (lower)
_T_ dust or _L_ IR than the current estimation if we assume there is a
positive correlation between Σ IR and _T_ dust revealed in previous
results (e.g., Díaz-Santos et al. 2017; Dudzeviˇci¯ut˙e et al. 2020).
In this case, the range of variation expands beyond the current estimation. We need high-frequency ALMA bands (Band-8/9/10),
which cover the frequencies corresponding to the peak of the
dust continuum emission, to derive the FIR SEDs of individual galaxies. While high-frequency band observations towards
large galaxy samples are still challenging due to limitations such
as sensitivities or atmospheric conditions, case studies of some
representative galaxies will help us to know accurate FIR SED.


_4.3._ _Star formation mode of_ _z_ ∼ 5 _LBGs_


4.3.1. Extended dust-obscured star formation


As described in Section 3.4 and Figure 6, we find _r_ _e_,dust are
consistentcomparablewithor slightlythe resultslargerfromthanTNG50 _r_ _e_,UV . Oursimulationsize ratiosexpectingare not
_r_ _e_,UV / _r_ _e_,dust ∼ 2–4 in the stellar mass range of the CRISTAL


Article number, page 10 of 22



galaxies (Popping et al. 2022). As Popping et al. (2022) measure
half-light radii of UV and dust continuum at the almost same
observed wavelength with our observations (λ obs = 1.6µm and
850µm for UV and dust continuum, respectively), the size ratios
can be directly compared.
Before comparing observational results and the simulation,
we need to be careful about observational biases coming from
the limited S/Ns or spatial resolutions. One possible reason for
the extended dust continua is the source blending of nearby companions. To demonstrate how the companions affect the size
measurement, we re-run galfit to the _HST_ images after matching _HST_ PSF to ALMA beam size with photutils/psf and adding
white noises to match peak S/Ns of UV continuum to dust
continuum. As ALMA beam sizes can be changed by different weighting of visibilities, here we use natural-weighted beam
sizes of each visibilities as nominal target beam sizes of the
PSF matching. Typically the naturally-weighted ALMA beam
sizes (0.46 [′′] = 2.9 kpc at _z_ = 5) are larger than _HST_ PSFs
(0.20 [′′] = 1.3 kpc at _z_ = 5). We test the procedure in three
CRISTAL galaxies (CRISTAL-02, 06a, and 22ab) since (i) they
have nearby companions in _HST_ images and (ii) their dust continua are detected in S/N > 6.5. The results reveal the measured
sizes are consistent with those without PSF and S/N matching.
Therefore source blending is not enough to explain the extended
dust continua in CRISTAL galaxies. Another possible reason is
the limited S/N, but it is not likely to be a possible reason because _r_ _e_,dust are still only slightly larger than _r_ _e_,UV when we only
take the sources with S/N > 6.5 into account.
In Figure 9, we show the stacked radial profile of the dust
and UV continuum to obtain better S/N than the individual measurements. Here we stacked UV and dust continuums of single
(“isolated”) galaxy samples to avoid blending with companions.
We follow the visibility-based method described in Section C.2
regarding the stacking of ALMA data. About the stacked UV
continuum image, we shift the fitting center to the central coordinate of the image and match the PSFs of each _HST_ image
to that of the stacked ALMA image, and then take an average.
Again, the stacked radial profile shows that the spatial extent of
the dust continuum is slightly more extended than that of the UV
continuum.
Therefore, the spatially extended dust continuum does not
originate from the observation, but from the properties of the
galaxy itself. Possible physical interpretations of _r_ _e_,UV / _r_ _e_,dust ≲ 1
are clumpy gas distributions that enable UV photons to radiate molecular clouds out to the outskirts of the galaxies, even
though these clouds are slightly distant from young massive
stars. The theoretical and observational studies suggest an increase of clumpy star-forming galaxies at high redshift (e.g.,
Genzel et al. 2008; Dekel et al. 2009; Tadaki et al. 2014; Guo
et al. 2015). In this case, the dust temperature is expected to decrease from the center to the outskirts of the galaxy. In our conversion from _S_ 158µm to _L_ IR, if the dust temperature has a negative
gradient of ∆ _T_ dust ∼ 10 K from center to the outskirts (e.g., Arata
et al. 2019), the infrared luminosity decrease ∼ 0.3 dex, and the
actual spatial extent of the dust-obscured star-forming region becomes comparable with that of the dust-unobscured ones as predicted in SERRA simulation (e.g., Pallottini et al. 2022). Another possibility is that rest-UV observations do not trace global
star formation activities but massive star-forming clumps within
the galaxies.


4.3.2. Stellar mass-size relation


Several _HST_ -based studies of galaxy morphology reveal that the
size of the stellar distribution depends on both redshift and stellar
mass (e.g., van der Wel et al. 2014; Shibuya et al. 2016). The stellar sizes become smaller with increasing redshift at fixed stellar
mass and with decreasing stellar mass at fixed redshift. Fujimoto
et al. (2017) suggest dust continuum sizes also follow a similar

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


**Fig. 8.** The distance from an average _f_ obs - _M_ ∗ relation as a function of (left) the spatial offset of the central position between UV and dust emission,
(middle) the size ratio between UV and dust emission, and (right) the surface density of _L_ IR . Galaxies without clear main UV components and
without dust continuum detection at < 4σ are not shown. Based on the Spearman correlation coefficients and _p_ -values, _f_ obs has a correlation with
the UV-dust spatial offset and Σ IR . On the other hand, there is no correlation between _f_ obs and the size ratio between UV and dust emission.



**Fig. 9.** Normalized radial profiles of the stacked dust and UV continua
(red and blue respectively). The perpendicular lines are effective radii
derived from the best-fit Sérsic profile in the corresponding colors. Here
we stack only single (“isolated”) galaxy samples to avoid the blending
of the companion. The matched PSF size is also shown in a black solid
line. The inset shows the 2D distributions. The spatial extent of the dust
continuum is more extended to that of the UV continuum.


evolutionary trend with redshift and stellar mass. Because the
dust continuum traces recent star formation events and the stellar emission traces histories of the star formation in the galaxies,
the size comparison of the dust continuum and stellar continuum
at similar epochs brings a crucial perspective on the morphological transformation of galaxies.
In Figure 10, we plot rest-frame 158µm dust continuum sizes
of the CRISTAL galaxies as a function of their stellar masses. We
also show typical rest-frame optical sizes of late-type galaxies
(LTGs) and early-type galaxies (ETGs) (van der Wel et al. 2014)
and rest-frame UV sizes (Shibuya et al. 2016) of Lyman-break
galaxies (LBGs) as a function of stellar masses at _z_ ∼ 5. Note
that we extrapolated the redshift evolution reported in van der



Wel et al. (2014) to _z_ ∼ 5 because the rest-frame wavelength of
5000 Å used to measure stellar sizes in van der Wel et al. (2014)
redshifted to the outside of the coverage of _HST_ NIR filters.
Therefore we also show recent _JWST_ studies of the rest-frame
UV sizes of LBGs (Morishita et al. 2023, see also Ono et al.
2023), and those of the rest-frame optical sizes of LTGs (Ward
et al. 2023) and ETGs (Ito et al. 2023). The extrapolated van
der Wel et al. (2014) relation might be slightly overestimated,
although the difference does not impact our conclusion. Future
direct comparison with the rest-frame optical sizes measured by
_JWST_ observations will allow us to capture the dust, UV, and
stellar size properties of the typical galaxies individually.
The dust continuum sizes and stellar masses of more dusty
galaxies follow the trend of ETGs (e.g., Gómez-Guijarro et al.
2022). These results imply that massive dusty galaxies are in a
build-up phase of central stellar cores (i.e., stellar bulge) of massive elliptical galaxies (e.g., Toft et al. 2014; Gómez-Guijarro
et al. 2022) or evolve into compact quiescent galaxies (e.g., Toft
et al. 2014; Ikarashi et al. 2015; Barro et al. 2016). This is consistent with the studies that investigated the stellar and dust continuum sizes of individual galaxies at _z_ ∼ 2–3 (Simpson et al.
2015; Gullberg et al. 2019; Lang et al. 2019; Tadaki et al. 2020a).
In contrast, as shown in Figure 10, the dust continuum sizes of
CRISTAL galaxies follow a similar trend as the mass-size relation of LTGs or LBGs. Average stellar mass ( _M_ ∗ ∼ 10 [9][.][8] _M_ ⊙ )
and effective radius (∼1.7 kpc) are in excellent agreement with
them on the mass-size plane. Our result suggests that typical starforming galaxies with _M_ ∗ ∼ 10 [10] _M_ ⊙ might be still growing their
disks via global star formation.


_4.4._ _Morphological transformation and descendant_


Recent wide field surveys revealed typical dark matter halo
masses of the bright LBGs ( _M_ UV ∼−21 mag, _M_ ∗ ∼ 10 [10] _M_ ⊙
in stellar mass) at _z_ = 4–6 are _M_ halo ∼ 10 [12] _M_ ⊙ (e.g., Harikane
et al. 2018). If we assume the median growth rate for their dark
matter haloes from N-body simulations, dark matter haloes with
masses of _M_ halo ∼ 10 [12] _M_ ⊙ at _z_ ∼ 5 evolve into haloes with
_M_ halo ∼ 10 [12][.][5][−][13][.][0] _M_ ⊙ at _z_ ∼ 2, which host massive galaxies with
mass of _M_ ∗ ∼ 10 [11] _M_ ⊙ at _z_ ∼ 2. In the case that the bright LBGs
at _z_ = 4–6 continue to stay MS to _z_ = 2, their stellar masses
could be _M_ ∗ ≳ 10 [11] _M_ ⊙ . From these estimation, the bright LBGs
with _M_ ∗ ∼ 10 [10] _M_ ⊙ at _z_ = 4–6 are likely to evolve into _z_ ∼ 2
massive galaxies with _M_ ∗ ∼ 10 [11] _M_ ⊙ .


Article number, page 11 of 22

_A&A proofs:_ manuscript no. main



**Fig.** **10.** Stellar mass versus effective radii of the dust continuum for
the CRISTAL galaxies. The dashed and solid lines show the scaling
relations derived with _HST_ and _JWST_ . The orange and green colors represent the rest-frame optical sizes of ETGs (van der Wel et al. 2014; Ito
et al. 2023), and the LTGs (van der Wel et al. 2014; Ward et al. 2023).
The blue colors indicate rest-frame UV sizes of LBGs (Shibuya et al.
2016; Morishita et al. 2023). The average stellar mass and stacked size
derived in Section C.2 is also shown. CRISTAL galaxies are distributed
around the scaling sequence of LTGs or LBGs in contrast to the massive SMGs that show consistent dust continuum sizes and stellar masses
with those of ETGs (Riechers et al. 2014; De Breuck et al. 2014; Hodge
et al. 2015; Gómez-Guijarro et al. 2018; Casey et al. 2019; Tadaki et al.
2020b).


As the average structural evolutions of SFGs are expected to
follow the scaling relation on the mass-size plane, a bright LBG
at _z_ = 4-6 will grow its stellar disk by a factor of two after a
ten-fold increase in stellar mass. The expected size of the stellar
disks is consistent with that of massive DSFGs at _z_ ∼ 2. This
consistency also supports that the bright LBGs at _z_ = 4–6 are
expanding their stellar disks through widespread star formation.


**5.** **Summary and Conclusion**


In this paper, we have focused on the dust continuum emissions
of _z_ ∼ 5 normal star-forming galaxies as a part of the ALMA
cycle-8 large program, CRISTAL. We have examined the spatial extent of the dust-obscured and unobscured star formation,
obscured fraction of star formation as a function of stellar mass
( _f_ obs − _M_ ∗ ) relation, and origin of the observed variation in fobs
with stellar mass on _f_ obs − _M_ ∗ . The sample is representative of
typical star-forming galaxies at _z_ = 4–6 as almost all of them
lie within 0.3 dex of the main sequence of star-forming galaxies in that redshift range. The stellar mass ( _M_ ∗ ) and SFR of the
target galaxies are the range of log 10 _M_ ∗ [ _M_ ⊙ ] ∼ 9.5–11.0 and
log 10 SFR [ _M_ ⊙ yr [−][1] ] ∼ 1.0–2.7. From individual measurements
and stacking analysis, we found:


1. The CRISTAL galaxies have ∼1 dex smaller infrared luminosities ( _L_ IR ) and are slightly more extended in dust continuum emission than DSFGs or SMGs. Consequently the
median IR surface densities Σ IR are ∼10 times smaller (Figure 5). This suggests that representative galaxy population


Article number, page 12 of 22



at _z_ ∼4–6 undergoes moderate star formation with a lower
Σ IR compared with the dusty galaxies indicating intensive,
centrally concentrated star formation.
2. The obscured fraction has a positive correlation with the stellar mass (Figure 7, left). Our averaged relationship is consistent with the previous results at _z_ ∼5–9 and supports that
the obscured fraction at the range of _M_ ∗ < 10 [10] _M_ ⊙ does not
show clear evolution from _z_ = 0–2.5, but may decrease at the
range of _M_ ∗   - 10 [10] _M_ ⊙ . The possible evolution at the range
of _M_ ∗   - 10 [10] _M_ ⊙ suggests the evolution of dust content from
_z_ ∼ 5 to _z_ ∼ 0–2.5.
3. A large variation in _f_ obs - _M_ ∗ relation across galaxies in our
sample. Through deep observations in our survey, we trace
the galaxy with an obscured fraction of as low as 20%,
which is smaller than what has been reported in previous
surveys. We find a weak correlation between _f_ obs and potential merger identified by multiplicity, and compactness of
the dust-obscured star-forming regions, but do not detect a
correlation with the spatial offset between UV and dust continuum, or viewing angle (Figure 8). Some mechanisms such
as interactions or rich gas accretions may enhance the concentration of gas and dust, and accelerate the obscuration of
the star formation activities.
4. The effective radii of the dust continuum ( _r_ _e_,dust ) are comparable or ∼ 2 times larger than that of the UV continuum
sion originates the dust heated by UV radiation from massive( _r_ _e_,UV ) in the individual comparison whereas the dust emisO/B type stars. These results are not consistent with the Illustris TNG50 simulation which expects0.5 in the stellar mass range of the CRISTAL galaxies. With _r_ _e_,dust / _r_ _e_,UV ∼ 0.25–
careful treatment and stacking analysis, we confirm comparable sizes of the dust and UV continuum do not come from
observational uncertainties. The extended dust size may be
due to (i) clumpy gas distribution makes UV photons possible to radiate molecular clouds around the outskirts of galaxies or (ii) rest-frame UV observations do not trace global star
formation activities but massive star-forming clumps within
galaxies.
5. The CRISTAL galaxies follow a similar trend as LTGs or
LBGs in the stellar mass-size plane (Figure 10). They are
distributed in a different regime compared with more dusty
galaxies that follow the trend of ETGs. Our result suggests
typical star-forming galaxies with _M_ ∗ ∼ 10 [10] _M_ ⊙ are in a
growing-up phase of disks through global star formation.
6. An expansion of the disks in _z_ ∼ 5 normal SFGs along
with the star-forming sequence in the mass-size plane are
completely consistent with the large stellar disks of massive
galaxies at _z_ ∼ 2. An expansion of the stellar disks from _z_ ∼ 5
to _z_ ∼ 2 and the subsequent compaction events naturally explain morphological transformation and are consistent with
previous studies examining massive galaxies at _z_ ∼ 2.


Our results emphasize the importance of considering the
spatial extent of both the dust-unobscured and obscured starformation activities are important when studying their morphological transformation, especially given more than ∼50% of the
star-formation activities is obscured by the dust at the stellar
mass range of _M_ ∗ - 10 [10] _M_ ⊙ . Since the spatial extent of the dustobscured star formation is almost comparable with that of the
dust-unobscured one, normal star-forming galaxies at _z_ ∼ 5 are
not making their sizes compact, but expanding their stellar disks.
Inner structures of the typical star-forming galaxies at _z_ ∼ 5, at
the end of the epoch of reionization, is an important question to
be addressed with future ALMA and _JWST_ observations, which
will provide the more secure spatial extent of dust-obscured starforming regions or other components such as pre-existing stellar
disks or ionized gas. Also, ALMA has the capability of highfrequency observations such as band-8/9/10, which enables us to
constrain the FIR SED of each galaxy and bring us to a clearer
picture of the obscured star formation.

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


_Acknowledgements._ This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2017.1.00428.S, #2018.1.01359.S, #2018.1.01605.S,
#2019.1.01075.S, #2019.1.00226.S, and #2021.1.00280.L. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS
(Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This work
was supported by JSPS KAKENHI grant No. 23K03466. I.M. is financially
supported by Grants-in-Aid for Japan Society for the Promotion of Science
(JSPS) Fellows (KAKENHI Number 22KJ0821). R.H.-C. thanks to the Max
Planck Society for support under the Partner Group project "The Baryon
Cycle in Galaxies" between the Max Planck for Extraterrestrial Physics
and the Universidad de Concepción. R.H-C. also gratefully acknowledges
financial support from Millenium Nucleus NCN19058 (TITANs), and ANID
BASAL projects ACE210002 and FB210003. M.A. acknowledges support from
FONDECYT grant 1211951. M.A. and R.J.A. acknowledge support from ANID
BASAL project grant FB210003. R.J.A. was supported by FONDECYT grant
number 123171. R.B. acknowledges support from an STFC Ernest Rutherford
Fellowship [grant number ST/T003596/1]. R.D. is supported by the Australian
Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. A.F. acknowledges
support from the ERC Advanced Grant INTERSTELLAR H2020/740120.
T.N. acknowledges support from the Deutsche Forschungsgemeinschaft
(DFG, German Research Foundation) under Germany’s Excellence Strategy
- EXC-2094 - 390783311 from the DFG Cluster of Excellence “ORIGINS”.
M.R. acknowledges support from project PID2020-114414GB-100, financed by
MCIN/AEI/10.13039/501100011033. H.Ü. gratefully acknowledges support by
the Isaac Newton Trust and by the Kavli Foundation through a Newton-Kavli
Junior Fellowship. Data analysis was in part carried out on the Multi-wavelength
Data Analysis System operated by the Astronomy Data Center (ADC), National
Astronomical Observatory of Japan.



Article number, page 13 of 22

_A&A proofs:_ manuscript no. main



**Table A.1.** Parameters for SED fitting


Parameters Range
**SFH: Delayed-** τ **(** delayed **)**
τ main [Myr] 100, 300, 500, 1000, 2000, 5000
Age main [Myr] 50 Myr steps in [50: 1000]
τ burst [Myr] 10, 50, 100
Age burst [Myr] 10, 20, 50
f burst [Myr] 0.0, 0.05, 0.1, 0.2
**SSP: BC03**

IMF Chabrier
_Z_ [ _Z_ ⊙ ] 0.2, 1
**Nebular emission: CLOUDY**
log 10 _U_ -3.0
line width [ km s [−][1] ] 300
**Dust attenuation: Calzetti00**
E(B-V) 0.1 steps in [0.0: 2.0]
E(B-V) factor 0.44
_R_ v 3.1


**Appendix A:** **CIGALE parameters used to estimate**
**global properties**


We use all available broad- (BBs) and medium bands (MBs) in
optical to near-infrared (NIR) for the SED fitting. In the COSMOS2015 catalog, we use 10 broad bands ( _u_ [∗], _B_, _V_, _r_ [+], _i_ [+], _z_ [++],
_Y_, _J_, _H_, _K_ _s_ ) and 12 medium bands on Ground-based telescopes,
and 4 _Spitzer_ bands that achieve the best sensitivities among the
bands covering similar wavelength. We take 4 broad bands ( _U_,
_B_, _R_, _K_ _s_ ) and 23 medium bands on Ground-based telescopes,
and 10 _HST_ and 4 _Spitzer_ bands on space telescopes from the
ASTRODEEP catalog. We extract the total fluxes of the counterparts of the CRISTAL galaxies from the corresponding catalogs.
Table A.1 shows parameters used in SED fitting to derive stellar
masses and SFRs (see Section 2.2).


**Appendix B:** **comparison of** **SFR** **SED** **and**
**SFR** **UV** + **SFR** **IR**

In Figure B.1, we compare SFR UV +SFR IR and SFR SED . SFR UV +
SFR IR is calculated by summing up SFR UV from best-fit SED
and SFR IR from the rest-frame 158 µm dust continuum flux
and SFR SED is computed by averaging the SFH over 100 Myr.
SFR SED is broadly consistent with SFR UV + SFR IR . CRISTAL24 show ∼ 1.4 dex smaller SFR SED than SFR UV + SFR IR . This
difference is due to the degeneracy of the dust extinction and
stellar age and makes CRISTAL-24 distribute ∼ 1.2 dex lower
than the main sequence.


**Appendix C:** **Validation of the dust size**
**measurement**


As shown in Table 1, about half of the CRISTAL galaxies range
4.4 < S/N < 5.5 in the dust continuum images. These S/Ns
might translate to significant uncertainties in our flux measurements but also to systematical errors in the sizes. To evaluate
uncertainties of the size measurement through visibility fitting
and confirm the validity of the size measurement, we conducted
a Monte Carlo simulation and a stacking analysis toward fainter
CRISTAL galaxies.


_Appendix C.1:_ _Monte-Carlo simulation_


Because the measured sizes might be affected by noise fluctuations, we need to know the dependence of the size measurement
uncertainties on the source S/N.


Article number, page 14 of 22



**Fig. B.1.** SFR UV + SFR IR vs SFR SED . The black dashed line represents
a one-to-one relationship. SFR SED is broadly consistent with SFR UV +
SFR IR, except for CRISTAL-24.


In the following Monte-Carlo simulation, we use the visibilities of six galaxies (CRISTAL-01b, 07ab, 09, 10, 11a, and
19) that have relatively low S/Ns among the CRISTAL sample
(4.4 ≤ S/N ≤ 5.5). This selection was made because galaxies
with smaller S/N are anticipated to be more affected by noise
fluctuations in size measurements. We take different array configurations used in each CRISTAL galaxy into account as the visibilities of the six galaxies encompass various representative _uv_
coverages among those obtained in our observations. We create

∼ ∼
1500 ( 300 in each field) artificial circular Gaussian sources
with a log uniform distribution of total flux within a range of
0.025–1.25 mJy and effective radius ranging 0.025–1.5 [′′] . After subtracting observed galaxies with the CASA task tclean,
we injected the generated mock sources in the visibilities at a
random position and calculated source S/N in the same manner
as referred to in Sec 3.1. When the mock source is detected at
4.4 < S/N (lowest S/N among observed galaxies in dust continuum), we fit a circular Gaussian model by setting an initial
estimation of the central position to the artificial source center
using UVMultifit.
In Figure C.1, we plot the result of the Monte-Carlo simulation, with an average and standard deviation of the ratio between input and output values. As shown in Figure C.1, independent of the S/N of the source, we do not find any systematic offsets between intrinsic sizes and resulting measured sizes
(size inp /size fit ∼ 0). This result demonstrates the estimated sizes
of these galaxies are on average reliable. However, careful treatment of individual sizes of the sources with 4.4 ≤ S/N ≤ 5.5
is needed as the output sizes of these sources show large scatters
from input sizes (size inp /size fit = 0.07 [+] − [0] 0 [.] . [67] 26 [) especially in the case]
that output sizes are less than 0.4 [′′] (size inp /size fit = 0.09 [+] − [0] 0 [.] . [83] 32 [). To]
obtain a better estimation of the size of these low-S/N sources,
we additionally carry out a stacking analysis in the following
section.


_Appendix C.2:_ _Stacked size_


We now perform stacking analysis to check whether there are
systematic biases in our size estimates. If galaxies included in
stacking are intrinsically compact (extended) but appear as extended (compact) due to noise effects, stacked sizes are expected
to become smaller (larger) than a weighted average of the indi

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


**Fig. C.1.** Comparison of the flux density and FWHM between fitting results and input models. The left, middle, and right panels show the results
for sources detected at S/N = 4.4–5.5, S/N = 6.5–7.8 and S/N ≥ 12.3, respectively. Different colors indicate different visibilities used in the
simulation, corresponding to the different array configurations. White circles and error bars show 50 ± 34% percentiles in the bins of output values.
Black solid and dashed lines correspond to the averages and standard deviations of the fitting results and output models, which are also shown in
the bottom right of each panel.



vidual sizes. We perform the stacking analysis, especially for six
of eight CRISTAL galaxies with 4.4 ≤ S/N ≤ 5.5 (CRISTAL01b, 07ab, 09, 10, 11a, and 19), to evaluate the potential size misestimations. We did not use the other two galaxies (CRISTAL-03
and 21) because CRISTAL-03 is not resolved and CRISTAL-21
has extremely extended sizes therefore they may affect stacked
sizes strongly.
We align phase centers to the measured central position and
set the phase center to a common coordinate of α = 00h 00m
00s; δ = 00d 00m 00s (J2000) with CASA task fixplanet. We
concatenate all visibilities into a single measurement set with the
concat task. Finally, we measured the sizes with UVMultifit.
The estimated average size is 0.209±0.061 [′′], which is consistent with the average of the individually measured sizes (0.237 [′′] )
within 1σ uncertainty. Therefore we conclude that the individual
measurements of the six CRISTAL galaxies listed above are reliable. While the stacked measurements do not significantly affect
the conclusion, we also plot the stacked size in Figure 10.


**Appendix D:** **Sérsic index-dependence of the UV**
**sizes**


In Figure D.1, we compare the derived UV sizes under the assumption of Sérsic index _n_ = 1 and _n_ = free. Overall, there
is no systematic difference between the two sizes. CRISTAL-25
shows a larger size in the case of _n_ = free because the best-fit



Sérsic index is larger than unity ( _n_ = 7.3 ± 1.7). We note that this
size difference of CRISTAL-25 does not affect the conclusion.


**Appendix E:** **fitting results of ALMA and HST**


Figure E.1 shows the results of the dust continuum size measurements in the visibility domain. The left and middle panels show
the observed and residual images respectively. The observed and
model images are natural-weighted in Figure E.1. The right panels show visibility amplitudes as a function of _uv_ -distance from
the central position of the fitting in two different binning scales
(red and magenta). Red solid lines and shaded regions show bestfit models and uncertainties. To illustrate how the sizes are measured without the CRISTAL dataset, we add these results in gray
points and solid lines. Figure E.3 shows results of the rest-frame
UV size measurements in _HST_ /F160W.


Article number, page 15 of 22

_A&A proofs:_ manuscript no. main


**Fig.** **D.1.** UV size comparison between the case with the Sérsic index fixed ( _n_ = 1) and with the Sérsic index free. Black solid and
dashed lines indicate one-to-one relation and ±0.3dex. The sizes are
almost consistent, except for CRISTAL-25 showing a large Sérsic index ( _n_ = 7.3 ± 1.7).


Article number, page 16 of 22

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


**Fig. E.1.** Fitting results of the ALMA images. The left and middle panels show the natural-weighted observed and residual images respectively.
The contours indicate every 1σ from ±3σ to 10σ and every 3σ from 10σ. The right panels show the visibility real part as a function of _uv_ -distance
from a central position of the fitting in two different binning scales (red and blue). Red solid lines and shaded regions show best-fit models and 1σ
uncertainties. We also show sizes without the CRISTAL dataset when the fittings have converged. (gray points and solid lines).


Article number, page 17 of 22

_A&A proofs:_ manuscript no. main


**Fig. E.2.** Continue from Figure E.2. For CRISTAL-21, we also show the best-fit profile assuming Gaussian to illustrate how the measurement is
uncertain due to the extrapolation toward the uv distance of < 50 kλ


Article number, page 18 of 22

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6


**Fig. E.3.** The fitting results of the _HST_ /F160W images. Observed, model, and residual images are shown from left to right. The contours indicate
every 2σ from ±4σ.


Article number, page 19 of 22

_A&A proofs:_ manuscript no. main



**Fig. E.4.** (continue)


Article number, page 20 of 22

Mitsuhashi et al.: Resolved dust of normal SFGs at _z_ = 4–6



**References**


Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142
Arata, S., Yajima, H., Nagamine, K., Li, Y., & Khochfar, S. 2019, MNRAS, 488,
2629
Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021, MNRAS, 508, L58
Barnes, J. E. & Hernquist, L. 1996, ApJ, 471, 115
Barro, G., Kriek, M., Pérez-González, P. G., et al. 2016, ApJ, 827, L32
Behrens, C., Pallottini, A., Ferrara, A., Gallerani, S., & Vallini, L. 2018, MNRAS, 477, 552
Béthermin, M., Accard, C., Guillaume, C., et al. 2023, arXiv e-prints,
arXiv:2311.08474
Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113
Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2
Béthermin, M., Wu, H.-Y., Lagache, G., et al. 2017, A&A, 607, A89
Blain, A. W., Smail, I., Ivison, R. J., Kneib, J. P., & Frayer, D. T. 2002,
Phys. Rep., 369, 111
Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103
Bouwens, R., González-López, J., Aravena, M., et al. 2020, ApJ, 902, 112
Bouwens, R. J., Aravena, M., Decarli, R., et al. 2016, ApJ, 833, 72
Bouwens, R. J., Illingworth, G. D., Blakeslee, J. P., Broadhurst, T. J., & Franx,
M. 2004a, ApJ, 611, L1
Bouwens, R. J., Illingworth, G. D., Franx, M., & Ford, H. 2007, ApJ, 670, 928
Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2012, ApJ, 754, 83
Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160
Bouwens, R. J., Thompson, R. I., Illingworth, G. D., et al. 2004b, ApJ, 616, L79
Bowler, R. A. A., Bourne, N., Dunlop, J. S., McLure, R. J., & McLeod, D. J.
2018, MNRAS, 481, 1631
Bowler, R. A. A., Cullen, F., McLure, R. J., Dunlop, J. S., & Avison, A. 2022,
MNRAS, 510, 5088
Bowler, R. A. A., Inami, H., Sommovigo, L., et al. 2023, arXiv e-prints,
arXiv:2309.17386
Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000
Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682
Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455
Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2022, arXiv e-prints,
arXiv:2211.07865
Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45
Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55
Casey, C. M., Zavala, J. A., Manning, S. M., et al. 2021, ApJ, 923, 215
Chabrier, G. 2003, PASP, 115, 763
Chen, C.-C., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 194
Cochrane, R. K., Anglés-Alcázar, D., Cullen, F., & Hayward, C. C. 2023, arXiv
e-prints, arXiv:2310.08829
Cullen, F., McLure, R. J., Khochfar, S., Dunlop, J. S., & Dalla Vecchia, C. 2017,
MNRAS, 470, 3006
Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2
da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110
Daddi, E., Cimatti, A., Renzini, A., et al. 2004, ApJ, 617, 746
Daddi, E., Renzini, A., Pirzkal, N., et al. 2005, ApJ, 626, 680
Dale, D. A. & Helou, G. 2002, ApJ, 576, 159
De Breuck, C., Williams, R. J., Swinbank, M., et al. 2014, A&A, 565, A59
Dekel, A., Sari, R., & Ceverino, D. 2009, ApJ, 703, 785
Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5
Devereaux, T., Cassata, P., Ibar, E., et al. 2023, arXiv e-prints, arXiv:2311.11493
Díaz-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32
Draine, B. T. & Li, A. 2007, ApJ, 657, 810
Dudzeviˇci¯ut˙e, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828
Dunlop, J. S., Abraham, R. G., Ashby, M. L. N., et al. 2021, PRIMER: Public
Release IMaging for Extragalactic Research, JWST Proposal. Cycle 1, ID.
#1837
Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861
Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020a, MNRAS, 498, 4192
Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020b, ApJS, 247, 61
Ferguson, H. C., Dickinson, M., Giavalisco, M., et al. 2004, ApJ, 600, L107
Ferland, G. J., Korista, K. T., Verner, D. A., et al. 1998, PASP, 110, 761
Ferrara, A., Hirashita, H., Ouchi, M., & Fujimoto, S. 2017, MNRAS, 471, 5018
Ferrara, A., Sommovigo, L., Dayal, P., et al. 2022, MNRAS, 512, 58
Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152
Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020a, A&A, 643, A4
Fudamoto, Y., Oesch, P. A., Magnelli, B., et al. 2020b, MNRAS, 491, 4724
Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489
Fujimoto, S., Kohno, K., Ouchi, M., et al. 2023, arXiv e-prints,
arXiv:2303.01658
Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83
Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1
Genzel, R., Burkert, A., Bouché, N., et al. 2008, ApJ, 687, 59
Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020a, A&A, 643, A7
Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020b, A&A, 633, A90
Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 658, A43
Gómez-Guijarro, C., Toft, S., Karim, A., et al. 2018, ApJ, 856, 121
Gruppioni, C., Béthermin, M., Loiacono, F., et al. 2020, A&A, 643, A8
Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, MNRAS, 490, 4956
Guo, Y., Ferguson, H. C., Bell, E. F., et al. 2015, ApJ, 800, 39
Harikane, Y., Ouchi, M., Ono, Y., et al. 2018, PASJ, 70, S11
Hathi, N. P., Jansen, R. A., Windhorst, R. A., et al. 2008, AJ, 135, 156
Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649,
A31



Hodge, J. A., Riechers, D., Decarli, R., et al. 2015, ApJ, 798, L18
Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103
Howell, J. H., Armus, L., Mazzarella, J. M., et al. 2010, ApJ, 715, 572
Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS, 524, 1775
Ikarashi, S., Ivison, R. J., Caputi, K. I., et al. 2015, ApJ, 810, 133
Ikeda, R., Tadaki, K.-i., Iono, D., et al. 2022, ApJ, 933, 11
Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126
Ito, K., Valentino, F., Brammer, G., et al. 2023, arXiv e-prints, arXiv:2307.06994
Jonsson, P., Groves, B. A., & Cox, T. J. 2010, MNRAS, 403, 17
Kennicutt, Robert C., J. 1998, ARA&A, 36, 189
Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531
Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24
Lang, P., Schinnerer, E., Smail, I., et al. 2019, ApJ, 879, 54
Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJ, 837, L21
Laporte, N., Zitrin, A., Ellis, R. S., et al. 2021, MNRAS, 505, 4838
Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1
Leslie, S. K., Schinnerer, E., Groves, B., et al. 2018, A&A, 616, A157
Liang, L., Feldmann, R., Hayward, C. C., et al. 2021, MNRAS, 502, 3210
Lilly, S., Schade, D., Ellis, R., et al. 1998, ApJ, 500, 75
Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415
Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6
Magnelli, B., Elbaz, D., Chary, R. R., et al. 2009, A&A, 496, 57
Magnelli, B., Elbaz, D., Chary, R. R., et al. 2011, A&A, 528, A35
Martí-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563,
A136
McLure, R. J., Dunlop, J. S., Cullen, F., et al. 2018, MNRAS, 476, 3991
Merlin, E., Castellano, M., Santini, P., et al. 2021, A&A, 649, A22
Morishita, T., Stiavelli, M., Chary, R.-R., et al. 2023, arXiv e-prints,
arXiv:2308.05018
Moutard, T., Sawicki, M., Arnouts, S., et al. 2020, MNRAS, 494, 1894
Nelson, E. J., Tadaki, K.-i., Tacconi, L. J., et al. 2019, ApJ, 870, 130
Oesch, P. A., Bouwens, R. J., Carollo, C. M., et al. 2010, ApJ, 709, L21
Ono, Y., Harikane, Y., Ouchi, M., et al. 2023, arXiv e-prints, arXiv:2309.02790
Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621
Pannella, M., Carilli, C. L., Daddi, E., et al. 2009, ApJ, 698, L116
Pannella, M., Elbaz, D., Daddi, E., et al. 2015, ApJ, 807, 141
Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266
Popping, G., Pillepich, A., Calistro Rivera, G., et al. 2022, MNRAS, 510, 3321
Popping, G., Puglisi, A., & Norman, C. A. 2017a, MNRAS, 472, 2315
Popping, G., Somerville, R. S., & Galametz, M. 2017b, MNRAS, 471, 3152
Reddy, N. A., Oesch, P. A., Bouwens, R. J., et al. 2018, ApJ, 853, 56
Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014, ApJ, 796, 84
Rowan-Robinson, M., Oliver, S., Wang, L., et al. 2016, MNRAS, 461, 1100
Safarzadeh, M., Hayward, C. C., & Ferguson, H. C. 2017, ApJ, 840, 15
Schouws, S., Stefanon, M., Bouwens, R., et al. 2022, ApJ, 928, 31
Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30
Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150
Sérsic, J. L. 1963, Boletin de la Asociacion Argentina de Astronomia La Plata
Argentina, 6, 41
Shen, S., Mo, H. J., White, S. D. M., et al. 2003, MNRAS, 343, 978
Shibuya, T., Ouchi, M., Kubo, M., & Harikane, Y. 2016, ApJ, 821, 72
Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 81
Skelton, R. E., Whitaker, K. E., Momcheva, I. G., et al. 2014, ApJS, 214, 24
Smail, I., Dudzeviˇci¯ut˙e, U., Stach, S. M., et al. 2021, MNRAS, 502, 3426
Sommovigo, L., Ferrara, A., Carniani, S., et al. 2022a, MNRAS, 517, 5930
Sommovigo, L., Ferrara, A., Carniani, S., et al. 2021, MNRAS, 503, 4878
Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022b, MNRAS, 513, 3122
Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS,
214, 15
Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112
Steidel, C. C., Adelberger, K. L., Giavalisco, M., Dickinson, M., & Pettini, M.
1999, ApJ, 519, 1
Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74
Tadaki, K.-i., Belli, S., Burkert, A., et al. 2020a, ApJ, 901, 74
Tadaki, K.-i., Iono, D., Yun, M. S., et al. 2020b, ApJ, 889, 141
Tadaki, K.-i., Kodama, T., Tanaka, I., et al. 2014, ApJ, 780, 77
Toft, S., Smolˇci´c, V., Magnelli, B., et al. 2014, ApJ, 782, 68
Toft, S., van Dokkum, P., Franx, M., et al. 2007, ApJ, 671, 285
Trujillo, I., Förster Schreiber, N. M., Rudnick, G., et al. 2006, ApJ, 650, 18
Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36
van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28
Wang, W., Kassin, S. A., Pacifici, C., et al. 2018, ApJ, 869, 161
Ward, E. M., de la Vega, A., Mobasher, B., et al. 2023, arXiv e-prints,
arXiv:2311.02162
Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327
Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11
Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ, 850, 208
Witt, A. N. & Gordon, K. D. 2000, ApJ, 528, 799
Wuyts, S., Labbé, I., Förster Schreiber, N. M., et al. 2008, ApJ, 682, 985
Yajima, H., Choi, J.-H., & Nagamine, K. 2011, MNRAS, 412, 411
Yamaguchi, Y., Kohno, K., Hatsukade, B., et al. 2019, ApJ, 878, 73
Zavala, J. A., Casey, C. M., Manning, S. M., et al. 2021, ApJ, 909, 165


Article number, page 21 of 22

_A&A proofs:_ manuscript no. main


1 Department of Astronomy, The University of Tokyo, 7-3-1 Hongo,
Bunkyo, Tokyo 113-0033, Japan
2 National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan
e-mail: `ikki0913astr@gmail.com`
3 Faculty of Engineering, Hokkai-Gakuen University, Toyohira-ku,
Sapporo 062-8605, Japan
4 Department of Astronomical Science, SOKENDAI (The Graduate
University for Advanced Studies), Mitaka, Tokyo 181-8588, Japan
5 Departamento de Astronomía, Universidad de Concepción, Barrio
Universitario, Concepción, Chile
6 Instituto de Estudios Astrofísicos, Facultad de Ingeniería y Ciencias,
Universidad Diego Portales, Av. Ejército 441, Santiago, Chile
7 Sterrenkundig Observatorium, Ghent University, Krijgslaan 281 S9, B-9000 Ghent, Belgium
8 Department of Physics & Astronomy, University College London,
Gower Street, London WC1E 6BT, UK
9 Max-Planck-Institut für Extraterrestische Physik (MPE), Giessenbachstr., 85748, Garching, Germany
10 Las Campanas Observatory, Carnegie Institution of Washington,
Casilla 601, La Serena, Chile
11 Department of Physics and Astronomy and George P. and Cynthia
Woods Mitchell Institute for Fundamental Physics and Astronomy,
Texas A&M University, College Station, TX, USA
12 Leiden Observatory, Leiden University, NL-2300 RA Leiden,
Netherlands
13 Joint ALMA Observatory, Alonso de Córdova 3107, Vitacura, Santiago, Chile
14 National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA 22903, USA
15 Jodrell Bank Centre for Astrophysics, Department of Physics and
Astronomy, School of Natural Sciences, The University of Manchester, Manchester, M13 9PL, UK
16 European Southern Observatory (ESO), Karl-Schwarzschild-Straße
2, 85748, Garching bei München, Germany
17 Centre for Astrophysics and Supercomputing, Swinburne Univ. of
Technology, PO Box 218, Hawthorn, VIC, 3122, Australia
18 ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), Australia
19 Research School of Astronomy and Astrophysics, Australian National University, Canberra, ACT 2611, Australia
20 Institute of Astrophysics, Foundation for Research and TechnologyHellas (FORTH), Heraklion, 70013, Greece
21 Chinese Academy of Sciences South America Center for Astronomy
(CASSACA), National Astronomical Observatories, CAS, Beijing,
100101, PR China
22 Scuola Normale Superiore, Piazza dei Cavalieri 7, I-50126 Pisa,
Italy
23 Dept. Fisica Teorica y del Cosmos, Universidad de Granada,
Granada, Spain
24 Instituto Universitario Carlos I de Física Teórica y Computacional,
Universidad de Granada, E-18071 Granada, Spain
25 Max-Planck Institute for Astrophysics, Karl Schwarzschildstrasse 1,
85748, Garching, Germany
26 INAF - OAS, Osservatorio di Astrofisica e Scienza dello Spazio di
Bologna, via Gobetti 93/3, 40129 Bologna, Italy
27 Cavendish Laboratory, University of Cambridge, 19 J.J. Thomson
Avenue, Cambridge, CB3 0HE, UK
28 Kavli Institute for Cosmology, University of Cambridge, Madingley
Road, Cambridge, CB3 0HA, UK
29 Department of Astronomy and Joint Space-Science Institute, University of Maryland, College Park, Maryland, USA 20742


Article number, page 22 of 22


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "4 Spitzer bands in COSMOS2015 and ASTRODEEP catalogs used for SED fitting",
  "failed_quote": "In the COSMOS2015 catalog, we use 10 broad bands (u*, B, V, r+, i+, z++, Y, J, H, K_s) and 12 medium bands on Ground-based telescopes, and 4 Spitzer bands that achieve the best sensitivities among the bands covering similar wavelength."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "Publicly available photometric catalog in COSMOS field (COSMOS2015 catalog) with 10 broad bands, 12 medium bands, and 4 Spitzer bands",
  "failed_quote": "We cross-match positions of the CRISTAL galaxies to publicly available photometric catalogs in COSMOS (COSMOS2015 catalog, Laigle et al. 2016) and GOODS-S fields (ASTRODEEP catalog, Merlin et al. 2021)."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "Publicly available photometric catalog in COSMOS field (COSMOS2015 catalog) with 10 broad bands, 12 medium bands, and 4 Spitzer bands",
  "failed_quote": "In the COSMOS2015 catalog, we use 10 broad bands (u*, B, V, r+, i+, z++, Y, J, H, K_s) and 12 medium bands on Ground-based telescopes, and 4 Spitzer bands that achieve the best sensitivities among the bands covering similar wavelength."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Publicly available photometric catalog in GOODS-S field (ASTRODEEP catalog) with 4 broad bands, 23 medium bands, 10 HST and 4 Spitzer bands",
  "failed_quote": "We cross-match positions of the CRISTAL galaxies to publicly available photometric catalogs in COSMOS (COSMOS2015 catalog, Laigle et al. 2016) and GOODS-S fields (ASTRODEEP catalog, Merlin et al. 2021)."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Cross-match galaxy positions within 1'' to COSMOS2015 and ASTRODEEP catalogs and perform multi-wavelength SED fitting using CIGALE",
  "failed_quote": "We cross-match positions of the CRISTAL galaxies to publicly available photometric catalogs in COSMOS (COSMOS2015 catalog, Laigle et al. 2016) and GOODS-S fields (ASTRODEEP catalog, Merlin et al. 2021). All of the CRISTAL galaxies have counterparts within 1''."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Consistent with LePhare results from the ALPINE program within 1σ uncertainty, and SFR_SED is compared against SFR_UV + SFR_IR",
  "failed_quote": "CRISTAL galaxies have stellar masses of log_10 M_* [M_⊙] ≳ 9.5, which are consistent with the results from LePhare code in the ALPINE program within the 1σ uncertainty."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Convert rest-frame 158 µm dust continuum fluxes to total IR (8–1000 µm) luminosity using the scaling factor from Béthermin et al. (2020), and calculate Σ_IR = L_IR / (2π r_e,dust^2)",
  "failed_quote": "Figure 5 shows the total infrared luminosity against the circularized effective radius (left) or the surface infrared luminosity ≡ Σ_IR = L_IR /2π r_e,dust^2 (right) of dust continuum emission."
 },
 {
  "path": "analysis_steps[4].method.evidence[2]",
  "value": "Construct empirical PSF by stacking normalized, reprojected point sources; generate sigma maps from drizzle weights and mask maps from SExtractor segmentation maps; fit 2D Sérsic profile (fixed n = 1) using GALFIT and circularize radius via r_e,UV = r_e,UV^major * sqrt(q)",
  "failed_quote": "Finally we obtain an effective radius along the major axis r_e,UV^major and axis ratio q, and convert them to the circularized effective radius r_e,UV through r_e,UV ≡ r_e,UV^major sqrt(q)."
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "Compute f_obs = SFR_IR / (SFR_UV + SFR_IR) for individual galaxies and in 3 stellar mass bins via median image stacking of 3''-smoothed images scaled by (1+z)/d_L^2; compute Spearman rank correlation coefficients between Δf_obs and UV-dust spatial offset, size ratio, Σ_IR, and axis ratios",
  "failed_quote": "f_obs = SFR_IR / (SFR_UV + SFR_IR)"
 },
 {
  "path": "analysis_steps[5].method.evidence[1]",
  "value": "Compute f_obs = SFR_IR / (SFR_UV + SFR_IR) for individual galaxies and in 3 stellar mass bins via median image stacking of 3''-smoothed images scaled by (1+z)/d_L^2; compute Spearman rank correlation coefficients between Δf_obs and UV-dust spatial offset, size ratio, Σ_IR, and axis ratios",
  "failed_quote": "We divide the sample into three ranges with log_10 M_* [M_⊙] = [9.3 : 9.8], [9.8: 10.2] and [10.2: 10.9] so that the number of galaxies in each bin is similar. For the stacking analysis, we make the images with the taper scale of 2'' after shifting the phase center of the image to the central position of the [C II] emission (Ikeda et al. in prep.). Then we apply the CASA/imsmooth to unify the beam size to 3'' following the flux measurements in Section 3.2 and perform median stacking of the images."
 },
 {
  "path": "analysis_steps[5].key_parameters[0].evidence[0]",
  "value": "Stellar mass bins: log_10 M_* [M_⊙] = [9.3 : 9.8], [9.8: 10.2], [10.2: 10.9]; taper scale 2'', smoothed beam 3''; redshift scaling factor (1+z)/d_L^2",
  "failed_quote": "We divide the sample into three ranges with log_10 M_* [M_⊙] = [9.3 : 9.8], [9.8: 10.2] and [10.2: 10.9] so that the number of galaxies in each bin is similar."
 },
 {
  "path": "analysis_steps[5].key_parameters[0].evidence[1]",
  "value": "Stellar mass bins: log_10 M_* [M_⊙] = [9.3 : 9.8], [9.8: 10.2], [10.2: 10.9]; taper scale 2'', smoothed beam 3''; redshift scaling factor (1+z)/d_L^2",
  "failed_quote": "We take into account the redshift difference of the target galaxies by multiplying the factor of (1 + z)/d_L^2 to the image because our calculation from S_158µm to L_IR is proportional to the reciprocal of the factor."
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Dust continuum detection rate for log_10 M_* [M_⊙] > 9.7 = 89 %",
  "failed_quote": "The detection rate is 89% (16/18) in a stellar mass range of log_10 M_* [M_⊙] > 9.7 (Figure 1)."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Median stellar mass of dust-detected sample (log_10 M_*) = 10.1 dex (M_⊙)",
  "failed_quote": "The median stellar mass and SFR of the dust-detected and undetected sample are log_10 M_* [M_⊙] = 10.1, log_10 SFR [M_⊙ yr^-1] = 1.8 and log_10 M_* [M_⊙] = 9.5, log_10 SFR [M_⊙ yr^-1] = 1.4, respectively."
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Median SFR of dust-detected sample (log_10 SFR) = 1.8 dex (M_⊙ yr^-1)",
  "failed_quote": "The median stellar mass and SFR of the dust-detected and undetected sample are log_10 M_* [M_⊙] = 10.1, log_10 SFR [M_⊙ yr^-1] = 1.8 and log_10 M_* [M_⊙] = 9.5, log_10 SFR [M_⊙ yr^-1] = 1.4, respectively."
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Median infrared surface density (Σ_IR) of CRISTAL galaxies = 2.0e10 L_⊙ kpc^-2",
  "failed_quote": "The infrared surface densities of these galaxies (Σ_IR ~ 2.0 * 10^10 L_⊙ kpc^-2) are one order of magnitude lower than those of DSFGs that host compact central starbursts."
 },
 {
  "path": "results_numeric[5].evidence[1]",
  "value": "Median infrared surface density (Σ_IR) of CRISTAL galaxies = 2.0e10 L_⊙ kpc^-2",
  "failed_quote": "The median Σ_IR of the CRISTAL galaxies is 2.0 * 10^10 L_⊙ kpc^-2 and ~10 times smaller than that of the central compact star-forming regions of DSFGs or SMGs"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Average obscured fraction of multiple (merging) galaxy sample (<f_obs>_multiple) = 0.43 dimensionless",
  "failed_quote": "The average obscured fraction and SFR of the multiple galaxy sample (<f_obs>_multiple = 0.43^+0.03_-0.03, <log_10 SFR [M_⊙ yr^-1]>_multiple = 1.97^+0.60_-0.54) is higher than that of the single galaxy samples (<f_obs>_single = 0.34^+0.03_-0.03, <log_10 SFR [M_⊙ yr^-1]>_single = 1.58^+0.10_-0.11)."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Average obscured fraction of single (isolated) galaxy sample (<f_obs>_single) = 0.34 dimensionless",
  "failed_quote": "The average obscured fraction and SFR of the multiple galaxy sample (<f_obs>_multiple = 0.43^+0.03_-0.03, <log_10 SFR [M_⊙ yr^-1]>_multiple = 1.97^+0.60_-0.54) is higher than that of the single galaxy samples (<f_obs>_single = 0.34^+0.03_-0.03, <log_10 SFR [M_⊙ yr^-1]>_single = 1.58^+0.10_-0.11)."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Spearman correlation coefficient between Δf_obs and UV-dust spatial offset = -0.58 dimensionless",
  "failed_quote": "We find a negative correlation between Δf_obs and the spatial offset within 1σ uncertainty of the correlation coefficient of ρ_corr = -0.58^+0.30_-0.20 with a p-value of 0.082."
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "Typical star-forming galaxies at z = 4–6 have ~1 dex lower L_IR and ~10 times smaller Σ_IR than DSFGs/SMGs, indicating moderate, disk-wide star formation rather than compact central starbursts.",
  "failed_quote": "The infrared surface densities of these galaxies (Σ_IR ~ 2.0 * 10^10 L_⊙ kpc^-2) are one order of magnitude lower than those of DSFGs that host compact central starbursts."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "The average obscured fraction of star formation (f_obs) correlates positively with stellar mass, showing no clear evolution from z = 0–2.5 at M_* < 10^10 M_⊙ but a possible decrease at M_* > 10^10 M_⊙ compared to z = 0–2.5.",
  "failed_quote": "Our results support that the obscured fraction at the range of M_* < 10^10 M_⊙ does not show clear evolution from z = 0–2.5 (Magdis et al. (2012) and Béthermin et al. (2015)) to z ~ 5. On the other hand, we find the possible evolution of the obscured fraction from z ~ 5 to z ~ 0–2.5 at the range of M_* > 10^10 M_⊙, and that implies a build-up of dust in massive galaxies."
 },
 {
  "path": "findings_qualitative[2].evidence[1]",
  "value": "Dust continuum effective radii are on average ~2 times more extended than rest-frame UV radii, contrary to Illustris TNG50 predictions.",
  "failed_quote": "These results are not consistent with the Illustris TNG50 simulation which expects r_e,dust / r_e,UV ~ 0.25–0.5 in the stellar mass range of the CRISTAL galaxies."
 },
 {
  "path": "findings_qualitative[3].evidence[1]",
  "value": "CRISTAL galaxies follow the stellar mass-size relation of late-type galaxies (LTGs) and Lyman-break galaxies (LBGs) rather than early-type galaxies (ETGs), indicating they are growing their stellar disks via global star formation.",
  "failed_quote": "Our result suggests that typical star-forming galaxies with M_* ~ 10^10 M_⊙ might be still growing their disks via global star formation."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "Typical star-forming galaxies at z = 4–6 form stars moderately throughout the entirety of their disks, expanding their stellar disks rather than building compact central bulges.",
  "failed_quote": "The infrared surface densities of these galaxies (Σ_IR ~ 2.0 * 10^10 L_⊙ kpc^-2) are one order of magnitude lower than those of DSFGs that host compact central starbursts. On the basis of the comparable contribution of dust-obscured and dust-unobscured star formation along with their similar spatial extent, we suggest that typical star-forming galaxies at z = 4–6 form stars throughout the entirety of their disks."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "The TNG50 prediction of compact dust relative to UV is refuted for these galaxies; dust emission is ~2 times more extended than rest-frame UV emission.",
  "failed_quote": "The effective radii of the dust continuum (r_e,dust) are comparable or ~ 2 times larger than that of the UV continuum (r_e,UV) in the individual comparison whereas the dust emission originates the dust heated by UV radiation from massive O/B type stars. These results are not consistent with the Illustris TNG50 simulation which expects r_e,dust / r_e,UV ~ 0.25–0.5 in the stellar mass range of the CRISTAL galaxies."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "f_obs correlates positively with stellar mass at z = 4–6, with no clear evolution from z = 0–2.5 below 10^10 M_⊙ and a possible decrease above 10^10 M_⊙ suggesting ongoing dust build-up in massive galaxies.",
  "failed_quote": "Our results support that the obscured fraction at the range of M_* < 10^10 M_⊙ does not show clear evolution from z = 0–2.5 (Magdis et al. (2012) and Béthermin et al. (2015)) to z ~ 5. On the other hand, we find the possible evolution of the obscured fraction from z ~ 5 to z ~ 0–2.5 at the range of M_* > 10^10 M_⊙, and that implies a build-up of dust in massive galaxies."
 },
 {
  "path": "claims[3].evidence[1]",
  "value": "Inhomogeneous dust reddening, merger-induced boosts in obscured star formation, and central dust concentration partially explain the scatter in f_obs.",
  "failed_quote": "We find a negative correlation between Δf_obs and the spatial offset within 1σ uncertainty of the correlation coefficient of ρ_corr = -0.58^+0.30_-0.20 with a p-value of 0.082."
 },
 {
  "path": "claims[3].evidence[2]",
  "value": "Inhomogeneous dust reddening, merger-induced boosts in obscured star formation, and central dust concentration partially explain the scatter in f_obs.",
  "failed_quote": "The average obscured fraction and SFR of the multiple galaxy sample (<f_obs>_multiple = 0.43^+0.03_-0.03, <log_10 SFR [M_⊙ yr^-1]>_multiple = 1.97^+0.60_-0.54) is higher than that of the single galaxy samples (<f_obs>_single = 0.34^+0.03_-0.03, <log_10 SFR [M_⊙ yr^-1]>_single = 1.58^+0.10_-0.11)."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[2]",
  "value": "A single FIR SED template (T_dust ~ 42 K) is assumed for all galaxies due to single-band ALMA continuum detections; a T_dust variation of ~20 K changes L_IR by ~0.25 dex and f_obs by ~0.15.",
  "failed_quote": "A variation of T_d ~ 20 K changes infrared luminosities with ΔL_IR ~ 0.25 dex and the obscured fractions with Δf_obs ~ 0.15."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Because the parent sample selection is based on bright UV continuum and emission lines, heavily obscured dusty galaxies are likely missed.",
  "failed_quote": "Note that as our sample selection is originally based on a bright UV continuum and emission lines, it likely led to missing obscured dusty galaxies (e.g., Franco et al. 2018; Yamaguchi et al. 2019)."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[0]",
  "value": "Axis ratios in the dust continuum cannot be constrained for most galaxies due to moderate S/N (S/N ~ 5), requiring an assumption of a circular exponential disk and preventing direct dust inclination measurements.",
  "failed_quote": "As the CRISTAL galaxies typically do not have high S/N (S/N ~ 5) in the dust emission (Table 1), the axis ratio (q) is not well constrained in most galaxies."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[1]",
  "value": "Axis ratios in the dust continuum cannot be constrained for most galaxies due to moderate S/N (S/N ~ 5), requiring an assumption of a circular exponential disk and preventing direct dust inclination measurements.",
  "failed_quote": "Moreover, only a few CRISTAL galaxies have constraints on the axis ratios in dust emission. The current data quality is not sufficient to discuss the possibility that inclinations explain the variation in f_obs."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[0]",
  "value": "Individual visibility size measurements for sources with 4.4 <= S/N <= 5.5 have large scatter in Monte Carlo simulations, especially for output sizes < 0.4''.",
  "failed_quote": "However, careful treatment of individual sizes of the sources with 4.4 <= S/N <= 5.5 is needed as the output sizes of these sources show large scatters from input sizes (size_inp /size_fit = 0.07^+0.67_-0.26) especially in the case that output sizes are less than 0.4'' (size_inp /size_fit = 0.09^+0.83_-0.32)."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "ALMA project codes are listed in Acknowledgements; photometric catalogs (COSMOS2015, ASTRODEEP) are stated as publicly available.",
  "failed_quote": "We cross-match positions of the CRISTAL galaxies to publicly available photometric catalogs in COSMOS (COSMOS2015 catalog, Laigle et al. 2016) and GOODS-S fields (ASTRODEEP catalog, Merlin et al. 2021)."
 }
]
```
