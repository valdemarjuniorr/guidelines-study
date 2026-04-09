# Lessons Learned

These lessons are annotations from practical exercises from [Whizlabs AWS Certified AI Practitioner](https://www.whizlabs.com/aws-certified-ai-practitioner/)

## Guidelines for Responsible AI

The benefits of using Amazon Bedrock over building and managing your own models is to reduce cost and complexity and have access to the latest cutting-edge models without the need for in-house expertise.

A SageMaker Model Card serves as a comprehensive documentation hub for a machine learning model to capture and communicate key information about the model, promoting transparency and facilitating responsible AI development and deployment which includes model's purpose, intended use, performance metrics, ethical considerations and relevant information that helps stakeholders understand and evaluate the model.

SageMaker real-time hosting services are specifically designed to provide persistent endpoints that are always available and ready to serve predictions with low latency. They are optimized for handling individual prediction requests in real time, making them ideal for applications that require immediate responses, such as chatbots, recommendations engines and fraud detection systems.

To enhance a chatbot's capabilities is using Retrieval Augmented Generation(RAG) to enhance the responses with relevant and factual information from their knowledge base.

The knowledge base in Retrieval-Augmented Generation(RAG) is act as a source of domain-specific information for the model to reference during the generation process.

Throughput allows the company to reserve a specific capacity  for their Bedrock models, ensuring that they can handle the increased traffic even during peak periods. This eliminates the risk of delays and provides a consistent experience for customers.

Those factors are crucial to a AI technology to be considered trustworthy: `Fairness`, `Transparency`, `Accountability` and `Privacy`.

Red teaming is an adversarial approach specifically aimed at proactively identifying weaknesses and vulnerabilities in a system. It involves simulating real-world attacks and adversarial scenarios to expose potential flaws that might be exploited my malicious actors or lead to unintended harmful consequences.

## Fundamentals of AI and ML

The N-gram transformation with a window size of 3 from the input _"This product is amazing and exceeded my expectations"_ is: ["This product is", "product is amazing", "is amazing and", "amazing and exceeded", "and exceeded my", "exceeded my expectations"]. A trigram is a sequence of three consecutive works.

One option of deploy in Amazon SageMaker is _Serverless Inference_ is the optimal choice for workloads characterized by fluctuating traffic patterns with idle periods. It automatically scales compute resources up or down based on demand. This makes it cost-effective for applications with unpredictable or intermittent use patterns;

There are some algorithms to optimize the model's performance by tuning its hyperparameters:
- Grid Search: it involves  defining a grid of possible hyperparameter values and systematically evaluating the model's performance for each combination of values. It is brute-force approach that can be computationally expensive but guarantees finding the best combination within the defined grid;
- Bayesian Optimization: It is an advanced method that leverages a probabilistic model to steer the search for optimal hyperparameters. It learns from past evaluations to select the next set of values to test;
- Random Search: It involves randomly sampling hyperparameter values from a defined range and evaluating the model's performance for each set of sampled values;

Amazon Transcribe is specifically designed for automatic speech recognition(ASR), making it the ideal choice for converting spoken language in videos into text that can then be analyzed by LLMs or other AI models.

In Amazon Rekognition there is a feature designed for detecting scene changes in videos by identifying these transitions, you can efficiently capture representative frames from each scene, avoiding redundant processing and ensuring that captions are generated for the most relevant parts of the video.

The best ML algorithm to predict customer churn is _Decision tree_ and _Support Vector Machine(SVM). Decision tree are well-suited for classification tasks and can handle both numerical and categorical data. Support Vector Machine(SVM) are powerful classification algorithms that can handle high-dimensional data and non-linear relationships, making them effective for binary classification problems like churn prediction, especially when the data is well-separated.

Amazon SageMaker K-Means clustering algorithm is specifically designed for unsupervised learning tasks like customer segmentation. It can analyze customer spending patterns in Redshift, for example, and identify distinct groups of clusters.

The k-NN (k-Nearest Neighbors) plugin is specifically designed to extend the capabilities of Amazon OpenSearch Service by enabling efficient k-nearest neighbor search. This type of serach is fundamental for finding documents or items that are most similar to a given query, based on their vector embeddings.

## Fundamentals of Gen AI

The benefits of using Gen AI in summarization of CloudWatch logs is:
- Accelerate incident triage by providing a concise overview of recent log events;
- Enable proactive identification of potential issues or anomalies;
- Facilitate better collaboration and communication among teams;

ROUGE (Recall-Oriented Understudy for Gisting Evaluation) is a widely adopted metric specifically designed for evaluating the quality of automatically summarization systems. It compares the generated summary against one or more human-written reference summaries and calculating the overlap of n-grams. Higher ROUGE score generally indicate a better match between the generated summary and the reference summaries.

The prompt technique for mitigate overly long and verbose responses is:
- Specify a concise response format in the prompt;
- Limit the model's token generation capacity;

The technique to enhance the accuracy and reliability of Gen AI models in summarizing customer reviews and extracting actions is _Prompt engineering_ and _Fine-tuning the foundation models on domain-specific data_.

The combination best support the goal of boosting agent productivity and reducing after-call work using Gen AI is _Amazon Q in Connect_ which is a Gen AI assistant embedded in Amazon Connect that helps agents by providing real-time guidance, summarizing conversations and automating post-call documentation. The _Amazon Connect Contact Lens_ provides real-time analytics, sentiment analysis and transcription, which enhance the context and accuracy of generative AI outputs.

The differences between Few-shot prompting and Zero-shot prompting are:
- `Few-shot prompting`: It incorporates examples to guide the model.
- `Zero-shot prompting`: It relies solely on the model's pre-existing knowledge without providing any examples, making it more challenging for the model to generate accurate responses, especially for complex tasks or those requiring specific domain knowledge.

Amazon Comprehend is the natural language processing(NLP) designed to extract insights from text, including sentiment analysis and key phrase extraction. This makes it the ideal choice for analyzing customer reviews and understanding their opinions.

`AutoML` refers the automation of typical steps in the model development workflow, eliminating often tedious and time-consuming steps involved in building ML models, such as data preprocessing, feature engineering, algorithm selection, hyperparameter tuning and even model evaluation.

The concept of `knowledge cutoff` is when an LLM provides outdated information about a recent event.

The best algorithm for customer churn prediction is Decision Tree and Support Vector Machine(SVM). Decision Tree are well-suited for classification tasks and can handle both numerical and categorical data. Support Vector Machine(SVM) are powerful classification algorithms that can handle high-dimensional data and non-linear relationships. Effective for binary classification problems like churn prediction, especially when the data is well-separated.

Amazon SageMaker's K-Means clustering algorithm is specifically designed for unsupervised learning tasks like customer segmentation. It can analyze customer spending patterns in Redshift and identify distinct groups or clusters.

## Applications of FMs

The Exploratory Data Analysis (EDA) is the investigative phase of the ML pipeline where you delve into your dataset to understand its structure, distributions and relationships between variables which involves visualizing the data through plots and charts, calculating summary statistics and identifying potential outliers or anomalies.

There are three techniques for model compression:
- Pruning: It involves removing redundant or less important parameters from the model, effectively deucing its size and computational requirements;
- Quantization: It reduces the precision of the model's weights, representing them with fewer bits. This leads to a smaller memory footprint and often faster inference, making it a common model compression technique;
- Distillation: It involves training  a smaller "student" model to mimic the behavior of a larger "teacher" model. This allows you to deploy a more compact and efficient model while retaining a significant portion of the original model's performance;

The context of FM the key application is enable the creation of Account Summaries, providing comprehensive and personalized insights into customer accounts by integrating data from various sources.

Those AWS services support storing and querying vector embeddings: Amazon S3 with S3 Vectors, Amazon OpenSearch Service and Amazon RDS for PostgreSQL with pgvector extension.

The purpose of Diffusion in a diffusion model is a process where Gaussian noise is gradually added to the original image over multiple steps. This creates a sequence of increasingly noisy images, culminating in an image that is almost pure noise.

The role of _Amazon Multimodel Embeddings G1_ is specifically designed to generate numerical representations(embeddings) for both textual and visual data.

The optimal number of epochs for fine-tuning is _Validation output accuracy_ and _Validation Loss_. This metric directly measure how well your model is performing on unseen data. A higher validation accuracy generally indicates a better model.

The deployment strategy as known as `Shadow Deployment` is a technique where the new model version runs in parallel with the existing one, receiving the same input, but its output is not sent back to the user. Instead, the output is typically logged or analyzed offline

Amazon SageMaker Autoscaling Policies are designed to automatic scaling of SageMaker endpoints based on predefined metrics and thresholds.

`Quantization` is the process of reducing the number of bits used to represent the model's wights and activations to reduce the memory footprint of the model, enabling faster loading and inference, especially on resource-constrained devices.

## Security, Compliance and Governance for AI Solutions

The Amazon Bedrock's data privacy does not use the customer data to train or improve the Bedrock Service or the underlying FMs. It means that data is kept confidential and used solely for your own applications.

CloudTrail Lake is managed data lake taht allows users to store and query CloudTrail events using SQL-like syntax. Customers can ingest CloudTrail events into CLoudTrail Lake to analyze API Activity, including user interactions with _Amazon Bedrock_.

In a multi-tenant applications which uses DynamoDB table the best approach to ensure which tentant access only their own data is through IAM policies. It involves providing each business with unique credentials that have permissions restricted to their specific data in DynamoDB, enforcing access control directly at the database level, ensuring strong data isolation between tenants.

The ensure the secure connectivity between your application and Amazon Bedrock you can use AWS VPC Endpoints which enables establish a private connection. This ensure that your data travels within the secure AWS network backbone, avoiding the public internet.

In the AWS Shared Responsibility Model, customers are responsible for the security of their applications and the data they process within those applications. It includes protecting against prompt injection, which involves carefully handling user input and implementing secure coding practices.
