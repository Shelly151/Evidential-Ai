# 🚢 Evidently AI Sets Sail in Docker: A Voyage into Data Monitoring 🐳📊

## 📌 Introduction

This guide walks you through setting up an **Evidently AI-based Streamlit application** inside a Docker container. The application:

✅ **Monitors machine learning models** using Evidently AI.  
✅ **Provides an interactive dashboard** with Streamlit.  
✅ **Organizes reports and projects** efficiently.  
✅ **Uses Docker** for simplified deployment and management.  

---

## 📂 Project Structure

Ensure your working directory contains the following files and folders:

```
📁 evidently-ai-streamlit
 ├── 📂 projects                # Contains different ML monitoring projects
 │    ├── 📂 project_1
 │    │    ├── 📂 reports       # Stores monitoring reports
 │    │    ├── ...
 │    ├── 📂 project_2
 │    │    ├── 📂 reports
 │    │    ├── ...
 │    ├── ...
 │
 ├── 📂 src                     # Contains Python scripts for UI and utilities
 │    ├── ui.py                 # UI components
 │    ├── utils.py              # Utility functions
 │    ├── ...
 │
 ├── 📂 static                  # Stores static assets (CSS, images, etc.)
 │    ├── style.css             # Custom styling
 │    ├── ...
 │
 ├── 📄 app.py                   # Main Streamlit application
 ├── 📄 Dockerfile               # Defines the Docker image for Streamlit
 ├── 📄 requirements.txt          # Python dependencies
 ├── 📄 README.md                 # Project documentation
```

---

## 📝 Main Application (`app.py` Overview)

The `app.py` script:

- Dynamically **loads available projects and reports**.
- Allows users to **select a project, period, and report**.
- **Displays Evidently AI reports** inside Streamlit.
- Gracefully **handles missing projects or reports**.
- Uses `src/ui.py` for UI elements and `src/utils.py` for helper functions.

### 🔑 Key Functions:

🔹 `display_sidebar_header()`: Renders the sidebar with branding and navigation.  
🔹 `select_project()`: Lets users pick a project.  
🔹 `select_period()`: Allows selection of a reporting period.  
🔹 `select_report()`: Fetches available reports.  
🔹 `display_report()`: Loads and displays the selected report.  

---

## 🐳 Dockerfile (Containerizing the Streamlit App)

```dockerfile
# Use the official Python base image
FROM python:3.10

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir --break-system-packages -r requirements.txt

# Copy the entire project into the container
COPY . /app/

# Expose the port Streamlit runs on
EXPOSE 8501

# Run the Streamlit app
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

## 🐍 Python Dependencies (`requirements.txt`)

```text
category_encoders==2.6.0
evidently==0.2.6
jupyter==1.0.0
jupyter_contrib_nbextensions==0.7.0
matplotlib==3.7.0
numpy==1.24.2
pandas==1.5.3
pyarrow==11.0.0
python-box==5.4.1
requests==2.28.2
streamlit==1.19.0
pyyaml==5.1
scikit-learn==1.2.1
scipy==1.10.1
seaborn==0.12.2
altair==4.0
```

---

## 🛠 Steps to Run the Application

### 1️⃣ Clone the Repository & Navigate to the Project

```sh
git clone <repo-link>
cd evidently-ai-streamlit
```

### 2️⃣ Build & Run the Docker Container

```sh
docker build -t evidently-streamlit .
docker run -p 8501:8501 evidently-streamlit
```

### 3️⃣ Access the Streamlit App

Open **[http://localhost:8501](http://localhost:8501)** in your browser. 🚀

---

## 🏆 Features & Benefits

✅ **Automated ML Monitoring**: Tracks model performance over time.  
✅ **Interactive Dashboard**: View reports and insights seamlessly.  
✅ **Efficient Project Management**: Organizes reports in structured directories.  
✅ **Dockerized Deployment**: Ensures portability and easy s



![image](https://github.com/vidhi-jaju/DockSpace/blob/ff8a146fe1dd823cbec9c8928ee976e68157ad40/8.%20Evidently%20AI%20Sets%20Sail%20in%20Docker/img1.png)

