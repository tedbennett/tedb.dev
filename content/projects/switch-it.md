---
title: "Switch It"
date: 2020-11-11T08:45:58Z
description: "iOS app to transfer music between services"
icon: "fas fa-arrows-alt-h"
github: "https://github.com/tedbennett/Spotify-Apple-Music-Transfer"
appStore: ""
techStack: 
    - "iOS"
    - "SwiftUI"
    - "Apple Music API"
    - "Spotify API"
---

Switch It is an app to transfer music between Apple Music and Spotify

### Description

This app is designed for users who frequently share music with their friends across both Apple Music and Spotify. The user can log in to both services and easily transfer their playlists between them. The app can also open URLs from the clipboard, and search for the corresponding song, playlist, album or artist on the other service.

I attempted to build this app a while ago ([here](https://github.com/tedbennett/music-manager)), but became frustrated with the structure of the app, and with inconsistencies in both service APIs. From this I spun off the first iteration of [Switch It](https://github.com/tedbennett/switch-it), which only opened song and album urls from the user's clipboard. I tried to submit this to the App Store, however it was denied due to it's functionality being too simplistic.

I created two packages for accessing the [Apple Music API](https://github.com/tedbennett/AppleMusicForSwift) and [Spotify API](https://github.com/tedbennett/SpotifyForSwift). Both of these do not yet cater to all endpoints, but they do provide a set of structs to easily handle the requested data, as well as handling response pagination and some common response errors.

To match songs between services, this app uses ISRC ids, which refer to a particular recording of a song. Matching artists and albums requires searching each service, which can fail for lesser known artists/albums.

### Future Work

I'm currently working on getting this app submitted to the App Store.

In the future I'd love to be able to add more music streaming services, as well as finding a more robust way of searching for artists and albums, as well as ensuring that the transferred songs are the correct song.