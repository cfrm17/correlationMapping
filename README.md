# Implied Base Correlation Mapping Methodology


The Mapping model serves the purpose of finding implied base correlations for a bespoke CDO trade from market quoted standard CDO indices Dow Jones CDX and iTraxx Europe. In this report, a CDO tranche is defined as bespoke if its reference portfolio composition is different from that of CDO indices.  

A simplified Loss Ratio method (named “Maturity Loss Ratio”) is adopted in the model.  The detachment points of the bespoke base tranche are solved such that, given the same correlation value, the normalized expected losses of the bespoke tranche meet with that of the standard index base tranches. The new method is considered as a replacement of the existing mapping methodology “Scale” to reflect the latest development of credit market. 

To our best knowledge there is no generally accepted mapping methodology. It is an open question and subject to future research. Furthermore, several ad hoc adjustments have to be made, if a bespoke tranche is to be calibrated to different indices. This makes it more difficult for the market participants to find a consensus solution to the mapping methodology. In our opinion, the base correlation mapping is theoretically sound only if the risk profile of the bespoke portfolio is similar to that of the indices. For example, if a bespoke portfolio has well-diversified North America names with similar trade definition of the CDX and similar credit spread levels, it would be reasonable to use the base correlation implied by CDX indices.  If they are different, there exist uncertainties with respect to dispersion of credit quality, portfolio diversification, and portfolio mixture issues. No known mapping methodology can fully address all the uncertainties. 

As an effective way of managing the imbedded uncertainties, the mapping methodology can be monitored through a monthly IPV process. On the other hand no matter what mapping methodology is being used, an adequate model risk reserve has to be set up.

The implementation of the submitted model was first verified by an independently implemented test model. The “Maturity Loss Ratio” and “Loss Ratio” were tested. The underlying approximation of “Maturity Loss Ratio” was assessed. The results were also analyzed. 

The implication of the mapping methodology on MTMs, credit spread sensitivities, default sensitivities, correlation sensitivity, credit spread hedging, and stress testing were investigated. The testing results indicate that, when we switch a mapping methodology, not only MTM will change, but also the hedging positions need to be adjusted which might be costly. Furthermore, a possible mis-hedge can be material, especially in the stress events. In our opinion, adequate IPV/model risk reserve can cover the MTM adjustment. Other risk control methods, such as stress testing and DS-CS gap control, can play an important role to prevent a possible large mis-hedging incurred by the uncertainty of the model.

We therefore concluded that the bespoke mapping methodology “Maturity Loss Ratio” in submitted model is approved for computing mapped base correlations for bespoke CDO trades, conditional on an adequate model risk reserve and a frequent re-review through MarkIt. The old mapping methodology “Scale” is now considered obsolete. 

The model serves the purpose of computing appropriate correlations in the valuation of a collateral debt obligation (CDO) tranche via market information. Currently standard credit default swaps (CDS) indices, Dow Jones CDX and iTraxx in Europe, are quoted actively by dealers in the market.  From this market information, we intend to retrieve the correlation information of the standardized collateral pools and then use it to get the market implied correlation for 1) non-standard CDO tranches with standard collateral pools and 2) tranches of a bespoke non-index CDO trade. A CDO tranche is defined as bespoke if its reference portfolio composition is different from that of the indices. 

The index base correlation curves are defined as the correlation inputs required for a series of equity tranches that gives the tranche value consistent with quoted spreads. It was introduced by JPMorgan to address the difficulty of applying market-implied correlation to a tranche with non-standard attachment and detachment points.  A tranche with non-standard tranching positions can be valued readily via base correlations derived by interpolation on the standard base correlation curves. 

At the present time, it is also a standard market practice to value a bespoke tranche within the base correlation framework. A mapping methodology is introduced to calculate bespoke base correlation curves from the index base correlation curves. 

To our best knowledge there is no generally accepted mapping methodology. It has been the most challenging question facing the structured credit derivative market. Furthermore, several ad hoc adjustments have to be made, if a bespoke tranche is to be calibrated to different indices. This makes it more difficult for the market participants to find a consensus solution to the mapping methodology. In our opinion, the base correlation mapping is theoretically sound only if the risk profiles of the bespoke portfolio are similar to that of the indices. For example, if a bespoke portfolio has well-diversified North America names with similar trade definition of the CDX and similar credit spread levels, it would be reasonable to use the base correlation implied by CDX indices. If there is a difference, for example, in the credit spread level, somehow an adjustment of the base correlation can be made via a mapping methodology. This is based on the belief that the base correlations correspond to different level of risk in the capital structure of the collateral pool. However, a typical synthetic CDO contains more than a hundred obligors and could be considered as a product with thousands of risk factors. Roughly the uncertainties can be classified as dispersion of credit quality, portfolio diversification, and portfolio mixture issue. All the mapping methodologies that exist in the market are a kind of normalization or scaling to the index base correlation curves. However, each of them can only address certain uncertainties to some degree.

