# PowerBi_dashboard_project
This is power bi end to end Project 
Like this project! 

                                                                            EASY QUESTION

 Q1.Who is the senior most employee based on job title?
                                                                                                   
 Select * from customer2;
SELECT title, last_name, first_name 
FROM employee
ORDER BY levels DESC
LIMIT 1;

Q2. Which countries have the most Invoices?

 select * from invoice2;
SELECT COUNT(billing_country ) AS c, billing_country 
FROM invoice2
GROUP BY billing_country
ORDER BY c DESC;

Q3. What are top 3 values of total invoice?

 SELECT total 
FROM invoice2
ORDER BY total DESC
limit 3;


Q4.Which city has the best customers? We would like to throw a promotional Music Festival in the city we made the most money.
 Write a query that returns one city that has the highest sum of invoice totals. Return both the city name & sum of all invoice totals 

SELECT billing_city,SUM(total) AS Invoice2Total
FROM invoice2
GROUP BY billing_city
ORDER BY Invoice2Total DESC
LIMIT 1;

Q5.Who is the best customer? The customer who has spent the most money will be declared the best customer. 
Write a query that returns the person who has spent the most money

 SELECT customer2.customer_id, first_name, last_name, SUM(total) AS total_spending
FROM customer2
JOIN invoice2 ON customer2.customer_id = invoice2.customer_id
GROUP BY customer2.customer_id , first_name,last_name
ORDER BY total_spending DESC
LIMIT 1;

                                                                                                MODERATE QUESTION       


                                                                                     
Q1.Write query to return the email, first name, last name, & Genre of all Rock Music listeners. Return your list ordered alphabetically by email starting with A.

SELECT DISTINCT C.first_name, C.last_name, C.email, (G.name)genre_name
FROM customer C
INNER JOIN invoice I
ON C.customer_id = I.customer_id
INNER JOIN invoice_line IL
ON I.invoice_id = IL.invoice_id
INNER JOIN track T
ON IL.track_id = T.track_id
INNER JOIN genre G
ON T.genre_id = G.genre_id
WHERE G.name = 'Rock'
ORDER BY C.email;


  Q2. Let's invite the artists who have written the most rock music in our dataset. Write a query that returns the Artist name and total track count of the 
 top 10 rock bands.

select artist.name,count(artist.artist_id) as number_of_songs
from track2 . track2 join genre gen
on track2.genre_id = genre.genre_id
join album album on album.album_id = track2.album_id
join artist artist on artist.artist_id = album.artist_id
where genre.name like 'Rock'
group by artist.artist_id 
order by number_of_songs desc limit 10;


Q3.Return all the track names that have a song length longer than the average song length. Return the Name and Milliseconds for each track. Order by the song length with the longest songs listed first.

SELECT name, milliseconds
FROM track2
WHERE milliseconds > (SELECT AVG(milliseconds) FROM track2)
ORDER BY milliseconds DESC;













