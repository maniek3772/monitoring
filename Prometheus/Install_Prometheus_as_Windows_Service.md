# Install Prometheus as a Windows Service using NSSM

This guide shows how to run Prometheus as a background service on Windows using NSSM (Non-Sucking Service Manager).

---

## Download Prometheus

Go to the official website:  
👉 https://prometheus.io/download

- Download the **Windows version**.
- Extract it to a desired location, for example:  
  `C:\Prometheus`

---

## ⚙️ 2. Configure `prometheus.yml`

Inside the `C:\Prometheus` folder, you'll find a file named `prometheus.yml`.

- Make sure its contents are correct, especially:
  - The **port**
  - The **data/target paths**
  - Any custom jobs or scrape targets

---

## 3. Download and Extract NSSM

Go to the official site:  
👉 https://nssm.cc/download

- Extract the contents to a folder, e.g.:  
  `C:\nssm`

---

## 4. Install Prometheus as a Service via NSSM

1. Open **Command Prompt as Administrator**.

2. Navigate to the NSSM directory:

    ```bash
    cd C:\nssm\win64
    ```

3. Launch the service installer:

    ```bash
    nssm install prometheus
    ```

4. Fill out the configuration window:

    **4.1 Application tab**    
    Path:
    C:\Prometheus\prometheus.exe

    Startup directory:
    C:\Prometheus

    Arguments:
    --config.file=prometheus.yml

    **4.2 Details tab**
    
    Display name: Prometheus

    Description: Prometheus monitoring server

    **4.3 I/O tab**
    
    Output: C:\Prometheus\nssm_log\output.txt
    
    Error: C:\Prometheus\nssm_log\error.txt


5. Click **Install service** to finish.

---

## 5. Start the Service

Start Prometheus with:

```bash
nssm start prometheus
```

or open services.msc, find Prometheus, and click Start.

---
Done!
Prometheus is now running as a background Windows service.
You can access the web interface at:

👉 http://localhost:9090
(assuming the port wasn’t changed in prometheus.yml)