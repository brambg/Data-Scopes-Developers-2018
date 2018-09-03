# Hands-on Session 2: Combining Heterogeneous Review Datasets

There are three datasets with reviews extract from three different websites:

- [leestafel.info](http://leestafel.info/)
- [literairnederland.nl]()https://www.literairnederland.nl/category/recensies/
- [boekreviews.nl](http://www.boekreviews.nl/)

These websites were crawled for book reviews. Not all website content was crawled, and some reviews may have been missed. Also, some crawled pages may not represent book reviews.

Go to the workshop SurfDrive folder (you should have received the URL for that in an email) and download the datasets 

- *crawled_reviews-boekreviews.csv.gz*
- *crawled_reviews-leestafel-info.csv.gz*
- *crawled_reviews-literair-nederland.csv.gz*

These contain some 8k reviews. Because the websites each have their own choices of what metadata to include, have changed their policies over time and have not always been consistent, the available metadata per review varies. 

## Step 1. Comparing Datasets

Compare the three datasets on a number of aspects:

- number of reviews
- source of metadata
- overlap in metadata
- completeness of metadata
- number of reviewers

Make a description of this analysis for others (or yourself at a later date) so they can get a quick understanding of the characteristics of these datasets.

### Step 2. Filtering/Selecting Reviews

Are there reviews that you would leave out? E.g.:

- data records for which the reviewed book cannot be identified,
- data records that are not actual book reviews,

Think of a good way to keep the filtered out reviews visible, along with clear filtering criteria.

Also, some reviews may review multiple books. How would you deal with these in combining the three datasets?

How do you deal with different provenance of specific metadata fields? E.g. ISBN extracted from text vs. ISBN via WorldCat Search SRU lookup?



