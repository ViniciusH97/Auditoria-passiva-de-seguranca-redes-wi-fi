# Análise passiva de segurança em redes wi-fi

### Objetivo do projeto
Realizar uma auditoria passiva em redes wi-fi de quatro cidades da região, identificando redes que utilizam protocolos vulneráveis como WEP ou que estão com o WPS ativado, **sem se conectar a nenhuma rede**.

### Ferramentas e Métodos utilizados
- Celular Android com Termux (no-root)
  - Ferramentas: `termux-wifi-scaninfo`, `termux-location`, `date`.
  - Scripts Bash para escanear a cada 10 segundos (ônibus/carro) e 40 segundos (a pé).
  - Armazenamento em JSON com geolocalização, horário e segurança das redes wi-fi.

- Kali Linux
  - Ferramenta: `airodump-ng`, `nmcli`, `wash`, `iwlist`
  - Captura apenas de BSSID, ESSID, força de sinal e protocolos de segurança (WEP/WPA/WPA2/WPS)

### Locais 
- Wardriving e warwalking em quadro cidades distintas.

### Dados
- **Sem** captura de pacotes (apenas escaneamento passivo)
- Sem tentativas de conexão, autenticação ou desautenticação
- Apenas metadados: SSID, BSSID, Sinal, Canal, Capabilities.

### Resultados
- Grande quantidade de roteadores com WPS ativado.
- Ainda existem roteadores com WEP ativo.
- Os dados foram armazenados em arquivos JSON, analisados e filtrados por vulnerabilidades.
- Pretendo futuramente compartilhar mapas e dados anonimizados.

### Considerações Importantes
- Nenhuma rede foi acessada.
- Coleta feita de forma **anônima e passiva**.
- Projeto com fins **educacionais e de conscientização** sobre segurança em redes Wi-Fi.

### Passo a passo do que foi feito

1. Instalação das ferramentas mobile: As ferramentas não foram baixadas diretamente pelo Google Play, para utilizar as ferramentas com as versões mais recentes foi necessário instalar o [F-Droid](https://f-droid.org/), que é um catálogo de aplicativos android. Por essa plataforma instalei o _Termux_, _Termux:API_ e _Termux:Widget_

#### Para utilizar a ferramentas na versão mais atualizada, no primeiro momento deve-se atualizar para a ultima versão com o seguinte comando:
```bash
pkg apt updte # atualizar a lista de pacotes
```
e

```bash
pkg apt update # atualiza todos os pacotes instaalados
```

2. O _Termux:API_ pode ser baixado diretamente no F-Droid, nesse caso, deve ser instalado primeiramente o app _Termux:API_, e depois o pacote `termux-api` pelo `Termux`.
  - instalação do Termux:API: https://f-droid.org/packages/com.termux.api/
  - instalação do termux-api com o seguinte comando:
```bash
pkg install termux-api
```
3. Ao instalar a ferramenta, o próximo passo é testar com o comando `termux-location`, porém é necessário que o termux:api tenha permissões de uso do GPS(localização) do dispositivo móvel. Aleḿ disso, para que o comando funcione corretamente deve permanecer com a opção de GPS ativada.

- Para testar utilize o comando abaixo:
```bash
termux-location
```
O retorno do comando deve ser algo como:

```bash
~ $ termux-location
{
  "latitude": xx.xxxxxxxxx,
  "longitude": xx,xxxxxxxxx,
  "altitude": xxx,xxxxxxxxx,
  "accuracy": 13.63453197479248,
  "vertical_accuracy": 14.190823554992676,
  "bearing": 0.0,
  "speed": 0.0,
  "elapsedMs": 40,
  "provider": "gps"
}
~ $
```

> Script que foi utilizado no wardriving e warwalking: [scanf.sh](https://github.com/ViniciusH97/Auditoria-passiva-de-seguranca-redes-wi-fi/blob/main/scanwf.sh)

### Repositório em desenvolvimento...

### License
<a href="https://github.com/ViniciusH97/Auditoria-passiva-de-seguranca-redes-wi-fi">Auditoria passiva de segurança a redes wi-fi</a> © 2025 by <a href="https://github.com/ViniciusH97">ViniciusH97</a> is licensed under <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0</a>


[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
