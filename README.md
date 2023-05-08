Download Link: https://assignmentchef.com/product/solved-stat823-homework-12-poisson-regression
<br>
Using RMarkdown in RStudio, complete the following questions. Launch RStudio and open a new RMarkdown file or use the class RMarkdown template provided and save it on your working directory as a .Rmd file. At the end of the activity, save your <strong>pdf </strong>generated from RMarkdown+Knitr and submit your homework on the Blackboard.

Poison distribution can be utilized for analyzing data with counts as the outcome of interest (<em>Y<sub>i </sub></em>= 0<em>,</em>1<em>,</em>2<em>,···</em>). The main assumption is that the mean and variance of the Poisson distribution are equall. That is, <em>E{Y } </em>= <em>µ </em>and <em>σ</em><sup>2</sup><em>{Y } </em>= <em>µ</em>.

<ol>

 <li>A study was conducted by Sir Richard Doll and colleagues (Breslow and Day, 1987) based on 1951 data where all British doctors were sent a brief questionnaire about whether they smoked tobacco. Since then information about their deaths has been collected. The data below shows the numbers of deaths from coronary heart disease among male doctors 10 years after the survey. It also shows the total number of person-years of observation at the time of the analysis. Note that this data can be loaded using data(doctors) after loading the <em>R </em>package dobson. However, you have to convert the strings variables into factors and numerical values where appropriate.</li>

</ol>

The data is shown on the Table below:

Page -1- of 3

<strong>Table 1: </strong>Deaths from coronary heart disease after 10 years among British male doctors by age and smoking status in 1951

<table width="370">

 <tbody>

  <tr>

   <td width="38">age</td>

   <td width="53">agesq</td>

   <td width="59">agecat</td>

   <td width="94">smoke</td>

   <td width="60">deaths</td>

   <td width="65">personyrs</td>

  </tr>

  <tr>

   <td width="38">1</td>

   <td width="53">1</td>

   <td width="59">35-44</td>

   <td width="94">smoker</td>

   <td width="60">32</td>

   <td width="65">52407</td>

  </tr>

  <tr>

   <td width="38">2</td>

   <td width="53">4</td>

   <td width="59">45-54</td>

   <td width="94">smoker</td>

   <td width="60">104</td>

   <td width="65">43248</td>

  </tr>

  <tr>

   <td width="38">3</td>

   <td width="53">9</td>

   <td width="59">55-64</td>

   <td width="94">smoker</td>

   <td width="60">206</td>

   <td width="65">28612</td>

  </tr>

  <tr>

   <td width="38">4</td>

   <td width="53">16</td>

   <td width="59">65-74</td>

   <td width="94">smoker</td>

   <td width="60">186</td>

   <td width="65">12663</td>

  </tr>

  <tr>

   <td width="38">5</td>

   <td width="53">25</td>

   <td width="59">75-84</td>

   <td width="94">smoker</td>

   <td width="60">102</td>

   <td width="65">5317</td>

  </tr>

  <tr>

   <td width="38">1</td>

   <td width="53">1</td>

   <td width="59">35-44</td>

   <td width="94">non-smoker</td>

   <td width="60">2</td>

   <td width="65">18790</td>

  </tr>

  <tr>

   <td width="38">2</td>

   <td width="53">4</td>

   <td width="59">45-54</td>

   <td width="94">non-smoker</td>

   <td width="60">12</td>

   <td width="65">10673</td>

  </tr>

  <tr>

   <td width="38">3</td>

   <td width="53">9</td>

   <td width="59">55-64</td>

   <td width="94">non-smoker</td>

   <td width="60">28</td>

   <td width="65">5710</td>

  </tr>

  <tr>

   <td width="38">4</td>

   <td width="53">16</td>

   <td width="59">65-74</td>

   <td width="94">non-smoker</td>

   <td width="60">28</td>

   <td width="65">2585</td>

  </tr>

  <tr>

   <td width="38">5</td>

   <td width="53">25</td>

   <td width="59">75-84</td>

   <td width="94">non-smoker</td>

   <td width="60">31</td>

   <td width="65">1462</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Write an <em>R</em>-code to create this dataset or load it from the package dobson. Fit a Poisson regression model to the data with the response being the number of deaths as follows: <em>Y<sub>i </sub></em>= <em>β</em><sub>0 </sub>+ <em>β</em><sub>1</sub><em>Age<sub>i </sub></em>+ <em>β</em><sub>2</sub><em>Age</em><sup>2</sup><em><sub>i </sub></em>+ <em>β</em><sub>3</sub><em>Smoke<sub>i </sub></em>+ <em>β</em><sub>4</sub><em>Smoke<sub>i </sub>× age<sub>i </sub></em>+ <em><sub>i</sub></em>. Use an offset = log(personyrs) in your model. From this model, what is the value of the residual deviance? What is the value of the residual degrees of freedom? What is the <em>pseudo R</em><sup>2 </sup>value for the model?</li>

 <li>Obtain the deviance residuals and present them in an index plot (explore the function <em>resid</em>() after fitting your model). Are there any outlying cases?</li>

</ul>

