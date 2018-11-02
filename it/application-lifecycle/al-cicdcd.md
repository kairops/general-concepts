# Ciclo de Vida: CI-CD-CD

Contenido:

- [Introducción](../application-lifecicle.md)
- [Ciclo de vida: Evolución y adaptación](al-evolution-and-adaptation.md)
- **CI-CD-CD**
- [Entregabilidad](al-releasability.md)
- [Pipeline](al-pipeline.md)
- [Changelog](al-changelog.md)

Si tratta di tre concetti strettamente relativi col _Ciclo di Vita_:

- CI -  _Continuous Integration_ (Integrazione Continua): Pratica di sviluppo software nella quale i membri di un team integrano il loro lavoro frequentemente. L'obiettivo é trovare errori prima possibile.

- CD - _Continuous Delivery_ (Consegna continua): Paradigma di sviluppo software che garantisce che i cambi nel codice possano essere rilasciati in qualsiasi momento nell'ambiente di produzione.

- CD - _Continuous Deployment_ (Rilascio Continuo): Processo automatizzato di rilascio dei cambi in produzione. Generalmente é orchestrato con una pipeline in una serie di _passi_ o _stages_ che conducono il codice dall'uscita del PC dello sviluppatore fino al suo rilascio nell'ambiente produttivo in un unico processo.

Mediante pratiche di _Integrazione continua_ mischiamo frequentemente i nostri cambi nel branch principale di sviluppo per garantire che quello che stiamo sviluppando é sostenibile nell'applicazione e niente smette di funzionare. Questa garanzia si certifica con l'esecuzione di _tests_ di diverso tipo: unitari, funzionali, d'integrazione, di accettazione, di sicurezza, di rendimento, ecc.

Il concetto di _rilasciabilitá_ del software consiste in quelle attivitá che il team del progetto devono compiere per creare e mantenere automatismi che permettano un rilascio a produzione senza frizioni nell'applicazione. Proprio qui abbiamo una relazione diretta con il _rilascio continuo_.

Concludendo, grazie agli automatismi, se abbiamo esercitato bene la _consegnabilitá_ possiamo garantire che i cambi che abbiamo inetgrato nel branch principale di sviluppo si possano mettere in produzione in qualsiasi momento in modo sicuro, arrivando ad un grado di maturitá nel quale assicuriamo il _rilascio continuo_ dei cambi.

---

Successivo: [Consegnabilitá](al-releasability.md) - Andare alla [Pagina principale](../toc.md)
