---
type: brief
engagement: case-1-perfect-competition
capability: marginal-analysis
date: 2026-08-26
status: committed
hypothesis: "Mesclun and carrot heavy mix (30, 20) in comparison to tomatoes (14) because tomatoes use the most resources, time and labor with most diminishing returns"
---

# Perfect Competition — Engagement Brief

## The problem
A farmer is trying to decide what and how much to plant in one season in order to optimize profit. Farmers operate on such small profit margins that a bad decision could cost them the business and leave them without enough money to survive.

The price is fixed by the farmer's market, since the farmer isn't big enough to influence it. They are limited by time and resources, with only sixty-four beds and three crops to work with (tomatoes, carrots, mesclun), and need to plan strategically what to grow in one season. Time is a resource they can't get back, so they need to get it right in order to keep buying seeds, labor and other resources for future seasons.

## What I am assuming
I am assuming that the weather will be optimal for all three crops, that I have already hired all the labor I need for the season, and that all of the resources will be available when I'm ready to start. Essentially, I am not factoring in weather delay or myself or a laborer quitting or getting sick.

Here is what the brief provided:

- Season = 36 weeks
- 64 beds (16 beds × 4 plots)
- Fixed costs = $20,000
- The farmer's pay: $50,000 a season, spends half her time in the field (720 hours, implied $34.72/hr)
- Can hire up to 4 temporary workers at $25,000 each for 1,440 hours each ($17.36/hr)

| Crop | Max Beds | Price $/bed | Labor hrs/wk/bed | Fertilizer $/bed | Diminishing returns |
|---|---|---|---|---|---|
| Tomatoes | 20 | 8,800 | 2.5 | 880 | 10.00% / bed |
| Carrots | 20 | 2,094 | 0.833 | 440 | 2.50% / bed |
| Mesclun | 30 | 2,700 | 1.25 | 880 | 1.25% / bed |

## Hypothesis
Although it's the highest revenue per bed, I predict that the farmer would need to plant fewer tomatoes than carrots and mesclun, based on the 10% diminishing returns for tomatoes. Carrots and mesclun also take less labor. Out of the 64 beds, I would assume 14 tomatoes, 20 carrots, and 30 mesclun to maximize possible profit. I debated splitting the beds of carrots evenly with mesclun but realized I could plant more beds of mesclun than carrots and earn more per bed. Also, carrots are capped out at 20 beds. Carrots take less labor and less fertilizer, so I planned the next-highest amount for them. Tomatoes came last, based on their high labor, high cost, and diminishing returns.

## How I would know I was wrong
To test my hypothesis, I will build an Excel sheet and run the actual math against the claims I made in my hypothesis (outlined below). From there, I will be able to see the ideal combination of crops needed to maximize profits based on available resources and costs. Below are the outcomes tied to each claim that will show whether I was right or wrong.
- Claim #1: All 64 beds should be used. If the model leaves any beds empty, then my "use all available resources" strategy was not the right approach. It would show that some resources or labor could have been saved for the next season and that some beds were not worth planting.
- Claim #2: The 10% diminishing returns rate keeps tomatoes below their 20-bed cap. I predicted 14. If the model's answer falls within a 4-bed margin (explanation for this specific margin is in claim #4) either way, I would say it's close enough to be considered correct.
- Claim #3: Carrots and mesclun should be planted to their max caps, 20 and 30 beds respectively. Applying the same 4-bed margin from claim #2, if the model plants either or both below its cap and shifts those beds to tomatoes instead, I would be okay with calling that close enough.
- Claim #4: Aside from the exact numbers, I predicted the ranking of how much of each crop should be planted (mesclun most, carrots second, tomatoes least). It is very possible that I've gotten the exact numbers wrong, but I will still be pleased if I at least get the ranking correct. If the model returns a different ranking, I was incorrect about the overall ratios and ultimately about how diminishing returns, resource costs, and labor costs affect the case. Also, I'm allowing myself a 4-bed margin (equal to ¼ of a plot) because my reasoning here is qualitative rather than computed and to leave room for human error. Personally, anything beyond that (5 beds and above) would tell me that my initial estimate of how labor and resource costs affect the ranking was significantly off.
