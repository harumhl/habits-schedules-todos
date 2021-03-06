# regression-on-stock-market

Tools used
* UI: React.js (Firebase)
* Backend: Spring Boot (Heroku)
* Logic Server: Python (Heroku)
* Database: Firebase

Components
- UI/Frontend displays the analysis and the forecast chart
- Backend gathers data and triggers the analysis
- Logic analyzes the data and forecasts


Current plan
1. build the backend to gather the data
2. link the backend to trigger the analysis
3. build the logic server to analyze the data
4. build the frontend to display the data
5. improve the logic to forecast the future cases
6. improve (especially #3-5)


To Do (Nov/19/2018), especially with Spring Boot backend
1. Set the spring boot to have controller/service/repo
2. Host the spring boot backend to a server (Heroku)
3. Make the spring boot to gather data
4. Make the spring boot to store the gathered data
5. Make the spring boot to retrieve the data (to hand it off to the Logic server)


React-app
* Using axios for http requests
```
$ npm start
$ npm run build
move the build folder content to public
```

React Native
```
$ lsof -i :19003
$
$ react-native run-ios
$ react-native bundle --entry-file index.js --platform ios --dev false --bundle-output ios/main.jsbundle --assets-dest ios (react native doesn't create main.jsbundle automatically)
$ killall node (save 8081)

```

Spring Boot
```
$ export PATH=/Library/Maven/apache-maven-3.6.0/bin:$PATH
$ mvn package
$ git subtree push --prefix spring-boot-backend regression-on-sm-backend master
$ cd spring-boot-backend/ && mvn install && cd .. && git subtree push --prefix spring-boot-backend regression-on-sm-backend master
```

Heroku (https://devcenter.heroku.com/articles/getting-started-with-python)
```
$ git add .
$ git commit
$ git push heroku master (in python folder)
$ heroku open
```

Firebase
```
$firebase deploy
HOW TO GET ID TOKEN: POST https://www.googleapis.com/identitytoolkit/v3/relyingparty/verifyPassword?key=[API_KEY], with body {"email": "EMAIL", "password": "PASSWORD", "returnSecureToken": true
HOW TO GET DATA: GET https://firestore.googleapis.com/v1beta1/projects/PROJECT_ID/databases/(default)/documents/COLLECTION_NAME/DOCUMENT_NAME, with no body but header {AUTHORIZATION: "Bearer ID_TOKEN", Content-Type: application/json}
HOW TO UPDATE DATA: PATCH https://firestore.googleapis.com/v1beta1/projects/PROJECT_ID/databases/(default)/documents/COLLECTION_NAME/DOCUMENT_NAME, with header {AUTHORIZATION: "Bearer ID_TOKEN", Content-Type: application/json} and body {"name": "projects/PROJECT_ID/databases/(default)/documents/COLLECTION_NAME/DOCUMENT_NAME", "fields": {"NEW_FIELD_NAME": {"stringValue": "VALUE"}}, "createdTime": "TIMESTAMP", "updatedTime": "TIMESTAMP"}
HOW TO ADD DATA: POST https://firestore.googleapis.com/v1beta1/projects/PROJECT_ID/databases/(default)/documents/COLLECTION_NAME?documentId=NEW_DOCUMENT_NAME, with header {AUTHORIZATION: "Bearer ID_TOKEN", Content-Type: application/json} and body {"fields": {"NEW_FIELD_NAME": {"stringValue": "VALUE"}}}
(datatype info: https://firebase.google.com/docs/firestore/reference/rest/v1beta1/Value)
```
