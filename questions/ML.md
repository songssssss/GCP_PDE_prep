Question 40

You work for a shipping company that has distribution centers where packages move on delivery lines to route them properly. The company wants to add cameras to the delivery lines to detect and track any visual damage to the packages in transit. You need to create a way to automate the detection of damaged packages and flag them for human review in real time while the packages are in transit.

Which solution should you choose?
Use BigQuery machine learning to be able to train the model at scale, so you can analyze the packages in batches.
Train an AutoML model on your corpus of images, and build an API around that model to integrate with the package tracking applications.
Use the Cloud Vision API to detect for damage, and raise an alert through Cloud Functions. Integrate the package tracking applications with this function.
Use TensorFlow to create a model that is trained on your corpus of images. Create a Python notebook in Cloud Datalab that uses this model so you can analyze for damaged packages.




Answer is B. Train an AutoML model on your corpus of images, and build an API around that model to integrate with the package tracking applications.

For this scenario, where you need to automate the detection of damaged packages in real time while they are in transit, the most suitable solution among the provided options would be B.

Here's why this option is the most appropriate:

Real-Time Analysis: AutoML provides the capability to train a custom model specifically tailored to recognize patterns of damage in packages. This model can process images in real-time, which is essential in your scenario.

Integration with Existing Systems: By building an API around the AutoML model, you can seamlessly integrate this solution with your existing package tracking applications. This ensures that the system can flag damaged packages for human review efficiently.

Customization and Accuracy: Since the model is trained on your specific corpus of images, it can be more accurate in detecting damages relevant to your use case compared to pre-trained models.

Let's briefly consider why the other options are less suitable:
A. Use BigQuery machine learning: BigQuery is great for handling large-scale data analytics but is not optimized for real-time image processing or complex image recognition tasks like damage detection on packages.

C. Use the Cloud Vision API: While the Cloud Vision API is powerful for general image analysis, it might not be as effective for the specific task of detecting damage on packages, which requires a more customized approach.

D. Use TensorFlow in Cloud Datalab: While this is a viable option for creating a custom model, it might be more complex and time-consuming compared to using AutoML. Additionally, setting up a real-time analysis system through a Python notebook might not be as straightforward as an API integration.
