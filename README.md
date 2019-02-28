# *iOS Debugging Notes*



## 1.Symbolic breakpoints


### Symbolic breakpoint - all dealloc methods

`-[UIViewController dealloc]`
<br><br>
`po $arg1`
#### EXAMPLE: 
<img src="images/1.Symbolic_ViewAllDeallocate.png" width="500">
<br><br>



When Symbolic breakpoint hits, we can use example arguments:
- Symbolic fetch Objective C
`po (BOOL)[$arg1 isKindOfClass:[UIViewController class]].` 
- Symbolic fetch Swift
`po (BOOL)[$arg1 isKindOfClass:(id)NSClassFromString(@"ModuleOrAppName.SomeViewController")]`

To symbolic breakpoint CONTITION: (BOOL)[$arg1 isKindOfClass:(id)NSClassFromString(@"ModuleOrAppName.SomeViewController")]
#### EXAMPLE: 
<img src="images/0.Args.png" width="500">






## **Requirements for installation**
- Xcode
<br><br>
