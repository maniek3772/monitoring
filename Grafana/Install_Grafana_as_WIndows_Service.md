# Install Grafana as a Windows Service using NSSM

This guide shows how to install Grafana as a background Windows service using NSSM (Non-Sucking Service Manager).

---
## 1. Download Grafana

Go to the official download page:  
👉 https://grafana.com/grafana/download

- Choose the **Windows (ZIP)** version.
- Extract it to a desired location, e.g.:  
  `C:\Grafana`

---

## 2. Prepare NSSM (if not already installed)

Download from:  
👉 https://nssm.cc/download

- Extract it, for example, to:  
  `C:\nssm`

---

## 3. Install Grafana as a Service via NSSM

1. Open **Command Prompt as Administrator**.
2. Navigate to the NSSM directory:

    ```bash
    cd C:\nssm\win64
    ```

3. Launch the NSSM service installer:
    ```
    nssm install grafana
    ```

4. Fill out the configuration window:

    **4.1 Application tab**    
    Path:
    C:\Grafana\bin\grafana-server.exe

    Startup directory:
    C:\Grafana

    Arguments:
    --config="conf\defaults.ini"

    **4.2 Details tab**
    
    Display name: Grafana

    Description: Grafana dashboard service

    **4.3 I/O tab**
    
    Output: C:\Grafana\nssm_log\output.txt
    
    Error: C:\Grafana\nssm_log\error.txt

5. Click Install service to finish.

## 4. Start the Service
To start the Grafana service use:
```
nssm start grafana
```
Alternatively, open services.msc, find Grafana, and start it from there.

---

Grafana should now be running in the background as a Windows service. 

You can access the dashboard via your browser:
http://localhost:3000


ℹ️ Notes
Default credentials:

login: admin

password: admin

Config file location (used in --config):
C:\Grafana\conf\defaults.ini

---
To uninstall the service using NSSM:
```
nssm remove grafana
```