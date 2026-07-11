# Global Superstore: Regional Profitability Analysis

**Tool:** Microsoft Excel (XLOOKUP, PivotTables, calculated fields, data validation, data mapping)  
**Dataset:** Global Superstore, around 51,000 order records across 13 regions, 2011 to 2014

## The question

Sales were growing but profit wasn't keeping up. So the question I set out to answer was simple to ask and less simple to answer: where across the 13 regions is the business actually losing money, and what is driving it?

The reason that matters is that a business can look fine in total while quietly losing money underneath. The overall margin here sat at a few percent, which on its own looks unremarkable. But an average like that hides as much as it shows, because it blends the strong regions and the failing ones together. The job was to pull them apart and find out which was which, and then work out the cause honestly instead of blaming the first thing that lined up with the losses.

## What I found

About a quarter of all sales were unprofitable, and the losses were not spread evenly across the business.

- The losses sat in three regions. Africa, EMEA, and Southeast Asia were running negative average margins, while the other ten regions stayed profitable. The business only looked healthy overall because the profitable regions were covering for the rest.
- Discounting was the factor most closely tied to the losses. The three loss making regions were discounting between 16 and 27 percent, while Canada, the healthiest region, discounted nothing and held the best margin. Across all the regions, the deeper the discount, the worse the margin.
- Shipping was not the cause. Before settling on discounting I wanted to check whether shipping was really behind it, so I tested both shipping cost and shipping delay. Neither lined up with the losses. Africa and EMEA actually had the lowest shipping costs in the company and were still losing money, which pointed back to discounting.
- Southeast Asia was a different shape from the other two. Most of the region was profitable. The damage came from a few heavily discounted categories (Tables, Accessories, Supplies, Fasteners) that were dragging the whole region into the red. So the fix there is targeted at those categories rather than applied to the whole region.

## Dashboard

![Global Superstore Regional Profitability Dashboard](dashboard.png)

The dashboard is built as one argument rather than a pile of charts. The first chart shows where the problem is, the second shows the cause, the third shows what it is not (shipping), and the fourth shows where inside Southeast Asia to actually act.

## Recommendations

- Treat the three loss making regions as the priority for a pricing and discount review.
- Cap discounts in those regions for a quarter and measure whether margins recover before making it permanent.
- In Southeast Asia, aim the discount limits at the specific categories that are losing money rather than the whole region, and check local demand before restocking them.

## How I worked through it

1. Cleaned and checked the data first. The dates came in as text and would not calculate, so I confirmed that and rebuilt them into real dates before doing any date maths. I built profit margin (Profit divided by Sales) and shipping delay (Ship Date minus Order Date) as new columns, and checked for duplicate rows.
2. Mapped targets onto the data. I built a small reference table giving each region a margin target and used XLOOKUP to pull those onto every row, so I could judge each region against a goal instead of just looking at raw numbers.
3. Tested the idea with PivotTables. I compared profit, sales, margin, and discount across the regions to find where the losses were and to see whether discounting explained them.
4. Tried to prove myself wrong. I tested shipping cost and shipping delay against the weak regions to see if shipping, not discounting, was the driver. It was not, and ruling it out is part of why I trust the finding.
5. Went down to product level. I broke the problem regions down by category, and checked the most extreme result against how many sales it was based on before treating it as a real finding.

## Data dictionary (key fields)

| Field | What it is |
|---|---|
| Order ID | Identifies each order. One order can appear across several rows, one per product. |
| Order Date / Ship Date | When the order was placed and shipped. Used to work out shipping delay. |
| Sales | Revenue for the line. Misleading on its own, since high sales can still lose money. |
| Profit | Gain or loss on the line. Can be negative. |
| Discount | Price reduction applied. The factor most closely tied to the losses. |
| Category / Sub-Category | Product groupings, used to find which products were losing money. |
| Region | Broad geographic area, 13 in total. The main focus of this analysis. |
| Shipping Cost | Cost to ship the order. Tested as an alternative cause and ruled out. |

Fields I added during the analysis: Profit Margin, Shipping Delay, and a Target Margin pulled from the reference table with XLOOKUP.

## What I would want you to know about the limits

I think being clear about what this analysis can and cannot say is part of doing it properly, so:

- It shows discounting is closely associated with the losses, not that discounting is the proven single cause. I only tested a limited set of explanations.
- The data covers four years, which is too short to say for certain whether things are getting better or worse over time.
- The dataset has nothing on regional economies, customer behaviour, or pricing strategy, so I can't test those and I don't claim them.
- The margin targets I used were reasonable assumptions I set for this exercise, not real company figures.
- Some numbers are averages that can hide variation. The most extreme result, Tables in Southeast Asia, is based on only 59 sales, so the direction is clear but the exact figure is shakier than the others.

## What I took from it

The most useful thing here was not a feature of Excel. It was learning to test my own conclusion before trusting it, and to look twice at a dramatic number before leaning on it. The striking finding is not always the whole story, and an honest analysis is worth more than an impressive sounding one.
