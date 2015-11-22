---
layout: post
title: Week 3

---

Creating a Popover in XCode

As seen in class, creating a popover view can seem daunting at first, but when broken down into small parts its a relatively simple task to implement. Storyboard makes this particularly easy to accomplish.

First, what is a popover?  A popover is a type of view which can be initiated in iOS where, rather than replacing a view-controller, a second view-controller appears on screen in the form of something like a speech bubble (this is as opposed to a full modal view that replaces the initial view controller).  

To create a popover, we will first require two view controllers.

So:  Open up xcode with a single view application and create a second view controller.

Then, add a button of some form in the first view controller to initiate the segue (optionally you can embedin a navigation controller and create an "add" button which is what we've done in class so far).

Next, control drag from your button to the second view, release, and select "present as popover"

Then, name your segue identifier as you will in its attributes inspector.  For the code below and this example, I used the indentifier: "showExamplePopover"

Now we will go into the code for ViewController.Swift (our initial view controller) and add "UIPopoverPresentationControllerDelegate" to our super class after UIViewController (be sure to separate these two by a comma)

We implement the viewcontroller as delegate relationship in the prepareForSegue method with the code that follows:

 override func prepareForSegue(segue: UIStoryboardSegue, sender: AnyObject?)
    {
        if segue.identifier == "showExamplePopover"
        {
            let vc = segue.destinationViewController

            let controller = vc.popoverPresentationController

            if controller != nil
            {
                controller?.delegate = self
            }
        }
    }

In this code, the identifier will be the name of the identifier you chose for the second vc (the one to be the popover)

The popover is then formatted with the following function:


    func adaptivePresentationStyleForPresentationController(controller: UIPresentationController) -> UIModalPresentationStyle
    {
        return .None
    }


Press run, click your button, and there you have it!
