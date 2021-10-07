# App Store Badge

This repository contains the source code for web component that displays the "Get this app on the Microsoft Store" badge.

## Usage

Generate your own app badge using https://black-water-0eaf5100f.azurestaticapps.net/create-your-own.html

Alternately, add the following code in your HTML where you want the button to appear:

```html
<script type="module" src="https://getbadgecdn.azureedge.net/ms-store-badge.bundled.js"></script>
<ms-store-badge productid="9wzdncrfhvjl" size="large"></ms-store-badge>
```

The component has some additional configuration options:

| Option         | Type     | Default value | Description |
|--------------|-----------|------------|------------|
| productid | string  | undefined | Your app ID in the Microsoft Store. You can find this value by going to your URL in the Microsoft Web Store and grabbing the last part of the URL. For OneNote, for example, the web link is https://www.microsoft.com/en-us/p/onenote-for-windows-10/9wzdncrfhvjl, so OneNote's product ID is `9wzdncrfhvjl` |
| size | "large" or "small"  | "large" | small:<br>![image](https://user-images.githubusercontent.com/312936/135373704-9e786838-d75e-4962-bcf1-255b88de67b5.png)<br>large:<br> ![image](https://user-images.githubusercontent.com/312936/135373726-0eda0945-7d6d-413d-8af4-70e812509cf5.png)  |
| language | string | '' | The language to display the install button in. If left empty, the language will be detected from the user's browser `navigator.userAgent.language`. <br>Sample of specifying a different language:<br>![image](https://user-images.githubusercontent.com/312936/135659926-cafb666a-15ca-4129-a623-59e89a8ab7ea.png) |

Example using all the available options:

```html
<script type="module" src="https://getbadgecdn.azureedge.net/ms-store-badge.bundled.js"></script>
<ms-store-badge productid="9wzdncrfhvjl" size="small" language="he"></ms-store-badge>
```

## Why a web component?

Most app store badges are a simple image with a link to the web store. Why is this a web component?

In short, for better localization and better user experience.

- Localization: the web component supports automatic detection of the user's locale, showing a localized button to the user based on the user's browser locale.
- Better user experience: the web component detects if you're on Windows, and if so, allows the install to jump right into your app's product description page (PDP).
- Better user experience 2x: the web component works with Edge's whitelist to skip security prompts ("this site wants to launch Microsoft Store...") when the user is running on Edge.
- Better user experience 3x: Where supported, rather than launch the full store app, a user who clicks your app badge on Windows will get a mini PDP centered within the page, allowing for inline install. The user doesn't lose context.

## Running the code

To run code locally, `npm run dev`, then launch http://localhost:8000/create-your-own.html

To build for production, `npm run build`. This will create the production artifacts in `/dist`.

## Deploying

Github actions are set to deploy the changes to https://black-water-0eaf5100f.azurestaticapps.net

You will need to manually deploy `/ms-store-badge.bundled.js` to `https://getbadgecdn.azureedge.net/ms-store-badge.bundled.js`. (Future work: auto-deploy this to the CDN via Github Actions)
