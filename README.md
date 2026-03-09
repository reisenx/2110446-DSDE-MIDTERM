# 2110446 DATA SCIENCE AND DATA ENGINEERING (MIDTERM)

Traffy Fondue Take-home Midterm exam of 2110446 DATA SCIENCE AND DATA ENGINEERING Course in Chulalongkorn University (2025)

---

# Traffy Fondue

**Traffy Fondue** is a digital platform developed by Thailand's National Electronics and Computer Technology (NECTEC)
which allows residents to report infrastructure issues such as broken streetlights, garbage or flooding.

It is adopted by the Bangkok Metropolitan Administration (BMA) as a central digital platform for the residents
to report their issue and uses Artificial Intelligence (AI) to automatically send to the correct government department.
The residents can access the service via LINE messaging app and a website.
After reporting the issues, users receive updates on the progress.

In March 2026, Bangkok Traffy Fondue has received more than 1,200,000 reports and more than 1,000,000 reports resolved.
This shows that the system clearly improves efficiency, transparency, and citizen engagement of Bangkok government workflow.

---

# Overview

This project focuses on building a pipeline to perform data preprocessing and implement machine learning model
to classify the input report text according to government department below.

- สำนักงานตำรวจแห่งชาติ
- การรถไฟฟ้าขนส่งมวลชนแห่งประเทศไทย
- สภาเด็กและเยาวชนกรุงเทพมหานคร
- กรมควบคุมมลพิษ
- กรมสรรพสามิต
- การไฟฟ้านครหลวง
- กรมทางหลวง
- สำนักงานประกันสุขภาพแห่งชาติ
- การประปานครหลวง
- คณะกรรมการการพัฒนาเศรษฐกิจ
- กระทรวงการท่องเที่ยวและกีฬา
- สำนักงาน กสทช. ศูนย์รับแจ้งปัญหา 1200

Overall, this project uses **PyThaiNLP** for data preprocessing, **PhayaThaiBERT** for deep learning model
and use **Macro F1 score** for evaluation.

---

# Project Resources

| **Resource**                |                                              **Link**                                              |
| :-------------------------- | :------------------------------------------------------------------------------------------------: |
| Kaggle Dataset              | [`Link`](https://www.kaggle.com/datasets/worralopsrichainont/2110446-dsde-midterm-dataset-cleaned) |
| Raw Train Dataset           |             [`Link`](https://drive.google.com/uc?id=1viyCPfSO-3vCwEpEfS6KhinpFk9_Ozg2)             |
| Raw Test Dataset            |             [`Link`](https://drive.google.com/uc?id=1o0redlOH2bDN8iZqqBZVew7Bb80KIeXo)             |
| Cleaned Train Dataset       |             [`Link`](https://drive.google.com/uc?id=1b_UK7477inZgaCib2oH8pniF9R8EkIWU)             |
| Cleaned Test Dataset        |             [`Link`](https://drive.google.com/uc?id=1DIaNv7YWiFKhTSoSvaBZ4YRudal-3m51)             |
| Model Checkpoint            |             [`Link`](https://drive.google.com/uc?id=1twq0FrPmmeP9nU0m4JWdJGUOp-SwXCWF)             |
| Data Preprocessing Notebook |     [`Link`](https://www.kaggle.com/code/worralopsrichainont/2110446-dsde-midterm-preprocess)      |
| EDA Notebook                |         [`Link`](https://www.kaggle.com/code/worralopsrichainont/2110446-dsde-midterm-eda)         |
| Model Notebook              |        [`Link`](https://www.kaggle.com/code/worralopsrichainont/2110446-dsde-midterm-model)        |

---

# Conclusion

In summary, the objective of this project is to design the data pipeline and implement a deep learning model to classify
complaints text from Bangkok Traffy Fondue into the correct responsible government department.

For the data cleaning, this project uses Python pandas to load raw CSV file as a DataFrame,
then uses Python regex to find a pattern to remove or replace, and then uses PyThaiNLP to normalize
and encode the Thai text.

For the data pipeline, this project split the dataset into training dataset and validation dataset in 90:10 ratio
by using iterative stratification method to ensure the equality of class ratio in both dataset.
Next, we implement PyTorch DataModule to easily feed the data into a deep learning model as a batch.

For the deep learning model, this project uses PhayaThaiBERT model for classification. We load the pre-trained model,
set BCEWithLogitsLoss as a loss function and use Macro F1 score as an evaluation metric.
In addition, we also use Adam optimizer with dynamic learning rate.

For the fine-tuning process, this project dynamically adjust the probability threshold to convert logits score to class prediction
for improving the validation macro F1 score.

According to the validation result and submission result in Kaggle competition,
this model reaches 0.36637 Macro F1 Score on the public leaderboard
and 0.34254 Macro F1 Score on the private leaderboard which indicates that the model
is still not performing well on the minor classes, but performing satisfactorily on the major classes.
However, this model still needs improvement in the future as discussed in the discussion part.
