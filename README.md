<div align="center">

[![license](https://img.shields.io/badge/license-Apache_2.0-red.svg)]()
[![npm](https://img.shields.io/npm/v/react-singletons.svg)]()
[![npm](https://img.shields.io/badge/build-passing-brightgreen.svg)]()
[![npm](https://img.shields.io/npm/dt/react-singletons.svg)]()
[![npm](https://img.shields.io/badge/supported-typescript-2a507e.svg)]()
[![npm](https://img.shields.io/badge/supported-babel-yellow.svg)]()

React Singletons brings the singleton pattern to React components. This module allows applications to create components that live outside of your application with shared states for popups and overlays.

**&Lt;**
[**My other Modules**](https://github.com/elraccoone) &middot;
[**Buy me a Coffee**](https://paypal.me/jeffreylanters)
**&Gt;**

Made with &hearts; by Jeffrey Lanters

</div></br></br>

# Installation

Install using npm.

```sh
$ npm install react-singletons
```

# Usage

To get started import the Singleton component from `react-singletons`. Then instead of exporting your component. Wrap and export it into a Singleton as shown below.

## Example usage

The example usign is using props and TypeScript, but both are not required.

```tsx
import * as React from "react";
import { Component, ReactNode } from "react";
import { Singleton } from "react-singletons";

interface IProps {
  title: string;
}

export const Popup = new Singleton<IProps>(
  class extends Component<IProps, {}> {
    public render(): ReactNode {
      return <div>Popup {this.props.title}!</div>;
    }
  }
);
```

```ts
import { Popup } from "./Popup";

Popup.mount({ title: "Hello!" });
Popup.mount({ title: "Hello!" });

Popup.update({ title: "Bye!" });
Popup.update({ title: "Bye!" }, 1000); // delay(ms)

Popup.unmount();
Popup.unmount(1000); // delay(ms)
```

```ts
// All events are chainable
Popup.mount({ title: "Hello!" })
  .update({ title: "Bye!" }, 1000)
  .unmount(2000);
```
