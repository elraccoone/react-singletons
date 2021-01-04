<div align="center">

# React Singletons

[![license](https://img.shields.io/badge/license-Apache_2.0-red.svg?style=for-the-badge)]()
[![npm](https://img.shields.io/npm/v/react-singletons.svg?style=for-the-badge)]()
[![npm](https://img.shields.io/badge/build-passing-brightgreen.svg?style=for-the-badge)]()

React Singletons brings the singleton pattern to React components. This module allows applications to create components that live outside of your application with shared states for popups and overlays.

**&Lt;**
[**Installation**](#installation) &middot;
[**Documentation**](#documentation) &middot;
[**License**](./LICENSE.md)
**&Gt;**

</br></br>

[![npm](https://img.shields.io/badge/sponsor_the_project-donate-E12C9A.svg?style=for-the-badge)](https://paypal.me/jeffreylanters)

Hi! My name is Jeffrey Lanters, thanks for checking out my modules! I've been a Game and Web developer for years when in 2020 I decided to start sharing my modules by open-sourcing them. So feel free to look around. If you're using this module for production, please consider donating to support the project. When using any of the packages, please make sure to **Star** this repository and give credit to **Jeffrey Lanters** somewhere in your app or game.

**&Lt;**
**Made with &hearts; by Jeffrey Lanters**
**&Gt;**

</br>

</div>

# Installation

Install React-Singletons using the Node Package Manager, the package is available natively or for both Babel and TypeScript compilers.

```sh
$ npm install react-singletons
```

# Documentation

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
Popup.mount({ title: "Hello!" }).update({ title: "Bye!" }, 1000).unmount(2000);
```
