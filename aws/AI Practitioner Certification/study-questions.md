# AWS AI Practitioner Certification - Study Questions

## Chapter 1: AI and ML Fundamentals

### Question 1
**What is the main difference between Generative AI and traditional AI?**

<details>
<summary>Answer</summary>

Generative AI is a subset of AI that specifically focuses on creating new content (text, images, audio, code) from existing data. Traditional AI encompasses broader tasks like problem-solving, decision-making, and natural language understanding, but doesn't necessarily create new content.
</details>

---

### Question 2
**What are the three broad categories of Machine Learning?**

<details>
<summary>Answer</summary>

1. **Supervised Learning**: Algorithms trained on labeled data to learn a mapping function
2. **Unsupervised Learning**: Algorithms that learn from unlabeled data to discover patterns
3. **Reinforcement Learning**: Given only a performance score as guidance, learns through rewards or penalties
</details>

---

### Question 3
**What is the relationship between Deep Learning and Generative AI?**

<details>
<summary>Answer</summary>

Generative AI is a subset of deep learning. It can adapt models built using deep learning techniques without retraining or fine-tuning the model.
</details>

---

### Question 4
**What are Foundation Models (FMs)?**

<details>
<summary>Answer</summary>

Foundation Models are large-scale models that are pre-trained on internet-scale data and can be adapted to perform multiple tasks such as text generation, image generation, and code generation.
</details>

---

### Question 5
**Describe the key difference between RAG and Fine-Tuning.**

<details>
<summary>Answer</summary>

**RAG (Retrieval-Augmented Generation)**: Supplies domain-relevant data as context by retrieving a small set of relevant documents to answer user prompts. Does not require model retraining.

**Fine-Tuning**: Involves further training a pre-trained model on a specific task or domain-specific dataset, updating model parameters.
</details>

---

## Chapter 2: AWS AI Services

### Question 6
**What is the primary purpose of Amazon SageMaker?**

<details>
<summary>Answer</summary>

Amazon SageMaker is a fully managed ML service that allows you to build, train, and deploy ML models for any use case with fully managed infrastructure, tools, and workflows. It removes the heavy lifting from each step of the ML process.
</details>

---

### Question 7
**Which AWS service would you use for sentiment analysis of customer reviews?**

<details>
<summary>Answer</summary>

**Amazon Comprehend** - It uses ML and natural language processing (NLP) to understand how positive or negative text is, extract key phrases, and identify entities.
</details>

---

### Question 8
**What is Amazon Bedrock used for?**

<details>
<summary>Answer</summary>

Amazon Bedrock is a fully managed service that makes Foundation Models from Amazon and leading AI startups available through an API. It allows you to experiment with FMs, privately customize them with your own data, and seamlessly integrate them into applications without managing infrastructure.
</details>

---

### Question 9
**What is the difference between Amazon Transcribe and Amazon Polly?**

<details>
<summary>Answer</summary>

**Amazon Transcribe**: Converts speech to text (Automatic Speech Recognition - ASR)

**Amazon Polly**: Converts text to speech (Text-to-Speech - TTS)
</details>

---

### Question 10
**Which AWS service enables intelligent search capabilities?**

<details>
<summary>Answer</summary>

**Amazon Kendra** - An intelligent search service powered by ML that reimagines enterprise search for websites and applications. It can connect to various data sources to deliver accurate and relevant search results.
</details>

---

### Question 11
**What is SageMaker JumpStart?**

<details>
<summary>Answer</summary>

SageMaker JumpStart helps you quickly get started with ML by providing pre-built solutions for common use cases. It supports one-click deployment and fine-tuning of more than 150 popular open-source models for tasks like NLP, object detection, and image classification.
</details>

---

### Question 12
**Which service would you use for real-time video analysis?**

<details>
<summary>Answer</summary>

**Amazon Rekognition** - It facilitates adding image and video analysis to applications using proven, highly scalable, deep learning-based technology.
</details>

---

## Chapter 3: Responsible AI

### Question 13
**What are the core dimensions of Responsible AI?**

<details>
<summary>Answer</summary>

1. **Fairness**: Prevent discrimination and promote inclusion
2. **Explainability**: Ability to clearly explain model decisions
3. **Privacy and Security**: Protect data from theft and exposure
4. **Transparency**: Communicate information about AI systems
5. **Veracity and Robustness**: Ensure reliable operation
6. **Governance**: Processes to enforce responsible AI practices
7. **Safety**: Develop algorithms responsibly
8. **Controllability**: Ability to monitor and guide AI behavior
</details>

---

### Question 14
**What is the difference between Bias and Variance in ML models?**

<details>
<summary>Answer</summary>

**Bias**: Error from missing important features or oversimplification. High bias means the model is too basic and has wide difference between predictions and true values.

**Variance**: Model's sensitivity to fluctuations in training data. High variance leads to overfitting - the model performs well on training data but poorly on new data.

A balanced model has low bias and low variance.
</details>

---

