# Maji-Ndogo-From-analysis-to-action-SQL-

## Introduction
In this project I embarked on an expedition into the heart of Maji Ndogo's (a hypothetical country) vast data landscape. With a database comprising of 60,000 records meticulously collected by our devoted team of engineers, field workers, scientists, and analysts, where my mission was to use SQL to uncover actionable insights to drive informed decision making. 
I unraveled the story behind the numbers, exploring how SQL can be used to make sense of raw data. I uncovered patterns, extracted key information, and transformed this immense data trove into actionable insights.
 I loaded the database in MySQL Workbench and acquaint myself with it. I delved deep, explored its structure, understood the variables and how they were realated to each other.
 ## About The data
 ## Get to know the data
 Before I do anything else, let me introduce you to the data. I will load up the database and pull up the first few records from each table. It's like getting to know a new city I need to help you explore the lay of the land before we can start our journey.
 ## Dive into the water sources
 We've got a whole table dedicated to the types of water sources in our database. This table focuses on all the unique types of water sources we're dealing with.
 ## Unpack the visits to water sources
 The 'visits' table in our database is a record of all the trips made to different water sources. This table will help us to understand the frequency and distribution of these visits. We will be able to identify which locations -- have been visited more than a certain number of times.
 ## Assess the quality of water sources
 The quality of water sources is a vital table. We'll turn to the water_quality table to find records where the subjective_quality_score is within a certain range and the visit_count is above a certain threshold. This should help us spot the water sources that are frequently visited and have a decent quality score.
 ## Investigate any pollution issues
 We can't overlook the pollution status of our water sources. This table will help us to find those water sources where the pollution_tests result came back as 'dirty' or 'biologically contaminated'. This will help us flag the areas that need immediate attention.
 ## Note
 A data dictionary table has been embedded into the database. If you query the data_dictionary table, an explanation of each column is given there.

*IN [1]:* 

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/42196913-1825-4dd8-ba39-c67c617e2078)

*49 rows affected*

*OUT [1]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/d8b0b5cf-82d6-419f-a8e7-d19c42dfce3c)

Truncated to displaylimit of 10.

*We need to understand the various locations within Maji Ndogo by running this query.*

*IN [2]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/a26b3075-b91b-4f00-92d6-7a1f6766bb90)

*50 rows affected.*

*OUT [2]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/32d85067-6a14-42f3-b9e6-8f767b0d3ae6)

*Truncated to displaylimit of 10.*

*We need to understand the visits to ech water source within Maji Ndogo by running this query.*

*IN [3]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/785c50a0-e4fb-4cde-b059-1507de2cdc3e)

*50 rows affected.*

*OUT [3]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/a329a4a2-1275-4055-9a59-d8148b98d82c)

*Truncated to displaylimit of 10.*

*We need to retrieve the number of people served by each water source by running this query.*

*IN [4]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/99a899d8-9d59-4c09-94bf-0b38e61649ef)

*OUT [4]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/3108d557-749b-4e93-bdcf-9ce8f12c11ff)

Truncated to displaylimit of 10.

*We need to understand the various water sources within Maji Ndogo by running this query.*

*IN [5]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/ea4e4b18-7e96-414b-ba7c-0c5aa1ee4f91)

*5 rows affected.*

*OUT [5]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/45008908-ffe1-41f3-a1a5-4e3025475d0e)


**Type_of_water_source** 1- tap_in_home 2- tap_in_home_broken 3- well 4- shared_tap 5- river -- Let me quickly bring you up to speed on these water source types:

**1. River** - People collect drinking water along a river. This is an open water source that millions of people use in Maji Ndogo. Water from a river has a high risk of being contaminated with biological and other pollutants, so it is the worst source of water possible.

**2. Well** - These sources draw water from underground sources, and are commonly shared by communities. Since these are closed water sources, contamination is much less likely compared to a river. Unfortunately, due to the aging infrastructure and the corruption of officials in the past, many of our wells are not clean.

**3. Shared tap** - This is a tap in a public area shared by communities

**4. Tap in home** - These are taps that are inside the homes of our citizens. On average about 6 people live together in Maji Ndogo, so each of these taps serves about 6 people.

**5. Broken tap in home** - These are taps that have been installed in a citizen’s home, but the infrastructure connected to that tap is not functional. This can be due to burst pipes, broken pumps or water treatment plants that are not working.

**Note**
An important note on the home taps: About 6-10 million people have running water installed in their homes in Maji Ndogo, including broken taps. If we were to document this, we would have a row of data for each home, so that one record is one tap. That means our database would contain about 1 million rows of data, which may slow our systems down. For now, the surveyors combined the data of many households together into a single record.

