Budget Categories
===

## Feature Tasks

### Category
Create a `category` folder for this feature.

In this application, a category should contain *(at least)* the following properties
* `id` - a unique identifier (use `shortid`, or `uuid`)
* `timestamp` - a date from when the category was created (use `new Date()`)
* `name` - a string that is the name of the category
* `budget` - a number that is the total amount of money in the category

### Redux

#### reducer
* create a `reducer.js` in your your feature directory
* This reducer should support the following interactions:
  * `CATEGORY_CREATE`
  * `CATEGORY_UPDATE`
  * `CATEGORY_DESTORY`
  * (These are also your action constants)

#### action creators

Create an action creator for each interaction supported by your category reducer. The createCategory action is
where you should add the id and timestamp to a newly created category

#### store
* in `lib/store.js` export a function that will return a new redux store based on your (imported) category reducer

### Components
* create the following component and structure it according to the diagram below:
```
Provider
  App  
    BrowserRouter
      Route / Dashboard
        CategoryForm -- for creating categories
        [CategoryItem] (array of components)
           CategoryForm  -- for updating categories
```

### `index.js`

The redux store should be created and the `<Provider>` component should wrap the `<App>` component

### App Component

* the App component should setup the `Router`

### Dashboard Component
* should be displayed on the `/` route
* should use react-redux's `connect` to map state and dispatch methods to props
* should display a `CategoryForm` for adding categories to the application state
* should display a `CategoryItem` for each category in the application state

### CategoryForm Component
* should expect an `onComplete` prop to be a function
  * that function should be invoked with the `CategoryForm`'s state when the form is submitted
* should expect a `buttonText` prop to configure the submit button text ("Add" or "Update")

### CategoryItem Component
* should display the category's name and budget
* should display a delete button
  * `onDelete` the category should be removed from the application state
* should display a `CategoryForm`
  * `onComplete` the form should update the component in the application state