### Question 15
**What is the purpose of Amazon SageMaker Model Cards?**

<details>
<summary>Answer</summary>

SageMaker Model Cards serve as comprehensive documentation for ML models, capturing key information such as intended uses, risk ratings, training details, performance metrics, and ethical considerations. They promote transparency and facilitate responsible AI development and deployment.
</details>

---

### Question 16
**What is Red Teaming in AI security?**

<details>
<summary>Answer</summary>

Red teaming is an adversarial approach that proactively identifies weaknesses and vulnerabilities in AI systems by simulating real-world attacks and adversarial scenarios to expose potential flaws that might be exploited or lead to harmful consequences.
</details>

---

### Question 17
**What does "Jailbreaking" a Foundation Model mean?**

<details>
<summary>Answer</summary>

Jailbreaking refers to manipulating a model through crafted prompts to bypass its safety mechanisms and generate responses it would normally restrict, such as offensive, harmful, or unethical content.
</details>

---

## Chapter 4: ML Model Development and Evaluation

### Question 18
**What are the stages of the ML Lifecycle?**

<details>
<summary>Answer</summary>

1. Business goal identification
2. ML problem framing
3. Data processing (collection, preprocessing, feature engineering)
4. Model development (training, tuning, evaluation)
5. Model deployment (inference and prediction)
6. Model monitoring
7. Model retraining
</details>

---

### Question 19
**What is the difference between Precision and Recall?**

<details>
<summary>Answer</summary>

**Precision**: Focuses on minimizing false positives. High precision means fewer incorrect positive predictions. Important when the cost of false positives is high (e.g., spam detection).

**Recall**: Focuses on minimizing false negatives. High recall means fewer missed actual positives. Important when the cost of false negatives is high (e.g., medical diagnosis).

There is a trade-off - improving one can decrease the other.
</details>

---

### Question 20
**What are common evaluation metrics for Classification vs Regression?**

<details>
<summary>Answer</summary>

**Classification**: Accuracy, Precision, Recall, F1 Score, AUC-ROC

**Regression**: Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Square Error (RMSE), R-squared
</details>

---

### Question 21
**What is MLOps?**

<details>
<summary>Answer</summary>

MLOps combines people, technology, and processes to deliver collaborative ML solutions. It refers to practices that operationalize and streamline the end-to-end ML lifecycle from development and deployment to monitoring and maintenance. It combines ML, DevOps, and Data Engineering to automate the ML lifecycle.
</details>

---

### Question 22
**What is the purpose of SageMaker Feature Store?**

<details>
<summary>Answer</summary>

SageMaker Feature Store helps data scientists create, share, and manage features for ML development, enabling feature reusability and consistency across different models and teams.
</details>

---

## Chapter 5: Foundation Model Optimization

### Question 23
**What are the five techniques to improve Foundation Model performance?**

<details>
<summary>Answer</summary>

1. **Prompt Engineering**: Adjust model behavior through well-crafted prompts
2. **Prompt Techniques**: Strategies to guide generative AI models
3. **Retrieval-Augmented Generation (RAG)**: Combine retrieval systems with generative models
4. **Fine-Tuning**: Further train pre-trained models on specific datasets
5. **Creating from Scratch**: Train completely new model architecture (used when no suitable pre-trained models exist)
</details>

---

### Question 24
**What is the difference between Temperature and Top P parameters?**

<details>
<summary>Answer</summary>

**Temperature**: Controls randomness/creativity. Higher values (e.g., 1.0) produce more random and creative outputs; lower values (e.g., 0.2) produce more focused and deterministic outputs.

**Top P**: Controls diversity by selecting from the smallest set of words whose cumulative probability exceeds threshold P. Low Top P = focused output; High Top P = diverse output.
</details>

---

### Question 25
**What is the purpose of Stop Sequences in inference?**

<details>
<summary>Answer</summary>

Stop Sequences are special tokens that signal the model to stop generating further output. When encountered during inference, the model terminates generation regardless of maximum length setting.
</details>

---

### Question 26
**What is ROUGE metric used for?**

<details>
<summary>Answer</summary>

ROUGE (Recall-Oriented Understudy for Gisting Evaluation) is used to evaluate the quality of text generation, particularly summarization. It measures the overlap of n-grams, word sequences, and word pairs between generated text and reference texts. Higher ROUGE scores indicate better quality summaries.
</details>

---

### Question 27
**What is BLEU score?**

<details>
<summary>Answer</summary>

BLEU (Bilingual Evaluation Understudy) evaluates machine-generated translations by comparing them to human reference translations. It measures the precision of n-grams in generated translation against reference translations.
</details>

---

### Question 28
**What is BERTScore?**

<details>
<summary>Answer</summary>

BERTScore evaluates generated text quality using contextual embeddings from the BERT model. It measures semantic similarity between generated and reference texts based on their contextual representations, making it useful for evaluating stories, articles, and other creative content.
</details>

---

## Chapter 6: Prompt Engineering

