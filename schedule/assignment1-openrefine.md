### Normalizing names using Open Refine

1. Start up Open Refine

2. Choose *Create Project*, then choose the gzipped reviews file as input, then click *Next*.

Open Refine automatically unzips the file and tries to figure out field separator, headers and column value types.

3. In the next screen, you're shown an preview of the table that Open Refine will generate. All default values should be correct, so choose a project name in the top right, then click *Create Project*.

4. Find the *collectionname* column and click the upside down triangle, select *Facet* > *Text Facet*. On the left hand side, you should now see a distribution of the reviews over collections. If you click a collection name in this facet box once, the table will be filtered to show only the reviews belonging to this collection. If you click another collection name, you change the filter. If you click the active name again, you remove the filter.

5. Now add another facet for the *publisher* column. Make sure that no *collectionname* filter is used. You should see a list of 1831 values in the *publisher* facet. 

6. Before making any changes to a particular column, it's wise to first copy it to an extra column and make changes in that extra column. In the *publisher* column, select *Edit column* > *Add column based on this column...*. Choose a name for the column, e.g. "publisher_normalized". in The *Expression* box, change the default expression (*value*) to remove some common but not very meaningful variation, such ("Uitgeverij ", ", Uitgeverij", " Uitgevers"). Make sure the *Expression* box has the following expression: *value.replace(", Uitgeverij","").replace("Uitgeverij ","").replace(" Uitgevers")*. The are other common variants, like *B.V.*, *[.etc]*. 

7. In the top left, click on *Undo/Redo*. This shows a list of the transformations you've made on the original table. This is a useful documentation of the data interaction process. Moreover, this list can be exported and repeated on similar datasets. 

8. Open Refine offers a very simple interface for clustering variant names. Create a *Text Facet* for the new column, then in facet box, click *Cluster* and you will be shown a list of what Open Refine suggsts as values to be clustered, and preferred names for those clusters. You can change the algorithm and parameters used for clustering and accept suggested clusters. If you merge clusters you can rerun the clustering algorithm to see if it finds new clusters. Another strategy is the iterate over the clustering algorithm, as some are more effective after initial clustering by other algorithms.

### Classifying by NUR codes

NUR codes are 3-digit numbers used to classify books by genre according to a Dutch variant of the Dewey Decimal Classification. (See [http://www.boek.nl/nur](http://www.boek.nl/nur) for more information).

9. Make a copy of the *nur* column (*Edit column* > *Add column based on this column...*) and use the *Expression* box to transform the original value to an actual number, rounded down to its multide of 100. E.g. 614 becomes 600, 338 becomes 300. Use the following expression for this: *(toNumber(value) / 100) * 100*.

Like the DDC, the NUR classification system is hierarchical, with all numbers between 500 and 599 indicate genres related to *travel*. The top level NUR codes are a way to broadly classify books and their reviews, but also publishers of those books. Many of the small publishers only publish books in a specific non-fiction subject area or in a small number of fiction genres (e.g. only literary thriller, or crime and mistery). But there are also small publishers that cover a diverse set of genres. 



