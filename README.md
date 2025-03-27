# Flatadango Movie Theater

**Project Description:**

Flatadango is a web application that allows users to browse movies and purchase tickets from the Flatiron Movie Theater. It provides a user-friendly interface to view movie details, check availability, and buy tickets.

**Core Features:**

* **Movie Details:** Displays the poster, title, runtime, showtime, and available tickets for the first movie on page load.
* **Movie List:** Shows a list of all movies on the left side of the page.
* **Ticket Purchase:** Allows users to buy tickets, updating the number of available tickets in real-time.
* **Sold Out Indicator:** Displays "Sold Out" for movies with no available tickets.
* **Movie Deletion:** Provides a "Delete" button to remove movies from the server.

**Project Setup Instructions:**

1.  **Clone the Repository:**
    ```bash
    git clone [repository URL]
    cd [project directory]
    ```

2.  **Install `json-server` (if you don't have it):**
    ```bash
    npm install -g json-server
    ```

3.  **Run `json-server`:**
    ```bash
    json-server --watch db.json
    ```

4.  **Open `index.html`:**
    Open `index.html` in your web browser.

**API Endpoints:**

* **GET /films/1:** Retrieves details for the first movie.
    * Example Response:
        ```json
        {
          "id": "1",
          "title": "The Giant Gila Monster",
          "runtime": "108",
          "capacity": 30,
          "showtime": "04:00PM",
          "tickets_sold": 27,
          "description": "A giant lizard terrorizes a rural Texas community and a heroic teenager attempts to destroy the creature.",
          "poster": "[https://www.gstatic.com/tv/thumb/v22vodart/2157/p2157_v_v8_ab.jpg](https://www.gstatic.com/tv/thumb/v22vodart/2157/p2157_v_v8_ab.jpg)"
        }
        ```
* **GET /films:** Retrieves a list of all movies.
    * Example Response:
        ```json
        [
           {
             "id": "1",
             "title": "The Giant Gila Monster",
             "runtime": "108",
             "capacity": 30,
             "showtime": "04:00PM",
             "tickets_sold": 27,
             "description": "A giant lizard terrorizes a rural Texas community and a heroic teenager attempts to destroy the creature.",
             "poster": "[https://www.gstatic.com/tv/thumb/v22vodart/2157/p2157_v_v8_ab.jpg](https://www.gstatic.com/tv/thumb/v22vodart/2157/p2157_v_v8_ab.jpg)"
           },
           {
             "id": "2",
             "title": "Manos: The Hands Of Fate",
             "runtime": "118",
             "capacity": 50,
             "showtime": "06:45PM",
             "tickets_sold": 44,
             "description": "A family gets lost on the road and stumbles upon a hidden, underground, devil-worshiping cult led by the fearsome Master and his servant Torgo.",
             "poster": "[https://www.gstatic.com/tv/thumb/v22vodart/47781/p47781_v_v8_ac.jpg](https://www.gstatic.com/tv/thumb/v22vodart/47781/p47781_v_v8_ac.jpg)"
           }
        ]
        ```
* **PATCH /films/:id:** Updates the `tickets_sold` count for a movie.
    * Request Headers:
        ```
        Content-Type: application/json
        ```
    * Request Body:
        ```json
        {
          "tickets_sold": 28
        }
        ```
    * Example Response:
        ```json
        {
           "id": "1",
           "title": "The Giant Gila Monster",
           "runtime": "108",
           "capacity": 30,
           "showtime": "04:00PM",
           "tickets_sold": 28,
           "description": "A giant lizard terrorizes a rural Texas community and a heroic teenager attempts to destroy the creature.",
           "poster": "[https://www.gstatic.com/tv/thumb/v22vodart/2157/p2157_v_v8_ab.jpg](https://www.gstatic.com/tv/thumb/v22vodart/2157/p2157_v_v8_ab.jpg)"
        }
        ```
* **POST /tickets:** Creates a new ticket purchase record.
    * Request Body:
        ```json
        {
           "film_id": "28",
           "number_of_tickets": 5
        }
        ```
    * Example Response:
        ```json
        {
           "id": "1",
           "film_id": "28",
           "number_of_tickets": 5
        }
        ```
* **DELETE /films/:id:** Deletes a movie from the server.
    * Example Response:
        ```json
        {}
        ```

**HTML Structure:**

* `ul#films`: Contains the list of movies.
    * `li.film item`: Represents a movie in the list.
    * `li.sold-out film item`: Represents a sold-out movie.

**Notes:**

* Make sure to replace `[repository URL]` and `[link-to-your-demo-gif-here]` with your actual information.
* You can customize the styling and layout as needed.
* The `json-server` will be used to serve the data from the `db.json` file.
* The `db.json` file should be located in the root directory of the project.
* The `db.json` file should contain the data for the movies and tickets.