# <img src="https://emojis.slackmojis.com/emojis/images/1483052921/1537/vue.png?1483052921" width="30px" height="30px"> [Vue/Firebase] TaskCrud

<h4> This project is created to show a complete crud using vue and firebase. </h4>
<hr>

<h3> Project Description 📖 </h3>

The project allows creating user accounts by entering an email and password.

Once the account is created, each user can create, edit and delete various tasks. In addition, the project has control of protected views.

<h3> Pre-requisites 📋 </h3>

* Get your **Api-Key** in <a href= https://firebase.google.com> Firebase </a>
    * Once on the page, log in and click on "go to console" then add a new project.
    * When having the project created go to build -> authentication -> "Get Started" and click on native providers: Email/Password, then push enable and save.
    * Now click "⚙️" -> Project settings -> General, and copy your Api Key.
* Create a **DataBase** in <a href= https://firebase.google.com> Firebase </a>
    * After the first step, go to Build -> Realtime Database and click on "Create Database".
    * Security Rules: click in Start in locked mode, and then enable.
    * Copy the link of your new Database.
    * Before finishing the step go to rules -> Edit rules and leave the rules as the following.
    ```
    { "rules": {
      "tareas":{
        "$uid":{
              ".read": "auth.uid === $uid",
   					  ".write": "auth.uid === $uid"
               }
            }
        }
    }
    ```
    * Finally click in publish.

<h3> Getting Started ⚙️ </h3>

* Clone the repository. 
```
git clone https://github.com/chriz96/TaskCrud-Vue-Firebase
```
* Install NPM packages.
```
npm install
```
* Enter your Api-Key and DataBase Url in <code>../src/store/index.js</code>
```
Line 4: var apiKey = 'Enter your api key'
Line 5: var urlDB = 'Enter your DataBase Url'
```
* Finally Run the project.
```
npm run serve
```
<h3> Built with 🛠️ </h3>

* [**Vue version 3.0.0.**](https://vuejs.org)
* **Vue router 4.0.0.**
* **Vuex 4.0.0.**
* **Javascript.**

<h3> Live-Demo 🔴 </h3>

[**Vue TaskCrud Live-demo**](https://task-manager-firebase.netlify.app)

#