### Question 29
**What is the difference between Zero-shot and Few-shot prompting?**

<details>
<summary>Answer</summary>

**Zero-shot Prompting**: Relies solely on the model's pre-existing knowledge without providing any examples. More challenging for complex tasks.

**Few-shot Prompting**: Incorporates examples to guide the model, making it easier to generate accurate responses for specific tasks.
</details>

---

### Question 30
**What techniques can mitigate overly long responses from Foundation Models?**

<details>
<summary>Answer</summary>

1. Specify a concise response format in the prompt
2. Limit the model's token generation capacity using Maximum Length parameter
</details>

---

### Question 31
**What is the purpose of Top K parameter?**

<details>
<summary>Answer</summary>

Top K controls diversity by limiting selection to the top K most probable words. Low Top K = focused and predictable output; High Top K = more diverse and creative output by considering more candidate words.
</details>

---

## Chapter 7: Advanced ML Concepts

### Question 32
**What is an N-gram?**

<details>
<summary>Answer</summary>

An N-gram is a sequence of N consecutive words. For example, with window size 3 (trigram), the sentence "This product is amazing" would produce: ["This product is", "product is amazing", "is amazing and"].
</details>

---

### Question 33
**What are three hyperparameter optimization algorithms?**

<details>
<summary>Answer</summary>

1. **Grid Search**: Systematically evaluates all combinations in a defined grid (brute-force, guarantees finding best combination)
2. **Random Search**: Randomly samples hyperparameter values from defined ranges
3. **Bayesian Optimization**: Uses probabilistic model to intelligently guide the search based on past evaluations
</details>

---

### Question 34
**What is K-Means Clustering used for?**

<details>
<summary>Answer</summary>

K-Means is an unsupervised learning algorithm for customer segmentation and grouping. It partitions n observations into k clusters where each observation belongs to the cluster with the nearest mean. It's ideal for identifying patterns in data like customer spending behaviors.
</details>

---

### Question 35
**What is the role of an Agent in Reinforcement Learning?**

<details>
<summary>Answer</summary>

The agent is the core decision-maker that interacts with the environment, observes states, takes actions based on its policy, and receives rewards or penalties. Its goal is to learn from experiences and improve its policy over time to maximize cumulative reward.
</details>

---

### Question 36
**What is A/B Testing in ML model deployment?**

<details>
<summary>Answer</summary>

A/B testing conducts controlled experiments by directing a portion of live traffic to a new model variant while the majority goes to the existing model. This enables data-driven decisions about whether to fully adopt the new model based on real-world performance.
</details>

---

### Question 37
**What is Computer Vision?**

<details>
<summary>Answer</summary>

Computer Vision is a field of AI that enables computers to "see" and interpret images. It involves techniques for analyzing visual information to extract relevant features, making it ideal for applications like automatic image tagging and categorization.
</details>

---

## Chapter 8: Model Compression and Optimization

### Question 38
**What are three techniques for model compression?**

<details>
<summary>Answer</summary>

1. **Pruning**: Removing redundant or less important parameters to reduce size
2. **Quantization**: Reducing precision of model weights (fewer bits) for smaller memory footprint and faster inference
3. **Distillation**: Training a smaller "student" model to mimic a larger "teacher" model while retaining performance
</details>

---

### Question 39
**What is the difference between Fine-tuning and Parameter-Efficient Fine-Tuning (PEFT)?**

<details>
<summary>Answer</summary>

**Fine-tuning**: Updates all parameters of the pre-trained model. Computationally expensive and memory-intensive.

**PEFT**: Updates only a small subset of parameters or adds new parameters efficiently, leading to significant resource savings while maintaining performance.
</details>

---

### Question 40
**What is Shadow Deployment?**

<details>
<summary>Answer</summary>

Shadow Deployment is a technique where the new model version runs in parallel with the existing one, receiving the same input, but its output is not sent to users. Instead, outputs are logged or analyzed offline to evaluate performance before full deployment.
</details>

---

## Chapter 9: Specialized ML Algorithms

### Question 41
**When would you use Decision Trees and Support Vector Machines?**

<details>
<summary>Answer</summary>

Both are suitable for **classification tasks** like customer churn prediction. Decision Trees handle both numerical and categorical data well. SVMs are powerful for high-dimensional data and non-linear relationships, especially effective when data is well-separated.
</details>

---

### Question 42
**What is the k-NN algorithm used for?**

<details>
<summary>Answer</summary>

k-Nearest Neighbors enables efficient similarity search by finding documents or items most similar to a query based on their vector embeddings. It's commonly used in search engines like Amazon OpenSearch Service for finding related content.
</details>

---

### Question 43
**What is Word2Vec algorithm?**

<details>
<summary>Answer</summary>

Word2Vec learns word representations (embeddings) that capture semantic and syntactic relationships between words. It allows AI to understand relationships based on context, such as "King" - "man" + "woman" = "queen".
</details>

---

