<div align="center">

[![Spotify](https://spotify-readme-maitre-oda.vercel.app/api/spotify)](https://open.spotify.com/user/maitre_oda)

</div>

![separator](https://user-images.githubusercontent.com/43296168/132062615-3b18c43a-fa5f-45f2-99c3-4b831cde910e.gif)

<div align="center">

# Set Up Guide

</div>

## Spotify

- Create a [Spotify Application](https://developer.spotify.com/dashboard/applications)
- Take note of:
  - `Client ID`
  - `Client Secret`
- Click on **Edit Settings**
- In **Redirect URIs**:
  - Add `https://localhost/callback/`

</div>

![separator](https://user-images.githubusercontent.com/43296168/132062615-3b18c43a-fa5f-45f2-99c3-4b831cde910e.gif)

## Refresh Token

- Navigate to the following URL:

```
https://accounts.spotify.com/authorize?client_id={SPOTIFY_CLIENT_ID}&response_type=code&scope=user-read-currently-playing,user-read-recently-played&redirect_uri=https://localhost/callback/
```

- After logging in, save the {CODE} portion of: `https://localhost/callback/?code={CODE}`

- Create a string combining `{SPOTIFY_CLIENT_ID}:{SPOTIFY_CLIENT_SECRET}` (e.g. `5n7o4v5a3t7o5r2e3m1:5a8n7d3r4e2w5n8o2v3a7c5`) and **encode** into [Base64](https://www.base64encode.org/).

- Then run a [curl command](https://httpie.org/run) in the form of:

```sh
curl -X POST -H "Content-Type: application/x-www-form-urlencoded" -H "Authorization: Basic {BASE64}" -d "grant_type=authorization_code&redirect_uri=https://localhost/callback/&code={CODE}" https://accounts.spotify.com/api/token
```

- Save the Refresh token

![separator](https://user-images.githubusercontent.com/43296168/132062615-3b18c43a-fa5f-45f2-99c3-4b831cde910e.gif)

## Vercel

- Register on [Vercel](https://vercel.com/)

- Fork this repo, then create a vercel project linked to it

- Add Environment Variables:

  - `https://vercel.com/<YourName>/<ProjectName>/settings/environment-variables`
    - `SPOTIFY_REFRESH_TOKEN`
    - `SPOTIFY_CLIENT_ID`
    - `SPOTIFY_SECRET_ID`

- Deploy !

![separator](https://user-images.githubusercontent.com/43296168/132062615-3b18c43a-fa5f-45f2-99c3-4b831cde910e.gif)

## ReadMe

You can now use the following in your readme :

`[![Spotify](https://USER_NAME.vercel.app/api/spotify)](https://open.spotify.com/user/USER_NAME)`

### Status String

Have a string saying either "Vibing to:" or "Last seen playing:".

- Change [`height` to `height + 40`](https://github.com/maitre_oda/maitre_oda/api/templates/spotify-light.html.j2#L1-L2) (or whatever `margin-top` is set to)
- Uncomment [**.main**'s `margin-top`](https://github.com/maitre_oda/maitre_oda/api/templates/spotify-light.html.j2#L10)
- Uncomment [currentStatus](https://github.com/maitre_oda/maitre_oda/api/templates/spotify-light.html.j2#L93)

### Theme Templates

If you want to change the widget theme, you can do so by the changing the `current-theme` property in the `templates.json` file.

Themes :

- `light`
- `dark`

If you wish to customize farther, you can add your own customized `spotify-light.html.j2` file to the templates folder, and add the theme and file name to the `templates` dictionary in the `templates.json` file.

![separator](https://user-images.githubusercontent.com/43296168/132062615-3b18c43a-fa5f-45f2-99c3-4b831cde910e.gif)
