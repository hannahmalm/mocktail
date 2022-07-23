1. mkdir project_name
- optionally set up with git hub
- log into github and select new repo
- git init

2. mkdir backend
3. mkdir frontent 
mkdir = make directory 
4. Add in notes.md file to take notes
5. cd into the backend
    - cd is change directory
6. rails new backend-project_name --api
    - using the api flag prevents gems and dependencies from being created
    - user resource generators
7. Draw out main components of website with relationships
    - I want this website to have a homepage (text), about me (text, image), recipes (name, image, description-text, ingredients (text), directions), contact me (text)
    - cd into the backend-mocktail
8. rails g resource Recipe name image description ingredeient directions
    - This means that a Recipe has a name, image, description, ingredients, and directions
    - after running this, look in the 'db' folder under migrate
    - 



    rails g resource Run category total_distance:float 
    rails g resource Log run_id:integer distance:float pace:decimal date:date notes:string 
2. Add in basic controllers and models
    - Relationships and validations --> Most validations are on the front end
    ---- Models----------------
            - User will have mutliple run types that each have multiple logs

            Runs - These will be created on backend. A run has many logs
            ++++
            category - string
            instructions - string


            Logs. A log belongs to a Run
            +++++
            run_id - integer
            distance - float
            pace - decimal
            date - date
            notes - string 
3. Add in serializer gem and serializers --> Serializers are used to create custom JSON responses
    rails g serializer run --> add in appropriate attributes to display
    rails g serializer log --> add in appropriate attributes to display
4. Add in Routes --> Namespaced and nested
5. Add in Cors --> Cross Origin Resource Sharing --> Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.
6. Add in Seed data --> Run Types will be standardized - these will not change so add these in to the DB. 
7. Set up repos for both and push

-------FRONTEND---------
1. create-react-app frontend-run
2. Test the front end fetch using component did mount in App.js and console log
     - componentDidMount is a lifecycle method that can be used to test the fetch - this was the first step to ensuring backend and frontend are working properly 
     - test fetch - asynch, request will take some time, dont do anything with the data until you get respopnse back
     - fetch request returns a promise which is a promise that it will bring back data
3. Add in the redux pacakge
    npm install redux react-redux redux-thunk react-router-dom --save
4. Import the things needed for the store into the index.js --> This could also be broken out into a store.js file 
    - import {createStore, applyMiddleware, compose} from 'redux' //compose combines all the different middlewares
    - import thunk from 'redux-thunk' //lets you make asynch calls to the backend used for any fetch calls 
    - import {Provider} from 'react-redux' //Library used for integrating Redux and React together    
    *Three librarys to import from: redux, redux-thunk, react-redux
5. Home component
    - This is the first thing that renders when the app starts up
    - For this app, this is STRICTLY presentational and static --> this will never change
    - I wanted to use differnt types of CSS and HMTML and Iframes to make this homepage educational. This does not hold state because a user is not changing any part of the component
6. Home Container
    - For organization purposes I put the home component into a Home container and rendered it within App.js
    - I kept ALL routes within containers
    - This is not a traditioanl container --> but I liked keeping the main component seperate from the container in case someone adds on to this at a later time. 
    *The 2 "traditional" containers are the Logs Container and the Runs Container *
7. Header & Footer
    - Basic stateless components used only for presentational purposes.
    - These are rendered directly in the App.js because I want them on every page of the application
8. Benefits 
    - This is the last stateless and presiontational component
    - This is a STATIC PAGE and will never change
    - I wanted to include this to incorporate both dynamic and static componenets into the application
    - The link to access benefits is within the Homepage 
    - Used bootstrap icons
9. Benefits container
    - Same as homepage 
    - Not a traditional container -> but wanted to use it to keep routes seperated and ensure that when you visit each route it is its own seperate "page"
