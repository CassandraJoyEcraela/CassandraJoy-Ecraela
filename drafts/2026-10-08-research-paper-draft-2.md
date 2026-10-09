# Is AI Doing to Customer Service Jobs What Offshoring Did?

BUS 620 | Micro & Macro Economic Foundations for Managers  
Individual Research Paper  
Cassandra Joy Ecraela-Pantoca  
October 8, 2026

## The Question

We keep hearing that AI will let firms do the same work with far less labor, and that it’s already happening in customer service. This paper asks whether AI is hitting customer service rep jobs in the way offshoring did, and whether we can already see it in the numbers. The short answer is that employment is down 11.1% from its 2019 peak (to about 2.6 million workers), but it started falling before any company I could verify blamed AI, so these numbers cannot separate AI from offshoring-style cost pressure. I wrote this for a head of customer operations deciding whether to hold US headcount, cut further, or bring jobs back onshore.

## Why It Is One Problem

Offshoring made answering phone calls much cheaper with an overseas rep substituting for a US-based rep at a lower price. When the price of a substitute for human labor falls, firms shift toward it, and employment and pay in the pricier version fall. AI is the same disruption through another channel, since a chatbot or voice agent is another, cheaper substitute. How easily work can be swapped (the elasticity of substitution) decides how far jobs fall. Scripted work (password resets, order status) is easy to swap, while exceptions and upset customers are not (Acemoglu & Restrepo, 2019; Autor et al., 2003).

## The Evidence

I used three data series and kept them separate: BLS employment and median pay for customer service representatives, May 2016 to May 2025 (U.S. Bureau of Labor Statistics \[BLS\], 2026a); Indeed’s seasonally adjusted customer service postings index (Indeed Hiring Lab, 2026); and a dated log of companies blaming AI for customer support labor cuts. I wrote the tests down before pulling any data, so I could not pick whichever flattered the result. Employment reports alone cannot tell an AI-driven drop from an offshoring-driven one, so timing is the only tool I have to separate them at this time.

**Did employment break from trend?** I drew a line through the 2016–2021 employment numbers and extended it to 2025 to show where it was headed if nothing changed. Then I drew a floor below it, a cushion for normal ups and downs; two years in a row under the floor counts as a break in the trend. I tried a fixed cushion (the same every year) and a growing one that widens the further out I go (a forecast band). I made the growing one primary because a line built on six points is less trustworthy four years out, but I ran both (Appendix A), and they disagree. The fixed band puts 2024 and 2025 under the floor. The forecast band puts only 2025 below, by about 118,000 jobs, so the test did not detect a break, though employment did fall to its series low (Figure 1).

**Did the decline start before firms blamed AI?** For this timing test I ignore any fall that starts in 2020 or 2021, a rule I wrote down before pulling data, so the pandemic can’t pass for an early AI signal. With that rule, postings first fall two quarters in a row in 2022 Q2 at a 1% threshold and 2023 Q1 at my primary 3%. At 5%, there is no such run. Employment’s first two straight declines after the pandemic window start in 2023. I counted a statement only if it was about customer-facing work, publicly blamed the cut on AI, and had a source and date I could verify. Only Salesforce cleared that. In September 2025, its CEO said support headcount went from about 9,000 to 5,000 because of AI agents (TechRepublic, 2025). Uber does not count. It only named “embrace AI” as one aim of a July 2026 restructuring, not a cause (Doerer, 2026), and it came after Salesforce anyway. Both declines start well before the Salesforce statement, about two and a half years for postings and two years for employment, so AI may be a label on cuts already happening. IBM’s 2023 back-office hiring pause (Ford, 2023) and C.H. Robinson’s freight jobs (C.H. Robinson Worldwide, Inc., 2026) are close calls (Appendix B).

Surveys suggest more talk than action: only 20% of customer service leaders had cut agent headcount because of AI (Gartner, 2025). So I kept the statements as a separate, non-numeric series, since they record the stated public cause, not the true internal one.

