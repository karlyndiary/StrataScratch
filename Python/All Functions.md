### EASY
| Function | Description |
|----------|-------------|
| dt.month = 4 | Selecting rows where the month component of a datetime column equals April. |
| employee['avg_salary'] | Creating a new column named 'avg_salary' in the 'employee' DataFrame. |
| employee.groupby('department')['salary'].transform('mean') | Grouping the 'employee' DataFrame by 'department' and calculating the average salary for each group, then broadcasting these mean values back to the original DataFrame. |
| ['end_time'].max() | Returning the highest value from the 'end_time' column. |
| ['movie'].count() | Counting the number of occurrences of values in the 'movie' column. |
| oscar_nominees[oscar_nominees['nominee'] == 'Abigail Breslin'] | Isolating rows where the 'nominee' column equals 'Abigail Breslin' in the 'oscar_nominees' DataFrame. |
| ['event_name'].value_counts() | Counting the occurrences of each unique value in the 'event_name' column. |
| pd.merge(customers, orders, left_on='id', right_on='cust_id', how='left') | Merging the 'customers' and 'orders' DataFrames on the 'id' and 'cust_id' columns respectively, using a left join. |
| .sort_values(['first_name', 'order_details']) | Sorting the DataFrame by the 'first_name' and 'order_details' columns. |
| [['home_library_code']].drop_duplicates() | Dropping duplicate values from the 'home_library_code' column. |
| sf_public_salaries[sf_public_salaries['jobtitle'].str.contains('CAPTAIN')] | Filtering rows in the 'sf_public_salaries' DataFrame where the 'jobtitle' column contains the string 'CAPTAIN'. |
| lyft_drivers[(lyft_drivers['yearly_salary'] <= 30000) (lyft_drivers['yearly_salary'] >= 70000)] | Filtering rows in the 'lyft_drivers' DataFrame where the 'yearly_salary' column is less than or equal to $30,000 or greater than or equal to $70,000. |
| amazon_shipment['shipment_date'].dt.strftime('%Y-%m') | Formatting the 'shipment_date' column as a string with the format 'YYYY-MM'. |
| df[df['first_name'].isin(['Jill', 'Eva'])] | Selecting rows from the DataFrame where the 'first_name' column is either 'Jill' or 'Eva'. |
| [yelp_reviews['cool'] == yelp_reviews['cool'].max()] | Returning rows where the 'cool' column value equals the maximum value in the 'cool' column. |
| .value_counts() | Counting the occurrences of unique values in a Series. |
| .nunique() | Counting the number of unique values in a Series. |
### MEDIUM
| Function | Description |
|----------|-------------|
| df = df.drop_duplicates(subset=['user_id', 'device']) | Removing duplicate rows from the DataFrame based on the values in the 'user_id' and 'device' columns. |
| df = winemag_p1[winemag_p1['description'].str.lower().str.contains("\\bplum\\b")] | Filtering rows in the 'winemag_p1' DataFrame where the 'description' column contains the words 'plum', 'cherry', 'rose', or 'hazelnut' (case-insensitive). |
| median_scores = sat_scores[sat_scores['sat_writing'] == sat_scores['sat_writing'].median()] | Selecting rows from the 'sat_scores' DataFrame where the 'sat_writing' column value equals the median value of the 'sat_writing' column. |
| df['address'].count() / len(df['address'].notna()) * 100 | Calculating the percentage of non-null values in the 'address' column of the DataFrame. |
|  | or operator |
|[0:10] or head 10 |Top 10 items|
|result = draft.contents.str.split('\W+', expand=True).stack().value_counts().reset_index()||
|.diff()||
|df[df['diff'] <= pd.Timedelta(days=7)]||
|df = df.rename(columns = {'username': 'num_unique_users'})| renaming column|
|energy = pd.concat([fb_eu_energy, fb_asia_energy, fb_na_energy])| when one or more data frames have the same no of columns and datatypes|
|df = titanic.pivot_table(index = 'survived', columns = 'pclass', values = 'passengerid', aggfunc = 'nunique').reset_index()|pivot table|
|df1['year'] = df1['inspection_date'].dt.year|isolate the year from the date column|
|premium['seven_days_later'] = premium.entry_date + pd.Timedelta(days=7)||
|yelp_business['category'] = yelp_business['categories'].str.split(';')||
|yelp_business = yelp_business.explode('category')||
|.iloc[1]||
|.to_frame('user_count')||
|result.loc['open']||
|df1['day'] = df1['timestamp'].dt.date||
### HARD
| Function | Description |
|----------|-------------|
|||
