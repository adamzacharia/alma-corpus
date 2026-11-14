# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691A.248L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# A&A, 691, A248 (2024)https://doi.org/10.1051/0004-6361/202348341 Astronomy
### &
# ⃝c The Authors 2024 Astrophysics

## **The role of stellar mass in the cosmic history of star formation as** **seen by Herschel and ALMA**

L. Leroy [1][,][⋆], D. Elbaz [1], B. Magnelli [1], C. Gómez-Guijarro [1], E. Daddi [1], M. Xiao [1,2], and M. Dickinson [3]


1 Université Paris Cité, Université Paris-Saclay, CEA, CNRS, AIM, F-91191 Gif-sur-Yvette, France
2 Department of Astronomy, University of Geneva, Chemin Pegasi 51, 1290 Versoix, Switzerland
3 NSF’s National Optical-Infrared Astronomy Research Laboratory, 950 N. Cherry Ave., Tucson, AZ 85719, USA


Received 20 October 2023 / Accepted 27 September 2024


**ABSTRACT**


_Aims_ . We explore the contribution of galaxies, as a function of their stellar mass, to the cosmic star formation history (CSFH). In
order to avoid uncertain extrapolations of the infrared luminosity function, which is often polluted by the contribution of starbursts,
we base our analysis on stellar mass. Attenuation by dust is accounted for thanks to the combination of deep surveys by _Herschel_ and
the Atacama Large Millimeter/submillimeter array (ALMA).
_Methods._ We combined for the first time the deepest _Herschel_ (GOODS-South, GOODS-North, COSMOS and UDS) and ALMA
(GOODS-South) surveys. We constrained the star formation rate (SFR), dust mass ( _M_ dust ), dust temperature ( _T_ dust ) and gas mass
( _M_ gas ) of galaxies as a function of their stellar mass ( _M_ ⋆ ) from _z_ ∼ 5 to _z_ ∼ 0 by performing a stacking analysis of over 128 000
_Hubble_ Space Telescope (HST) _H_ -band selected galaxies. We studied the evolution of the star formation efficiency of galaxies as a
function of redshift and _M_ ⋆ .
_Results_ . We show that the addition of ALMA to _Herschel_ allows us to reach lower _M_ ⋆ and higher redshifts. We confirm that the
SFR- _M_ ⋆ star formation main sequence (MS) follows a linear evolution with a slope close to unity with a bending at the high-mass
end at _z_ < 2. The mean _T_ dust of MS galaxies evolves linearly with redshift, with no apparent correlation with _M_ ⋆ . We show that, up
to _z_ ∼ 5, massive galaxies (i.e. _M_ ⋆ ≥ 10 [10] _M_ ⊙ ) account for most of the total SFR density (ρ SFR ), while the contribution of lowermass galaxies (i.e. _M_ ⋆ ≤ 10 [10] _M_ ⊙ ) is rather constant. We compare the evolution of star-forming galaxy (SFGs) to the cosmological
simulation TNG100. We find that TNG100 exhibits a noticeable difference in the evolution of the CSFH, that is, the marked evolution
of massive galaxies found in the observations appears to be smoothed in the simulation, possibly due to feedback that is too efficient.
In this mass complete analysis, _H_ -dropout (also called HST-dark) galaxies account for ∼23% of the CSFH in massive galaxies at
_z_    - 3. Finally, we find hints that the star formation efficiency of distant galaxies ( _z_ = 3–5) is stronger (shorter depletion time) as
compared to low-redshift galaxies.


**Key words.** galaxies: evolution – galaxies: high-redshift – galaxies: photometry – galaxies: star formation –
infrared: galaxies – submillimeter: galaxies



**1.** **Introduction**


The evolution of the star formation rate density (ρ SFR ) over
time follows a gradual growth from the Big Bang to cosmic
noon (i.e. _z_ ∼ 2), followed by a continuous decline by a
factor ∼10 to the present day (e.g. Madau & Dickinson 2014;
Bouwens et al. 2015b; Liu et al. 2018; Leslie et al. 2020 and
Schreiber et al. 2015, hereafter S15). This evolution alone raises
many questions about the growth and death of galaxies. For
example, the contribution to the ρ SFR of galaxies of different stellar masses ( _M_ ⋆ ), or the ρ SFR at high redshift (i.e. _z_ ≥ 4) are
still largely uncertain. Our understanding of the high-redshift
part (i.e. _z_ ≥ 4) is mainly built from the ultraviolet (UV),
and then deduced by correcting these UV measurements from
dust attenuation (e.g. Bouwens et al. 2012b,a; Schenker et al.
2013; Bouwens et al. 2015a,b; Oesch et al. 2018). However, it
has recently been claimed, through studies using dust-unbiased
measurements (i.e. radio or far-infrared emission), that ρ SFR is
actually higher, by a factor of two to six, at high redshift (i.e.
_z_ ≥ 4, e.g. Rowan-Robinson et al. 2016; Novak et al. 2017;


⋆ Corresponding author; `[lucas.a.leroy@gmail.com](mailto: lucas.a.leroy@gmail.com)`



Lagache 2018; Gruppioni et al. 2020; Khusanova et al. 2021)
compared to Madau & Dickinson (2014).
In order to deduce the cosmic star formation history, it
is necessary to correctly infer the star formation rate (SFR)
of galaxies. It has been shown that the SFR of star-forming
galaxies (SFGs) is positively correlated with their stellar mass
(e.g. Elbaz et al. 2007; Daddi et al. 2007; Whitaker et al. 2012,
2014; Speagle et al. 2014; S15; Lee et al. 2015; Delvecchio et al.
2021; Leslie et al. 2020; Popesso et al. 2023) with a small
scatter of ∼0.2−0.3 dex (e.g. Elbaz et al. 2007; Whitaker et al.
2012; Speagle et al. 2014; S15). This correlation is called the
main sequence (MS; Noeske et al. 2007) of SFGs. Although
the specifics of this correlation remain a matter of debate,
most recent studies tend to favour a linear MS in logarithmic space with a bending appearing at high _M_ ⋆ and for
_z_ ≤ 2−3 (e.g. Whitaker et al. 2014; Magnelli et al. 2014; S15;
Delvecchio et al. 2021; Leslie et al. 2020), rather than a strictly
linear correlation between SFR and _M_ ⋆ (e.g. Whitaker et al.
2012; Speagle et al. 2014).
The fraction of star formation obscured by dust is still highly
uncertain at high redshift (i.e. _z_ ≥ 3), as it could be higher
up to a factor of ten above unobscured formation (Casey et al.
2018). As the correction factors for dust extinction are quite


A248, page 1 of 25



[Open Access article, published by EDP Sciences, under the terms of the Creative Commons Attribution License (https://creativecommons.org/licenses/by/4.0),](https://www.edpsciences.org)
which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.
[This article is published in open access under the Subscribe to Open model.](https://www.aanda.org/subscribe-to-open-faqs) [Subscribe to A&A to support open access publication.](mailto:subscribers@edpsciences.org)

Leroy, L., et al.: A&A, 691, A248 (2024)



large (e.g. Calzetti et al. 1994; Madau et al. 1998; Steidel et al.
1999), this leads studies to combine SFR from the UV (uncorrected for dust extinction) and SFR deduced directly from the
infrared (IR) (e.g. S15; Delvecchio et al. 2021) when seeking
the total SFR and ρ SFR . Although most of them are based on
_Hubble_ Space Telescope (HST) detected catalogues to infer the
evolution of the SFR, they do not take into account the contribution of so-called HST-dark galaxies in the study of the ρ SFR .
_H_ -dropout (Wang et al. 2019), HST-dark (Zhou et al. 2020)
or optically dark and faint (Gómez-Guijarro et al. 2022a;
Xiao et al. 2023b) galaxies, represent massive and highly
obscured galaxies usually detected with a low significance or
not at all in the optical. Although initially thought to be a
marginal population with little effect on the ρ SFR, over time it
has been shown that such obscured galaxies could significantly
contribute to the ρ SFR above _M_ ⋆ ∼ 10 [10][.][5] _M_ ⊙ (e.g. Wang et al.
2019; Xiao et al. 2023b).
Since the Atacama Large Millimeter/submillimeter array
(ALMA) came online in 2013n it has enabled large and deep
surveys, with a better resolution, in the millimetre and submillimetre range (e.g. Franco et al. 2018; Gómez-Guijarro et al.
2022a). Studies can now combine higher-quality millimetre and
submillimetre measurements with IR measurements. ALMA has
proven to be a powerful tool to probe the gas content of galaxies (e.g. Scoville et al. 2014; Groves et al. 2015; Scoville et al.
2016; Schinnerer et al. 2016; Kaasinen et al. 2019; Liu et al.
2019; Millard et al. 2020; Magnelli et al. 2020; Wang et al.
2022), and developing our global understanding of high-redshift
galaxies (see Hodge & da Cunha 2020 for a review). Studies
have also been using the discrete ALMA archive pointings to
study the ρ SFR (e.g. Traina et al. 2024).
Spatially resolved studies show that the SFR mostly correlates with the molecular gas (H 2 ) surface density, and very little
with the atomic gas (HI) surface density (e.g. Bigiel et al. 2008;
Leroy et al. 2008). The gas content of galaxies is usually probed
through CO emission lines because of the difficulty of directly
observing the H 2 content (see Bolatto et al. 2013 for a review).
However, other techniques have been developed to infer the gas
content of galaxies through the study of multi-wavelength dust
spectral energy distribution (SED) fits, and by applying the gasto-dust ratio to infer gas masses ( _M_ gas ) from dust masses ( _M_ dust ;
e.g. Leroy et al. 2011; Magdis et al. 2011, 2012; Magnelli et al.
2012; Rémy-Ruyer et al. 2014; Genzel et al. 2015).
By combining the SFR and the gas content of galaxies, we
can infer the star formation efficiency ( _S FE_ ≡ _S FR_ / _M_ gas ) of
galaxies, which gives a straightforward indicator of how galaxies form stars at a different moment in cosmic time. The SFE has
been shown to evolve quickly at a low redshift (i.e. 0 ≤ _z_ ≤ 1),
but to be rather constant at higher redhsifts (i.e. _z_ - 1; e.g.
Saintonge et al. 2017; Scoville et al. 2017; Tacconi et al. 2018;
Liu et al. 2019; Wang et al. 2022). Another way of looking at
this is to use the Kennicutt-Schmidt relation (Kennicutt 1998b).
This relation has been shown to follow the power-law correlation between the SFR and gas surface density with a slope
of ∼1.0−1.5 (e.g. Kennicutt 1998b; de los Reyes & Kennicutt
2019; Wang et al. 2022).
In this paper, combining _Spitzer_, _Herschel_ and ALMA, we
study the evolution of galaxy properties from _z_ ∼ 0 to 5 through
stacking on four fields: COSMOS, UDS, GOODS-South, and
GOODS-North. We try to answer a few open questions about
the evolution and global history of galaxies. In particular, we
seek to constrain the main sequence, ρ SFR at a high redshift
(i.e. _z_ ≥ 4), the different contributions to ρ SFR as a function of
_M_ ⋆, and the impact of the _H_ -dropout galaxy population on the


A248, page 2 of 25



**Table 1.** Number of galaxies in the final sample from each field.


Field Number of galaxies Area (arcmin [2] )


GOODS South 26 811 134

GOODS North 35 322 142

COSMOS 34 124 388

UDS 32 695 412

Total 128 952 1077

GOODS-ALMA 8659 69


properties of galaxies as a whole. A similar study using _Spitzer_
and _Herschel_ measurements has been carried out by S15. However, the addition of ALMA measurements to _Herschel_ using
stacking has not been carried out yet. The reason is that this
requires access to an extensive study programme on ALMA.
This has only recently been possible thanks to blind surveys
such as the GOODS-ALMA survey (Franco et al. 2018, 2020;
Gómez-Guijarro et al. 2022a). A summary of the data used in
this study is given in Sect. 2. The stacking method is described
in Sect. 3. Section 4 is devoted to the SED fitting procedure.
Section 5 reviews the properties of galaxies that can be deduced
from this analysis. Sections 6 and 7 present the cosmic star formation history and the cosmic evolution of the gas mass density
deduced for this work, respectively. We interpret and discuss our
results in a global cosmological context in Sect. 8, and in Sect. 9
we summarise the main results and conclusions.
For this work, we adopted a Salpeter (1955) initial mass
function (IMF) and the cosmological parameters (Ω M, Ω Λ,
_h_ ) = [0.30, 0.70, 0.70]. We used a factor of 1.7 to convert _M_ ⋆
and SFR from a Chabrier (2003) to a Salpeter (1955) IMF
whenever necessary (e.g. Reddy et al. 2006; Santini et al. 2012;
Elbaz et al. 2018; Gómez-Guijarro et al. 2022b). When mentioned, magnitudes are in the AB system, such that _M_ AB =
23.9−2.5 log 10 ( _S_ ν [µJy]).


**2.** **Sample and observations**


_2.1._ _Sample_


In this study, we worked from catalogues of _H_ -band selected
SFGs on four fields: GOODS-South, GOODS North, COSMOS and UDS. We used the ultra-deep _H_ -band catalogue of the CANDELS-HST team (Grogin et al. 2011;
Koekemoer et al. 2011) for GOODS-South (Guo et al. 2013),
COSMOS (Nayyeri et al. 2017) and UDS (Galametz et al. 2013)
fields, while in GOODS-North we use the catalogue from
Barro et al. (2019). The 5σ limiting magnitude range from _H_ ∼
27.4 to 29.7 for GOODS-South, _H_ ∼ 27.4 to 28.8 for COSMOS,
_H_ ∼ 27.1 to 27.6 for UDS, and _H_ ∼ 27.8 to 28.7 for GOODSNorth. The photometric redshifts and _M_ ⋆ of the galaxies in these
catalogues were derived in S15 (GOODS-South, COSMOS and
UDS) and Barro et al. (2019) (GOODS-North). Photometric
data were fitted up to IRAC 4.5 µm, with _EAZY_ (Brammer et al.
2008), by assuming a delayed exponentially declining star formation history with the Bruzual & Charlot (2003) stellar population synthesis model. The SFGs are UVJ selected, following the
definition from Muzzin et al. (2013). The final number of SFGs
in the sample is given in Table 1. _H_ -dropout galaxies are by definition not included in these samples, as they are not detected in
_H_ -band. However, we used the sample from Wang et al. (2019)
to add and discuss their impact in any necessary analyses.

_2.2._ _Observations_



Leroy, L., et al.: A&A, 691, A248 (2024)


**Table 2.** Number of galaxies in each bin of _M_ ⋆ and redshift.



Observations with _Spitzer_ -MIPS at 24 µm include maps of
the COSMOS field (PI: D. Sanders; LeFloc’h et al. 2009),
the GOODS-South and GOODS-North fields (GOODS Legacy
programme; PI: M. Dickinson), and the UDS field (SpUDS
_Spitzer_ Legacy programme; PI: J. Dunlop). The _Herschel_
PACS and SPIRE maps of the four fields come mainly from
the CANDELS- _Herschel_ programme. The PACS GOODSNorth and GOODS-South maps are the combined _Herschel_ PACS data from the PEP (Lutz et al. 2011) and GOODS_Herschel_ (Elbaz et al. 2011) programmes, as described in
Magnelli et al. (2013). For ALMA, we used the 1.13 mm lowresolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam [−][1], Gómez-Guijarro et al. 2022a),
within the GOODS-South field with the 1 [′′] . 1 circularised point
spread function (PSF) full width half maximum (FWHM). We
note that there is a global and local offset between the position of sources in the ALMA and HST images (Franco et al.
2018, 2020). We corrected them using the offsets provided by
Franco et al. (2020).


**3.** **Stacking**


Our method consists in stacking several images of galaxies on
top of each other in order to increase the overall signal-to-noise
ratio (S/N). The result of a stacking procedure is the mean or
median flux for all galaxies stacked together. The main advantage of this method is to be able to recover reliable flux measurements for populations of galaxies whose S/N is too low when
studied individually. In practice, this means being able to measure the properties of galaxies with lower _M_ ⋆ and higher redshift. An effective way to take advantage of the stacking method
is to group galaxies into sub-populations with similar properties.
To this end, in this study, we stack our sample of galaxies over
different redshift and _M_ ⋆ bins. The total numbers of galaxies per
bin are displayed in the Table 2.
In order to access the completeness of the catalogues that
we stacked in this study, we followed the method of S15. In
summary, we assumed, for each redshift bin, that the observed
luminosity at 1.6 µm ( _L_ 1 [obs] .6 µm [)] [can] [be] [related] [to] _[M]_ [⋆] [simply] [by]
_M_ ⋆ = _C_ × _L_ 1 [α] .6 µm−obs [with] [a] [scatter.] [The] [relation] [and] [disper-]
sion are fitted from the _H_ -band photometry of the catalogues. We
derive the completeness from Monte Carlo simulations by generating, from a uniform redshift distribution in the redshift bin
and a given _M_ ⋆, the corresponding _L_ 1.6 µm−obs taking into account
the dispersion, and comparing it to the corresponding _H_ -band
detection limit for each catalogue. We assume that catalogues
are complete when the completeness is above 90% (S15). The
corresponding _M_ ⋆ [90%], above which all catalogues are assumed
to be mass complete, are listed in Table 3. All but two of the
bins which yield significant detection (i.e. with _S_ / _N_ ≥ 3σ in
at least one band from 24 µm to 1.13 mm) considered in this
study are mass complete: for 9.5 ≤ log 10( _M_ ⋆ / _M_ ⊙ ) ≤ 10.0
at 2.3 ≤ _z_ ≤ 3.1, and 10.0 ≤ log 10( _M_ ⋆ / _M_ ⊙ ) ≤ 10.5 at
3.1 ≤ _z_ ≤ 3.9. The latter bin is, however, almost mass complete
as _M_ ⋆ [90%] = 10 [10][.][1] _M_ ⊙ and is consistent with a _M_ ⋆ [90%] = 10 [10] _M_ ⊙
within the uncertainties of the method used to compute the completeness.
The completeness computed in this paper is determined
assuming that the _H_ -band is a good proxy for the stellar mass.
This hypothesis may however become less robust at high redshifts (i.e. _z_ - 3). To assess whether our derivation of the completeness limit remains relevant for the redshift range 3 < _z_ < 5,



**Notes.** Number of galaxies in each bin of _M_ ⋆ and redshift for the stacking in the _Herschel_ 100 µm, 160 µm, 250 µm, 350 µm and 500 µm bands,
and for the stacking in the ALMA band are displayed in the top and bottom row of each cell, respectively. The two axes represent the boundaries of the bins in redshift and _M_ ⋆ . Bins with at least a FIR, and a submillimeter stack detection (i.e. with a _S_ / _N_ ≥ 3σ in at least one band)
are highlighted in faded blue and red, respectively. Bins that are mass
complete are noted with a black bar.


**Table 3.** Completeness limits.


Redshift bin log 10 ( _M_ ⋆ [90%] / _M_ ⊙ ) _H_ -dropout/arcmin [2]


0.1 ≤ _z_ ≤ 0.4 7.5 0
0.4 ≤ _z_ ≤ 0.7 7.9 0
0.7 ≤ _z_ ≤ 1.0 8.1 0
1.0 ≤ _z_ ≤ 1.3 8.2 0
1.3 ≤ _z_ ≤ 1.8 8.6 0
1.8 ≤ _z_ ≤ 2.3 9.2 1.67 × 10 [−][3]

2.3 ≤ _z_ ≤ 3.1 9.7 1.17 × 10 [−][2]

3.1 ≤ _z_ ≤ 3.9 10.1 [(][∗][)] 3.67 × 10 [−][2]

3.9 ≤ _z_ ≤ 5.0 10.0 3 × 10 [−][2]


**Notes.** Stellar mass for which we obtain a completeness of 90% in
the _H_ -band catalogues used in this work; and the number of _H_ dropout/arcmin [2] that can be found at these redshifts from Wang et al.
(2019). [(][∗][)] Consistent with a _M_ ⋆ [90%] = 10 [10] _M_ ⊙ within the uncertainties of
the method used to compute the completeness.


we looked at a deep JWST-NIRCAM survey of the EGS field
(Gómez-Guijarro et al. 2023). We found that 89.7% of the galaxies with log 10 ( _M_ ⋆ / _M_ ⊙ ) - 10 (209 galaxies detected, 233 overall) detected in the JWST bands are also detected in the HST
_H_ -band (the 5σ limiting magnitude is 27.37 in CEERS – see
Gómez-Guijarro et al. 2023, Sect. 2.2 – that is comparable to
27.4, 27.4, 27.1, 27.8 in the GOODS-South, COSMOS, UDS
GOODS-North fields respectively). This is consistent with our
90% completeness of log 10 ( _M_ ⋆ [90%] / _M_ ⊙ ) ∼ 10 for 3.1 ≤ _z_ ≤ 5 and
3.9 ≤ _z_ ≤ 5.0, which gives us confidence that our sample is not
strongly biased.
We choose to use mean stacking for our work, rather
than median stacking. Indeed, although median stacking better


A248, page 3 of 25

**Table 4.** Clustering bias correction factors.



Leroy, L., et al.: A&A, 691, A248 (2024)


_3.1._ _Spitzer_



Wavelength (µm) Correction


100 0% [+] − [7%] 7%
160 3% [+] − [9%] 8%
250 8% [+] − [12%] 8%
350 13% [+] − [12%] 10%
500 25% [+] − [19%] 18%


**Notes.** The clustering bias correction factors in this Table are from S15.


suppresses secondary sources in the stacked image (i.e. bright
sources which are close to the stacked target and might appear
in the final stacked image), it has been shown that it also yields
to systematically biased measurements at low S/N or in the presence of a flux distribution skewed towards low or high values
(White et al. 2007; S15). It comes from the fact that the median
(⟨.⟩) is not a linear operation: ⟨ _a_ + _b_ ⟩ � ⟨ _a_ ⟩ + ⟨ _b_ ⟩. As shown
in S15, correcting for these systematic biases involves making
strong assumptions on the actual flux distribution of the stacked
sources, which is non-trivial and very uncertain. On the contrary,
the mean stack gives us access to the total flux in the stack, which
we currently miss to infer ρ [IR] SFR [.]
During the stacking procedure, it is possible to treat detected
and undetected galaxies separately. The main way to do this is to
stack only the undetected sources on the residual map, and then
add them to the fluxes of the detected galaxies via a weighted
mean (e.g. Magnelli et al. 2009). Although this method reduces
the confusion noise of faint sources and removes most of the contamination from bright neighbours, it can also introduce some
biases (S15). Following S15, we have therefore chosen to treat
detected and undetected sources in the same way for consistency
(i.e. directly from the image and not from the residual). The contamination of bright neighbours is dealt with later in the study
(see Sect. 3.2).
We noticed the presence of a global background gradient in
most _Herschel_ images. In order to deal with it, we have decided
to rotate the stacked postage stamp images successively by 90 [◦] .
The resulting flux density in each stacked image was
obtained via standard aperture measurements or PSF fitting
method (see detail for each wavelength in Sects. 3.1, 3.2 and
3.3). The corresponding S/N was then derived using a simple
Monte Carlo approach, that is, _S_ / _N_ = _S_ ν /σ MC, where _S_ ν is the
flux density measured at the centre of the stacked image within
an aperture of radius, _r_, while σ MC is the standard deviation of
the signal in 100 circles, of the same radius _r_, randomly positioned on the edges of the stacked stamp. Depending on the
method used to compute the flux, _r_ corresponds to either the
radius used for the aperture measurement method, or the radius
within which the PSF fitting method was performed.
In addition to this photometric noise, there is an uncertainty
in the recovered flux density due to the intrinsic dispersion of the
underlying stacked population (i.e. all galaxies in the stack do
not have the exact same flux density). This flux dispersion can be
quantified using a bootstrap analysis (e.g. S15). The method consists in repeating several time the full stacking and flux density
measurement process, picking, for each realisation, the galaxies from the origin sample, with replacement, until the number
of galaxies in the original sample is reached. In this study, we
compute a 100 runs. The error is then deduced from the standard
deviation of the computed flux densities for this bin.


A248, page 4 of 25



As the 24 µm MIPS- _Spitzer_ map (∼5 [′′] . 8 PSF FWHM) has a better
resolution than _Herschel_ -PACS (∼7 [′′] and ∼ 11 [′′] . 3 PSF FWHM at
100 µm and 160 µm, respectively), we do not expect the clustering bias (see Sect. 3.2) to be a dominant effect on the stacked
stamp. The fluxes are calculated using a classical aperture photometry method. The aperture is chosen to be 4 pixels (i.e. 4 [′′] . 8)
in radius, which contains about ∼60% of the total flux for a point

source.


_3.2._ _Herschel_


When stacking galaxies, a ‘clustering bias’ can occur due to the
neighbouring galaxies of the main stacking targets. Such contamination from neighbouring sources can become significant
when the size of the PSF becomes comparable to the typical cluster length of SFGs. It has been shown that the clustering bias has
a non-negligible impact on the results when stacking galaxies in
the _Herschel_ bands (e.g. Bavouzet et al. 2008; Béthermin et al.
2010; Kurczynski & Gawiser 2010; Bourne et al. 2012;
Béthermin et al. 2012; Viero et al. 2013; Béthermin et al. 2014;
S15; Béthermin et al. 2015; Delvecchio et al. 2021) due to the
large PSF of _Herschel_ . Correcting for this bias is crucial to
accurately measure the peak of SED of SFGs, as this bias tends
to cause the fluxes of _Herschel_ to be increasingly overestimated
with increasing wavelength (as the size of the PSF increases
with the wavelength).
To mitigate this clustering signal contamination, we choose
to follow the method presented in S15. It consists in fitting only
a PSF and a local background term:


_S_ ( _x_, y) = ϕ × _PS F_ ( _x_, y) + ε, (1)


where ϕ and ε are the normalisation of the source flux and background, respectively. The fit is performed on a fixed aperture of
radius of 0.9×FWHM, as this was found to minimise the clustering contamination to ϕ (S15). The clustering bias signal is in this
case largely included in the background term. Nevertheless, even
with this radius the contamination of ϕ is not null and we still
need to apply a correction for what remains of the clustering signal in the mean flux term (ϕ). The correction factors were calculated by simulating the stacking procedure on mock images (see
S15 for more details). The correction factors of S15 are listed in
Table 4. For the PACS maps, we used the truncated PSF derived
from Vesta, while for _Herschel_ -SPIRE the PSF is assumed to be
Gaussian with a FWHM of 18 [′′] . 15, 25 [′′] . 15 and 36 [′′] . 3 respectively
at 250, 350 and 500 µm according to Griffin et al. (2010) (see
also Shirley et al. 2021).
Finally, for _Herschel_ -PACS, it was shown (Popesso et al.
2012; Magnelli et al. 2013) that the high-pass filter data reduction technique that was used to remove low-frequency noise in
the maps could induce an underestimation of the photometric
measurements of the unmasked faint sources. It was shown in
Popesso et al. (2012) that a correction factor of 17%, and 10%
should be taken into account when stacking undetected faint,
and detected, sources in the PACS maps (100 µm and 160 µm),
respectively.


_3.3._ _ALMA_


For the purpose of this study, we decided to work in the image
plane when dealing with ALMA. Another option would have
been to work in the _u_ v plane (i.e. in Fourier space), as ALMA
provides us with measurements in the _u_ v space. Although this

Leroy, L., et al.: A&A, 691, A248 (2024)



may give more robust results, since we do not need to go through
the conversion between the _u_ v plane and the image plane first, it
is very computationally intensive. Furthermore, on few test bins
we only observed a 10% difference between fluxes calculated
from stacks in the _u_ v and image planes. We decided not to stack
directly in the _u_ v plane but in the image plane in order to save
computing time as this should not impact the results of this study.
As the ALMA 1.1mm map has a much better resolution
(∼1 [′′] . 1 PSF FWHM; which is comparable to typical sizes of individual SFGs, Suess et al. 2019; Wang et al. 2022) than _Herschel_ PACS (∼7 [′′] and ∼11 [′′] . 3 PSF FWHM at 100 µm and 160 µm,
respectively), the clustering bias is negligible on the stacked
stamp. Due to the high angular resolution of the ALMA data,
and to possible small offsets between the optical centroids (on
which our stack positions are based) and millimetre centroids,
the stacked images are extended on scales larger than that of the
ALMA PSF. However, this has no significant impact of the measure flux density via the aperture photometry method. To measure ALMA flux densities, we applied an aperture photometry
within a radius of 1 [′′], containing 85% of the total flux density
(i.e. _S_ AP [PSF] [/] _[S]_ [ PSF] tot [=][ 0][.][85).]


**4.** **SED fitting**


_4.1._ _SED fitting procedure_


One of the objectives of this paper is to retrieve several properties such as SFR, dust temperature ( _T_ dust ), dust masses and
gas masses from our far-infrared (FIR) to submillimetre stacking analysis, and compare them to the literature. We performed
an SED fit from the measured fluxes for each bin of redshift and
_M_ ⋆ . Because we do not have many points on the FIR at low
_M_ ⋆ and high redshifts, we used the library from Schreiber et al.
(2018, hereafter S18), which is well suited for our study given its
small number of free parameters. Choosing a model with more
parameters, such as Draine & Li (2007) and Draine et al. (2014),
would imply fixing parameters on some bins. The library of S15
is calibrated on galaxies from _z_ = 0.5 to _z_ = 4, which allows to
have a realistic SED while reducing the number of free parameters. We have assumed a form of SED that we would expect for
the main sequence galaxies, and no active galactic nuclei (AGN)
contribution to the stacked SED.
To fit the SED, we only considered fluxes with _S_ / _N_ ≥ 3.
Stacked flux measurements with _S_ / _N_ < 3 are replaced by conservative 5σ upper limits. At _z_ - 4 MIPS-24 stacked fluxes, if
available, have been transformed to 5σ upper limits as they are
no longer dominated by dust and polycyclic aromatic hydrocarbon (PAH) emissions, but rather by stellar emission. From these
SED fits, we measured the corresponding infrared luminosity
( _L_ IR ) by integrating the best-fit SED in the range 8–1000 µm rest
frame. The error on _L_ IR was obtained by varying their stacked
photometry randomly within their uncertainties.
The _T_ dust can be defined in different ways (i.e. weighted
by mass or luminosity). The luminosity weighted _T_ dust [L] [,] [for] [the]
library from S18, is calculated from a grey body of effective
emissivity β = 1.5 (S18). This means that _T_ dust [L] [follows] [Wien’s]
law (see Eq. (2)).


_T_ dust [L] [[K]][ =][ 2][.][897][ ×][ 10] [3] [/][(][λ] [max] [[][µ][m])][,] (2)


where λ max is the wavelength corresponding to the peak of
λ [β] _L_ λ . A mass weighted _T_ dust [M] [, was also calculated for each tem-]
plate by mass weighted averaging each individual template of
Galliano et al. (2011) (see S18 for more details). In the cases
where we only had one or two points to perform our fit (i.e. the



SED peak was not well defined in this case), we chose to restrict
the _T_ dust [M] [during] [the] [fit] [to] [the] _[T]_ [ M] dust [evolution] [from] [S18] [±][10] [K.]
This is a reasonable way to reduce the error on the deduced _L_ IR
by slightly restricting the _T_ dust [M] [to reasonable values. Our best-fits]
of SEDs are displayed in Fig. 1.
The templates from the library of S18 are built using the
amorphous carbon model from Galliano et al. (2011). This differs from the model from Draine & Li (2007) which takes into
account amorphous silicate and graphite grains. This change of
model was shown in Galliano et al. (2011) to lower the tension,
in the Large Magellanic Cloud and the Milky Way, between the
observed dust-to-gas ratio and the stellar abundances. The differences between the two models are mainly reflected in the different emissivity. The choice of a different emissivity does not
affect the dust temperature or the _L_ IR, as these properties correspond to the peak and the area under the SED, respectively.
However, the _M_ dust deduced from Galliano et al. (2011) is about
a factor of 2 lower than those deduced from Draine & Li (2007),
without affecting the _M_ gas as the factor cancels out when converting _M_ dust to _M_ gas . The debate on the composition of dust
grains goes far beyond the scope of this study. We chose to work
with _M_ dust derived from the Draine & Li (2007) model, as it will
ease comparison with the literature, which is widely base on the
later model. In practice, we have re-fitted the model library of
S18 with a Draine & Li (2007) model to associate the _M_ dust . The
impact on _M_ gas of choosing an amorphous carbon model instead
of an amorphous silicate and graphitic grains model is briefly
discussed at the end of the Sect. 5.3.
Overall we verified that fitting our stacked flux with the S18
or Draine & Li (2007) libraries has little to no impact on our
results, as the differences on some key properties such as _L_ IR,
_T_ dust and _M_ dust (once corrected for the emissivity chosen in S18)
are quite small: −7% [+] − [7%] 4% [for] _[L]_ [IR] [,] [1%] [+] − [12%] 6% [for] _[T]_ [dust] [and] [4%] [+] − [33%] 17%
for _M_ dust . An essential consequence of this observation is that the
models of S18 reproduce well the global SED shape of stacked
galaxies. This reinforces the choice we made to use the S18 templates instead of Draine & Li (2007) for this study.


_4.2._ _Adding ALMA to Herschel_


The addition of ALMA to this study results in an improvement of
the SED at high redshift (i.e, at 3.1 ≤ _z_ ≤ 5.0). More specifically,
it allows to get an ALMA measurement at 10.0 ≤ log 10 ( _M_ ⋆ ) ≤
10.5 for 3.1 ≤ _z_ ≤ 3.9 and 3.9 ≤ _z_ ≤ 5 that provides information on some of the properties of galaxies (i.e. _L_ IR and _M_ gas ) at
these redshifts and _M_ ⋆ instead of what would have just been an
upper limit on these properties. At 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 for
3.1 ≤ _z_ ≤ 3.9 and 3.9 ≤ _z_ ≤ 5, and 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0
for 3.9 ≤ _z_ ≤ 5, this also allows the SED peak to be constrained
more effectively, as it is only weakly constrained, if at all, by the
_Herschel_ data alone. The SED peak is crucial for determining
properties such as _T_ dust [M] [and] _[M]_ [gas] [. Elsewhere it also provides an]
extra point or upper limit that significantly reduces the uncertainty in the properties inferred from the SED fit. These extra
ALMA point are thus decisive for this study, which aims to probe
the properties of galaxies over a wide dynamic range, extending
up to _z_ ∼ 5.


_4.3._ _Simulations to correct for averaging biases_


Because a mean stacking procedure is luminosity weighted, it
can have non-linear effects on the shape of the resulting SED
(e.g. Elbaz et al. 2011; S15; S18). These effects include the
widening of the FIR bump and a bias of the peak towards warmer


A248, page 5 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)


**Fig. 1.** Best-fit SED for each bin of redshift and stellar mass. Blue dots correspond to the flux measurements, red triangles represent the 5σ upper
limits. Blue line is the best-fit SED, the blue shaded area shows the 68% uncertainty of the fit. Red line is the SED maximising _L_ IR in case only
upper limits are available.


A248, page 6 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)



