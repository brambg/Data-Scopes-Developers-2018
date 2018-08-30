## Research background: Online Book Reviews

The reception of literature is an research direction within the Humanities Cluster. One aspect to study is how readers discuss the books they read online, as part of communities of readers or just for themselves as way to reflect on what they thought of the book or to keep track of their own reading. Studying book reviews by different readers allows us to analyse how fiction and non-fiction books are received by the reading public, how appreciation varies across book genres, reader demographics, reading communities and over time. 

At Huygens ING, researcher Peter Boot is collecting online book responses, including reviews and discussions, of Dutch and translated fiction to study how the reading of books affects readers. This requires linguistic analysis of how readers express the aesthetic and emotional impact of a book, what it reminded them of, what they've learned or how it changed their opinions, views or attitudes. This is a challenging research project that requires both a large collection of book responses, complex linguistic analysis of review text, careful gathering and curation of book and review metadata: 

- which book and which edition is reviewed?
- who is the reviewer?
- when did they read and review this?
- what is the purpose of the review (a product review for a commercial website versus a review for a book discussion website, as part of a book club or just for themselves)

This research project serves as the background for data and assignments in this workshop. 

## Data Scopes assignments

### Preparing review dataset for analysis of publishers and genres

Publishers often focus on a small range of genres, although some publish books on any genres. They sometimes also play with genre labels for sales purposes, such as classifying a Thriller as a Literary Thriller to target an audience that would consider "normal" thrillers of no interest.

To investigate how publishers are related to fiction and non-fiction genres, and how this changes over time, scholars want to transform the dataset of book reviews to make the data axes "publisher" and "genre" useful for analysis.

The assignment is to help with this transformation.

**Note: it is not a test to see if you make the right decisions nor a suggestion that HuC DI developers are responsible for making these kinds decisions for researchers. It is about understanding what is important in this process, how it potentially affects research (and therefore how we can communicate this to researchers), and how we as a department should take into account these issues when developing data models, functionality for searching and analysing, and user interfaces.**

### Step 1. getting an overview

- How many reviews are in the dataset?
- Which fields are there and for what fraction of the dataset are these fields filled in?
- How complete is the *isbn* metadata? Sort the reviews on book title. Is ISBN useful for grouping reviews for the same book?
- How complete is the *publisher* and *bookgenre* metadata?


### Step 2. understanding distributions

- what is the frequency distribution of ISBNs? of authors? of publishers? of bookgenres? 
- 

The dataset contains book reviews from different source sites, including bol.com and hebban.nl. The source of a review is identified in the *collectionname* field. 

- What is the distribution of reviews of collections?

### Step 3. investigating publisher metadata

- Sort the *publisher* column alphabetically. What issues do you foresee in analysing the relation between *publisher* and *bookgenre*?

The tail is very long, with some very small publishers who published only a few titles, but also variant names of large publishers that should be grouped with other variants to get appropriate grouping of book titles, genres and reviews.

- Look at the *publisher* metadata for the Hebban collection
    - sort publishers alphabetically. Does it need the same amount of normalizing?
    
It seems Hebban already normalizes publisher names (see their policy on modifying book information in the [Hebban FAQ](https://www.hebban.nl/faq)). Compare some of the normalized publisher names in Hebban reviews with variants of those names in the other collections. Can you reverse engineer how they normalized names?