![Figure 1](https://github.com/CassandraJoyEcraela/CassandraJoy-Ecraela/blob/main/drafts/2026-10-08-fig1_employment_trend_floors-draft-2.png)

**Figure 1.** Employment (May snapshots) vs. trend and two floors. The shaded years are the pandemic years, which the break test keeps in the baseline and the timing test sets aside. The axis starts at 2.5M, not zero, which exaggerates the 11.1% drop from the 2019 peak. Purple lines mark where postings first fall two quarters in a row (1% and 3% thresholds); the red line marks the Salesforce statement (Sep 2025).

## What These Numbers Can’t Tell Apart

I can’t separate AI from offshoring with the data I have, and I’d rather say so plainly than stretch the tests. Employment and postings started falling before the first customer-facing AI statement I could verify. But that only tells us the cuts did not begin with AI statements, not what caused them, and the BLS numbers stop at May 2025, before that statement. AI is still evolving, so I may be looking at the early part of the story. We are starting to see effects, and it will take more data to say what they are. I also never measured what offshoring itself did, so this compares mechanisms, not sizes. And pay did not fall the way the substitution story predicts (real pay is back above its 2021 level, Appendix C). Possibly because the jobs left are the harder ones. Evidence that could separate the two (overseas contact-center hiring, imports of business services, a company’s total headcount including overseas) sits outside the three series I fixed in advance, so I did not add it later.

## What It Means and What to Do

So is AI the same disruption as offshoring? I can’t fully tell yet. Employment and postings are both down, so something real is happening, but it’s not clear whether AI is acting like offshoring or like something new. The next BLS release is the first to include the 2025–2026 cuts, and if it lands below the forecast floor, the break holds under either test. If job postings recover, AI as a sole cause weakens.

I’d advise a head of customer operations to hold headcount steady for now rather than cut deeply or bring jobs back onshore. The tests give no case for a deep cut, but I wouldn’t wait for proof. First, sort your team’s work into scripted work (password resets, order status) and judgment work (upset customers, AI review), then let scripted roles shrink only through attrition and hiring freezes, not layoffs.

Second, repurpose the money you would have spent backfilling those roles into retraining your current reps. Retraining pays off slowly, with gains that grow over two to three years (Card et al., 2018), so waiting for cuts to show up in your numbers delays the gains. Aim it at judgment work and AI review, and pay more for that harder work or your best reps will leave.

Third, decide your warning signs ahead of time so headlines don’t make the call for you. Watch the two outside signals above (the next BLS release, job postings), plus two of your own: how many contacts the AI resolves without a person, and customer satisfaction. Decide now what readings mean speed up or pause (pause if satisfaction drops). Also, inform your managers upfront of the labor, training, and knowledge retention plan.

Some may ask: the stricter test found no break, so why act at all? Because six data points can’t tell us much, and not finding a break isn’t proof there isn’t one. A slow, reversible plan costs little if no break comes, and keeping a human option open covers the worry that most customers would rather talk with a real person instead of a chatbot.

## References

Acemoglu, D., & Restrepo, P. (2019). Automation and new tasks: How technology displaces and reinstates labor. *Journal of Economic Perspectives, 33*(2), 3–30. https://doi.org/10.1257/jep.33.2.3

Autor, D. H., Levy, F., & Murnane, R. J. (2003). The skill content of recent technological change: An empirical exploration. *The Quarterly Journal of Economics, 118*(4), 1279–1333. https://doi.org/10.1162/003355303322552801

Bloomberg News. (2026, July 28). Uber, Hyatt and others pick AI over human customer service. *Staffing Industry Analysts*. https://www.staffingindustry.com/news/global-daily-news/uber-hyatt-and-others-pick-ai-over-human-customer-service

Card, D., Kluve, J., & Weber, A. (2018). What works? A meta analysis of recent active labor market program evaluations. *Journal of the European Economic Association, 16*(3), 894–931. https://doi.org/10.1093/jeea/jvx028

C.H. Robinson Worldwide, Inc. (2026). *2025 annual report and Form 10-K*. https://s21.q4cdn.com/950981335/files/doc_financials/2025/ar/CHRW-2025-Annual-Report-10-K.pdf

Doerer, K. (2026, July 23). Uber cuts 10% of customer service team as it embraces AI. *Customer Experience Dive*. https://www.customerexperiencedive.com/news/uber-cuts-10-of-customer-service-team-as-it-embraces-ai/826087/

Ford, B. (2023, May 2). IBM to pause hiring for jobs that AI could do. *Fortune*. https://fortune.com/2023/05/01/ibm-ceo-ai-artificial-intelligence-back-office-jobs-pause-hiring

Founder Reports. (n.d.). *AI layoffs by company: A tracker of every major layoff tied to AI (2026)*. Retrieved September 23, 2026, from https://founderreports.com/ai-layoffs-tracker/

Gartner. (2025, December 2). *Gartner survey finds only 20% of customer service leaders report AI-driven headcount reduction* \[Press release\]. https://www.gartner.com/en/newsroom/press-releases/2025-12-02-gartner-survey-finds-only-20-percent-of-customer-service-leaders-report-ai-driven-headcount-reduction

Indeed Hiring Lab. (2026). *Job postings index: Customer service for the United States* \[IHLIDXUSTPCUSTSERV; Data set\]. FRED, Federal Reserve Bank of St. Louis. https://fred.stlouisfed.org/series/IHLIDXUSTPCUSTSERV

TechRepublic. (2025, September 3). *Salesforce ‘needs less heads,’ so it cut 4,000 jobs, as AI takes over*. https://www.techrepublic.com/article/news-salesforce-cuts-4k-jobs/

U.S. Bureau of Labor Statistics. (2026a). *Occupational Employment and Wage Statistics: Customer service representatives (SOC 43-4051), May 2016–May 2025* \[Data set\]. https://www.bls.gov/oes/

U.S. Bureau of Labor Statistics. (2026b). *Consumer price index for all urban consumers: All items in U.S. city average* \[CPIAUCNS; Data set\]. FRED, Federal Reserve Bank of St. Louis. https://fred.stlouisfed.org/series/CPIAUCNS

## Appendix

### Appendix A. Employment Floor Test, Both Formulas

Linear trend (OLS) fit to 2016–2021 OEWS employment and projected forward. Floors are the lower end of a 90% one-sided prediction interval (t with 4 degrees of freedom). The fixed band uses the same spread every year. The forecast band widens with distance from the baseline. A break requires two consecutive years below a floor. All six baseline years are kept, pandemic years included, which adds noise and widens the floor. The spec originally described the floor only as how much the 2016–2021 numbers bounced around the line; the choice of the forecast band, and the reason, is recorded in the spec with the original wording kept, and both results are reported here.

| **Year** | **Actual** | **Projected trend** | **Fixed floor** | **Forecast floor** | **Below fixed?** | **Below forecast?** |
|----------|------------|---------------------|-----------------|--------------------|------------------|---------------------|
| 2016     | 2,707,040  | 2,768,271           | 2,651,738       | 2,624,419          | No               | No                  |
| 2017     | 2,767,790  | 2,786,681           | 2,670,148       | 2,654,057          | No               | No                  |
| 2018     | 2,871,400  | 2,805,092           | 2,688,558       | 2,678,453          | No               | No                  |
| 2019     | 2,919,230  | 2,823,502           | 2,706,969       | 2,696,863          | No               | No                  |
| 2020     | 2,833,250  | 2,841,912           | 2,725,379       | 2,709,287          | No               | No                  |
| 2021     | 2,787,070  | 2,860,322           | 2,743,789       | 2,716,471          | No               | No                  |
| 2022     | 2,879,840  | 2,878,733           | 2,762,200       | 2,719,518          | No               | No                  |
| 2023     | 2,858,710  | 2,897,143           | 2,780,610       | 2,719,499          | No               | No                  |
| 2024     | 2,725,930  | 2,915,553           | 2,799,020       | 2,717,267          | Yes              | No                  |
| 2025     | 2,595,750  | 2,933,964           | 2,817,430       | 2,713,443          | Yes              | Yes                 |

Result: with the fixed band, a break (2024 and 2025 below the floor). With the forecast band, the test did not detect a break: 2024 sits just above the floor (by about 8,700 jobs) and 2025 is below it (by about 117,700). A two-sided 90% interval reaches the same conclusions (forecast band: 2024 above, 2025 below by about 32,000). Landing inside the floor would mean the test did not detect a break, not that nothing happened.

### Appendix B. Postings Thresholds and Statement Log

First run of two consecutive falling quarters after 2021 (seasonally adjusted Indeed index, quarterly averages; falls starting in 2020 or 2021 are ignored). The timing result holds at 1% and 3%. At 5% the series never has two falling quarters in a row, so there is no start date and that threshold cannot answer the timing question; it is reported as “no run,” not as “postings never fell.”

| **A quarter is “falling” if the index drops at least** | **First run of two falling quarters** | **Quarters before first statement (2025 Q3)** |
|--------------------------------------------------------|---------------------------------------|-----------------------------------------------|
| 1%                                                     | 2022 Q2                               | 13                                            |
| 3% (primary)                                           | 2023 Q1                               | 10                                            |
| 5%                                                     | No run                                | Not applicable                                |

Employment: the first two decline years in a row after the ignored 2020–2021 window start in 2023 (employment rose in 2022 and fell in 2023, 2024 and 2025), two years before the year of the first verified statement (2025); the rule needs at least one. Employment also fell in 2020 and 2021, but those years are set aside by the pre-set pandemic rule.

Customer-facing AI statements. Inclusion rule: customer-facing work, company attributes the cut to AI, verifiable source and date. When in doubt, the statement is not counted. Source links for every entry are in my exclusion log, available on request.

| **Company**                                                           | **Date**                                                                                                                          | **Status**      | **Words used for the role**                                                               | **Note and source**                                                                                                                                                                                                                                          |
|-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|-----------------|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Salesforce                                                            | Early Sep 2025                                                                                                                    | Counts          | “customer support”                                                                        | CEO: support headcount about 9,000 to 5,000, credited to AI agents (TechRepublic, 2025)                                                                                                                                                                      |
| Uber                                                                  | Jul 22, 2026 (first reported by Bloomberg)                                                                                        | Excluded        | “community operations” (headlines say customer service)                                   | 10% cut. Spokesperson named “continue to embrace AI” as one of three aims, with simplifying operations and in-person work; did not say AI caused the cut. Borderline, so not counted. Later than Salesforce, so it would not change the clock (Doerer, 2026) |
| Microsoft (support)                                                   | About Apr 2026                                                                                                                    | Not counted yet | “customer service” costs                                                                  | Savings of about \$750M a year stated; headcount drop reported, not stated (Bloomberg News, 2026)                                                                                                                                                            |
| Hyatt                                                                 | Jun 2025                                                                                                                          | Excluded        | “guest services and support”                                                              | Company cited guest inquiries and business needs; spokesperson said unrelated to AI, though its AI lead said automation now helps cut customer service costs (Bloomberg News, 2026)                                                                          |
| Brinks Home                                                           | 2026                                                                                                                              | Excluded        | “call center”                                                                             | No usable date; most reduction by attrition and transfers                                                                                                                                                                                                    |
| Block                                                                 | Mar 2026                                                                                                                          | Excluded        | Not named                                                                                 | Company-wide cut; customer support role not confirmed by a second source                                                                                                                                                                                     |
| IBM                                                                   | May 2023                                                                                                                          | Excluded        | “non-customer-facing”                                                                     | Back-office roles; sensitivity case: if counted, it lands one quarter after the 3% postings run begins and in the same year as employment’s first decline, so timing becomes inconclusive at 3% (at 1%, postings still fall well before it) (Ford, 2023)     |
| C.H. Robinson                                                         | Tracker says 2022; company filings: productivity measured from end of 2022, “Lean AI” tied to headcount in the 2025 annual report | Excluded        | “quote-to-cash” freight work (quoting, order entry, load tenders, appointment scheduling) | Not customer service. A commercial tracker dated this to 2022 (Founder Reports, n.d.), but the company's own filing supports only the end-2022 productivity baseline and Lean AI language by 2025 (C.H. Robinson Worldwide, Inc., 2026)                      |
| UPS, Amazon, Cisco, Atlassian, Citigroup, PayPal, Coinbase, Grammarly | 2024–2026                                                                                                                         | Excluded        | Not named                                                                                 | No customer service function named                                                                                                                                                                                                                           |

Backup check: the extra search terms for tech support, IT support and help-desk roles turned up no qualifying statement, so there is no second clock and the check could not be run. That is a limit of the search, not evidence that such statements do not exist.

### Appendix C. Real vs. Nominal Median Pay

Real pay is the median annual wage for SOC 43-4051 in dollars of May 2025, adjusted with May CPI-U (BLS, 2026b). Real pay fell 5.8% from 2021 to 2022 while nominal pay rose 2.3%, and is up about 3.6% over 2016–2025. CPI-U tracks prices in general, not the cost of living for customer service workers, so real pay is a rough guide to buying power.

| **Year** | **Nominal median wage** | **May CPI-U** | **Real median wage (2025 dollars)** |
|----------|-------------------------|---------------|-------------------------------------|
| 2016     | \$32,300                | 240.229       | \$43,223                            |
| 2017     | \$32,890                | 244.733       | \$43,202                            |
| 2018     | \$33,750                | 251.588       | \$43,124                            |
| 2019     | \$34,710                | 256.092       | \$43,570                            |
| 2020     | \$35,830                | 256.394       | \$44,923                            |
| 2021     | \$36,920                | 269.195       | \$44,089                            |
| 2022     | \$37,780                | 292.296       | \$41,550                            |
| 2023     | \$39,680                | 304.127       | \$41,942                            |
| 2024     | \$42,830                | 314.069       | \$43,839                            |
| 2025     | \$44,770                | 321.465       | \$44,770                            |

![Figure C](https://github.com/CassandraJoyEcraela/CassandraJoy-Ecraela/blob/main/drafts/2026-10-08-figureC_wages_real_vs_nominal-draft-2.png)

**Figure C.** Median annual wage for SOC 43-4051, nominal and real. Real wages are in dollars of May 2025, adjusted with May CPI-U, which tracks prices in general and not the cost of living for customer service workers. The axis starts at \$30,000, not zero. Nominal pay rose every year, but real pay fell 5.8% from 2021 to 2022 while nominal pay rose 2.3%. The shaded years are the pandemic years.

### Appendix D. Job Postings vs. Employment, 2020–2025

![Figure D](https://github.com/CassandraJoyEcraela/CassandraJoy-Ecraela/blob/main/drafts/2026-10-08-figureD_postings_vs_employment-draft-2.png)

**Figure D.** Top: Indeed customer service postings index (seasonally adjusted, February 1, 2020 = 100; daily line and quarterly averages). The March–April 2020 crash is shaded so it is not read as a lasting drop, and the purple lines mark where postings first fall two quarters in a row at the 1% (2022 Q2) and 3% (2023 Q1) thresholds. Bottom: OEWS employment (May snapshots) over the years both series cover; the gray block marks the pandemic years. Postings turned down in 2022, before employment fell in 2023 and well before the first verified customer-facing statement (red line). Postings measure hiring plans, not headcount, so they are read as a hint, not as employment.

### Appendix E. Limits

Six baseline years projected four years out, two of them pandemic years. Two reasonable floors disagree, which shows how little six years can show. One company clears the statement rule so far, and statements record stated causes, not true ones. These data cannot separate AI from offshoring: evidence that could (offshore contact-center employment, imports of business services, a firm's total headcount including overseas) is outside the three series fixed in advance, and AI's effect on this job is still unfolding. Postings measure hiring demand, not employment, and the latest quarter (2026 Q3, data through September 18) is incomplete. Each OEWS estimate blends three years of survey responses and is a May snapshot, so timing is blurry. The occupation description was checked word for word only for years with their own BLS page. The statement list started from commercial trackers, so every counted entry needs a primary source; the one tracker date I checked against company filings (C.H. Robinson, 2022) did not hold up. CPI-U is a general price index. AI is not the only force at work: interest rates and the post-pandemic hiring swing also matter.
