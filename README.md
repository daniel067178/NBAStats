# 🏀 NBA MLOps Project: End-to-End Learning and Best Practices

This project is a hands-on platform for mastering the End-to-End (E2E) Machine Learning Operations (MLOps) lifecycle. The primary goal is to move beyond isolated Jupyter Notebooks and build a robust, production-ready system for predicting NBA game outcomes.

---

### 🎯 Core Philosophy: Learning by Doing

This initiative is focused on translating theoretical MLOps knowledge into practical engineering skills. The core philosophy is to learn by building, with an emphasis on industry-standard practices.

-   **E2E MLOps Implementation:** Master the key stages of the MLOps lifecycle, including automated ETL, feature engineering pipelines, containerization (Docker), continuous testing, and cloud deployment.
-   **Software Engineering for Data Science:** Adhere to best practices that ensure code quality, reproducibility, and maintainability.
-   **Pure Development Focus:** While AI guided the high-level architecture, all core logic—data extraction, feature calculations, model training, and the API—was developed manually. This approach maximizes the learning curve and deepens the understanding of fundamental concepts.

---

### 🧠 Prediction Goals

The project tackles two classic machine learning problems applied to NBA statistics:

1.  **Winner Prediction (Classification):**
    -   **Goal:** Predict the winning team of an NBA game.
    -   **Models:** Utilizes powerful classifiers like XGBoost or Random Forest.

2.  **Total Points Prediction (Regression):**
    -   **Goal:** Predict the final combined score (Over/Under) of the game.
    -   **Models:** Employs efficient regression models like LightGBM or Linear Regression.

---

### 📊 The Heart of the Model: Time-Aware Feature Engineering

The project's intelligence lies in its feature engineering process, which strictly prevents data leakage by respecting the temporal nature of sports data.

-   **Data Source:** All raw data is sourced from the official NBA API.
-   **Key Features:**
    -   **ELO Score:** A dynamic, opponent-weighted ranking system that provides a powerful predictive signal of a team's true strength.
    -   **Rolling Statistics:** Moving averages (e.g., 5-game, 10-game windows) for key metrics to capture a team's recent performance trends.
-   **Data Leakage Prevention:** Features for any given game are calculated **only** using data available *before* that game occurred. This critical constraint is verified via unit tests (Pytest).

---

### 🚀 Production-Ready Pipeline

The final stage transforms the trained models into a fully operational web service, ready for real-world consumption.

-   **Service Layer:** A high-performance **FastAPI** application exposes a `/predict` endpoint that serves live predictions.
-   **Containerization:** The entire application is packaged into a **Docker** image, ensuring it runs consistently in any environment.
-   **Cloud Deployment:** The Docker image is deployed to **Google Cloud Run**, leveraging its serverless and auto-scaling capabilities for efficient, on-demand inference.
-   **Reproducibility:** **DVC (Data Version Control)** is used alongside Git to track datasets and models, ensuring the entire pipeline is versioned and fully reproducible.