10. Run List Component & Run Show & Runs Container
    - Run List Component:
        - Stateless and Presentational but does take in props 
        - Iterate over the runs as props and create a link to each individual run cateogry
    - Run Show Component: 
        - Takes in props from the Runs Container 
        - Finds the specific run category using an array -1 
        - If the run category is within the array and not null, then display the run category and instructions
        - ALSO DISPLAY the logs associated with each run category --> pass in the props to the logs container
    - Runs Container:
        - The runs container is used to pass props down to run list and run show, but it also is asynchronously fetching all the runs as they are updated
        - Anytime component mounts, make a fetch to the backend to get the list of runs created
        --> Action
    - fetchRuns Action
        - Actions are plain objects with a type field and payload, and describe what happened in the app
        - Action creator is a function

11. Run List Header Component & ListHeader Container
10. Import all containers into the App.js to render all pages


1. Create backend and repo
    Use rails new airbnb-backend --api 
    create Github repo for backend
    Install fast JSON, rack cors, and bcrypt
2. Add in models and test data using seeds
    rails g scaffold user 
    rails g scaffold reservation
    rails g model review description user_id:integer listing_id:integer
    rails g model reservation start_date:date end_date:date listing_id:integer user_id:integer
    rails g resource for the rest 
3. Add in basic relationships/validations
4. Add in namespacing in routes and models and controllers
5. Add in statuses in controllers
6. Add in serializers using fastJson api
    - dont wanna see created at or update 
    rails g serializer User name username --> check that attributes are in the code 


7. Add Frontend
    cd into main directory
    check node version
    nvm use stable
    npm install -g create-react-app
    create-react-app airbnb-frontend
    cd airbnb-frontend
    * add in frontend repo
    git init
    git add .
    git commit -m "first commit"
    git branch -M main
    git remote add origin https://github.com/hannahmalm/frontend-run.git
    git push -u origin main
    **
    npm start


- REDUX -> DO THIS IN INDEX.JS
 - https://github.com/zalmoxisus/redux-devtools-extension
    - install package if not installed (npm install redux-thunk, npm install redux, npm install react-redux)
    - import {createStore, applyMiddleWare, compose, combineReducers} from 'redux'
    ** You need a store, reducer(s) or combine reducers, middleWare
    - import {thunk} from 'redux-thunk
    - import {Provider} from 'react-redux'

    - const users = () => []
    - const reducer = combineReducers({users})
  

    - const composeEnhancer = window._REDUX_DEVTOOLS_EXTENSION_COMPOSE_ || compose;
    *This is how you put the middleware together
   

    - Create a store -> takes reducer as an argument and the redux dev tool
        const store = createStore(reducer, composeEnhancer(applyMiddleware(thunk)))

    - Wrap App in Provider
    - Store Prop MUST be provided to provider and must be created using create store

* Create a new folder for actions and for reducers
    - add in users.js to both of these folders because the actions and reducers are on users

REDUX NOTES
    Redux is a predictable state container for JavaScript apps. 
    Redux gives you a single object that holds the state for your entire application in one location 
    Initial State:
    The core concepts of Redux — Store, Actions, Reducers, and Subscriptions.
    The initial state is what it looks like at the start.
    ** FIRST STEP TO REDUX IS CREATING THE STORE **
     1. Three Libraries to import from: redux, redux-thunk, react-redux
        import {createStore, applyMiddleware, compose, combineReducers} from 'redux' 
            - createStore: Creates a Redux store that holds the complete state tree of your app.
            - applyMiddleware: A type of Enahncer. In Redux it takes Thunk
            - compose:
            - combineReducers: 
        import thunk from 'redux-thunk' -->
        import { Provider } from 'react-redux'. This is a way to integrate with the UI framework.
    2. Install the Redux Dev tools 
    Actions:
    With Redux, every action can alter the initial state — which means anything you do can change something around you.
    Reducers:
    Interpret actions
    Reducers take in the argument of the state set to the default initial state and the action. This action helps the reducer determine what needs to be done with the state.
    STORE:
        We have our list of actions and our reducer that can handle our actions
        This is where State is contained
        A State Needs a reducer and an intital state
        With Redux, the state of your application is kept in a store, and each component can access any state that it needs from this store
    - Anything that is changing - all forms - have a state. If there is a state there is anaction and a reducer

    Authentication - Log in Log Out
    - create a reducer for current user
    - This reducer and action for current user
        - This action should post a fetch to the auth controller on the backend
    - Create components folder
        - Create login form
    - When application loads, grab the current user

