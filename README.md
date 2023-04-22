# Steeleye Frontend Developer Assignment

Q.1: Explain what the simple List component does.

Ans:
List component is displaying a list of text as SingleListItem.
It takes an array of objects with each object mandatorily having text as its key.
SingleListItem is showing the text and upon clicking it that particular list item will
become green while the other options turns red. To determine which list item is selected;
WrappedListComponent state contains a state named selectedIndex, it contains the index
of item which is currently selected by the user.

Q.2: What problems / warnings are there with code?

Ans:

1. Uncaught TypeError: prop_types_WEBPACK_IMPORTED_MODULE_2\_\_default(...).shapeOf is not a function
2. factoryWithTypeCheckers.js:183 Uncaught Invariant Violation: Calling PropTypes validators directly is not supported by the prop-types package. Use PropTypes.checkPropTypes() to call them.
3. Uncaught TypeError: Cannot read properties of null (reading 'map')
4. The above error occurred in the component: at WrappedListComponent
5. Warning: Each child in a list should have a unique "key" prop.
6. react-dom.development.js:86 Warning: Failed prop type: Invalid prop isSelected of type function supplied to WrappedSingleListItem, expected `boolean
7. Uncaught TypeError: setSelectedIndex is not a function.

Q.3: Optimised code

Ans:
import React, { useState, useEffect, memo } from "react";
import PropTypes from "prop-types";

// Single List Item
const WrappedSingleListItem = ({ index, isSelected, onClickHandler, text }) => {
const handleClick = () => {
onClickHandler(index);
};

return (
<li
style={{ backgroundColor: isSelected ? "green" : "red" }}
onClick={handleClick} >
{text}
</li>
);
};

WrappedSingleListItem.propTypes = {
index: PropTypes.number,
isSelected: PropTypes.bool,
onClickHandler: PropTypes.func.isRequired,
text: PropTypes.string.isRequired
};

const SingleListItem = memo(WrappedSingleListItem);

// List Component
const WrappedListComponent = ({ items }) => {
const [selectedIndex, setSelectedIndex] = useState();

useEffect(() => {
setSelectedIndex(null);
}, [items]);

const handleClick = (index) => {
selectedIndex === index ? setSelectedIndex(null) : setSelectedIndex(index);
};
// console.log(selectedIndex);
return (
<ul style={{ textAlign: "left" }}>
{items.map((item, index) => (
<SingleListItem
key={index}
onClickHandler={() => handleClick(index)}
text={item.text}
index={index}
isSelected={selectedIndex === index}
/>
))}
</ul>
);
};

WrappedListComponent.propTypes = {
items: PropTypes.arrayOf(
PropTypes.shape({
text: PropTypes.string.isRequired
})
)
};

WrappedListComponent.defaultProps = {
items: [
{ text: "Token 1" },
{ text: "Token 2" },
{ text: "Token 3" },
{ text: "Token 4" }
]
};

const List = memo(WrappedListComponent);

export default List;

# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
