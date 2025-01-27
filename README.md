# MERN

### Project Structure
```
mern-hello-world
├── backend
│   ├── server.js
│   ├── package.json
│   └── node_modules
├── frontend
│   ├── public
│   │   └── index.html
│   ├── src
│   │   ├── App.js
│   │   ├── index.js
│   │   └── components
│   │       └── HelloWorld.js
│   ├── package.json
│   └── node_modules
├── .gitignore
└── README.md
```

---

### Steps to Create the Project

#### 1. **Set up the Backend (Node.js + Express)**
1. Create a folder called `backend` and navigate into it.
2. Initialize a Node.js project:
   ```bash
   npm init -y
   ```
3. Install dependencies:
   ```bash
   npm install express cors
   ```
4. Create `server.js` in the `backend` folder:
   ```javascript
    const express = require('express');
    const cors = require('cors');
    const app = express();
    const PORT = 5000;
    
    // Enable CORS
    app.use(cors());
    
    // Define a route for the root ("/")
    app.get('/', (req, res) => {
        res.send('Welcome to the Backend! Navigate to /api/hello to see the message.');
    });
    
    // Define the API route
    app.get('/api/hello', (req, res) => {
        res.json({ message: 'Hello World from the Backend!' });
    });
    
    // Start the server
    app.listen(PORT, () => {
        console.log(`Server is running on http://localhost:${PORT}`);
    });
   ```
5. Run the server:
   ```bash
   node server.js
   ```

---

#### 2. **Set up the Frontend (React)**
1. Navigate to the root directory and create a folder called `frontend`.
2. Initialize a React project:
   ```bash
   npx create-react-app frontend
   ```
3. Navigate into the `frontend` folder:
   ```bash
   cd frontend
   ```
4. Install Axios for API calls:
   ```bash
   npm install axios
   ```
5. Create a new component `HelloWorld.js` in `src/components`:
   ```javascript
   import React, { useEffect, useState } from 'react';
   import axios from 'axios';

   const HelloWorld = () => {
       const [message, setMessage] = useState('');

       useEffect(() => {
           axios.get('http://localhost:5000/api/hello')
               .then(response => setMessage(response.data.message))
               .catch(error => console.error('Error fetching data:', error));
       }, []);

       return (
           <div>
               <h1>{message}</h1>
           </div>
       );
   };

   export default HelloWorld;
   ```
6. Update `App.js` to use the `HelloWorld` component:
   ```javascript
   import React from 'react';
   import HelloWorld from './components/HelloWorld';

   const App = () => {
       return (
           <div>
               <HelloWorld />
           </div>
       );
   };

   export default App;
   ```
7. Start the React development server:
   ```bash
   npm start
   ```

---

#### 3. **Run the Full MERN Project**
1. Start the backend server:
   ```bash
   cd backend
   node server.js
   ```
2. Start the frontend server:
   ```bash
   cd frontend
   npm start
   ```
3. Open your browser and navigate to `http://localhost:3000`. You should see:
   ```
   Hello World from the Backend!
   ```

---

This is a basic "Hello World" MERN project setup. You can expand it further by integrating MongoDB or deploying it to a cloud platform.
