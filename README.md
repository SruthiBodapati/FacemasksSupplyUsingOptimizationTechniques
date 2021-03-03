
Summary
In this report, we present models for optimizing the acquisition of a variety of face masks intended to be used by care providers to care for victims of the Covid-19 pandemic.
Our models will consider 33 hospitals the San Francisco Bay Area, and both surgical and N95 face masks.
A surgical mask is a loose-fitting, disposable device that creates a physical barrier between the mouth and nose of the wearer and potential contaminants in the immediate environment. These are often referred to as face masks, although not all face masks are regulated as surgical masks. Note that the edges of the mask are not designed to form a seal around the nose and mouth. (U.S. Food and Drug Administration, 2020)
An N95 respirator is a respiratory protective device designed to achieve a very close facial fit and very efficient filtration of airborne particles. Note that the edges of the respirator are designed to form a seal around the nose and mouth. Surgical N95 Respirators are commonly used in healthcare settings and are a subset of N95 Filtering Facepiece Respirators (FFRs), often referred to as N95s. (U.S. Food and Drug Administration, 2020)
In the treatment of an infectious patient, staff uses disposable Personal Protective Equipment, or PPE. This equipment can be masks, gowns, face shields, gloves, hazmat suits,
4
and so on. Typically, PPE is used one time for one patient and then discarded. A nurse may use many sets of PPE during a shift.
Sadly, this is not the case for the COVID-19 pandemic. The demand created on the health system so far exceeds any previous plans that PPE is unavailable in many places. In some cases, nurses have had to use the same N95 respirator for two weeks, storing it in a Ziploc bag between shifts.
On Wednesday March 4th, the U.S. Department of Health and Human Services (HHS) stated that the Strategic National Stockpile (SNS) has approximately 1% of the needed supply for the Covid-19 pandemic. This amounts to 12M N95 masks and 30M surgical masks. (Berkeley Lovelace Jr. @ CNBC, 2020)
As a result, hospital systems have been left to acquire their own PPE via market channels, in competition with everyone else in the demand pool. Our model seeks to inform the decision makers in Bay Area hospitals as to the amount and cost of acquiring the requisite PPE.
5
Introduction
We have set our focus on acquiring the correct number of masks given some variety of conditions.
One of the conditions we forecast is demand. The San Francisco Bay Area was the first to enact shelter-in-place (SIP) restrictions and depending on the rate of adherence to the SIP order we can expect demand to be variable. If 100% of people stay home and have no contact, then we can expect lower demand than if 75% of people breached the SIP order to congregate and further spread the virus. In our LP and Simulation models we use three levels of demand with varying probability.
We have had to make some assumptions about the number and cost of masks. Clearly the situation is so dire that calculating the pre-pandemic number of masks is not viable. There are not enough masks to use the standard protocol of “one set of PPE per patient visit”. We have used the standard of one mask per day per nurse. We have also assigned an average market price of $20 per mask under the same presumption as demand…that we are at the start of the pandemic and as such the demand is unknown and the price for PPE isn’t yet put under control by the government.
We intend to show Simulation models to determine demand, LP models for optimal supply chain choices, and Decision Analysis to consider the effects of supplier mask quality and defects if we were limited to choosing one supplier. We hope you find our content informative.
6
Data Collection and Analysis
In order to optimize the usage of masks, we must determine the demand of masks in Alameda County hospitals and medical facilities. As of data reported by Alameda County’s Data Sharing Initiative database, there were a total of 33 hospitals and 8,422 inpatient beds (Alameda County). It can be assumed that utilization volume is a percentage of the total number of inpatient beds.
In order to determine the amount of maximum staff that would be working on any given day, we can assume that each nurse on average works an 8-hour shift. This means that on any given day, there are 3 shifts of nurses working. Each nurse is assumed to wear 1 mask per shift.
We can estimate the number of nurses to be staffed using the California nurse staffing ratios that are mandated by the California Department of Public Health via Title 22 of the California Code of Regulations, Section 70217 (Kasprak). The regulation calls for a 1:2 ratio in Intensive Care Unit environments (ICU). Due to the pandemic hospitals are only treating the ‘worst of the worst’ cases and so we will use the ICU rates for our models. Some field research indicates this may be a conservative estimate, but it will suffice for our academic purposes.
From the ICU ratio of 1:2, we can calculate the number of nurses we will need and subsequently the numbers of masks. For example, with 100% utilization of beds (8,422) we will demand 4,211 nurses at all times. Using three shifts of nurses per day each with one mask gives us 12,633 nurses and masks per day.
Finally, for demand we’ve made some assumptions about the pervasiveness of the virus spread. We think there is a low probability the virus will be contained. A greater probability the virus will spread moderately, and a high probability the virus will have high spread.
We’ve translated that to the following levels and probabilities of utilization:
• 10% probability of 25% utilization of total beds
• 35% probability of 75% utilization of total beds
• 55% probability of 100% utilization of total beds.
7
Simulation
Simulation of Mask Demand and Cost
In order to optimize daily face mask demand and cost, we performed Monte Carlo simulations utilizing three different methodologies and probability of different levels of utilization: excel simulation utilizing discrete demand distribution and random numbers, @Risk simulation using the discrete demand distribution and @Risk simulation using the normal demand distribution. We selected simulation because we have uncertainty surrounding our decision variables and there are a lot of unknown elements such as hospital utilization or staffing.
For these simulations, we will use the average cost of $20 per mask from 3 different suppliers.
Figure 1 - Cost per mask
Additional modeling related to supplier mix and cost optimization was performed in another section.
We also recognized that at each potential level of demand, there may be a range of plus or minus 10% of staffing needed. This range reflects the uncertainty in the nurse to patient ratios as not all patients will be admitted to ICU level units. While we used the ICU level staffing in order to be conservative in our estimate. In reality, there are going to be patients that are suffering from less acute symptoms and will require less observation. As such, the range of plus or minus 10% reflects our uncertainty.
8
Figure 2 - Nurse Staff Demand
Using a discrete demand distribution, we selected the average between the low and high range of staff needed at each capacity level. The weighted-average demand using the sumproduct function is 10,580 masks with a standard deviation of 3,186 (see table below). Using a normal demand distribution, we utilized the discrete demand distribution’s average demand and standard deviation.
Figure 3 - Demand Distribution
9
Figure 4 - Simulation Results
Daily Costs
Running a simulation in excel using random numbers for 1,000 simulations and without using @Risk, there is an estimated daily demand of 10,615 masks and a daily cost of $212,297.57. Running a simulation with @Risk with a discrete demand distribution, there is an estimated daily demand of 9,475 masks and a cost of $189,495.00. Running a simulation with @Risk with a normal demand distribution, there is an estimated daily demand of 10,580 masks and a cost of $211,602.75.
Monthly Costs
Running a simulation in excel using random numbers for 1,000 simulations and without using @Risk, there is an estimated monthly demand of 318,446 masks and a daily cost of $6,368,926.95. Running a simulation with @Risk with a discrete demand distribution, there is an estimated daily demand of 284,243 masks and a cost of $5,684,850. Running a simulation with @Risk with a normal demand distribution, there is an estimated daily demand of 317,404 masks and a cost of $6,348,082.50.
Simulation of Mask Demand and Cost Analysis
Two out of the three simulation methods, simulation in Excel without @Risk using random numbers estimate monthly demand of approximately 317,000 to 319,000 and a monthly cost of approximately $6.3 million to $6.4 million. These two methods yield a higher demand and cost
10
than the simulation with @Risk using the discrete demand distribution. As we are attempting to predict the demand of face masks to be used while minimizing costs if possible, we also want to ensure that we provide enough masks to meet demand based on patient utilization and associated staffing. As such, in this situation, we may not want to use the lowest cost option. Rather, we may want to use the most progressive monthly estimates of approximately 319,000 masks with an approximate cost of $6.4 million.
11
Optimization Modeling
Supply Chain Management (Outsourcing)
Using the same inputs as the simulation (33 hospitals, 8,422 beds, 4,211 nurses per shift) we’ll consider the following supply chain model.
Hospitals typically outsource face mask production in order to maintain an efficient supply chain. The pandemic has created new demand conditions and the staff require N-95 masks and surgical masks in a quantity that was not prepared or planned for by anyone. While face mask procurement is a key part in keeping staff safe and control virus spread, it is important to keep in mind the financial burden on hospitals. As hospitals incur significantly higher costs, some hospital operations have had to cut back on staffing. In some smaller community hospitals, there is a long-term going concern issue. As such, we want to be able to optimize the supply chain in order to minimize costs while procuring enough face masks in case of a surge.
Hospitals need to understand how many face masks need to be acquired from different suppliers in order to minimize the total monthly cost for Alameda County hospitals. Hospitals also need to ensure enough masks are procured. Given the objective function (minimize costs) and decision variable (number of masks), we used a supply chain management model. We will assume three hypothetical suppliers as described below. We have also assumed the same cost for each mask type due to the significant increases in demand causing prices of all mask types to increase to a new market equilibrium. We have also assumed a product mix percentage for each supplier below.
12
Suppliers
Cost per mask
Proportion of N 95 Masks
Proportion of Surgical Masks
Supplier 1,S1
$21
0.40
0.60
Supplier 2,S2
$20
0.25
0.75
Supplier 3,S3
$19
0.55
0.45
Figure 5 - Supplier Breakdown
In the simulation section of this report, we determined that approximately 319,000 face masks are required each month. While utilizing this simulated amount of mask may make sense, from a practical standpoint, we need to ensure that enough masks are procured in case of additional surges and as reserve. We assume that at minimum, Alameda County would require at least a one-month reserve of face masks. As such, we took our solution for the simulation section and doubled the number (319,000 x 2) and rounded up to the nearest hundred thousand. Therefore, the total number of face masks we will be ordering is 700,000. We also assumed that we would want a mix of mask types as N-95 masks are typically not used in all medical care settings. We assumed that each month, Alameda County can place an order with each given hypothetical supplier. At least 300,000 N-95 masks and 400,000 surgical masks must be purchased each month.
We also assumed that each supplier would have supply constraints due to production volume and contract issues. Because of the limited availability of these masks due to high demand, we assumed that at most, 500,000 masks per month could be purchased from each supplier. Assuming contractual obligations with Supplier 1, Alameda County would need to purchase at least 100,000 masks. We assumed that Alameda County would like to purchase at least 300,000 masks from Supplier 3 which has the lowest cost per mask.
13
S1, S2, and S3 are decision variables and below are the constraints developed from the above information.
Constraints:
Formula
Number of purchased N95 Masks at least 300,000
0.4S1 + 0.25S2 + 0.55S3 >= 300,000
Number of purchased Surgical Masks at least 400,000
0.6S1 + 0.75S2 + 0.45S3 >= 400,000
Quantity from Supplier 1 at most 500,000 masks
S1 <= 500,000
Quantity from Supplier 2 at most 500,000 masks
S2 <= 500,000
Quantity from Supplier 3 at most 500,000 masks
S3 <= 500,000
Total masks purchased from supplier S1 at least 100,000
S1 >= 100,000
Total masks purchased from supplier S3 at least 300,000
S3>=300,000
Non-negativity
S1, S2, S3 >= 0
Figure 6 - Constraints
14
Below is the Mathematical formulation of our model:
Figure 7 - Mathematical Formulation
The optimal solution is to purchase 100,000 masks from Supplier 1, 233,333 masks from Supplier 2 and 366,667 masks from supplier 3. From Supplier 1, we are going to purchase 40,000 N-95 masks and 60,000 Surgical masks. From Supplier 2, we are going to purchase 58,333 N-95 masks and 175,000 Surgical masks. From Supplier 3, we are going to purchase 201,667 N-95 masks and 165,000 Surgical masks. Given the constraints, the minimal cost for these purchases is $13,733,333.
The supplier breakdown is below, followed by the minimized objective function, total cost.
15
Suppliers
Total number of masks
Cost per mask
N 95 masks
Surgical Masks
S1 =
100,000
$21
40,000
60,000
S2 =
233,333
$20
58,333
175,000
S3 =
366,667
$19
201,667
165,000
Figure 8 - Supplier Optimization
Objective Function
Cost($)
Minimize total costs, $
13,733,333
Figure 9 - Objective Function Outcome
Figure 10 - Model Solution spreadsheet
16
Sensitivity Analysis
When we investigate the sensitivity report, we can see that none of the constraints have a negative shadow price, and several have a shadow price of zero. This means that if Alameda County would like to negotiate a higher availability of masks without increase in cost, they would need to go with Supplier 3 for an allowable increase of 66,667 mass.
As the reduced cost for all the decision variables (all suppliers) is 0, the initial cost from all suppliers will remain the same.
Figure 11 - Sensitivity Report
One-way Sensitivity Analysis
Using one-way sensitivity analysis for the RHS of the last constraint in the revised model (cell $D$17), we investigate the effect on the total cost of changing the number of masks from Supplier 1 from 0 to 300,000 units. The results of this analysis show that for every 10,000 units of increase in mask purchase from Supplier 1, the total cost increases by $15 between 0 and 230,000 masks, by $50 from 240,000 to 300,000.
17
As purchase from supplier 1 increases, the number of units from suppliers 2 and 3 will experience a downward tendency and the optimal value to minimize cost increases to the variations of purchase from supplier 1. Below graph represents that increase in total cost if we increase purchase of masks from S1.
Figure 12 - Sensitivity of Total Cost to Supplier 1
18
Decision Analysis
Selecting a Single Supplier
With Alameda County hospital resources and capital being scarce, it is likely that hospitals will be forced to limit the number of vendors it contracts with. In a hypothetical situation in which only one supplier can be selected to contract with due to cost and vendor contract constraints, the hospitals should consider the effect face mask quality and defects.
Figure 13 – Decision Tree Inputs and Factors
Using the number of required masks from the supply chain management linear programming model, we can assume that if we were going to choose only 1 supplier, we would order 700,000 face masks from any one of the 3 suppliers. Using the prices given in the simulation and linear programming model, the calculated expected monetary value (cost) is
19
given in the chart below: Supplier 1: $14,700,000 Supplier 2: $14,000,000 and Supplier 3: $13,300,000.
For Supplier 1, we assume a probability of 10% of masks will be defective which will translate to a defective mask cost of $1,470,000 which will need to be replaced. For Supplier 2, we assume a probability of 20% of masks will be defective which will translate to a defective mask cost of $2,800,000 which will need to be replaced. For Supplier 3, we assume a probability of 30% of masks will be defective which will translate to a defective mask cost of $3,990,000 which will need to be replaced.
Additionally, because we will want to expedite mask replacements, we assume that there is a replacement cost fee from each supplier. Given a 10% replacement fee for Supplier 1 and 70,000 potentially defective masks, there would be an additional fee of $147,000. Given a 15% replacement fee for Supplier 2 and 140,000 potentially defective masks, there would be an additional fee of $420,000. Given a 20% replacement fee for Supplier 3 and 210,000 potentially defective masks, there would be an additional fee of $798,000. These costs will need to be included in our decision as well.
20
Figure 14 – Decision Tree
Figure 15 – Optimal Decision Tree
When analyzing the decision tree, with all defect and replacement costs included, Supplier 1 has a total cost of $14,994,000, Supplier 2 has a total cost of $14,980,000 and Supplier 3 has a total cost of $15,295,000.
21
Given the inputs and factors noted, our decision tree analysis shows that if we had to choose only 1 supplier and considered defects and related charges, we would select Supplier 2. While Supplier 2 is not the cheapest mask producer (Supplier 3 had the cheapest face masks at $19 per face mask), nor the highest quality mask producer (Supplier 1 had both the lowest probability of defects at 10% and lowest replacement fee at 10%), the mix of defects and replacement fee costs in addition to the initial total purchase cost contribute to Supplier 2 being the most optimal choice when having to select one supplier.
22
Conclusion
In this project, using Excel Solver, Excel Solver Table add-in and @Risk add-in, we were able to determine the optimal quantity of face masks to order for hospitals in Alameda county. Through the Optimization Model we were able to find the best order combination to have between our three suppliers while ensuring we kept within our constraints.
We performed three Monte Carlo Simulations, two of which used the @Risk add-in. These simulations were done because we had uncertainty surrounding our decision variables and there are a lot of unknown elements such as hospital bed utilization and staffing. Two of the three simulations calculated a daily face mask demand of 10,600 to 10,700 and a cost of $211,000 to $212,500. This will give us a monthly demand of 317,000 to 319,000 and a monthly cost of approximately $6.3 million to $6.4 million. For these calculated outcomes, the hospitals should choose to purchase enough masks to meet the higher end of the uncertain demand, rather than simply the lowest cost option.
Our Optimization Model shows that to supply over 12,000 employees and build at least a one-month reserve of face masks, hospitals in Alameda County will have to purchase a minimum of 700,000 masks from the 3 suppliers. From Supplier 1 Alameda County’s hospitals need to purchase 40,000 N-95 masks and 60,000 Surgical masks. From Supplier 2 the hospitals need to purchase 58,333 N-95 masks and 175,000 Surgical masks. Finally, from Supplier 3 the hospitals need to purchase 201,667 N-95 masks and 165,000 Surgical masks. These purchases will total to a minimum cost of $13,733,333. By incorporating this strategy Alameda County can supply its healthcare workers with necessary protective equipment without overspending.
In the situation where only one supplier could be selected and when taking into account defects and replacement costs, Supplier 2 was the optimal choice with the lowest all-in cost of
23
$14,980,000 when compared to Supplier 1 with a total cost of $14,994,000 and Supplier 3 with a total cost of $15,295,000. If hospitals or Alameda county were limited to one supplier, Supplier 2 should be selected to provide facemasks at the lowest cost.
24
References
Alameda County Data Sharing Initiative. (2020, 12 19). Hospitals with Bed Counts. From data.acgov.org: https://data.acgov.org/datasets/189764738fb248a89e3bfa75918d5953_0/data
Berkeley Lovelace Jr. @ CNBC. (2020, 03 04). HHS clarifies US has about 1% of face masks needed for ‘full-blown’ coronavirus pandemic. From cnbc.com: https://www.cnbc.com/2020/03/04/hhs-clarifies-us-has-about-1percent-of-face-masks-needed-for-full-blown-pandemic.html
Kasprak, John. (2004, 02 10). California RN Staffing Ratio Law. From California RN Research Report: https://www.cga.ct.gov/2004/rpt/2004-R-0212.htm
U.S. Food and Drug Administration. (2020, 04 05). N95 Respirators and Surgical Masks (Face Masks). From U.S. Food and Drug Administration: https://www.fda.gov/medical-devices/personal-protective-equipment-infection-control/n95-respirators-and-surgical-masks-face-masks
25
Appendices
● Simulation in Excel without @Risk: Measures
● Simulation with @Risk-Discrete
26
● Simulation with @Risk-Normal
27
• Decision Analysis: Probability Chart
