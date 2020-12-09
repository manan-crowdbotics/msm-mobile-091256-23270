# CB Basic Splash Screen

The CB Basic Splash Screen is a ReactNative based splash screen, by that means, it truly isn't executed until after the app 
is fully loaded. If it's desired to appear during load, you will need to build a native screen in both Android and iOS 
directories of the project.
  
## Installation

After you have added the screen module into your project, you will need to configure a few items by modifying the project 
files in the github repository. You will need to review/modify/add:

  **/src/config/installed_blueprints.js:**
    Make sure any screens that aren’t desired in the side menu are removed from the file. This list should only contain the screens desired to be linked on the side menu hamburger.

   In installed_blueprints.js you need to add objects for every screen that you want to show in the sidemenu/splash screen.
   They have a specific format:
    
   ``` { name: 'splash', human_name: 'Splash', access_route: 'splash'} ```
            
   name:  doesn't matter much, its used as a unique key for the side menu and splash screens array of 
   buttons, it must be unique, that's the only requirement
   
   human_name:  is what will be displayed in actual app
   
   access_route:  must be the name of the key in your mainNavigator setup  
  
  **/src/mainNavigator.js:**
   
   **ADD** comma in Line 44 (IMPORT_SCREEN_NAME must match the access_route in the installed_blueprints.js file above)
    
   ``` (contentComponent: SideMenu , ```

   **ADD** above top listed screen BlueprintImportInsertion:  
   
   ```import SplashScreen#######Navigator from '../features/SplashScreen#######/navigator';```
   
   **ADD** above top listed screen in BlueprintNavigationInsertion section:
   
   ```SplashScreen#######: { screen: SplashScreen#######Navigator },```
   
   **ADD** After Line 44 (this RouteName must match the name in the installed_blueprint.js file)
   
   ```initialRouteName: “IMPORT_SCREEN_NAME”, ```
  
  **/src/features/SplashScreen######/navigator.js** (where the "#####" is replaced by the generated numeric string specific to your 
  project)
  
  **ADD** after Line 10 (if it doesn't already exist -- consider removing this instruction --)
     
  ``` defaultNavigationOptions: ({ navigation }) => ({ header: null }), ```
  
 **MODIFY** Line 22 of generated screen /src/features/SplashScreen#####/screens/index.js file (replace BlankScreen1177768 with your desired destination screen):
    
  ``` this.props.navigation.navigate('BlankScreen1177768') ```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
