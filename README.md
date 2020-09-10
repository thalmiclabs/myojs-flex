# myojs-flex

> North (formerly Thalmic Labs), the creator of the Myo armband, was acquired by Google in June 2020. Myo sales ended in October 2018 and Myo software, hardware and SDKs are no longer available or supported. [Learn more.](https://support.getmyo.com)

A plugin for [Myo.js](https://github.com/thalmiclabs/myo.js) that emits muscle flex strength and detects if the arm is flexed.

**[See it in action here](http://thalmiclabs.github.io/myojs-flex/demo/)** <small>(requires a myo!)</small>

Whenever the Myo sends EMG events `flex.myo.js` will emit a `flex_strength` event with a number between 0 and 1.

It will also emit a `arm_flex` or a `arm_unflex` emit if the flex strength passes a certain threshold. This will also set a boolean, `myo.isArmFlexed` which you can check.

We detect if the arm is flexed based on some parameters, you can control them like so

```
Myo.plugins.flex = {
	threshold     : 0.4, //What flex strength we considered to be 'flexed'
	timeout       : 150, //Milliseconds after flexing that we send the event
	emgResolution : 10   //How many EMG datasets we use to smooth the data
};
```

**Note:** The flex dectection is highly dependant on the threshold and resoltuion set. I picked numbers that worked for me, but feel free to experiment :)


#### applications

Flex detection is useful for reducing false positive on certain events. It's currently being used in [myo.snap.js](https://github.com/thalmiclabs/myojs-snap) to make sure the user was actually snapping and not just bumped their hand.

The flex strength is useful to detect how strong a gesture is. By picking thresholds, you could use this to differentiate between a 'light fist' and a 'hard fist'.


Check out the [demo](/demo/index.html) for an example of how to use it.
