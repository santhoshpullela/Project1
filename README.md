

```python
# Import Dependencies
import pandas as pd
import numpy as np
import requests
from pprint import pprint
import matplotlib.pyplot as plt
import time

# Access key 
from config import api_key
```


```python
# Define API base url and targetted years of movies data
url1 = "https://api.themoviedb.org/3/discover/movie?"
year_data = [2007,2008,2009,2010,2011,2012,2013,2014,2015,2016,2017,2018]
```


```python
# We should call two different url's under this API to pull the full movie data information 
#     1. To Retrieve Movie ID list 
#     2. Using Movie ID list pull the important factors information that defines movie success like(Revenue, Budget..etc.)
# Calling below url to pull movie id information,Check for response and print the response whether the data is available or not
# Retrieving data for 12 years and 10 pages of information for each year. This API gives 20 results per page. 

movies_id_data = []
page_num = 1

for year in year_data:
    
    print("Retrieving Data for : " + str(year) )
    
    for page_num in range(1,11):
        response = requests.get(f"{url1}api_key={api_key}&primary_release_year={year}&page={page_num}")
        print(response.url)
        movies = response.json()
       #movies_data.append(response.json())
        page_num = page_num + 1
               
        for movie in movies['results']:
            movies_id_data.append(movie['id'])
            
# Sleep time to call each year data is 5 secs
    time.sleep(5)

```

    Retrieving Data for : 2007
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2007&page=10
    Retrieving Data for : 2008
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2008&page=10
    Retrieving Data for : 2009
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2009&page=10
    Retrieving Data for : 2010
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2010&page=10
    Retrieving Data for : 2011
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2011&page=10
    Retrieving Data for : 2012
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2012&page=10
    Retrieving Data for : 2013
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2013&page=10
    Retrieving Data for : 2014
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2014&page=10
    Retrieving Data for : 2015
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2015&page=10
    Retrieving Data for : 2016
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2016&page=10
    Retrieving Data for : 2017
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2017&page=10
    Retrieving Data for : 2018
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=1
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=2
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=3
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=4
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=5
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=6
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=7
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=8
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=9
    https://api.themoviedb.org/3/discover/movie?api_key=f63b434c2eae10c869016441dc039f7b&primary_release_year=2018&page=10
    


```python
#Total movie id list pulled from API
print(len(movies_id_data))
```

    2400
    


```python
# Using movie id list, retrieving full movie details from the TMDb API
url2 = "https://api.themoviedb.org/3/movie/"
movies_details = []

for mve_id in movies_id_data:
    
    response2 = requests.get(f"{url2}{mve_id}?api_key={api_key}")
    #print(response2.url)
    movies_details.append(response2.json())
        
#pprint(movies_details)
```


```python
# Pull the required data from the reponse received
movie_id1 = []
movie_title = []
budget = []
revenue = []
release_date = []
genre = []
production_comp = []
overview = []

def write_null(v1): 
         
    if v1 == movie_id1:
        movie_id1.append("NaN")
    if v1 == movie_title:
        movie_title.append("NaN")
    if v1 == budget:
        budget.append("NaN")
    if v1 == revenue:
        revenue.append("NaN")
    if v1 == genre:
        genre.append("NaN")
    if v1 == overview:
        overview.append("NaN")
    if v1 == production_comp:
        production_comp.append("NaN")
    if v1 == release_date:
        release_date.append("NaN")
       


for detail in movies_details:
      
    try:
        movie_id1.append(detail["id"])
    except:
        write_null(movie_id1)
    try:
        movie_title.append(detail["title"])
    except:
        write_null(movie_title)
    try:
        budget.append(detail["budget"])
    except:
        write_null(budget)
    try:
        revenue.append(detail["revenue"])
    except:
        write_null(revenue)
    try:
        genre.append(detail["genres"][0]["name"])
    except:
        write_null(genre)
    try:
        overview.append(detail["overview"])
    except:
        write_null(overview)  
    try:
        production_comp.append(detail["production_companies"][0]["name"])
    except:
        write_null(production_comp)
    try:
        release_date.append(detail["release_date"])
    except:
        write_null(release_date)

```


```python
# Check all data list have same lenght which will be used before creating dataframe
print(len(movie_id1))
print(len(movie_title))
print(len(budget))
print(len(revenue))
print(len(genre))
print(len(overview))
print(len(release_date))
```

    2400
    2400
    2400
    2400
    2400
    2400
    2400
    


