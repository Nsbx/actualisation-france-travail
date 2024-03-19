<script>
  import Const from '../utils/const';
  import download from '../utils/download';
  import * as ics from 'ics';

  const REFRESH_EVENT_TITLE = 'Actualisation France Travail';

  const REFRESH_EVENTS = [
    { title: 'Janvier 2024',   start: [2024, 1, 28],  end: [2024, 2, 1] },
    { title: 'Février 2024',   start: [2024, 2, 28],  end: [2024, 3, 1] },
    { title: 'Mars 2024',      start: [2024, 3, 28],  end: [2024, 4, 2] },
    { title: 'Avril 2024',     start: [2024, 4, 28],  end: [2024, 5, 2] },
    { title: 'Mai 2024',       start: [2024, 5, 28],  end: [2024, 6, 3] },
    { title: 'Juin 2024',      start: [2024, 6, 28],  end: [2024, 7, 2] },
    { title: 'Juillets 2024',  start: [2024, 7, 28],  end: [2024, 8, 1] },
    { title: 'Août 2024',      start: [2024, 8, 28],  end: [2024, 9, 2] },
    { title: 'Septembre 2024', start: [2024, 9, 28],  end: [2024, 10, 1] },
    { title: 'Octobre 2024',   start: [2024, 10, 28], end: [2024, 11, 4] },
    { title: 'Novembre 2024',  start: [2024, 11, 28], end: [2024, 12, 2] },
    { title: 'Décembre 2024',  start: [2024, 12, 28], end: [2025, 1, 2] },
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
