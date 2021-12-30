# kickstart your project!

I've noticed that as a software develoepr I tend to burn out on projects most often because of a few reasons:
- the uncertain nature of thier size
- the hassle of "context switching" between designing and actually coding 
- the annoyance of boilerplate code in any language, library or with any tool

This repo aims to solve these problems by creating tools focused solely on project design and ideation, but which output the basic boilerplate code, classes, types, etc. for a new project in whatever language you choose while also allowing graceful edits at the conceptual level which propogate through your source code.

Basically, it's a prototype creater and updater in one. Like Make, but for source code editing instead of compiling, linking, etc.

## Project creation

Write a function that creates the boilerplate code for each component, class, interface, abstract method etc. the way _you_ want it and then automate it yourself! This acts as the prototype for your project.

Run `kickstart`

...and your boilerplate generation will run on your prototype, creating your source code.

## Edit with confidence

You have a dozen or so classes in your java program which each independently import `com.uhpacke.stump4j;` and have a logging function and interface like:

```java
void log(message: String, errors: Iterable<Exception>) {
  String errorMsg =  "Oh no a bad thing happened in " + this.componentName "!!! - " + message;
  stumpLogWithError(errorMsg, errors);
}
```

and because of a very nasty vulnerability (oh no!) with said stump-related-logging software, you decide now is the perfect time to both ditch this library altogether and consolidate the logging into your own home-grown solution.

...but the thing that absolutely _sucks_ is that now when you make the switch you have to touch each component in a similar way, so it's quite error-prone and also time consuming. No one wants to author that commit and no one wants to review that commit. And aww, lonely commits just suck :(

But if you have a Prototype and a kickstart, solving this problem is easy and bug-free: just update the prototype and re-run the kickstart in edit mode:

`kickstart edit`

And see the immediate changes.

## Handle your own edge cases

With language-specific or library-specific scaffolding, templating or code generation tools there usually comes a point where you ditch the tool entirely as your project naturally outgrows its usefulness. Usually you can't easily re-run the tool without ditching something custom you've written, or some core components each have their own edge cases you need to tackle first. Writing your own generation function allows you to handle these without ever ditching the generation, allowing kickstart (in theory) to be useful much longer than scaffolding, templating or code generation tools by effectively acting as a "living prototype" of the project.

## Fly free, little software project!

At some point, it's time to ship. As fond as we've grown, it's not right to leave artifacts of the prototype in a build. Since the prototype should be versioned but not show up in a build artifact, there comes a point where it's time to cut a branch or even completely remove kickstart from the project. That's why `kickstart remove` will do exactly that for you.
