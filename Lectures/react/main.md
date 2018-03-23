# ReactJS Frontend Applications Introduction

[ReactJS](https://reactjs.org/) is a Javascript framework written by Facebook to make it easy to build applications with a Graphical User Interface on the web. You can think of web applications just like any application that runs on your computer with a GUI -- except that it runs inside a browser (but still "on" your computer). When you visit a web URL of a react application, such as [http://adpl.suyash.io](http://adpl.suyash.io), your browser actually _downloads_ the code and assets needed to run the web application to your computer and then runs the web application (again, this is all running on _your_ computer). One of the biggest advantages of web applications is that they are cross platform, because browsers generally run the same across Windows/Mac/Linux and mobile devices like iPhone/Android. 

## Anatomy of a React Application
### Components
A component is a key unit of React--it is the most granular unit that has _both_ functionality and a view. Components are classes in Javascript that inherit from a base class `React.Component` that imbue your class with additional React-rendering powers. Every component has to do one thing -- define a `render()` method that returns a blob of `JSX` which is essentially `HTML` with some minor changes that we will see. 

```js
class Hello extends Component {

	render() {
		return (
			<div>
				Hello, Suyash
			</div>
		)
	}

}
```
