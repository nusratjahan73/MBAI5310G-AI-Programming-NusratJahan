Assignment 6: Model Evaluation, Explainability, and Fairness Reflection

Project: Hotel Booking Cancellation Prediction
Course: AI Programming


Dataset Description

This project uses the Hotel Booking Cancellation dataset. It has 350 booking records and 16 columns. Each row is one hotel booking and each column is one detail about that booking, such as the guest age, the guest type, the region, the booking channel, the room type, the number of guests, the number of nights, the lead time in days, the average daily rate, the number of special requests, the number of previous cancellations, the deposit type, and whether the stay covered a weekend. The dataset has no duplicate rows. One column, the average daily rate, had 6 missing values, which were filled with the median price of about 257.24 before training.


Target Variable

The target variable is booking_cancelled. A value of 1 means the booking was cancelled and a value of 0 means the booking was kept. About 55 percent of the bookings were kept and about 45 percent were cancelled, so the two groups are fairly balanced.


Model Used

The model is a Decision Tree classifier with a maximum depth of 4 and a fixed random state so the result repeats every run. Three group columns, the age group, the region, and the guest type, were kept aside for the fairness check and were not used as model inputs. The text columns were turned into numbers using one hot encoding, which gave 15 input columns, and the data was split into 280 training bookings and 70 testing bookings.


Main Evaluation Results

On the test data the model reached an accuracy of about 0.71, a precision of about 0.72, a recall of about 0.58, and an F1 score of about 0.64. The confusion matrix showed 32 correct kept bookings, 18 correctly caught cancellations, 7 false alarms, and 13 missed cancellations. Five fold cross validation gave an average accuracy close to 0.71 with only small variation, so the result is stable.


Main Business Interpretation

The model predicts whether a hotel booking will be cancelled so the hotel can act early, for example by confirming the stay, asking for a deposit, or planning to resell the room. Recall is the most important score here, because the main goal is to catch real cancellations, and the model still misses some. The most common mistake is the false negative, a missed cancellation, which is the costly error for a hotel because the room can sit empty at the last moment. The strongest signals were the lead time and the number of previous cancellations. The fairness check showed the model does not behave equally across age groups, regions, and guest types. Overall the model is best treated as an early prototype that gives useful insight but is not yet ready for real business decisions on its own.


One Limitation

The dataset is small with only 350 bookings and appears to be synthetic, so it may not reflect the messy patterns of real hotel data. Because of this, the model may not perform the same way on real bookings and should be retested on a larger real dataset before any real use.
