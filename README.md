# kinda-cicd

github link: https://github.com/Raigodo/kinda-cicd

comments:
nav izdevies aizvērt neeksitējošu pm2, tika izmēģinātas vairākas metodes, bet neviena no tām nestrādāja ne CMD ne PowerShell komandrindas rīkā:
* pm2 delete greetings-app-<vides_nosaukums>
* pm2 delete greetings-app-<vides_nosaukums> & set "errorlevel=0" 
* pm2 delete greetings-app-<vides_nosaukums> & EXIT /B 0

izpildot doto komandu lai startētu Flask API, PowerShell vidē tiek izvadīts kļūdas paziņojums:
    komanda:            pm2 start app.py --name greetings-app-dev -- --port 7001
    kļūdas paziņojums:  error: unknown option `--port' 

izpildot šo ašu konadu Cmd rīka vidē, šāda kļūda netiek uzrādīta, tomēr neatkarīgi no norādāmās porta vērtības, Flask API vienmēr tiek startēts izmantojot portu 3000, kas ir norādīts kodā
Nav izdevies atrast kā šo problēmu apiet

Lai turpinātu darba izpildi, tika pielāgots mocha projekts:
* pievienots papildus vides mainīgais "greetings-preprod"
* visiem vides mainīgajiem, kas attiecas uz izmantojamaiem "stage" poriem, tika iestatīta porta vērtība vienāda ar 3000

Lai mazinātu koda atkārtošanos, tika izmantoti Github Actions
