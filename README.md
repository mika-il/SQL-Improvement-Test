# SQL-Improvement-Test
1. Purpose: These are a SQL query that produces a search result. The query produces results in approximately 8 seconds.
2. Task: Please suggest what improvements should be done to the query in order to improve its performance.

# Improvements
1. Index All Columns Used in where, group by and order by Clauses.
we can just add an index to each table using the below command:
<br /><br />Table jobs: <code>ADD INDEX `jobs_index` (`publish_status`, `deleted`, `sort_order`)</code><br /> 
Table job_categories: <code>ADD INDEX `job_categories_index` (`deleted`)</code><br />
Table job_types:  <code>ADD INDEX `job_types_index` (`deleted`)</code><br />
Table affiliates:  <code>ADD INDEX `affiliates_index` (`type`, `deleted`)</code><br />
Table basic_abilities:  <code>ADD INDEX `basic_abilities_index` (`deleted`)</code><br />
Table personalities:  <code>ADD INDEX `personalities_index` (`deleted`)</code><br />
Table practical_skills:  <code>ADD INDEX `practical_skills_index` (`deleted`)</code><br /> 

2. Avoid Like Expressions (Wildcards Search) using Full-text Searches
To add a full-text search index to the column each table, we can use the below command:
<br /><br />Table jobs: <code>ADD FULLTEXT `jobs_ft_index` (`name`, `description`, `detail`, `business_skill`, `knowledge`, `location`, `activity`, `salary_statistic_group`, `salary_range_remarks`, `restriction`, `remarks`)</code><br /> 
Table job_categories: <code>ADD FULLTEXT `job_categories_ft_index` (`name`)</code><br />
Table job_types:  <code>ADD FULLTEXT `job_types_ft_index` (`name`)</code><br />
Table affiliates:  <code>ADD FULLTEXT `affiliates_ft_index` (`name`)</code><br />
Table basic_abilities:  <code>ADD FULLTEXT `basic_abilities_ft_index` (`name`)</code><br />
Table personalities:  <code>ADD FULLTEXT `personalities_ft_index` (`name`)</code><br />
Table practical_skills:  <code>ADD FULLTEXT `practical_skills_ft_index` (`name`)</code><br />

3. Optimize a lot of join table with Union Distinct
