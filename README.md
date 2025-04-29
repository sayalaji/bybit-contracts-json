# 📊 Bybit Contracts Tracker Bot

Este proyecto automatiza la extracción de contratos con volumen superior a $500K desde el exchange Bybit, genera un archivo JSON con la data y lo sube a GitHub automáticamente cada 3 minutos. Además, incluye un dashboard local (Flask) para visualizar los contratos activos desde http://localhost:5000. Incluye un servicio de Windows totalmente automatizado gracias a NSSM (Non-Sucking Service Manager), y puede ser instalado en segundos usando un script `.bat`.

Funcionalidades:
- Extracción de contratos desde Bybit.
- Filtrado por volumen 24h >= $500K.
- Generación automática de bybit_contracts.json.
- Push automático a GitHub vía SSH.
- Dashboard local con Flask en http://localhost:5000.
- Servicio de Windows con inicio automático al encender el PC.

Estructura del proyecto:
bybit-contracts-json/
├── Launcher.py          → Inicia el bot y el dashboard  
├── tu_script.py         → Lógica para consultar y filtrar contratos  
├── dashboard.py         → Panel web en Flask  
├── requirements.txt     → Librerías necesarias para el entorno  
├── bybit_contracts.json → Archivo generado cada 3 minutos  
└── instalar_bot.bat     → Script de instalación automática como servicio

Instalación:
1. Clona este repositorio o copia la carpeta en tu equipo.
2. Instala Python 3.10+ y NSSM.
3. Ejecuta el archivo instalar_bot.bat como administrador.
4. El bot se ejecutará automáticamente como servicio en segundo plano.

Dashboard:
Una vez iniciado el servicio, accede al dashboard en tu navegador ingresando a http://localhost:5000. Verás los contratos activos que cumplen con el criterio de volumen filtrado.

Desinstalación:
Para eliminar el servicio, abre PowerShell como administrador y ejecuta:  
nssm remove BybitBotService confirm

Instalación manual (alternativa):
- cd C:\Users\sebas\bybit-contracts-json  
- python -m pip install -r requirements.txt  
- nssm install BybitBotService C:\ruta\a\pythonw.exe Launcher.py  
- nssm set BybitBotService AppDirectory C:\Users\sebas\bybit-contracts-json  
- nssm set BybitBotService AppStdout C:\Users\sebas\Documents\stdout.log  
- nssm set BybitBotService AppStderr C:\Users\sebas\Documents\stderr.log  
- nssm start BybitBotService  

Licencia:  
Este proyecto es de libre uso bajo licencia MIT. Puedes modificarlo, distribuirlo o integrarlo en tus propios sistemas con fines personales o comerciales, dando el crédito correspondiente.

Autor:  
Desarrollado por Sebastian Ayala Jimenez con pasión por la automatización y el análisis financiero.

