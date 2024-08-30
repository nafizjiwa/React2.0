# React2.0

To write JavaScript within JSX surround code with curly braces { - javascript code - }
JSX must return a single element so a parent element should wrap all nested elements.
Rendering multiple elements wrap them in parentheses ( )
( <div> //Parent element
<p></p> //Child element
</div> );
To comments out in JSX {/**/}
Render JSX to the HTML DOM use React’s rendering API – ReactDOM
Render a React element to the DOM with 
ReactDOM.render( componentToRender, whereRenderAtTargetNode);
First select the DOM to whereRenderAtTargetNode with 
	document.getElementById(‘NodesIdValue’).
ComponentToRender – const JSX = ( <h1>Render Me at the Target Node</> );
JSX and JavaScript difference
Use className not class using camelCase eg. onClick
2 ways to create/define a React component 
1st JavaScript function
- They are stateless which receives and renders data
- It returns either JSX or null
- Functions begin with capital
const DemoComponent = function() {
return (
 <div>something her</div>
)};
2nd ES6 class syntax
	Class Demo extends React.Component {  //this class Demo extends React class
		constructor(props) { //Demo class has a constructor METHOD defined
super(props);	//Constructor uses super to call the Parents constructor 
}				//and also passes props to both
render() {		//render method returns h1 element
    return (
	<h1>Hi</h1>
   );
}
}

To compose multiple components create an App parent component to render each child

	const ChildComponent = ( ) => { return ( <div> Test </div> ); };
class ParentComponent extends React.Component {
   constructor(props) {
	super(props);
   }
render() {
 	    return (
		<App>
			<ChildComponent /> //here React encounter a reference to another component
		
		</App>
):
}
}

