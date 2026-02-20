# Wi-Fi di Ateneo

Sapienza offre a studenti, dottorandi, assegnisti di ricerca, ricercatori, personale docente e tecnico-amministrativo due reti wireless: **Sapienza** ed **Eduroam**. Entrambe consentono una navigazione veloce utilizzando le credenziali universitarie, ma presentano alcune differenze significative.

## Rete Sapienza

La rete wireless Sapienza utilizza un sistema di autenticazione chiamato Captive Portal:

1. Connettiti alla rete WiFi "Sapienza".
2. Apparirà automaticamente una pagina di login.
3. Inserisci le tue credenziali universitarie (username e password).
4. Una volta effettuato l'accesso, potrai navigare liberamente.

La rete Sapienza richiede il login ogni volta che ci si collega, cosa che può risultare poco pratica per un uso frequente. Per questo motivo, è consigliabile considerare l'utilizzo della rete Eduroam per un accesso più agevole.

## Rete Eduroam

Eduroam (education roaming) è un servizio internazionale di roaming wireless progettato per facilitare l'accesso a internet a studenti e personale universitario. Questo servizio offre diversi vantaggi:

- Permette di connettersi a reti WiFi in numerose istituzioni accademiche in tutto il mondo.
- Utilizza le stesse credenziali fornite dall'ateneo Sapienza.
- Una volta configurata, la connessione avviene automaticamente senza necessità di login ripetuti.

{{% hint warning %}}
<i class="fa-solid fa-triangle-exclamation" style="color: #FFD43B;"></i> **Attenzione**

A differenza della rete Sapienza, le credenziali per la rete Eduroam richiedono l'**email istituzionale** e la password di ateneo. L'email istituzionale è composta da COGNOME.MATRICOLA@studenti.uniroma1.it.
{{% /hint %}}

{{% hint tip %}}
<i class="fa-solid fa-lightbulb" style="color: #238636;"></i> **Sapevi che...**

La rete network di Eduroam è disponibile in tante università internazionali! Questo significa che, se tu volessi, potresti andare in un'altra università associata ad Eduroam e connetterti al suddetto network usando le stesse credenziali che useresti presso la Sapienza!
{{% /hint %}}

### Configurazione di Eduroam

{{% tabs "eduroamdevices" %}}
{{% tab "📱 Smartphone" %}}

Per accedere alla rete Eduroam tramite smartphone iOS e Android:

1. Scarica l'applicazione ufficiale **GetEduroam**:
   * [Download Android](https://play.google.com/store/apps/details?id=app.eduroam.geteduroam)
   * [Download iOS](https://apps.apple.com/no/app/geteduroam/id1504076137)
2. Apri l'app e segui la procedura guidata per configurare la rete.
{{% /tab %}}
{{% tab "💻 Laptop" %}}

Per accedere alla rete Eduroam tramite PC o Mac:

1. Visita il [sito ufficiale di Eduroam](https://cat.eduroam.org).
2. Scarica l'installer appropriato per il tuo sistema operativo.
3. Esegui l'installer e segui le istruzioni per completare la configurazione.

Su **Mac**, dopo il download:
1. Vai su **Impostazioni** > **Privacy e Sicurezza**.
2. Scorri fino in fondo e clicca su **Profili**.
3. Fai doppio click sul certificato **Eduroam**.
4. Premi su **Installa...** per completare la procedura.

Su **Linux** (Debian based): gli access point di Eduroam utilizzano TLSv1.0. A meno che la versione TLS non venga aggiornata a livello di hotspot, procedere in questo modo:
1. Scarica lo script di configurazione da CAT eduroam
2. Lancia `sudo nano /etc/NetworkManager/system-connections/<connection-ssid>.nmconnection` nel nostro caso, `eduroam`
3. Aggiungi la riga `phase1-auth-flags=32` come ultima nella sezione `[802-1x]`. Salva.
4. (Solo su Fedora) Lancia `sudo update-crypto-policies --set DEFAULT:SHA1` da terminale se sei su Fedora 42 o precedenti.
5. Riavvia sia `NetworkManager` che `wpa_supplicant` (lancia `sudo systemctl restart NetworkManager` e `sudo systemctl restart wpa_supplicant`)
6. D'ora in avanti, per connetterti a eduroam dovrai lanciare da terminale `sudo nmcli --ask connection up eduroam`. Ti chiederà di inserire la password del tuo account uniroma1: inseriscila e premi `ENTER`.

Tieni presente che mentre sei connesso a Eduroam il NetworkManager integrato al sistema operativo _non_ funzionerà (KDE Plasma) e vedrai comportamenti strani. Quando hai necessità di disconnetterti, utilizza sempre nmcli (es. `sudo nmcli --ask connection down eduroam`). NetworkManager tornerà a funzionare normalmente.


{{% /tab %}}
{{% /tabs %}}

## Quale rete scegliere?

- **Rete Sapienza**: Ideale per un uso occasionale o se incontri difficoltà con Eduroam.
- **Rete Eduroam**: Consigliata per l'uso quotidiano e se frequenti diverse istituzioni accademiche.
