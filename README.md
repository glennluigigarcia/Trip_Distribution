<p style='text-align: center'>
  <img src='https://ops.fhwa.dot.gov/publications/fhwahop18073/images/figure1.png' width='500' height=275/>
</p>

<div style='text-align:center'>
    <p style='font-size: 25px; color: rgb(0,125,183);'><b>Convergence Analysis of Trip Distribution Methods</b></p>
</div>

---

# <h1 style='background-color: rgb(0,125,183); padding: 21px; color: #FFFFFF; font-family: Helvetica; font-size: 25px'>**Introduction**</h1> 

Trip distribution is a central stage of the traditional four-step model in transport planning. <b>It provides the connection between how many trips are produced in each zone and how they are attracted to other zones, ultimately producing the origin-destination (OD) matrix required for mode choice and assignment.</b> Without this stage, it would not be possible to understand how future travel demand will be distributed across a regional network. The method chosen for distribution is crucial, as it determines whether the resulting OD matrix reflects realistic behavioural patterns or imposes artificial assumptions on flows. Among the many techniques available, growth factor methods and synthetic methods have historically been the most widely implemented in both research and practice.  

Growth factor methods rely on information about current and future productions and attractions, adjusting a base-year OD matrix iteratively until row and column totals match the targets. Synthetic methods, on the other hand, estimate flows directly from zonal productions and attractions while applying cost-based impedance or deterrence functions to capture behavioural sensitivity to travel distance, time, or cost. Both classes of methods can be structured in a doubly constrained manner, which ensures that totals at both the production and attraction ends are exactly matched. This requirement of double constraint is especially important in planning contexts because it avoids systematic errors in marginal totals that could distort network forecasts.  

<b>The purpose of this notebook is to present a clear, teaching-oriented exploration of nine trip distribution methods:</b> four under the growth factor category and five under the synthetic category. For each method, mathematical formulas and worked matrix examples are provided to make the process transparent. The notebook further examines the convergence behaviour of each technique under a 5% tolerance criterion, comparing which methods reach equilibrium most efficiently. This comprehensive presentation not only demonstrates the mechanics of each method but also provides a comparative lens for assessing their practical usefulness.  

---

# <h1 style='background-color: rgb(0,125,183); padding: 21px; color: #FFFFFF; font-family: Helvetica; font-size: 25px'>**Motivation**</h1> 

The motivation for developing this notebook arises from the dual challenges faced in transport planning: balancing computational rigour with behavioural realism. Planners often need to choose among several distribution models, each with different assumptions and computational demands. Growth factor methods, while straightforward and computationally inexpensive, may not always replicate observed behavioural responses to travel cost. Synthetic methods, while more behaviourally grounded, can require careful calibration of parameters and more iterations before reaching convergence.  

By presenting both classes of methods side by side under a common doubly constrained framework, <b>the notebook allows readers to observe their similarities and differences in a structured way.</b> Another key motivation is pedagogical: students and practitioners often encounter these methods in abstract terms in textbooks, but rarely see their step-by-step application on a matrix. Worked examples with four zones are therefore included to make the procedures tangible and reproducible.  

From a research perspective, this notebook also aims to highlight convergence properties as a practical performance measure. In real-world transport planning, computational efficiency matters, particularly when dealing with hundreds of zones and millions of trips. Methods that converge quickly without sacrificing accuracy are highly valuable in such contexts. Additionally, the notebook emphasizes transparency by presenting intermediate iterations, so that convergence is not seen as a “black box” but as a measurable and interpretable process.  

Finally, the <b>broader motivation is to equip transport professionals with a comparative understanding of distribution techniques.</b> By documenting advantages, disadvantages, and convergence outcomes for all nine methods, the notebook serves as a reference for choosing the most suitable approach for specific contexts, whether that involves rapid forecasting or detailed policy evaluation.  

---

# <h1 style='background-color: rgb(0,125,183); padding: 21px; color: #FFFFFF; font-family: Helvetica; font-size: 25px'>**Process**</h1> 

The process implemented in this notebook begins with the establishment of a base OD matrix representing trips between ten zones. This matrix is adjusted or re-estimated depending on the method under consideration. For growth factor methods, the starting point is a historical OD matrix, which is progressively updated using factors derived from future productions and attractions. Each method applies these factors differently, whether averaging growth ratios, scaling by origin, or iteratively balancing both sides through proportional fitting.  

For synthetic methods, the process diverges because no historical OD matrix is assumed. Instead, trip distributions are estimated from productions and attractions directly, using impedance or deterrence functions that express behavioural sensitivity to travel costs. The exponential, power, and combined forms of deterrence functions are presented, alongside impedance-based formulations constrained by either generations or attractions. Each case requires iterative proportional fitting to ensure that both row and column totals align with the required control totals.  

A common feature of all methods is the convergence check. After each iteration, the row and column totals are compared with the target productions and attractions, and the relative differences are computed. When these differences fall below the 5% tolerance threshold, the method is considered converged. The notebook documents this process step by step, so that readers can see how convergence is achieved and how many iterations each method requires.  

---

# <h1 style='background-color: rgb(0,125,183); padding: 21px; color: #FFFFFF; font-family: Helvetica; font-size: 25px'>**Conclusion**</h1> 

The convergence analysis carried out in this notebook provides several important insights. First, growth factor methods are reliable when both base and future data are available, but their convergence properties vary: while average and Detroit methods are fast, they may leave imbalances, whereas Fratar and Furness ensure balance but may require more iterations. Second, synthetic methods demonstrate the behavioural richness of cost-based formulations, with impedance and deterrence functions producing distributions that better reflect observed travel behaviour.  

Among the nine methods studied, the Impedance – Generation Constrained approach and the Deterrence – Power Cost Function were identified as the fastest to converge. Their smoother weighting structures make iterative proportional fitting more stable, reducing oscillations between row and column adjustments. Exponential and combined deterrence forms, while behaviourally appealing, were more sensitive to parameter settings and therefore required more iterations.  

The conclusion also emphasizes that no single method is universally best; the choice depends on data availability, behavioural realism required, and computational resources. Growth factor methods remain useful in contexts with strong continuity of travel patterns and historical OD data, while synthetic methods are indispensable in data-scarce environments or when behavioural interpretation of cost sensitivity is essential.  

Overall, the notebook demonstrates that <b><i>understanding convergence behaviour is not a purely academic exercise but has practical implications for planning.</i></b> Methods that converge efficiently can save significant time and resources in large-scale forecasting exercises. By documenting both the mechanics and comparative performance of nine different approaches, this notebook provides a comprehensive guide for both students and practitioners. Its results highlight the importance of careful model selection, transparent calibration, and systematic convergence evaluation in producing reliable transport forecasts.  

---