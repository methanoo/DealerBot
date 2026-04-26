&nbsp;

<div align="center">

# DealerBot: Documentazione Telecomandi
    Sistema di distribuzione carte automatizzato via segnale Infrarosso (NEC).
</div>
&nbsp;
&nbsp;
&nbsp;
&nbsp;

## Architettura Hardware

<div align="center">
<img src="https://i.imgur.com/kS9Gw3v.png" width="450" alt="Schema Circuitale">
<p style="font-size: 0.9em; color: gray; margin-top: 10px;">
<i>Configurazione pinout: ATtiny85 collegato a un LED IR da 940nm e pulsante (Alimentazione 3V).</i>
</p>
</div>
&nbsp;

!!! abstract "Logica di Funzionamento"
    Ogni giocatore possiede un telecomando a tasto singolo. Premendo il pulsante, l'ATtiny85 invia un comando specifico che il mazziere centrale riconosce per distribuire la carta al giocatore corrispondente.

<br>

## Mappatura Segnali (Protocollo NEC)


| ID Giocatore | Chiamata Funzione | Valore HEX (Raw) 
| :---: | :---:| :---: |
| 👤 **01** | `sendNEC(1, 0x0, 0xC, 0);`  | `F30CFF00` |
| 👤 **02** | `sendNEC(1, 0x0, 0x18, 0);` | `E718FF00` | 
| 👤 **03** | `sendNEC(1, 0x0, 0x5E, 0);` | `A15EFF00` | 
| 👤 **04** | `sendNEC(1, 0x0, 0x8, 0);`  | `F708FF00` | 
| 👤 **05** | `sendNEC(1, 0x0, 0x1C, 0);` | `E31CFF00` |
| 👤 **06** | `sendNEC(1, 0x0, 0x5A, 0);` | `A55AFF00` |
| 👤 **07** | `sendNEC(1, 0x0, 0x42, 0);` | `BD42FF00` | 


&nbsp;


## Firmware e Programmazione


=== "Arduino ISP (Programmazione)"

    #### 1. Setup Arduino come Programmatore
    * Collega **SOLAMENTE** l'Arduino Uno al PC.
    * Vai su `File` > `Esempi` > `11.ArduinoISP` > `ArduinoISP`.
    * Carica lo sketch sull'Arduino Uno.

    #### 2. Collegamenti ATtiny85
    Ora puoi collegare l'Arduino UNO all'ATtiny85, i collegamenti sono i seguenti:
    | Arduino Uno (Master) | ATtiny85 (Target) | Pin Fisico ATtiny |
    | :--- | :--- | :---: |
    | **5V** | VCC | 8 |
    | **GND** | GND | 4 |
    | **Pin 10** | Reset | 1 |
    | **Pin 11** | MOSI | 5 |
    | **Pin 12** | MISO | 6 |
    | **Pin 13** | SCK | 7 |

    #### 3. Impostazioni IDE e Bootloader
    * **Scheda:** `ATtiny25/45/85`
    * **Processor:** `ATtiny85`
    * **Clock:** `Internal 1 MHz` (Ottimale per batteria 3V)
    * **Programmer:** `Arduino as ISP`
    <br><br>
    !!! info "Arrivati a questo punto si può passare alla prossima scheda: Trasmettitore (ATtiny85)"
        

=== "Trasmettitore (ATtiny85)"

    !!! warning "Personalizzazione Obbligatoria"
        Modifica la **linea 14** inserendo il codice assegnato al giocatore specifico preso dalla tabella sopra.

    ```cpp linenums="1" hl_lines="14"
    #include <Arduino.h>
    #include <TinyIRSender.hpp>

    #define IR_PIN 1      // (1)
    #define BUTTON_PIN 2  // (2)

    void setup() {
    pinMode(BUTTON_PIN, INPUT_PULLUP); 
    }

    void loop() {
    if (digitalRead(BUTTON_PIN) == LOW) {

        sendNEC(1, 0x0, 0xC, 0);
        
        delay(500); 
    }
    }
    ```

    1.  **Pin Fisico 6**: Collegamento LED IR (Anodo).
    2.  **Pin Fisico 7**: Collegamento Pulsante (verso GND).
    <br>
    !!! danger "Step Finale"
        Prima clicca su **Strumenti > Scrivi Bootloader**, poi carica lo sketch tramite **Sketch > Carica tramite programmatore**. <br>
        In caso di non funzionamento consultare la prossima scheda: **Debugger (Ricevitore)**

=== "Debugger (Ricevitore)"

    Usa questo codice per intercettare i segnali e verificare i telecomandi.

    ```cpp linenums="1"
    #include <IRremote.hpp>
    #define IR_RECEIVE_PIN 11

    void setup() {
    Serial.begin(9600);
    IrReceiver.begin(IR_RECEIVE_PIN, ENABLE_LED_FEEDBACK); 
    }

    void loop() {
    if (IrReceiver.decode()) {
        Serial.print("Codice Ricevuto: ");
        Serial.println(IrReceiver.decodedIRData.decodedRawData, HEX); 
        IrReceiver.resume();
    }
    }
    ```
