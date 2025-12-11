___

ssh -L 8080:localhost:8080 arielxbp@192.168.1.106

curl -X POST http://localhost:8080/session   -H "Content-Type: application/json"   -d '{"name":"alice"}'

## Vue Router

A **Vue Router** manages navigation in a single-page application (SPA). It maps URL paths to Vue components and renders them without reloading the entire page.

---

## What It Does

| Function                | Description                                                 |
| ----------------------- | ----------------------------------------------------------- |
| **URL Matching**        | Maps paths like `/login` to components like `LoginView.vue` |
| **Component Rendering** | Shows the correct component based on the URL                |
| **Navigation**          | Allows moving between "pages" without full page reload      |
| **History Management**  | Handles browser back/forward buttons                        |
| **Parameters**          | Extracts dynamic values from URLs like `/users/123`         |

## Your router configuration

```javascript
import {createRouter, createWebHashHistory} from 'vue-router'

import HomeView from '../views/HomeView.vue'

import LoginScreen from '../views/LoginScreen.vue'

  

const router = createRouter({

    history: createWebHashHistory(import.meta.env.BASE_URL),

    routes: [

        {path: '/', component: HomeView},           // localhost/#/ → HomeView

        {path: '/link1', component: HomeView},      // localhost/#/link1 → HomeView

        {path: '/link2', component: HomeView},      // localhost/#/link2 → HomeView

        {path: '/users/:id/conversations', component: HomeView},  // Dynamic param

        {path: '/session', component: LoginScreen}, // localhost/#/session → LoginScreen

    ]

})

  

export default router
```


## How It Works

### 1. User visits URL

```
Browser: http://localhost:5173/#/session
                                ↓
Router matches: path: '/session'
                                ↓
Router renders: LoginScreen component
```

### 2. `<RouterView />` placeholder

In `App.vue`, the router injects the matched component here:

```vue
<template>
    <header>...</header>
    <main>
        <RouterView />  <!-- Router puts the component HERE -->
    </main>
</template>
```

### 3. Navigation without page reload

```vue
<!-- Link-based navigation -->

<RouterLink to="/session">Go to Login</RouterLink>

  

<!-- Programmatic navigation -->

<script>

export default {

    methods: {

        goToLogin() {

            this.$router.push('/session')  // Navigate via code

        }

    }

}

</script>
```


## doLogin

- [x] API
- [x] Backend
- [ ] Frontend

## setMyUserName

- [x] API
- [ ] Backend
- [ ] Frontend

## getMyConversations

- [x] API
- [ ] Backend
- [ ] Frontend

## getConversation

- [x] API
- [ ] Backend
- [ ] Frontend

## sendMessage

- [x] API
- [ ] Backend
- [ ] Frontend

## forwardMessage

- [x] API
- [ ] Backend
- [ ] Frontend

## commentMessage

- [x] API
- [ ] Backend
- [ ] Frontend

## uncommentMessage

- [x] API
- [ ] Backend
- [ ] Frontend

## deleteMessage

- [x] API
- [ ] Backend
- [ ] Frontend

## addToGroup

- [x] API
- [ ] Backend
- [ ] Frontend

## leaveGroup

- [x] API
- [ ] Backend
- [ ] Frontend

## setGroupName

- [x] API
- [ ] Backend
- [ ] Frontend

## setMyPhoto

- [x] API
- [ ] Backend
- [ ] Frontend

## setGroupPhoto

- [x] API
- [ ] Backend
- [ ] Frontend