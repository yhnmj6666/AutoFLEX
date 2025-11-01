Hey, so I managed to figure it out. Actually quite useful information for converting jailbreak tweaks to (try) and work with LiveContainer’s injection.

If the tweak was built without theos-jailed it will point to CydiaSubstrate at;

> /Library/Frameworks/CydiaSubstrate.framework/CydiaSubstrat

LiveContainer’s TweakLoader injects substrate from its path in;

> LiveContainer.app/Frameworks

Changing the absolute dependency path with whatever tool you prefer (ESign, install name tool, etc) to the relative path allows the binary to load substrate from LC’s injector;

> @rpath/CydiaSubstrate.framework/CydiaSubstrate

Here’s a quickly patched version of the AutoFLEX dylib, compiled with the tweak source I replied with earlier. Link will be up for 3 days, after that you’ll have to compile and patch on your own (or just compile with theos-jailed): 

Credit: SpezIsaSpigger
Source: https://www.reddit.com/r/sideloaded/comments/1n93pxo/comment/ndo5u3q/
