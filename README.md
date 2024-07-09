# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [2_skills_count](Project/2_skills_count.ipynb).


fig, ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style='ticks')
for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short']==job_title].head(5)
    # df_plot.plot(kind='barh', x='job_skills', y='skill_percent', ax=ax[i], title = job_title, legend=False)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r', legend=False)
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_xlim(0,78)

    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')

    if i!= len(job_titles) -1:
        ax[i].set_xticks([])

fig.suptitle('Likelihood of skills requested in Job Postings', fontsize=15)
fig.tight_layout(h_pad=0.5)
plt.show()

### Results 

[Visualization of Top Skills for Data Nerds](Project/images/skill_demand_Canada.png)

### Insights

Data Analyst:

Core Skills:
SQL: Dominates the requirements, showing that database management and querying are critical (52%).
Excel: Remains a fundamental tool for data manipulation and analysis (32%).
Python: Equally important as Excel, indicating a need for programming skills for data analysis and automation (32%).
Tableau: Significant for data visualization and reporting (25%).
Power BI: Also important for creating interactive dashboards and visualizations (21%).

Data Engineer:
Core Skills:
SQL: Essential for managing and querying large datasets (65%).
Python: Highly valued for its versatility in scripting and data processing (61%).
Azure: Important for cloud-based solutions and services (38%).
AWS: Critical for working with Amazon's cloud platform (35%).
Spark: Necessary for big data processing and analytics (33%).

Senior Data Engineer:
Core Skills:
SQL: Equally critical as for Data Engineers, highlighting its importance across experience levels (67%).
Python: Matches SQL in importance, underscoring the need for advanced programming skills (67%).
AWS: More emphasized compared to Data Engineers, reflecting the need for expertise in cloud infrastructure (45%).
Spark: Continues to be significant for big data technologies (41%).
Azure: Remains relevant for cloud solutions (36%).

Overall Observations:
SQL and Python: Universally critical across all roles, indicating a fundamental need for these skills in data-related positions.
Cloud Technologies (AWS and Azure): Increasingly important, especially for Data Engineers and Senior Data Engineers, reflecting the industry's shift towards cloud computing.
Big Data Tools (Spark): Significant for handling and processing large-scale data, particularly for engineering roles.
Visualization Tools (Tableau and Power BI): Important for Data Analysts to transform data into actionable insights through visualizations.