# MAILERLITE AUTOMATION SETUP
# Neuroplasticity Training Academy
# Copia questi template direttamente in MailerLite

═══════════════════════════════════════
EMAIL 1 — IMMEDIATA (trigger: iscrizione gruppo)
═══════════════════════════════════════

SUBJECT:
I tuoi risultati del baseline neurocognitivo 🧠

PREVIEW TEXT:
Il tuo profilo è pronto. Ecco cosa abbiamo scoperto.

BODY (plain text, funziona meglio):
---
Ciao {{name}},

Il tuo baseline neurocognitivo è completato.

Ecco quello che abbiamo misurato su 6 dimensioni del funzionamento cerebrale:

→ Il tuo profilo è nel tuo account Academy
→ Il protocollo personalizzato è calibrato sui tuoi risultati

Il primo passo che ti consiglio di fare oggi?

Il protocollo di respirazione. Effetto immediato sul sistema nervoso, zero effort.
Ci vogliono 5 minuti: neuroplasticitytraining.it/respiro

Poi, quando sei pronta, inizia il training completo:
→ neuroplasticitytraining.it/checkout

Il tuo cervello è plastico. Iniziamo.

Giulia
Neuroplasticity Training Academy
neuroplasticitytraining.it

---
CTA BUTTON: "Inizia il Training →" → neuroplasticitytraining.it/checkout


═══════════════════════════════════════
EMAIL 2 — DAY 3
═══════════════════════════════════════

SUBJECT:
Come stai dopo il test? (una domanda)

PREVIEW TEXT:
Ho pensato a te. Rispondo personalmente.

BODY:
---
Ciao {{name}},

Ti ho pensato in questi giorni.

Hai visto i tuoi risultati. Hai una mappa del tuo funzionamento cognitivo.

Ma una mappa senza un piano è solo carta.

La cosa che vedo più spesso è questa:
le persone fanno il test, vedono dove sono vulnerabili,
e poi... non fanno niente.

Non perché non vogliano cambiare.
Ma perché non sanno da dove iniziare.

Per questo ho costruito il protocollo.

Non è "leggi questo PDF".
È un sistema di 30 giorni che allena il tuo cervello come si allena un musicista:
più sistemi insieme, ogni giorno, in modo misurabile.

Se sei pronta a iniziare:
→ neuroplasticitytraining.it/checkout

Se hai domande, rispondi a questa email.
Rispondo io, personalmente.

Giulia

---
CTA BUTTON: "Inizia il Tuo Protocollo →" → neuroplasticitytraining.it/checkout


═══════════════════════════════════════
EMAIL 3 — DAY 7
═══════════════════════════════════════

SUBJECT:
Il tuo cervello si allena o no?

PREVIEW TEXT:
Una settimana fa hai scoperto il tuo profilo.

BODY:
---
Ciao {{name}},

Una settimana fa hai scoperto come funziona il tuo cervello.

Ti chiedo una cosa diretta:

Hai iniziato ad allenarlo?

Se sì → scrivimi. Voglio sapere come va.

Se no → capisco. La vita è piena di cose urgenti.
Ma il tuo cervello non aspetta.

La neuroplasticity è massimale a 25-45 anni.
Non tra 10 anni. Adesso.

Quello che fai nei prossimi 30 giorni
si misura in risultati reali: focus, memoria, regolazione emotiva.

€39 al mese. 15 minuti al giorno.
Risultati misurabili in 30 giorni.

→ neuroplasticitytraining.it/checkout

Se invece senti che c'è qualcosa di più profondo
(ansia, trauma, difficoltà di apprendimento, emozioni difficili da gestire),
il percorso clinico con me è il posto giusto:
→ neuroplasticitytraining.it (sezione Percorso Clinico)

A presto,
Giulia

---
CTA BUTTON: "Accedi all'Academy €39/mese →" → neuroplasticitytraining.it/checkout


═══════════════════════════════════════
EMAIL 4 — POST ACQUISTO (trigger: campo "source" = "checkout")
═══════════════════════════════════════

SUBJECT:
Benvenuta nell'Academy ✓

PREVIEW TEXT:
Il tuo accesso è confermato. Inizia da qui.

BODY:
---
Ciao {{name}},

Pagamento confermato. Sei dentro.

Ecco i tuoi accessi:

🫁 INIZIA OGGI — Protocollo Respiro
→ neuroplasticitytraining.it/respiro
(Effetto immediato. Fallo adesso.)

🧠 ASSESSMENT COMPLETO
→ neuroplasticitytraining.it/assessment
(Se non lo hai ancora fatto, inizia da qui.)

🎮 MINI TRAINING
→ neuroplasticitytraining.it/training
(Memoria + ritmo. 5 minuti.)

Nelle prossime 24 ore ti scrivo personalmente
per impostare il tuo piano specifico.

Se hai domande, rispondi a questa email.

Giulia
Neuroplasticity Training Academy

---
CTA BUTTON: "Inizia il Respiro →" → neuroplasticitytraining.it/respiro


═══════════════════════════════════════
SETUP IN MAILERLITE
═══════════════════════════════════════

AUTOMATION 1: "Sequenza Assessment"
Trigger: Subscriber aggiunto al gruppo "neuroplasticity_academy"

Step 1: Invia Email 1 (immediato)
Step 2: Aspetta 3 giorni
Step 3: Invia Email 2
Step 4: Aspetta 4 giorni
Step 5: Invia Email 3

---

AUTOMATION 2: "Post Acquisto"
Trigger: Campo personalizzato "source" = "checkout"
(questo campo viene impostato da integrations.js quando qualcuno paga)

Step 1: Invia Email 4 (immediato)
Step 2: Rimuovi dalla sequenza "Sequenza Assessment" (per non ricevere email doppie)

═══════════════════════════════════════
STRIPE: Aggiungi success URL ai Payment Links
═══════════════════════════════════════

Per ogni payment link su Stripe:
→ Modifica payment link
→ "After payment" → "Redirect customers to your website"
→ URL: https://neuroplasticity-academy.vercel.app/grazie?plan=assessment

Per Training Basic:
→ URL: https://neuroplasticity-academy.vercel.app/grazie?plan=basic

Per Premium:
→ URL: https://neuroplasticity-academy.vercel.app/grazie?plan=premium
