# Kenan Player — Static Wrapper Pages (GitHub Pages)

Diese Seiten werden via **GitHub Pages** unter `https://kenan1206.github.io/webosend/` gehostet
und dienen als **HTTPS-Origin-Wrapper** fuer YouTube-Trailer-Embeds.

## Warum?

Die webOS-App laeuft aus `file:///media/apps/usr/palm/applications/com.kenanplayer.webos/`.
YouTube akzeptiert NIEMALS einen `file://` Referer-Header → Error 153 ("Video player
configuration error"). 

IPTV-Smarters-Pro und andere Premium-Apps loesen das ueber einen HTTPS-Wrapper auf
ihrem eigenen Server. Wir machen es genauso ueber GitHub Pages (kostenlos):

```
App (file://)  →  iframe src="https://kenan1206.github.io/webosend/yt.html?v=ID"
                   ↓
               yt.html (HTTPS-Origin)  →  iframe src="https://youtube.com/embed/ID"
                                          (Referer: https://kenan1206.github.io ✓)
                                          → YouTube spielt den Trailer
```

## Files

- `yt.html` — YouTube-Trailer-Wrapper. Akzeptiert `?v=VIDEO_ID&lang=de` als Query-Params.

## Setup

GitHub Pages muss einmalig fuer das Repo aktiviert sein:

```
Settings → Pages → Source: "Deploy from a branch"
Branch: e1/movies-1to1 → /docs
```

Nach dem ersten Build (1-2 Min) ist die Seite erreichbar unter:
https://kenan1206.github.io/webosend/yt.html?v=dQw4w9WgXcQ&lang=de
