<script>
  import Const from '../utils/const';
  import download from '../utils/download';
  import * as ics from 'ics';

  const PAYMENT_EVENT_TITLE = 'Paiement France Travail';
  const PAYMENT_EVENT_DESCRIPTION = 'Paiement France Travail';

  const PAYMENT_EVENTS = [
    { title: 'Janvier 2025',   start: [2025, 2, 1] },
    { title: 'Février 2025',   start: [2025, 3, 3] },
    { title: 'Mars 2025',      start: [2025, 4, 2] },
    { title: 'Avril 2025',     start: [2025, 5, 2] },
    { title: 'Mai 2025',       start: [2025, 6, 2] },
    { title: 'Juin 2025',      start: [2025, 7, 2] },
    { title: 'Juillets 2025',  start: [2025, 8, 1] },
    { title: 'Août 2025',      start: [2025, 9, 2] },
    { title: 'Septembre 2025', start: [2025, 10, 1] },
    { title: 'Octobre 2025',   start: [2025, 11, 3] },
    { title: 'Novembre 2025',  start: [2025, 12, 2] },
    { title: 'Décembre 2025',  start: [2025, 1, 2] },
  ]

  let refreshEvents = [];

  PAYMENT_EVENTS.forEach((event) => {
    event.title = PAYMENT_EVENT_TITLE + ' - ' + event.title;
    event.description = 'Paiement à partir de cette date (plus tard si actualisation tardive)';
    event.url = Const.FRANCE_TRAVAIL_URL;
    refreshEvents.push(event)
  })

  const { error, value } = ics.createEvents(refreshEvents);
  
  const onClick = () => {
    download('france-travail-paiement.ics', value)
  }
</script>

<button on:click={onClick}>
  Télécharger les événements de Paiement
</button>