_T_ [L]
dust [. It is mainly a result of mixing galaxies of di][ff][erent redshifts]
and _T_ dust [L] [(e.g.] [Elbaz et al.] [2011][;] [S15][;] [S18][).] [The] [broadening] [of]
the SED increases the difficulty of determining precisely _T_ dust [L]
(S18). For the rest of the paper, we chose to work with massweighted dust temperatures, and we will refer to _T_ dust [M] [simply]
as _T_ dust . To ensure that our conclusions are not biased by these
effects, we performed simulations to identify any systematic bias
due to our stacking procedure.
To this end, for each bin of _M_ ⋆ and redshift, we simulated the
biases coming from stacking starting from the distribution of the
galaxies in the bin. This has the advantage of taking into account
the specificity of the _M_ ⋆ and redshift distributions within our
bin. For each set of galaxies, we created a mock counterpart in
order to compare the properties resulting from the stacking with
those expected.
To each galaxy of mass _M_ ⋆, we assigned the SFR starting
from _M_ ⋆ and following _S FR_ = _R_ SB × _S FR_ MS . The _S FR_ MS
was calculated from the main sequence trend found in this work
(See Eq. (12) and parameters Table 5) as a function of redshift and _M_ ⋆ . _R_ SB represents the starburstiness and is defined
by _R_ SB = _S FR_ / _S FR_ MS . We want to generate both mock main
sequence galaxies and starburst galaxies. It was shown in S15
that both the main sequence width (∼0.3 dex, see S15) and
the starburst fraction do not evolve with redshift and _M_ ⋆ . We
can therefore reasonably assume that the distribution function of
_R_ SB does not vary (S15). This assumption still allows the luminosity functions to be reconstructed properly (e.g. Sargent et al.
2012; S15). Following Sargent et al. (2012), we have modelled
the probability density function of _R_ SB by a double log-normal
distribution (see Eq. (3)):




[SB] [ −] _[f]_ [miss] − log 10 ( _x_ / _x_ 0 ) [2]

exp
2πσ MS  2σ [2] MS



Φ _R_ SB ( _x_ ) = [1][ −] ~~√~~ _[f]_ 2 [SB] πσ [ −] MS _[f]_ [miss]



2σ [2]
MS







_f_ SB − log 10 ( _x_ / _B_ SB ) [2]

exp
2πσ SB  2σ [2] SB



Magnelli et al. (2014) (see Eq. (9)) to take into account the
impact on _T_ dust of the distance of the mock galaxy from the
main sequence ( _R_ SB ). The SED, for each mock galaxy, was
then calculated using _T_ dust, _L_ IR and redshift with the template
library from S18 assuming a contribution of PAH molecules
_f_ PAH ≡ _M_ dust [PAH] [/] _[M]_ [dust] [.] [The] [value] [of] _[f]_ [PAH] [was] [set] [to] [follow] [a]
Gaussian distribution with a mean of 0.039 and a scatter 2.5/100
(S18, roughly for main sequence galaxies). Next, the _M_ dust were
obtained from the selected SED template and the _M_ gas were calculated according to the different methods presented in Sect. 5.3.
The individual SEDs were then stacked using a mean stacking method. Fluxes at 24 µm, 100 µm, 160 µm, 250 µm, 350 µm,
500 µm and 1130 µm were deduced from the stacked SED. The
fluxes were then fitted with the template library from S18. The
properties of the stacked SED were deduced using the method
presented in the corresponding section of this paper: see Sect. 5.1
for _T_ dust, Sect. 5.2 for _L_ IR and Sect. 5.3 for _M_ gas . Potential biases
were then investigated by comparing the actual average properties with those deduced from our stacking analysis.
The relative differences between the actual average properties with those deduced from our stacking analysis are quite
small: −1% [+] − [2%] 4% [for] _[L]_ [IR] [,][ −][6%] [+] − [1%] 2% [for] _[ T]_ [dust] [and 7%] [+] − [2%] 4% [for] _[M]_ [dust] [.]
As a result, we find no clear evidence of significant averaging
bias and thus decided not to apply any correction.


_4.4._ _Active galactic nuclei bias_


It has been reported that AGN can have a major contribution
to the total outgoing light of a galaxy (e.g. Hao et al. 2005;
Richards et al. 2006). However, most of this emission is radiated at wavelengths shorter than 24 µm and thus will not affect
our FIR measurement. Most extreme AGN may still have an
impact on the mid-to-far infrared ratio (in particular 24 µm in our
case), but should not affect the FIR colour compared to normal
star-forming galaxies (Hatziminaoglou et al. 2010). We checked
for any AGN contribution by fitting our SED with a combination of Draine & Li (2007) dust model, and Fritz et al. (2006)
AGN model. No conclusive evidence for a major contribution
(i.e. _L_ IR [AGN] / _L_ IR [TOT] ≥ 10%) from AGNs to the rest-frame FIR was
found in any of our _M_ ⋆ and redshift bins.


**5.** **Stacked galaxies properties**


_5.1._ _Dust temperature_


In this section, we examine the evolution of _T_ dust . In Fig. 2, we
display the corresponding _T_ dust for our SED as a function of redshift and _M_ ⋆ . We do not see a significant dependence of _T_ dust on
_M_ ⋆ . It seems that, overall, the _T_ dust of a main sequence galaxy is
mainly determined by its redshift, independently of its _M_ ⋆ (see
also Magdis et al. 2012; Magnelli et al. 2014).
The temperature of the cosmic microwave background
(CMB) ranges from 2.73 K at _z_ = 0, up to 16.4 K at _z_ = 5,
and, thus, it could become a significant source of heating at high
redshift. We, however, verified, following da Cunha et al. (2013)
that this is not the case. Indeed, the observed _T_ dust of galaxies at
high redshift is significantly higher than that of the CMB.
Because our results come from _H_ -band selected galaxies,
our stacking analysis does not take into account the _H_ -dropout
galaxies (Wang et al. 2019). There are 63 _H_ -dropout galaxies
that have been detected in Wang et al. (2019) over ∼600 arcmin [2] .
In this work, we have 1464 galaxies with _M_ ⋆ ≥ 10 [10] _M_ ⊙ and
_z_ ≥ 3 over ∼1077 arcmin [2] . The _H_ -dropout would then only
account for ∼7.2% of the total sample. We re-fitted the stack


A248, page 7 of 25



_f_ SB
+
~~√~~ 2πσ



2σ [2]
SB



, (3)




where _f_ SB is the fraction of starbursts, _f_ miss is the fraction of
galaxies missed by such distribution (neither starburst nor main
sequence galaxies), σ MS and σ SB are the widths of the main
sequence and starburst distributions, _B_ SB is the median multiplicative boost of star formation that can be expected for a starburst compared to a main sequence galaxy (i.e. the median of
starburst galaxies), and _x_ 0 is the median _R_ SB of main sequence
galaxies. We note that with this parametrisation, we expect _f_ miss
and _x_ 0 to be close to 0 and 1 respectively, by construction. We
have chosen here to use the parametrisation of S15: σ MS =
σ SB = 0.31 ± 0.02 dex, _f_ SB = 3.3% ± 1.5%, _B_ SB = 5.3 ± 0.4,
_f_ miss = 0% ± 2%,and _x_ 0 = 0.87 ± 0.04.
To each galaxy we assign _L_ IR, deduced from the SFR by
subtracting the UV SFR assuming the UV dust attenuation
( _A_ UV ) derived from _M_ ⋆ as in Pannella et al. (2015) (see Eqs. (4)
and (5)) and Kennicutt (1998a) (see Eq. (6)):


_A_ UV = 1.6 × log 10 ( _M_ ⋆ ) − 13.5, (4)


_S FR_ IR = _S FR_ − _S FR_ UV

