# SALES INSIGHTS PROJECT
- [PROBLEM STATEMENT](#problem-statement)
- [PROJECT PLANNING AND APPROACH](#project-planning-and-approach)
- [MY APPROACH FOR THIS PROJECT](#my-approach-for-this-project)
- [DASHBOARD](https://public.tableau.com/views/SalesInsightsDashboard2/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link)
## PROBLEM STATEMENT
AtliQ Hardware is a company and it's a company which supplies the hardware peripherals to different clients such as Normad stores, Excel stores, Surge stores. These are all the clients and this is a hardware company which will supply computers other peripheral networking equipment to them. 
Company have a head office in Delhi India and it has regional offices in different states of India and Bhavin Patel is a sales director of this company and he's managing the business from the head office and company has regional managers per state or per region or district.


![a](https://user-images.githubusercontent.com/67784234/122781289-46a0bd00-d2cd-11eb-9f0e-ddf9ba7ecb46.png)

What's happening with this company is the sales are declining for this company and Bhavin Patel as a sales director is having a lot of struggle tracking where the business is failing because when the business is smaller let's say you're 10 employee’s small business you can manage but when your business is bigger and you have multiple offices it's hard to manage actually you don't get a right picture and that's when data analysis can help you. 
So for Bhavin Patel when he talks with the regional managers or regarding the business in their areas the managers have a tendency to paint a rosy picture so sometimes they don't lie but they put sugar coating around the facts and as a sales director Bhavin Patel doesn't have any idea on what is actually happen at a ground level, he doesn't have data insights so that's the challenge that he goes through and when he calls this regional managers they will give him this big excel files and these excel files as humans we're not good at consuming so many numbers you know we want simple insights so he's frustrated because these managers are giving him so many excel files and he's like why the hell you're giving me 69 excel files.

## PROJECT PLANNING AND APPROACH
Here i have cover project planning and data discovery aspect of our sales insights data analysis project. Once sales directory of atliQ hardware has decided to invest in data analysis project he will do a meeting with IT director, data analytics team to come up with a plan. They will use AIMS grid to define purpose and success criteria of this project. 
Once AIMS grid is defined, next step is data discovery. In this step, data analyst team approaches IT team within an organization who owns software system that keep track of sales records. These records are stored in mysql database. Tableau can be plugged to this database to pull necessary information required for data analysis. I also discuss ETL, OLTP, OLAP and data warehouse concepts. Many times we need separate data warehouse or OLAP system to run our data analytics queries but in my project i will directly use mysql database.

![b](https://user-images.githubusercontent.com/67784234/122781818-cf1f5d80-d2cd-11eb-98c1-f81cecde396c.png)

## MY APPROACH FOR THIS PROJECT:

![c](https://user-images.githubusercontent.com/67784234/122782339-45bc5b00-d2ce-11eb-8943-9f0eb59adaba.png)

***Step1:*** Uploading dump.sql(sales data) file in mysql workbench and then analyzing the sales data using some sql queries
             .\
             \
             - [Database](db_dump.sql)
             \
             - [Data Analysis](https://github.com/Abhishekkr26/Sales-Insights-Project/blob/14bd4df1b052fdb74178260c4d842869b344656b/Data%20analysis.sql)
			    :
             1.	In transactions table , column sales amont contain some negative or zero values , acccording to me it will be a system error when filling the data so i have                     filter out those values and applied filter that sales amount should be at least 1 rupees
                  .
                  \
                  `data > edit source filter > add sales amount > at least 1`
             \
             \
             2.	AtliQ hardware has only business in India but in market column there is two market name New york & Paris so it will be a error so i have removed these two                       market name by their market code Mark097, Mark999
                  .
                  \
                  `Data > edit source filter > add market code > uncheck Mark097, Mark999` 
              \
              \
             3.	Cureency column contain transaction in INR as well as USD so i have converted all USD to INR and create a seperate calculated field named as Normalized Amount                   which will contain all sales amount in INR by using IF formula.
                  \
                  `IF [Currency] == 'USD' 
                  THEN [Sales Amount]* 74
                  ELSE [Sales Amount] 
                  END`

***Step3:*** Creation of dashboard
                  \
                  \
                  ![Dashboard](https://user-images.githubusercontent.com/67784234/122873323-3df0cb00-d34f-11eb-9e96-e7ccc43f8002.png)
