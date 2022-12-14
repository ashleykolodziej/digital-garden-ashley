---
aliases: [AMP, Facebook Instant Articles]
---

# Web Packaging
A controversial technology introduced by various companies such as Facebook (Instant Articles) and Google (AMP). The technology allows for bundling of web assets so they can be shared, cached, etc. easily, which in the examples above, allows for faster loading of assets by reducing the amount of unnecessary HTML, CSS, and JavaScript the browser needs to load. In theory, you could also use this to download and share an offline copy of a website, without having any real proof of where it came from. 

Like [[Packaging]] in Adobe InDesign, this process gathers up all the external assets - [[CSS]], [[JavaScript]], and images - which are connected to an [[HTML]] file. In both instances, if you were to try to view the file by itself, there would be many broken or missing assets in the file.

## Controversy
Several companies have come out with statements deeming web packaging to ultimately a harmful practice - at least the way it is implemented now - including [Mozilla](https://www.reddit.com/r/firefox/comments/bws1xq/mozillas_position_on_web_packaging/) and Apple.

Of greatest concern is how it allows content from one website to be served from a different URL while appearing legitimate, called Signed Exchanges. [Source](https://9to5google.com/2019/04/18/apple-mozilla-google-amp-signed-exchanges/) One of the most reliable ways a user can detect a malicious or fake website is to check its URL. Signed Exchanges mask that cue. Worse, if someone can obtain the private key used to make an exchange legitimate, they can make their malicious copy of a website look completely like the real thing, including serving it through Google. And because there is no connection to the original website, the original website owner would have a hard time telling something was wrong.

Reddit's AmputatorBot has an [excellent summary of why the technology is flawed](https://www.reddit.com/r/AmputatorBot/comments/ehrq3z/why_did_i_build_amputatorbot/).