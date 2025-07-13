# Todo API

A simple REST API for managing todo items built with Go and the Gin web framework.

## Features

- ✅ Get all todos
- ✅ Add new todos
- ✅ Get todo by ID
- ✅ Toggle todo completion status
- 🚀 Fast and lightweight
- 📝 JSON API responses

## Prerequisites

- Go 1.16 or higher
- Git

## Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd todo-api
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

## Project Structure

```
todo-api/
├── main.go          # Main application file with all handlers
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

- [Gin Web Framework](https://github.com/gin-gonic/gin) - HTTP web framework written in Go

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
