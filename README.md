# arxiv.org_paper_clustering_system
Every day arxiv.org get more than a thousand pre-print articles submitted. Their authors classify these articles as hep-ph, hep-ex hep-th, etc. However, some of these papers in each subfield can be clustered by their content. For example, in hep-ph, articles can be submitted based on effective field theory (EFT), or it could be dark matter. Even in EFT, there are different sub-branches such as HQET, SMEFT, etc. So the question is can we cluster these papers by their similarity in content? Ideally, it would be awesome if we could cluster the EFT papers into one cluster and dark matter papers into another group, but such a perfect clustering will not be an easy feat. 

As a physics researcher, I regularly read pre-print articles from arxive.org to get updated with the field's state-of-the-art research. However, finding a relevant and interesting article for my line of work was difficult with many submissions. Finding a suitable paper took several hours of my time every day. Because of this, I decided to build a program that clusters similar documents together and visualizes the clustered articles. 

 # The arxiv.org research article clustering system incorporates 
  -Data extraction system from abstracts using web scraping
  -Research article clustering system based on knn algorithm
  -Clustered article visualization system using T-SNE. 