For example, the first record, AkHa00000224 is for a tap_in_home that serves 956 people. What this means is that the records of about 160 homes nearby were combined into one record, with an average of 6 people living in each house 160 x 6 ≈ 956. So 1 tap_in_home or tap_in_home_broken record actually refers to multiple households, with the sum of the people living in these homes equal to number_of_people_served.

 *I had to write an SQL query that retrieves all records from this table where the time_in_queue is more than some crazy time,-- say 500 min. How would it feel to queue 8 hours for water?*

*IN [6]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/a65c1ea7-33ba-486b-a09b-b9e2624a47db)

*105 rows affected.*

*OUT [6]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/b39a3d52-3ec8-46a4-9b12-13aea0b9705a)

*Truncated to displaylimit of 10.*

> I am wondering what type of water sources take this long to queue for. 
> We will have to find that information in another table that lists the types of water sources.
> If I remember correctly, the table has type_of_water_source, and a source_id column.
> So let's write down a couple of these source_id values from our results, and search for them in the other table.
      #AkKi00881224
      #SoRu37635224
      #SoRu36096224
>If we just select the first couple of records of the visits table without a WHERE filter,
>we can see that some of these rows also have 0
>mins queue time. So let's write down one or two of these too

*IN [7]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/0f951d52-fce7-40c3-88de-6ad0b05d2dd1)

*5 rows affected.*

*OUT [7]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/f3cc354b-cb7d-49ef-8316-aeca128a6fb4)

> We need to assess the quality of water sources:
> The quality of our water sources is the whole point of this survey.
> We have a table that contains a quality score for each visit made about a water source that was assigned by a Field surveyor.
> They assigned a score to each source from 1, being terrible, to 10 for a good, clean water source in a home. Shared taps are not rated as high,
and the score also depends on how long the queue times are.

>Let's check if this is true. 
>The surveyors only made multiple visits to shared taps and did not revisit other types of water sources.
>So there should be no records of second visits to locations where there are good water sources, like taps in homes.

>So I will write a query to find records where the subject_quality_score is 10 -- only looking for home taps -- and where the source was visited a second time. What will this tell us?

*IN [8]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/e04d7f79-80e9-42e9-8163-e5bf44c4e77b)

> I get 218 rows of data. But this should not be happening!
> I think some of our employees may have made mistakes. 
> To be honest, I'll be surprised if there are no errors in our data at this scale! 

*218 rows affected.*

*OUT [8]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/9fca586d-aeb9-453b-8866-e4baa55d7301)

*Truncated to displaylimit of 10.*

> We need to investigate pollution issues:
> Did you notice that we recorded contamination/pollution data for all of the well sources?
> Find the right table and print the first few rows.

*IN [9]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/860d8167-dd1d-4fc7-88c1-1115d4b9e70d)

*10 rows affected.*

*OUT [9]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/f114a580-21b3-47d5-b9c9-0e3a1f4fabdf)

*Truncated to displaylimit of 10.*

**Water Quality Integrity Check**

> It looks like our scientists diligently recorded the water quality of all the wells. Some are contaminated with biological contaminants, -- while others are polluted with an excess of heavy metals and other pollutants. Based on the results, each well was classified as Clean, -- Contaminated: Biological or Contaminated: Chemical. It is important to know this because wells that are polluted with bio- or -- other contaminants are not safe to drink.

> It looks like they recorded the source_id of each test, so we can link it to a source, at some -- place in Maji Ndogo. -- In the well pollution table, the descriptions are notes taken by our scientists as text, so it will be challenging to process it.

>  The -- biological column is in units of CFU/mL, so it measures how much contamination is in the water. 0 is clean, and anything more than -- 0.01 is contaminated. -- Let's check the integrity of the data. The worst case is if we have contamination, but we think we don't. People can get sick, so we -- need to make sure there are no errors here.

*-- So, I wrote a query that checks if the results is Clean but the biological column is > 0.01.*

*IN [10]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/7a15f43e-7ec2-457c-a046-c7ba69e1f424)

-- If we compare the results of this query to the entire table,
-- it seems like we have some inconsistencies in how the well statuses are
-- recorded. Specifically, it seems that some data input personnel 
-- might have mistaken the description field for determining the cleanliness of the water.

*50 rows affected.*

*OUT [10]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/f871431a-00b5-48d9-932e-f0ca3deb23ea)

*Truncated to displaylimit of 10.*

**Biological Contamination Data Integrity Analysis**

-- It seems like, in some cases, if the description field begins with the word “Clean”, the results have been classified as “Clean” in the results column, even though the biological column is > 0.01

-- When we work with real-world data we may find inconsistencies due to data being misinterpreted based on a description rather than its actual values. Let’s dive deeper into the cause of the issue with the biological contamination data.

