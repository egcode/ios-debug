# iOS Debugging Notes



# Symbolic breakpoint
-[UIViewController dealloc]
<br><br>
po $arg1

<br><br>
<br><br>
### USAGE: 
<br><br>
<img src="images/0.Args.png" width="250">





## Symbolic fetch Objective C
po (BOOL)[$arg1 isKindOfClass:[UIViewController class]]. # Objective C

## Symbolic fetch Swift
po (BOOL)[$arg1 isKindOfClass:(id)NSClassFromString(@"ModuleOrAppName.SomeViewController")]

To symbolic breakpoint CONTITION: (BOOL)[$arg1 isKindOfClass:(id)NSClassFromString(@"ModuleOrAppName.SomeViewController")]










## **Requirements for installation**
- Xcode
<br><br>