<table width="632">

 <tbody>

  <tr>

   <td width="632">docm1<strong>$</strong>null.deviance <em># NULL DEVIANCE </em>docm1<strong>$</strong>deviance <em># DEVIANCE RESIDUALS</em>devresd &lt;- <strong>round</strong>(<strong>resid</strong>(docm1, type = “deviance”), 3) <strong>sum</strong><sub>(devresd</sub><strong><sub>^</sub></strong><sub>2</sub><sub>) </sub><em># Chi-square goodness-of-fit statistic </em>stddevres &lt;- <strong>rstandard</strong>(docm1) <em># standardized deviance residuals</em><em># standardized Pearson’s residuals</em>stdpearsons &lt;- <strong>rstandard</strong>(docm1, type = “pearson”) pearson.resid &lt;- <strong>round</strong>(<strong>resid</strong>(docm1, type = “pearson”), 3<sub>) </sub><em># Pearson residuals </em><strong>sum</strong>(pearson.resid<strong><sub>^</sub></strong>2) <em># Pearson goodness-of-fit statistic # expected &lt;- fitted.values(docm1, type=’response’)</em>expected &lt;- <strong>round</strong>(<strong>predict</strong>(docm1, type = “response”),2)</td>

  </tr>

 </tbody>

</table>

2

<ul>

 <li>Create a table with the observed and expected number of deaths together with the age groups and smoking status. What is the value of the deviance residuals goodness-of-fit statistic (<em>G</em><sup>2</sup>)? (<strong>Hint</strong>: sum the squares of the residual deviances) What is the value of the Pearson’s Chi-square goodness-of-fit statistic (<em>χ</em><sup>2</sup>)? (<strong>Hint</strong>: sum the squares of the pearson’s residuals).</li>

</ul>

<strong>kable</strong>(<strong>cbind</strong>(dataDeaths[, <strong>c</strong>(1, 3, 4, 5)], expected, pearson.resid, devresd))

<table width="485">

 <tbody>

  <tr>

   <td width="38">age</td>

   <td width="59">agecat</td>

   <td width="94">smoke</td>

   <td width="60">deaths</td>

   <td width="76">expected</td>

   <td width="105">pearson.resid</td>

   <td width="52">devresd</td>

  </tr>

  <tr>

   <td width="38">1</td>

   <td width="59">35-44</td>

   <td width="94">smoker</td>

   <td width="60">32</td>

   <td width="76">29.58</td>

   <td width="105">0.444</td>

   <td width="52">0.438</td>

  </tr>

  <tr>

   <td width="38">2</td>

   <td width="59">45-54</td>

   <td width="94">smoker</td>

   <td width="60">104</td>

   <td width="76">106.81</td>

   <td width="105">-0.272</td>

   <td width="52">-0.273</td>

  </tr>

  <tr>

   <td width="38">3</td>

   <td width="59">55-64</td>

   <td width="94">smoker</td>

   <td width="60">206</td>

   <td width="76">208.20</td>

   <td width="105">-0.152</td>

   <td width="52">-0.153</td>

  </tr>

  <tr>

   <td width="38">4</td>

   <td width="59">65-74</td>

   <td width="94">smoker</td>

   <td width="60">186</td>

   <td width="76">182.83</td>

   <td width="105">0.235</td>

   <td width="52">0.234</td>

  </tr>

  <tr>

   <td width="38">5</td>

   <td width="59">75-84</td>

   <td width="94">smoker</td>

   <td width="60">102</td>

   <td width="76">102.58</td>

   <td width="105">-0.057</td>

   <td width="52">-0.057</td>

  </tr>

  <tr>

   <td width="38">1</td>

   <td width="59">35-44</td>

   <td width="94">non-smoker</td>

   <td width="60">2</td>

   <td width="76">3.41</td>

   <td width="105">-0.766</td>

   <td width="52">-0.830</td>

  </tr>

  <tr>

   <td width="38">2</td>

   <td width="59">45-54</td>

   <td width="94">non-smoker</td>

   <td width="60">12</td>

   <td width="76">11.54</td>

   <td width="105">0.135</td>

   <td width="52">0.134</td>

  </tr>

  <tr>

   <td width="38">3</td>

   <td width="59">55-64</td>

   <td width="94">non-smoker</td>

   <td width="60">28</td>

   <td width="76">24.74</td>

   <td width="105">0.655</td>

   <td width="52">0.641</td>

  </tr>

  <tr>

   <td width="38">4</td>

   <td width="59">65-74</td>

   <td width="94">non-smoker</td>

   <td width="60">28</td>

   <td width="76">30.23</td>

   <td width="105">-0.405</td>

   <td width="52">-0.411</td>

  </tr>

  <tr>

   <td width="38">5</td>

   <td width="59">75-84</td>

   <td width="94">non-smoker</td>

   <td width="60">31</td>

   <td width="76">31.07</td>

   <td width="105">-0.013</td>

   <td width="52">-0.013</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Perfom a test of the goodness of fit for this model. Are the Poisson’s distribution assumptions violated? Based on this model, what conclusions do you reach?</li>

</ul>