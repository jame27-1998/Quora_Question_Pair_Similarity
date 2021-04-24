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
        1.Removing html tags</br>
        2.Removing Punctuations </br>
        3.Performing stemming</br>
        4.Removing Stopwords</br>
        5.Expanding contractions etc. </br>
        <hr>
        <h3>Advanced Feature Extraction (NLP and Fuzzy Features) </h3>
        Few Terminology:

Token: You get a token by splitting sentence a space </br>
Stop_Word : stop words as per NLTK. </br>
Word : A token that is not a stop_word</br></br>
Features:
<br>
cwc_min : Ratio of common_word_count to min lenghth of word count of Q1 and Q2 <br>
cwc_min = common_word_count / (min(len(q1_words), len(q2_words)) <br>



cwc_max : Ratio of common_word_count to max lenghth of word count of Q1 and Q2 <br>
cwc_max = common_word_count / (max(len(q1_words), len(q2_words)) <br>



csc_min : Ratio of common_stop_count to min lenghth of stop count of Q1 and Q2
csc_min = common_stop_count / (min(len(q1_stops), len(q2_stops))



csc_max : Ratio of common_stop_count to max lenghth of stop count of Q1 and Q2 <br>
csc_max = common_stop_count / (max(len(q1_stops), len(q2_stops)) <br>



ctc_min : Ratio of common_token_count to min lenghth of token count of Q1 and Q2 <br>
ctc_min = common_token_count / (min(len(q1_tokens), len(q2_tokens)) <br>



ctc_max : Ratio of common_token_count to max lenghth of token count of Q1 and Q2
ctc_max = common_token_count / (max(len(q1_tokens), len(q2_tokens))



last_word_eq : Check if First word of both questions is equal or not <br>
last_word_eq = int(q1_tokens[-1] == q2_tokens[-1]) <br>



first_word_eq : Check if First word of both questions is equal or not <br>
first_word_eq = int(q1_tokens[0] == q2_tokens[0]) <br>



abs_len_diff : Abs. length difference <br>
abs_len_diff = abs(len(q1_tokens) - len(q2_tokens)) <br> 



mean_len : Average Token Length of both Questions <br>
mean_len = (len(q1_tokens) + len(q2_tokens))/2 <br>



fuzz_ratio : https://github.com/seatgeek/fuzzywuzzy#usage http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/ <br>



fuzz_partial_ratio : https://github.com/seatgeek/fuzzywuzzy#usage http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/ <br>



token_sort_ratio : https://github.com/seatgeek/fuzzywuzzy#usage http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/ <br>
 
token_set_ratio : https://github.com/seatgeek/fuzzywuzzy#usage http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/ <br>

longest_substr_ratio : Ratio of length longest common substring to min lenghth of token count of Q1 and Q2 <br>
longest_substr_ratio = len(longest common substring) / (min(len(q1_tokens), len(q2_tokens)) <br>

<h6> Featurizing Text Data</h6>
<br>
Tf-idf weighted word2vec
</br>
<h6>Machine Learning models</h6>
</br>
1.Random model , testloss =0.887242646958</br>
2.Logistic Regression with hyperpararmeter tuning, testloss=0.520035530431</br>
3.Linear SVM with hyperparameter tuning ,test loss= 0.489669093534</br>
4.Xgboost , testloss= 0.357054433715</br>

<h3> Conclusion</h3>
Given data is  imbalance data with 63.08% not similar and  39.02% similar. Taking logloss as a metric to measure perfomance of the model is a wrong idea because even a dumb model can have an logloss of 0.88. So we plot  , precision matrix and recall matrix, and also plot connfusion matrix to clearly understand about performance of model.From the results obtained Xgboost model performs better here.
     


   