### Question 44
**What is the difference between Linear Regression and K-Means Clustering?**

<details>
<summary>Answer</summary>

**Linear Regression**: Supervised learning algorithm that finds linear relationships between dependent and independent variables. Requires labeled data.

**K-Means Clustering**: Unsupervised learning algorithm that groups data based on inherent similarities without labeled data.
</details>

---

## Chapter 10: AWS Security and Governance

### Question 45
**What AWS services help secure AI systems?**

<details>
<summary>Answer</summary>

1. **AWS Security Hub**: Centralized security management and monitoring
2. **AWS KMS**: Encrypts data with AWS managed or customer-managed keys
3. **Amazon GuardDuty**: Threat detection monitoring for suspicious activity
4. **AWS Shield Advanced**: Protection against DDoS events, includes WAF and Firewall Manager
</details>

---

### Question 46
**What are the four security best practices for AI?**

<details>
<summary>Answer</summary>

1. **Principle of Least Privilege**: Grant only necessary permissions
2. **Defense in Depth**: Multiple security layers (network, encryption, access control)
3. **Regular Security Assessments**: Conduct audits and vulnerability scans
4. **Security Training**: Train teams on AI security best practices
</details>

---

### Question 47
**What AWS services support data governance for AI?**

<details>
<summary>Answer</summary>

1. **Amazon DataZone**: Create data catalog and manage access policies
2. **AWS Glue Data Catalog**: Organize, discover, and share data assets
3. **Amazon Macie**: Discover and protect sensitive data
4. **AWS Lake Formation**: Build secure data lakes and manage permissions
</details>

---

### Question 48
**What are the key governance strategies for Responsible AI?**

<details>
<summary>Answer</summary>

1. **Policies**: Clear guidelines for generative AI usage
2. **Review Cadence**: Regular assessment of performance and safety
3. **Review Strategies**: Comprehensive technical and non-technical evaluations
4. **Transparency Standards**: High standards for AI development transparency
5. **Team Training**: Adequate training on policies and best practices
</details>

---

### Question 49
**How does AWS Shared Responsibility Model apply to AI?**

<details>
<summary>Answer</summary>

Customers are responsible for:
- Security of their applications
- Data processing security
- Protection against prompt injection
- Secure coding practices
- Handling user input securely
</details>

---

### Question 50
**What is the purpose of AWS PrivateLink with Amazon Bedrock?**

<details>
<summary>Answer</summary>

AWS PrivateLink enables private connection between applications and Amazon Bedrock, ensuring data travels within the secure AWS network backbone without traversing the public internet. This provides enhanced security and compliance.
</details>

---

## Chapter 11: Specialized AWS Services

### Question 51
**What is Amazon Q and its variants?**

<details>
<summary>Answer</summary>

**Amazon Q**: AI assistant that provides answers, solves problems, generates content, and takes actions using company data and expertise.

**Amazon Q Developer**: Specifically designed for developer productivity, providing ML-powered code recommendations to accelerate development.
</details>

---

### Question 52
**What is AWS DeepRacer?**

<details>
<summary>Answer</summary>

AWS DeepRacer is a 1/18th scale race car that provides an engaging way to learn reinforcement learning (RL). It learns complex behaviors without labeled training data and can make short-term decisions while optimizing for long-term goals.
</details>

---

### Question 53
**When would you use SageMaker Serverless Inference?**

<details>
<summary>Answer</summary>

Serverless Inference is optimal for workloads with fluctuating traffic patterns and idle periods. It automatically scales compute resources based on demand, making it cost-effective for unpredictable or intermittent use patterns.
</details>

---

### Question 54
**What is the purpose of SageMaker Ground Truth?**

<details>
<summary>Answer</summary>

SageMaker Ground Truth facilitates human-in-the-loop ML tasks, including collecting and managing human feedback for techniques like Reinforcement Learning from Human Feedback (RLHF). It helps improve model alignment with human values.
</details>

---

### Question 55
**What does Amazon Comprehend do?**

<details>
<summary>Answer</summary>

Amazon Comprehend uses ML and NLP to:
- Identify language of text
- Extract key phrases, places, people, brands, events
- Analyze sentiment (positive/negative)
- Perform tokenization and parts of speech analysis
- Organize text files by topic
</details>

---

## Chapter 12: Model Evaluation Metrics

### Question 56
**What is the F1 Score?**

<details>
<summary>Answer</summary>

F1 Score is the harmonic mean of Precision and Recall, providing a balanced measure when you need to consider both false positives and false negatives. It's useful for imbalanced datasets where accuracy alone would be misleading.
</details>

---

### Question 57
**What is AUC-ROC?**

<details>
<summary>Answer</summary>

Area Under the ROC Curve (AUC) evaluates classification models by measuring the trade-off between true positive rate (sensitivity) and false positive rate (1-specificity). Higher AUC indicates better model performance at distinguishing between classes across different thresholds.
</details>

---

### Question 58
**What is Perplexity used for?**

<details>
<summary>Answer</summary>

