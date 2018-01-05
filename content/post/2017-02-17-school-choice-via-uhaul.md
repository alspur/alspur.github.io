---
title: School choice via U-Haul
date: 2017-02-17T13:21:00-05:00
tags: 
  - ed policy
  - school choice
  - data

---

Earlier this week, [Alex Hernandez](http://www.twitter.com/thinkschools) argued that 43 percent of children in the United States are benefiting from school choice. [In The 74, he wrote](https://www.the74million.org/article/hernandez-devos-should-tell-her-critics-all-kids-deserve-school-choice-just-like-theirs-have):

> School districts assign children to public schools based on where they live. Then, the world’s largest game of musical chairs begins. The families of 24 million students find ways around their forced assignments to get the schools they want for their kids.  
>   
> The biggest school choice group is families who move to a new neighborhood to change their assigned school. They represent an estimated 8.2 million students, about one third of all school choosers. To be clear: The most popular way to choose a school in America is to literally move your family.  

This led me to wonder: what kinds of families are able to choose a school for their child by moving? Thankfully, Hernandez shows his work in [a Medium post](https://medium.com/@thinkschools/the-74-million-hernandez-devos-should-tell-her-critics-all-kids-deserve-school-choice-just-like-21d250c48e0f#.r6scv7i9l), revealing the specific NCES reports he used to generate his estimates. His data comes from the [NCES National Household Education Surveys Program](https://nces.ed.gov/nhes/dataproducts.asp), specifically the Parent and Family Involvement in Education (PFI) survey. 

Earlier this month, I was at an [SDP workshop](http://sdp.cepr.harvard.edu) and heard from [Alex Bowers](https://twitter.com/alex_j_bowers) on the kinds of research you can do with publicly-available education data, including NCES surveys. 

I took this coincidence as a sign to take the advice of one Alex (Bowers) and extend the work of another Alex (Hernandez). All of the analysis below was performed using this publicly available data and [the code is available on GitHub](https://github.com/alspur/nces_household_survey).

## Who are the movers?
Moving isn’t cheap. Families with more financial resources are more able to absorb the costs associated with moving to a neighborhood with a more desirable zoned school. Generally, as household income rises, students are more likely to have moved to their neighborhood specifically for the school. The following graph shows how frequently parents responding to the NCES survey decided to move neighborhoods for a better school, broken down by household income.

![inc_move_pct](https://raw.githubusercontent.com/alspur/nces_household_survey/master/figures/inc_move_pct.png)

The racial demographics of each income bracket vary. Higher-income movers are less racially diverse than lower-income movers.

![race_in_move](https://raw.githubusercontent.com/alspur/nces_household_survey/master/figures/race_inc_move.png)

Splitting the chart above by racial group, we can see how likely a family is to move given their race and their incomes. We can see that the groups most likely to move neighborhoods for better schools are white and Asian families with a six-figure household income. 

![race_in_move_pct](https://raw.githubusercontent.com/alspur/nces_household_survey/master/figures/race_inc_move_pct.png)

## What are the most popular destinations for movers?
The public NCES survey data doesn’t include precise location data, but it does provide the **type** of neighborhood where these families live. It’s not surprising to see that most movers head for the suburbs. For clarification on what separates a “suburb, large” from a “town, distant” check out [their definitions on the NCES website](https://nces.ed.gov/surveys/ruraled/definitions.asp).

![zip_move](https://raw.githubusercontent.com/alspur/nces_household_survey/master/figures/zip_move.png)

This chart shows the volume of movers by their chosen destination and their household income. It’s pretty clear that affluent families overwhelmingly choose to move to either suburbs or “rural, fringe” areas, defined as:

>Census-defined rural territory that is less than or equal to 5 miles from an urbanized area, as well as rural territory that is less than or equal to 2.5 miles from an urban cluster

![inc_move_zip](https://raw.githubusercontent.com/alspur/nces_household_survey/master/figures/inc_move_zip.png)

For lower-income families, suburbs are still a popular destination, but they are much more likely to choose cities or towns.

![inc_move_zip_pct](https://raw.githubusercontent.com/alspur/nces_household_survey/master/figures/inc_move_zip_pct.png)

Mover destinations by race reveal a consistent preference for suburbs, with varying degrees of preference for other destination types.

![zip_race_move_pct](https://raw.githubusercontent.com/alspur/nces_household_survey/master/figures/zip_race_move_pct.png)

I’ve only scratched the surface of what we can learn from this particular survey. It has a lot more information I’d like to investigate, including parents’ views on school quality, if their students are in their first-choice school, and more. The survey has also been administered in 2007, 2005, and 2003, so it would be interesting to track some of these patterns on both sides of the Great Recession. 

Publicly-available education data is pretty cool. 