------VIDEOS AND LINKS -------
https://www.youtube.com/watch?v=YximXs08SS4 VIDEO

https://www.youtube.com/watch?v=uvB4cUi4RrI Routing Video

https://gist.github.com/izikaj/821dc5a2b3c2232ee8713e13f34bc062 Issues with POstgre sql - reinstalled postgres



-------PROJECT REQUIREMENTS-----
The code is written in ES6 as much as possible - yes
create-react-app was used to create your React app  - yes
There are 2 container components  - yes
There are 5 stateless components - yes
There are 3 routes - yes
react-router is being used with proper RESTful routing - yes
Redux and redux-thunk middleware are being used to modify state change and make use of async actions to send data and receive data from the server - yes
Use of Rails API backend to persist data for the application - yes
Good understanding of the react/redux state flow - yes 
Good understanding of state and props in React - yes
Knowledge of async JS with Promises - yes

----------------------------------------------------
https://codesandbox.io/s/react-live-coding-forked-xe6of?file=/src/DogList.js









---MOCK INTERVIEW QUESTIONS-------------------------
How do you create a new react/redux app
    - npx create-react-app my-app --template redux
What is the one-way-data-flow?
    View --> Actions --> State
    1. State describes the condition of the app at a specific point in time
    2. The UI is rendered based on state
    3. When an event happens, the state is updated
    4. The UI re-renders based on new state
How do you update values immutable?
    - Make copies of existing objects/arrays and then modifies copies 
Why Should you use Redux?
    - The patterns and tools provided by Redux make it easier to understand when, where, why, and how the state in your application is being updated, and how your application logic will behave when those changes occur. 
Describe a basic example of Redux
    1. The global state of app is stored in an object tree inside a STORE
    2. The tree gets changed when an action is called and dispatched to the store
    3. To specify how state is updated, create a pure reducer to calculate new state based on old state
Redux Basic Flow
    Store Created --> Initial State --> Action(actual event) --> Dispatch(event trigger) --> Reducer(Event Listener)
What is a dispatch?
    - The only way to update the state is to call store.dispatch() and pass and action type
    - EX: store.dispatch({type: 'counter/increment'})
    - console.log(store.getState()) 
    - triggering the event
What does createStore return?
     An object that holds the complete state of your app. The only way to change its state is by dispatching actions. 
What does createStore take in?
    reducer (function)
    initial state (any object)
    enhancer (function for applyMiddleware)
What is a reducer?
    - a pure function
What does a reducer take in?
    - previous or initial state and an action
What does a reducer return?
    - The new object state (instead of mutating the previous state)
Does a reducer mutate the previous state?
    No!
What are 3 Rules that reducers always have to follow?
    - Only calculate new state value based on state and action arguments
    - not allowed to modify existing stae --> make immutable updates and copies --> change state on copied values
    - Do not do asychnoronus logic --> must be pure
What is an Action?
    - A way to specify mutations or changes that you want to happen
    - An event that describes something that happened 
What are the two objects that Actions have?
    - Type
    - Payload
What is an Action Type?
    - String with domain/eventName
    - EX login/createLogin
What is an Action Payload?
    - Any other fiels with additoinal information about what happened
What are the 3 principles of Redux?
    1.single source of truth - global state of application stored in an object tree within a single source
    2.read onlly - the only way to change the state is to emit an action
    3. Changes are made with pure functions - used to specify how state tree is transformed by actions --> aka pure reducers

How do you change a state?
    States are naturally read only, emit an action to change state
