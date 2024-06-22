# Home Assistant Add-on: NM HTTP


#### Diretorio de arquivos de configuracao

    /config/nmserver


#### Exemplos de CGI para reproduzir audio

    - curl http://local-nmhttp/cgi-bin/play?alarme.wav
    - curl http://local-nmhttp/cgi-bin/ffplay -d "/media/alarme.wav -loop 2 -volume 10"

#### RESTful Command

    incluir em /homeassistant/configuration.yaml

    rest_command:
      play_alarme:
        url: "http://local-nmhttp/cgi-bin/play?alarme.wav"
        method: GET
      ffplay:
        url: "http://local-nmhttp/cgi-bin/ffplay"
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

    Nesse caso a url nao sera http://local-nmhttp
    Dever ser algo do tipo http://fe06975f-nmhtpp
    executar "hostname" no prompt do WEB UI

#### NOTA 

    Exemplos originais de configuracao e CIG em /nmserver-config-ori
    Acesso via WEB UI

