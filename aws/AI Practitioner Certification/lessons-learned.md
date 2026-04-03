# Lessons Learned

These lessons are annotations from practical exercises from [Whizlabs AWS Certified AI Practitioner](https://www.whizlabs.com/aws-certified-ai-practitioner/)

## Guidelines for Responsible AI

The benefits of using Amazon Bedrock over building and managing your own models is to reduce cost and complexity and have access to the latest cutting-edge models without the need for in-house expertise.

A SageMaker Model Card serves as a comprehensive documentation hub for a machine learning model to capture and communicate key information about the model, promoting transparency and facilitating responsible AI development and deployment which includes model's purpose, intended use, performance metrics, ethical considerations and relevant information that helps stakeholders understand and evaluate the model.

SageMaker real-time hosting services are specifically designed to provide persistent endpoints that are always available and ready to serve predictions with low latency. They are optimized for handling individual prediction requests in real time, making them ideal for applications that require immediate responses, such as chatbots, recommendations engines and fraud detection systems.

## Fundamentals of AI and ML

The N-gram transformation with a window size of 3 from the input _"This product is amazing and exceeded my expectations"_ is: ["This product is", "product is amazing", "is amazing and", "amazing and exceeded", "and exceeded my", "exceeded my expectations"]. A trigram is a sequence of three consecutive works.

One option of deploy in Amazon SageMaker is _Serverless Inference_ is the optimal choice for workloads characterized by fluctuating traffic patterns with idle periods. It automatically scales compute resources up or down based on demand. This makes it cost-effective for applications with unpredictable or intermittent use patterns;

There are some algorithms to optimize the model's performance by tuning its hyperparameters:
- Grid Search: it involves  defining a grid of possible hyperparameter values and systematically evaluating the model's performance for each combination of values. It is brute-force approach that can be computationally expensive but guarantees finding the best combination within the defined grid;
- Bayesian Optimization: It is an advanced method that leverages a probabilistic model to steer the search for optimal hyperparameters. It learns from past evaluations to select the next set of values to test;
- Random Search: It involves randomly sampling hyperparameter values from a defined range and evaluating the model's performance for each set of sampled values;

## Fundamentals of Gen AI

The benefits of using Gen AI in summarization of CloudWatch logs is:
- Accelerate incident triage by providing a concise overview of recent log events;
- Enable proactive identification of potential issues or anomalies;
- Facilitate better collaboration and communication among teams;

ROUGE (Recall-Oriented Understudy for Gisting Evaluation) is a widely adopted metric specifically designed for evaluating the quality of automatically summarization systems. It compares the generated summary against one or more human-written reference summaries and calculating the overlap of n-grams. Higher ROUGE score generally indicate a better match between the generated summary and the reference summaries.

The prompt technique for mitigate overly long and verbose responses is:
- Specify a concise response format in the prompt;
- Limit the model's token generation capacity;

## Applications of FMs

The Exploratory Data Analysis (EDA) is the investigative phase of the ML pipeline w
here you delve into your dataset to understand its structure, distributions and relationships between variables which involves visualizing the data through plots and charts, calculating summary statistics and identifying potential outliers or anomalies.

There are three techniques for model compression:
- Pruning: It involves removing redundant or less important parameters from the model, effectively deucing its size and computational requirements;
- Quantization: It reduces the precision of the model's weights, representing them with fewer bits. This leads to a smaller memory footprint and often faster inference, making it a common model compression technique;
- Distillation: It involves training  a smaller "student" model to mimic the behavior of a larger "teacher" model. This allows you to deploy a more compact and efficient model while retaining a significant portion of the original model's performance;

## Security, Compliance and Governance for AI Solutions

The Amazon Bedrock's data privacy does not use the customer data to train or improve the Bedrock Service or the underlying FMs. It means that data is kept confidential and used solely for your own applications.
