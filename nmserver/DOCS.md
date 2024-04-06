# Baseado em Home Assistant Add-on: Terminal & SSH

  Para configuracao do SSH ver Home Assistant Add-on: Terminal & SSH

  https://github.com/home-assistant/addons/tree/master/ssh

#### Diretorio de arquivos de configuracao

    /config/nmserver


#### Exemplos de CGI para reproduzir audio

    - curl http://local-nmserver/cgi-bin/play?alarme.wav
    - curl http://local-nmserver/cgi-bin/ffplay -d "/media/alarme.wav -loop 2 -volume 10"

#### RESTful Command

    incluir em /homeassistant/configuration.yaml

    rest_command:
      play_alarme:
        url: "http://local-nmserver/cgi-bin/play?alarme.wav"
        method: GET
      ffplay:
        url: "http://local-nmserver/cgi-bin/ffplay"
        method: POST
        payload: '{{params}}'


#### Automacao Call Service exemplo

    automation:
    - alias: "Arrive at Work"
      trigger:
        platform: zone
        entity_id: device_tracker.my_device
        zone: zone.work
        event: enter
      action:
        - service: rest_command.ffplay
          data:
            params: /media/alarme.wav -loop 2 -volume 10


#### Referencia RESTful Command

    https://www.home-assistant.io/integrations/rest_command/


#### NOTA addon instalado via repositorio

    Nesse caso a url nao sera http://local-nmserver
    Dever ser algo do tipo http://fe06975f-nmserver
    executar "hostname" no prompt do WEB UI

#### NOTA 

    Exemplos originais de configuracao e CIG em /nmserver-config-ori

