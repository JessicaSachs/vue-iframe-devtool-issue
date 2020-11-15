# Reproduction of Vue devtools bug w/ lack of iframe support

## Synopsis

Vue Devtools doesn't support iframes (even on same-domain). In theory, there exists support for external devtools (for Electron apps, etc), but these also do not work. See the `external` branch for a reproduction of this.

External devtools isn't a great solution for web-based application that use iframes (mainly microfrontends) or for tools like Storybook or Cypress (component workbenches).

## Symptoms

Vue devtools doesn't detect Vue on the page.

## Attempted fixes

Telling the child iframe to reach up into the parent window and bind certain globals like the root Vue node or Vue module (perhaps I'm not binding the right stuff? Maybe there's a Devtools.refresh() kinda function I need to call?)

## Steps to reproduce

1. Install latest devtools for 2.x and 3.x (depending on what branch you're on)

1. Install deps

```bash
yarn install
```

1. Start static server

```bash
yarn serve
```

1. Open index.html in server
1. See that devtools doesn't light up
1. Navigate to iframe.html directly, see that devtools lights

## Branches

* 2.x - Latest Vue 2 script

* 3.x - Latest Vue 3 script

* external - Demo of external devtools failing with Vue 2