-- Vuyisile has told me that the descriptions should only have the word “Clean” if there is no biological contamination (and no chemical pollutants). Some data personnel must have copied the data from the scientist's notes into our database incorrectly. We need to find and remove the “Clean” part from all the descriptions that do have a biological contamination so this mistake is not made again.

-- The second issue has arisen from this error, but it is much more problematic. Some of the field surveyors have marked wells as Clean in the results column because the description had the word “Clean” in it, even though they have a biological contamination. So we need to find all the results that have a value greater than 0.01 in the biological column and have been set to Clean in the results column.

-- First, let's look at the descriptions. We need to identify the records that mistakenly have the word Clean in the description. However, it is important to remember that not all of our field surveyors used the description to set the results – some checked the actual data

-- To find these descriptions, search for the word Clean with additional characters after it. 
-- As this is what separates incorrect descriptions from the records that should have "Clean".

*IN [11]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/28fc7c4a-2aba-4bd9-bd54-eba9a75ccbf6)

-- The query should return 38 wrong descriptions.

*38 rows affected.*

*OUT [11]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/319c9b54-8f91-448e-9203-8380cde86b0a)

*Truncated to displaylimit of 10.*

-- Now we need to fix these descriptions so that we don’t encounter this issue again in the future.

-- Looking at the results we can see two different descriptions that we need to fix:
-- 1. All records that mistakenly have Clean Bacteria: E. coli should updated to Bacteria: E. coli
-- 2. All records that mistakenly have Clean Bacteria: Giardia Lamblia should updated to Bacteria: Giardia Lamblia

-- The second issue we need to fix is in our results column.
-- We need to update the results column from Clean to Contaminated: Biological 
-- where the biological column has a value greater than 0.01.

*IN [12]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/f066e54f-ebc9-4680-b250-23c027fae80f)

*38 rows affected.*

*OUT [12]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/d3d8984e-016a-4ae7-b4d2-151fed593b3f)

*Truncated to displaylimit of 10.*

**Ok, so here is how I did it:**
-- Case 1a: Update descriptions that mistakenly mention -- Clean Bacteria: E. coli to Bacteria: E. coli -- Case 1b: Update the descriptions that mistakenly mention -- Clean Bacteria: Giardia Lamblia to Bacteria: Giardia Lamblia -- Case 2: Update theresulttoContaminated: Biologicalwhere --biologicalis greater than 0.01 plus current results isClean`

*IN [13]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/9657cfad-5317-4ccc-9ce3-c204fbe42975)

*26 rows affected.*
*12 rows affected.*
*64 rows affected.*

-- Put a test query here to make sure we fixed the errors.
-- Use the query we used to show all of the erroneous rows

*IN [14]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/c3e4fca8-351c-4eaf-ac57-9580efedbdce)

*OUT [14]:*

![image](https://github.com/simonrimui5/Maji-Ndogo-From-analysis-to-action-SQL-/assets/155226875/08df0566-93f0-418d-983e-4ab4ccf95102)

**Conclusion**

In the final stretches of our data expedition in Maji Ndogo, significant strides were taken to fortify the integrity of water quality records. Let's delve into the additional analyses conducted and their impactful outcomes:

**1. Correcting Clean Bacteria: Giardia Lamblia Records:**

Building on our commitment to precision, records erroneously labeled "Clean Bacteria: Giardia Lamblia" underwent meticulous correction. Leveraging the prowess of SQL, these records were accurately updated to reflect "Bacteria: Giardia Lamblia," ensuring an unambiguous portrayal of water quality data.

**2. Elevating Contaminated: Biological Results:**

To bolster the accuracy of our biological contamination data, a strategic update was executed. All instances where the Biological column surpassed the threshold of 0.01 now bear the label "Contaminated: Biological." This enhancement not only refines the categorization but also underscores our dedication to presenting nuanced, actionable insights.

**3. Biological Contamination Data Integrity Analysis:**

A comprehensive analysis was conducted, scrutinizing the Biological column to pinpoint values surpassing the defined threshold. This rigorous examination not only facilitated targeted updates but also laid the groundwork for future data quality protocols, ensuring the ongoing reliability of Maji Ndogo's water quality dataset.

**4. Water Quality Integrity Check:**

The entire water quality dataset underwent a meticulous integrity check. Beyond individual corrections, this holistic evaluation aimed at verifying the coherence of the entire dataset. The outcome is a robust and reliable foundation upon which stakeholders can base critical decisions with confidence.

As we conclude this chapter, Maji Ndogo's water quality dataset stands fortified, reflecting not just the correction of anomalies but a commitment to the continuous enhancement of data integrity. Here's to a future marked by precision, reliability, and informed decision-making in our virtual nation. 





















 

 

 
 