As an effective way managing the imbedded uncertainties, the mapping methodology can be monitored through a monthly IPV process. Although we are still subject to modeling uncertainties, we believe that the underlying model risk is small if we know that, using our mapping methodology, we can price the bespoke CDO consistent with the market consensus. In the mean time, if our bespoke tranche prices become an outlier among all market participants, it is a clear message that the mapping methodology needs to be reviewed (see https://finpricing.com/lib/FiBondCoupon.html)

The outstanding approved mapping methodology is called “Scale” with a scaling factor of 0.5 for the entire capital structure. It has been well known that this method is not very good, if the credit spread dispersion in the bespoke portfolio is dramatically different from those of the indices. For example, the presence of several names with exceptionally high spreads will cause the equity tranche undervalued, and subsequently the super senior tranche overvalued.  When “Scale” was introduced, it was consistent with results. Furthermore, an examination of all then outstanding bespoke portfolios showed that the heterogeneity of the credit spread distribution was not a concern by that time. However, the latest result indicates that the weakness of this mapping methodology becomes material; hence this mapping methodology is no longer adequate. 

At the present time it is generally perceived that another mapping methodology, namely “Loss Ratio” has the merit to address the credit spread dispersion. This is verified by the most recent results (shown in the next section). 

We are fully aware of the uncertainty imbedded in the mapping and a model reserve has been set up since the method was introduced two year ago. No matter what mapping methodology is used, an adequate model risk reserve is needed to cover the fundamentally imbedded uncertainties of the mapping methodology.

In our opinion, although adequate IPV/model risk reserve can cover the MTM adjustment, other risk control methods, such as stress testing and DS-CS gap control, should also play an important role in the risk control of a possible mis-hedge incurred by model uncertainty. The testing results shown in Section 2.4 below indicate that, when we switch a mapping methodology, not only MTM will change, but the hedging positions also need to be adjusted which might be costly. Furthermore, a possible mis-hedge can be material, especially in the stress events. 

Upon the Oscar/Fritz platform, “Loss Ratio” and a simplified loss ratio mapping, namely “Maturity Loss Ratio”, are implemented in the model. The new method is more efficient than the standard “Loss Ratio” method with an approximation of ignoring discount factor in the computation of expected losses. Our tests have shown that the approximation is acceptable. 

At the present time there are quoted curves with different indices (CDX and iTraxx) and maturities (3y, 5y, 7y, 10y) in the market. A base correlation for CDX is denoted as a function of detachment point   and maturity . The base correlation curves for iTraxx are denoted the same as the CDX except that the detachment points are different ( ). 

Suppose the index base correlation curves have been built and in total there are eight on-the-run base correlation curves. Therefore the object of bespoke mapping is to build eight equivalent bespoke base correlation curves for a given bespoke CDO trade. Four are mapped to the CDX.NA.IG on the run curves with four maturities and the other four are mapped to the same set of iTraxx curves. 

Assume an index base correlation for CDX at detachment point   and maturity   be  . A mapping methodology is a formula to find a detachment point   such that the target bespoke correlation is .

In our first version of base correlation toolbox, five mapping methodologies were available, which is shown in Table 1. As far as we know, there are other mapping methodologies in the market, such as matching the tranche sensitivities. 

Notations:   and   are the notional amount and total expected loss of the source collateral pool (CDX or iTraxx).   is the tranche notional amount.   and  are the expected loss of the base tranche for index with detachment point  and bespoke with detachment point  , respectively.   is a scaling factor, which is normally assumed constant.

Table 1. Six Known Mapping Methodologies
Criteria	Equations to solve 

Loss Ratio	 

Loss Fraction	 

Breakeven Spread/Equity Spread	 

Scale/Expected Loss	 

Probability	 

Maturity Loss Ratio Mapping	 


Note that “Maturity Loss Ratio” is a simplified “Loss Ratio” mapping methodology to increase computational efficiency.

In the computation of the expected loss of a tranche, the following approximation is applied:

(1)        

Therefore the approximated “Loss Ratio” can be written as

(2)          ,

where   is the accumulated expected loss amount for the bespoke tranche seen at maturity. Using the current semi-analytical solution, computing  is much faster than .

From the viewpoint of model, the approximation can also be viewed as ignoring the discount factor in the computation of expected loss (assuming ). Therefore the only difference between the “Loss Ratio” and “Maturity Loss Ratio” is accounting for time value of money. 

An analysis by GRMMR London on the entire CDO book indicates that the impact of this approximation is very small. Several test scenarios have been designed to assess this approximation with the test results shown in the next section.

Note that, when the index base correlation is computed, there is a basis adjustment for the credit spread curves for each obligor. When calculating the expected losses or probability of the index base tranches, the adjusted curves should always be used. In the submitted model, you can choose to use the curves with or without curve adjustment. 

