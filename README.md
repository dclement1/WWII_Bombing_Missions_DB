# WWII_Bombing_Missions_DB
This repository is a clone of a project I did for a Digital Humanities II class at the University of South Florida. 

# World War II Bombing Mission -- SQL Relational Database

This project is an attempt to create a relational database of the World War II bombing missions dataset. Some digital
humanities projects have already been done with this dataset; however none of them take advantage of the usefulness
of relational databases. Therefore, I believe the creation of this database will allow an increased ease of access, 
as well an increase in the ability of digital humanists to study this dataset in ways not previously possible.
    
# Background and Purpose

This dataset was completely new to me, and was found online while searching for historical datasets. 
This dataset was hosted on a website, www.kaggle.com , and was uploaded by the United States Air force. 
This dataset contains 178,282 missions by allied air forces during World War II. It contains over 43 columns 
of information, such as units associated with each mission, departure and target geographic coordinates, 
aircraft left, aircraft returned, aircraft damaged, as well as information on the amount and type of
ordinance which was dropped on the target.

This dataset has certainly been used by others in very interesting digital humanities projects. On Kaggle, the 
website allows people to post about and share projects where they used the dataset. One of the projects which 
stood out to me was done by Kevin Mader, and uses a programming language entitled "R" to process the data, and 
produce various maps of the bombing missions. One very interesting series of maps produced shows the progression 
of missions over time. This can be seen below.
[Credits: Kevin Mader; https://www.kaggle.com/kmader/maps-of-ww2-bombings/notebook](imgs/included/Kevin_Mader_WWII_Bombing_Maps.JPG)

Another project, which was done by Shane Smith is entitled "Did Bombing Operations Change on D-Day?". This used 
Python to process and analyze the WWII bombing dataset. In this project, Smith was able to identify various trends
in the bombing missions that took place during D-Day. This project is available here: 
[https://www.kaggle.com/smid80/did-bombing-operations-change-on-d-day-no-maps](https://www.kaggle.com/smid80/did-bombing-operations-change-on-d-day-no-maps)

The last project that deals with the WWII bombing dataset, was done by "cswingle", and is entitled "Preliminary look
at the data". This project uses the same R language used in the mapping project discussed earlier. In this project, 
the data is analyzed statistically, and some interesting trends are visible. This project is available at the following 
address: [https://www.kaggle.com/cswingle/preliminary-look-at-the-data](https://www.kaggle.com/cswingle/preliminary-look-at-the-data)

These projects would show me the potential that this dataset contains, and would motivate me to create something useful  from it. Based on my observations, all of the projects done on this dataset so far, have only ever used the raw  spreadsheet version. With the goal of our Digital Humanities II class being the creation of a database, I could see 
how doing this could lead to increase access and dissemination, as well as an increase in research on the dataset. In 
the future, I believe that if the database produced in this project can be fine-tuned and tweaked, a very useful, 
historical dataset will be more easily and readily available for researchers.

# Roadblocks
   
This dataset is fairly large and cumbersome to work with, however, luckily it was already decent in terms of formatting and     standardization. This topic is one which is very important in digital humanities, as inconsistencies in a dataset can lead to major    
issues and headaches in the future. One example of this could be for instance, if you had one column which listed what country each     mission was flown from, and some entries had "France" and some others said "france" or "FR". This will cause major issues, as when attempting to query the data and ask questions about it, you will not be receiving accurate counts as certain entries will be emitted.
    
One issue I did have with this dataset however, was incomplete data. Many columns had incomplete data, with a lot of missions having blank fields. This, while not a huge issue is still something you want to consider, when thinking about how your data can affect and altar your analysis and conclusions. Digital humanities techniques make use of technologies that allow researchers to perform monumental feats of data processing and analysis, with relatively little effort compared to in the past. However, there are also some pitfalls which can lead to issues if not careful.

# Design
    
To create a relational database, one must first develop some manner of categorizing the data such a manner where the different categories relate to each other in some fashion. These different categories are called tables, or models, and are at their essence, simply different groupings of columns from a spreadsheet.
    
Designing the database for this particular dataset initially seemed fairly straightforward, however required several attempts to fine tune and refine, before I was satisfied with it. Ultimately it was the design that proved the largest challenge with this project. The database would be created using a free program entitled, MySQL Workbench. This is a program which allows you to design a SQL database, graphically, rather than purely in code. This allows someone with only a rudimentary knowledge of SQL language to create and design database. The decision was made to make five main tables: Mission, Location, Target, Ordinance, Units. These five tables are joined together via intermediary tables which serve simply as place holders for ID numbers which relate each table to the other. In addition, the Ordinance table was related to the target table, so that it would be possible to query the database for things such as the amount of ordinance dropped on a particular target. Similar relations were formed between the Units table and the Ordinance table. in addition, the Mission table has had relationships connected to all of the other tables. An image of the graphical representation of the schema, as designed in MySQL Workbench is displayed below.
    
I have also created two views, which are a way of designing a query, and then saving it, so that in the future, you can simply use the view, as opposed to writing the entire code for the view.
The first view I created was a view which will display information about units and the ordinance they used at specific target locations. This would be useful if you wanted to quickly find out statistics about ordinance dropped on targets.
The second view I created produces the number of missions a specific unit went on. This could be used as reference in research on specific units. It could also be used as a way to realize new and interesting insights which would be difficult to gain through traditional humanities efforts.
    
[Final Version of the Schema](imgs/included/Scheema_Design3.png)
    
    
Also included is the MySQL Workbook file, which contains the schema design.
[Workbook file](files/WWII_Bombing_DB_Final.mwb).

# Next Steps
    
The database could be redesigned as there are a couple things which may be able to improve it. For instance, if we were to combine the target table and the Location table into one, We could then simply use a new field in the new table, called "Location_Type". This would then indicate if a location is a target or a departure location. After this, we could create a table entitled country and have a column in this table that is a Country_ID this would allow us to simply include "Country_ID" to any table which includes a country location and have that column relate to the country ID field in the country table. Doing this would allow us to ask questions about specific countries which is not possible in the current design, as every table that includes a country field, has a unique country column such as, Takeoff_Country, Target_Country, Country (Unit Table).
    
This project would also benefit from the addition of other complementary datasets. This could be, for instance, a dataset comprised of ground troop operations, with which one could compare and analyze various trends between aerial bombing and ground operations. Also, another logical next step in this project could be to host this database on a site, and allow academic researcher as well as the public to access, explore and analyze the dataset. This would fulfill the goal of the project, which is to increase access and awareness of this dataset, in order to promote new research on the subject.

# Project credits
    
* Daniel Clement - Project Management, Coding, Visualizations, and Analysis
    
* David J. Thomas - Coding and All around assistance.
                    This project would not have been possible with out his support,
                    expertise and guidance. 
    
* Students of HIS4936, Hacking History: Programming Digital Scholarship

    
