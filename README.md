# Global Superstore: Regional Profitability Analysis

## Project background

Global Superstore is a global online retailer selling office supplies, furniture, and technology to customers across many countries and regions. Like any retailer, its goal is not just to sell more but to make sure those sales actually turn into profit.

The business had a problem that is easy to miss. Sales were growing, but profit was not growing with them. That gap is worth taking seriously, because a company can look healthy on total sales while losing money underneath, in places the headline numbers hide.

This project analyses around 51,000 orders across 13 regions from 2011 to 2014 to answer one question: where is the business actually losing money, and what is driving it? The aim was to give a clear answer that someone making a pricing decision could act on, not just a set of charts.

The analysis was done in Microsoft Excel, and the findings are pulled together in a one page dashboard included in this repository.

## Headline numbers

- Total sales: $12.6M
- Total profit: $1.47M
- Net margin: 12%
- Share of sales that lose money: 24%

That last number is the one that started the investigation. Almost a quarter of all sales were unprofitable, so the question was never whether there was a problem, but where it sat and what was causing it.

## Executive summary

The losses are not spread evenly across the business. They sit in three regions, Africa, EMEA, and Southeast Asia, which all run negative average margins while the other ten regions stay profitable. The business only looks healthy overall because the profitable regions cover for the ones losing money.

The factor most closely tied to those losses is discounting. The three loss making regions discount the heaviest, between 16 and 27 percent, while Canada, the healthiest region, discounts nothing and keeps the best margin. Across all regions, the deeper the discount, the worse the margin.

Before settling on that answer, I checked whether shipping was really the cause instead. It was not. The loss making regions actually had some of the lowest shipping costs in the company and were still losing money, which pointed back to discounting.

Southeast Asia turned out to be a different shape from the other two. Most of the region was fine. The damage came from a small number of heavily discounted categories dragging the whole region into the red, which means the fix there can be targeted rather than applied across the board.

## Insights and recommendations

The analysis focused on these areas:

**Where the losses sit**
Africa, EMEA, and Southeast Asia run negative average margins while the other ten regions stay profitable. About 24 percent of all sales lose money, and these three regions are where that loss concentrates.
Recommendation: treat these three regions as the priority for a pricing and discount review, rather than spreading attention evenly across all regions.

**What is driving the losses**
Discounting is the factor most closely associated with the losses. The heaviest discounting regions have the worst margins, and the region that discounts nothing has the best. This pattern holds across all 13 regions.
Recommendation: cap discounts in the affected regions for a quarter and measure whether margins recover before making the change permanent.

**What is not driving the losses**
Shipping cost and shipping delay were both tested and neither lines up with the losses. Two of the loss making regions have the lowest shipping costs in the company.
Recommendation: avoid spending effort on logistics or shipping renegotiation for this problem, since the evidence points to discount policy instead.

**Where inside a region to act**
Southeast Asia is mostly profitable apart from a few heavily discounted categories (Tables, Accessories, Supplies, Fasteners) that pull the whole region negative.
Recommendation: aim the discount limits at those specific categories rather than the whole region, and check local demand before restocking them.

## Dashboard

![Global Superstore Regional Profitability Dashboard](dashboard.png)

The dashboard is built as one argument rather than a set of separate charts. It opens with the four headline numbers, then works through where the problem is, what is causing it, what is not causing it, and where inside Southeast Asia to act.

## The data

The dataset holds around 51,000 order lines, one row per product within an order, so a single order can span several rows. The fields that mattered most for this analysis:

| Field | What it is |
|---|---|
| Order ID | Identifies each order. Repeats across rows when an order has several products. |
| Order Date / Ship Date | When the order was placed and shipped. Used to work out shipping delay. |
| Sales | Revenue for the line. Misleading on its own, since high sales can still lose money. |
| Profit | Gain or loss on the line. Can be negative. |
| Discount | Price reduction applied. The factor most closely tied to the losses. |
| Category / Sub-Category | Product groupings, used to find which products were losing money. |
| Region | Broad geographic area, 13 in total. The main focus of this analysis. |
| Shipping Cost | Cost to ship the order. Tested as an alternative cause and ruled out. |

Fields added during the analysis: profit margin (Profit divided by Sales), shipping delay (Ship Date minus Order Date), and a target margin per region pulled in with XLOOKUP.

## How the analysis was done

1. Cleaned and checked the data first. The dates came in as text and would not calculate, so I confirmed that and rebuilt them into real dates. I added profit margin and shipping delay as new columns and checked for duplicate rows.
2. Set a benchmark for each region. I built a small reference table of margin targets and used XLOOKUP to pull them onto every row, so each region could be judged against a goal rather than a raw number.
3. Located the losses with PivotTables. I compared profit, sales, margin, and discount across the regions to find where the money was leaking and to test whether discounting explained it.
4. Tested the alternative. I checked shipping cost and shipping delay against the weak regions to see if shipping was the real cause. It was not, and ruling it out is part of why I trust the finding.
5. Went to product level. I broke the problem regions down by category, and checked the most extreme result against how many sales it was based on before treating it as real.

## What this analysis does not claim

Being clear about the limits is part of doing this properly.

- It shows discounting is closely associated with the losses, not that it is the proven single cause. Only a limited set of explanations was tested.
- The data covers four years, which is too short to say for certain whether things are improving or getting worse over time.
- The dataset has nothing on regional economies, customer behaviour, or pricing strategy, so those cannot be tested and are not claimed.
- The margin targets used were reasonable assumptions set for this exercise, not real company figures.
- Some figures are averages that can hide variation. The most extreme result, Tables in Southeast Asia, rests on only 59 sales, so its direction is clear but its exact figure is less reliable.

## Tools

Microsoft Excel: XLOOKUP, PivotTables, calculated fields, data validation, data mapping, and a one page dashboard.