Perplexity measures the probability of a model generating a given sequence of words. Commonly used for language models, where lower perplexity indicates better fit to the data. It assesses how "surprised" the model is by the test data.
</details>

---

### Question 59
**What is Inception Score (IS)?**

<details>
<summary>Answer</summary>

Inception Score measures quality and diversity of generated images based on their classification by an Inception network. Higher scores indicate better image quality and variety.
</details>

---

### Question 60
**What is Fréchet Inception Distance (FID)?**

<details>
<summary>Answer</summary>

FID measures the distance between the distribution of generated images and real images in the feature space. Lower FID scores indicate generated images are more similar to real images in terms of quality and diversity.
</details>

---

## Chapter 13: Advanced Techniques

### Question 61
**What is Exploratory Data Analysis (EDA)?**

<details>
<summary>Answer</summary>

EDA is the investigative phase of the ML pipeline where you explore datasets to understand structure, distributions, and variable relationships. It involves visualizing data, calculating statistics, and identifying outliers or anomalies.
</details>

---

### Question 62
**What is AutoML?**

<details>
<summary>Answer</summary>

AutoML automates typical model development workflow steps including data preprocessing, feature engineering, algorithm selection, hyperparameter tuning, and model evaluation. It eliminates tedious and time-consuming manual steps in building ML models.
</details>

---

### Question 63
**What is Knowledge Cutoff in LLMs?**

<details>
<summary>Answer</summary>

Knowledge Cutoff refers to the limitation where an LLM provides outdated information about recent events because its training data only includes information up to a specific date. The model has no knowledge of events after its training cutoff date.
</details>

---

### Question 64
**What are three ways human feedback is used in Human-in-the-Loop (HITL)?**

<details>
<summary>Answer</summary>

1. Fine-tune LLMs and improve performance
2. Identify potential biases or inconsistencies
3. Track changes in model performance over time
</details>

---

### Question 65
**What are Reranking Algorithms?**

<details>
<summary>Answer</summary>

Reranking algorithms refine initial search results by prioritizing documents that are both highly relevant and diverse in content. This reduces redundancy and improves overall search quality by ensuring users receive a broader range of pertinent information.
</details>

---

## Chapter 14: Model Architecture Concepts

### Question 66
**What is Self-Attention in Transformers?**

<details>
<summary>Answer</summary>

Self-attention is at the heart of Transformer architecture, allowing models to understand context and relationships within sequences. It computes weighted representations by letting every token interact with all other tokens simultaneously, enabling the model to focus on relevant parts of the input.
</details>

---

### Question 67
**What are Encoder-Decoder Models used for?**

<details>
<summary>Answer</summary>

Encoder-Decoder models are well-suited for text summarization and machine translation. The encoder processes and captures the meaning of the input sequence, while the decoder generates the output sequence based on the encoded representation.
</details>

---

### Question 68
**What is the Diffusion process in image generation?**

<details>
<summary>Answer</summary>

Diffusion is a process where Gaussian noise is gradually added to original images over multiple steps, creating increasingly noisy versions. The model learns to reverse this process, generating images from noise.
</details>

---

### Question 69
**What is the role of Amazon Multimodal Embeddings G1?**

<details>
<summary>Answer</summary>

Amazon Multimodal Embeddings G1 is specifically designed to generate numerical representations (embeddings) for both textual and visual data, enabling cross-modal search and understanding.
</details>

---

## Chapter 15: Specialized Features and Tools

### Question 70
**What is Amazon Rekognition Custom Labels?**

<details>
<summary>Answer</summary>

Rekognition Custom Labels allows training custom image classification models using your own labeled dataset stored in S3. It enables creating models tailored to specific use cases that can recognize application-relevant objects or scenes.
</details>

---

### Question 71
**What is the purpose of scene detection in Amazon Rekognition?**

<details>
<summary>Answer</summary>

Scene detection identifies transitions in videos, efficiently capturing representative frames from each scene. This avoids redundant processing and ensures captions or analysis are generated for the most relevant parts of the video.
</details>

---

### Question 72
**What does SageMaker Inference Recommender do?**

<details>
<summary>Answer</summary>

SageMaker Inference Recommender automates load testing and benchmarking across various SageMaker instance types and endpoint configurations. It evaluates model performance (latency, throughput) and recommends the best cost-performance match, avoiding manual trial-and-error.
</details>

---

### Question 73
**What is SageMaker Clarify used for?**

<details>
<summary>Answer</summary>

SageMaker Clarify helps identify and address potential biases in ML models. It provides tools for analyzing model behavior, understanding feature importance, and generating explanations for predictions to ensure fairness and transparency.
</details>

---

### Question 74
**What is SageMaker Automatic Model Tuning?**

<details>
<summary>Answer</summary>

SageMaker Automatic Model Tuning automates finding the best hyperparameters for ML models. It runs multiple training jobs with different hyperparameter combinations and selects the model with best performance based on defined objective metrics.
</details>