where SFR UV = SFR × 10 [−][0][.][4][×][A] [UV], (5)


_L_ IR [ _L_ ⊙ ] = 5.8 × 10 [9] × _S FR_ IR [ _M_ ⊙ yr [−][1] ]. (6)


Then _T_ dust was calculated using the best-fit of our work
(see Eq. (7)) for the main sequence trend, and we followed

Leroy, L., et al.: A&A, 691, A248 (2024)



**Fig. 2.** _T_ dust as a function of _M_ ⋆ colour-coded by the redshift bin. Average trend of _T_ dust as a function redshift from S18, is shown as a reference
in faded coloured dashed line.


of _H_ -dropout from Wang et al. (2019) with S18 templates and
deduced a _T_ dust _[H]_ [-drop] = 37.34 [+] − [1] 1 [.] . [2] 27 [K. The contribution of] _[ H]_ [-dropout]
from Wang et al. (2019) was then added to our last bin of redshift
(i.e. 3.9 ≤ _z_ ≤ 5).
In Fig. 2, our result seems to be globally consistent with
the trend of S18. We see only slight evidence that the highest
_M_ ⋆ bin (11 ≤ log 10 ( _M_ ⋆ ) ≤ 12) could be cooler than lowermass galaxies at a fixed redshift. This effect can be observed
for _z_ ≤ 2.5. This could simply show that high-mass galaxies
are actually starting to slowly reduce their SFE on their way
to become quiescent. This is particularly apparent in our first
redshift bin (0.1 ≤ _z_ ≤ 0.4) in which the bending of the main
sequence is also the strongest (see Sect. 5.2; S15).
In Fig. 3, we display the mean _T_ dust over each redshift bin,
weighted by the number of galaxies in each bin of _M_ ⋆, as a function of redshift. Our analysis suggests a linear evolution of _T_ dust
as a function of redshift. Our best linear fit, for 0.1 ≤ _z_ ≤ 5,
follows:


_T_ dust [K] = 34.20 [+] − [0] 0 [.] . [14] 15 [+][ 5][.][06] − [+][0] 0. [.][03] 03 [(] _[z]_ [ −] [2)][.] (7)


We compare our results with those in the literature:
S18, Magnelli et al. (2014), Bouwens et al. (2020), Magdis et al.
(2012) and Béthermin et al. (2015). We also re-fitted the two
stacks of Béthermin et al. (2020) using the template library from
S18. For consistency, we converted all _T_ dust [L] [to] _[ T]_ [ M] dust [when com-]
paring our results with the literature (i.e. for Magnelli et al.
2014; Bouwens et al. 2020). To do this, we adopt the conversion
factor, between mass and light weighted dust temperature, given
by S18:


_T_ dust [M] [[K]][ =][ 0][.][91][ ×][ T] [L] dust [[K]][.] (8)


This conversion factor represents the average conversion factor between _T_ dust [M] [and] _[T]_ [ L] dust [for] [each] [individual] [template.] [Some]
studies (i.e. Magdis et al. 2012; Béthermin et al. 2015) consider the mean starlight heating rate (⟨ _U_ ⟩) (Draine & Li 2007;
Draine et al. 2014) instead of _T_ dust as defined here. To compare


A248, page 8 of 25



**Fig.** **3.** _T_ dust and ⟨ _U_ ⟩ as a function of redshift. The blue dots represent
the _T_ dust of this work, the blue line is the best-fit (up to _z_ = 5), the
dashed blue line is the best-fit extrapolation (for _z_ ≥ 5), and the blue
shaded area represents the 68% uncertainty of the fit. From the literature: S18 (grey solid line), Magnelli et al. (2014) (grey dotted line) and
Bouwens et al. (2020) (grey dash-dotted line) converted using Eq. (8).
Magdis et al. (2012) (grey, dashed line) and Béthermin et al. (2015)
(grey dots) converted using Eq. (9). We also re-fitted the two stacks from
Béthermin et al. (2020) (grey dotted error bars) using template library
from S18.


our results with those, we have chosen to use the ⟨ _U_ ⟩-to- _T_ dust
conversion formula of S18 (see Eq. (9)):


_T_ dust [K] = (⟨ _U_ ⟩ [ _U_ ⊙ ]) [1][/][5][.][57] × 18.2 K. (9)


As ⟨ _U_ ⟩ is only a proxy of _T_ dust, any comparison between the two
quantities should be essentially qualitative.
Our _T_ dust as a function of redshift is consistent within the
uncertainties with S18, extended to _z_ = 5. We find no clear
evidence for the softening of the _T_ dust as the redshift increases
reported by Magnelli et al. (2014), Magdis et al. (2012). This
could stem from the lack of clustering bias correction in their
study, as previously reported in S18. Clustering bias correction
is a quite important step when stacking in _Herschel_ passbands.
Especially in the SPIRE wavelengths, as this effect can account
for up to 50%, of the total signal, on average at 500 µm (e.g.
S15; Béthermin et al. 2015; Delvecchio et al. 2021). Ignoring
this could result in a cooler SED and a lower _T_ dust . Comparing our trend to other works by Béthermin et al. (2015, 2020),
Bouwens et al. (2020), all agree on a linear trend. The differences with our trend may again stem from the way in which the
correction for clustering bias is handled in the two works, as it is
essential to correctly determine _T_ dust .
Another way to look at the redshift evolution of the FIR SED
is to consider the wavelength of the IR SED bump (λ peak ) as a
function of _L_ IR (see Fig. 4). We observe no dependence of λ peak
as a function of _L_ IR at fixed redshift, up to _z_ ≃ 4. Only our
last two redshift bins (i.e. 3.1 ≤ _z_ ≤ 3.9 and 3.9 ≤ _z_ ≤ 5.0)
shows some evolution. However, for the same reason as above,
this could result from a bias due to selection effects, as well
as the fact that we only have two points in these redshift intervals. We conclude that λ peak of main sequence galaxies does not
depend significantly on _L_ IR at a given redshift. This property has

Leroy, L., et al.: A&A, 691, A248 (2024)


Daddi et al. (2004):


_S FR_ UV [ _M_ ⊙ yr [−][1] ] = 2.17 × 10 [−][10] _L_ UV [ _L_ ⊙ ]. (11)



**Fig. 4.** λ peak as a function of _L_ IR . The colour-coded error bars (per redshift bins) represent the results of this work, coloured lines represent the
best-fit and shaded area the 68% uncertainty of the fit. The solid black
line corresponds to the trend of Drew & Casey (2022), while the dotted
black line is an extrapolation of their relation.


already been observed by Magnelli et al. (2014), up to _z_ ≃ 2,
where no clear dependence of _T_ dust has been observed along the
main sequence in the _S FR_ − _M_ ⋆ plane. However, the normalisation seems to evolve with redshift, reflecting the smooth increase
of λ peak with redshift presented in Drew & Casey (2022). But
our results differ from those of Drew & Casey (2022) who studied a different sample built on individual detections and found
an evolution of _T_ dust, as probed by λ peak, with _L_ IR . This discrepancy comes from the probable incompleteness of the sample of Drew & Casey (2022). In this paper, we stack galaxies to
recover the main sequence, and we look at a mass complete sample, where non-detections are accounted for thanks to the stacking technique. On the other hand, Drew & Casey (2022) worked
with individually detected galaxies, and thus might be biased
towards the brightest galaxies at all redshifts (i.e. starbursts). In
addition, their flux-limited sample suffer from selection effect:
at low _L_ IR, their λ peak comes from low redshift galaxies, while
at high _L_ IR, their values are coming from distant galaxies. What
Drew & Casey (2022) find is an effect of redshift not an effect of
_L_ IR .


_5.2._ _The main sequence of star-forming galaxies_


Here we constrain the _S FR_ − _M_ ⋆ correlation, also called the
MS of star-forming galaxies (Noeske et al. 2007). The preferred
method for estimating the SFR of a galaxy is to study the light
from OB stars, because of the close link between their short lifetimes and the instantaneous SFR of galaxies. Although most of
their light is emitted in the UV, it can be largely absorbed by dust
and then re-emitted as thermal radiation in the IR. To obtain the
total SFR associated with a galaxy, or in our case the stack of
several galaxies, it is necessary to combine the SFRs deduced
from both the UV and the IR as:


_S FR_ Tot = _S FR_ UV + _S FR_ IR . (10)


The _S FR_ UV, uncorrected for dust attenuation, is computed
from _L_ UV (rest-frame 1500 Å UV luminosity) following



For our catalogues, the _L_ UV were calculated for all individual
galaxies from _EAZY_ (Pannella et al. 2015). In this study, the
_S FR_ UV was derived for each redshift and _M_ ⋆ bin by averaging the _S FR_ UV of all individual galaxies in the bin. The _L_ IR was
obtained from the SED fit of our stacks, by integrating the best-fit
SED in the range 8–1000 µm rest frame, we deduced the _S FR_ IR
following Kennicutt (1998a) (see Eq. (6)).
The left panel of Fig. 5 displays our SFR for each bin of
redshift and _M_ ⋆ . The SFR follows a monotonic dependence
with increasing _M_ ⋆, at fixed redshift; and with increasing redshift, at fixed _M_ ⋆ . The high-mass end presents a bending of the
main sequence slope, which is more prominent as the redshift
decreases.
Regarding the contribution of _H_ -dropouts to our main
sequence estimate, Wang et al. (2019) reported that ALMAdetected _H_ -dropouts mostly fall within the main sequence at
_z_ ∼ 4 (the version from S15). Moreover, as they represent only
∼7.1% of the galaxies at equivalent _M_ ⋆, their omission should
not alter the overall shape of the main sequence.
The _S FR_ − _M_ ⋆ correlation was then fitted using the formula
introduced in S15 as it is able to capture the bending of the main
sequence at the high-mass end (see Eq. (12)),


log 10 ( _S FR_ MS [ _M_ ⊙ yr [−][1] ]) = _m_ − _m_ 0 + _a_ 0 _r_

− _a_ 1 [max(0, _m_ − _m_ 1 − _a_ 2 _r_ )] [2], (12)


where _r_ ≡ log 10 (1 + _z_ ) and _m_ ≡ log 10 ( _M_ ⋆ /10 [9] _M_ ⊙ ). It was shown
in S15 that the main sequence has the shape in logarithmic space
of a Gaussian distribution with a homogeneous scatter of σ ≃
0.3 dex. Because we stacked our galaxies, via mean stacking,
we actually recover the ⟨ _L_ IR ⟩ of our sample which is different
from the mean of a Gaussian distribution in logarithmic space
with a dispersion σ dist, with, ⟨10 _[X]_ ⟩ = exp((σ X × ln(10)) [2] /2) ×
10 [⟨] _[X]_ [⟩], _X_ = log 10 ( _S FR_ ) following a Gaussian distribution. To
correct for this, we assume that the dispersion of this Gaussian
distribution in logarithmic space is σ dist = 0.3 dex (S15). Our
best-fit parameters are given in Table 5, and displayed on the left
panel of Fig. 5 (left panel).
The shape chosen for the fit sets a slope of one, which is
broadly consistent with our data points. The normalisation of
the main sequence increases significantly with redshift. As we
have already pointed out in the study of _T_ dust, at the highest
redshift (i.e. 3.9 ≤ _z_ ≤ 5.0) and the two highest _M_ ⋆ bins (i.e.
10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11 and 11 ≤ log 10 ( _M_ ⋆ ) ≤ 12), appear to be
highly star-forming and are above our main sequence by a factor
of two. This suggests that these bins include a significant fraction of galaxies with high SFR relative to the main sequence (i.e.
high _R_ SB ).
We compare our results with several versions of the main
sequence from the literature in Fig. 6. Compared to Speagle et al.
(2014), who did not fit any bending, our best-fit is consistent
with the general trend and evolution of the normalisation. However, our work suggests that the bending is real and becomes
stronger at low redshift. Overall, our best-fit remains close to
what was found by S15 at _z_ ≥ 0.7. As already confirmed by
Delvecchio et al. (2021), the trend of S15 main sequence holds
when constructed mainly from FIR data. Nevertheless, we find
a stronger curvature of the main sequence at _z_ ≤ 0.7 compared to what we could extrapolate from S15. This is probably due in part to the fact that they did not probe the main
sequence for _z_ ≤ 0.3. The version of the main sequence by


A248, page 9 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)


**Fig.** **5.** _S FR_ MS as a function of _M_ ⋆ over different redshift bins. The dots represent data from this work. The upper limits were used to perform
the fit but are not shown here to avoid overloading the figure. Left panel: fitted by the Eq. (12), the shaded area the 68% uncertainty of the fit.
Right panel: fitted by the Eq. (13), the shaded area the 68% uncertainty of the fit. The squares represent the best-fit parameter _M_ 0 . No bending was
detected for _z_ - 3.1 and therefore no square error bars are displayed.



Leslie et al. (2020) was derived from a study of the radio continuum at 3 GHz, which may explain the differences in slope,
normalisation and bending. But both roughly agree on the same
evolutionary trend and on a bending of the main sequence with
marginal differences. The bending of the main sequence being at
the high-mass end, it suggests that it is triggered by some mass
driven physical processes.
We have also followed the evolution of the stellar mass knee
_M_ 0 marking the bending point of the main sequence by following
Daddi et al. (2022) (see Eq. (13)):

_S FR_ 1
_S FR_ 0 = 1 + ( _M_ 0 / _M_ ⋆ ) [γ] [.] (13)


Following recommendations from Daddi et al. (2022), we set
γ = 1.1, which should help to reduce the errors and should not
affect the result much. If γ was defined as a free parameter in the
fit, the ⟨γ⟩ would be close to 1.1 anyway. Our best-fit parameters
are given in Table 6, and displayed on the right panel of Fig. 5.
Overall, our results are quite comparable to the evolution of the
bending found by Lee et al. (2015) and Daddi et al. (2022) (i.e.
a decrease in _M_ 0 as we move to a lower redshift). However, we
see little or no evidence of a bending for _z_ - 3. We suggest that
this may be because the physical processes that trigger the main
sequence bending have not had enough time to impact the main
sequence trend at the high-mass end at _z_ - 3. Another possibility
is that the bending still occurs at high redshifts, but only for very
high-mass galaxies ( _M_ ⋆ - 2 − 3 × 10 [11] _M_ ⊙ ), which we could not
probe with this study because they are extremely rare.


_5.3._ _Gas mass_


We chose to calculate _M_ gas from _M_ dust deduced from our stacked
SEDs. We can link _M_ gas to _M_ dust by a gas-to-dust mass ratio
(δ GDR ) that depends only on the metallicity _Z_ (log _Z_ = 12 +
log 10 (O/H)) of the galaxy,


_M_ gas = δ GDR ( _Z_ ) _M_ dust . (14)


A248, page 10 of 25



**Table** **5.** Best-fit parameters of the main sequence of star-forming
galaxies.


_m_ 0 _m_ 1 _a_ 0 _a_ 1 _a_ 2


9.36 [+] − [0] 0 [.] . [02] 02 8.52 [+] − [0] 0 [.] . [26] 06 1.34 [+] − [0] 0 [.] . [09] 04 0.241 [+] − [0] 0 [.] . [018] 010 3.42 [+] − [0] 0 [.] . [11] 12


**Notes.** Best-fit parameters of the main sequence of star-forming galaxies using Eq. (12).


Multiples studies (e.g. Leroy et al. 2011; Magdis et al. 2012;
Rémy-Ruyer et al. 2014; Genzel et al. 2015) show consistent
δ GDR − _Z_ relations that hold at both low and high redshift. We
chose here to use the relation from Magdis et al. (2012):


log δ GDR = 10.54 − 0.99 × (12 + log 10 (O/H)). (15)


As for most galaxies we do not have UV or optical spectra, we
do not have a direct measurement of their metallicity. To go
around this problem, we use the mass-metallicity relation (MZR;
Erb et al. 2006) and follow its redshift dependent version from
Genzel et al. (2015),


12 + log 10 (O/H) = _a_ − 0.087 × (log 10 ( _M_ ⋆ /1.7) − _b_ ) [2], (16)


where _a_ = 8.74 and _b_ = 10.4 + 4.46 log 10 (1 + _z_ ) − 1.78(log 10 (1 +
_z_ )) [2] . We note that Genzel et al. (2015) use a Chabrier (2003)
IMF to define the MZR. In order to use it correctly, our _M_ ⋆
must first be divided by a factor of 1.7. We chose to adopt an
uncertainty of 0.2 dex for our metallicity following the recommendation from Magdis et al. (2012). These latter metallicities
are calibrated in the PP04 N2 scale ( _N_ 2 = [N II ] λ6583/H α ;
Pettini & Pagel 2004). We note that by using the δ GDR relation
of Leroy et al. (2011), instead of Magdis et al. (2012), would
not change our conclusions because for our sample, the relative
median difference in linear scale between the two estimates is
( _M_ gas [MZR][−][Leroy11] − _M_ gas [MZR][−][Magdis12] )/ _M_ gas [MZR][−][Magdis12] = 0.14 [+] − [0] 0 [.] . [05] 08 [.]

Leroy, L., et al.: A&A, 691, A248 (2024)


**Fig. 6.** _S FR_ MS as a function of _M_ ⋆ . The red triangles represent upper limits, the blue dots are the observed values from this work, and shaded area
the 68% uncertainty of the fit. The blue lines represent the best-fit from this work. The green, cyan and orange lines represents the main sequence
from S15, Speagle et al. (2014) and Leslie et al. (2020), respectively. The dashed lines represent extrapolated main sequences to redshifts that were
not investigated in their respective studies.



Another way to calculate the metallicity is the fundamental
metallicity relation (FMR; Mannucci et al. 2010, see Eq. (17)).
It differs from the MZR by adding some dependence on the SFR,


12 + log 10 (O/H) = 8.90 + 0.37m − 0.14s

− 0.19 [2] + 0.12ms − 0.054s [2], (17)


where _m_ = log 10 ( _M_ ⋆ /1.7) − 10 and _s_ = log 10 ( _S FR_ /1.7).
These metallicities are calibrated for the KD02 photoionisation models (Kewley & Dopita 2002). We used the recipe
from Kewley & Ellison (2008) to convert it into a PP04 N2
scale. But once again the differences in metallicities between
the MZR and FMR method does not impact our conclusions,
as for our sample, the relative median is ( _M_ gas [FMR][−][Magdis12] −
_M_ gas [MZR][−][Magdis12] )/ _M_ gas [MZR][−][Magdis12] = −0.16 [+] − [0] 0 [.] . [16] 06 [.]



The previous methods are only reliable when the SED peak
is well defined (i.e. _T_ dust and _M_ dust ), which is not the case in our
bins. The only two bins concerned are 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5
for 3.1 ≤ _z_ ≤ 3.9 and 3.9 ≤ _z_ ≤ 5.0. In this situation, we can
also estimate _M_ gas from a single band measurement located in
the Rayleigh-Jeans part of the SED (e.g. Scoville et al. 2014;
Groves et al. 2015; Schinnerer et al. 2016). The main limitation
is that it does not take into account the evolution with redshift of the _M_ gas metallicity and _T_ dust (e.g. Genzel et al. 2015;
Berta et al. 2016; Schinnerer et al. 2016; Magdis et al. 2017;
Harrington et al. 2021). However, this is a reliable way of estimating _M_ gas at low cost (25% uncertainties; Scoville et al. 2016)
and especially when there is only one band measured in the
Rayleigh-Jeans tail. For these reasons, while we favoured δ GDR −
MRZ methods to deduce _M_ gas as long as the _T_ dust was well
defined. In the opposite case, and when an ALMA measurement


A248, page 11 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)


**Table** **6.** Best-fit parameters of the main sequence of star-forming
galaxies.


Redshift bin ⟨ _z_ ⟩ log 10 ( _M_ 0 / _M_ ⊙ ) log 10 ( _S FR_ 0 / _M_ ⊙ yr [−][1] )

0.1 ≤ _z_ ≤ 0.4 0.19 9.36 [+] − [0] 0 [.] . [04] 04 0.49 [+] − [0] 0 [.] . [03] 03
0.4 ≤ _z_ ≤ 0.7 0.59 10.13 [+] − [0] 0 [.] . [02] 02 1.13 [+] − [0] 0 [.] . [01] 01
0.7 ≤ _z_ ≤ 1.0 0.87 10.36 [+] − [0] 0 [.] . [01] 01 1.49 [+] − [0] 0 [.] . [01] 01
1.0 ≤ _z_ ≤ 1.3 1.16 10.60 [+] − [0] 0 [.] . [03] 02 1.76 [+] − [0] 0 [.] . [02] 02
1.3 ≤ _z_ ≤ 1.8 1.52 10.86 [+] − [0] 0 [.] . [02] 02 2.12 [+] − [0] 0 [.] . [02] 02
1.8 ≤ _z_ ≤ 2.3 2.02 11.10 [+] − [0] 0 [.] . [02] 02 2.48 [+] − [0] 0 [.] . [02] 02
2.3 ≤ _z_ ≤ 3.1 2.70 11.03 [+] − [0] 0 [.] . [05] 04 2.63 [+] − [0] 0 [.] . [04] 03
3.1 ≤ _z_ ≤ 3.9 3.37 11.65 [+] − [0] 0 [.] . [35] 23 3.25 [+] − [0] 0 [.] . [08] 11
3.9 ≤ _z_ ≤ 5.0 4.30 11.92 [+] − [0] 0 [.] . [07] 11 3.84 [+] − [0] 0 [.] . [08] 11


