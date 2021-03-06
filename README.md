# XamariniOSBinding

Xamarin Binding integration guide For iOS AppsFlyer Xamarin Binding version 1.0.0

# Introduction
AppsFlyer’s Xamarin binding provides application installation and events tracking functionality


# Initial steps

To Embed SDK into your Application:

1. Copy AppsFlyerXamarinBinding.dll into your project.

2. On Xamarin Studio go to References and click on Edit References. 

3. Go to .Net Assembly tab and click on Browse… button.
 
4. Locate AppsFlyerXamarinBinding.dll and chose it.



# SDK Initialization
Go to your AppDelegate.cs and add:

using AppsFlyerXamarinBinding; at the top of the file.

Add the following code in the FinishedLaunching method:

	public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)

	AppsFlyerTracker.SharedTracker().AppleAppID = "YOUR_APP_ID_HERE";
	AppsFlyerTracker.SharedTracker().AppsFlyerDevKey = "APPSFLYER_DEV_KEY_HERE";
	AppsFlyerTracker.SharedTracker().IsDebug = true;
	AppsFlyerTracker.SharedTracker().TrackAppLaunch();


Set your appId & DevKey Replace appId & devKey with your values.

You can get your AppsFlyer DevKey on our dashboard. See “SDK integration” on your app screen. 

DevKey = your unique developer ID, which is accessible from your account, e.g. rbz2mfgZQY5mSEYNTyjwni // For example: 

#	Adding Custom Event 
Example: “Add-to-cart” Event 

	var addToCartEvent = new NSDictionary (AFEventParameter.AFEventParamContentId, "id 123",
	AFEventParameter.AFEventParamContentType, "type 1", AFEventParameter.AFEventParamCurrency,
	"USD", AFEventParameter.AFEventParamDescription, "add to cart Description");

	AppsFlyerTracker.SharedTracker().TrackEvent(AFEventName.AFEventAddToCart, addToCartEvent);


#	Conversion Data
For Conversion data your should call this method:

	AppsFlyerTracker.SharedTracker().LoadConversionDataWithDelegate (new AppsFlyerConversionDataDelegate());

AppsFlyerConversionDataDelegate.cs can be found in the sample app provided with this guide