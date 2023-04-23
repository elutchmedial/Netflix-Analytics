# Netflix Analytics Project

This project analyzes the "netflix_titles_info" and "netflix_people" datasets, which contain information about movies and TV shows available on Netflix as of September 2021. The dataset includes 8807 records and 13 columns, such as the show ID, type, title, country, date added, release year, rating, duration, listed in, and description.

The goal of this project is to explore the dataset and answer some questions, such as the number of movies in the database, the most recent batch of TV shows and/or movies added, and the oldest movie in the database.

## Querying the Dataset

To extract the relevant information from the dataset, we used SQL queries. Here are some of the queries we ran:

```sql
SELECT 
people.show_id, people.director, titles.title, titles.type
FROM "CharlotteChaze/BreakIntoTech"."netflix_people" people
LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
ON people.show_id=titles.show_id ;
```

This query joins the "netflix_people" and "netflix_titles_info" tables to retrieve information about directors for each movie and TV show.

```sql
SELECT Count(*) FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" WHERE type = 'Movie';
```

This query calculates the number of movies in the database.

```sql
SELECT max(date(date_added)) from "CharlotteChaze/BreakIntoTech"."netflix_titles_info";
```

This query retrieves the date of the most recent batch of TV shows and/or movies added to the database.

```sql
SELECT (title) FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" ORDER BY title ASC;
```

This query lists all the movies and TV shows in alphabetical order.

```sql
SELECT director
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_people" people
ON titles.show_id=people.show_id
WHERE title= 'Bright Star';
```

This query retrieves the director of the movie "Bright Star".

```sql
SELECT title, release_year
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
WHERE type= 'Movie'
ORDER BY release_year asc LIMIT 1;
```

This query finds the oldest movie in the database and the year it was released.

## Results

Here are the answers to the questions we asked:

- Number of movies in the database: 6131
- Date of the most recent batch of TV shows and/or movies added: 2021-09-25
- List of all movies and TV shows in alphabetical order: see SQL query above
- Director of the movie "Bright Star": Jane Campion
- Oldest movie in the database and its release year: "Prelude to War" (1942)
