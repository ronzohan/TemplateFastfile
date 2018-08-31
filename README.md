# TemplateFastfile

### Requirements
 * Apple Generic Versioning should be enabled in order to use this. <br/> (Link below shows how to enable Apple Generic Versioning) <br/>
 https://medium.com/xcblog/agvtool-automating-ios-build-and-version-numbers-454cab6f1bbe
 * Fastlane installed in the system (https://docs.fastlane.tools/getting-started/ios/setup/)
 *  Fastlane integrated in the project

#### This fastfile handles the following:
* Updates build version automatically if no version bump has been defined
* Updates app version automatically if version bump is defined and resets build version to 1
* Uploads app to **testflight** depending which lane has been used
* There are currently two lanes defined: **production** and **staging**

## Example usage
* Open up Terminal, cd into your top-level project directory, and run the following commands:
  
  * #### Build and upload production app  
    ```fastlane production```

    Fastlane will increment the build number only and build the current app based on the production scheme.
  
  
  * #### Build and bump version number on a patch level on a staging app
    ```fastlane staging bump_type:patch```
  
    Fastlane will bump version number of the app (e.g. in this case patch level bump from 1.0.0 to 1.0.1). This also 
    resets the build number to 
    
  * #### Build and bump version number on a minor level on a staging app
    ```fastlane staging bump_type:minor```
  
    Fastlane will bump version number of the app (e.g. in this case minor level bump from 1.0.0 to 1.1.0). This also 
    resets the build number to 1
    
  * #### Build and bump version number on a major level on a staging app
    ```fastlane staging bump_type:major```
  
    Fastlane will bump version number of the app (e.g. in this case major level bump from 1.0.0 to 2.0.0). This also 
    resets the build number to 1
