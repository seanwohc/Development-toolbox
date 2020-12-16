# #if DEBUG in SWIFT

Created time: Jul 16, 2020 10:12 AM
Last edited time: Dec 16, 2020 9:41 AM
Tags: information

## Configuration for DEBUG

1. In Xcode, select Project > select target > select Build Settings > search for `Swift Compiler - Custom Flags`
2. Expand `Active Compilation Conditions` and make sure the value for key **Debug** is `DEBUG`
3. Expand the section below it (`Other Swift Flags`) and add `-D DEBUG` for the **Debug** key

## Using #if DEBUG in Swift

```swift
#if DEBUG
	//code for debugging
#else
	//code for release
#endif
```

## Create a public variable for easy access

```swift
public var IsDEBUG: Bool{
    #if DEBUG
        return true
    #else
        return false
    #endif
}

func testDebug(){
	if IsDEBUG{
		//Your function definition here
	}
}
```
