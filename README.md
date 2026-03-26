## Project Overview
This project implements a complete data pipeline for amazon sales using Python and Docker. The pipeline processes raw data, performs analysis, generates visualizations, and applies clustering techniques.

---

## ⚙️ Technologies Used
- Python 3.11
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- scipy
- requests
- Docker

---

## 🐳 Docker Commands Used
### 🔹 Build Docker Image
```
docker build -t bigdata_assignment .   
```
### 🔹 Run Docker Container
```
docker run -dit --name container_1 bigdata_assignment
```
### 🔹 Execute Pipeline Inside Container
```
docker exec container_1 python ingest.py amazon.csv
docker exec container_1 python preprocess.py data_raw.csv
docker exec container_1 python analytics.py data_preprocessed.csv
docker exec container_1 python visualize.py data_preprocessed.csv
docker exec container_1 python cluster.py data_preprocessed.csv
```
### 🔹 Copy Outputs from Container
```
docker cp container_1:/app/pipeline/data_raw.csv bigdata_assignment/results/
docker cp container_1:/app/pipeline/data_preprocessed.csv bigdata_assignment/results/
docker container_1:/app/pipeline/clustered_data.csv bigdata_assignment/results/

docker cp container_1:/app/pipeline/insight1.txt bigdata_assignment/results/
docker cp container_1:/app/pipeline/insight2.txt bigdata_assignment/results/
docker cp container_1:/app/pipeline/insight3.txt bigdata_assignment/results/

docker cp container_1:/app/pipeline/summary_plot.png bigdata_assignment/results/
```
### 🔹 Stop and Remove Container
```
docker stop container_1
docker rm container_1
```
### 🔹 Pushing the image to Docker Hub
```bash
docker tag bigdata_assignment omarabdelwahed/bigdata_assignment
docker push omarabdelwahed/bigdata_assignment
```
### 🔹 Docker Hub link:
```
https://hub.docker.com/layers/omarabdelwahed/bigdata_assignment/latest/images/
```
### Execution Flow
```
amazon.csv
↓
ingest.py → loads raw data → data_raw.csv
↓
preprocess.py → cleans data → data_preprocessed.csv
↓
analytics.py → generates insights → insight1.txt, insight2.txt, insight3.txt
↓
visualize.py → creates plots → summary_plot.png
↓
cluster.py → performs clustering → clustered_data.csv
```

📂 Output Files

The following outputs are generated and stored in:
```
bigdata_assignment/results/
data_raw.csv
data_preprocessed.csv
clustered_data.csv
summary_plot.png
insight1.txt
insight2.txt
insight3.txt
```
