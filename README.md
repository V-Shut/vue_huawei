# Huawei Test Project

This project is a Vue.js application that fetches and displays quotes from an API, with functionality to copy quotes and save them to the history. It also supports viewing previously fetched quotes.

## Features

- Fetches a random quote from an API on each update.
- Copies the quote to the clipboard with a "Copied!" message.
- Saves and displays a history of previously fetched quotes.
- Displays an error message when there is an issue with the API or network.

## Technologies

- **Vue.js** (version 3)
- **Vite** — a fast development tool
- **Axios** — for HTTP requests (API calls)
- **Clipboard API** — for copying quotes

## Installation

To run the project locally, follow these steps:

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/huawei_test.git
    ```

2. Navigate to the project directory:

    ```bash
    cd huawei_test
    ```

3. Install dependencies:

    ```bash
    npm install
    ```

4. Start the local development server:

    ```bash
    npm run start
    ```

5. Open the application in your browser at [this link](https://vue-huawei.vercel.app/).

## Project Structure

- `src/` — source code of the project.
  - `components/` — components for displaying quotes and buttons.
  - `App.vue` — the main component of the app.

- `vite.config.js` — configuration for Vite.

- `package.json` — file with dependencies and project scripts.

## Production Build

To build and preview the project for production:

1. Build the project:

    ```bash
    npm run build
    ```

2. Preview the production build:

    ```bash
    npm run preview
    ```

## License

This project is open-source and available under the MIT license.
