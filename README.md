# Basically Mobile Controls

---

a library for making easier to add VirtualPad/MobilePad into your game.

---

- [Setup](docs/SETUP.md)
- [Usage](#usage)

---

# USAGE

Creating a mobile controls should be fairly easy and very much self-explanatory

```haxe
// *
// * src/Main.hx
// *

import mobile.MobileInputHandler;

class Main {
	static function main():Void {
		MobileInputHandler.init('MobileControls', 'ArkoseLabs/HaxeTale', 'mobile/',
			[
				'MobilePad/DPadModes',
				'MobilePad/ActionModes',
				'Hitbox/HitboxModes',
			], [
				DPAD,
				ACTION,
				HITBOX
			]
		);
	}
}

// *
// * src/PlayState.hx
// *

import mobile.MobilePad;
import mobile.Hitbox;

class PlayState extends FlxState {
	public var mobilePad:MobilePad;
	public var hitbox:Hitbox;
	override function create() {
		// MobilePad
		mobilePad = new MobilePad('Test', 'Test');
		add(mobilePad);

		var mobilePadCam:FlxCamera = new FlxCamera();
		mobilePadCam.bgColor.alpha = 0;
		FlxG.cameras.add(mobilePadCam, false);
		mobilePad.buttonCameras = [mobilePadCam];

		// Hitbox
		hitbox = new Hitbox('Test');
		var hitboxCam = new FlxCamera();
		hitboxCam.bgColor.alpha = 0;
		FlxG.cameras.add(hitboxCam, false);
		hitbox.buttonCameras = [hitboxCam];
	}
	override function update(elapsed:Float) {
		if (mobilePad.getButtonByName.get('buttonA').justPressed) {
			trace('hello from buttonA');
		}

		if (hitbox.getButtonByName.get('buttonUp').justPressed) {
			trace('hello from buttonUp');
		}
	}
}

```