---

## Chapter 16: RAG and Knowledge Bases

### Question 75
**How does RAG work with Amazon Bedrock Knowledge Bases?**

<details>
<summary>Answer</summary>

RAG with Knowledge Bases enables Gen AI with context injection using enterprise data (like documents in S3). It:
- Requires no fine-tuning
- Provides fully managed setup without infrastructure maintenance
- Reduces hallucinations by grounding responses in factual data
- Works out-of-the-box with top FMs like Claude, Llama 3, and Titan
</details>

---

### Question 76
**What role does k-NN play in Amazon OpenSearch with RAG?**

<details>
<summary>Answer</summary>

The k-NN plugin enables efficient k-nearest neighbor search in OpenSearch, which is fundamental for finding documents most similar to a query based on vector embeddings. This supports RAG by retrieving relevant context for generation.
</details>

---

### Question 77
**Which AWS services support vector embeddings?**

<details>
<summary>Answer</summary>

1. **Amazon S3** with S3 Vectors
2. **Amazon OpenSearch Service**
3. **Amazon RDS for PostgreSQL** with pgvector extension
</details>

---

## Chapter 17: Compliance and Privacy

### Question 78
**What compliance features does Amazon Bedrock provide?**

<details>
<summary>Answer</summary>

- HIPAA eligibility and GDPR compliance
- Encryption at rest and in transit by default
- Optional KMS key integration
- Support for AWS PrivateLink to eliminate public internet exposure
- No-code customization of FMs
- Customer data is NOT used to train or improve Bedrock or FMs
</details>

---

### Question 79
**What is CloudTrail Lake used for with AI services?**

<details>
<summary>Answer</summary>

CloudTrail Lake is a managed data lake that stores and queries CloudTrail events using SQL-like syntax. It enables analysis of API activity, including user interactions with AI services like Amazon Bedrock, supporting audit and compliance requirements.
</details>

---

### Question 80
**How do you enforce tenant isolation in multi-tenant AI applications?**

<details>
<summary>Answer</summary>

Use IAM policies to provide each tenant with unique credentials that have permissions restricted to their specific data. This enforces access control at the database level, ensuring strong data isolation between tenants.
</details>

---

## Chapter 18: Performance Optimization

### Question 81
**What factors determine when to use which evaluation metric?**

<details>
<summary>Answer</summary>

- **Accuracy**: Balanced classes; misleading with imbalanced datasets
- **Precision**: Minimize false positives (e.g., spam detection)
- **Recall**: Minimize false negatives (e.g., medical diagnosis)
- **F1-Score**: Balance precision and recall (e.g., information retrieval)
</details>

---

### Question 82
**What determines the optimal number of epochs for fine-tuning?**

<details>
<summary>Answer</summary>

Monitor:
- **Validation Output Accuracy**: Higher indicates better model
- **Validation Loss**: Lower indicates better generalization

Stop training when validation metrics plateau or start degrading (overfitting).
</details>

---

### Question 83
**What is Amazon SageMaker Autoscaling Policies?**

<details>
<summary>Answer</summary>

Autoscaling Policies enable automatic scaling of SageMaker endpoints based on predefined metrics (like request count or latency) and thresholds, ensuring optimal performance during traffic spikes while minimizing costs during low usage.
</details>

---

### Question 84
**What are the benefits of ongoing pre-training for Foundation Models?**

<details>
<summary>Answer</summary>

Ongoing pre-training allows FMs to:
- Continue learning from new and relevant domain-specific data
- Adapt internal representations
- Improve understanding of domain-specific terminology
- Deliver better results when fine-tuned for downstream tasks
</details>

---

## Chapter 19: Specialized Use Cases

### Question 85
**Which combination optimizes call center agent productivity with Gen AI?**

<details>
<summary>Answer</summary>

**Amazon Q in Amazon Connect** + **Amazon Connect Contact Lens**

- Amazon Q provides real-time guidance, conversation summarization, and automated post-call documentation
- Contact Lens provides real-time analytics, sentiment analysis, and transcription
</details>

---

### Question 86
**What service converts video speech to text for AI analysis?**

<details>
<summary>Answer</summary>

**Amazon Transcribe** - Specifically designed for automatic speech recognition (ASR), converting spoken language in videos to text that can be analyzed by LLMs or other AI models.
</details>

---

### Question 87
**What are the benefits of Gen AI for CloudWatch log analysis?**

<details>
<summary>Answer</summary>

1. Accelerate incident triage with concise overviews of recent log events
2. Enable proactive identification of potential issues or anomalies
3. Facilitate better collaboration and communication among teams
</details>

---

### Question 88
**Which Amazon Bedrock model is best for text generation tasks?**

<details>
<summary>Answer</summary>

**Amazon Titan Text** - A Gen LLM specifically designed for various text generation tasks including summarization, text generation, classification, open-ended Q&A, and information extraction.
</details>

---

## Chapter 20: Advanced Concepts

