# React2.0

To write JavaScript within JSX surround code with curly braces { - javascript code - }
JSX must return a single element so a parent element should wrap all nested elements.
Rendering multiple elements wrap them in parentheses ( )

	( <div> //Parent element
	<p></p> //Child element
	</div> );

##### To comments out in JSX {/**/} --> 
					`{/*The comment to comment out goes between these */}`

##### Render JSX to the HTML DOM by using React’s rendering API -->
									`ReactDOM`
##### Render a React element to the DOM with --> 
						`ReactDOM.render( componentToRender, whereRenderAtTargetNode);`

1st select the DOM target node where to Render with `document.getElementById(‘NodesIdValue’).`
	
ComponentToRender – const JSX = ( <h1>Render Me at the Target Node</> );
One JSX and JavaScript difference --> Use className not class in camelCase eg. onClick


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

 	MyComponent.propTypes = { quantity: PropTypes.number.isRequired }
##### Access Props With this.props when passing props to ES6 child class components and not a stateless functional component

		class App extends React.Component {
		  render() {
		    return (
		        <div>
		            <Welcome name={'zayyan'}/>	</div>
		class Welcome extends React.Component {    //ES6 CHILD CLASS COMPONENT
		  render() {
		    return (
		        <div>
		          <p>Hello, <strong>'{this.props.name}'</strong>!</p>   </div>
	    
##### Props with Stateless Functional Components

	class CampSite extends React.Component {	/CampSite renders child Camper
	  render() {   return (
		        <Camper />
	    	); }				// both types of function render
	const Camper = function (props){  return <p>{props.name}</p>  };	//renders html and passed in prop

	Camper.defaultProps = { name: 'CamperBot'}; 	// Camper is assigned default properties
	Camper.propTypes = {name: PropTypes.string.isRequired };	
 			//propTypes are defined on the Camper component which requires name as a provided prop of type string

function you write which accepts props and returns JSX. A stateless component, on the other hand, is a class that extends React.Component, but does not use internal state (covered in the next challenge). Finally, a stateful component is a class component that does maintain its own internal state.
		
##### Create a Stateful Component

How? Declare a state property on the component class in its constructor


		this.state = { //JavaScript object
  			property: value 
     			}

The state can updated, rendered in the UI, or passed as a prop to child components.  
`NOTE: class components are created by extending React.Component.`


##### Render State in the User Interface

State allows to track data and if it changes to make changes in UI by triggering render

	class MyComponent extends React.Component {	//Define a components initial state below	
	    this.state = { 			//Initializing state in constructor makes component stateful
	      name: 'freeCodeCamp'
	  render() {				//state data can be accessed in render
	    return (
	          <h1>{this.state.name}</h1> //access state data with this.state

##### Render State another way

	    render() {		//JavaScript can be written in render before return and accessed in return
	      const name = this.state.name;
	    return (
	      <div>
	          <h1>{name}</h1>
	      </div>
       
##### Set State with this.setState

To update a components state call method this.setState() 
Pass in an object with key value pairs.
Keys = state

 	this.setState({	    //To update username stored in state
  		username: 'Lewis'
		});

Eg. 

	    this.state = {
	      name: 'Initial State' 		//Initial state on the UI is the h1 below
	    };
	    this.handleClick = this.handleClick.bind(this);  //Binds this to the class method handleClick
	   }
	  handleClick() {		//event handler method used to update state
	      this.setState({
	        name: 'React Rocks!'
	      })
	   render() {
	     return (
	       <div>
	         <button onClick={this.handleClick}>Click Me</button>      //event handler triggered by button click
	         <h1>{this.state.name}</h1>	//When button clicked h1 is changed from initial state to new state in handlClick
	       </div>

 ##### Bind 'this' to a Class Method

 this.handleClick = this.handleClick.bind(this);


	 
