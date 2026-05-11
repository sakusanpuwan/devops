# Innovating with Google Cloud Artificial Intelligence
## AI & ML Fundamentals
Artificial intelligence is a broad field which refers to the use of technologies to build machines and computers that can mimic cognitive functions associated with human intelligence. These functions include, being able to see, understand, and respond to spoken or written language, analyze data, make recommendations and more.

Machine learning is a subset of AI that lets a machine learn from data without being explicitly programmed. It relies on various models to analyze large amounts of data, learn from the insights, and then make predictions and informed decisions. Machine learning algorithms improve performance over time as they are trained or exposed to more data.

Generative AI is a type of AI that can generate new content, such as text, images, or music, based on the data it has been trained on. It uses techniques like deep learning and neural networks to create original and realistic outputs, making it a powerful tool for creative applications, such as conversational bots, content generation, document synthesis, and product discovery.

Most data analysis and business intelligence is based on historic data used to calculate metrics or identify trends but to create value in your business you need to leverage that data to make decisions for future business. With access to the right data, AI and ML can be used to uncover predictive insights to benefit companies and their customers.

ML is suited to solve common business problems:
- Replacing or simplifying rule based systems: If all the data that's available shows which search results users clicked on per query, a machine learning model can be trained to predict the rank for search results, instead of hard coding rule based systems.
- Automating processes: Replace manual, time-consuming processes prone to human error with predictable, repeatable, efficient and accurate decisions at scale
- Understanding unstructured data: Use machine learning to analyze and derive insights from unstructured data sources, such as text, images, and videos, enabling better decision-making.
- Personalisation: Leverage machine learning to deliver personalized experiences and recommendations to users based on their behavior, preferences, and interactions.

### Data Quality
ML models require high-quality, diverse, and representative training data to perform well and avoid biases. It's essential to continuously monitor and update these models to ensure they remain effective and relevant over time.

6 dimensions to assess data quality:
- Completeness: Ensuring all required data is present and accounted for, if incomplete model will not learn all patterns that are necessary to make accurate predictions.
- Uniqueness: Ensuring each data point is distinct and not duplicated, if not it can skew the model's understanding and lead to inaccurate predictions.
- Timeliness: Ensuring data is up-to-date and available when needed, if not model might make predictions based on outdated data or irrelevant information.
- Validity: Ensuring data is accurate and conforms to defined formats and standards, e.g. invalid date format.
- Accuracy: Ensuring data is correct and reliable, minimizing errors and inconsistencies, e.g invalid labels (picture of dog labelled as cat).
- Consistency: Ensuring data is consistent across different sources and over time, without contradictory information e.g. same entity appears with different value.

### Ethics of AI
Google has established principles that guide Google AI applications, best practices to share work with communities and programs to operationalise AI efforts.

Principles include:
- Bold innovation: Embrace cutting-edge research and technology to push the boundaries of what's possible with AI.
- Responsible development & deployment: Prioritize safety, privacy, and ethical considerations throughout the AI lifecycle.
- Collaborative progress: Work together with diverse stakeholders to ensure AI benefits everyone.

Explainable AI is Google Cloud's set of tools and frameworks to help you understand and interpret predictions made by AI models, fostering trust and transparency in AI-driven decisions.

## GCP AI & ML Solutions
### ML Solutions
- BigQuery ML: A tool for using SQL queries to create and execute ML models in BigQuery empowering non-technical users by reducing complexity.
- Pretrained API: A set of pre-built machine learning models that can be easily integrated into applications for tasks like image recognition, natural language processing if limited training data is available.
- AutoML: A no code solution which lets you build your own ML models on Vertex AI (Google Cloud's end to end AI & ML platform) through GUIs
- Code your own models: Gives you flexibility and full control over the ML pipeline
- TensorFlow: An open-source machine learning framework that provides a comprehensive ecosystem for building and deploying ML models. Leverages TPI (Tensor Processing Units) which is Google's custom developed application specific integrated circuit (ASIC) used to accelerate machine learning workloads. TPUs act as domain specific hardware as opposed to general purpose hardware with CPUs and GPUs.

### AI Solutions
- Contact Center AI: models for speaking with customers and assisting human agents, increasing operational efficiency, and personalizing customer care to transform your contact center
- Document AI: unlocks insights by extracting and classifying information from unstructured documents such as invoices, receipts, forms, letters, and reports.
- Discovery AI: for retail uses machine learning to select the optimal ordering of products on a retailer's e-commerce site when shoppers choose a category like winter jackets or kitchen ware.
- Cloud Talent Solution:  uses AI with job search and talent acquisition capabilities, matches candidates to ideal jobs faster, and allows employers to attract and convert higher quality candidates.

### Considerations 
- Speed: How quickly model to prod? Pre-trained APIs require no model training but custom build ML model from scratch unlike AutoML and BigQuery ML.
- Differentiation: How unique is your model, or how unique does it need to be? Vertex AI provides tools for custom model training and fine-tuning, allowing for greater differentiation in model performance.
- Expertise: What level of expertise is required to develop and maintain the model? Pre-trained APIs and AutoML require less expertise compared to custom model development.
- Effot: How complex? How much data? Experience of team?