### Question 89
**What is Amazon Bedrock Model Distillation?**

<details>
<summary>Answer</summary>

Model Distillation transfers knowledge from an existing model (teacher) to create a smaller, more efficient model (student) without training from scratch. This maintains performance while reducing computational requirements.
</details>

---

### Question 90
**What is the purpose of RLHF (Reinforcement Learning from Human Feedback)?**

<details>
<summary>Answer</summary>

RLHF aligns model outputs with human values and preferences by incorporating human feedback into the training process. This helps models generate more helpful, harmless, and honest responses.
</details>

---

### Question 91
**What is Provisioned Throughput in Amazon Bedrock?**

<details>
<summary>Answer</summary>

Provisioned Throughput allows reserving specific capacity for Bedrock models, ensuring consistent performance during peak periods. This eliminates delay risks and provides predictable response times for customer-facing applications.
</details>

---

### Question 92
**What are the major limitations of Generative AI?**

<details>
<summary>Answer</summary>

1. **Knowledge Cutoff**: No information beyond training data cutoff date
2. **Hallucinations**: Can generate plausible-sounding but incorrect information
</details>

---

### Question 93
**What is Amazon Augmented AI (A2I)?**

<details>
<summary>Answer</summary>

A2I is a fully managed service that builds workflows for human review of ML predictions. It provides built-in workflows for common use cases like content moderation and document analysis, and supports custom workflows for specific needs.
</details>

---

### Question 94
**What is Amazon Personalize?**

<details>
<summary>Answer</summary>

Amazon Personalize is an ML service that enables developers to create individualized recommendations for customers using their applications, leveraging the same technology used at Amazon.com.
</details>

---

### Question 95
**What is AWS Glue Data Catalog's role in ML pipelines?**

<details>
<summary>Answer</summary>

AWS Glue Data Catalog provides a centralized metadata repository for organizing, discovering, and managing data assets. It ensures reliable, repeatable, and auditable ML pipelines by maintaining data schemas, formats, and locations while supporting data governance and compliance.
</details>

---

## Chapter 21: Model Selection and Factors

### Question 96
**What factors should be considered when selecting an AI model?**

<details>
<summary>Answer</summary>

1. **Model types**: Classification, regression, generation, etc.
2. **Performance requirements**: Latency, throughput, accuracy
3. **Capabilities**: What tasks the model can perform
4. **Constraints**: Computational resources, budget, time
5. **Compliance**: Regulatory and data privacy requirements
</details>

---

### Question 97
**What are the three principles of Human-Centered Design for Explainable AI?**

<details>
<summary>Answer</summary>

1. **Design for Amplified Decision-Making**: Support high-stakes decisions while minimizing risks
2. **Design for Unbiased Decision-Making**: Ensure processes are free from biases
3. **Design for Human and AI Learning**: Create effective AI through cognitive apprenticeship and personalization
</details>

---

### Question 98
**What is SageMaker Data Wrangler?**

<details>
<summary>Answer</summary>

SageMaker Data Wrangler is a Low-Code/No-Code (LCNC) tool providing an end-to-end solution to import, prepare, transform, featurize, and analyze data using a visual web interface, simplifying data preparation for ML.
</details>

---

### Question 99
**What are AI Service Cards?**

<details>
<summary>Answer</summary>

AI Service Cards are documentation on Responsible AI that provide teams with a single source of information on intended use cases, limitations, responsible AI design choices, and deployment/performance optimization best practices for AWS AI services.
</details>

---

### Question 100
**What are the eight Foundation Model lifecycles?**

<details>
<summary>Answer</summary>

1. Data selection
2. Pre-training
3. Optimization
4. Evaluation
5. Deployment
6. Feedback and continuous improvement
7. Monitoring (implied)
8. Iteration (implied)

Note: The source mentions six explicitly; monitoring and iteration are commonly included in FM lifecycle frameworks.
</details>

---

## Quick Reference Tables

### AWS Service Quick Reference

| Use Case | AWS Service |
|----------|-------------|
| Text sentiment analysis | Amazon Comprehend |
| Speech to text | Amazon Transcribe |
| Text to speech | Amazon Polly |
| Image/video analysis | Amazon Rekognition |
| Document text extraction | Amazon Textract |
| Language translation | Amazon Translate |
| Conversational AI/Chatbots | Amazon Lex |
| Intelligent search | Amazon Kendra |
| Foundation Models | Amazon Bedrock |
| Full ML lifecycle | Amazon SageMaker |
| Code assistance | Amazon Q Developer |
| Human review workflows | Amazon Augmented AI (A2I) |
| Personalized recommendations | Amazon Personalize |

### Metric Selection Guide

| Problem Type | Recommended Metrics |
|--------------|---------------------|
| Classification (balanced) | Accuracy, F1 Score |
| Classification (imbalanced) | Precision, Recall, F1 Score, AUC-ROC |
| Regression | MAE, MSE, RMSE, R-squared |
| Text generation | ROUGE, BLEU, BERTScore |
| Image generation | Inception Score, FID |
| Language models | Perplexity |

