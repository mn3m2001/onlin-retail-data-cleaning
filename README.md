
 Online Retail — Data Cleaning & Analysis

A portfolio project using Python, pandas and Matplotlib to prepare retail transaction records and explain country, product and daily results.

Results

- Input records --> 5,000 
- Records after excluding identical extra rows --> 4,921 
- Descriptions filled from the same product code --> 4 
- Descriptions still missing --> 8 
- Positive transaction value (GBP) --> 103,763.71 
- Negative transaction value (GBP) --> -1,866.33 
- Net transaction value (GBP) -->> 101,897.38 

The UK contributes about 96.06% of sample net transaction value. Product code is 22423, REGENCY CAKESTAND 3 TIER, ranks first at GBP 3,480.09.

 Method
1. Inspect schema, missing values and identical rows.
2. Restore four missing descriptions using matching product codes; retain unknown descriptions and customer IDs.
3. Convert CustomerID to nullable integers. Create a separate deduplicated analysis copy.
4. Retain negative quantities and zero prices; calculate signed `line_total = Quantity * UnitPrice`.
5. Aggregate by country, product code and date; reconcile country and daily totals against the overall total.

 Charts
- Top five countries --> images/chart-1.png
- Top five product codes --> images/chart-2.png
- Daily net transaction value --> images/chart-3.png

 Run
Install dependencies with `python -m pip install -r requirements.txt`, open `online-retail-cleaning.ipynb` in Jupyter or VS Code, and run cells in order. Keep the supplied Excel file beside the notebook. In Google Colab, upload the Excel file when prompted. No paid services or credentials are required.

 Source and attribution
The Excel file contains the first 5,000 records, in source order, from UCI Online Retail (https://archive.ics.uci.edu/dataset/352/online+retail), credited to Daqing Chen. DOI: https://doi.org/10.24432/C5BW33. Dataset license: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The supplied source sample is uncleaned; transformations are documented in the notebook.

 Limits
- Sample interval: 2010-12-01 08:26 to 2010-12-02 18:08. It is not a representative annual sample; neither calendar day is guaranteed complete.
- Removing 79 identical extra rows is an analytical assumption, not proof of erroneous recording. The in-memory `df` retains these rows for comparison.
- Negative values include a Discount line; they are not all proven returns. Zero-price records are retained without inventing prices.
- Amounts are signed transaction values, **not profit**. Missing customer IDs prevent attributing every transaction to a known customer.
- This is a project on public data, not paid work delivered for a client.

--ملخص عربي
مشروع  لتنظيف وتحليل أول 5000 سجل من بيانات متجر. يشمل مراجعة القيم الناقصة والتكرارات، حساب قيمة العمليات، و3 رسوم. النتائج تخص العينة خلال 1–2 ديسمبر 2010 فقط. الصافي ليس ربحًا،مع ازاله التكرار. شغّل الخلايا بالترتيب وتأكد من وجود ملف Excel بجوار الـNotebook.

