# ContactTracer-iOS-SDK
ContactTracer iOS SDK

# Steps To Integrate

## Step 1: Download SDK
Download the latest release 


## Step 2: Get the API key from ContactTracer tem

## Step 3: Importing SDK to XCode project

1. Open project navigation and drag the ContactTracer framework to project folder structure. Remeber to choose "Copy items if needed"
2. Go to Build Phase->Link Binary With Libraries->Press + icon and add the ContactTracer-iOS framework
3. Go to Build Phase->Embed Frameworks->Press + icon and add the ContactTracer-iOS framework

## Step 4: Integrate the Contact Tracer SDK with your app

### 1. Import the SDK

'''swift
import ContactTracerSDK 
'''

### 2. Init and start the ContactTracer SDK
In "func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {"

CTManager.shared.initWithApiKey(apiKey: "AUFUxY5yox2XSnPid2F2Q2FluHfEitGxay6W8YwX")
CTManager.shared.start()

### 3. Register User's phone number
You can call below message to register user's phone number with the ContactTracer system
'''swift
public func registerPhoneNumber(_ countryCode: Int, _ phoneNumber: String, completionHandler: @escaping(_ success:Bool) -> Void)
'''

### 4. Upload collected data
You can call this function to upload the collected to the server
'''swift
public func uploadData()
'''

### 5. Show debug view
You can call this function to show the debug view
'''swift
public func presentDebugViewController(parentViewController: UIViewController)
'''
The displayed debug view will list what device it detects in which time period.


### OTP rleated function

If OTP is enabled for your region, you can call below functions to send and validate the OTP request
'''swift
public func requestOtp(countryCode:String, phone: String, completion: @escaping(_ success:Bool) -> Void)
'''

'''swift
public func validateOtp(passcode:String) -> Bool
'''