**Notes.** Best-fit parameters of the main sequence of star-forming galaxies using Eq. (13).


is available, we calculated _M_ gas by the method described in
Scoville et al. (2016) (see their Eqs. (16) and (6)), that is



ν 850 µm
_M_ gas = 1.78 _S_ v obs [mJy](1 + _z_ ) [−][4][.][8]
� ν obs



3.8
( _d_ L [Gpc]) [2]
�



× [6][.][7][ ×][ 10] [19]

α 850



Γ 0
10 [10] _M_ ⊙ for λ rest  - 250 µm, (18)
Γ RJ



Γ( _z_, _T_ d, ν) = _[h]_ [v] [obs] [(][1][ +] _[ z]_ [)]

_k_ B _T_ d



1

, (19)

�exp( _[h]_ [v] [obs] _k_ B [(] _T_ [1] d [+] _[z]_ [)] ) − 1�



**Fig.** **7.** _M_ gas as a function of redshift for different _M_ ⋆ . The dots represent _M_ gas estimates from this work using the δ GDR − MRZ method.
the crosses represent _M_ gas estimates from this work following the
method from Scoville et al. (2016). The squares are measurements from
Saintonge et al. (2017). The bins that have been corrected for the _H_ dropout contribution are circled. The thick and thin solid colour lines
represent the best-fit from this work, using Eq. (21) and Eq. (20), respectively. The dashed lines are the fits extrapolation. The shaded area the
68% uncertainty of the fit.


Our _M_ gas measurements are displayed in Fig. 7. We observe a
rapid rise with redshift from Saintonge et al. (2017) data at low
redshift, to our first data points at _z_ ≥ 0.4. Then, at fixed _M_ ⋆,
_M_ gas reach a maximum at _z_ ∼ 1−2 and remains relatively constant as the redshift increases. At fixed redshift, _M_ gas gradually
increase with _M_ ⋆ . All values of our gas masses are provided in
Appendix A.
We examined the contribution of the _H_ -dropouts to _M_ gas in
order to have the most unbiased view possible. Here, we have
simply calculated the _M_ gas, associated with each _H_ -dropout in
the sample of Wang et al. (2019), using their ALMA measurement at 870 µm and following Scoville et al. (2016) method.
The final contribution of the _H_ -dropout to the total _M_ gas within
each bin is _M_ gas _[H]_ [-dropout] × _N_ gal _[H]_ [-dropout] × ϵ/( _M_ gas _[H]_ [-dropout] × _N_ gal _[H]_ [-dropout] ×
ϵ + _M_ gas × _N_ gal ) = 19% [+] − [7%] 17% [on] [average] [(only] [the] [bins] [with]
at least one _H_ -dropout are taken into account), where ϵ =
_Area_ This work / _Area_ Wang+19 ∼ 1.8. The contribution of _H_ -dropouts
can represent up to ∼32% for some bins, hence we chose to add
it to our data. The seven bins that have been corrected for the
_H_ -dropout contribution are circled Fig. 7.

Tacconi et al. (2018) combined _M_ gas from stacks in the IR
and _M_ gas from CO emission. We try to fit our data using the
formula of Tacconi et al. (2018):


log 10 ( _M_ gas ) = _A_ + _B_ × (log 10 (1 + _z_ ) − _F_ ) [β]

+ _D_ × (log 10 ( _M_ ⋆ /1.7) − 10.7) + log 10 ( _M_ ⋆ /1.7) (20)

[+ _C_ × log 10 ( _R_ SB ( _z_, _M_ ⋆ )) + _E_ × log 10 ( _R_ e / _R_ e0 ( _z_, _M_ ⋆ ))],


where the factor 1.7 represents the conversion of _M_ ⋆ from a
Salpeter (1955) to Chabrier (2003) IMF. As our data points represent main sequence galaxies, we cannot probe the _C_ µ term in



where _d_ L is the luminosity distance, α 850 = 6.2 ×
10 [19] erg sec [−][1] Hz [−][1] M [−] ⊙ [1] [,] [Γ] [0] [=] [Γ][(] _[z]_ [=] [0][,] _[ T]_ [d] [=] [25 K][, ν] [=] [ν] [850][ µ][m] [)]
and Γ RJ = Γ( _z_, _T_ d = 25 K, ν = ν 1.1 mm ), _h_ is Planck’s constant, _k_ B is Boltzmann’s constant, _T_ d = 25 K and ν λ = λ _c_ [.]
We note that this technique provides, for our sample, consistent
results with those of the MZR method, with a relative median
( _M_ gas [Scoville16] − _M_ gas [MZR][−][Magdis12] )/ _M_ gas [MZR][−][Magdis12] = 0.19 [+] − [0] 0 [.] . [35] 32 [when]
both δ GDR − MRZ and Scoville et al. (2016) could be performed.
In summary, we chose to calculate our _M_ gas using
Magdis et al. (2012) for δ GDR ( _Z_ ) (Eq. (15)) and Genzel et al.
(2015) MZR for the metallicities (Eq. (16)). When the peak of
the SED is poorly constrained and an ALMA flux is available,
we chose to calculate _M_ gas from Scoville et al. (2016) method.
For the rest of the paper, we will refer to _M_ gas [MZR][−][Magdis12], or
_M_ gas [Scoville16] simply as _M_ gas .
Here _M_ gas represents the total gas budget of a galaxy including both molecular gas ( _M_ H 2 ) and atomic gas ( _M_ HI ), that is,
_M_ gas = _M_ H 2 + _M_ HI . The HI content of galaxies is still poorly
known outside the local universe because the 21cm emission line is difficult to detect with current facilities. However,
Bauermeister et al. (2010) showed that it is unlikely that the HI
content of galaxies varies strongly with redshift. In contrast, the
H 2 content evolves strongly with redshift (e.g. Daddi et al. 2010;
Tacconi et al. 2010, 2013; Lagos et al. 2015; Genzel et al. 2015;
Tacconi et al. 2018). In Tacconi et al. (2018), it was concluded
that the assumption _M_ gas ∼ _M_ H 2 should hold for _z_ - 0.4. Therefore, we decided not to consider our _M_ gas for _z_ < 0.4 (i.e. our
first redshift bin), as we could not probe the HI content of the
galaxy at these redshifts. In order to add some reliable measurements of _M_ H 2 to our study at _z_ < 0.4, we used data points from
Saintonge et al. (2017) that come from very local measurements
(0.01 ≤ _z_ ≤ 0.05).


A248, page 12 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)


**Table 7.** Best-fit parameters of _M_ gas evolution of the main sequence.


_A_ _B_ _F_ _D_ β [(][∗][)]


0.0453 [+] − [0] 0 [.] . [146] 036 [−][1][.][61] − [+] 2 [0] . [.][73] 87 [0][.][901] − [+][0] 0 [.] . [362] 373 [−][0][.][306] − [+][0] 0 [.] . [929] 718 2


**Notes.** Best-fit parameters of _M_ gas evolution of the main sequence using
Eq. (20). [(][∗][)] Indicates that this parameter was fixed during the fit.


**Table 8.** Best-fit parameters of _M_ gas evolution of the main sequence.


_m_ 0 _m_ 1 _a_ 1 _a_ 2


1.93 − [+] 0 [0] . [.][18] 23 0.69 [+] − [0] 0 [.] . [02] 01 3.53 [+] − [0] 0 [.] . [33] 56 −2.96 [+] − [0] 0 [.] . [92] 71


**Notes.** Best-fit parameters of _M_ gas evolution of the main sequence using
Eq. (21).



Tacconi et al. (2018), that represents the evolution with respect
to the distance to the main sequence _sS FR_ / _sS FR_ MS, where
_sS FR_ is the specific SFR ( _sS FR_ = _S FR_ / _M_ ⋆ ). And we do not
explore the morphology of galaxies in this study, which makes it
impossible to probe the term _E_ µ, which compares the effective
radius of galaxies ( _R_ e ) to the mean effective radius of the star
forming population _R_ e 0 . The results are displayed in Fig. 7, and
our best-fit parameters are given in Table 7.
Looking at Fig. 7, we notice that _M_ gas observed at low redshift (0.4 ≤ _z_ ≤ 1) tends to be higher than the best-fit trend
(even though it is in most cases within the error bars), and the
trends from literature such as Tacconi et al. (2018). A similar
effect has been observed by Tacconi et al. (2018) who measured
higher depletion times (τ dep ) deduced from dust observations
compared to the ones deduced from CO line fluxes. The effect
observed in Tacconi et al. (2018) decreases slowly with redshift
(about 0.3 dex at _z_ ∼ 0.4 to 0 at _z_ ∼ 1.5) and roughly matches
the effect observed here. We conclude that this effect, which was
solved in Tacconi et al. (2018) by matching the zero-point for
each method, arises when deducing _M_ gas from dust observations.
It feels that the form use in Tacconi et al. (2018) to fit _M_ gas fails
to properly recover the form of our measurements. In a way to
provide for a better fit, we chose to also fit our data using a formula of the form:

log 10 ( _M_ gas ) = � _mm_ 00 + + _m m_ 11 _mm_ + + _a a_ 11 _rr_ 0 + + _a a_ 22 _rr_ [2] 0 [2] forfor _z z_ < ≥ _zz_ 00, (21)


where _m_ = log 10 ( _M_ ⋆ ), _r_ = log 10 (1 + _z_ ), _r_ 0 = log 10 (1 + _z_ 0 ) and
_z_ 0 = − _a_ 1 /2 _a_ 2 . The best-fit parameters, using Eq. (21) are given
in Table 8.
We compare our results to the trends observed by
Tacconi et al. (2018) and Wang et al. (2022) in Fig. 8. In Fig. 8,
the trends are displayed for stellar mass bins in the Salpeter
(1955) IMF. Differences between our results and previous works
(e.g. Scoville et al. 2016, 2017; Tacconi et al. 2018; Liu et al.
2019; Wang et al. 2022) may result from selection effects and
from the method used to derive the gas masses. The present sample was built using an _H_ -band selection that is the best proxy
for the stellar mass, although not perfect for the highest redshifts. Other studies generally rely on a CO-line and/or dust continuum selection. This may lead to a potential bias favouring
galaxies with higher specific star formation rate, that is, higher



**Fig. 8.** _M_ gas as a function of redshift and _M_ ⋆ . The solid lines represent
the best-fit from this work colour-coded by _M_ ⋆ (using Eq. (21)), the
dashed lines represent the trend from Tacconi et al. (2018), the dotted
lines are from Wang et al. (2022). The faded lines represent an extrapolation from their respective laws.


_sS FR_ = _S FR_ / _M_ ⋆, hence galaxies above the main sequence. It
has been found that such galaxies in general exhibited higher gas
fractions. In our analysis, we tried to avoid such bias by checking
that our stacked samples followed the median of the _S FR_ − _M_ ⋆
main sequence.
The trends observed by Wang et al. (2022) were obtained
as well using a mass-selected sample, but the gas masses were
derived from millimetre continuum fluxes using the method from
Scoville et al. (2016). We produced a version of our analysis
using the same method for consistency check, it is presented in
Appendix B. We find that we are able to reproduce the same
trends as Wang et al. (2022) if we were to use the same technique based only on the formula of Scoville et al. (2016). Hence,
the differences found in the present study can be explained by
the use of a different method to derive gas masses. We favoured
the present method because it takes into account the variation
of metallicity and the associated change in dust-to-gas ratio as a
function of stellar mass. This is one of the reasons why we opted
for a mass-selection in the first place.
As mentioned in Sect. 4, we chose to work with _M_ dust
from amorphous silicate and graphitic grains (Draine & Li 2007)
instead of amorphous carbon (Galliano et al. 2011; S18). We
investigated what the impact would have been on _M_ gas if
we had chosen a model based on amorphous carbon such as
Galliano et al. (2021). Although the results are quite comparable, using the model from Galliano et al. (2021), would translate
into slightly lower _M_ gas (∼−10% at _z_ = 4). These differences
would not have changed the conclusions drawn in this paper.


**6.** **Cosmic star formation history**


In this section, we present the redshift evolution of ρ SFR, that is,
the cosmic star formation history. To calculate the ρ SFR, we start
from the stellar mass function of SFGs of Davidzon et al. (2017),
that is given for different redshift bins. For each redshift bin, we


A248, page 13 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)


**Fig.** **9.** Cosmic star formation rate density (ρ SFR ) as a function of redshift. The green line represents the total ρ SFR trend from this work (i.e.
integrating the stellar mass function down to 3 × 10 [9] _M_ ⊙ ). The red and blue lines represent the contribution of galaxies with log 10 ( _M_ ⋆ / _M_ ⊙ ) - 10
and log 10 ( _M_ ⋆ / _M_ ⊙ ) < 10, respectively. The black dotted line represents the ρ SFR detected with stacking. The purple squares show the contribution
of _H_ -dropout from Wang et al. (2019). The dotted green and red lines show the trend once _H_ -dropout contribution from Wang et al. (2019) has
been added to the respective coloured solid lines. The grey line represents the trend from Madau & Dickinson (2014). The cyan and orange squares
represent ρ SFR estimate from Leslie et al. (2020) and Gruppioni et al. (2020), respectively.



generated galaxies with uniform redshift distribution within the
bin, and a _M_ ⋆ distribution following these stellar mass functions.
From the redshift and _M_ ⋆, we then assigned a SFR using the
same method as in Sect. 4.3. In summary, _S FR_ = _R_ SB × _S FR_ MS,
where _S FR_ MS is calculated from the main sequence evolution
found in this work (see Eq. (12) and parameters Table 5). And a
_R_ SB is randomly drawn from a double Gaussian distribution representing the position of normal and starbursting galaxies relative to the main sequence (Eq. (3)). Then ρ SFR is calculated by
summing the SFR of galaxies down to _M_ ⋆ [lim] = 3 × 10 [9] _M_ ⊙ . Errors
were generated by varying the _S FR_ MS trend of Eq. (12) within
the errors of the fit, a 100 times.
The study of Wang et al. (2019) presents the contribution
to ρ SFR of _H_ -dropout galaxies, which can reach up to 10%
at _z_ ∼ 4−5. We have therefore added the contribution of _H_ dropout galaxies of Wang et al. (2019) to our ρ SFR considering
the sample of _H_ -dropout galaxies have a median stellar mass of
_M_ ⋆ ∼ 10 [10][.][6] _M_ ⊙ (Wang et al. 2019).
We compare the ρ SFR evolution with that of
Madau & Dickinson (2014) who integrate UV and IR luminosity functions down to _L_ min = 0.03 _L_ ∗ . Deducing ρ SFR by
integrating luminosity functions down to 0.03 _L_ ∗, or the mass
function down to 3 × 10 [9] _M_ ⊙ should yield, to the first order,
similar results (Schreiber et al. 2015). We chose for the rest of
the paper to derive our ρ SFR by integrating the mass function
down to 3 × 10 [9] _M_ ⊙ . Thus, all conclusions on the evolution of the


A248, page 14 of 25



ρ SFR in this paper should be understood in this framework, as
integrating the luminosity function down to lower luminosities,
or the mass function down to lower masses, must yield a higher
total ρ SFR .
The total ρ SFR is displayed in Fig. 9 along with some examples from the literature, and the data points from this work are
summarised in Table 9. We observe a rise of ρ SFR from _z_ ∼ 5
to _z_ ∼ 2, and then it gradually decreases down to _z_ ∼ 0.35. The
high masses (i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) - 10) account for most of the
ρ SFR until _z_ ∼ 4. On the other hand the ρ SFR associated to lowmass galaxies (i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) < 10) is roughly constant over
0 ≤ _z_ ≤ 5.
We can see that our estimate of the total ρ SFR is close to what
has been observed by Leslie et al. (2020) and to the evolution
of Madau & Dickinson (2014). On the other hand, the measurements from Gruppioni et al. (2020) are mostly in disagreement
with our results at high redshift (i.e. _z_ ≥ 2). The ρ SFR from
Gruppioni et al. (2020) is deduced from the integration of the
IR-luminosity function (which make it ρ [IR] SFR [) down to 10] [8] _[L]_ [⊙] [.]
In Fig. 10, we show the contribution to the total ρ SFR of the
full range of stellar masses. We observe that the increase in the
total ρ SFR, from _z_ ∼ 5 to _z_ ∼ 2, comes from the growing number
of massive galaxies (i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) > 10), which can be seen
in the evolution of the stellar mass function at these redshifts
(Davidzon et al. 2017). Downsizing and the bending of the main
sequence explain the fall of the contribution of massive galaxies

Leroy, L., et al.: A&A, 691, A248 (2024)


**Table 9.** ρ SFR as a function of redshift.


Redshift 0.35 0.65 0.95 1.3 1.75 2.25 2.75 3.25 3.75 5.00


log 10 � _M_ ⊙ yrρ [−] SFR [1] Mpc [−][3] � −1.41 [+] − [0] 0 [.] . [01] 01 [−][1][.][22] − [+][0] 0 [.] . [01] 01 [−][1][.][01] − [+][0] 0 [.] . [01] 01 [−][0][.][90] − [+][0] 0 [.] . [01] 01 [−][0][.][84] − [+][0] 0 [.] . [01] 01 [−][0][.][92] − [+][0] 0 [.] . [01] 01 [−][0][.][97] − [+][0] 0 [.] . [01] 01 [−][1][.][11] − [+][0] 0 [.] . [01] 02 [−][1][.][26] − [+][0] 0 [.] . [01] 02 [−][1][.][39] [+] − [0] 0 [.] . [02] 03



−1.60 [+] − [0] 0 [.] . [01] 01 [−][1][.][37] − [+][0] 0 [.] . [01] 01 [−][1][.][13] − [+][0] 0 [.] . [01] 01 [−][1][.][00] − [+][0] 0 [.] . [01] 01 [−][0][.][92] − [+][0] 0 [.] . [01] 01 [−][1][.][00] − [+][0] 0 [.] . [01] 01 [−][1][.][08] − [+][0] 0 [.] . [01] 01 [−][1][.][25] − [+][0] 0 [.] . [01] 02 [−][1][.][41] − [+][0] 0 [.] . [02] 02 [−][1][.][55] [+] − [0] 0 [.] . [02] 02
�


−1.88 [+] − [0] 0 [.] . [03] 03 [−][1][.][74] − [+][0] 0 [.] . [02] 03 [−][1][.][62] − [+][0] 0 [.] . [02] 02 [−][1][.][60] − [+][0] 0 [.] . [02] 02 [−][1][.][60] − [+][0] 0 [.] . [03] 04 [−][1][.][67] − [+][0] 0 [.] . [04] 05 [−][1][.][61] − [+][0] 0 [.] . [04] 05 [−][1][.][65] − [+][0] 0. [.][03] 07 [−][1][.][77] − [+][0] 0 [.] . [05] 07 [−][1][.][91] [+] − [0] 0 [.] . [05] 09
�



log 10


log 10



ρ SFR _[M]_ [⋆>][10][10] _[M]_ [⊙]
_M_ ⊙ yr [−][1] Mpc [−][3]
�

ρ SFR _[M]_ [⋆<][10][10] _[M]_ [⊙]
_M_ ⊙ yr [−][1] Mpc [−][3]
�



**Notes.** ρ SFR as a function of redshift from this work. Here, ρ SFR values include the _H_ -dropout contribution from Wang et al. (2019).



from _z_ ∼ 2 to _z_ ∼ 0. We again observe that massive galaxies (i.e.
log 10 ( _M_ ⋆ / _M_ ⊙ ) > 10) dominate the total ρ SFR at all redshifts (i.e.
they account for more than 70%). In particular, it appears that
galaxies with 10.5 ≤ log 10 ( _M_ ⋆ / _M_ ⊙ ) ≤ 11.25 account for more
than ∼55% of the total ρ SFR at _z_ = 2, making them the main
driver of the peak in the observed cosmic star formation history
at this redshift.


**7.** **Cosmic evolution of the gas mass density**


In Sect. 6, we have simulated a catalogue of galaxies where for
each of them, we calculated _M_ ⋆ and _R_ SB . From these properties,
we now infer _M_ gas by expanding Eq. (21) as follows:



_m_ 0 + _m_ 1 _m_ + _a_ 1 _r_ + _a_ 2 _r_ [2]
+ _C_ × log 10 ( _R_ SB ( _z_, _M_ ⋆ )) for _z_ < _z_ 0
_m_ 0 + _m_ 1 _m_ + _a_ 1 _r_ 0 + _a_ 2 _r_ 0 [2]
+ _C_ × log 10 ( _R_ SB ( _z_, _M_ ⋆ )) for _z_ ≥ _z_ 0,



log 10 ( _M_ gas ) =







(22)



gas mass discrepancy discussed in Fig. 8 is the largest at high
redshifts (i.e. _z_ - 3). The latter part is a potential weakness of
all studies including ours, since the low stellar mass – high redshift of the cosmic gas mass density range relies on rather uncertain extrapolations. As already pointed out in Liu et al. (2019),
the form of the formula chosen to fit _M_ gas can have a significant
impact on the resulting ρ gas trend, and could be the cause of what
is observed here.
We also computed ρ gas by summing _M_ gas of all galaxies
down to several different _M_ lim [∗] [(] _[M]_ lim [∗] [=] [1][.][7][ ×][ 10] [8] [, 1][.][7][ ×][ 10] [9] [and]
1.7 × 10 [10] _M_ ⊙ ). We compared it to Magnelli et al. (2020) where
a ρ gas was computed for the same _M_ lim [∗] [from the stacking of] _[ H]_ [-]
band selected galaxies in ALMA and through the method from
Scoville et al. (2016). The results are displayed in Fig. 12. Here,
our work agrees quite well with that of Magnelli et al. (2020) for
the total ρ gas (i.e. _M_ ⋆ [lim] = 1.7 × 10 [8] ). However, the mass distribution is not similar: massive galaxies (i.e. _M_ ⋆ [lim] = 1.7 × 10 [10] )
contribute more at low redshift (i.e. _z_ ≤ 0.7) in this work as compared to Magnelli et al. (2020); conversely, their contribution is
smaller at higher redshift (lower by a factor ∼3 at _z_ ∼ 2.8 compared to Magnelli et al. 2020).


