# Building a Progressive Web App

Flipkart decided to shut down their desktop website and just be a mobile web app recently. In India, 80% of their users were on a 2g connection.

Obvious next step for Flipkart was to make an isomorphic/universal app. They adapted the App Shell architecture. All pages had a "Loading State" and a "Loaded State". They adapted the same placeholder style as Facebook for the Loading State.

## Offline First

Cache all UI except the dynamic data itself. Utilizing ServiceWorker to intercept all network requests and serve any cache you might actually have instead worrying about getting more UI from the actual internet.

Service Worker Strategies:

- Cache First
- Network First
- Fastest (Race) - The presenter's favorite strategy because it allows whatever is fastest to be returned.

Utilize SW Toolbox to handle all Service Worker routing.

The ultimate goal was for the user to **never** see loading white-space.

The user can even browse perviously visited pages on airplane mode.

## Rendering @ 60fps

GPU Rasterization:
```html
<meta name="viewport" content"width=device-width, minimum-scale=1.0">
```

## Add a Home Screen Icon

A manifest.json in your meta tags can allow your web app to have a great icon for a mobile device's home screen.

## Push Notifications

Chrome and Firefox allows notifications thanks to a Web Notification API:
bit.ly/webpushguide
