# Problem Statement

Misinformation and Fake news have become a serious issue to consider. With such a numerous amount of people using social media in today's digital society, information spreads incredibly fast—often without being verified. As a result, misleading information can reach over hundreds of thousands of people within minutes, causing confusion,or even worse, a real-world disaster.

Many existing machine learning models are unable to keep up with this issue, especially when different types of fake news or misinformation appear. At the same time, relying on people to manually verify every piece of information is not practical as it takes too much time and effort.

To tackle this, our project proposes a hybrid fake news detection system. The idea is to combine a deep learning model, which can analyze and classify news content, with real-time verification from trusted online sources. To put it in another way, the system doesn’t just rely on patterns it has learned before, it also checks whether the information actually matches reliable data available on the internet.

This combination makes the system be both fast and versatile, making it more effective at identifying fake news as it evolves.

# Objective

The main objectives of this project are as follows:

1. Develop a machine learning model which is capable of categorizing news articles as genuine(Real) or misinformed(Fake).
2. Improve and work on a DistilBERT transformer model working on the WELFake dataset.
3. Evaluation of model performance using accuracy, precision, recall-ability, and F1-score.
4. Integrate online verification of the result provided by the model via:

   * Wikipedia API
   * GNews API
   * Google Fact Check Tools API
5. Build a hybrid prediction system that combines AI classification with real-time fact verification.
6. Provide a Streamlit-based user interface for end-users to test and verify news(Information).

# Scope of the Project

In this project, I primarily sought out on finding misinformation(fake news) in textual form. Information which is in the form of images, videos, or other types of content were not included, even though they form a major part of the misinformation spread. The system was also designed to work on a single language(English), which means it is not suitable for content in other languages.

To test the veracity of the news, I used third-party APIs to search the information online. The Hybrid system helped improve the system’s reliability, but it also came with a few limitations. I utilized the free versions of these APIs for my work, thus, there were restrictions on how much I could use them. So while the system worked well, it had to operate within those limits until or unless an upgraded or paid services is used later on.


# Expected Outcomes

1. A DistilBERT model was trained to classify news with a high level of accuracy.
2. A hybrid verification system was developed to cross-check the authenticity of news using online sources.
3. An effective and user-friendly Streamlit application was created to enable real-time testing.
4. A performance report was generated, including metrics such as accuracy, precision, recall-ability, F1-score, and a confusion matrix.
5. An overall improvement in reliability was observed when detecting fake news compared to a standalone machine learning model.