**8.** **Discussion**


Here, when we discuss the evolution of galaxies, it should
be understood that we are discussing the evolution of main
sequence galaxies, as all scaling relations of SFR, _M_ gas and _T_ dust
with _M_ ⋆ and redshift have been deduced for main sequence
galaxies.


_8.1._ _Cosmic densities of star formation and gas density as a_
_function of stellar mass_


An interesting feature of Fig. 9 is the fact that the contribution to
ρ SFR of galaxies with _M_ ⋆ ≤ 10 [10] _M_ ⊙ appears to be constant over
1 ≤ _z_ ≤ 3 and slightly decreasing for _z_ ≥ 3. This means that the
balance of the number of these galaxies and their efficiency in
producing stars remains constant with cosmic time. This feature
can also be seen in Fig. 11, where the contribution to ρ gas is also
quite stable for galaxies with _M_ ⋆ ≤ 10 [10] _M_ ⊙ .
On the other hand, galaxies with _M_ ⋆ ≥ 10 [10] _M_ ⊙ account for
most stars formed up to _z_ ∼ 5. This shows that it is galaxies with
_M_ ⋆ ≥ 10 [10] _M_ ⊙ that are responsible for the observable shape on
the ρ SFR, especially at the cosmic noon at _z_ ∼ 2. In Fig. 13a, we
can see that the 10% (of the total number of galaxies contributing to ρ SFR ) most massive galaxies contribute to a large fraction
of the ρ SFR at all redshifts. This contribution goes from ∼24%
at _z_ ∼ 0 to ∼48% at _z_ ∼ 5. In particular, this means that by
considering only 10% (in number) of the most massive galaxies, we can deduce a relatively good estimation of the total ρ SFR


A248, page 15 of 25



where _m_ = log 10 ( _M_ ⋆ ), _r_ = log 10 (1 + _z_ ), _r_ 0 = log 10 (1 + _z_ 0 ) and
_z_ 0 = − _a_ 1 /2 _a_ 2 . Here, _m_ 0, _m_ 1, _a_ 1 and _a_ 2 are taken from Table 8,
and _C_ = 0.53 is taken from Tacconi et al. (2018). Next, the cosmic evolution of gas density (ρ gas ) is calculated by summing the
_M_ gas of galaxies down to _M_ ⋆ [lim] = 3 × 10 [9] _M_ ⊙ . Errors were generated by varying our best-fit of _M_ gas [MS] [within its errors, one hundred]
times. Defined this way, ρ gas directly represents the gas content
of galaxies contributing to the ρ SFR presented in Fig. 9. We display the evolution of ρ gas as a function of redshift in Fig. 11.
We can see the same kind of features as for the evolution of
ρ SFR : a rise and fall with redshift with a maximum around _z_ ∼ 2;
a dominance across all redshifts of the high-mass galaxies (i.e.
log 10 ( _M_ ⋆ / _M_ ⊙ ) - 10) contribution; and a relatively flat evolution of the low-mass galaxies (i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) < 10). This
shows that the SFE of both high and low-mass galaxies are not
drastically changing with time, and thus that the gas content of
galaxies (i.e. the accretion) is the primary driver of their SFRs:
high-mass galaxies have higher SFR at fixed redshift because
they have more gas. However, comparing the relative evolution
of ρ gas (see Fig. 11) and ρ SFR (see Fig. 9) shows that ρ _[z]_ gas [=][5] [/ρ] _[z]_ gas [=][0]
(and in particular the high-mass contribution) is lower by a factor ∼3−4 compared to ρ _[z]_ SFR [=][5] [/ρ] _[z]_ SFR [=][0] [. This hints that one unit of gas]
leads to more stars being formed at _z_ ∼ 5 compared to _z_ ∼ 0 (i.e.
a higher SFE at _z_ ∼ 5 compared to _z_ ∼ 0).
We substituted, in our later method to estimate ρ gas, _M_ gas
from this work, for best-fit of _M_ gas from the literature and compared it to our estimate of ρ gas . We can see in Fig. 11, that the redshift evolution of ρ gas from Tacconi et al. (2018) or Wang et al.
(2022) are higher compared to the one from this work. Theses
are simply resulting from discrepancies already observed in the
respective _M_ gas trend they were built from, and goes together
with a stronger contribution of low-mass galaxies for which the

Leroy, L., et al.: A&A, 691, A248 (2024)


**Fig. 10.** Contributions over the whole range of stellar masses to the total ρ SFR as a function of redshift for SFGs.



**Fig. 11.** ρ gas as a function of redshift. The green line represents the total
ρ gas inferred from this work (i.e. integrating the stellar mass function
down to 3 × 10 [9] _M_ ⊙ ). The red and blue lines represent the contribution
to the total ρ gas of galaxies with log 10 ( _M_ ⋆ ) - 10 and log 10 ( _M_ ⋆ ) < 10,
respectively. The purple and cyan lines represent ρ gas deduced from
the _M_ gas definition of Wang et al. (2022) and Tacconi et al. (2018),
respectively.


at intermediate and high redshifts. From these numbers, we can
also recognise some hierarchical growth effect, as bins gradually
rise in _M_ ⋆ over time.
We find that _H_ -dropout galaxies account for 13% of the total
cosmic SFR density (CSFD) at _z_ = 4–6. This is in agreement
with the value of 10% found in Wang et al. (2019). We note
that _H_ -dropout galaxies account for ∼23% of the stars formed
in massive galaxies (i.e. _M_ ⋆ ≥ 10 [10][.][3] _M_ ⊙ ). This is a large contribution but not a dominant one, as opposed to the claim of
Wang et al. (2019) that _H_ -dropouts dominate the SFR density
in the most massive galaxies. This discrepancy results from our
use of a fully complete sample of galaxies selected in stellar
mass, whereas Wang et al. (2019) compared _H_ -dropouts to UVselected and similarly massive Lyman-break (LBG) galaxies.
We observe a decline in star formation in massive galaxies
that mirrors that of the total star formation density. This is an
illustration of the bending effect of the MS at high mass (see
Fig. 13a). The use of the depletion time in Fig. 13b illustrates
this clearly: the depletion time of massive galaxies varies from
τ dep ≲ 200 Myr at _z_ - 4 to τ dep ≳ 600 Myr at _z_ < 1.


A248, page 16 of 25



**Fig.** **12.** ρ gas as a function of redshift. The green, orange and red lines
represent ρ gas derived from this work with _M_ ⋆ [lim] of 1.7 × 10 [8], 1.7 × 10 [9]
and 1.7 × 10 [10] _M_ ⊙, respectively. The green, orange and red hatches
represent estimates of ρ gas from Magnelli et al. (2020) with _M_ ⋆ [lim] of
1.7 × 10 [8], 1.7 × 10 [9] and 1.7 × 10 [10] _M_ ⊙, respectively. The green dots
with black circles depict the estimate of ρ gas from Magnelli et al. (2020)
for _M_ ⋆ - _M_ limit, _M_ limit being the stellar mass completeness limit from
Magnelli et al. (2020).


In Fig. 13c, we show that the contribution of the most massive galaxies (e.g. _M_ ⋆ ∼ 10 [11] M ⊙ ) to the CSFD is nearly flat (i.e.
their contribution to the CSFD is roughly constant), meaning that
they tightly follow the global history of cosmic star formation
(i.e. the global shape of the CSFD consisting of a rise, a cosmic
noon and a fall).
Let us consider a typical galaxy with _M_ ⋆ = _M_ star, such that
50% of ρ ⋆ (cosmic stellar mass density) is made of galaxies
above and below _M_ star . We can follow the contribution of such
typical galaxy to the cosmic SFR density by following the line
where the _Y_ -axis on the right of Fig. 13c equals 50%. We find
that galaxies with _M_ ⋆ - _M_ star contribute to ∼50% of ρ SFR at
_z_ - 3 and drops to only ∼25% at _z_ ∼ 0. This decrease of the relative contribution of massive galaxies to ρ ⋆ illustrates the impact
on the cosmic SFR history of the bending of the MS. The fact
that this happens continuously with cosmic time, supports a scenario of a slow downfall of star formation rather than a rapid
quenching of the most massive galaxies.

Leroy, L., et al.: A&A, 691, A248 (2024)


**Fig.** **13.** Contribution to ρ SFR of SFGs as a function of redshift. Catalogues were binned through different methods and a specific property is
displayed through colours: see each sub-figure for specifics. (a) Each bin includes 10% of the galaxies in number, picking from the lowest _M_ ⋆
onwards. The minimum _M_ ⋆ in the bin defines the colour. The numbers give the median _M_ ⋆ within the bin along with the lower and maximum
extension of the bin. (b) Each bin includes 10% of the total _M_ ⋆ of all galaxies, picking from the lowest _M_ ⋆ onwards. The median τ dep in the bin
defines colour. (c) Each bin includes 10% of the total _M_ ⋆ of all galaxies, picking from the lowest _M_ ⋆ onwards. The minimum _M_ ⋆ in the bin defines
the colour. Contours of log 10 ( _M_ ⋆ = _M_ ⊙ ) = 10 and log 10 ( _M_ ⋆ = _M_ ⊙ ) = 11 are added as black dashed lines.



In Fig. 14, we track the evolution of the stellar mass above
which galaxies contribute to exactly 50% of the CSFD. We
can see in Fig. 14 that this particular stellar mass falls around
∼10 [10][.][2] _M_ ⊙ with an evolution with redshift that mirror the one of
the CSFD by peaking at the cosmic noon at ∼10 [10][.][4] _M_ ⊙ .


_8.2._ _Comparison with the TNG100 simulation_


Here we compare our results with cosmological simulations.
In particular, we have investigated whether current simulations
are able to reproduce the contribution of the different stellar



mass bins to the total ρ SFR . We chose to examine the TNG100
simulation (Nelson et al. 2019, 2018; Springel et al. 2018;
Marinacci et al. 2018; Naiman et al. 2018; Pillepich et al.
2018b,a; Weinberger et al. 2017) of the IllustrisTNG
project.
We retrieved the ρ SFR of TNG100 using the same method
as the one with which we calculate the ρ SFR in this work, that
is, by integrating down to 3 × 10 [9] _M_ ⊙ . In order to compare the
trends with our work, this was also done by integrating only
galaxies with log 10 ( _M_ ⋆ / _M_ ⊙ ) - 10 and log 10 ( _M_ ⋆ / _M_ ⊙ ) < 10.
We display the evolution of ρ SFR with redshift retrieved from the


A248, page 17 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)



**Fig.** **14.** Stellar mass above which galaxies contribute exactly 50% of
the CSFD as a function of redshift.


**Fig. 15.** Cosmic star formation rate density (ρ SFR ) as a function of redshift. The green, red and blue lines represent ρ SFR deduced from the
TNG100 simulation integrated from 3 × 10 [9] _M_ ⊙, including all galaxies,
galaxies with log 10 ( _M_ ⋆ / _M_ ⊙ ) - 10, and galaxies with log 10 ( _M_ ⋆ / _M_ ⊙ ) <
10, respectively. The green, red and green faded dots represent the total
ρ SFR trend, ρ SFR of galaxies with log 10 ( _M_ ⋆ / _M_ ⊙ ) > 10, and galaxies with
log 10 ( _M_ ⋆ / _M_ ⊙ ) < 10, respectively (including _H_ -dropout contribution
from Wang et al. 2019), from this work. The grey line represents the
trend from Madau & Dickinson (2014) for reference.


TNG100 simulation in Fig. 15. By comparing the trends of the
TNG100 simulation with our results, we can see clear discrepancies as also noticed and discussed in Pillepich et al. (2018a).
The ρ SFR of the low masses in TNG100 (i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) <
10) is not nearly as flat as observed (especially at _z_ ≤ 2).
On the other hand, the ρ SFR of the high masses in TNG100
(i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) - 10) does not account for as large a part
of the total ρ SFR for _z_ < 3. The high masses account for less than
half of the total ρ SFR at _z_ ∼ 1.7 in the simulation compared to the
observations. As a result, the ρ SFR peak is reached too early (i.e.
at _z_ ∼ 3 instead of the observed at _z_ ∼ 1.7) in the simulation.
The disparities between the two total ρ SFR trends can be almost
exclusively associated with the contribution of massive galaxies
being off in the TNG100 simulation.


A248, page 18 of 25



**Fig. 16.** Ratio of the ρ SFR of high-mass ( _M_ ⋆ - 10 [10] _M_ ⊙ ) over low-mass
( _M_ ⋆ < 10 [10] _M_ ⊙ ) galaxies, as a function of redshift. The red line represents the ratio deduced from this work (i.e. from observations). The
blue line represents the ratio deduced from the TNG100 simulation.



Another way to show the difference in behaviour between
the TNG100 simulation and our observations for the two mass
bins, is to look at the evolution over redshift of ρ SFR _[M]_ [⋆] [>][10] [10] /ρ SFR _[M]_ [⋆] [<][10] [10]

(see Fig. 16). We can see that the ratio decreases continuously
with increasing redshift in the simulation, while observations
show a clear peak in the ratio around _z_ ∼ 1.7 (i.e. the cosmic
noon) where the amount of stars formed in high-mass galaxies
(i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) > 10) exceeds by a factor up to ∼5.6 the one
from low-mass galaxies (i.e. log 10 ( _M_ ⋆ / _M_ ⊙ ) < 10).
In addition to underestimating the contribution of massive
galaxies to ρ SFR, these simulations tend to recover, for SFGs,
lower gas fractions (see Fig. 17) and SFR (see Fig. 18) compared
to observations. In TNG100, _f_ gas < 15% for _M_ ⋆ - 10 [10] _M_ ⊙ at all
redshifts (Fig. 17), as it was already addressed in Pillepich et al.
(2019). Moreover, the SFR of massive individual galaxies is
lower in the TNG100 simulation than in observations at, for
example, _z_ - 4 (see Fig. 18). Lewis et al. (2024) shows a lack of
metal content in IllustrisTNG simulations at _z_ = 1, that might be
due to AGN feedback that removes large quantities of metal-rich
gas from the centres of massive galaxies. The lower metallicities observed by Lewis et al. (2024) in IllustrisTNG simulations
at _z_ = 1 could be a residual memory of how AGN affected star
formation at higher _z_, which matches the lack of star formation
we observe in Fig. 18. This could indicate flaws in the way gas
accretion, the efficiency of galaxies to form stars from their gas
content, or the ejection of gas through galactic winds is treated in
the simulations. This shows that the problems encountered in the
simulations may be due to the feedback processes used to regulate star formation and the gas reservoir of galaxies. In particular,
the impact of AGN feedback may be overestimated to regulate
star formation and kill massive galaxies. It has been shown that
AGN feedback does not directly expel the gas and quench star
formation at large scales. High-resolution simulations (i.e. with
maximum spatial resolution ∼5−100 pc) show that the AGN
feedback tends to have little or no effect on the dense gas inside
the galactic disc, because most of the out-flowing winds escape
perpendicular to the galactic disc (Gabor & Bournaud 2014).
AGN-driven outflows (i.e. ejective feedback), if sustained, could
only quench a galaxy after a long time scale, that is, more than
one Gyr (Gabor & Bournaud 2014; Biernacki & Teyssier 2018).
These high-resolution simulations favour preemptive feedback

Leroy, L., et al.: A&A, 691, A248 (2024)



**Fig. 17.** _f_ gas as a function of _M_ ⋆ for SFGs in TNG100. Coloured lines
represent the evolution deduced from the best-fit of _M_ gas from this work
(see Table 7).


(i.e. cutting out inflows of gas into the disc), though AGNdriven winds, to quench a galaxy (Gabor & Bournaud 2014;
DeGraf et al. 2017; Biernacki & Teyssier 2018). However, even
strong AGN-driven winds (i.e. ∼2500 km/s) would only reduce
star formation in the galaxy by a factor of 2 (DeGraf et al. 2017).
The TNG100 simulation has a much lower spatial resolution
(i.e. a softening length of ∼0.74 kpc at _z_ = 1), and is therefore
not able to resolve the AGN-feedback interactions correctly. The
sub-grid model of AGN feedback used in the _IllustrisTNG_ has
already been advocated to be responsible for a lower submillimetre galaxies (SMGs) number counts compared to observations (Hayward et al. 2021). The first _James_ _Webb_ Space Telescope ( _JWS T_ ) results interestingly go in the same direction: the
number of bright, possibly massive, galaxies is found to exceed
predictions at high _z_ (Finkelstein et al. 2022; Donnan et al. 2023;
Mason et al. 2023). This discrepancy on ρ SFR could be a starting
point to the underestimation of the global ρ SFR in TNG100 for
(1 ≤ _z_ ≤ 2) reported early by Donnari et al. (2019) or non-trivial
issues in the simulated galaxy and halo populations found in the
Illustris simulation (Nelson et al. 2015).


_8.3._ _The SFE and Kennicutt-Schmidt relation_


Through this work, we have obtained a measurement of both
SFR and _M_ gas of main sequence galaxies over various redshift
and _M_ ⋆ bins. We can thus deduce the corresponding SFE of
main sequence galaxies (i.e. examine the SFR- _M_ gas plane) and
its evolution as a function of redshift and _M_ ⋆ . We display the
SFE deduced from this work in Fig. 19, where, bins of redshift were regrouped into 3 bins to empathise results discussed
later on.
The SFE we measured shows an increase with redshift,
which is accentuated at the highest masses. To investigate
whether the evolution of SFE can be explained by the gas
content of galaxies at high redshift we look at the KennicuttSchmidt relation (Kennicutt 1998b). The Kennicutt-Schmidt
relation illustrates similar properties by examining SFR and _M_ gas



**Fig. 18.** SFR as a function of _M_ ⋆ for SFGs in TNG100. Coloured lines
represent the best-fit from this work (see Table 5).


surface density (i.e. Σ SFR and Σ gas respectively):


Σ SFR = _S FR_ /(2π _R_ [2] e [)][,] (23)


Σ gas = _M_ gas /(2π _R_ [2] e [)][.] (24)


It also links them as:


log 10 (Σ SFR ) = _A_ + _N_ × log 10 (Σ gas ). (25)


We do not probe _R_ e in this study, thus, we chose to use _R_ e ( _z_, _M_ ⋆ ),
for galaxies with _M_ ⋆ ≥ 10 [10], from Wang et al. (2022). We
divided galaxies into bins of redshift (0 ≤ _z_ ≤ 6) and _M_ ⋆
(10 ≤ log 10 ( _M_ ⋆ ) ≤ 12). When fitting all bins, we added the
sample with low redshift and low _M_ ⋆ from Kennicutt (1998b).
The error on the fit was generated by randomly varying the bin
values within the uncertainties of the corresponding bin. We display the Schmidt-Kennicutt relation deduced from this work in
Fig. 20.
All studies agree on a linear dependence of log 10 (Σ SFR ) as a
function of log 10 (Σ gas ) with an overall slope ranging from 1 to
1.5 (e.g. Kennicutt 1998b; Wang et al. 2022), with no evolution
of the slope or normalisation with redshift or _M_ ⋆ . Our best-fit,
over all redshifts and _M_ ⋆ bins, also suggests a power-law scaling
with a slope of _N_ = 1.18 − [+] 0 [0] . [.] 01 [01] [.]
We found that Σ SFR = _A_ × (Σ SFR ) _[N]_ with _N_ ∼ 1.18 which
means that an increase in _M_ gas induces some increase in SFE
(i.e. SFE ∼ (M gas ) [0][.][18] ). It would not be the case if the slope of
the Kennicutt-Schmidt relation was _N_ = 1 as in Tacconi et al.
(2013). We can correct Fig. 19 from this effect by plotting
SFE/ _M_ gas [(] _[N]_ [−][1)] instead of SFE (see Fig. 21).
At _z_ ≤ 2, in Fig. 21, the normalisation does not evolve much
with redshift. On the other hand, in Fig. 7, _M_ gas increases with
redshift and _M_ ⋆ at _z_ ≤ 2. This means that an increase in SFR as
a function of redshift or stellar mass, at _z_ ≤ 2, is mainly due to
the variation of _M_ gas .
At _z_  - 2, in Fig. 21, the normalisation increases with redshift: by a factor ∼3 between _z_ ∼ 2 and _z_ ∼ 4.3. On the other
hand, in Fig. 7, _M_ gas remains roughly constant for _z_ - 2. This


A248, page 19 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)



**Fig. 19.** SFE as a function of stellar mass. Squares linked with a dashed
line represent the measured from this work, colour coded by bin of redshift. Dotted lines are the value SFE deduced from our best fit law of
the SFR and _M_ gas main sequences.


