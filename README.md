# MSR-Assignment-2
Mining Software Repositories project to analyze Github Commits and use sentiment analysis to check whether there is correlation between negative human sentiment and Faulty Commits which may induce Fixes by Developers.

A reproduction as part of the MSR course at MSR course 2020/21 at UniKo, CS department, SoftLang Team 

Please cite the following paper if you intend to know more about the original research 

>  **Is Developer Sentiment Related to Software Bugs: An Exploratory Study on GitHub Commits**
  https://ieeexplore.ieee.org/document/9054801
  
> **DBLP Link:**
  https://dblp.org/rec/conf/wcre/HuqSS20.html

## Requirements:

To run this project, you will need

Python IDE (Jupyter Notebook or PyCharm-In Case of Alternative Process)
Python3+ must be installed on the system.
	
Execute the below commands in the terminal based on your OS
```
	Unix/macOS
	python -m pip install -r requirements.txt

	Windows
	py -m pip install -r requirements.txt

```
## Process for acquiring the results: 

  * **Step 1:**
  Clone the project into your local machine

  * **Step 2:**
  Execute the requirements commands in the terminal based on your OS to ensure you have the right setup for code execution

  * **Step 3:**
  Change directory to the Process folder 
  
 	 ```cd Process```

  * **Step 4:**
  Execute the code present in the Process folder (File Name-MSR-Assignment.py) in the IDE
  
  Please note that after each run of the file Guava Repository Folder from the Process folder has to be deleted manually as for each run, GitHub API scrapes updated data and for successfull scraping older data has to be deleted

## Alternative Process for acquiring the results(Backup):
For quick running of program, PyCharm use is suggested as it has good controls for removing manual steps to pull a repository and get it running.

Steps are:
  * **Step 1:**
  Make sure one is signed in on Github in Pycharm
  
  * **Step 2:**
  Open a new project
  
  * **Step 3:**
  Go to VCS Option on the Top Horizontal Options Bar
  
  * **Step 4:**
  Select Enable Version Control Integration Control inside VCS if not done already
  
  * **Step 5:**
  After checking the previous option on, select Checkout from Version Control and select Git
  
  * **Step 6:**
  In the new pop up window, include the link of the github repository you are trying to pull.
  Subsequently in the same pop up window, select an appropriate directory where the  project will be pulled.
  
  * **Step 7:**
  Select clone option to start the pulling process.
  
  * **Step 8:**
  Select option to start the pulled project in New Window or This window as per your personal preference.
  
  * **Step 9:**
  After this the project will be up and running and requirements. Txt file will automatically install required libraries. Run the file MSR-Assignment.py from Process Folder to get the results

This is a quick process to start the testing of GitHub project taken from the Official Jet Brains Website. We have tried this with several PC’s and are confident that this will not give any errors.

> **Link to Above Process Video:**
  https://www.youtube.com/watch?v=ukbvdF5wqPQ&feature=emb_title

## Results:

Results are stored in an excel file inside Doc Folder named results.xlsx. The information stored is taken from program console and are taken after the code was run on 30/1/2021 10:08:00 PM IST.

Screenshots of Results are as follows:

<img src="Data/Result_2.png"> 
<img src="Data/Result_1.png"> 

## Contents of Doc Folder:

Doc Folder consists of Input File (Acquired after scraping GitHub Repository) named as Guava_Commit_Raw.csv and an Output File(Results.xlsx) for viewing the input and output without execution. 

## Validation: 

Check the generated output files in the below order to validate and understand the result

**1) Guava_Commits_Raw.csv** - The cloned repository commit messages

**2) Guava_Cleaned_Commits.csv** - The cleaned commit messages

**3) Guava_Commits_Categorized.csv** - The categorised messages

**4) Guava_Commits_Cleaned_Final.csv** - The clean data after categorisation

**5) Guava_Sentiment_Scores.csv** - The sentiment values for each message

**6) Guava_Commits_Final.csv** - The final output which will be used for statistical analysis including the categories and the sentiment values

**7) Results.xlsx** – The final statistical inference


## Data: 

Input data is the extracted messages from the cloned repository, the remaining files created as part of the program are all intermediate files.
The final results are printed as part of the console

<img src="Data/DataFlow.png"> 

## Delta: 

### Process delta: 

* The original process followed in the research paper applies to 13 different GitHub repositories to collect a strong inference on the actual research. With respect to reproducing the research, we have applied the research steps on only 1 repository to avoid scalability issues. 

* The sentiment analysis performed in the original research paper involves Senti4SD tool but due to the corrupted jar file within the Senti4SD code, we chose to alternatively go for NLTK Vader Sentiment analysis. In addition, NLTK Vader Sentiment Analysis sentiment scores for GitHub Commits(which were in the form of floating numbers ranging from [-1,1] were rounded up to -1/1(0 was pre-defined by the tool) as the output sentiment scores of GitHub Commits in original research process gave output in form of -1/0/1 for Negative, Neutral and Positive Sentiments for each GitHub Commit respectively.

* Mann-Whitney U Test (aka, Wilcoxon Rank Sum Test) has been implied on the data for statistical analysis despite the fact that Wilcoxon Rank Sum Test was used in the research paper since both are officially the same. Both are known to produce similar results but with minute differences.

### Data delta: 

* Due to no underlying piece of code in the research paper, we have developed the code from scratch using Python and its libraries to perform pre-processing, categorization, sentiment analysis and statistical analysis on the input data. 

* Among the multiple categories in which the data was split into, we have left out the non-FIF FC category as there was no clear understanding about this categorization in the paper and we were not ready to try out the categorization on the basis of our assumption.

* The p-values resulting from Bonferroni corrections is mostly 1 which means that the Mean values of the comparing data is almost same. This is inevitable as there is minor difference between the sentiment values among the different categories.

* The result in the research paper involves a combination of 13 huge repositories wherein we assume the results that we got from our reproduction project is different since we considered only one medium sized repository for this task and that the repository might be biased.
