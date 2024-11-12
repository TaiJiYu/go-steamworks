# go-steamworks

** This project is still work in progress! **

A Steamworks SDK binding for Go

## Steamworks SDK version

161

## How to use

On Windows, copy one of these files on the working directory:

 * `steam_api.dll` (For 32bit. Copy `redistribution_bin\steam_api.dll` in the SDK)
 * `steam_api64.dll` (For 64bit. Copy `redistribution_bin\win64\steam_api64.dll` in the SDK)

```go
package steamapi

import (
	"os"

	"github.com/hajimehoshi/go-steamworks"
	"golang.org/x/text/language"
)

const appID = 480 // Rewrite this

func init() {
	if steamworks.RestartAppIfNecessary(appID) {
		os.Exit(1)
	}
	if !steamworks.Init() {
		panic("steamworks.Init failed")
	}
}

func SystemLang() language.Tag {
	switch steamworks.SteamApps().GetCurrentGameLanguage() {
	case "english":
		return language.English
	case "japanese":
		return language.Japanese
	}
	return language.Und
}
```

## License

All the source code files are licensed under Apache License 2.0.

These binary files are copied from Steamworks SDK's `redistribution_bin` directory. You must follow [Valve Corporation Steamworks SDK Access Agreement](https://partner.steamgames.com/documentation/sdk_access_agreement) for these files:

 * `libsteam_api.dylib` (copied from `redistribution_bin/osx/libsteam_api.dylib`)
 * `libsteam_api.so` (copied from `redistribution_bin/linux32/libsteam_api.so`)
 * `libsteam_api64.so` (copied from `redistribution_bin/linux64/libsteam_api.so`)

## Resources

 * [Steamworks SDK](https://partner.steamgames.com/doc/sdk)
 * 