# Lazy todo app - Vue

This is a copy of my lazy todo app made in Vue.js 3 using templates.

### Pros of using Vue in making this app:
- Project structure is simple, with a single file per component, containing the style, script, and template for that component.
- Emitters are really cool, but seem like a complicated layer of props. 
- Provide/Inject is awesome, like React's context but smoother and easier to implement.
- Vue CLI is significantly better than CRA, allowing me to customize my project setups.
- Being able to specify when a style is scoped or not is awesome.
- Atomic state manipulation is a *HUGE* plus.

### Cons of using Vue:
- I really don't know my way around Vue, and the wonky syntax makes it very difficult to get used to.
- Templates instead of JSX, just feels really abstract in what actually goes where, with weird syntax that confuses me.
- TypeScript might as well not be used here because when it comes to actually using the data, you don't get what the structure actually is. The decorators used feel pretty janky and the documentation for using TypeScript pretty much just doesn't exist. This might not be as big of a deal using JSX, but I did things the Vue way for this project.
- There isn't much support for deploying the app, with the gh-pages tutorial instructing you to copy a .sh script and run it. Using a third party tut actually made this much simpler.
- This is more of a framework, you sort of have to do things their way.
- Why do the dev tools go so wonky? It just says anonymous component for just about anything that actually uses state.
- If you wrote something incorrectly, it doesn't tell you. Instead, the component with the mistake just simply doesn't get rendered.
- Needing to specifically declare which components a component will use is absolute insanity.

My first impressions are that Vue is really weird. For one, I don't like using templates with custom syntax. It's like learning an entire new language, not to say that I'm not okay with learning a new language, but the fact that you have to write templates in that manner immediately makes me rather use React. I haven't tried using JSX for this yet, but I do intend to. I'll likely make another version of this app using JSX instead of the templates. There are a lot of weird things that are required to get a component to render that I feel just add to the workflow without improving functionality, like I should be able to use a component without telling the parent component that I'm using it. TypeScript support for this feels unfinished. The decorators feel janky, and the fact that I had to get another package for property decorators just seemed wrong. I get that they're probably trying to keep package bloat down, but it just feels like everything I need should be int the vue-class-components package. Also, a lack of autocomplete when using TypeScript makes TypeScript feel useless. It seemed like I should just write it all in JavaScript to save myself the time. There are definitely things that I wish React had. Provide/Inject is such a handy feature that requires very little setup, it makes context look terrible. Emitters are really awesome, but I feel are sort of limited. I think it would be better for you to be able to set up a listener on a parent, and any descendent should be able to emit to that listener without needing to set up a listener on every descendent that contains the component, though I understand that that would be technically very difficult. Thankfully Provide/Inject is there to pick up the slack, being able to pass down methods that can be used to handle the same sort of tasks. All in all, I like Vue, but not nearly as much as React, and probably not even as much as Angular.