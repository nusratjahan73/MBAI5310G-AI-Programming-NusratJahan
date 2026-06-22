Assignment 8 Natural Language Processing Pipeline and Text Classification


Overview

In this assignment I build a basic Natural Language Processing pipeline in Python. I work with a dataset of hotel guest reviews, and I teach a computer to read a review and decide which service area it belongs to. The work follows the topics from class, such as cleaning text, tokenizing, removing stopwords, stemming and lemmatizing, part of speech tagging, named entity recognition, feature extraction, and text classification.


The Dataset

I use a dataset of 120 hotel guest reviews. The text column is GuestReview, which holds what the guest has written. The label column is ServiceArea, which has six balanced groups. They are Staff Service, Booking Issue, Location, Check In, Breakfast, and Room Cleanliness. The data has no missing values, and each group has exactly twenty reviews.


The Business Problem

A hotel group receives many reviews every day and cannot read them all by hand. My model reads each review and predicts its service area, so the hotel can send the comment to the right team and reply to guests faster.


Why I Choose ServiceArea as the Target

I choose ServiceArea as the target because it has six clear and balanced groups, which keeps the model fair and the results easy to judge. I have also looked at the Rating column from one to five, but its values are uneven and a short review does not always show the exact star score, so ServiceArea gives a cleaner and more useful task.


What I Have Built

I have built two things. The first is a Jupyter notebook named Assignment8_NLP_Hotel_Reviews.ipynb, which holds the full solution with code and clear explanations. The second is a business report named Assignment8_Business_Report.docx, which explains the project in plain language for a business reader.


What the Notebook Contains

The notebook completes eight tasks. In task 1 I load and inspect the data. In task 2 I clean the text and make a clean text column. In task 3 I explore the text and show the most common words with a chart. In task 4 I apply part of speech tagging and named entity recognition on three example reviews. In task 5 I turn the words into numbers with TF IDF. In task 6 I split the data and train two models, Naive Bayes and Logistic Regression. In task 7 I evaluate the models with accuracy, a confusion matrix, and a classification report. In task 8 I write a short business interpretation.


How to Run the Notebook

I open the notebook in Jupyter from inside the assignment folder, because the notebook reads the data with a short relative path. I then run the cells from top to bottom. The first cell checks that every needed library is installed and installs any that is missing. The first run also downloads small language files for NLTK and the small English model for spaCy, so I need internet for a moment. After that the notebook runs on its own.


Libraries I Use

I use pandas, numpy, matplotlib, NLTK, spaCy, and scikit learn. The notebook installs any missing library by itself, so I do not have to set up anything by hand.


The Result

Both models classify the test reviews with very high accuracy, so the pipeline sorts reviews into the correct service area. I keep Naive Bayes as the final model because it is simple, fast, and easy to explain. I am also honest that the accuracy is very high because the dataset is small and the words in each area are very distinct, so the score may drop on larger and messier reviews.
