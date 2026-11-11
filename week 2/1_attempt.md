Problem 1:There is duplicated row ,the row 96 and 8 matches each other
code:raw[raw.duplicated(keep=False)]
decision:use clean=clean.drop_duplicates() to remove any duplicated rows
reason:Duplicate records give invalid summary statistics, counts, and inflation rate calculations.

problem 2:Missing price value
code:raw.isna().sum()
decision: remove rows with unrecoverable prices
reason: missing number make it difficult to do mathematical calculations

problem 3:there is oil b in one of the rows which has incorrect casing 
code:raw["item"].value_counts()
decision:using clean["item"] = clean["item"].str.strip().str.title() to fix all the casing and any spaces in between.

problem 4: in rows where thousand seperaters are used it caused the entire price column to be stored as string object
code:raw[number.isna()][["date","item","city","price"]]
decision: using .str and.replace to remove these commas
reason:commas cannot be converted to floats directly
