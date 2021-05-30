JSX allows you to use JavaScript to control the logic flow in the templates. However, without a Virtual DOM naive use of things like `Array.prototype.map` would wastefully recreate all the DOM nodes on every update. Instead it is common for Reactive libraries to use template helpers. In Solid we wrap them in components.

The most basic control flow is the conditional. Solid's compiler is smart enough to optimally handle ternaries (`a ? b : c`) and boolean expressions (` a && b`). However, often it is more compact to use the `<Show>` component.

To only show the appropriate button to reflect the current state update the JSX to:
```jsx
<Show
  when={loggedIn()}
  fallback={<button onClick={toggle}>Log in</button>}
>
  <button onClick={toggle}>Log out</button>
</Show>
```
The `fallback` prop acts as the `else` and will show when the condition passed to `when` is not `true`.

Now clicking the button will change back and forth like you would expect.