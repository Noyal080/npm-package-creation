#### Installing
To install `travel-itinerary`, you can use npm:
	
		npm i travel-itinerary
#### Install dependencies
Before using `travel-itinerary`, you need to ensure that you have the following dependencies installed in your project:

     npm install react react-dom 
     npm install react-leaflet

#### About
`travel-itinerary` is a React library designed to support geolocation-related planning within web applications. It uses the `react-leaflet` library to generate interactive maps for users, allowing them to drop markers or input locations to plan trips or geo-planning activities. Key features include:
-   Generation of a polyline to display the path from the origin to the destination.
-   Visualization of elevation data through a chart, showing the elevation of both the origin and destination points.

#### ViewMap Component:
This component renders the map using `react-leaflet` and shows the markers, polyline and the elevation based on provided data.
##### Usage:

	import  React  from  'react'; 
	import {Loader} from 'semantic-ui-react';
	import { ViewMap } from  'travel-itinerary';
	const App = () =>{
	const dummyData = {
		origin :"Kathmandu",
		destination:"Pokhara",
		originElevation: "2234m",
		destinationElevation: "1658m",
		originLatLng:[,],
		destinationLatLng: [,],
		encodedPolyline:""
		}
	const loader = <Loader active /> //For Semantic UI loader
	return(
	<div>
	<ViewMap 
 	data={dummyData} 
	mapConfig ={
	showElevation: true,
	url : url,
	attribution: attribution,
	markerIcon : markerIcon,
	polylineColor : red
	loader : loader
	zoom : "5"
	mapPosition : [],
	}
	 />
	</div>
	);
	}
	export default App;
	
#### InteractiveMap Component:
This component renders the map using `react-leaflet` and asks the users to drop the data for the origin and destination and then generates the polyline using Api used within.
##### Usage:

	import  React  from  'react'; 
	import { InteractiveMap } from  'travel-itinerary';
	const App = () =>{
	const [formData , setFormData ] = useState('');
	const loader = <Loader active /> //For Semantic UI loader
	return(
	<div>
	<InteractiveMap data={formData} setData={setFormData} 
	mapConfig ={
	url : url,
	attribution: attribution,
	markerIcon : markerIcon,
	polylineColor : red
	loader : loader
 	zoom : "5"
	mapPosition : [],
	} >
		<Form {formData , setFormData } />
		<ElevationInfo />
	</InteractiveMap>
	</div>
	);
	}
	export default App;

#### ElevationChart Component
This component uses the `c3.js` library to generate and display an elevation chart of origin destination to the user.
##### Usage
	import  React  from  'react'; 
	import { ElevationChart} from  'travel-itinerary';
	import bg from "../assets/bg.png";
	const App = () =>{
	const chartData = [ {
	day : 1,
	label : "KTM",
	elevation:"2234m",
	},
	{
	day : 2,
	label : "Pokhara",
	elevation:"1658m",
	} ,
	...
	]
	const loader = <Loader active /> //For Semantic UI loader
	return(
	<div>
	<ElevationChart 
	title={title}
	data={chartData} 
	backgroundImage={bg}
	chartColor= {"red"}
	loader={loader}/>
	</div>
	);
	}
	export default App;



