---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-17"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}

# Pacchetto {{site.data.keyword.visualrecognitionshort}}

Il servizio {{site.data.keyword.visualrecognitionfull}} utilizza gli algoritmi di apprendimento approfondito (deep learning) per identificare scene, oggetti e volti nelle immagini che carichi nel servizio. Puoi creare e formare un classificatore personalizzato per identificare i soggetti adatti alle tue esigenze.
{:shortdesc}

Il pacchetto {{site.data.keyword.visualrecognitionshort}} contiene le seguenti entità. Puoi trovare ulteriori dettagli nella guida di riferimento API {{site.data.keyword.visualrecognitionshort}} facendo clic sul nome dell'entità.

| Entità | Tipo | Parametri | Descrizione |
| --- | --- | --- | --- |
| [`visual-recognition-v3`](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html) | pacchetto | username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,  | Lavorare con il servizio {{site.data.keyword.visualrecognitionshort}}. |
| [classify](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#classify) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    images_file,     accept_language,     url,     threshold,     owners,     classifier_ids,     images_file_content_type,  | Classificare le immagini. |
| [detect-faces](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#detect-faces) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    images_file,     url,     images_file_content_type,  | Rilevare i volti nelle immagini. |
| [create-classifier](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#create-classifier) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    name,     classname_positive_examples,     negative_examples,  | Creare un classificatore. |
| [delete-classifier](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#delete-classifier) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    classifier_id,  | Eliminare un classificatore. |
| [get-classifier](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#get-classifier) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    classifier_id,  | Richiamare i dettagli del classificatore. |
| [list-classifiers](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#list-classifiers) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    verbose,  | Richiamare un elenco di classificatori. |
| [update-classifier](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#update-classifier) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    classifier_id,     classname_positive_examples,     negative_examples,  | Aggiornare un classificatore. |
| [get-core-ml-model](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#get-core-ml-model) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    classifier_id,  | Richiamare un modello Core ML di un classificatore. |
| [delete-user-data](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#delete-user-data) | azione |  username, password,  iam_access_token, iam_apikey, iam_url,  headers, headers[X-Watson-Learning-Opt-Out], url,    customer_id,  | Eliminare i dati etichettati. |

## Creazione di un'istanza del servizio {{site.data.keyword.}}
{: #service_instance}

Prima di installare il pacchetto, devi creare un'istanza del servizio {{site.data.keyword.}} e le credenziali del servizio.
{: shortdesc}

1. [Crea un'istanza del servizio {{site.data.keyword.}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/watson_vision_combined).
2. Quando l'istanza del servizio viene creata, vengono anche create per tuo conto le credenziali del servizio generate automaticamente.

## Installazione del pacchetto {{site.data.keyword.}}
{: #install}

Una volta che disponi di un'istanza del servizio {{site.data.keyword.}}, utilizza la CLI {{site.data.keyword.openwhisk}} per installare il pacchetto {{site.data.keyword.}} nel tuo spazio dei nomi.
{: shortdesc}

### Installazione dalla CLI {{site.data.keyword.openwhisk_short}}
{: #visualrecognition_cli}

Prima di iniziare:
  1. [Installa il plug-in {{site.data.keyword.openwhisk_short}} per la CLI {{site.data.keyword.Bluemix_notm}}](bluemix_cli.html#cloudfunctions_cli).
  2. Installa il comando [`wskdeploy` ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://github.com/apache/incubator-openwhisk-wskdeploy/releases) e aggiungi il file binario scaricato al tuo PERCORSO.

Per installare il pacchetto {{site.data.keyword.}}:

1. Clona il repository del pacchetto {{site.data.keyword.}}.
    ```
    git clone https://github.com/watson-developer-cloud/openwhisk-sdk
    ```
    {: pre}

2. Distribuisci il pacchetto.
    ```
    wskdeploy -m openwhisk-sdk/packages/visual-recognition-v3/manifest.yaml
    ```
    {: pre}

3. Verifica che il pacchetto venga aggiunto al tuo elenco pacchetti.
    ```
    ibmcloud fn package list
    ```
    {: pre}

    Output:
    ```
    packages
    /myOrg_mySpace/visual-recognition-v3                        private
    ```
    {: screen}

4. Esegui il bind delle credenziali dall'istanza {{site.data.keyword.}} che hai creato al pacchetto.
    ```
    ibmcloud fn service bind watson-vision-combined visual-recognition-v3
    ```
    {: pre}

    Output di esempio:
    ```
    Credentials 'Credentials-1' from 'watson-vision-combined' service instance 'Watson Visual Recognition' bound to 'visual-recognition-v3'.
    ```
    {: screen}

5. Verifica che il pacchetto sia configurato con le tue credenziali dell'istanza del servizio {{site.data.keyword.}}.
    ```
    ibmcloud fn package get visual-recognition-v3 parameters
    ```
    {: pre}

    Output di esempio:
    ```
    ok: got package visual-recognition-v3, displaying field parameters
    [
      {
        "key": "__bx_creds",
        "value": {
          "watson-vision-combined": {
            "apikey": "AA1Aa111AAA1aaAA1AAAAaaAaaa1AAAA1AaAA1",
            "credentials": "Auto-generated service credentials",
            "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:language-translator:us-south:a/a11a1a11aa111a111aa1aa1111a1a111:1111a11-aaa1-11a1-111a-1a1111a11111::",
            "iam_apikey_name": "auto-generated-apikey-aa1a1a1-aa1a-11a1-a1aa-aa11aa1a11a1",
            "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Manager",
            "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/a11a1a11aa111a111aa1aa1111a1a111::serviceid:ServiceId-11a1111-11a1-1111-1111-aaa11a11a11a",
            "instance": "Watson Visual Recognition-g2",
            "url": "https://gateway.watsonplatform.net/visual-recognition/api"
          }
        }
      }
    ]
    ```
    {: screen}

### Installazione dall'IU {{site.data.keyword.openwhisk_short}}
{: #visualrecognition_ui}

1. Nella console {{site.data.keyword.openwhisk_short}}, vai alla [pagina Crea ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/openwhisk/create).

2. Utilizzando gli elenchi **Organizzazione Cloud Foundry** e **Spazio Cloud Foundry**, seleziona lo spazio dei nomi in cui vuoi installare il pacchetto {{site.data.keyword.cos_short}}. Gli spazi dei nomi sono formati dai nomi di organizzazione e spazio combinati.

3. Fai clic su **Installa pacchetti**.

4. Fai clic sul gruppo di pacchetti **Watson**.

5. Fai clic sul pacchetto **Visual Recognition**.

5. Fai clic su **Installa**.

6. Dopo che il pacchetto è stato installato, verrai reindirizzato alla pagina Azioni e puoi cercare il tuo nuovo pacchetto, che è denominato **visual-recognition-v3**.

7. Per utilizzare le azioni nel pacchetto **visual-recognition-v3**, devi eseguire il bind delle credenziali del servizio alle azioni.
  * Per eseguire il bind delle credenziali del servizio a tutte le azioni nel pacchetto, attieniti ai passi 5 e 6 nelle istruzioni della CLI sopra elencate. 
  * Per eseguire il bind delle credenziali del servizio a singole azioni, completa la seguente procedura nell'IU. **Nota**: devi completare la seguente procedura per ogni azione che desideri utilizzare.
    1. Fai clic su un'azione dal pacchetto **visual-recognition-v3** che vuoi utilizzare. Viene aperta la pagina dei dettagli per tale azione. 
    2. Nella navigazione sulla sinistra, fai clic sulla sezione **Parametri**. 
    3. Immetti un nuovo **parametro**. Per la chiave, immetti `__bx_creds`. Per il valore, incolla l'oggetto JSON delle credenziali del servizio dall'istanza del servizio che hai creato in precedenza.

## Utilizzo del pacchetto {{site.data.keyword.visualrecognitionshort}}
{: #usage}

Per utilizzare le azioni in questo pacchetto, esegui i comandi nel seguente formato:

```
ibmcloud fn action invoke visual-recognition-v3/<nome_azione> -b -p <param name> <param>
```
{: pre}

Tutte le azioni richiederanno un parametro della versione nel formato AAAA-MM-GG. Quando l'API viene modificata in un modo non compatibile con le versioni precedenti, viene rilasciata una nuova data di versione. Ulteriori dettagli sono disponibili nella [guida di riferimento API](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/curl.html?curl#versioning).

Le funzioni di questo pacchetto utilizzano la versione corrente di Visual Recognition, 2018-03-19. Prova l'azione `list-classifiers`.
```
ibmcloud fn action invoke visual-recognition-v3/list-classifiers -b -p version 2018-03-19
```
{: pre}
