# Defold flatpak
Flatpak configs for the Defold Engine

## What is Defold?
Defold is a free to use, source available, game engine with a developer-friendly license. Defold is owned and developed by the Defold Foundation.

## How to build and host the repo
Install `flatpak` and `flatpak-builder`

Generate a gpg key if you don't have one
```
gpg --full-generate-key
gpg --list-secret-keys --keyid-format LONG
```
Copy the id of the gpg key
```
sec   rsa4096/E7A009C635B360CC 2021-03-08 [SC] 
```
The id here is `E7A009C635B360CC`

Generate the repo
```
flatpak-builder --gpg-sign=E7A009C635B360CC --repo=repo build com.defold.Engine.yml --force-clean
```
Upload repo to the web or flathub

Create base64 version of the gpg key
```
gpg --export E7A009C635B360CC | base64 --wrap=0
```
Set `GPGKey` in .flatpakref and .flatpakrepo to the base64 string

In .flatpakrepo set Url to the repo folder (and set icon url)

In .flatpakref set Url to repo folder and RuntimeRepo to the location of .flatpakrepo

## Defold License
Defold is created and distributed under the developer-friendly Defold License. The Defold License is derived from the popular Apache 2.0 license.
https://defold.com/license/

## Sources
- https://github.com/defold/defold
- https://defold.com/
- https://flatpak.org/
