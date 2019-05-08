# Parent & Child Components

## Learning Objectives

- SWBAT articulate the difference between parent and child components
- SWBAT break down a page into parent and child components
- SWBAT rearrange existing code into parent and child components

## Sequence

1. [Launch](#launch)
2. [Parents & Children](#parents--children)
3. [Rearranging Components](#rearranging-components)
4. [Close](#close)

## Launch

Let's all clone this React app [insert a link to a repository] and take a look at the code. [The code is all one long not-at-all-nested series of nested JSX with no props]

Based on what you know so far, how would you accomplish the following modifications to this code:

- Make all `<h2>`'s (in certain conditions) `<h3>`'s (so you can't just do a find/replace).
- Reorder the elements so the `<p>` is the last element in each container.
- Change the class of the second `<li>` in each list to be `completed`.

#### Questions for students

- How tedious did you think it was to make those changes?
- Can you think of a more efficient way to arrange the code so that changes like those are not so laborious?

## Parents & Children

As you've seen, it's possible to break code up into functional components to make it easier for a developer to manage the code in different parts of a React app. It's worth recognizing, however, that components can use (or be used by) other components. This makes code a bit more structurally semantic (it gives it more meaning), instead of just duplicating the way you might build an app in HTML.

When component A uses component B as part of its `return` statement, component A is referred to as the "parent" of component B, and component B is referred to as the "child" of parent A. Component B could, in turn, be built from other components - say components C and D. In this case, component B is the "parent" of components C and D, and components C and D are the "children" of component B. Component B is the "child" of component A and the "parent" of components B and C; it's all about the relationship between component B and one of the other elements.

The parent-child relationship is all about nesting. 

#### Mini-Challenges

- Revisit the app we started with, and think about how it could be rearranged into nested components.
- Map out (on paper) the nested structure of the app into granular sub-components. What is/are the most granular functional components you would make?

## Rearranging Components

Now that you've had a chance to think about how to restructure the app above, try to implement that restructuring:

1. Break apart the code into functional components
	1. Tip: start by breaking the code into large components, then try to break those components into smaller components.
2. Keep breaking the code into separate functional components until you are satisfied that the functional components are as granular as they should be.
	1. Remember to include the necessary `import` and `export` statements when you create new functional components:
	```
	import React from 'react'
	import Component from './Component'
	...
	```
	and
	```
	export default ComponentName
	```
	2. Remember to include a new `import` statement wherever you use a new functional component.
	3. Remember to replace the code you abstract into the functional component with the component name: e.g. `<Component />`.

## Close

Think back to the three changes that you were asked to make at the beginning of this lesson. Take a moment to make those changes to your app now that you've broken it apart into parent and child functional components:

- Make all `<h2>`'s (in certain conditions) `<h3>`'s (so you can't just do a find/replace).
- Reorder the elements so the `<p>` is the last element in each container.
- Change the class of the second `<li>` in each list to be `completed`.

#### Questions for students

- Was it easier/harder to make the changes now that you've restructured the app?
- What are the challenges to working with an app that has a lot of child components, many of which might have child components, some of which might have child components?