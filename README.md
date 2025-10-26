# Disney
Database Model and system for Disney

Team Members Mahathi - https://github.com/mrb74060/Disney.git Morgan - https://github.com/morganlemmings Clark - https://github.com/clarkfarrell2/Disney Melissa - https://github.com/melissatran0

Problem Description

The objective of this project is to design and build a relational database that models the core operations of Disney. The two primary entities in our model are the Park entity, representing the physical locations of Disney World, and the Movie entity.

The Park entity connects to multiple related components: employees who manage and operate the park, various attractions, Disney-themed stores, and customers who visit the park. Meanwhile, the Movie entity includes details about characters, actors, merchandise, and the casting process.

This database aims to accurately represent these relationships and generate meaningful sample data, supporting Disney’s goals of running its parks efficiently and effectively. Additionally, the movie division is modeled to maximize profit, foster franchise growth, and improve cross-division coordination. A link between the movie and park entities illustrates how movies influence physical elements—such as themed merchandise—sold in Disney stores.

Data Model Explanation

Our data model is structured around Disney’s two most significant revenue streams—its movies and theme parks—which have been at the heart of the company since its inception.

The first entity designed was the Movie entity, containing general details such as title, release date, and genre. Many characters can appear in multiple movies, such as sequels or crossovers, creating a many-to-many relationship. To represent this, we introduced an associative entity called Appearance, linking characters to the movies they appear in.

Characters are voiced by Actors, forming a one-to-many, non-identifying relationship between Actor and Character. The modality for Actor is 1 since we only consider characters with speaking roles. Additionally, since many Disney films include live-action performances, a Casting associative entity was created to link Movies and Actors, recording which actors appear in which films.

Merchandise is another key part of Disney’s business. Each item may or may not be tied to a movie, so we established a non-identifying one-to-many relationship between Movie and Merchandise. Merchandise is sold through Disney stores, which are distributed across different parks. To represent this, we modeled a one-to-many relationship between Store and Merchandise.

Because each store maintains its own inventory, an Inventory table was added to track details such as stock quantity, unit cost, and selling price. A one-to-many relationship from Store to Inventory was used to capture store-specific stock data.

The Park entity holds details about each Disney park, including location and opening date (e.g., Magic Kingdom, Epcot, Animal Kingdom). Each park has multiple stores and attractions, represented by one-to-many relationships between Park–Store and Park–Attraction. The Attraction entity stores information such as attraction name, type, and area within the park.

Parks are staffed by Employees, who are assumed to work within a single park for consistency and efficiency. Therefore, Park has a one-to-many relationship with Employee, and the Employee entity includes data such as name, title, and tenure.

Customers visiting Disney World are represented by the Customer entity. Since many customers buy multiple merchandise items during their visit, we created an associative entity called Purchase to record these transactions. Customer visits are tracked in the Visit entity, forming a one-to-many relationship between Customer and Visit. Lastly, because Disney values customer loyalty and engagement, each customer’s favorite park is stored through a one-to-many relationship between Customer and Park.

Data Dictionary

<img width="875" height="393" alt="image" src="https://github.com/user-attachments/assets/d95d8428-ccc5-4918-a5c0-d6a59657bb0d" />
<img width="908" height="515" alt="image" src="https://github.com/user-attachments/assets/af1e8764-cabd-4f2a-86d3-0ef6bae2ace4" />
<img width="898" height="345" alt="image" src="https://github.com/user-attachments/assets/93a625e2-cdfb-45c6-bf4b-919aabc3d4be" />
<img width="951" height="452" alt="image" src="https://github.com/user-attachments/assets/14a26bba-6b25-41aa-b709-3151f10dcb24" />
<img width="947" height="602" alt="image" src="https://github.com/user-attachments/assets/5a6db26d-7d07-487a-9fcd-3cb92fcf45ff" />
<img width="991" height="638" alt="image" src="https://github.com/user-attachments/assets/c351743d-5aaa-4594-b689-37b27927c562" />
<img width="902" height="403" alt="image" src="https://github.com/user-attachments/assets/ff7aa0d3-3fc0-4405-9195-217f8f93a52a" />
<img width="892" height="592" alt="image" src="https://github.com/user-attachments/assets/581dd8f6-6e56-43f7-9cd8-dc3af3e22c54" />
<img width="877" height="251" alt="image" src="https://github.com/user-attachments/assets/dfd19439-80cc-41ab-a8f9-d81986a9e184" />
<img width="876" height="237" alt="image" src="https://github.com/user-attachments/assets/1b77ce8a-4c9b-44ea-a825-be9fc83a7182" />
<img width="906" height="277" alt="image" src="https://github.com/user-attachments/assets/8c025f51-fe84-4a94-98d4-a7f83dd6890b" />
<img width="937" height="397" alt="image" src="https://github.com/user-attachments/assets/621255e5-3742-4523-97ed-cc941acefa62" />
<img width="931" height="585" alt="image" src="https://github.com/user-attachments/assets/8672d291-d207-4c0b-91cc-89f7307d169d" />
<img width="931" height="452" alt="image" src="https://github.com/user-attachments/assets/e53d9f08-c2cf-4dd5-bd2c-83c7e75aaeac" />




