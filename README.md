# Supply-Chain-Management
Contents
Introduction
Data Exploration
Data Preprocessing
Data Visualization
Suggestions
Data Model comparison
Introduction
A Fast Moving Consumer Goods (FMCG) company entered into the instant noodles business two years back. Their higher management has noticed that there is a mismatch in the demand and supply. Where the demand is high, supply is pretty low and vice-versa which results in a loss in inventory cost and ultimately loss to the company. Hence, the higher management wants to optimize the supply quantity in each and every warehouse in the entire country.

Data Exploration
The datasets are given seperately for training and testing purposes.
Data Dictionary
Ware_house_ID : Unique Warehouse id where product is prepared for dispatch
WH_Manager_ID : Manager Id present in the warehouse
zone : Zone of the Warehouse
WH_regional_zone : Regional Zone of the warehouse
num_refill_req_l3m : Refilling request received by the warehouse in the last 3 months
transport_issue_l1y : No. of transport issued for warehouse in last 1 year
Competitor_in_mkt : No. of competitors in the market
retail_shop_num : Number of retail shops who sell noodlesproduced by the warehouse
wh_owner_type : The warehouse is owned by the company or it is on rent
distributor_num : No. of distributor who works between warehouse and retail shops
flood_impacted : Is the warehouse in a flood impacted area or not
flood_proof : Warehouse is having flood proof indicator
electric_supply : Does the warehouse have proper electric supply along with some power backup
dist_from_hub : distance from the warehouse to production hub
workers_num : no. workers in the warehouse
wh_est_year : warehouse establishment year
storage_issue_reported_l3m : storage issues reported by the warehouse in the last 3 months
govt_check_l3m : Government checking in last 3 months
temp_reg_mach : warehouse having temperature regulating machine indicator or not
approved_wh_govt_certificate : Type of approval warehouse having been issued by government
wh_breakdown_l3m : Number of times the warehouse faces thebreakdown in the last 3 months
product_wg_ton : Product weight
Both dataset has 25 columns
Train dataset contains 16620 rows
Test dataset contains 5529 rows
No. of columns with int datatype : 15
No. of columns with object datatype : 8
No. of columns with float datatype : 2
No. of unique values in each column for train dataset:
Unnamed: 0 16620
WH_Manager_ID 16620
Ware_house_ID 16620
retail_shop_num 4356
product_wg_ton 4248
dist_from_hub 217
workers_num 60
distributor_num 56
storage_issue_reported_l3m 37
govt_check_l3m 32
wh_est_year 28
Competitor_in_mkt 12
num_refill_req_l3m 9
wh_breakdown_l3m 7
transport_issue_l1y 6
WH_regional_zone 6
approved_wh_govt_certificate 5
zone 4
WH_capacity_size 3
flood_proof 2
flood_impacted 2
temp_reg_mach 2
Location_type 2
wh_owner_type 2
electric_supply 2

No. of unique values in each column for test dataset:
Unnamed: 0 5529
Ware_house_ID 5529
WH_Manager_ID 5529
product_wg_ton 2946
retail_shop_num 2891
dist_from_hub 217
distributor_num 56
workers_num 55
storage_issue_reported_l3m 37
govt_check_l3m 32
wh_est_year 28
num_refill_req_l3m 9
Competitor_in_mkt 9
wh_breakdown_l3m 7
WH_regional_zone 6
transport_issue_l1y 6
approved_wh_govt_certificate 5
zone 4
WH_capacity_size 3
electric_supply 2
temp_reg_mach 2
flood_impacted 2
Location_type 2
wh_owner_type 2
flood_proof 2

Data Preprocessing
This project mainly focuses on analyzing impact of features provided in the dataset on target variable product weight.

1. Drop irrelevent columns
Unnamed: 0
Ware_house_ID
WH_Manager_ID
These three columns each contain entirely distinct values. In the context of this project, the uniqueness of these columns holds no relevance, as they are only analyzing product quantity. Therefore, these three columns have been removed.

2. Missing values
Among the 25 columns, null values are present in three columns. These columns correspond to the number of workers in the warehouse (workers_num), the year of warehouse establishment (wh_est_year), and the grade of government certificate approved for the warehouse (approved_wh_govt_certificate).

Plot of null values in train dataset1
% of null values in each column:

workers_num(4.01 %)
wh_est_year(47.29 %)
approved_wh_govt_certificate(3.6 %)

Plot of null values in test dataset2
% of null values in each column:

workers_num(3.8 %)
wh_est_year(48.56 %)
approved_wh_govt_certificate(3.73 %)

workers_num :

numerical column
positively skewed Filled null values with median.
Train dataset3
Test dataset4
wh_est_year :

Since half of the values in the column wh_est_year are null, decided to drop it.

approved_wh_govt_certificate:

categorical column Filled null values with mode.
3. Duplicate values
No dupliocate values were present in both the dataset.

4. Outliers
Outliers were present in some of the columns. plotted boxplot to locate outliers.

Train dataset5

:6

Test dataset7

:8

Determined the count of outliers in every column. Among them, the 'flood_proof' and 'flood_impacted' columns, each containing only two distinct values, exhibit significant disparities in their value distributions and lack correlation. one of the unique values is considered as outlier due to its significantly lower proportion. Consequently, both of these columns were removed from the dataset.

Outliers were detected and removed

Data Visualization
Relationship between other features and target variable Product weight

Warehouse location type & Owner Type9

Electric_supply & temp_reg_mach availability10

Storage issue reported in the last 3 months11

No. of warehouse breakdown in the last 3 months12

zone & Regional_zone13

Type of approval by government14

govt checking in last 3 months15

No. of workers16

Warehouse capacity size & Transport issue17

Competitor_in_mkt18

No. of Distributors19

No. of refill request in last 3 months20

Distance from hub21

:22

Retail shop number23

Correlation Heatmap24

Suggestions
Focus on expanding warehouse operations in rural areas to capitalize on the higher average product weights and the larger share of total product weight, which can potentially lead to increased overall productivity and profitability.
Prioritize investment in temperature regulating machines and enhancing electric supply availability for warehouses to improve product weight and overall warehouse performance.
It is evident that, as production increases, storage issue increases. Hence, storage capacity must be upgraded to accomodate higher product weights. This highlights the importance of regularly assessing and expanding storage infrastructure in line with the production increments to ensure smooth warehouse operations and prevent bottlenecks.
Implement proactive maintanance protocols. Invest in scalable solutions to accomodate higher production levels while minimizing the risk of operational disruptions caused by breakdowns. Conduct comprehensive analysis to identify root causes of braekdowns during periods of heightened production.
Explore quality standards associated with different government approval grades. Identify opportunities to enhance product quality standards across all warehouse facilities.
Workers number does not significantly affect production. Examine various factors such as technology adoption, training programs, and workflow optimization strategies to understand their collective impact on production efficiency.
Data Model comparison
Actual values vs predicted values25

Evaluation Matrix26

Gradient Boosting Regression Model outperformed the others consistently across all metrics.
