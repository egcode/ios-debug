# iOS Debugging Notes



### Symbolic breakpoint
`-[UIViewController dealloc]`
<br><br>
`po $arg1`
<br><br>

#### USAGE: 
<img src="images/1.Symbolic_ViewAllDeallocate.png" width="500">



<br><br>


### Symbolic fetch Objective C
po (BOOL)[$arg1 isKindOfClass:[UIViewController class]]. # Objective C

### Symbolic fetch Swift
po (BOOL)[$arg1 isKindOfClass:(id)NSClassFromString(@"ModuleOrAppName.SomeViewController")]

To symbolic breakpoint CONTITION: (BOOL)[$arg1 isKindOfClass:(id)NSClassFromString(@"ModuleOrAppName.SomeViewController")]


#### USAGE: 
<img src="images/0.Args.png" width="500">








## **Requirements for installation**
- Xcode
<br><br>
