# INFO8985 Monolith Observability – Flask + OpenTelemetry + SigNoz

This project demonstrates the integration of **OpenTelemetry** for logging, tracing, and metrics collection in a Python monolithic Flask application. All telemetry data is exported to **[SigNoz](https://github.com/SigNoz/signoz)** for observability and analysis.

---

## 🧰 Technologies Used

- **Flask** – Python web framework
- **OpenTelemetry SDK (Python)** – for tracing, metrics, and logs
- **SigNoz** – open source observability platform
- **Docker Compose** – to run SigNoz

---

## ✅ Assignment Goals

1. **Instrument a Flask monolith with OpenTelemetry**
2. **Send traces, metrics, and logs to SigNoz**
3. **Introduce and track an exception using OpenTelemetry**
4. **Validate all observability features using the SigNoz dashboard**

---

## 🔧 Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/rishhi-patel/info8985_monolith_analysis.git
cd info8985_monolith_analysis
```

### 2. Install Python dependencies

```bash
pip install flask opentelemetry-distro \
    opentelemetry-sdk \
    opentelemetry-exporter-otlp \
    opentelemetry-instrumentation-flask
```

### 3. Run SigNoz locally

```bash
git clone --recurse-submodules https://github.com/SigNoz/signoz.git
cd signoz/deploy/docker
docker-compose up -d
```

SigNoz UI: [http://localhost:8080](http://localhost:8080)

---

## 🚀 Run the Flask App

```bash
python app.py
```

---

## 🔎 Endpoints

| Method | Endpoint                | Description                   |
| ------ | ----------------------- | ----------------------------- |
| GET    | `/rolldice`             | Rolls a 6-sided dice          |
| GET    | `/rolldice?player=NAME` | Adds player name to trace/log |
| GET    | `/rolldice?sides=0`     | **Triggers exception** (test) |

---

## 📊 Observability Features

### 🔹 Traces

- Span: `roll`
- Attributes: `player`, `roll.value`
- Visualized in **Traces** tab of SigNoz

### 🔹 Metrics

- Custom metric: `dice.rolls`
- Labeled by `roll.value`
- Viewable in SigNoz dashboards

### 🔹 Logs

- Emitted using Python `logging`
- Includes dice roll results
- Collected in **Logs** tab

### 🔹 Exceptions

- Triggered by invalid dice input (`sides <= 0`)
- Captured in SigNoz as error trace
- Counted in error rate % and Apdex drop

---

## 📎 Example Screenshots for Submission

1. Service visible in **SigNoz Services** tab

![image](https://github.com/user-attachments/assets/cb3583e8-dab9-4a6b-9dd9-af68a83beccc)


2. `roll` span trace with attributes
![image](https://github.com/user-attachments/assets/77a8b15c-b6f8-44b6-8d64-8a7ebb262d5a)

![image](https://github.com/user-attachments/assets/e759e1c7-ef79-4d35-8601-366495cf2deb)


3. Custom `dice_rolls` metric panel

![image](https://github.com/user-attachments/assets/fe5daf0d-55e5-4969-bbaa-0e7a694f0488)

4. Logs showing player rolls

![image](https://github.com/user-attachments/assets/b76a288f-4e7c-481b-9f53-be37e6c80c42)


5. Error trace from `sides=0`

![image](https://github.com/user-attachments/assets/1b66b402-56d8-4837-9958-c656a97900f9)



---

## 📌 Author

- **Name:** Rishikumar Patel
- **Student ID:** 8972657