**Fig. 20.** Kennicutt-Schmidt relation: Σ SFR as a function of Σ gas . The dots
represent the data from this work, and are colour coded by redshift.
The cyan squared error bar represents the median of the sample distribution from Kennicutt (1998b), with individual galaxies displayed as
grey crosses. The dashed black line represents the best-fit of all points.
Coloured lines represent the best-fit, by fixing the slope to the all points
best-fit value (i.e. _N_ = 1.18 [+] − [0] 0 [.] . [01] 01 [), at fix redshift.]


means that the SFE plays a non-negligible role in increasing the
normalisation of the main sequence SFR between 2 ≤ _z_ ≤ 4.3.
In Fig. 21, we can see that the increase of SFE seen in Fig. 19
cannot be explained by the amount of gas as it is still appearing
in Fig. 21.
Overall, it means that, we need to differentiate two effects:
an increase of SFE due to the increase of _M_ gas, and an intrinsic increase in SFE. For example, at fixed stellar mass for
10.5 ≤ log 10 ( _M_ ⋆ / _M_ ⊙ ) ≤ 11 between _z_ = 1.15 and _z_ = 2,
SFR increases by a factor ∼4 (see Fig. 5), while _M_ gas increase
by a factor ∼1.6 (see Fig. 7): it means that SFE increases by


A248, page 20 of 25



**Fig.** **21.** SFE/ _M_ gas [(] _[N]_ [−][1)] ( _N_ = 1.18) as a function of stellar mass. Squares
linked with a dashed line represent the measured from this work, colour
coded by bin of redshift.


a factor ∼2.5, which reflects the increase of the normalisation
in Fig. 19 by ∼2.5 for the same redshift range. The first effect
in an increase of SFE due to the increase of _M_ gas (i.e. resulting from the Kennicutt-Schmidt relation of slope _N_ ∼ 1.18):
α [due to] SFE _[M]_ [gas] [∼] [α] _[N]_ _M_ [1] gas [=] [(1][.][6)] [0][.][18] [∼] [1][.][09.] [The] [second] [e][ff][ect] [is] [an]
intrinsic increase in SFE between the two redshifts (i.e. independent of the increase of _M_ gas ): α [intrinsic] SFE ∼ α SFE /α due toSFE _M_ gas ∼ 2.3.
Finally, we could conclude by saying that a factor ∼2.3 is solely
due to an increase of SFE, and a factor ∼α _M_ gas ×α due toSFE _M_ gas = 1.75
is due to the increase of _M_ gas .
We note that this effect is not inherent to our specific data
points, or even best-fit evolution laws of SFR and _M_ gas, as a similar evolution could be observed if we were to generate catalogues from the laws of S15 for SFR, and Wang et al. (2022) or
Tacconi et al. (2018) for _M_ gas (following the method used to generate ρ SFR and ρ gas see Sects. 6 and 7). If we were to choose laws
from Speagle et al. (2014) for SFR and Tacconi et al. (2018) for
_M_ gas, this effect would disappear completely, and we would end
up observing an evolution of the SFE with redshift. We conclude,
in this case, that the correct normalisation and the presence of the
bending of the main sequence (which are lacking in the study
of Speagle et al. 2014) are essential to observe this effect. One
could advocate that the observation of an increase in efficiency
with redshift when generating catalogues, for example, from S15
for SFR, and Tacconi et al. (2018) for _M_ gas, comes from the fact
that the _M_ gas fitting form from Tacconi et al. (2018), or the one
use in this work, do not allow a bending or an evolution of it.
However, we found no evidence of a bending or its evolution
at high mass when we tried to fit our data using various forms
allowing them. Overall, it suggests that some physical processes
limit the star formation efficiency in low-redshift galaxies, as
compared to high-redshift galaxies, beyond the simple fact that
they have less available gas.
Overall, even though the evolution of the SFE with
redshift is not well constrained, this study suggests that
galaxies at high-redshift form stars more efficiently at a
fixed gas surface density. This excess cannot be explained
by a universal Kennicutt-Schmidt relation nor SFE over
all redshifts. This may partly explain the early results of
_JWST_ : a higher ρ UV at _z_ ≥ 8 (Finkelstein et al. 2023;
Donnan et al. 2023; Mason et al. 2023) compared to pre- _JWST_
extrapolation Oesch et al. (2018); more massive galaxies at
_z_ ≥ 5 (Labbe et al. 2023; Xiao et al. 2023a). This may

Leroy, L., et al.: A&A, 691, A248 (2024)



be explained by the model proposed by Dekel et al. (2023)
who showed that the environment of the most massive darkmatter haloes at _z_ ≥ 10 favour high star formation efficiencies.
In conclusion, the gradual appearance of the bending of the
main sequence with redshift appears to result from a reduction
of the SFE, that is, a gradual disappearance of this extra factor
affecting the SFE (observed at _z_ ∼ 4.3 and absent at _z_ ∼ 2). Then,
at a fixed lower redshift (i.e. _z_ < 2), the bending of the main
sequence (as _M_ ⋆ increases) is mainly due to an increase in _M_ gas
with stellar mass, and to second order, to a decrease in SFE with
stellar mass. This characteristics is also observed in the local universe (i.e. for 0.01 < _z_ < 0.05) in Saintonge et al. (2016): when
the stellar mass increases by a factor 10, the SFR increases by
a factor ∼1.4, which is due to an increase of _M_ gas by a factor
∼1.8 and a decrease in SFE by a factor ∼1.25. Saintonge et al.
(2016) reach the same conclusion in the local universe: at a fixed
redshift, _M_ gas is the main reason for the bending of the main
sequence. The slow downfall of the star formation efficiency
in the most massive galaxies (i.e. _M_ ⋆ ≥ 10 [11] _M_ ⊙ ) observed
between 0.1 ≤ _z_ ≤ 4.3, was also observed in Schreiber et al.
(2016). It seems that a discontinuation of gas accretion cannot
be the only reason for the bending of the SFR main sequence
(Daddi et al. 2022). It must be coupled with other effects that
prevent the gas in high _M_ ⋆ galaxies from cooling and collapsing
into stars (i.e. an evolution of the SFE). The main driver of the
bending could be the quenching of galaxies due to environmental
effects, as massive galaxies populate denser environments where
they suffer from ram pressure stripping, galaxy harassment (e.g.
Kalita et al. 2022).


**9.** **Summary and conclusions**


For this work we gathered catalogues of _H_ -band selected SFGs
over four fields (GOODS-South, GOODS-North, COSMOS,
UDS). This sample is stacked over seven wavelengths (24 µm,
100 µm, 160 µm, 250 µm, 350 µm, 500 µm and 1.13 mm). The
main addition to this work, compared to previous studies, is
the use of the GOODS-ALMA survey (Gómez-Guijarro et al.
2022b), which helps to reach lower _M_ ⋆ and higher redshifts,
when combined with _Herschel_ . We combined the stacking of
_H_ -band selected galaxies with _H_ -dropout galaxy properties to
obtain a complete view of the cosmic history of galaxies. We
derived the evolution of MS galaxy properties such as SFR, _T_ dust,
and _M_ gas through a consistent analysis. We generated a detailed
view of ρ SFR and ρ gas depending on key galaxy properties such
as _M_ ⋆, _L_ IR and τ dep .
This study allowed us to confirm several features of galaxies,
the main ones being summarised as follows:

– The _T_ dust evolves linearly with redshift. There is no clear evidence for a dependence of _T_ dust depending on _M_ ⋆ at a fixed
redshift, when considering MS galaxies.
– The SFR- _M_ ⋆ MS has a slope close to unity at low masses
(i.e. _M_ ⋆ ≲ 10 [10] −10 [11] _M_ ⊙ ), with a bending appearing below
_z_ ∼ 2 on the high-mass end. The bending of the MS corresponds to the slow downfall of SFE in massive galaxies.
– The total ρ SFR follows a form close to the one presented in

Madau & Dickinson (2014), at least up to _z_ = 5. As a result,
the contribution of _H_ -dropout galaxies to the total ρ SFR is
∼13% at _z_ = 5.
The main new results from this paper can be summarised as
follows:

– We measured the contribution of galaxies of different _M_ ⋆ to
the total ρ SFR over cosmic time. We find that massive galaxies (i.e. _M_ ⋆ ≥ 10 [10] _M_ ⊙ ) account for most of the ρ SFR up to



_z_ ∼ 5. Low-mass galaxies (i.e. _M_ ⋆ ≤ 10 [10] _M_ ⊙ ) contribute a
roughly constant fraction to the total ρ SFR at 0.4 ≤ _z_ ≤ 5.
– The global discrepancy between the cosmic SFR density
observed and the TNG100 one is discussed in Pillepich et al.
(2018b). However, we show that the TNG100 simulation
fails to reproduce the contributions of the different bins of
_M_ ⋆ to the total ρ SFR . In particular, in the TNG100 simulation, massive galaxies do not form enough stars around
cosmic noon, when the cosmic SFR density peaks (i.e.
ρ SFR _[M]_ [⋆] [≥] − [10] TNG100 [10] _[M]_ [⊙] [≃] [50%][ ρ] SFR _[M]_ [⋆] [≥] − [10] observed [10] _[M]_ [⊙] [at] _[ z]_ [=] [2). We conclude that]
the mechanisms used to regulate star formation (in particular
feedback from AGNs) are possibly too strong in this simulation, namely too efficient at producing a drop in the gas
content in massive galaxies.
– We estimate that _H_ -dropout galaxies (as defined in
Wang et al. 2019) contribute to ∼23% of the ρ SFR of galaxies
with _M_ ⋆ ≥ 10 [10][.][3] _M_ ⊙ at _z_ = 4–6.
– We find hints that high-redshift galaxies convert their gas
reservoirs more efficiently than local galaxies, that is, suggesting a possible evolution of SFE with redshift.


_Acknowledgements._ This work was supported by the Programme National Cosmology et Galaxies (PNCG) of CNRS/INSU with INP and IN2P3, co-funded by
CEA and CNES. C.G.G. acknowledges support from CNES.


**References**


