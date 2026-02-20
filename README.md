 

🏗️ Data Cleaning & Engineering

The cleaning phase focused on transforming "noisy" infrastructure logs into a high-fidelity analytical dataset ready for modeling and visualization

Structured Normalization:

After the data transformation, the data was normalized using “pd.read_csv()” with Data Sampling targeted delimiters (or custom string manipulation) to break down the concatenated text strings. 
This ensures that even without clear spacing, the dates, facility codes, and volumes were correctly isolated into independent columns. 
The DATE and TIME column are combined into unified TIMESTAMP Object to identify the busiest intervals and for pre/post - 2025 pricing analysis 

Catergorization and filtering:

Next, grouped various FAC_B descriptors into a standardized FAC_TYPE, merging “Crossing” and “Bridge" into a single “Bridge” category for accurate facility-level comparisons. 
Carrier Standardization is merging high-cardinality errors into one category (eg, merging “NJTransit” and “NJ Transit”) to avoid duplicates or prevent volume reporting and ensure accurate market share analysis.  
Implemented a MAINTENANCE_FLAG based on LANE_MODE to exclude the records where low speeds or low volume were strictly caused by scheduled repairs rather than lack of driver demands. 

 
Featured Engineering :

Violation Rate is created to quantify toll evasion rates or trends across different facility types.  
formula - Violation _Rate = Violation / Total 

Mobility Delta is calculated from free-flow speeds to isolate the physical impact of traffics surges and congestion.  
Formula - Delta = Avg_Speed - Freeflow 
