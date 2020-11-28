# MVC, MVP, MVVM
![](https://i.stack.imgur.com/CFbNC.png)


![](https://i.stack.imgur.com/ENBf1.png)

## Why MVC needs alternatives?
In MVC, Model represents the Data Model specified to that application. View is part of an application that users sees. Controller acts as an intermediary between view objects and its model objects. It is responsible for keeping the Model updated relative to user’s interactions with View and also updating the View with changes from the Model. View notifies the controller of any user interaction. The view controller then updates the model to reflect the change of state.
By definition they sound to be separated but in reality View and controller are tightly coupled, and also each one knows about the other two. And this is where all problems starts:
* This is violation of the Single Responsibility Principle
* This leads to a common problem so-called Massive View Controller
* This reduces reusability of each of entity
* Testability of the code is almost impossible
In real life the View and the Model are separated, but the View and the Controller are tightly coupled. All the code for both the controller and the view is written in ViewController. View Controllers get packed with the code quickly for various purposes. This problem is called Massive View Controller.

Massive View Controller is the state that a lot of logics and responsibilities such as network connection, converting Date to String, and image manipulation code has been moved into View Controllers. This practice makes your code bulky and hard to change. They clearly are not not belong here, but should we consider them as part of our model? No! They’re certainly not a view. Where else can they be?

## MVVM
Model View ViewModel introduces another component between View and Model called ViewModel. The main purpose of this special layer is to move the data state from the view controller to the ViewModel (MVVM considers both view and controller the View and treats the view controller as the View).
MVVM became a trending iOS architecture for couple reasons. It focuses on the separation of user interface from other layers. MVVM is compatible with your existing MVC architecture. This separation makes the apps more testable since the ViewModel knows nothing about the View.

**By using MVVM you will separate the whole business logic from UIKit which used to be coupled in MVC.**

## ViewModel

ViewModel is UIKit independent representation of the View and its state. It receives the user interaction from the View, fetches data from the Model, then process the data to a set of ready-to-display properties. Each of these properties represents a UI component in the View.
All the logic about preparing data for UI (e.g. converting date to string) happens in the ViewModel instead of the View. Therefore, it becomes possible to write a simpler tests for these logics without knowing the implementation of the View.
In MVVM, nothing is changed directly in the View, we deal with business logic in the ViewModel and thus the View changes itself accordingly. The View updates itself after observing the change of the ViewModel. Connecting UI components to ViewModel properties is called “Binding”.

## Binding
Binding refers to the data flow between the view and the viewModel. For each property in the view, there is a corresponding property exists in viewModel which will be updated regarding to that UI element. Suppose our view has a UITextField, for every new key press in a text field, the corresponding object in viewModel will be updated instantly. This should be two-way binding which means also the changes in viewModel properties will be reflected on the view.
The important part of the understanding of the MVVM is that View updates it’s state from the ViewModel through some sort of observer. Basically the whole idea is to notify the View of any state change in the ViewModel.
There are a few options to implement this (in Swift):
* Functional Reactive Programming, like RxSwift or ReactiveCocoa
* Swift KVO library like Bond
* Use home made solutions

There’s nothing about MVVM that forces you to use specific mechanisms to update the viewModel, or the view but usually if you are talking about MVVM the first solution comes to the mind is Functional Reactive Programming.

If you have experience working with functional reactive programming or you are familiar with frameworks like ReactiveCocoa, this will be the exact same as binding a property to a signal. In the case of the MVVM, view will bond the viewModel’s property to a UI element.

## TL;DR
In MVVM, ViewModel encapsulates properties that the view can bind to. MVVM let us bind our controls state to the view model. For example if we have a button that needs to change its title text, the button should bind its title to the corresponding property in the viewModel.

Using MVVM can be a solution to the Massive view controller problem (not always! because viewModel itself can become bulky), separates the business logic from UIKit, and makes the code more maintainable, and testable.

## MVP
 https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter

**references:** 
* https://stackoverflow.com/questions/141912/alternatives-to-the-mvc 
* https://medium.com/@m.tabrizi/mvc-alternatives-part-1-9fa72f859bd7
