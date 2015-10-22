# NWSTokenView

[![CI Status](http://img.shields.io/travis/James Hickman/NWSTokenView.svg?style=flat)](https://travis-ci.org/James Hickman/NWSTokenView)
[![Version](https://img.shields.io/cocoapods/v/NWSTokenView.svg?style=flat)](http://cocoapods.org/pods/NWSTokenView)
[![License](https://img.shields.io/cocoapods/l/NWSTokenView.svg?style=flat)](http://cocoapods.org/pods/NWSTokenView)
[![Platform](https://img.shields.io/cocoapods/p/NWSTokenView.svg?style=flat)](http://cocoapods.org/pods/NWSTokenView)

![NWSTokenView Demo](/Screenshots/NWSTokenViewExample.gif)

# Introduction
NWSTokenView is a flexible UIView subclass that shows a collection of objects in a similar manner to the Messages app. 

## Why is it different from others?
NWSTokenView’s main difference when compared to other similar libraries is the fact that it allows you to easily create your own style tokens via XIB files or programmatically without all the headaches. NWSTokenView does come with a default token style you can use.

## Installation

NWSTokenView is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "NWSTokenView"
```

## Usage

To run the example project, clone the repo, and run `pod install` from the Example directory first.

# How to use

## Import

    //Swift
    import NWSTokenView


## Protocol Conformance

    class ViewController: UIViewController, NWSTokenViewDataSource, NWSTokenViewDelegate
    {
         override func viewDidLoad()
         {
              super.viewDidLoad()
              tokenView.dataSource = self
              tokenView.delegate = self
         }
    }

## Data Source Implementation

Return the token data to display in the tokenView.

The number of tokens to display:

    func numberOfTokensForTokenView(tokenView: NWSTokenView) -> Int
    {
        return tokens.count
    }
    
The insets for the tokenView:

    func insetsForTokenView(tokenView: NWSTokenView) -> UIEdgeInsets?
    {
        return UIEdgeInsetsMake(5, 5, 5, 5)
    }
    
The title for the tokenView:

    func titleForTokenViewLabel(tokenView: NWSTokenView) -> String?
    {
        return "To:"
    }
    
The placeholder text for the tokenView when there are no tokens:

    func titleForTokenViewPlaceholder(tokenView: NWSTokenView) -> String?
    {
        return "Search contacts..."
    }
    
The custom view for the tokens:

    func tokenView(tokenView: NWSTokenView, viewForTokenAtIndex index: Int) -> UIView?
    {
        let contact = contacts[Int(index)]
        if let token = NWSToken.initWithTitle(contact.name, image: contact.image)
        {
            return token
        }
        return nil
    }

## Delegate Implementation

Return the behaviors for the token view.

Notifies you when a token was selected:

    func tokenView(tokenView: NWSTokenView, didSelectTokenAtIndex index: Int)
    {
        // Do something
    }
   
Notifies you when a token was deselected: 

    func tokenView(tokenView: NWSTokenView, didDeselectTokenAtIndex index: Int)
    {
        // Do something
    }
    
Notifies you when a token was deleted (i.e. selected then backspaced/overwritten/etc.):

    func tokenView(tokenView: NWSTokenView, didDeleteTokenAtIndex index: Int)
    {
        // Do something
    }
    
Notifies you when the token view’s textField becomes the first responder:

    func tokenView(tokenViewDidBeginEditing: NWSTokenView)
    {
        // Do something
    }
   
Notifies you when the token view’s textField resigns the first responder: 

    func tokenViewDidEndEditing(tokenView: NWSTokenView)
    {
        // Do something
    }
 
Notifies you when the token view’s textField’s text is changed:  
  
    func tokenView(tokenView: NWSTokenView, didChangeText text: String)
    {
        // Do something
    }
  
Notifies you when the token view’s textField’s text is returned:  
    
    func tokenView(tokenView: NWSTokenView, didEnterText text: String)
    {
        // Do something    
    }
    
Notifies you when the token view’s content size has changed (i.e. new line added): 
     
    func tokenView(tokenView: NWSTokenView, contentSizeChanged size: CGSize)
    {
        // Do something
    }

Notifies you when the token view finished loading all tokens:  
        
    func tokenView(tokenView: NWSTokenView, didFinishLoadingTokens tokenCount: Int)
    {
	// Do something
    }


## Author

James Hickman, james.hickman@nitwitstudios.com

## License

The MIT License (MIT)

Copyright (c) 2015 NitWit Studios, LLC

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.