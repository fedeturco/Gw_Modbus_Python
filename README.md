# Gw python3 ModBus TCP-RTU
Script python che fa da gw ModBus TCP &lt;-> RTU

          TCP
           |
       -------------
       | GW ModBus |
       -------------
           |
    ----------------------------------- 485 - RTU
     |         |                 |
    ID 1     ID 2               ID N
   
   
  
## File di configurazione: config.json

    {
        "verbose":"debug",          <- livelli della libreria logging (case insensitive)
                                        - CRITICAL 50
                                        - ERROR 40
                                        - WARNING 30
                                        - INFO 20
                                        - DEBUG 10
                                        - NOTSET 0
    
        "tcp": {                    <- Configurazione lato TCP
            "address": "0.0.0.0",   <- Address ModBus TCP
            "port": 504             <- Porta ModBus TCP
        },
        "serial": {
            "port": "/dev/ttyUSB0",     <- Porta seriale default per tutti gli slaves
            "baud":115200,              <- Baudrate
            "configuration": "8N1",     <- Configurazione seriale default per tutti gli slaves standard
            "timeout": 2000,            <- Timeout lettura seriale
            
            [Facoltativo]
            "slaves": {                 <- Configurazione specifica per determinati slaves
    
                [Facoltativo]
                "20": {                 <- Configurazione specifica per slave ID: 20
                    "enable": true,             <- Abilitazione slave ID 20
                    "port": "/dev/ttyUSB0",     <- Porta da usare con ID 20
                    "baud":115200,              <- Baudrate
                    "configuration": "8E1"      <- Configurazione porta seriale per ID 20
                    "timeout": 2000             <- Timeout lettura seriale
                }
            }
        }
     }