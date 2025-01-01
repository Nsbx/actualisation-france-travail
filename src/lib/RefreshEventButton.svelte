<script>
  import Const from '../utils/const';
  import download from '../utils/download';
  import * as ics from 'ics';

  const REFRESH_EVENT_TITLE = 'Actualisation France Travail';

  const REFRESH_EVENTS = [
    { title: 'Janvier 2025',   start: [2025, 1, 28],  end: [2025, 2, 15] },
    { title: 'Février 2025',   start: [2025, 2, 26],  end: [2025, 3, 15] },
    { title: 'Mars 2025',      start: [2025, 3, 28],  end: [2025, 4, 15] },
    { title: 'Avril 2025',     start: [2025, 4, 28],  end: [2025, 5, 15] },
    { title: 'Mai 2025',       start: [2025, 5, 28],  end: [2025, 6, 15] },
    { title: 'Juin 2025',      start: [2025, 6, 28],  end: [2025, 7, 15] },
    { title: 'Juillets 2025',  start: [2025, 7, 28],  end: [2025, 8, 15] },
    { title: 'Août 2025',      start: [2025, 8, 28],  end: [2025, 9, 15] },
    { title: 'Septembre 2025', start: [2025, 9, 28],  end: [2025, 10, 15] },
    { title: 'Octobre 2025',   start: [2025, 10, 28], end: [2025, 11, 15] },
    { title: 'Novembre 2025',  start: [2025, 11, 28], end: [2025, 12, 15] },
    { title: 'Décembre 2025',  start: [2025, 12, 28], end: [2026, 1, 15] },
  ]

  let refreshEvents = [];

  REFRESH_EVENTS.forEach((event) => {
    event.title = REFRESH_EVENT_TITLE + ' - ' + event.title;
    event.url = Const.FRANCE_TRAVAIL_URL;
    refreshEvents.push(event)
  })

  const { error, value } = ics.createEvents(refreshEvents);
  
  const onClick = () => {
    download('france-travail-actualisation.ics', value)
  }
</script>

<button on:click={onClick}>
  Télécharger les événements d'actualisation
</button>
