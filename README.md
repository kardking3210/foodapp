# SharePlate

A local full-stack prototype for sharing restaurant surplus food with nearby community members and clubs.

## Run locally

Requires Node.js 18 or newer. No third-party packages are needed.

```powershell
npm start
```

Open http://localhost:3000.

## Prototype flows

- Register as a restaurant, community club, or community member.
- Restaurants list discounted offers or club donations with meal count, price, location, date, and pickup window.
- Clubs and members reserve offers and see pickup details in **My activity**.
- Restaurants confirm completed pickups. Each confirmation adds 10 points to the restaurant Food Score, starting from 50.
- Accounts and offers persist in `data.json` in this folder. That file is excluded from Git.

This is a local prototype. It uses a lightweight JSON file store and cookie sessions; it is not configured for public production deployment.

- Use **Find near me** to sort/filter food by distance, or let a restaurant save GPS coordinates for directions. Browser location is requested only after the user clicks GPS. GPS works on localhost or HTTPS; browsers block it on ordinary HTTP network addresses.
