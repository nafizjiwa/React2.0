# React2.0

To write JavaScript within JSX surround code with curly braces { - javascript code - }
JSX must return a single element so a parent element should wrap all nested elements.
Rendering multiple elements wrap them in parentheses ( )
( <div> //Parent element
<p></p> //Child element
</div> );
To comments out in JSX {/**/}

`{/*The comment to comment out goes between these */}`
 
Render JSX to the HTML DOM use React’s rendering API – ReactDOM
Render a React element to the DOM with 
ReactDOM.render( componentToRender, whereRenderAtTargetNode);
First select the DOM to whereRenderAtTargetNode with 
	document.getElementById(‘NodesIdValue’).
ComponentToRender – const JSX = ( <h1>Render Me at the Target Node</> );
JSX and JavaScript difference
Use className not class using camelCase eg. onClick

|2 ways to create/define a React component||
|:---:|:--:|
|1st JavaScript function|
||- They are stateless which receives and renders data|
||- It returns either JSX or null|
||- Functions begin with capital|
<br />
		
  	const DemoComponent = function() {
		return (
		 <div>something her</div>
		)};
 
|2nd ES6 class syntax||
|:---:|:--:|

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

##### To compose multiple components create an App parent component to render each child

	const ChildComponent = ( ) => { 
 		return ( <div> Test </div> ); 
   	};
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


### Render a class Component or nested Components to the DOM
<hr/>

	<ComponentToRender /> = <App />
	
	const targetNode = document.getElementById('challenge-node');
	ReactDOM.render(<ComponentToRender />, targetNode or DomNode)
	React will display <App /> in the DomNode

##### Render returns HTML from JSX or null. if reactNode is a class component then it will return an instance of that component.

###### (React components are class or function components)


	class MyComponent extends React.Component{  //Create a class react component 
	  constructor(props){			//call constructor for this created class. How?
	    super(props);		//use super to pulls the constructor of the components parent class and pass props to both
	  }
	  render(){			//Defines what our component will render
	    return(						//return the JSX code
	          <div id="challenge-node">
	            <h1>My First React Component!</h1>
	          </div>
	    );
	  }
	};
	ReactDOM.render(<MyComponent/>, document.getElementById("challenge-node"));

##### To pass an array to a JSX element, wrap in curly braces as javascript.

	const Child = (props) => {
  		return <p>{props.tasks.join(', ')}</p>
	};

 	class extends React.Component {
 	  constructor(props){
    		super(props);
	   }
	  render() {
		return(
		 	<ParentComponent>
		   	   <ChildComponent tasks = {['walk dog', 'workout']}/>	//child component has access to array property
			</ParentComponent>
		);
	  }

##### To assign default props
   
 	ComponentName.defaultProps = { //The values to assign in curly braces// }
##### Override Default Props
How? SET the prop values for a component.
    
    TheComponentName.defaultProps = {	         //default value for property
    	quantity: 0
    }
    class MyComponent extend React.Component {
		constructor(props){
 	  	    super(props);
		}
		render() {					// set value in component to override default
    			return <ComponentWithProps quantity={10}/> //quantity is passed in prop with value of 10
    		}							//surrounded with curly braces

##### PropTypes help Define the Props(properties) You Expect

	TheComponentName.propTypes = { propertyName: PropTypes.thePropertyType.isRequired }
<br />
 	Items.propTypes = { quantity: PropTypes.number.isRequired }
