# ContactTracer-iOS-SDK
The ContactTracer SDK gives you the power to detect nearby devices throught Bluetooh. If nearby devices also instal ContactTracer SDK enabled app, the conatc list can be tracked at https://contactracer.net pag

# Steps To Integrate

## Step 1: Download SDK
Download the latest release 
'''
git clone https://github.com/BCT-Mobile/ContactTracer-iOS-SDK
'''

## Step 2: Get the API key from ContactTracer team
Contact ContactTracer team to get your API key

## Step 3: Importing SDK to XCode project

1. In the project navigation sidebar, select "Add files to [ProjectName]".
2. Navigate to the ContactTracer-iOS-SDK directory and select the ContactTracerSDK.framework file.
Make sure that "Copy items if necessary" is checked and all targets that will use the SDK are selected
3. Go to Build Phase->Link Binary With Libraries->Press + icon and add the ContactTracer-iOS framework
4. Go to Build Phase->Embed Frameworks->Press + icon and add the ContactTracer-iOS framework

## Step 4: Integrate the Contact Tracer SDK with your app

### 1. Import the SDK

```swift
import ContactTracerSDK 
```

### 2. Init and start the ContactTracer SDK
In "func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {"

```swift
CTManager.shared.initWithApiKey(apiKey: "AUFUxY5yox2XSnPid2F2Q2FluHfEitGxay6W8YwX")
CTManager.shared.start()
```

### 3. Add device will go to background callback
When your app is going to background, please call this function
```swift
 CTManager.shared.willGotoBackground()
```

```swift
CTManager.shared.didGotoBackground()
```

**Sample code:**
```swift
func sceneWillResignActive(_ scene: UIScene) {
    CTManager.instance.willGotoBackground()
}

func sceneDidEnterBackground(_ scene: UIScene) {
    CTManager.instance.didGotoBackground()
}
```

### 4. Add device will go to foreground cabllcak
```swift
CTManager.instance.willGotoBackground()
```
**Sample code:**
```swift
    func sceneDidBecomeActive(_ scene: UIScene) {
        CTManager.instance.didGotoForeground()
```

### 5. Register User's phone number
You can call below message to register user's phone number with the ContactTracer system
```swift
public func registerPhoneNumber(_ countryCode: Int, _ phoneNumber: String, completionHandler: @escaping(_ success:Bool) -> Void)
```

**Sample code**
```swift
CTManager.instance.registerPhoneNumber("+886", "953999999") { (success) in
  if (success) {
    print("Register phone number successfully)")
    
    CTManager.instance.start()
    //Do your sucess tasks, like showing your UI
  } else {
    print("Fail to register user)")
  }
}
```

### 4. Upload collected data
You can call this function to upload the collected to the server
```swift
public func uploadData()
```

**Sample code**
You can have a button to allow user to manual upload data
```swift
@IBAction func uploadData(_ sender: Any) {
  CTManager.instance.uploadData()
}
```

### 5. Show debug view
You can call this function to show the debug view
```swift
public func presentDebugViewController(parentViewController: UIViewController)
```
The displayed debug view will list what device it detects in which time period.

**Sample code**
```swift
@IBAction func showDebug(_ sender: Any) {
  CTManager.instance.presentDebugViewController(parentViewController: self)
}
```

### OTP rleated function

If OTP is enabled for your region, you can call below functions to send and validate the OTP request
```swift
public func requestOtp(countryCode:String, phone: String, completion: @escaping(_ success:Bool) -> Void)
```

```swift
public func validateOtp(passcode:String) -> Bool
```


## How to Test
You can enable install your app on two iOS devices. You just need to put the device there and the device will start to detect nearby devices. By default, the data capture period is 5 mins. You can use the debug view to view the data capture status or you can use [ContactTracer web admin page][http://contactracer.net] to search the phone number and see data capture result







