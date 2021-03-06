#BDToastAlert - Self-managed HUD-style alert text.

##Overview

BDToastAlert provides you an easy way to display non-obstructive messages to 
user without having to worry about its behavior and conflicts with other views.

##version 1.0.0

The first major version release. Version 1.0.0.

Since this is a major release, there is incompatibility with previous betas. :( Sorry, Early adopters. But this
version API is simpler, and more importantly, now it looks great! See below.


[![](https://github.com/norsez/BDToastAlert/raw/master/BDToastAlert/screencap.png)](https://github.com/norsez/BDToastAlert/raw/master/BDToastAlert/screencap.png)

##How to use
Out of the box, all you need to do is first get the singleton like this:

	BDToastAlert *toast = [BDToastAlert sharedInstance];

In order to display a message, call:

	UIViewController *ctrl  = <a view contorller…>
	[toast showToastWithText:@"Hello!" onViewController:ctrl];

That's it! You should see your text on the controller's view.

##Features

BDToastAlert works out of the box. However, you can customize it quite a bit if you like with these properties

- `verticalAlignment` defines where the toast should appear on the specified view.
- `customToastViewClassName` defines the class name of your own custom toast view. 

###Customizing Toast 

Two ways:

####Customize by Subclassing (Recommended)
Though you can start from scratch with a custom UIView for a custom toast view, I recommend subclassing the `BDDefaultToastView` class. This is the default view that `BDToastAlert` uses out of the box. 

An example for customizing toast view by subclassing `BDDefaultToastView`. 

To change the toast font, override the `-init` method, like this

	- (id)init
	{
	    self = [super init];
	    if (self) {
	        self.textLabel.font = <your font>;
	    }
	    return self;
	}

If you guess that the `textLabel` property is the `UILabel` on the `BDDefaultToastView` class, then you are correct. You can configure the label any way you like. For the background gradient, the following methods: configure how it looks

- `startGradientColor`
- `endGradientColor`
- `shadowColor`
- `backgroundRadius`

####Customize by Starting from Scratch
You can subclass a `UIView` for your custom toast with the following requirements:

1. The view must conform to the `BDToastViewProtocol`
2. The designated initializer (i.e. all your init code must be in) is the `-init` method. This is because
3. In order to use it with `BDToastAlert`, set the class name to its `customToastViewClassName` property. The `BDToastAlert` singleton creates an instance of your custom toast view using `-init` method only.

##Requirements
- Requires ARC
- `QuartzCore.framework`

##How to use
- With CocoaPods, add to your dependency list.

	dependency 'BDToastAlert'
	
- Without CocoaPods, just include h/.m files in BDToastAlert folder to your project source code 
- See the sample project. There's really not much to it.

##Apps using BDToastAlert

- [Photosophia iOS for Flickr Groups](http://www.google.com/url?sa=t&rct=j&q=photosophia%20app&source=web&cd=4&cad=rja&ved=0CDYQFjAD&url=http%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fphotosophia-for-flickr-groups%2Fid530161971%3Fmt%3D8&ei=2DA8UPDzEcLsrAed3YGwAQ&usg=AFQjCNEqFsfzipOIXDlFn1gzTmcioNsV2A&sig2=4J9p4wXIWYC-rGLzF5LXbg) (Shameless plug :)
- Please let me know of your apps so I can extend this list. Thanks!

##License
BDToastAlert is licensed under BSD. More info in LICENSE file.