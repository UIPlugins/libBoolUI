# libBoolUI
[![HitCount](http://hits.dwyl.io/UIPlugins/libBoolUI.svg)](http://hits.dwyl.io/UIPlugins/libBoolUI)
A simple API to create yes no forms
# Documentation
This library is to make easy things easier (and have less boilerplate), so here's some docs to help!
#### Creating a form

Simply create a ```YesNoForm``` object using the new keyword!

```
$form = new YesNoForm($closure, 'Are you sure?');
```

The first argument is the callable (we'll get to that later) and the second is the title of the form, they're both optional.
However, if you leave the callable out you'll have to set it later.

**Adding the buttons**

Add the buttons by calling the method ```registerButtons()``` in your object!

```
$form->registerButtons();
```

Optionally, you can change the text for the buttons by passing an argument to the method.

```
$form->registerButtons(['Custom Yes', 'Custom No']);
```

**Images**

After you register your buttons, you can call the function ```setImage()``` to give it an image!

The parameters for setImage are ```(int $yesOrNo, bool $isURL, string $imageURL)``` the first is yes or no, there are predefined constants for this that you can access like ```YesNoForm::YES``` and ```YesNoForm::NO```, then simply put true if your image is accessed via URL or false if it's a path to a texture.

I recommend using a texture because URL's load really slow to the client.

Code example

```
$form->setImage($form::YES, false, 'textures/ui/checkboxFilledYellow');
$form->setImage($form::NO, false, 'textures/ui/checkboxUnFilled');
```

**Randomization**

You can randomize the order of the options by calling the method ```randomize()``` in your object!

```
$form->randomize(); 
```

**Forcing user input**

You can force the user to press one of your options by calling the setter method ```setForced()``` in your object
```
$form->setForced();
```

#### Sending the form to a player

Sending a form is as simple as
```
$player->sendForm($form)
```
with ```$form``` being your YesNoForm object mentioned above!

#### Callables and return values

Your callable function should have the arguments ```(Player $player, $data)```
If the player hits yes, the ```$data``` variable will be true; pressing no makes it false.


#### That's it!

It's really that simple, if you need help with this refer to the [sample plugin](https://github.com/UIPlugins/PvPUI)