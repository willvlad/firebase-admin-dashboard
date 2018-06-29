# Starter Project For Building Admin Dashboards For Firebase Apps

Easily create admin dashboards for your Firebase powered apps. For example, you
can create a merchant dashboard for uploading items on an e-commerce site which
uses Firebase as the backend.

## Project Structure

- **dashboard:** contains a react based app which will be served using
  Firebase hosting. It hits a Firebase cloud function `api`
  defined inside `functions` folder.
- **functions:** contains an `api` cloud function which is basically
  an Express based API for your app. Your write all your protected business
  logic here.

### Setup

1.  Put your Firebase project's name in `.firebaserc`.
2.  Set a secret key for JWT token on Firebase.
    ```sh
    firebase functions:config:set auth.secret="<YOUR_SECRET>"
    ```
3.  For every admin user, run the npm script from `functions` folder:
    ```sh
    yarn run passwdgen <username> <password>
    ```
    and follow further instructions.
4.  In `dashboard/src/globals.js` file, set your local and production cloud
    functions endpoints in API_URL. To get these values, run:

    for local

    ```sh
    firebase serve --only functions
    ```

    for production

    ```sh
    firebase deploy
    ```

### Debugging

1.  Get a copy of Firebase environment variables set on the server, for running the functions locally. From
    `functions` folder, run
    ```sh
    firebase functions:config:get > .runtimeconfig.json
    ```
2.  Run the functions locally
    ```sh
    firebase serve --only functions
    ```

### Deploying

Run `deploy.sh`.

#### Help

Please open a new issue in case you are facing some problem or write to me at
rajat@raynstudios.in.
