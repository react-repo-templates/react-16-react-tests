# Advanced Frontend with React.js (Sprint 16)
Testing JS Applications (React Applications)

# Application
- The application is very simple. It consists of two components, **App** and **Info**, and one service module named **DataService**
- **DataService** gathers information from the GitHub API using a *username*
- Run the application with ```npm start```
- Open a web browser at ```http://localhost:3000``` (the browser opens automatically after the previous command)

## Tasks
Write unit tests that check the functionality of every module (components and the service) with Jest:
- [ ] **App** component
- [ ] **Info** component
- [ ] **DataService** module

Place every test module in the ```src/tests``` directory.
Replace the fake tests that are already there. Until you replace them, ```npm test``` fails, and that failure is expected.
Assertions must exercise the real modules. An assertion such as ```expect(2 + 2).toBe(4)``` does not count.

Jest reports coverage for statements, branches, functions, and lines. Each of these must be at least **90%**.
Check coverage with ```npm test -- --watchAll=false --coverage```.

## Pieces of advice
- The application is written with **create-react-app**, which includes a pre-configured Jest setup
- When you need test doubles (mocking), create a ```src/__mocks__``` directory and put the mock modules there
- While testing **DataService**, mock the third-party library **axios**. **DataService** calls ```axios.get``` with ```https://api.github.com/users/${user}``` and returns that response
- While testing **Info** and **App**, mock ```getGitHubUser``` so the tests do not call the GitHub API
- **Info** loads data asynchronously. The first render uses an empty object. After the request settles, the component lists fields from ```response.data```, or shows ```error: request error``` when the request fails. Assert that result with an async query such as ```findBy``` or ```waitFor```
- **Info** requests data again when the ```user``` prop changes
- **App** renders the text ```Hello World!``` and two **Info** components, for the users ```yurkovskiy``` and ```mplesha```

*I hope this little task will help you to understand some basics of unit testing*
