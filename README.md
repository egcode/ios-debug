# *iOS Debugging Notes*



## *1.LLDB*

## *LLDB Step commands* 
<img src="images/13.png" width="500">
<br><br>


## *LLDB evaluation commands* 
<img src="images/3.png" width="500">


### `po` - evaluate expressions
<br><br>
<img src="images/4.png" width="500">


### `p` - evaluate expressions and methods (`p` is the alias for expression, if you need to pass arguments `expr` command is used)
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


## *Changing UI with LLDB* 
- assign new text to label `p label.text = "changed label text"`
- and refresh UI `p CATransaction.flush()`
<img src="images/12.png" width="500">
<br><br>


## *Extract object from memory with type with LLDB* 
store object in global variable  `p let $image = unsafeBitCast(0x0000600001acf1e0, to: UIImage.self)`
<br><br>


## *LLDB View Return Values* 

When we have breakpoint in return value like this:
<br><br>
<img src="images/14.png" width="500">
<br><br>



- we can hit `finish` and it will step out of this method and execute return
- then we get memory address of returned value by `register read $rax` (swift)
- then we can extract what is stored in that location if we know the type by `po unsafeBitCast(0x0000600001acf1e0, to: UIImage.self)`
- and we can create expression and view the image extracted from memory

<img src="images/15.png" width="900">
<br><br>


## *Calling methods with breakpoints inside LLDB* 

If we run method with breakpoint from lldb, breakpoint will be ignored. 
To include breakpoints inside lldb we hit command:
`expr -i false -- someMethodWithBreakpoint()` 
or `expression -i false -- someMethodWithBreakpoint()`


<img src="images/17.png" width="900">
<br><br>


## *If we stuck in Objective-C context we can go to Swift context inside LLDB* 

<img src="images/18.png" width="600">
<br><br>



## *get swift singleton inside Objective-C*
`expr -l swift -O -- import XPMobileSDK; DataManager.shared.pendingAlarmEvent`



--------------

## *2.Symbolic breakpoints*


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