[Barro, G., Pérez-González, P. G., Cava, A., et al. 2019, ApJS, 243, 22](http://linker.aanda.org/10.1051/0004-6361/202348341/1)
[Bauermeister, A., Blitz, L., & Ma, C.-P. 2010, ApJ, 717, 323](http://linker.aanda.org/10.1051/0004-6361/202348341/2)
[Bavouzet, N., Dole, H., Le Floc’h, E., et al. 2008, A&A, 479, 83](http://linker.aanda.org/10.1051/0004-6361/202348341/3)
Berta, S., Lutz, D., Genzel, R., Förster-Schreiber, N. M., & Tacconi, L. J. 2016,

[A&A, 587, A73](http://linker.aanda.org/10.1051/0004-6361/202348341/4)
[Béthermin, M., Dole, H., Cousin, M., & Bavouzet, N. 2010, A&A, 516, A43](http://linker.aanda.org/10.1051/0004-6361/202348341/5)
[Béthermin, M., Le Floc’h, E., Ilbert, O., et al. 2012, A&A, 542, A58](http://linker.aanda.org/10.1051/0004-6361/202348341/6)
[Béthermin, M., Kilbinger, M., Daddi, E., et al. 2014, A&A, 567, A103](http://linker.aanda.org/10.1051/0004-6361/202348341/7)
[Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113](http://linker.aanda.org/10.1051/0004-6361/202348341/8)
[Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2](http://linker.aanda.org/10.1051/0004-6361/202348341/9)
[Biernacki, P., & Teyssier, R. 2018, MNRAS, 475, 5688](http://linker.aanda.org/10.1051/0004-6361/202348341/10)
[Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846](http://linker.aanda.org/10.1051/0004-6361/202348341/11)
[Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207](http://linker.aanda.org/10.1051/0004-6361/202348341/12)
[Bourne, N., Maddox, S. J., Dunne, L., et al. 2012, MNRAS, 421, 3027](http://linker.aanda.org/10.1051/0004-6361/202348341/13)
[Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2012a, ApJ, 754, 83](http://linker.aanda.org/10.1051/0004-6361/202348341/14)
[Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2012b, ApJ, 752, L5](http://linker.aanda.org/10.1051/0004-6361/202348341/15)
[Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015a, ApJ, 811, 140](http://linker.aanda.org/10.1051/0004-6361/202348341/16)
[Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015b, ApJ, 803, 34](http://linker.aanda.org/10.1051/0004-6361/202348341/17)
[Bouwens, R., González-López, J., Aravena, M., et al. 2020, ApJ, 902, 112](http://linker.aanda.org/10.1051/0004-6361/202348341/18)
[Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503](http://linker.aanda.org/10.1051/0004-6361/202348341/19)
[Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000](http://linker.aanda.org/10.1051/0004-6361/202348341/20)
[Calzetti, D., Kinney, A. L., & Storchi-Bergmann, T. 1994, ApJ, 429, 582](http://linker.aanda.org/10.1051/0004-6361/202348341/21)
[Casey, C. M., Zavala, J. A., Spilker, J., et al. 2018, ApJ, 862, 77](http://linker.aanda.org/10.1051/0004-6361/202348341/22)
[Chabrier, G. 2003, PASP, 115, 763](http://linker.aanda.org/10.1051/0004-6361/202348341/23)
[da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13](http://linker.aanda.org/10.1051/0004-6361/202348341/24)
[Daddi, E., Cimatti, A., Renzini, A., et al. 2004, ApJ, 617, 746](http://linker.aanda.org/10.1051/0004-6361/202348341/25)
[Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156](http://linker.aanda.org/10.1051/0004-6361/202348341/26)
[Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJ, 714, L118](http://linker.aanda.org/10.1051/0004-6361/202348341/27)
[Daddi, E., Delvecchio, I., Dimauro, P., et al. 2022, A&A, 661, L7](http://linker.aanda.org/10.1051/0004-6361/202348341/28)
[Davidzon, I., Ilbert, O., Laigle, C., et al. 2017, A&A, 605, A70](http://linker.aanda.org/10.1051/0004-6361/202348341/29)
[DeGraf, C., Dekel, A., Gabor, J., & Bournaud, F. 2017, MNRAS, 466, 1462](http://linker.aanda.org/10.1051/0004-6361/202348341/30)
[Dekel, A., Sarkar, K. S., Birnboim, Y., Mandelker, N., & Li, Z. 2023, MNRAS,](http://linker.aanda.org/10.1051/0004-6361/202348341/31)
[523, 3201](http://linker.aanda.org/10.1051/0004-6361/202348341/31)
[de los Reyes, M. A. C., & Kennicutt, R. C. Jr 2019, ApJ, 872, 16](http://linker.aanda.org/10.1051/0004-6361/202348341/32)
[Delvecchio, I., Daddi, E., Sargent, M. T., et al. 2021, A&A, 647, A123](http://linker.aanda.org/10.1051/0004-6361/202348341/33)
[Donnan, C. T., McLeod, D. J., Dunlop, J. S., et al. 2023, MNRAS, 518, 6011](http://linker.aanda.org/10.1051/0004-6361/202348341/34)
[Donnari, M., Pillepich, A., Nelson, D., et al. 2019, MNRAS, 485, 4817](http://linker.aanda.org/10.1051/0004-6361/202348341/35)
[Draine, B. T., & Li, A. 2007, ApJ, 657, 810](http://linker.aanda.org/10.1051/0004-6361/202348341/36)
[Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172](http://linker.aanda.org/10.1051/0004-6361/202348341/37)
[Drew, P. M., & Casey, C. M. 2022, ApJ, 930, 142](http://linker.aanda.org/10.1051/0004-6361/202348341/38)
[Elbaz, D., Daddi, E., Le Borgne, D., et al. 2007, A&A, 468, 33](http://linker.aanda.org/10.1051/0004-6361/202348341/39)
[Elbaz, D., Dickinson, M., Hwang, H. S., et al. 2011, A&A, 533, A119](http://linker.aanda.org/10.1051/0004-6361/202348341/40)
[Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110](http://linker.aanda.org/10.1051/0004-6361/202348341/41)
[Erb, D. K., Shapley, A. E., Pettini, M., et al. 2006, ApJ, 644, 813](http://linker.aanda.org/10.1051/0004-6361/202348341/42)


A248, page 21 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)



Finkelstein, S. L., Bagley, M. B., Ferguson, H. C., et al. 2022, CEERS Key Paper
I: An Early Look into the First 500 Myr of Galaxy Formation with JWST
Finkelstein, S. L., Bagley, M. B., Ferguson, H. C., et al. 2023, ApJ, 946,
[L13](http://linker.aanda.org/10.1051/0004-6361/202348341/44)

[Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152](http://linker.aanda.org/10.1051/0004-6361/202348341/45)
[Franco, M., Elbaz, D., Zhou, L., et al. 2020, A&A, 643, A53](http://linker.aanda.org/10.1051/0004-6361/202348341/46)
[Fritz, J., Franceschini, A., & Hatziminaoglou, E. 2006, MNRAS, 366, 767](http://linker.aanda.org/10.1051/0004-6361/202348341/47)
[Gabor, J. M., & Bournaud, F. 2014, MNRAS, 441, 1615](http://linker.aanda.org/10.1051/0004-6361/202348341/48)
[Galametz, A., Grazian, A., Fontana, A., et al. 2013, ApJS, 206, 10](http://linker.aanda.org/10.1051/0004-6361/202348341/49)
[Galliano, F., Hony, S., Bernard, J. P., et al. 2011, A&A, 536, A88](http://linker.aanda.org/10.1051/0004-6361/202348341/50)
[Galliano, F., Nersesian, A., Bianchi, S., et al. 2021, A&A, 649, A18](http://linker.aanda.org/10.1051/0004-6361/202348341/51)
[Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20](http://linker.aanda.org/10.1051/0004-6361/202348341/52)
[Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022a, A&A, 658, A43](http://linker.aanda.org/10.1051/0004-6361/202348341/53)
[Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022b, A&A, 659, A196](http://linker.aanda.org/10.1051/0004-6361/202348341/54)
[Gómez-Guijarro, C., Magnelli, B., Elbaz, D., et al. 2023, A&A, 677, A34](http://linker.aanda.org/10.1051/0004-6361/202348341/55)
[Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3](http://linker.aanda.org/10.1051/0004-6361/202348341/56)
[Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, ApJS, 197, 35](http://linker.aanda.org/10.1051/0004-6361/202348341/57)
[Groves, B. A., Schinnerer, E., Leroy, A., et al. 2015, ApJ, 799, 96](http://linker.aanda.org/10.1051/0004-6361/202348341/58)
[Gruppioni, C., Béthermin, M., Loiacono, F., et al. 2020, A&A, 643, A8](http://linker.aanda.org/10.1051/0004-6361/202348341/59)
[Guo, K., Zheng, X. Z., & Fu, H. 2013, ApJ, 778, 23](http://linker.aanda.org/10.1051/0004-6361/202348341/60)
[Hao, L., Strauss, M. A., Fan, X., et al. 2005, AJ, 129, 1795](http://linker.aanda.org/10.1051/0004-6361/202348341/61)
[Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95](http://linker.aanda.org/10.1051/0004-6361/202348341/62)
[Hatziminaoglou, E., Omont, A., Stevens, J. A., et al. 2010, A&A, 518, L33](http://linker.aanda.org/10.1051/0004-6361/202348341/63)
[Hayward, C. C., Sparre, M., Chapman, S. C., et al. 2021, MNRAS, 502, 2922](http://linker.aanda.org/10.1051/0004-6361/202348341/64)
[Hodge, J. A., & da Cunha, E. 2020, R. Soc. Open Sci., 7, 200556](http://linker.aanda.org/10.1051/0004-6361/202348341/65)
[Kaasinen, M., Scoville, N., Walter, F., et al. 2019, ApJ, 880, 15](http://linker.aanda.org/10.1051/0004-6361/202348341/66)
[Kalita, B. S., Daddi, E., Bournaud, F., et al. 2022, A&A, 666, A44](http://linker.aanda.org/10.1051/0004-6361/202348341/67)
[Kennicutt, R. C., Jr 1998a, ARA&A, 36, 189](http://linker.aanda.org/10.1051/0004-6361/202348341/68)
[Kennicutt, R. C., Jr 1998b, ApJ, 498, 541](http://linker.aanda.org/10.1051/0004-6361/202348341/69)
[Kewley, L. J., & Dopita, M. A. 2002, ApJS, 142, 35](http://linker.aanda.org/10.1051/0004-6361/202348341/70)
[Kewley, L. J., & Ellison, S. L. 2008, ApJ, 681, 1183](http://linker.aanda.org/10.1051/0004-6361/202348341/71)
[Khusanova, Y., Bethermin, M., Le Fèvre, O., et al. 2021, A&A, 649, A152](http://linker.aanda.org/10.1051/0004-6361/202348341/72)
[Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS, 197, 36](http://linker.aanda.org/10.1051/0004-6361/202348341/73)
[Kurczynski, P., & Gawiser, E. 2010, AJ, 139, 1592](http://linker.aanda.org/10.1051/0004-6361/202348341/74)
[Labbe, I., van Dokkum, P., Nelson, E., et al. 2023, Nature, 616, 266](http://linker.aanda.org/10.1051/0004-6361/202348341/75)
[Lagache, G. 2018, in Peering towards Cosmic Dawn, eds. V. Jeli´c, & T. van der](http://linker.aanda.org/10.1051/0004-6361/202348341/76)
Hulst, 333, 228
[Lagos, C. d. P., Crain, R. A., Schaye, J., et al. 2015, MNRAS, 452, 3815](http://linker.aanda.org/10.1051/0004-6361/202348341/77)
[Lee, N., Sanders, D. B., Casey, C. M., et al. 2015, ApJ, 801, 80](http://linker.aanda.org/10.1051/0004-6361/202348341/78)
[LeFloc’h, E., Aussel, H., Ilbert, O., et al. 2009, ApJ, 703, 222](http://linker.aanda.org/10.1051/0004-6361/202348341/79)
[Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782](http://linker.aanda.org/10.1051/0004-6361/202348341/80)
[Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12](http://linker.aanda.org/10.1051/0004-6361/202348341/81)
[Leslie, S. K., Schinnerer, E., Liu, D., et al. 2020, ApJ, 899, 58](http://linker.aanda.org/10.1051/0004-6361/202348341/82)
[Lewis, Z. J., Andrews, B. H., Bezanson, R., et al. 2024, ApJ, 964, 59](http://linker.aanda.org/10.1051/0004-6361/202348341/83)
[Liu, D., Daddi, E., Dickinson, M., et al. 2018, ApJ, 853, 172](http://linker.aanda.org/10.1051/0004-6361/202348341/84)
[Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235](http://linker.aanda.org/10.1051/0004-6361/202348341/85)
[Lutz, D., Poglitsch, A., Altieri, B., et al. 2011, A&A, 532, A90](http://linker.aanda.org/10.1051/0004-6361/202348341/86)
[Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415](http://linker.aanda.org/10.1051/0004-6361/202348341/87)
[Madau, P., Pozzetti, L., & Dickinson, M. 1998, ApJ, 498, 106](http://linker.aanda.org/10.1051/0004-6361/202348341/88)
[Magdis, G. E., Daddi, E., Elbaz, D., et al. 2011, ApJ, 740, L15](http://linker.aanda.org/10.1051/0004-6361/202348341/89)
[Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6](http://linker.aanda.org/10.1051/0004-6361/202348341/90)
[Magdis, G. E., Rigopoulou, D., Daddi, E., et al. 2017, A&A, 603, A93](http://linker.aanda.org/10.1051/0004-6361/202348341/91)
[Magnelli, B., Elbaz, D., Chary, R. R., et al. 2009, A&A, 496, 57](http://linker.aanda.org/10.1051/0004-6361/202348341/92)
[Magnelli, B., Saintonge, A., Lutz, D., et al. 2012, A&A, 548, A22](http://linker.aanda.org/10.1051/0004-6361/202348341/93)
[Magnelli, B., Popesso, P., Berta, S., et al. 2013, A&A, 553, A132](http://linker.aanda.org/10.1051/0004-6361/202348341/94)
[Magnelli, B., Lutz, D., Saintonge, A., et al. 2014, A&A, 561, A86](http://linker.aanda.org/10.1051/0004-6361/202348341/95)
[Magnelli, B., Boogaard, L., Decarli, R., et al. 2020, ApJ, 892, 66](http://linker.aanda.org/10.1051/0004-6361/202348341/96)
Mannucci, F., Cresci, G., Maiolino, R., Marconi, A., & Gnerucci, A. 2010,

[MNRAS, 408, 2115](http://linker.aanda.org/10.1051/0004-6361/202348341/97)
[Marinacci, F., Vogelsberger, M., Pakmor, R., et al. 2018, MNRAS, 480, 5113](http://linker.aanda.org/10.1051/0004-6361/202348341/98)
[Mason, C. A., Trenti, M., & Treu, T. 2023, MNRAS, 521, 497](http://linker.aanda.org/10.1051/0004-6361/202348341/99)


A248, page 22 of 25



[Millard, J. S., Eales, S. A., Smith, M. W. L., et al. 2020, MNRAS, 494, 293](http://linker.aanda.org/10.1051/0004-6361/202348341/100)
[Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJ, 777, 18](http://linker.aanda.org/10.1051/0004-6361/202348341/101)
[Naiman, J. P., Pillepich, A., Springel, V., et al. 2018, MNRAS, 477, 1206](http://linker.aanda.org/10.1051/0004-6361/202348341/102)
[Nayyeri, H., Hemmati, S., Mobasher, B., et al. 2017, ApJS, 228, 7](http://linker.aanda.org/10.1051/0004-6361/202348341/103)
[Nelson, D., Pillepich, A., Genel, S., et al. 2015, Astron. Comput., 13, 12](http://linker.aanda.org/10.1051/0004-6361/202348341/104)
[Nelson, D., Pillepich, A., Springel, V., et al. 2018, MNRAS, 475, 624](http://linker.aanda.org/10.1051/0004-6361/202348341/105)
[Nelson, D., Springel, V., Pillepich, A., et al. 2019, Comput. Astrophys. Cosmol.,](http://linker.aanda.org/10.1051/0004-6361/202348341/106)
[6, 2](http://linker.aanda.org/10.1051/0004-6361/202348341/106)
[Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJ, 660, L43](http://linker.aanda.org/10.1051/0004-6361/202348341/107)
[Novak, M., Smolˇci´c, V., Delhaize, J., et al. 2017, A&A, 602, A5](http://linker.aanda.org/10.1051/0004-6361/202348341/108)
Oesch, P. A., Bouwens, R. J., Illingworth, G. D., Labbé, I., & Stefanon, M. 2018,

[ApJ, 855, 105](http://linker.aanda.org/10.1051/0004-6361/202348341/109)
[Pannella, M., Elbaz, D., Daddi, E., et al. 2015, ApJ, 807, 141](http://linker.aanda.org/10.1051/0004-6361/202348341/110)
[Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59](http://linker.aanda.org/10.1051/0004-6361/202348341/111)
[Pillepich, A., Nelson, D., Hernquist, L., et al. 2018a, MNRAS, 475, 648](http://linker.aanda.org/10.1051/0004-6361/202348341/112)
[Pillepich, A., Springel, V., Nelson, D., et al. 2018b, MNRAS, 473, 4077](http://linker.aanda.org/10.1051/0004-6361/202348341/113)
[Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 490, 3196](http://linker.aanda.org/10.1051/0004-6361/202348341/114)
Popesso, P., Magnelli, B., Buttiglione, S., et al. 2012, A&A, submitted

[arXiv: `[1211.4257](https://arxiv.org/abs/1211.4257)` ]
[Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526](http://linker.aanda.org/10.1051/0004-6361/202348341/116)
[Reddy, N. A., Steidel, C. C., Erb, D. K., Shapley, A. E., & Pettini, M. 2006, ApJ,](http://linker.aanda.org/10.1051/0004-6361/202348341/117)
[653, 1004](http://linker.aanda.org/10.1051/0004-6361/202348341/117)
[Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31](http://linker.aanda.org/10.1051/0004-6361/202348341/118)
[Richards, G. T., Lacy, M., Storrie-Lombardi, L. J., et al. 2006, ApJS, 166, 470](http://linker.aanda.org/10.1051/0004-6361/202348341/119)
[Rowan-Robinson, M., Oliver, S., Wang, L., et al. 2016, MNRAS, 461, 1100](http://linker.aanda.org/10.1051/0004-6361/202348341/120)
[Saintonge, A., Catinella, B., Cortese, L., et al. 2016, MNRAS, 462, 1749](http://linker.aanda.org/10.1051/0004-6361/202348341/121)
[Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22](http://linker.aanda.org/10.1051/0004-6361/202348341/122)
[Salpeter, E. E. 1955, ApJ, 121, 161](http://linker.aanda.org/10.1051/0004-6361/202348341/123)
[Santini, P., Fontana, A., Grazian, A., et al. 2012, A&A, 538, A33](http://linker.aanda.org/10.1051/0004-6361/202348341/124)
[Sargent, M. T., Béthermin, M., Daddi, E., & Elbaz, D. 2012, ApJ, 747, L31](http://linker.aanda.org/10.1051/0004-6361/202348341/125)
[Schenker, M. A., Robertson, B. E., Ellis, R. S., et al. 2013, ApJ, 768, 196](http://linker.aanda.org/10.1051/0004-6361/202348341/126)
[Schinnerer, E., Groves, B., Sargent, M. T., et al. 2016, ApJ, 833, 112](http://linker.aanda.org/10.1051/0004-6361/202348341/127)
[Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74](http://linker.aanda.org/10.1051/0004-6361/202348341/128)
[Schreiber, C., Elbaz, D., Pannella, M., et al. 2016, A&A, 589, A35](http://linker.aanda.org/10.1051/0004-6361/202348341/129)
[Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30](http://linker.aanda.org/10.1051/0004-6361/202348341/130)
[Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84](http://linker.aanda.org/10.1051/0004-6361/202348341/131)
[Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83](http://linker.aanda.org/10.1051/0004-6361/202348341/132)
[Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150](http://linker.aanda.org/10.1051/0004-6361/202348341/133)
[Shirley, R., Duncan, K., Campos Varillas, M. C., et al. 2021, MNRAS, 507, 129](http://linker.aanda.org/10.1051/0004-6361/202348341/134)
Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, [ApJS,](http://linker.aanda.org/10.1051/0004-6361/202348341/135)
[214, 15](http://linker.aanda.org/10.1051/0004-6361/202348341/135)
[Springel, V., Pakmor, R., Pillepich, A., et al. 2018, MNRAS, 475, 676](http://linker.aanda.org/10.1051/0004-6361/202348341/136)
Steidel, C. C., Adelberger, K. L., Giavalisco, M., Dickinson, M., & Pettini, M.
[1999, ApJ, 519, 1](http://linker.aanda.org/10.1051/0004-6361/202348341/137)
[Suess, K. A., Kriek, M., Price, S. H., & Barro, G. 2019, ApJ, 885, L22](http://linker.aanda.org/10.1051/0004-6361/202348341/138)
[Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781](http://linker.aanda.org/10.1051/0004-6361/202348341/139)
[Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74](http://linker.aanda.org/10.1051/0004-6361/202348341/140)
[Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179](http://linker.aanda.org/10.1051/0004-6361/202348341/141)
[Traina, A., Gruppioni, C., Delvecchio, I., et al. 2024, A&A, 681, A118](http://linker.aanda.org/10.1051/0004-6361/202348341/142)
[Viero, M. P., Moncelsi, L., Quadri, R. F., et al. 2013, ApJ, 779, 32](http://linker.aanda.org/10.1051/0004-6361/202348341/143)
[Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211](http://linker.aanda.org/10.1051/0004-6361/202348341/144)
[Wang, T.-M., Magnelli, B., Schinnerer, E., et al. 2022, A&A, 660, A142](http://linker.aanda.org/10.1051/0004-6361/202348341/145)
[Weinberger, R., Springel, V., Hernquist, L., et al. 2017, MNRAS, 465, 3291](http://linker.aanda.org/10.1051/0004-6361/202348341/146)
[Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJ, 754,](http://linker.aanda.org/10.1051/0004-6361/202348341/147)
[L29](http://linker.aanda.org/10.1051/0004-6361/202348341/147)
[Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104](http://linker.aanda.org/10.1051/0004-6361/202348341/148)
White, R. L., Helfand, D. J., Becker, R. H., Glikman, E., & de Vries, W. 2007,

[ApJ, 654, 99](http://linker.aanda.org/10.1051/0004-6361/202348341/149)
Xiao, M., Oesch, P., Elbaz, D., et al. 2023a, ArXiv e-prints [arXiv: `[2309.02492](https://arxiv.org/abs/2309.02492)` ]
[Xiao, M. Y., Elbaz, D., Gómez-Guijarro, C., et al. 2023b, A&A, 672, A18](http://linker.aanda.org/10.1051/0004-6361/202348341/151)
[Zhou, L., Elbaz, D., Franco, M., et al. 2020, A&A, 642, A155](http://linker.aanda.org/10.1051/0004-6361/202348341/152)

Leroy, L., et al.: A&A, 691, A248 (2024)


**Appendix A:** **Table of gas masses**


**Table A.1.** Summary of the gas masses derived in this work.


Redshift bin _M_ ⋆ bin _S_ 1.13 mm [µJy] _M_ gas [Scoville16] [ _M_ ⊙ ] _M_ dust [ _M_ ⊙ ] 12 + log 10 ( _O_ / _H_ ) _M_ gas [MZR] [ _M_ ⊙ ]

0.1 ≤ _z_ ≤ 0.4 8.5 ≤ log 10 ( _M_ ⋆ ) ≤ 9.5 6.99 [+] − [0] 0 [.] . [28] 06 8.31 [+] − [0] 0 [.] . [2] 2 9.31 [+] − [0] 0 [.] . [34] 21
0.1 ≤ _z_ ≤ 0.4 9.5 ≤ log 10 ( _M_ ⋆ ) ≤ 10.0 7.5 [+] − [0] 0 [.] . [04] 06 8.58 [+] − [0] 0 [.] . [2] 2 9.55 [+] − [0] 0 [.] . [2] 21
0.1 ≤ _z_ ≤ 0.4 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 7.88 [+] − [0] 0 [.] . [06] 09 8.68 [+] − [0] 0 [.] . [2] 2 9.83 [+] − [0] 0 [.] . [21] 22
0.1 ≤ _z_ ≤ 0.4 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 8.1 [+] − [0] 0 [.] . [1] 03 8.72 [+] − [0] 0 [.] . [2] 2 10.01 [+] − [0] 0 [.] . [22] 2
0.1 ≤ _z_ ≤ 0.4 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 8.12 [+] − [0] 0 [.] . [55] 11 8.74 [+] − [0] 0 [.] . [2] 2 10.01 [+] − [0] 0 [.] . [58] 23
0.4 ≤ _z_ ≤ 0.7 9.5 ≤ log 10 ( _M_ ⋆ ) ≤ 10.0 7.49 [+] − [0] 0 [.] . [04] 03 8.48 [+] − [0] 0 [.] . [2] 2 9.63 − [+] 0 [0] . [.] 2 [2]
0.4 ≤ _z_ ≤ 0.7 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 0.1 [+] − [0] 0 [.] . [03] 03 9.91 − [+] 0 [0] . [.] 11 [13] 7.82 [+] − [0] 0 [.] . [02] 01 8.61 [+] − [0] 0 [.] . [2] 2 9.83 − [+] 0 [0] . [.] 2 [2]
0.4 ≤ _z_ ≤ 0.7 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.12 [+] − [0] 0 [.] . [05] 04 9.98 − [+] 0 [0] . [.] 16 [19] 8.13 [+] − [0] 0 [.] . [02] 04 8.69 [+] − [0] 0 [.] . [2] 2 10.07 [+] − [0] 0 [.] . [2] 2
0.4 ≤ _z_ ≤ 0.7 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 8.29 [+] − [0] 0 [.] . [11] 13 8.73 [+] − [0] 0 [.] . [2] 2 10.19 [+] − [0] 0 [.] . [22] 24
0.7 ≤ _z_ ≤ 1.0 9.5 ≤ log 10 ( _M_ ⋆ ) ≤ 10.0 7.47 [+] − [0] 0 [.] . [09] 08 8.4 − [+] 0 [0] . [.] 2 [2] 9.69 [+] − [0] 0 [.] . [22] 21
0.7 ≤ _z_ ≤ 1.0 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 7.89 [+] − [0] 0 [.] . [03] 04 8.55 [+] − [0] 0 [.] . [2] 2 9.97 − [+] 0 [0] . [.] 2 [2]
0.7 ≤ _z_ ≤ 1.0 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.14 [+] − [0] 0 [.] . [04] 05 10.16 [+] − [0] 0 [.] . [13] 14 8.25 [+] − [0] 0 [.] . [04] 02 8.65 [+] − [0] 0 [.] . [2] 2 10.23 [+] − [0] 0 [.] . [2] 2
0.7 ≤ _z_ ≤ 1.0 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 8.38 [+] − [0] 0 [.] . [04] 02 8.71 [+] − [0] 0 [.] . [2] 2 10.29 [+] − [0] 0 [.] . [2] 2
1.0 ≤ _z_ ≤ 1.3 9.5 ≤ log 10 ( _M_ ⋆ ) ≤ 10.0 7.51 [+] − [0] 0 [.] . [2] 19 8.32 [+] − [0] 0 [.] . [2] 2 9.81 [+] − [0] 0 [.] . [28] 28
1.0 ≤ _z_ ≤ 1.3 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 7.88 [+] − [0] 0 [.] . [02] 07 8.48 [+] − [0] 0 [.] . [2] 2 10.02 [+] − [0] 0 [.] . [2] 21
1.0 ≤ _z_ ≤ 1.3 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.12 [+] − [0] 0 [.] . [02] 03 10.11 [+] − [0] 0 [.] . [09] 1 8.17 [+] − [0] 0 [.] . [02] 01 8.62 [+] − [0] 0 [.] . [2] 2 10.18 [+] − [0] 0 [.] . [2] 2
1.0 ≤ _z_ ≤ 1.3 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 8.7 [+] − [0] 0 [.] . [02] 04 8.69 [+] − [0] 0 [.] . [2] 2 10.64 [+] − [0] 0 [.] . [2] 2
1.3 ≤ _z_ ≤ 1.8 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 7.7 − [+] 0 [0] . [.] 0 [01] 8.41 [+] − [0] 0 [.] . [2] 2 9.91 − [+] 0 [0] . [.] 2 [2]
1.3 ≤ _z_ ≤ 1.8 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.15 [+] − [0] 0 [.] . [03] 03 10.25 [+] − [0] 0 [.] . [09] 09 8.29 [+] − [0] 0 [.] . [01] 05 8.56 [+] − [0] 0 [.] . [2] 2 10.36 [+] − [0] 0 [.] . [2] 2
1.3 ≤ _z_ ≤ 1.8 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 0.43 [+] − [0] 0 [.] . [09] 1 10.71 [+] − [0] 0 [.] . [09] 1 8.71 [+] − [0] 0 [.] . [02] 01 8.65 [+] − [0] 0 [.] . [2] 2 10.68 [+] − [0] 0 [.] . [2] 2
1.8 ≤ _z_ ≤ 2.3 9.5 ≤ log 10 ( _M_ ⋆ ) ≤ 10.0 7.7 [+] − [0] 0 [.] . [04] 1 8.13 [+] − [0] 0 [.] . [2] 2 10.19 [+] − [0] 0 [.] . [2] 22
1.8 ≤ _z_ ≤ 2.3 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 0.1 [+] − [0] 0 [.] . [03] 02 10.04 [+] − [0] 0 [.] . [11] 09 7.72 [+] − [0] 0 [.] . [06] 03 8.34 [+] − [0] 0 [.] . [2] 2 10.0 [+] − [0] 0 [.] . [21] 2
1.8 ≤ _z_ ≤ 2.3 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.21 [+] − [0] 0 [.] . [03] 03 10.39 [+] − [0] 0 [.] . [06] 06 8.25 [+] − [0] 0 [.] . [01] 02 8.51 [+] − [0] 0 [.] . [2] 2 10.37 [+] − [0] 0 [.] . [2] 2
1.8 ≤ _z_ ≤ 2.3 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 0.46 [+] − [0] 0 [.] . [08] 04 10.73 [+] − [0] 0 [.] . [07] 04 8.58 [+] − [0] 0 [.] . [02] 04 8.62 [+] − [0] 0 [.] . [2] 2 10.58 [+] − [0] 0 [.] . [2] 2
2.3 ≤ _z_ ≤ 3.1 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 7.71 [+] − [0] 0 [.] . [02] 06 8.25 [+] − [0] 0 [.] . [2] 2 10.09 [+] − [0] 0 [.] . [2] 21
2.3 ≤ _z_ ≤ 3.1 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.32 [+] − [0] 0 [.] . [05] 04 10.55 [+] − [0] 0 [.] . [07] 05 8.14 [+] − [0] 0 [.] . [03] 04 8.43 [+] − [0] 0 [.] . [2] 2 10.33 [+] − [0] 0 [.] . [2] 2
2.3 ≤ _z_ ≤ 3.1 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 0.9 [+] − [0] 0 [.] . [18] 15 11.0 [+] − [0] 0 [.] . [09] 07 8.66 [+] − [0] 0 [.] . [08] 03 8.57 [+] − [0] 0 [.] . [2] 2 10.71 [+] − [0] 0 [.] . [21] 2
3.1 ≤ _z_ ≤ 3.9 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 0.08 [+] − [0] 0 [.] . [02] 02 9.95 − [+] 0 [0] . [.] 12 [1]
3.1 ≤ _z_ ≤ 3.9 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.29 − [+] 0 [0][.] . [16] 21 10.49 [+] − [0] 0 [.] . [23] 32 7.91 [+] − [0] 0 [.] . [12] 02 8.36 [+] − [0] 0 [.] . [2] 2 10.17 [+] − [0] 0 [.] . [23] 2
3.1 ≤ _z_ ≤ 3.9 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 0.91 [+] − [0] 0 [.] . [37] 37 10.98 [+] − [0] 0 [.] . [17] 17 8.57 [+] − [0] 0 [.] . [08] 09 8.51 [+] − [0] 0 [.] . [2] 2 10.69 [+] − [0] 0 [.] . [21] 22
3.9 ≤ _z_ ≤ 5.0 10.0 ≤ log 10 ( _M_ ⋆ ) ≤ 10.5 0.11 [+] − [0] 0 [.] . [03] 04 10.07 [+] − [0] 0 [.] . [13] 17
3.9 ≤ _z_ ≤ 5.0 10.5 ≤ log 10 ( _M_ ⋆ ) ≤ 11.0 0.37 − [+] 0 [0][.] . [19] 15 10.59 [+] − [0] 0 [.] . [23] 18 8.06 [+] − [0] 0 [.] . [2] 12 8.28 [+] − [0] 0 [.] . [2] 2 10.4 [+] − [0] 0 [.] . [28] 23
3.9 ≤ _z_ ≤ 5.0 11.0 ≤ log 10 ( _M_ ⋆ ) ≤ 12.0 0.7 [+] − [0] 0 [.] . [34] 34 10.86 [+] − [0] 0 [.] . [21] 21 8.35 [+] − [0] 0 [.] . [01] 13 8.5 − [+] 0 [0] . [.] 2 [2] 10.47 [+] − [0] 0 [.] . [2] 24


**Notes.** These gas masses do not include the possible contribution of _H_ -dropout.


A248, page 23 of 25

Leroy, L., et al.: A&A, 691, A248 (2024)


**Appendix B:** **Using only the Scoville16 method**


In this appendix, we look at the results that would be deduced
if we only considered gas masses that could be deduced from
our ALMA measurements and using the Scoville et al. (2016)
method to derive _M_ gas . This appendix goes through the accordingly updated Figures 7, 11, 12, 19, 20 and 21.
We follow the same method we went through in Sect. 5.3,
we add the contribution of the _H_ -dropouts to _M_ gas . In that case,
Eq. 20 allows to get an acceptable fit. Therefore, we chose to fit
the final _M_ gas with Eq. 20. Our best fit parameters are given in
Table B.1.


**Table B.1.** Best-fit parameters of _M_ gas evolution of the main sequence.


_A_ _B_ _F_ _D_ β [∗]



0.136 [+] − [0] 0 [.] . [235] 103 −1.68 − [+][0] 0 [.] . [56] 63 0.897 [+] − [0] 0 [.] . [151] 282 −0.321 [+] − [0] 0 [.] . [090] 088 2


**Notes.** Best-fit parameters of _M_ gas evolution of the main sequence using
Eq. 20 when using the method from Scoville et al. (2016) only. [∗] indicates that this parameter was fixed during the fit.


Our new gas masses measurements are deduced from the
method from Scoville et al. (2016) are displayed in Fig. B.1.
In Fig. B.1, we also compare our results to the trends observed
by Tacconi et al. (2018) and Wang et al. (2022). In Fig. B.1, the
trends are displayed for stellar mass bins in the Salpeter (1955)
IMF. Using this method, our results coincide with the one from
Wang et al. (2022), which is to be expected as they are both coming from a mass selected sample, deducing gas masses from
millimetre measurements through the method of Scoville et al.
(2016).
Next, the resulting gas mass densities are deduced through
the method we describe in Sect. 7. We display the results in
Fig. B.2. When deducing gas masses using the method from
Scoville et al. (2016) only we end up with results much closer
to what is found in the literature (e.g. Tacconi et al. 2018;
Wang et al. 2022).
We compare our results to Magnelli et al. (2020) in Fig. B.3.
Again, results are much more in line with what is found in
Magnelli et al. (2020).
Following the method we describe in Sect. 8.3, we computed the SFE corresponding to the gas masses deduced from
the method of Scoville et al. (2016). We display the results in
Fig. B.4. In that case, we can still observe an increase of the SFE
with redshift.
We also investigate whether the evolution of SFE can be
explained by the gas content of galaxies at high redshift by looking at the Kennicutt-Schmidt relation (Kennicutt 1998b). We follow the same method presented throughout Sect. 8.3. In that
case, our best-fit of the linear dependence of log 10 (Σ SFR ) as a
function of log 10 (Σ gas ) suggests a power-law scaling with a slope
of _N_ = 1.29 [+] − [0] 0 [.] . [01] 01 [. The results of the Kennicutt-Schmidt relation]
are shown in Fig. B.5. In Fig. B.5, an increase of the normalisation can still be observed at _z_ - 3. This effect is, however,
much more limited compared to the one observed though the
main studied (see Fig. 20).
We corrected the SFE from the gas contribution by looking
at SFE/ _M_ gas [(] _[N]_ [−][1)] instead of SFE (see Fig. B.6). In Fig. B.6, we
can still observe an evolution with redshift (i.e. SFE cannot be
explain only by the amount of _M_ gas ).


A248, page 24 of 25



**Fig.** **B.1.** _M_ gas as a function of redshift for different _M_ ⋆ . The
crosses represent _M_ gas estimates from this work following the method
from Scoville et al. (2016). The squares are measurements from
Saintonge et al. (2017). The bins that have been corrected for the _H_ dropout contribution are circled. The thick solid colour lines represent
the best-fit from this work using Eq. 20.The shaded area the 68% uncertainty of the fit. The faded solid lines represent the best-fit from this
work colour-coded by _M_ ⋆ (using Eq. 21), the faded dashed lines represent the trend from Tacconi et al. (2018), the faded dotted lines are from
Wang et al. (2022).


**Fig.** **B.2.** ρ gas as a function of redshift. The green dotted lines represent the total ρ gas inferred from this work (i.e. integrating the stellar mass function down to 3 × 10 [9] _M_ ⊙ ) using _M_ gas deduced with the
Scoville et al. (2016) method only. The red and blue dotted lines represent the contribution to the total ρ gas of galaxies with log 10 ( _M_ ⋆ ) - 10
and log 10 ( _M_ ⋆ ) < 10, respectively. The corresponding result deduced
throughout this paper are displayed in faded solid red, blue and green
coloured lines. The purple and cyan lines represent ρ gas deduced from
the _M_ gas definition of Wang et al. (2022) and Tacconi et al. (2018),
respectively.


Our conclusion on these results (i.e. using the method from
Scoville et al. (2016) to deduce gas masses) and the discrepancies observed from the ones of the main work of this paper (i.e.
using an MZR method to deduce gas masses from the IR to millimetre) is that the main reason these higher and evolving SFE
were not observed is mostly due to the method used to infer
the gas masses: IR to millimetre compared to millimetre only
methods.

Leroy, L., et al.: A&A, 691, A248 (2024)



**Fig. B.3.** ρ gas as a function of redshift. The green, orange and red dotted lines represent ρ gas derived from this work with _M_ ⋆ [lim] of 1.7 × 10 [8],
1.7 × 10 [9] and 1.7 × 10 [10] _M_ ⊙, respectively, using _M_ gas deduced with the
Scoville et al. (2016) method only. The corresponding result deduced
throughout this paper are displayed in faded solid red, orange and green
coloured lines. The green, orange and red hatches represent estimates
of ρ gas from Magnelli et al. (2020) with _M_ ⋆ [lim] of 1.7 × 10 [8], 1.7 × 10 [9]
and 1.7 × 10 [10] _M_ ⊙, respectively. The green dots with black circles depict
the estimate of ρ gas from Magnelli et al. (2020) for _M_ ⋆ - _M_ limit, _M_ limit
being the stellar mass completeness limit from Magnelli et al. (2020).


**Fig. B.4.** SFE as a function of stellar mass. Squares linked with a dashed
line represent the measured from this work when computed using _M_ gas
deduced with the Scoville et al. (2016) method only, colour coded by
bin of redshift. Dotted lines are the value SFE deduced from our best fit
law of the SFR and _M_ gas main sequences.



**Fig.** **B.5.** Kennicutt-Schmidt relation: Σ SFR as a function of Σ gas . The
dots represent the data from this work when computed using _M_ gas
deduced with the Scoville et al. (2016) method only, and are colour
coded by redshift. The cyan squared error bar represents the median of
the sample distribution from Kennicutt (1998b), with individual galaxies displayed as grey crosses. The dashed black line represents the bestfit of all points. Coloured lines represent the best-fit, by fixing the slope
to the all points best-fit value (i.e. _N_ = 1.29 [+] − [0] 0 [.] . [01] 01 [), at fix redshift.]


**Fig. B.6.** SFE/ _M_ gas [(] _[N]_ [−][1)] ( _N_ = 1.29) as a function of stellar mass. Squares
linked with a dashed line represent the measured from this work when
computed using _M_ gas deduced with the Scoville et al. (2016) method
only, colour coded by bin of redshift.


A248, page 25 of 25


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: archival_reuse",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "1.13 mm continuum",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "1.1 arcsec circularised PSF FWHM",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "data.sensitivity.evidence[0]",
  "value": "average sigma = 95.2 uJy beam^-1",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "data.pi_or_archival_as_stated.evidence[0]",
  "value": "GOODS-ALMA survey map from Gómez-Guijarro et al. (2022a)",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "data.other_facilities[3].provided.evidence[0]",
  "value": "NIRCam survey of the EGS field (CEERS) used to check H-band completeness at 3 < z < 5",
  "failed_quote": "To assess whether our derivation of the completeness limit remains relevant for the redshift range 3 < z < 5, we looked at a deep JWST-NIRCAM survey of the EGS field (Gómez-Guijarro et al. 2023)."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "1.13 mm low-resolution GOODS-ALMA map and astrometric offsets",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "processing.calibration.archive_products_used_as_is.evidence[0]",
  "value": "Used published 1.13 mm low-resolution GOODS-ALMA map from Gómez-Guijarro et al. (2022a)",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "1.1 arcsec circularised PSF FWHM",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "95.2 uJy beam^-1",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "1.13 mm low-resolution GOODS-ALMA mosaic map",
  "failed_quote": "For ALMA, we used the 1.13 mm low-resolution GOODS-ALMA map (sensitivity reaching an average of σ = 95.2 µJy beam−1, Gómez-Guijarro et al. 2022a), within the GOODS-South field with the 1′′. 1 circularised point spread function (PSF) full width half maximum (FWHM)."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Checked completeness at 3 < z < 5 against deep JWST-NIRCam CEERS survey in EGS, finding 89.7% of log10(M*/Msun) > 10 galaxies are detected in HST H-band",
  "failed_quote": "To assess whether our derivation of the completeness limit remains relevant for the redshift range 3 < z < 5, we looked at a deep JWST-NIRCAM survey of the EGS field (Gómez-Guijarro et al. 2023). We found that 89.7% of the galaxies with log10 (M⋆/M⊙) > 10 (209 galaxies detected, 233 overall) detected in the JWST bands are also detected in the HST H-band"
 },
 {
  "path": "analysis_steps[1].method.evidence[2]",
  "value": "Mean stack postage stamps of detected and undetected galaxies in bins of M* and z, rotating Herschel stamps by 90 deg successively. Measure fluxes via aperture photometry (Spitzer 24 um and ALMA 1.13 mm) or PSF + background fitting (Herschel PACS and SPIRE), and apply clustering and filtering corrections.",
  "failed_quote": "To measure ALMA flux densities, we applied an aperture photometry within a radius of 1′′, containing 85% of the total flux density (i.e. SPSF AP /S PSF tot = 0.85)."
 },
 {
  "path": "analysis_steps[1].key_parameters[2].evidence[0]",
  "value": "ALMA 1.13 mm aperture radius = 1 arcsec, S_AP^PSF / S_tot^PSF = 0.85",
  "failed_quote": "To measure ALMA flux densities, we applied an aperture photometry within a radius of 1′′, containing 85% of the total flux density (i.e. SPSF AP /S PSF tot = 0.85)."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[1]",
  "value": "Clustering bias is negligible in Spitzer 24 um and ALMA 1.13 mm stacks due to small PSF FWHM",
  "failed_quote": "As the ALMA 1.1mm map has a much better resolution (∼1′′. 1 PSF FWHM; which is comparable to typical sizes of individual SFGs, Suess et al. 2019; Wang et al. 2022) than Herschel-PACS (∼7′′ and ∼11′′. 3 PSF FWHM at 100 µm and 160 µm, respectively), the clustering bias is negligible on the stacked stamp."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Detection threshold S/N >= 3; non-detections and z > 4 MIPS 24 um fluxes set to 5 sigma upper limits",
  "failed_quote": "To fit the SED, we only considered fluxes with S/N ≥ 3. Stacked flux measurements with S/N < 3 are replaced by conservative 5σ upper limits. At z > 4 MIPS-24 stacked fluxes, if available, have been transformed to 5σ upper limits"
 },
 {
  "path": "analysis_steps[2].validation.evidence[1]",
  "value": "Compared S18 vs Draine & Li (2007) fits (differences -7% for L_IR, 1% for T_dust, 4% for M_dust); performed mock stacking simulations (bias -1% for L_IR, -6% for T_dust, 7% for M_dust); checked AGN contribution with Fritz et al. (2006) models (<10% L_IR) and CMB heating following da Cunha et al. (2013)",
  "failed_quote": "The relative differences between the actual average properties with those deduced from our stacking analysis are quite small: −1%+2% −4% for LIR, −6%+1% −2% for Tdust and 7%+2% −4% for Mdust."
 },
 {
  "path": "analysis_steps[2].validation.evidence[2]",
  "value": "Compared S18 vs Draine & Li (2007) fits (differences -7% for L_IR, 1% for T_dust, 4% for M_dust); performed mock stacking simulations (bias -1% for L_IR, -6% for T_dust, 7% for M_dust); checked AGN contribution with Fritz et al. (2006) models (<10% L_IR) and CMB heating following da Cunha et al. (2013)",
  "failed_quote": "We checked for any AGN contribution by fitting our SED with a combination of Draine & Li (2007) dust model, and Fritz et al. (2006) AGN model. No conclusive evidence for a major contribution (i.e. LAGN IR /LTOT IR ≥ 10%) from AGNs to the rest-frame FIR was found in any of our M⋆ and redshift bins."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Re-fitted Wang et al. (2019) H-dropout stack with S18 templates and added to 3.9 <= z <= 5.0 bin; compared MS fits with S15, Speagle et al. (2014), Leslie et al. (2020), and Daddi et al. (2022)",
  "failed_quote": "We re-fitted the stack of H-dropout from Wang et al. (2019) with S18 templates and deduced a TH-drop dust = 37.34+1.2 −1.27 K. The contribution of H-dropout from Wang et al. (2019) was then added to our last bin of redshift (i.e. 3.9 ≤ z ≤ 5)."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "M_gas ~ M_H2 holds for z > 0.4 (z < 0.4 excluded and supplemented with Saintonge et al. 2017 local data); PP04 N2 metallicity scale",
  "failed_quote": "In Tacconi et al. (2018), it was concluded that the assumption Mgas ∼ MH2 should hold for z > 0.4. Therefore, we decided not to consider our Mgas for z < 0.4 (i.e. our first redshift bin), as we could not probe the HI content of the galaxy at these redshifts."
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "Generate mock galaxy catalogues from the Davidzon et al. (2017) stellar mass functions, assign SFR and M_gas using the fitted MS relations and a double log-normal starburstiness (R_SB) distribution, integrate down to M*_lim = 3e9 Msun, compare with TNG100, and fit the Kennicutt-Schmidt relation using Wang et al. (2022) effective radii.",
  "failed_quote": "To calculate the ρSFR, we start from the stellar mass function of SFGs of Davidzon et al. (2017), that is given for different redshift bins. For each redshift bin, we generated galaxies with uniform redshift distribution within the bin, and a M⋆ distribution following these stellar mass functions."
 },
 {
  "path": "analysis_steps[5].method.evidence[1]",
  "value": "Generate mock galaxy catalogues from the Davidzon et al. (2017) stellar mass functions, assign SFR and M_gas using the fitted MS relations and a double log-normal starburstiness (R_SB) distribution, integrate down to M*_lim = 3e9 Msun, compare with TNG100, and fit the Kennicutt-Schmidt relation using Wang et al. (2022) effective radii.",
  "failed_quote": "Next, the cosmic evolution of gas density (ρgas) is calculated by summing the Mgas of galaxies down to Mlim ⋆ = 3 × 109 M⊙."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Dust temperature of H-dropout stack = 37.34 K",
  "failed_quote": "We re-fitted the stack of H-dropout from Wang et al. (2019) with S18 templates and deduced a TH-drop dust = 37.34+1.2 −1.27 K."
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Gas mass evolution parameter m_0 (Eq. 21) = 1.93 dimensionless",
  "failed_quote": "1.93+0.23 −0.18 0.69+0.02 −0.01 3.53+0.33 −0.56 −2.96+0.92 −0.71"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Gas mass evolution parameter m_1 (Eq. 21) = 0.69 dimensionless",
  "failed_quote": "1.93+0.23 −0.18 0.69+0.02 −0.01 3.53+0.33 −0.56 −2.96+0.92 −0.71"
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Gas mass evolution parameter a_1 (Eq. 21) = 3.53 dimensionless",
  "failed_quote": "1.93+0.23 −0.18 0.69+0.02 −0.01 3.53+0.33 −0.56 −2.96+0.92 −0.71"
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Gas mass evolution parameter a_2 (Eq. 21) = -2.96 dimensionless",
  "failed_quote": "1.93+0.23 −0.18 0.69+0.02 −0.01 3.53+0.33 −0.56 −2.96+0.92 −0.71"
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Total cosmic SFR density log10(rho_SFR) at z = 0.35 = -1.41 dex (Msun yr^-1 Mpc^-3)",
  "failed_quote": "log10 ρSFR M⊙ yr−1 Mpc−3 −1.41+0.01 −0.01 −1.22+0.01 −0.01 −1.01+0.01 −0.01 −0.90+0.01 −0.01 −0.84+0.01 −0.01 −0.92+0.01 −0.01 −0.97+0.01 −0.01 −1.11+0.01 −0.02 −1.26+0.01 −0.02 −1.39+0.02 −0.03"
 },
 {
  "path": "results_numeric[16].evidence[0]",
  "value": "Total cosmic SFR density log10(rho_SFR) at z = 1.75 = -0.84 dex (Msun yr^-1 Mpc^-3)",
  "failed_quote": "log10 ρSFR M⊙ yr−1 Mpc−3 −1.41+0.01 −0.01 −1.22+0.01 −0.01 −1.01+0.01 −0.01 −0.90+0.01 −0.01 −0.84+0.01 −0.01 −0.92+0.01 −0.01 −0.97+0.01 −0.01 −1.11+0.01 −0.02 −1.26+0.01 −0.02 −1.39+0.02 −0.03"
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "Total cosmic SFR density log10(rho_SFR) at z = 5.00 = -1.39 dex (Msun yr^-1 Mpc^-3)",
  "failed_quote": "log10 ρSFR M⊙ yr−1 Mpc−3 −1.41+0.01 −0.01 −1.22+0.01 −0.01 −1.01+0.01 −0.01 −0.90+0.01 −0.01 −0.84+0.01 −0.01 −0.92+0.01 −0.01 −0.97+0.01 −0.01 −1.11+0.01 −0.02 −1.26+0.01 −0.02 −1.39+0.02 −0.03"
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "Massive galaxies drive the rise and fall of the cosmic star formation history and peak at cosmic noon, while low-mass galaxies contribute a nearly constant SFR and gas density over cosmic time.",
  "failed_quote": "We can see the same kind of features as for the evolution of ρSFR: a rise and fall with redshift with a maximum around z ∼ 2; a dominance across all redshifts of the high-mass galaxies (i.e. log10 (M⋆/M⊙) > 10) contribution; and a relatively flat evolution of the low-mass galaxies (i.e. log10 (M⋆/M⊙) < 10)."
 },
 {
  "path": "claims[3].evidence[1]",
  "value": "TNG100 fails to reproduce the stellar-mass-dependent evolution of the CSFH because massive galaxies are overly gas-depleted and quenched too early, likely due to overly efficient AGN feedback.",
  "failed_quote": "In particular, in the TNG100 simulation, massive galaxies do not form enough stars around cosmic noon, when the cosmic SFR density peaks (i.e. ρM⋆≥1010 M⊙ SFR−TNG100 ≃ 50% ρM⋆≥1010 M⊙ SFR−observed at z = 2)."
 },
 {
  "path": "claims[4].evidence[0]",
  "value": "Distant galaxies (z = 3-5) convert gas into stars more efficiently at a fixed gas surface density than low-redshift galaxies, indicating an intrinsic redshift evolution of the SFE.",
  "failed_quote": "At z > 2, in Fig. 21, the normalisation increases with redshift: by a factor ∼3 between z ∼ 2 and z ∼ 4.3."
 },
 {
  "path": "reasoning.why_this_method.evidence[1]",
  "value": "Stellar-mass selection and mean stacking avoid uncertain extrapolations of the IR luminosity function (which is polluted by starbursts), avoid non-linear median stacking biases, and allow recovery of total flux for faint galaxy populations; the S18 SED library has few free parameters suited for sparse FIR sampling; the MZR gas mass method accounts for metallicity variations with stellar mass.",
  "failed_quote": "We choose to use mean stacking for our work, rather than median stacking. Indeed, although median stacking better suppresses secondary sources in the stacked image (i.e. bright sources which are close to the stacked target and might appear in the final stacked image), it has been shown that it also yields to systematically biased measurements at low S/N or in the presence of a flux distribution skewed towards low or high values (White et al. 2007; S15)."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Median stacking (rejected in favour of mean stacking because median is non-linear and introduces systematic biases at low S/N or for skewed flux distributions)",
  "failed_quote": "We choose to use mean stacking for our work, rather than median stacking. Indeed, although median stacking better suppresses secondary sources in the stacked image (i.e. bright sources which are close to the stacked target and might appear in the final stacked image), it has been shown that it also yields to systematically biased measurements at low S/N or in the presence of a flux distribution skewed towards low or high values (White et al. 2007; S15)."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[1]",
  "value": "H-band selection may become a less robust proxy for stellar mass at z > 3 and misses H-dropout galaxies (which are added a posteriori from Wang et al. 2019).",
  "failed_quote": "The completeness computed in this paper is determined assuming that the H-band is a good proxy for the stellar mass. This hypothesis may however become less robust at high redshifts (i.e. z > 3)."
 }
]
```