Queries and Explanations
<img width="1011" height="371" alt="image" src="https://github.com/user-attachments/assets/f135932a-f4c5-41d8-b3de-4260f3ca7440" />

Query 1

Retrieves movieID and movieTitle for all movies that have no corresponding entry in the Merchandise table. It uses a NOT EXISTS subquery to identify movies without related merchandise records.

Purpose:
This query helps management identify movies that have not yet been monetized through merchandise sales. Merchandise is a major revenue source for Disney, and recognizing these untapped titles allows marketing and product development teams to create new merchandise lines, maximizing profitability and expanding the brand’s reach.

Query 2

Retrieves each park’s location and opening date, ordering the results in descending order by opening date (newest to oldest).

Purpose:
This query helps managers and analysts quickly assess the timeline of Disney park openings. Understanding when each park was established provides insights into expansion strategies and helps evaluate performance differences between newer and older parks. It also assists in planning maintenance schedules, renovations, and anniversary events.

Query 3

Selects all movies released after January 1, 2020, where the box office revenue exceeds the average revenue across all movies. The results are sorted in descending order by box office performance.

Purpose:
This query identifies recent movies that have performed above average at the box office, highlighting current trends in audience preferences. Sorting by revenue allows managers to quickly pinpoint the strongest performers, informing future investment decisions, marketing strategies, and franchise development.

Query 4

Retrieves the first and last names of customers, along with their favorite park location, specifically filtering for customers whose favorite park is Epcot.

Purpose:
By identifying customers who prefer Epcot, Disney can create targeted marketing campaigns and personalized offers. This enables managers to send Epcot-specific promotions, such as discounts or event invitations, directly to those most likely to be interested—improving engagement, satisfaction, and repeat visitation.

Query 5

Calculates merchandise revenue per park, joining Purchase, Merchandise, Store, and Park. It filters for purchases made on or after January 1, 2023, and merchandise priced at $25 or higher. For each park, it sums total revenue and unit sales, ordering results by total revenue descending.

Purpose:
This query provides a comprehensive view of merchandise performance across all parks. Focusing on recent, high-value transactions helps management identify which parks generate the most revenue and where to allocate marketing, inventory, and operational resources for maximum profitability.

Query 6

Calculates total merchandise revenue by movie release year, joining Movie, Merchandise, and Purchase. It groups results by the movie’s release year and sums all merchandise sales, ordering results from earliest to most recent.

Purpose:
This query allows Disney to track merchandise revenue by movie release year, revealing which film cohorts continue to generate significant sales. The insights support trend analysis, profitability tracking, and long-term strategic planning around franchise growth and product development.

Query 7

Identifies customers who have not made any purchases since January 1, 2008, using a WHERE NOT EXISTS subquery to find customers lacking purchase records after that date.

Purpose:
This query flags inactive customers who may benefit from re-engagement efforts. Managers can use this information to send targeted promotions, loyalty rewards, or personalized offers aimed at bringing back lapsed customers. It also helps analyze long-term churn and customer retention patterns.

Query 8

Retrieves customer information along with details about family rides at their favorite parks. It joins Customer, Visit, Park, and Attraction, calculates visit durations, and filters for customers whose visits exceed the average duration. Only customers whose favorite park is Magic Kingdom or Hollywood Studios are included. Results are ordered by visit duration descending.

Purpose:
This query highlights the most engaged customers—those who spend longer than average at the parks—and shows which family rides are most relevant to them. Disney can use this insight to tailor promotions, enhance attractions, and improve the visitor experience for high-value customers.

Query 9

Calculates the average, highest, lowest, and total number of movies per genre, focusing on Action, Adventure, and Fantasy films released after 2010. A subquery filters for genres whose average box office exceeds the overall average across all movies.

Purpose:
This query identifies the most consistently successful modern genres. By analyzing performance metrics across genres, executives can determine which categories yield the highest returns, helping guide production budgets, marketing priorities, and future film development strategies.

Query 10

Joins Movie, Casting, and Actor to connect actors with their movies. It groups results by actor, calculating the total number of movies and the highest box office revenue among them. The HAVING clause filters for actors who have appeared in at least three movies and in at least one above-average box office film.

Purpose:
This query identifies actors who demonstrate both experience and commercial appeal. It helps producers and casting directors pinpoint proven, high-performing talent—those with consistent involvement in successful films. These insights reduce casting risks and support strategic talent decisions for upcoming projects.
