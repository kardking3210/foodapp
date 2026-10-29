# SharePlate

SharePlate connects hotel and restaurant kitchens with nearby community members and clubs so surplus meals can be collected instead of wasted.

## Run locally

Requires Node.js 18 or newer. The server has no npm package dependencies.

From the project root, run:

```powershell
npm start
```

Open [http://localhost:3000](http://localhost:3000). Keep the terminal open while using SharePlate and press `Ctrl+C` to stop it. To use another port, set the `PORT` environment variable before starting the server.

The server binds to this computer only (`127.0.0.1`). Accounts, offers, and reservations are stored in `data.json` beside the server. That file is ignored by Git. Sign-in sessions last seven days.

## MVP features

- Accounts for hotel kitchens, restaurants and cafes, community clubs, and community members.
- Food offers with meal count, price or donation, pickup area and window, optional GPS pin, meal details, and known allergens.
- Search, offer filters, distance sorting, directions, and an interactive map.
- Partial reservations: members choose a meal count, and cancelled reservations return meals to availability.
- Six-digit pickup codes that food businesses verify at handoff.
- Optional club-first donation fallback for unclaimed discounted offers.
- A public hotel lookup within 5 km. Enter an area or choose GPS; results appear on the map and in the hotel list.

### Location and map services

Browser GPS is requested only after a user chooses a location action. GPS sorting stays in the browser. Searching hotels by area sends the typed place name to OpenStreetMap Nominatim and then searches OpenStreetMap Overpass for hotels within 5 km. Searching by GPS sends the selected coordinates to Overpass. Area and hotel results are cached for the browser session, and area searches are rate-limited. Hotel lookup tries two global Overpass services in sequence with a short timeout per service, so a slow endpoint does not hold up the whole search.

The map uses Leaflet and OpenStreetMap tiles, so it needs an internet connection. Map data is attributed to [OpenStreetMap contributors](https://www.openstreetmap.org/copyright). The public tile service is best-effort and subject to its [tile usage policy](https://operations.osmfoundation.org/policies/tiles/). Area search follows the [Nominatim usage policy](https://operations.osmfoundation.org/policies/nominatim/). Use a dedicated map and geocoding provider or self-hosted services before a public or commercial launch.

## Deployment status

This is a locally hosted MVP, not a public production service. A public launch needs a hosted database, backups and restore procedures, monitoring, and a map provider sized for expected traffic.
