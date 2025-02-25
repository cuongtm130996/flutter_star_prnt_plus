# flutter_star_prnt_plus

[![Pub Version](https://img.shields.io/pub/v/flutter_star_prnt_plus)](https://pub.dev/packages/flutter_star_prnt_plus)

This version is a fix and continuation for the original Flutter Star Prnt plugin that can be found [here](https://pub.dev/packages/flutter_star_prnt)
All credit goes to the original publisher of the package.

Flutter plugin for [Star micronics printers](https://www.starmicronics.com/pages/All-Products).

Native code based on React Native and Ionic/Cordova version  
React native Version ➜ [here](https://github.com/infoxicator/react-native-star-prnt)  
Ionic/Cordova Version ➜ [here](https://github.com/auctifera-josed/starprnt)

## Updating from 1.0.4 and lower

If you're having trouble please run these commands

```bash
rm -rf ios/Pods && rm ios/Podfile.lock && flutter clean
```

## Getting Started

```dart
import 'package:flutter_star_prnt/flutter_star_prnt.dart';

// Find printers
List<PortInfo> list = await StarPrnt.portDiscovery(StarPortType.All);

list.forEach((port) async {
/// Check status
await StarPrnt.checkStatus(portName: port.portName,emulation: 'StarGraphic',)
}

///send print commands to printer
PrintCommands commands = PrintCommands();
commands.push({
 'appendBitmapText': "Hello World"
});
commands.push({
 'appendCutPaper': "FullCutWithFeed"
});
await StarPrnt.print(portName: port.portName, emulation: 'StarGraphic',printCommands: commands)
```

## Android

Permissions required depending on your printer:

```xml
<uses-permission android:name="android.permission.INTERNET"></uses-permission>
<uses-permission android:name="android.permission.BLUETOOTH"></uses-permission>
```

## Ios

Need to add this into your info.plist for bluetooth printers

```xml
<key>UISupportedExternalAccessoryProtocols</key>
  <array>
    <string>jp.star-m.starpro</string>
  </array>
```

## Work in progress

- [ ] Added documentations in readme

## Documentation work in progress, please refer to react native or Ionic/Cordova's documentations for command format
