# Todo API

A lightweight, high-performance REST API for managing todo items, built with Go and the Gin web framework. This API provides a clean and intuitive interface for creating, reading, and updating todo items with real-time status management.

Perfect for learning Go web development, building productivity applications, or as a foundation for more complex task management systems. The API follows RESTful conventions and returns JSON responses, making it easy to integrate with any frontend framework or mobile application.

## Features

- ✅ Get all todos
- ✅ Add new todos
- ✅ Get todo by ID
- ✅ Toggle todo completion status
- 🚀 Fast and lightweight
- 📝 JSON API responses
- 🎨 Beautiful frontend with HTML, Tailwind CSS & Vanilla JavaScript
- 🌐 CORS enabled for frontend integration
- 📱 Responsive design for mobile and desktop

## Prerequisites

- Go 1.16 or higher
- Git

## Installation

1. Clone the repository:

```bash
git clone https://github.com/noobconner21/go-todo-api.git
cd go-todo-api
```

2. Install dependencies:

```bash
go mod download
```

3. Run the application:

```bash
go run main.go
```

The server will start on `http://localhost:8080`

4. Open the frontend:

Open `index.html` in your browser or use a local server:

```bash
# Option 1: Open directly in browser
open index.html

# Option 2: Use Python's built-in server (if you have Python)
python3 -m http.server 3000
# Then open http://localhost:3000

# Option 3: Use Node.js http-server (if you have Node.js)
npx http-server -p 3000
# Then open http://localhost:3000
```

## API Endpoints

### Get All Todos

```
GET /todos
```

**Response:**

```json
[
  {
    "id": "1",
    "item": "Clean Room",
    "completed": false
  },
  {
    "id": "2",
    "item": "Read Book",
    "completed": false
  }
]
```

### Add New Todo

```
POST /todos
```

**Request Body:**

```json
{
  "id": "4",
  "item": "Learn Go",
  "completed": false
}
```

**Response:**

```json
{
  "id": "4",
  "item": "Learn Go",
  "completed": false
}
```

### Get Todo by ID

```
GET /todos/:id
```

**Example:** `GET /todos/1`

**Response:**

```json
{
  "id": "1",
  "item": "Clean Room",
  "completed": false
}
```

**Error Response (404):**

```json
{
  "message": "Todos not found"
}
```

### Toggle Todo Status

```
PATCH /todos/:id
```

**Example:** `PATCH /todos/1`

Toggles the completion status of the todo item.

**Response:**

```json
{
  "id": "1",
  "item": "Clean Room",
  "completed": true
}
```

**Error Response (404):**

```json
{
  "message": "Todo not found"
}
```

## Usage Examples

### Using curl

**Get all todos:**

```bash
curl http://localhost:8080/todos
```

**Add a new todo:**

```bash
curl -X POST http://localhost:8080/todos \
  -H "Content-Type: application/json" \
  -d '{"id":"4","item":"Learn Go","completed":false}'
```

**Get specific todo:**

```bash
curl http://localhost:8080/todos/1
```

**Toggle todo status:**

```bash
curl -X PATCH http://localhost:8080/todos/1
```

## Frontend Features

The included HTML frontend provides a modern, responsive interface with:

- 🎨 Modern gradient background and clean card-based layout
- 📊 Dashboard statistics (total, completed, pending)
- ➕ Add new todos instantly
- ✅ Mark todos as complete with one click
- 🔄 Real-time updates and notifications
- 📱 Fully responsive and touch-friendly

**Tech stack:** HTML, Tailwind CSS, and Vanilla JavaScript (no frameworks)

**Usage:**

1. Start the Go API server (`go run main.go`)
2. Open `index.html` in your browser (or use a local server)
3. Add, view, and complete todos directly from the web UI

## Project Structure

```
todo-api/
├── main.go          # Main application file with all handlers
├── index.html       # Frontend HTML file with Tailwind CSS
├── go.mod           # Go module file
├── go.sum           # Go dependencies checksum
└── README.md        # Project documentation
```

## Data Structure

The todo item structure:

```go
type todo struct {
    ID        string `json:"id"`
    Item      string `json:"item"`
    Completed bool   `json:"completed"`
}
```

## Dependencies

### Backend (Go)

- [Gin Web Framework](https://github.com/gin-gonic/gin) - HTTP web framework written in Go
- [Gin CORS Middleware](https://github.com/gin-contrib/cors) - CORS middleware for Gin

### Frontend

- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework
- Vanilla JavaScript (no frameworks)

## Development

### Running in Development Mode

```bash
go run main.go
```

### Building for Production

```bash
go build -o todo-api main.go
./todo-api
```

### Testing the API

You can test the API using tools like:

- [Postman](https://www.postman.com/)
- [Insomnia](https://insomnia.rest/)
- [HTTPie](https://httpie.io/)

## License

This project is open source and available under the [MIT License](LICENSE).

## Contact

For questions or suggestions, please open an issue in the repository.
