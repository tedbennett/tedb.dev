---
title: "Versa"
date: 2021-04-17T14:50:29+01:00
description: "iOS app to transfer music between services"
icon: "fas fa-arrows-alt-h"
github: "https://github.com/tedbennett/versa"
appStore: ""
techStack: 
    - "iOS"
    - "SwiftUI"
    - "Apple Music API"
    - "Spotify API"
---

Versa is an app to transfer music between Apple Music and Spotify

### Description

This app is designed for users who frequently share music with their friends across both Apple Music and Spotify. The user can log in to both services and easily transfer their playlists between them. The app can also open URLs from the clipboard, and search for the corresponding song, playlist, album or artist on the other service.

I've been through many iterations of building this app - in fact, this was the first idea for an app I had when I started exploring web and app development.

I created two packages for accessing the [Apple Music API](https://github.com/tedbennett/AppleMusicForSwift) and [Spotify API](https://github.com/tedbennett/SpotifyForSwift). Both of these do not yet cater to all endpoints, but they do provide a set of structs to easily handle the requested data, as well as handling response pagination and some common response errors.

To match songs between services, this app uses ISRC ids, which refer to a particular recording of a song. Matching artists and albums requires searching each service, which can fail for lesser known artists/albums.
