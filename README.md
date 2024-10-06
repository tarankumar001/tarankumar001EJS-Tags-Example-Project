
# EJS Tags Example Project

This project demonstrates the use of Embedded JavaScript (EJS) to dynamically render HTML content based on variables and conditions. It uses EJS for templating and dynamically generates a page that displays the current second, a list of items, and custom HTML content.

## Features

- **Dynamic Title:** The page title is dynamically set using the `title` variable.
- **Conditional Rendering:** Displays a list of items when the current second is even, or a message when it's odd.
- **HTML Injection:** Supports the inclusion of raw HTML content via the `htmlContent` variable.
- **Template Includes:** A footer is included using EJS's `include` function.

## Project Structure

```
 ├── views 
 │   ├── index.ejs        # Main EJS template file
 │   ├── footer.ejs       # Footer template file
 ├── public
 │   └── styles.css       # CSS file for styling (if any)
 ├── server.js            # Node.js server file to serve the EJS templates
 └── README.md            # Project documentation (this file)
```

### Template: `index.ejs`

The `index.ejs` file is the main template that includes:
- A dynamic title using the `<%= title %>` tag.
- The current second rendered using `<%= seconds %>`.
- Conditional logic that displays an unordered list if the current second is even and a message if it is odd.
- The inclusion of a footer template using `<%- include("footer.ejs") %>`.
- Raw HTML content passed in via `<%- htmlContent %>`.

### Example Code in `index.ejs`

```html
<h1><%= title %></h1>
<p>Current second: <%= seconds %></p>

<% if (seconds % 2 === 0) { %>
  <ul>
    <% items.forEach((fruit) => { %>
      <li><%= fruit %></li>
    <% }) %>
  </ul>
<% } else { %>
  <p>No items to display</p>
<% } %>

<p><%- htmlContent %></p>
<%- include("footer.ejs") %>
```

### Footer Template: `footer.ejs`

This file contains the HTML for the footer section of the page. It is included in `index.ejs` using the EJS `include` function.

### How to Run the Project

1. **Install Dependencies**: Make sure you have Node.js installed, then run:
```bash
npm install express ejs
```

2. **Run the Server**: Use the following command to start the server:
```bash
node server.js
```

3. **Access the Application**: Open your browser and go to:
```
http://localhost:3000
```

### Example Data

When rendering the `index.ejs`, the following data could be passed from the server:

```js
const data = {
  title: "EJS Example",
  seconds: new Date().getSeconds(),
  items: ["Apple", "Banana", "Cherry"],
  htmlContent: "<strong>Dynamic HTML content</strong>"
};
```

## License

This project is licensed under the MIT License. See the LICENSE file for details.
