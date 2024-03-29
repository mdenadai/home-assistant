# Baseado em Home Assistant Add-on: Terminal & SSH

  Para configuracao do SSH ver Home Assistant Add-on: Terminal & SSH
  https://github.com/home-assistant/addons/tree/master/ssh


#### Exemplo de CGI para reproduzir audio

  "curl http://local-nmserver/cgi-bin/play?alarme.wav"

#### Usando RESTful Command

    /homeassistant/configuration.yaml

    rest_command:
      play_alarme:
        url: "http://local-nmserver/cgi-bin/play?alarme.wav"
        method: GET

#### RESTful Command

    https://www.home-assistant.io/integrations/rest_command/
