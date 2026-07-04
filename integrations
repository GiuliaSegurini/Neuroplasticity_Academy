// ===== NEUROPLASTICITY TRAINING ACADEMY =====
// Integrations Config

const CONFIG = {
  mailerlite: {
    apiKey: 'mlsn.5a46c4ea0cf7c1d52cab40400493c74dc65a28f029a4598b08bbfed9628f5444',
    group: 'neuroplasticity_academy',
    apiUrl: 'https://connect.mailerlite.com/api'
  },
  whatsapp: {
    token: 'EAAdknYNQJDMBR70uROPHjApI6MH7kD4vBJBTz1FOOrzrZChP2K4UMHNYyQ7M3S7ROyfSYjcgeKhBlsC8RPZCZCWuPxmSb9U3Vd4yg8Haf1cEOw9gjJceRW2gdWCCiwfRxZAhiZCZBtg9nTJzdIoMaleKBWhzfhLLLLkTuHbkAjPv6a7iQBwSE7NpZB1uVXcTL2qPW8LWF8zLJ1dXMeB2I2OeKCkPi1MxrSeWZC69hxyTWnq7etRpUCO7n6ARWXJreeEXZAjz7MeAaHPTjJlr9fnfUVk4XRrD7rnt1g5MZD',
    phoneNumberId: '1189992294198133',
    notifyNumber: '393512935820', // es: 393401234567
    apiUrl: 'https://graph.facebook.com/v18.0'
  }
};

// ===== MAILERLITE: Aggiungi subscriber =====
async function addToMailerLite(email, name, fields = {}) {
  try {
    // Prima ottieni il group ID dal nome
    const groupRes = await fetch(`${CONFIG.mailerlite.apiUrl}/groups?filter[name]=neuroplasticity_academy`, {
      headers: {
        'Authorization': `Bearer ${CONFIG.mailerlite.apiKey}`,
        'Content-Type': 'application/json'
      }
    });
    const groupData = await groupRes.json();
    const groupId = groupData.data?.[0]?.id;

    if (!groupId) {
      console.log('Group not found, adding subscriber without group');
    }

    // Aggiungi subscriber
    const res = await fetch(`${CONFIG.mailerlite.apiUrl}/subscribers`, {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${CONFIG.mailerlite.apiKey}`,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        email,
        fields: { name, ...fields },
        groups: groupId ? [groupId] : []
      })
    });

    const data = await res.json();
    console.log('MailerLite:', data.data?.email || 'added');
    return data;
  } catch(e) {
    console.log('MailerLite error:', e);
  }
}

// ===== WHATSAPP: Notifica a Giulia =====
async function notifyWhatsApp(customerName, customerEmail, product, scores = {}) {
  if (!CONFIG.whatsapp.phoneNumberId || CONFIG.whatsapp.phoneNumberId.includes('SOSTITUISCI')) return;

  const message = `🧠 *Nuova iscrizione!*\n\nNome: ${customerName}\nEmail: ${customerEmail}\nProdotto: ${product}\n${scores.summary || ''}`;

  try {
    await fetch(`${CONFIG.whatsapp.apiUrl}/${CONFIG.whatsapp.phoneNumberId}/messages`, {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${CONFIG.whatsapp.token}`,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        messaging_product: 'whatsapp',
        to: CONFIG.whatsapp.notifyNumber,
        type: 'text',
        text: { body: message }
      })
    });
    console.log('WhatsApp notified');
  } catch(e) {
    console.log('WhatsApp error:', e);
  }
}

// ===== SEND RESULTS VIA WHATSAPP (to customer) =====
async function sendResultsWhatsApp(phone, name, scores) {
  if (!CONFIG.whatsapp.phoneNumberId || CONFIG.whatsapp.phoneNumberId.includes('SOSTITUISCI')) return;
  if (!phone) return;

  const weakAreas = Object.entries(scores)
    .filter(([k, v]) => v < 50)
    .map(([k]) => k)
    .join(', ') || 'nessuna area critica';

  const message = `Ciao ${name}! 🧠\n\nHo analizzato il tuo baseline neurocognitivo.\n\nArea prioritaria: *${weakAreas}*\n\nIl tuo protocollo personalizzato è pronto.\n\n→ Accedi all'Academy: neuroplasticitytraining.it/checkout\n\nGiulia — Neuroplasticity Training Academy`;

  try {
    await fetch(`${CONFIG.whatsapp.apiUrl}/${CONFIG.whatsapp.phoneNumberId}/messages`, {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${CONFIG.whatsapp.token}`,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        messaging_product: 'whatsapp',
        to: phone.replace(/\D/g,''),
        type: 'text',
        text: { body: message }
      })
    });
    console.log('Results sent via WhatsApp');
  } catch(e) {
    console.log('WhatsApp send error:', e);
  }
}
