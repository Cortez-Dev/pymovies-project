# Pymovies

Web Application Link: [Pymovies](https://pymovies-project.herokuapp.com/)

Github project link: [Cortez-Dev/pymovies-project](https://github.com/Cortez-Dev/pymovies-project.git)

## Introduction

__Pymovies__ is a python driven web application designed to provide users with movie recommendations based on frequently watched movies. User would be able to access personilized recommendation by creating account. User history will be saved while they browse movies and would be recommended movies based on their history. Users will also be able to save movies into watchlist to save movies for later. We provide users with filter to filter movies based on genre. User can also search for movies by title. Movies are ordered according to rating in descending order.

## Installation

Download or clone the project from git repository on local machine and install all requirements using the command

```bash
pip install -r requirements.txt
```

## Usage

Navigate to the project directory

- Create a admin using command
    ```bash
    python manage.py createsuperuser
    ```
- Create migrations and migrate using
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```
- Insert movie database in Movie model using the movies.json file by entering django shell

    - Entering the shell
        ```bash
            python manage.py shell
        ```
    - Inserting movies in Movie Model
        ```python
            import json
            form movies.models import Movie

            with open('movies.json') as f:
                movies_list = json.load(f)

            for movie in movies_list:
                movie = Movie(title=movie['title'], img_url=movie['img_url'], info=movie['info'], rating=movie['rating'], genre=movie['genre'], story=movie['story'])
                movie.save()

        ```
- After all above steps run server on local machine using
    ```bash
        python manage.py runserver
    ```

## Algorithm used for Dataset training

### Association Rule learning <p>
Association rule learning is a rule-based machine learning method for discovering interesting relations
between variables in large databases. It is intended to identify strong rules discovered in databases using
some measures of interestingness.</p>

### Apriori
<p>
Apriori uses a breadth-first search strategy to count the support of itemsets and
uses a candidate generation function which exploits the downward closure property of support.  
In simple terms, it proceeds by identifying the frequent individual items in
the database and extending them to larger and larger item sets as long as those item sets appear sufficiently often in the database.</p>

#### Support <p>
Support is an indication of how frequently the itemset appears in the dataset</p>
![](/resources/support.png)

#### Confidence <p>
Confidence is an indication of how often the rule has been found to be true.</p>
![](/resources/confidence.png)

#### Lift <p>
It is defined as :
![](/resources/lift.png) </p>

If the lift is > 1, that lets us know the degree to which those two occurrences are dependent on one another, and makes those rules potentially useful for predicting the consequent in future data sets.

If the lift is < 1, that lets us know the items are substitute to each other. This means that presence of one item has negative effect on presence of other item and vice versa.

#### Apriori Flowchart
![](/resources/flow.png)
## License
[MIT](https://choosealicense.com/licenses/mit/)
