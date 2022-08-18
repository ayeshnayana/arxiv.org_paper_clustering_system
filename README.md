# arxiv.org_paper_clustering_system
Every day arxiv.org get more than a thousand pre-print articles submitted. Their authors classify these articles as hep-ph, hep-ex hep-th, etc. However, some of these papers in each subfield can be clustered by their content. For example, in hep-ph, articles can be submitted based on effective field theory (EFT), or it could be dark matter. Even in EFT, there are different sub-branches such as HQET, SMEFT, etc. So the question is can we cluster these papers by their similarity in content? Ideally, it would be awesome if we could cluster the EFT papers into one cluster and dark matter papers into another group, but such a perfect clustering will not be an easy feat. 

As a physics researcher, I regularly read pre-print articles from arxive.org to get updated with the field's state-of-the-art research. However, finding a relevant and interesting article for my line of work was difficult with many submissions. Finding a suitable paper took several hours of my time every day. Because of this, I decided to build a program that clusters similar documents together and visualizes the clustered articles. 

 ### The arxiv.org research article clustering system incorporates: 
 
  -Data extraction system from abstracts using web scraping
  
  -Research article clustering system based on KMeans clustering algorithm
  
  -Clustered article visualization system using T-SNE. 
  
## Data extraction

We use web scraping techniques to obtain the data from the arxiv.org website. Using the python requests package, we get the HTML data from the "https://arxiv.org/list/hep-{}/recent" URL. Inside the curly brackets, the user must define the specific field. For example, if users wish to obtain phenomenology articles, they should input "ph."

These HTML data are then parsed into a soup using the python bs4 package. For further processing, we scrape the paper links from the soup. 

The scraped paper links are then used to access the main page of each paper on arxiv.org. Then we scrape the content found in the paper abstract. These scraped abstracts are then stored in an array to create a TF-IDF matrix using the TfidfVectorizer python package. The TF-IDF matrix only contains the vital text in each abstract. It omits less relevant words like articles. This TF-IDF matrix feed into the KMeans algorithm implemented using a pipeline for clustering. 
  
  
## KMeans clustering and unsupervised learning

In unsupervised learning, the algorithms find patterns in data. Unlike supervised learning, these data used in unsupervised learning do not contain labels to classify them. Therefore, we do not have a specific prediction task in unsupervised learning. 

### KMeans clustering

In KMeans clustering algorithm finds clusters of samples. The number of clusters (k) needs to be defined. Here we used the KMeans algorithm implemented in the sklearn("scikit-learn). 

The KMeans algorithm initializes a set of k number of clusters randomly. Then it calculates the cluster centroids (mean of each cluster). Each data point gets allocated into the groups when the algorithm progresses by reducing the in-cluster sum of squares.

In other words, KMeans try to allocate each data point to the nearest cluster while keeping the centroids small as possible.

## Visualization

To visualize the clustered articles, we use the T-SNE algorithm in sklearn. In KMeans, each cluster gets assigned a label. These labels and a list of article names then feed into T-SNE. 

The T-SNE algorithm is a dimensionality reduction algorithm similar to the PCA. 

Inside the TF-IDF matrix, each article is identified by many features. Each feature represents an important word obtained from the abstract. This large dimensionality needs to be reduced to 2 dimensions to visualize them in a 2D plane. Using T-SNE, we reduce the dimensionality of the TF-IDF matrix to two. Then we plot each paper using a scatter plot. Each point on the scatter plot is colored according to the label created during the clustering. The name of each article is then annotated. 

The following figure visualizes the clustered articles using T-SNE.

![download (7)](https://user-images.githubusercontent.com/42178947/185478958-af8a91ab-7602-437c-97fd-5b054df25a85.png)

Figure: The clustered research articles rendered using T-SNE. The articles that belongs to same cluster have similar color.