### Prompt Engineering Parameters

| Parameter | Controls | Low Value | High Value |
|-----------|----------|-----------|------------|
| Temperature | Randomness/Creativity | Focused, deterministic | Random, creative |
| Top P | Diversity (probability) | Focused, coherent | Diverse, creative |
| Top K | Diversity (word count) | Focused, predictable | Diverse, varied |
| Max Length | Output size | Shorter responses | Longer responses |

---

## Exam Tips

### Key Concepts to Remember

1. **RAG vs Fine-Tuning**: RAG adds context without retraining; Fine-tuning updates model parameters
2. **Bias vs Variance**: Bias = too simple; Variance = too complex (overfitting)
3. **Precision vs Recall**: Precision minimizes false positives; Recall minimizes false negatives
4. **Supervised vs Unsupervised**: Labeled data vs unlabeled data
5. **Foundation Models**: Pre-trained on internet-scale data, adaptable to multiple tasks

### Service Pairing Patterns

- **Text Analysis**: Comprehend
- **Visual Analysis**: Rekognition
- **Document Processing**: Textract
- **Speech Processing**: Transcribe (to text) / Polly (to speech)
- **Search**: Kendra
- **Full ML Pipeline**: SageMaker
- **Foundation Models**: Bedrock
- **Chatbots**: Lex (or Bedrock + RAG)

### Responsible AI Pillars

Remember **"FEPTS-GCS"**:
- **F**airness
- **E**xplainability
- **P**rivacy & Security
- **T**ransparency
- **S**afety
- **G**overnance
- **C**ontrollability
- **S**ecurity (Veracity & Robustness)

### Common Pitfalls

1. Confusing metrics for classification vs regression
2. Forgetting that RAG doesn't require fine-tuning
3. Mixing up encoder-decoder architectures
4. Not understanding when to use which AWS service
5. Overlooking compliance and security requirements

---

## Practice Scenarios

### Scenario 1: Customer Churn Prediction
**Question**: A company wants to predict customer churn. What should they use?

<details>
<summary>Answer</summary>

- **Task Type**: Binary Classification
- **Algorithms**: Decision Trees, SVM, Logistic Regression
- **AWS Service**: Amazon SageMaker
- **Metrics**: Precision, Recall, F1 Score, AUC-ROC
- **Why**: Need to identify customers likely to leave (minimize false negatives with good recall)
</details>

### Scenario 2: Document Search System
**Question**: Building an intelligent document search for a law firm. What architecture?

<details>
<summary>Answer</summary>

- **Core Service**: Amazon Kendra (intelligent search)
- **Enhancement**: RAG with Amazon Bedrock
- **Storage**: S3 for documents
- **Vector Search**: OpenSearch with k-NN for semantic search
- **Security**: AWS PrivateLink, KMS encryption
</details>

### Scenario 3: Real-time Image Moderation
**Question**: Need to moderate user-uploaded images in real-time for inappropriate content.

<details>
<summary>Answer</summary>

- **Primary Service**: Amazon Rekognition (content moderation)
- **Human Review**: Amazon A2I for edge cases
- **Deployment**: SageMaker real-time endpoints if custom model needed
- **Monitoring**: CloudWatch for API calls and performance
</details>

### Scenario 4: Multilingual Customer Support Chatbot
**Question**: Deploy a chatbot supporting 10 languages with company-specific knowledge.

<details>
<summary>Answer</summary>

- **Chatbot Framework**: Amazon Lex
- **Translation**: Amazon Translate
- **Knowledge Base**: Amazon Kendra connected to documentation
- **LLM Enhancement**: Amazon Bedrock with RAG
- **Alternative**: Amazon Q with custom data sources
</details>

### Scenario 5: Video Content Analysis
**Question**: Extract insights from thousands of archived video recordings.

<details>
<summary>Answer</summary>

- **Transcription**: Amazon Transcribe
- **Scene Detection**: Amazon Rekognition
- **Text Analysis**: Amazon Comprehend (sentiment, entities)
- **Storage**: S3 for videos
- **Processing**: SageMaker Processing for batch jobs
</details>

---

## Study Strategy

### Week 1: Fundamentals
- AI, ML, DL, and Generative AI concepts
- AWS AI service overview
- Responsible AI principles

### Week 2: Deep Dive on Services
- SageMaker capabilities
- Bedrock and Foundation Models
- Comprehend, Translate, Transcribe, Polly
- Rekognition, Textract, Lex

### Week 3: Model Development
- ML lifecycle
- Training and evaluation metrics
- Hyperparameter tuning
- MLOps practices

### Week 4: Advanced Topics
- Prompt engineering
- RAG architecture
- Model compression
- Security and compliance

### Week 5: Practice and Review
- Practice scenarios
- Review weak areas
- Take practice exams
- Review this question set

---

**Good luck with your AWS AI Practitioner Certification exam!**
