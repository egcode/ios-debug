# *iOS Debugging Notes*



## *1.Symbolic breakpoints*


### Symbolic breakpoint - Hit breakpoint on any UIViewController deallocation

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

- Symbolic breakpoint CONTITION for Swift: `(BOOL)[$arg1 isKindOfClass:(id)NSClassFromString(@"ModuleOrAppName.SomeViewController")]`
#### EXAMPLE: 
<img src="images/0.Args.png" width="500">
<img src="images/2.png" width="500">




## *2.LLDB*

<img src="images/3.png" width="500">


### `po` - evaluate expressions
<br><br>
<img src="images/4.png" width="500">


### `p` - evaluate expressions and methods
<br><br>
<img src="images/5.png" width="500">
<img src="images/6.png" width="500">

### `fr v` - don't do expressions, only inspecting data, and it's safe but more limited
<br><br>
<img src="images/7.png" width="300">



## *Creating Global Session Variables:* 

<img src="images/8.png" width="500">
<br><br>

### We even can create global variables with breakpoints: 
in example:
- we create `p var $row = 0` in viewDidLoad 
- change this var in tableViewDidSelect `p $row == indexPath.row` 
- and stop when `$row == 2`

<img src="images/9.png" width="500">
<img src="images/10.png" width="900">
<img src="images/11.png" width="500">



