# Research background: Online Book Reviews

The reception of literature is an research direction within the Humanities Cluster. One aspect to study is how readers discuss the books they read online, as part of communities of readers or just for themselves as way to reflect on what they thought of the book or to keep track of their own reading. Studying book reviews by different readers allows us to analyse how fiction and non-fiction books are received by the reading public, how appreciation varies across book genres, reader demographics, reading communities and over time. 

At Huygens ING, researcher Peter Boot is collecting online book responses, including reviews and discussions, of Dutch and translated fiction to study how the reading of books affects readers. This requires linguistic analysis of how readers express the aesthetic and emotional impact of a book, what it reminded them of, what they've learned or how it changed their opinions, views or attitudes. This is a challenging research project that requires both a large collection of book responses, complex linguistic analysis of review text, careful gathering and curation of book and review metadata: 

- which book and which edition is reviewed?
- who is the reviewer?
- when did they read and review this?
- what is the purpose of the review (a product review for a commercial website versus a review for a book discussion website, as part of a book club or just for themselves)

This research project serves as the background for data and assignments in this workshop. 

### Data Scopes Hands-on Sessions

- Hands-on Session 1: Creating a Data Axis for Publishers
- Hands-on Session 2: Combining Heterogeneous Datasets

### Preparing review dataset for analysis of publishers and genres

Publishers often focus on a small range of genres, although some publish books on any genres. They sometimes also play with genre labels for sales purposes, such as classifying a Thriller as a Literary Thriller to target an audience that would consider "normal" thrillers of no interest.

To investigate how publishers are related to fiction and non-fiction genres, and how this changes over time, scholars want to transform the dataset of book reviews to make the data axes "publisher" and "genre" useful for analysis.

The assignment is to help with this transformation.

**Note: it is not a test to see if you make the right decisions nor a suggestion that HuC DI developers are responsible for making these kinds decisions for researchers. It is about understanding what is important in this process, how it potentially affects research (and therefore how we can communicate this to researchers), and how we as a department should take into account these issues when developing data models, functionality for searching and analysing, and user interfaces.**

## Hands-on Session 1: Creating a Data Axis for Publishers

Go to the workshop SurfDrive folder (you should have received the URL for that in an email) and download the dataset *reviews.sample-0.05.csv.gz*. This contains some 18k reviews.

### Step 1. Getting an overview of the dataset

Unzip the CSV file and open it with your preferred software package or module (Pandas, Excel, Open Refine, UNIX command line, ...). [Here is a step-by-step version using Open Refine](assignment1-openrefine.md). The first step is to get an idea of what the data looks like. Try and find answers to the following questions:

- How many reviews are in the dataset?
- Which fields are there?
- How complete is the *isbn* metadata? Sort the reviews on book title. Is ISBN useful for grouping reviews for the same book?
- How complete is the *publisher* and *bookgenre* metadata?


### Step 2. Analyzing review distributions

The next step is to get a feel for how the data is distributed. E.g. how many different books are reviewed, by how many different authors? And how do the number of reviews per book or author vary?

- What is the frequency distribution of ISBNs? of authors? of publishers? of bookgenres?

The dataset contains book reviews from different source sites, including bol.com and hebban.nl. The source of a review is identified in the *collectionname* field.

The collectionname refers to the source website of reviews:
- [LTL (Lezers Tippen Lezers)](http://www.lezerstippenlezers.be/)
- [Bol](https://www.bol.com/nl/boeken/index.html)
- [Dizzie](http://dizzie.nl/) (offline since April 2016)
- [WLJN (Wat Lees Jij Nu)](http://watleesjij.nu/) (no longer a book review forum)
- [Hebban](https://www.hebban.nl/)

What is the distribution of reviews over the five collections? Is this a balanced dataset or is it skewed towards a particular collection?

### Step 3. creating a data axis for publishers

To analyse the relation between publishers and book genres, the *publisher* column needs to be turned into a usable data axis. But there are two hurdles to overcome first.

#### 3.1 normalizing publisher names 

Sort the *publisher* column alphabetically. What issues do you foresee in analysing the relation between *publisher* and *bookgenre*?

The tail is very long, with some very small publishers who published only a few titles, but also variant names of large publishers that should be grouped with other variants to get appropriate grouping of book genres and reviews by publisher.

- Select the reviews for the Bol collection and sort publishers alphabetically. 
- Do the same for the reviews of the Hebban collection. 

Does they need the same amount of normalizing?

It seems Hebban already normalizes publisher names (see their policy on modifying book information in the [Hebban FAQ](https://www.hebban.nl/faq)). Compare some of the normalized publisher names in Hebban reviews with variants of those names in the other collections. Can you reverse engineer how they normalized names?

Finally, try and normalize publishers names:
- First, come up with a plan to normalize names so that variations are conflated to a single canonical name. What normalizing steps would be relatively safe?
- How could you make this normalization process transparent to users of the dataset?
- You can use any tool you like. Open Refine has handy clustering functionality for just these kinds of tasks. (See the [OpenRefine clustering documentation](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth)


#### 3.2 clustering low-frequency publishers

The long tail of low-frequency publishers causes another problem for analysis. Individually, they carry little information to use in qualifying the relation between publishers, genres and reviewers. But they represent the vast majority of publishers, so visualizing all publishers would drown out the main publishers. But leaving out the small publishers limits the generality of the analysis, because together they form a sizeable chunk of the reviews and reviewed books.

Think of ways in which you can cluster or group low-frequency publishers, using f.i. the NUR codes of the books they publish, or the ISBN publisher prefixes (see [Structure of IBSN](https://en.wikipedia.org/wiki/International_Standard_Book_Number#Overview) (English) and [Structuur van het ISBN](https://nl.wikipedia.org/wiki/Internationaal_Standaard_Boeknummer#Structuur_van_het_ISBN) (Dutch)). As a (rather ad hoc) definition of low-frequency publisher, use a threshold of 10 or fewer ISBNs in the dataset.



