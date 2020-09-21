# Full Stack Challenge
#### [Find the Design with some instructions here](https://www.figma.com/file/9nHoPcsaW5BqMuDlYMWnVC/Gastronaut-FullStack-Challenge?node-id=0%3A1)

* [ ] Recreate Screen using the following Technologies ()
  * [ ] React (create-react-app)
  * [ ] @material-ui (see below)
  * [ ] axios (https://www.npmjs.com/package/axios)
  * [ ] use functional components (We mostly use Arrow functions over Class and since we mostly use Hooks you should be able to work with them)
  * [ ] use React-Hooks like, useEffect, useState, etc.
* [ ] on page load get data from API and display it
* [ ] build bilingual user interface using the provided API
  * [ ] use the provided LanguageToggle to toggle between german ('de') and english ('de')
  * [ ] as default language take 'de' if the languageSettings of the browser include 'de' else use 'en'
  * [ ] get the translations as Object from https://api.gastronaut.ai/v02/language/codeTest/:language
* [ ] Restaurant Id will should provided in url /:restaurantId
* [ ] just build the view for mobile don't worry about larger screens
* [ ] Create a Git Repo with an initial Commit
* [ ] While loading cover the whole page and show a spinner (<CircularProgress /> from Material UI) in the center;
* [ ] Error Handle Errors by Showing an <Alert severity="error">{message}</Alert> from Material UI instead of the UI;

```javascript
  // GET https://api.gastronaut.ai/codeTest/:restaurantId
  // For Testing available restaurantIds: 'neo-heidelberg', 'schillingroofbar'
const apiResponse {
  homeAddress: 'Alte Glockengießerei 9 69115 Heidelberg',
  link: 'https://www.schillingroofbar.com', // Use this as href for the logo
  name: 'Schilling Roofbar', // For alt-texts as well as meta title
  image:
    'https://firebasestorage.googleapis.com/v0/b/schillingroofbarhd.appspot.com/o/schillingroofbar%2FfullScreen%20(1).jpg?alt=media&token=878b95ee-93a8-48d2-9b04-4982c8ec1a5c',
  logo:
    'https://firebasestorage.googleapis.com/v0/b/schillingroofbarhd.appspot.com/o/logo.png?alt=media&token=cb08cef7-ed00-46dc-a695-5b933a11fa45',
  colorPalette: { primaryColor: '#ce9933', contrastText: '#ffffff' },
  products: ['reservation', 'voucher', 'menu', 'delivery'],
  regularHours: [
    // Array with 7 elements for each Weekday (null means closed)
    '18:00 - 00:00',
    null,
    '18:00 - 00:00',
    '18:00 - 00:00',
    '18:00 - 00:00',
    '18:00 - 00:00',
    '18:00 - 00:00'
  ],
  events: [
    // Array with upcoming events.
    {
      id: 1,
      date: '2020-09-30', // dates will always be in this format YYYY-MM-DD
      title: 'Test Event',
      status: 'BOOKABLE', // Can be either BOOKABLE or CLOSED if Close print closed;
      priceStartingAt: 69, // Only available when BOOKABLE you may display this (from 69€)
      currency: 'eur', // Only available when BOOKABLE
      available: true, // Only available when BOOKABLE if available show ticket button
      link: 'https://www.gastronaut.ai' // Link just for Testing
    }
  ]
}



// GET https://api.gastronaut.ai/v02/language/codeTest/:language
// Currently Available: de, en
const languageResponse = {
  date: {
    weekdays: [
      'So. der',
      'Mo. der',
      'Di. der',
      'Mi. der',
      'Do. der',
      'Fr. der',
      'Sa der'
    ],
    today: 'Heute',
    tomorrow: 'Morgen'
  },
  closed: 'Geschlossen',
  reservationButtonSmall: 'Reservieren',
  reservationButton: 'Tisch Reservieren',
  ticketButton: 'Ticket kaufen',
  menuButton: 'Menü anzeigen',
  deliveryButton: 'Essen bestellen',
  voucherButton: 'Gutschein kaufen',
  restaurantNotFound: 'Restaurant konnte nicht gefunden werden.'
};

```

## LINK FOR BUTTONS
- reservationButton => https://r.gastronaut.ai/:restaurantId (when small button is clicked add date to url ...?date=2020-09-21 )
- voucherButton => https://v.gastronaut.ai/:restaurantId (Link will not work...)
- ticketButton => https://t.gastronaut.ai/:restaurantId/:ticketId (Link will not work...)
- menuButton => https://menu.gastronaut.ai/:restaurantId (Link will not work...)

## HOW TO WORK WITH MATERIAL UI

```javascript
// get the documentation from https://material-ui.com
import { createMuiTheme, ThemeProvider } from '@material-ui/core/styles';
// Implement it in .App.js as follows:
const [restaurantTheme, setRestaurantTheme] = useState({
  primaryColor: '#d0d0d0', // default Value on load replace this with colorPalette
  contrastText: '#000000' // default Value
});

const theme = createMuiTheme({
  palette: {
    primary: {
      main: restaurantTheme.primaryColor,
      contrastText: restaurantTheme.contrastText
    }
  }
});

//Wrap Layout with API Provide
<ThemeProvider theme={theme}>// ...paste your Layout here</ThemeProvider>;
```

You have no time pressure, this task should'nt take to long. when you're done please clean up your code and push it to a github rep to share it with us.

Disclaimer: We will not use this work if we don't hire you, but you are free to use this in your portfolio (NOT IN PRODUCTION FOR ANY COMPANY OR YOURSELF.

## Have Fun!
