# Vue.js Workshop Part  1

## Introduction

Welcome to the Vue.js Workshop Part 1! This session is designed to introduce you to the basics of Vue.js. By the end of this workshop, you'll have a solid foundation in Vue.js and the skills to build basic Vue applications.

### Workshop Goals
- Understand Vue.js fundamentals
- Learn to create and navigate between pages
- Implement a NavBar using Vue.js
- Manage global state with Vuex
- Create reusable components, like a Card component

### Summary
- **Introduction**: 5 minutes
- **Step 0 - Installation**: 15 minutes
- **Step 1 - New Page & Navigation**: 30 minutes
- **Step 2 - NavBar**: 30 minutes
- **Step 3 - Global State with Vuex**: 30 minutes
- **Step 4 - Card Component**: 30 minutes
- **Q&A and Wrap-Up**: 10 minutes

## Resources
- [Vue Vite Documentation](https://vitejs.dev/)
- [Vuex State Management](https://vuex.vuejs.org/guide/state.html)

## Step 0: Installation and Setup

### Prerequisites
Ensure you have Node.js installed on your system. You can download it from [Node.js Official Website](https://nodejs.org/).

### Creating a New Vue Project
1. **Install Vite**: Vite is a build tool that aims to provide a faster and leaner development experience for modern web projects. To create a new project, run:
   ```bash
   npm create vite@latest my-vue-app --template vue
   ````
    Replace my-vue-app with the name of your project.
2. **Navigate to your project folder**:
    ```bash
    cd my-vue-app
    ```
3. **Install Dependencies**: Install Vue dependencies in your project.
    ```bash
    npm install
    ```
### Adding Vuetify
1. **Install Vuetify**: Add Vuetify to your project.
    ```bash
    npm install vuetify
    ```

2. **Configure Vuetify**: Import and use Vuetify in your `main.js` file.
    ```javascript
    import { createApp } from 'vue'
    import App from './App.vue'
    import vuetify from './plugins/vuetify' /* Ensure this path is correct */

    const app = createApp(App)

    app.use(vuetify)

    app.mount('#app')
    ```

3. **Create a Vuetify Plugin File**: In the plugins directory, create a `vuetify.js` file. Here's a basic setup:
    ```javascript
    // plugins/vuetify.js
    import 'vuetify/styles'
    import { createVuetify } from 'vuetify'
    export default createVuetify()
    ```

4. **Include Vuetify CSS**: Make sure to include Vuetify CSS in your project. You can add it to your `index.html` or main entry file.

### Running the Project
Once everything is set up, you can start your Vue.js project:

```bash
npm run dev
```

This command will start the local development server. You can access your application by going to http://localhost:5173 in your web browser.


## Step 1: Creating a New Page with Vuetify

In this step, you will learn how to create a new page in your Vue.js application and enhance it with Vuetify components, including a navigation button.

### Installing Vue Router

First, ensure that Vue Router is installed to manage page navigation:

```bash
npm install vue-router
```

### Adding a New Page

1. **Create a New Vue Component**: This will be your new page. In your project's `src/views` directory, create a new file, for example, `MyNewPage.vue`.

2. **Structure Your Page with Vuetify**: Use Vuetify components to layout your page. A simple structure may include a container, a text component, and other UI elements.

   ```vue
   <template>
     <v-container>
       <v-row justify="center">
         <v-col cols="12" sm="8" md="6">
           <h1>Bastien Mon Bébou</h1>
           <p>Welcome to the new page!</p>
           <!-- Add more Vuetify components as needed -->
         </v-col>
       </v-row>
     </v-container>
   </template>
   ```

### Implementing Navigation

1. **Configure Vue Router**: In your `src/router/index.js`, add a route for your new page.

   ```javascript
   import MyNewPage from '../views/MyNewPage.vue'

   const routes = [
     // other routes...
     { path: '/new-page', name: 'NewPage', component: MyNewPage },
   ]
   ```

2. **Add a Navigation Button**: Use a Vuetify button component to navigate to your new page. This button can be placed on your homepage or any other component.

   ```vue
   <template>
     <v-btn color="primary" to="/new-page">Go to New Page</v-btn>
   </template>
   ```

   The `to` attribute in `v-btn` is used for navigation, similar to `<router-link>` in Vue Router.

### Example: New Page Component

Here's a basic example of a new page component using Vuetify:

```vue
<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="12" sm="8" md="6">
        <h1>My New Page</h1>
        <p>Welcome to the new page!</p>
        <!-- Add more Vuetify components as needed -->
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'MyNewPage'
  // You can add script data, methods, etc. here
}
</script>
```

By following these steps, you can effectively create a new page and incorporate navigation within your Vue.js application using Vuetify.


## Step 2: NavBar with Vuetify

In this step, we will create a responsive and stylish navigation bar (NavBar) using Vuetify components.

### Designing the NavBar

1. **Import the Vuetify Components**: In your component where you want to add the NavBar, make sure to import the necessary Vuetify components. For a basic NavBar, we will use `VAppBar`, `VToolbarTitle`, and `VBtn`.

   ```javascript
   import { VAppBar, VToolbarTitle, VBtn } from 'vuetify/components'
   ```

2. **Add the Vuetify NavBar Markup**: Use the Vuetify components to structure your NavBar. Here's an example of a basic NavBar layout:

   ```vue
   <template>
     <v-app-bar app>
       <v-toolbar-title>My Vue App</v-toolbar-title>
       <v-spacer></v-spacer>
       <v-btn text to="/your-route">Home</v-btn>
       <!-- Add more buttons as needed -->
     </v-app-bar>
   </template>
   ```

   - `v-app-bar`: The container for your NavBar.
   - `v-toolbar-title`: To display the title of your application or website.
   - `v-spacer`: This pushes your navigation items to the right.
   - `v-btn`: Represents a button in the NavBar. The `to` attribute is used for navigation, similar to `<router-link>`.

3. **Styling the NavBar**: You can style your NavBar using Vuetify's built-in classes or custom CSS. Vuetify offers a wide range of options for colors, spacing, and more.

### Integrating Navigation

1. **Setup Vue Router**: Make sure you have Vue Router set up in your project for navigation.

2. **Linking Pages**: Use the `to` attribute in `v-btn` to navigate to different pages. For example:

   ```vue
   <v-btn text to="/">Home</v-btn>
   <v-btn text to="/about">About</v-btn>
   ```

   These buttons will navigate to the Home and About pages of your application.

3. **Responsive Design**: Vuetify's NavBar is responsive by default. However, you can further customize it for different screen sizes using Vuetify's breakpoint system.

### Example: Complete NavBar Component

Here's an example of a complete NavBar component using Vuetify:

```vue
<template>
  <v-app-bar app>
    <v-toolbar-title>My Vue App</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn text to="/">Home</v-btn>
    <v-btn text to="/about">About</v-btn>
    <!-- Add more navigation buttons as needed -->
  </v-app-bar>
</template>

<script>
export default {
  name: 'NavBar',
  components: {
    VAppBar,
    VToolbarTitle,
    VBtn
  }
}
</script>
```

This component creates a functional NavBar with home and about buttons for navigation. You can expand this NavBar by adding more buttons, dropdowns, or other elements as needed.


## Step 3: Global State with Vuex

Managing global state is a crucial part of larger applications. Vuex is a state management pattern and library for Vue.js applications.

### Installing Vuex

First, install Vuex in your project:

```bash
npm install vuex@next
```

### Setting Up Vuex

1. **Create a Store**: In your project's `src/store` directory, create a new file, `index.js`.

2. **Configure the Store**: Set up the state, mutations, actions, and getters.

   ```javascript
   import { createStore } from 'vuex'

   export default createStore({
     state: {
       // your state properties
     },
     mutations: {
       // your mutations
     },
     actions: {
       // your actions
     },
     getters: {
       // your getters
     }
   })
   ```

3. **Use the Store in Your Application**: Import and use the store in your `main.js`.

   ```javascript
   import { createApp } from 'vue'
   import App from './App.vue'
   import store from './store'

   createApp(App).use(store).mount('#app')
   ```

Refer to the [Vuex Documentation](https://vuex.vuejs.org/) for more detailed instructions on creating and managing a shared state.

## Step 4: Card Component with Vuetify

Developing reusable components like a Card component is simplified with Vuetify.

### Creating a Vuetify Card Component

1. **Define the Card Component**: In your `components` directory, create a new file, `MyCard.vue`.

2. **Add Vuetify Card Markup**: Utilize Vuetify's `v-card` component to structure your card.

   ```vue
   <template>
     <v-card>
       <v-card-title>{{ title }}</v-card-title>
       <v-card-text>{{ description }}</v-card-text>
       <!-- Add more Vuetify components as needed -->
     </v-card>
   </template>

   <script>
   export default {
     props: {
       title: String,
       description: String
     }
   }
   </script>
   ```

3. **Use the Card Component**: Import and use your card component in other parts of your application, passing the necessary props.

### Example: Displaying a List of Cards

To display a list of cards:

```vue
<template>
  <div>
    <my-card
      v-for="(item, index) in items"
      :key="index"
      :title="item.title"
      :description="item.description"
    />
  </div>
</template>

<script>
import MyCard from '@/components/MyCard.vue'

export default {
  components: {
    MyCard
  },
  data() {
    return {
      items: [
        // Your items here
      ]
    }
  }
}
</script>
```

## Bonus Step

Feel free to explore more advanced Vue.js and Vuetify features and expand on the exercises provided.

## Feedback

Your feedback is invaluable in improving future workshops. Please share your thoughts and suggestions about this workshop.

Thank you for participating in our Vue.js and Vuetify Workshop!

## Contacts Us
**Malek Gatoufi**: malek.gatoufi@epitech.eu

**Bastien Rodriguez**: bastien.rodrigues@epitech.eu
