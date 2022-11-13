---
theme: jekyll-theme-minimal
layout: default
title: "Netflix Top 10 (Web Development) "
permalink: /netflix-top-10/
---

# Netflix Top 10 - Choosing What To Watch Next (2022)

Built using: Python - Flask and BeautifulSoup, Javascript, HTML and hosted on <a href="https://netflix-top-10.onrender.com/"> Render </a>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

<p class="view"><a href="https://github.com/domteo95/netflix-top-10"><i class="fa fa-github" style="font-size:24px"></i>  View the Project on GitHub</a></p>

**Background**

Recently, Netflix began publicizing its global <a href="https://top10.netflix.com/united-states"> top 10 </a> most watched films or TV shows. This provides a list of content for people to watch yet besides the title, Netflix's website does not provide any more information on these films/shows that will help people decide if these films/shows are for them.

This website/program helps scrapes the top 10 lists from Netflix's website for the following countries:

| Countries covered in this program |
| --------------------------------- |
| Australia                         |
| Brazil                            |
| France                            |
| Hong Kong                         |
| India                             |
| Japan                             |
| Singapore                         |
| Taiwan                            |
| United States                     |
| United Kingdom                    |

Users can either select the country in the drop-down list or access the results directly via URL. There are 2 aspects to this program:

1. Web Scraping Netflix Top 10 data from Netflix's website.
2. Using the Netflix Top 10 data as input for the <a href="https://www.omdbapi.com"> OMDb API </a> to access the film/show's details as well as YouTube trailer.

The OMDb API and YouTube trailer will then be shown.

<img src="/assets/img/netflix-top-10.gif">

## Web Scraping the Netflix Top 10 data from Netflix's website

- I've created a Flask API that utilises BeautifulSoup to scrape Netflix's Top 10 <a href="https://top10.netflix.com/united-states"> website </a> to return the Top 10 shows and films for the country selected.

## Utilising OMDb API to get film/show's info and web scraping the YouTube trailer

- Loop through the web scrapped list of top 10 films and tv shows as input for a Flask API that utilises the OMDb API to return the show/film's IMDB rating (out of 10) and a short description of the film. <br><br>
- There will be cases where the film/show title does not match the OMDb API database and will hence return no results. I've tried to mitigate this through the following steps:

1. Oftentimes the title scrapped is too long (for titles with ":" e.g. 13 Hours: The Secret Soldiers of Benghazi) and the title in the OMDb database is its simplified version (e.g. 13 Hours) hence I will try to split the scrapped title on ":" and will use the first part of the title as input for the OMDb API again.
2. For TV shows, just search using the title without the season number.

- Then the Flask API will use the film title to web scrape the URL for the film trailer on YouTube which will then embedd it.

- Note: on Javascript, accessing the Flask API that loops through the web scrapped list means that it will return the results not in the Top 10 order but in the order in which the results are returned. Hence, I have created 10 unique ID divs for Films and another 10 unique ID divs for TV shows. Their ID contains their rank thus regardless of the order in which results are returned, they will populate the div that contains their rank.