```python
# Built the data frame 
movie_df_frame = pd.DataFrame({"Movie ID":movie_id1,"Title": movie_title, "Budget":budget,"Overview":overview,
                               "Revenue": revenue, "Genre": genre, "Production Company": production_comp, "Release Date": release_date},
                                 columns = ["Title", "Movie ID","Genre","Production Company","Budget", "Revenue", "Overview", "Release Date"])
movie_df_frame.to_csv("santhosh.csv", index =False)
movie_df_frame.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Movie ID</th>
      <th>Genre</th>
      <th>Production Company</th>
      <th>Budget</th>
      <th>Revenue</th>
      <th>Overview</th>
      <th>Release Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>285</td>
      <td>Adventure</td>
      <td>Jerry Bruckheimer Films</td>
      <td>300000000</td>
      <td>961000000</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>2007-05-19</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Harry Potter and the Order of the Phoenix</td>
      <td>675</td>
      <td>Adventure</td>
      <td>Warner Bros. Pictures</td>
      <td>150000000</td>
      <td>938212738</td>
      <td>Returning for his fifth year of study at Hogwa...</td>
      <td>2007-06-28</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Russian Lolita</td>
      <td>329103</td>
      <td>Romance</td>
      <td>Eros Movie</td>
      <td>0</td>
      <td>0</td>
      <td>The action of a controversial novel "Lolita", ...</td>
      <td>2007-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spider-Man 3</td>
      <td>559</td>
      <td>Fantasy</td>
      <td>Marvel Enterprises</td>
      <td>258000000</td>
      <td>890871626</td>
      <td>The seemingly invincible Spider-Man goes up ag...</td>
      <td>2007-05-01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Live Free or Die Hard</td>
      <td>1571</td>
      <td>Action</td>
      <td>Dune Entertainment</td>
      <td>110000000</td>
      <td>383531464</td>
      <td>John McClane is back and badder than ever, and...</td>
      <td>2007-06-20</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Cleaning the data by removing all the Nan values and zeroes on Revenue and Budget.
clean_movie_df = movie_df_frame.loc[(movie_df_frame["Title"] != 'NaN') & (movie_df_frame["Movie ID"] != 'NaN') &  (movie_df_frame["Genre"] != 'NaN') &  (movie_df_frame["Production Company"] != 'NaN') & (movie_df_frame["Budget"] != 'NaN') & (movie_df_frame["Revenue"] != 'NaN') & (movie_df_frame["Overview"] != 'NaN') & (movie_df_frame["Release Date"] != 'NaN')]
clean_movie_df.to_csv("santhosh clean.csv", index = False)
clean_movie_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Movie ID</th>
      <th>Genre</th>
      <th>Production Company</th>
      <th>Budget</th>
      <th>Revenue</th>
      <th>Overview</th>
      <th>Release Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>285</td>
      <td>Adventure</td>
      <td>Jerry Bruckheimer Films</td>
      <td>300000000</td>
      <td>961000000</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>2007-05-19</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Harry Potter and the Order of the Phoenix</td>
      <td>675</td>
      <td>Adventure</td>
      <td>Warner Bros. Pictures</td>
      <td>150000000</td>
      <td>938212738</td>
      <td>Returning for his fifth year of study at Hogwa...</td>
      <td>2007-06-28</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Russian Lolita</td>
      <td>329103</td>
      <td>Romance</td>
      <td>Eros Movie</td>
      <td>0</td>
      <td>0</td>
      <td>The action of a controversial novel "Lolita", ...</td>
      <td>2007-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spider-Man 3</td>
      <td>559</td>
      <td>Fantasy</td>
      <td>Marvel Enterprises</td>
      <td>258000000</td>
      <td>890871626</td>
      <td>The seemingly invincible Spider-Man goes up ag...</td>
      <td>2007-05-01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Live Free or Die Hard</td>
      <td>1571</td>
      <td>Action</td>
      <td>Dune Entertainment</td>
      <td>110000000</td>
      <td>383531464</td>
      <td>John McClane is back and badder than ever, and...</td>
      <td>2007-06-20</td>
    </tr>
  </tbody>
</table>
</div>




```python
clean_movie_df = clean_movie_df[clean_movie_df.Budget!=0]
clean_movie_df = clean_movie_df[clean_movie_df.Revenue!=0]
clean_movie_df.to_csv("clean movie data.csv", index = False)
clean_movie_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Movie ID</th>
      <th>Genre</th>
      <th>Production Company</th>
      <th>Budget</th>
      <th>Revenue</th>
      <th>Overview</th>
      <th>Release Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>285</td>
      <td>Adventure</td>
      <td>Jerry Bruckheimer Films</td>
      <td>300000000</td>
      <td>961000000</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>2007-05-19</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Harry Potter and the Order of the Phoenix</td>
      <td>675</td>
      <td>Adventure</td>
      <td>Warner Bros. Pictures</td>
      <td>150000000</td>
      <td>938212738</td>
      <td>Returning for his fifth year of study at Hogwa...</td>
      <td>2007-06-28</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spider-Man 3</td>
      <td>559</td>
      <td>Fantasy</td>
      <td>Marvel Enterprises</td>
      <td>258000000</td>
      <td>890871626</td>
      <td>The seemingly invincible Spider-Man goes up ag...</td>
      <td>2007-05-01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Live Free or Die Hard</td>
      <td>1571</td>
      <td>Action</td>
      <td>Dune Entertainment</td>
      <td>110000000</td>
      <td>383531464</td>
      <td>John McClane is back and badder than ever, and...</td>
      <td>2007-06-20</td>
    </tr>
    <tr>
      <th>5</th>
      <td>28 Weeks Later</td>
      <td>1562</td>
      <td>Horror</td>
      <td>DNA Films</td>
      <td>15000000</td>
      <td>64238440</td>
      <td>In this chilling sequel to 28 Days Later, the ...</td>
      <td>2007-04-26</td>
    </tr>
  </tbody>
</table>
</div>


