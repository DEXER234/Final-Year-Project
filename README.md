
-----

# Depression Detection via Text Analysis

([https://img.shields.io/badge/License-MIT-yellow.svg](https://www.google.com/search?q=https://img.shields.io/badge/License-MIT-yellow.svg))]([https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT))
[](https://www.google.com/search?q=%5Bhttps://www.python.org/downloads/%5D\(https://www.python.org/downloads/\))
([https://img.shields.io/badge/React-18.2.0-61DAFB?logo=react](https://www.google.com/search?q=https://img.shields.io/badge/React-18.2.0-61DAFB%3Flogo%3Dreact))]([https://reactjs.org/](https://reactjs.org/))
([https://img.shields.io/badge/Spring%20Boot-3.0-6DB33F?logo=spring](https://www.google.com/search?q=https://img.shields.io/badge/Spring%2520Boot-3.0-6DB33F%3Flogo%3Dspring))]([https://spring.io/projects/spring-boot](https://spring.io/projects/spring-boot))

A web-based application that leverages a state-of-the-art Natural Language Processing (NLP) model to detect signs of depression from textual input. This project is designed as a final year submission, demonstrating a full-stack application of machine learning.

**Live Demo:** [https://ml-depression-detection.vercel.app](https://ml-depression-detection.vercel.app) [1]

> **Disclaimer:** This tool is for educational and research purposes only. It is not a substitute for professional medical advice, diagnosis, or treatment. If you are experiencing symptoms of depression, please consult a qualified healthcare professional.

## Table of Contents

  - [Features](https://www.google.com/search?q=%23features)
    \-(\#tech-stack)
    \-(\#system-architecture)
    \-(\#getting-started)
      - [Prerequisites](https://www.google.com/search?q=%23prerequisites)
      - [Installation](https://www.google.com/search?q=%23installation)
  - [Usage](https://www.google.com/search?q=%23usage)
    \-(\#model-training)
  - [Contributing](https://www.google.com/search?q=%23contributing)
  - [License](https://www.google.com/search?q=%23license)

## Features

  - **Real-time Analysis:** Provides instant classification of user-provided text.
  - **User-Friendly Interface:** A clean and simple web interface for easy interaction.
  - **Scalable Architecture:** Built with modern cloud infrastructure to handle requests efficiently.
  - **High Accuracy:** Utilizes a fine-tuned Transformer model (BERT/RoBERTa) for state-of-the-art performance.

## Tech Stack

This project is a full-stack application composed of three main parts: a frontend, a backend, and the machine learning model hosted as an API.[1]

| Component | Technologies Used |
| -------------------- | ------------------------------------------------------------------------------ |
| **Frontend** | React.js, TypeScript, Vite, Tailwind CSS [1] |
| **Backend** | Spring Boot, Java, PostgreSQL, JPA, Hibernate [1] |
| **Machine Learning** | Python, TensorFlow, Keras, Hugging Face Transformers (BERT/RoBERTa) [1] |
| **Cloud & DevOps** | AWS Lambda, AWS RDS, AWS Beanstalk, AWS Route 53, Docker [1] |

## System Architecture

The application follows a decoupled, three-tier architecture to ensure scalability and maintainability.

1.  **Frontend (Client):** The user interacts with the React-based single-page application. When a user submits text, the frontend sends a request to the backend server.
2.  **Backend (Server):** The Spring Boot server receives the request. It handles business logic, user data (if any), and communicates with the machine learning model.
3.  **ML Model API:** The trained Python model is hosted on a serverless platform (AWS Lambda). The backend sends the text to this API endpoint, which returns the depression prediction. This separation allows the ML model to be updated independently of the main application.

<!-- end list -->

```
 <--> <--> <-->
```

## Getting Started

Follow these instructions to get a local copy of the project up and running for development and testing purposes.

### Prerequisites

  - Git
  - Node.js & npm
  - Python 3.8+
  - Java & Maven
  - Docker (optional, for containerization)
  - An AWS account (for deploying the model API)

### Installation

1.  **Clone the repository:**

    ```sh
    git clone https://github.com/your-username/depression-detection.git
    cd depression-detection
    ```

2.  **Setup the Machine Learning Model:**

      - Navigate to the `ml-model` directory.
      - Install Python dependencies: `pip install -r requirements.txt`
      - Follow the instructions to train the model (see(\#model-training)) and deploy it to AWS Lambda. Note the function name and region.

3.  **Setup the Backend:**

      - Navigate to the `backend` directory.
      - Create an `application.properties` file and add the necessary environment variables [1]:
        ```properties
        RECAPTCHA_SECRET=your_recaptcha_secret_key
        AWS_SECRET_ACCESS_KEY=your_aws_secret_key
        AWS_LAMBDA_FUNCTION_NAME=your_lambda_function_name
        AWS_LAMBDA_FUNCTION_REGION=your_lambda_function_region
        SPRING_DATASOURCE_URL=your_postgresql_db_url
        SPRING_DATASOURCE_USERNAME=your_db_username
        SPRING_DATASOURCE_PASSWORD=your_db_password
        ```
      - Run the server: `mvn spring-boot:run`

4.  **Setup the Frontend:**

      - Navigate to the `frontend` directory.
      - Install npm packages: `npm install`
      - Create a `.env` file and add the following variables [1]:
        ```
        VITE_WEB_KEY=your_recaptcha_web_key
        VITE_INPUT_POST_ENDPOINT=http://localhost:8080/api/predict
        VITE_TOKEN_VERIFICATION_ENDPOINT=http://localhost:8080/api/verify
        ```
      - Start the development server: `npm run dev`

## Usage

Once all services are running, open your browser and navigate to `http://localhost:5173` (or the port specified by Vite).

1.  Scroll to the demo section.
2.  Enter a piece of text (20-2000 characters).
3.  Complete the captcha.
4.  Click "Click to see the result" to get the model's prediction.

## Model Training

The core of this application is the NLP model trained to classify text.

  - **Dataset:** The model was trained on the **Reddit Self-reported Depression Diagnosis (RSDD) dataset**.[2, 3] This dataset contains posts from Reddit users who have self-reported a depression diagnosis, along with a matched control group. Access requires signing a Data Usage Agreement to protect user privacy.[3]
  - **Methodology:** The approach is based on fine-tuning a pre-trained Transformer model.
    1.  **Preprocessing:** Text data is cleaned by removing noise (URLs, special characters), converting to lowercase, and removing stopwords.[4]
    2.  **Model Architecture:** A **RoBERTa** model (`roberta-large`) is used as the base. This model is then fine-tuned on the RSDD dataset for the specific task of binary text classification (depressed vs. not depressed).[5]
    3.  **Training:** The model is trained using the Hugging Face `transformers` and `simpletransformers` libraries in Python.[5] Performance is evaluated using metrics like F1-score, precision, and recall.

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.
