Page Table of Contents
- [Introduction](#introduction)
- [Thinking Declaratively](#thinking-declaratively)
- [The Widget Tree](#the-widget-tree)
  - [Stateless Widgets](#stateless-widgets)
    - [Lifecycle](#lifecycle)
  - [Stateful Widgets](#stateful-widgets)
    - [Lifecycle](#lifecycle-1)
- [When to use Stateful/Stateful Widgets](#when-to-use-statefulstateful-widgets)
- [How to access State](#how-to-access-state)
- [References](#references)

## Introduction
This section will give you a better understanding of how programming in [Flutter (Flutter Dev Team 2018)](https://flutter.dev/) actually works. You will learn how a Declarative framework like Flutter differs form an Imperative Framework like Android or IOS. And lastly, you will be introduced to two of the most central topics of Flutter: The [_Widget Tree_ (Flutter Dev Team 2019)](https://flutter.dev/docs/development/ui/widgets-intro) and [_Sate_ (Flutter Dev Team 2019)](https://flutter.dev/docs/development/data-and-backend/state-mgmt).

## Thinking Declaratively
If you come from the native mobile world and frameworks like IOS and Android, developing with flutter can take while to get used to. Flutter, other then those frameworks mentioned above, is a _Declarative_ Framework. 

But what exactly is the difference between _Declarative_ and _Imperative_? An imperative approach is telling the framework **exactly** what you want to happen. "Imperium" (Latin) means "to command". A declarative approach is describing the to the framework what kind of result you want to get. "Declaro" (Latin) means "to explain". Let's look at an example:

```dart
List numbers = [1,2,3,4,5]
for(int i = 0; i < numbers.length; i++){
    if(numbers[i] > 3 ) print(numbers[i]);     
}
```
_Code Snippet 1: Number List (Imperative)_

Here we search for ever entry in the list that is bigger the 3. We explicitly tell the framework to go through the List and check each value.

```dart
List numbers = [1,2,3,4,5]
print(numbers.where((num) => num > 3));
```
_Code Snippet 2: Number List (Declarative)_

In the Declarative version, we simply state how our result should look like, but not how to achieve it.

Okay, that's all well but let's get back to Flutter:

> "Flutter is declarative. This means that Flutter builds its user interface to reflect the current state of your app" [(Flutter Dev Team 2019)](https://flutter.dev/docs/development/data-and-backend/state-mgmt/declarative)

![UI = f(State)](https://github.com/Fasust/flutter-guide/wiki//.images/ui-equals-function-of-state.png)

_Figure 1: [UI = f(State) (Flutter Dev Team 2019)](https://flutter.dev/docs/development/data-and-backend/state-mgmt/declarative)_

This means that you never _imperatively_ or explicitly call an UI element to change it. You rather change the state of you application and the UI change is implicit. For Example, let's say we want to build a button that changes it's color to red when it is pressed. In an imperative framework like Android, we have to call the UI element and tell it to change it's color:

```java
Button button = findViewById(R.id.button_id);
boolean pressed = false;

button.setOnClickListener(new View.OnClickListener() { 
    @Override
    public void onClick(View view) 
    { 
        button.setBackground(pressed ? red : blue);
    } 
}); 
```
_Code Snippet 3: Red button in Android (Imperative)_

In Flutter on the other hand, we never call the UI element directly, we instead change the App-Sate (here the bool "pressed") and trigger a rebuild of the button with the function setSate(). The Color of the Button is _declared_ to depend on the bool "pressed":

```dart
bool pressed = false;

@override
Widget build(BuildContext context) {
    return FlatButton(
        color: pressed ? Colors.red : Colors.blue,
        onPressed: () {
            setState(){ // trigger re-build of the button
                pressed = !pressed;
            } 
        }
    );
}
```
_Code Snippet 4: Red button in Flutter (Declarative)_

## The Widget Tree
- the tree
- Buildcontext
- Widgets in General
  - Imutable
  - Each widget does one specific thing

### Stateless Widgets
#### Lifecycle
### Stateful Widgets
- what is state 
  - mutable
  - "n properties that change over time"
  - long life span
  - sticks around
- why 2 party
#### Lifecycle

## When to use Stateful/Stateful Widgets

## How to access State
- Lifting up
- Inherited Widget
- 2 types of state
  - local and global
  - more in architecture

<p align="center"><a href="#">Back to Top</a></center></p>

---
## References 