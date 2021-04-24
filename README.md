# Quora_Question_Pair_Similarity
  <h3>Problem Statement: </h3></br>
     1.Identify which questions asked on Quora are duplicates of questions that have already been asked.</br>
     2.This could be useful to instantly provide answers to questions that have already been answered.</br>
     3.Therefoe its like  predicting whether a pair of questions are duplicates or not, which boils down to two class classification problem.</br>
   <hr>
   <h3>Data Overview</h3>
   </br>
     1.Data can be obtained from  https://www.kaggle.com/c/quora-question-pairs/data </br>
     2.That csv contains 5 columns : qid1, qid2, question1, question2, is_duplicate </br>
     3.Number of rows in that csv file = 404,290 </br>
   </br><hr>  
   <h3>Exploratory Data Analysis</h3>
     Perform exploratory data analysis on whole data to get some meaningful insights about data.
     <h6>Distribution of classes in data set</h6>
     ![Screenshot (157)](https://user-images.githubusercontent.com/65904480/115962924-2659b980-a53b-11eb-9959-0eef4a382506.png)</br>
     <h6>Plot between unique questions and duplicate questions</h6>
      ![Screenshot (158)](https://user-images.githubusercontent.com/65904480/115962928-278ae680-a53b-11eb-8515-0450e1e195cc.png)</br>
      <h6>Number of occurences of each question</h6>
      ![Screenshot (159)](https://user-images.githubusercontent.com/65904480/115962930-28237d00-a53b-11eb-8423-da8521fc904e.png)</br>
     <hr>
     <h3>Basic Feature Extraction (before cleaning)</h3>
      1.freq_qid1 = Frequency of qid1's </br>
      2.freq_qid2 = Frequency of qid2's </br>
      3.q1len = Length of q1 </br>
      4.q2len = Length of q2 </br>
      5.q1_n_words = Number of words in Question 1 </br>
      6.q2_n_words = Number of words in Question 2 </br>
      7.word_Common = (Number of common unique words in Question 1 and Question 2) </br>
      8.word_Total =(Total num of words in Question 1 + Total num of words in Question 2) </br>
      9.word_share = (word_common)/(word_Total) </br>
      10.freq_q1+freq_q2 = sum total of frequency of qid1 and qid2 </br>
      11.freq_q1-freq_q2 = absolute difference of frequency of qid1 and qid2 </br>
      <hr>
      <h3>Preprocessing of Text</h3>
       1 Preprocessing:
Removing html tags
Removing Punctuations
Performing stemming
Removing Stopwords
Expanding contractions etc.
     


   
