### **📡 Signal Strength Predictor**

An end-to-end data engineering and predictive machine learning pipeline designed to parse, process, and model highly volatile 5G telecommunication telemetry. The system ingests raw network traces from live drive-tests, applies custom pattern-matching feature extraction, and trains an optimized ensemble model to predict downlink throughput in real-time.



Unlike standard static academic scripts, this project bridges data science and software engineering by compiling the underlying machine learning logic into a highly interactive, responsive Streamlit web application for real-time link adaptation simulation.


---


### **Features**



* Messy Data Extractor: Pulls out raw metrics like signal strength (RSRP) and link settings (MCS) from complicated, multi-file base station text strings using smart search filters.



* Two Separate AI Engines: Runs two independent machine learning models—one dedicated to tracking signal drops and the other built to calculate final download speed limits.



* 91% Speed Accuracy: Handles tricky, unstable cellular signals (like blocks from buildings or movement) to deliver accurate speed predictions across thousands of data points.



* Interactive Simulation Controls: Features a real-time web control panel with sliders, letting you manually adjust signal conditions to test how the connection reacts instantly.



* Real-World Math Tuning: Blends the machine learning predictions with actual physics rules so the dashboard gives realistic results when you shift the link settings.


---


### **Architecture Overview**



The system architecture is strictly decoupled into distinct processing layers to guarantee modular scalability, separating raw data ingestion from runtime interface rendering.



**1. Ingestion \& Custom Regex ETL Layer:**



Time Complexity: O(N\*L)



Raw diagnostic records are extracted across multiple scenarios from the Eurecom ElasticMon 5G testbed repository. 

The core physical layer metrics are enclosed inside an unstructured string column (mac\_stats). The ETL layer targets and decodes internal JSON-like key/value structures dynamically without parsing overhead.



**2. Statistical Analysis \& Validation Layer:**



A bivariate mapping script compiles a Pearson correlation grid using Seaborn to detect feature dependencies and collinearity bounds. 

Feature tracking protocols use Gini impurity scores to audit model priorities.



**3. Ensemble Core Processing Layer:**



Time Complexity: O(M\*K\*(N log N))



The mathematical model leverages ensemble random forests initialized with 100 deep estimators. 

By distributing variance across separate bootstrap decision boundary trees, the model isolates non-linear cellular signal anomalies (shadowing, atmospheric path attenuation) natively.



**4. Interactive Simulation Runtime Interface:**



Time Complexity: O(M\*D)



A web framework compiled via Streamlit maps the frozen predictive matrix into memory buffers using lazy-loading resource caching techniques. 

Moving sliders instantly updates the underlying input arrays to yield immediate speed diagnostics.


---


### **Evaluation Report**



* High Speed Accuracy (91%): The main throughput model achieved a 0.91 accuracy score. This means the AI is highly reliable at looking at signal conditions and predicting the actual download speed a user will experience.



* Accurate Signal Tracking: The first model successfully mapped out how signal quality (RSRQ) and settings affect the raw signal strength (RSRP), proving the data collected from the drive-tests is consistent.



* RSRP is the Main Driver: The feature importance charts proved that raw signal strength (RSRP) is the absolute most important factor. The AI correctly learned that if the raw power is too weak, the download speed will drop no matter what.



* Smart Handling of Clutter: The graphs showed that if you have high signal strength but bad signal quality, the predicted speed drops. This proves the AI accurately simulates real-world network congestion (like a crowded stadium scenario).


---


### **Results**



**1. Model Evaluation Metrics**



Our validation pipeline maps the performance profiles across the entire dataset to ensure the Random Forest isn't overestimating network capacity:



<img width="1586" height="590" alt="__results___0_1" src="https://github.com/user-attachments/assets/1741f8db-cde5-4867-b2d1-f99c6b778bca" />



<img width="1790" height="690" alt="__results___1_1" src="https://github.com/user-attachments/assets/68fe3eec-f7fa-4667-9b8f-5ef77d255452" />



**2. Live Network Simulation Environment**



This dashboard enables dynamic, interactive evaluation of User Equipment (UE) behaviors under challenging radio link environments:



<img width="1920" height="1022" alt="Screenshot (221)" src="https://github.com/user-attachments/assets/3889cea6-9223-4d59-af83-78d99a8f0d43" />


---


### **Deployment \& Local Setup**



To set up and run this predictive dashboard locally, clone the repository, initialize an isolated virtual environment, and execute the application sequence:


---


**1  Clone the Repository**



git clone \[https://github.com/harshit12-web/signal-strength-Predictor.git](https://github.com/harshit12-web/signal-strength-Predictor.git)

cd signal-strength-Predictor


---


**2  Create a Virtual Environment**



\# Windows

python -m venv venv

venv\\Scripts\\activate



\# macOS/Linux

python3 -m venv venv

source venv/bin/activate


---


**3  Install Package Dependencies**



pip install -r requirements.txt


---


**4  Launch the Predictive Dashboard**



streamlit run app.py

Note: Your default web browser will automatically open a local interface window at http://localhost:8501. 

If the command prompt asks for an email entry, simply press Enter to bypass it.


---


### **🔮 Future Improvements**



* Live Traffic Streaming: Connect the system to live, incoming network feeds from active 5G towers instead of static data files.
* Interactive Network Maps: Add map visuals (like Leaflet or Folium) so you can track signal strength and speed predictions on a real, physical map.
* Smarter AI Tuning: Run automated tuning tests (like GridSearchCV) to adjust the model's inner settings for an even higher performance score.
* Signal Quality Alerts: Build a system that pops up warning notifications when interference levels block download speeds from reaching their full potential.


---


### **License**



This project is licensed under the MIT License.

