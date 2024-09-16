# React2.0

To write JavaScript within JSX surround code with curly braces

	 { - javascript code - }
JSX returns a single element so a parent element should wrap all nested elements --> parentheses ( allows rendering of multiple elements)

 	return (
	 	<div> 			//This is the Parent element
			<p></p> 	//This is the Child element
		</div> 
  		);

##### To comments out in JSX {/*open close*/} --> 
					`{/*The comment to comment out goes between these */}`

##### Render JSX to the HTML DOM by using React’s rendering API -->
`ReactDOM`
##### Rendering a React element --> 
`ReactDOM.render( componentToRender, whereToRender);`

##### 1st Select the target DOM node or where to Render --> 
`document.getElementById(‘NodesIdValueHere’).`
	
##### 2nd The ComponentToRender --> 
`const componentToRender = (<h1>Render Me at the Target Node</>);`

##### One JSX and JavaScript difference --> 
`Use className not class in camelCase eg. onClick`
<br/>

### 2 ways to create/define a React component
|1st JavaScript function|- They are stateless which receives and renders data|
|:---:|:--:|
||- It returns either JSX or null|
||- Functions begin with capital|
<br />
		
  	const DemoComponent = function() {
		return (
		 <div>something her</div>
		)};
 
|2nd ES6 class syntax|classes extends React.Component class|
|:---:|:--:|
||classes has a constructor METHOD defined|

	class DemoComponent extends React.Component {  
		constructor(props) { 
		super(props);	//Constructor uses super to call the Parents constructor 
		}				//and also passes props to both Parent and Child
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

`this.functionName = this.functionName.bind(this);`

`this.increment = this.increment.bind(this);`  - Binds this to the function increment. This must be bound to all function in component

`<button className='inc' onClick={this.increment}>Increment!</button>`  - When the button is clicked the funciton increment is triggered

`increment() {`						- The function increment changes the state with .setState() by '+ 1' <br/>
	`this.setState(state => ({`												<br/>
	`count: state.count + 1`												<br/>
	`}));`															<br/>
`}`																<br/>

##### Controlled Input b/c React can control the internal state of an element and make them controlled components

	class ControlledInput extends React.Component {
	  etc..
	    this.handleChange = this.handleChange.bind(this);  //Bind handle function
	  }
	      handleChange(event){			//Set or change state for input
	        this.setState({
	          input: event.target.value		//To access string from input use event
	        })
	      };
	  render() {
	     etc..				//value below updates the state with what is typed in
	         <input type="text" onChange={this.handleChange}  value={this.state.input} />
	        <p>{this.state.input}</p>		//without value the text update from the browser and not the state
     	etc..

##### Pass a callback as Props

	class MyApp extends React.Component {		//Parent component
	    etc... contructor, initial states for input and submit also binding of handlChange method
	  }
	  handleChange(event) {
	    this.setState({
	      inputValue: event.target.value   //value typed in to input box by user set to inputValue
	    });					// now set to state object as this.state.inputValue
	  }
	  render() {
	    return (			//Parent component renders the children components below 
	          <GetInput input={this.state.inputValue} handleChange={this.handleChange}/> //GetInput passed 2 props
	          <RenderInput input={this.state.inputValue}/>		
	   		//property input is passed inputValue from state so it is visible on screen what is input to GetInput 
		  	//GetInput prop1 passed in is input and assigned inputValue from state
		    	//GetInput prop2 passed in is an input handler handleChange to the prop handleChange 
			//After typing in the field of GetInput it calls the function handleChange in parent and updates input in state
	class GetInput extends React.Component { 		///child component
		etc.
	          <input value={this.props.input} onChange={this.props.handleChange}/>
	class RenderInput extends React.Component { 		///child component
		etc.
	        <p>{this.props.input}</p>
##### Pass an Event Handler as a prop

	function Talker(){
	talker component with event handler talk
	    function talk(){
	    }
	    return <Button talk={talk}/> pass event handler to button as a 'prop'
	}

##### Receive an Event Handler as a prop
Give that JSX element an attribute and value in curly braces. Attribute: name = event name (onClick or onHover), Value = event handler.

	<button onClick={props.talk}>
	      Click me!
	</button>

	 
