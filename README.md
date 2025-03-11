# Tercen gRPC API

This repository (`https://github.com/tercen/tercen_grpc_api.git`) contains the gRPC `.proto` files that define the Tercen gRPC API.
The API provides a set of services for interacting with Tercen, a platform for data analysis and workflow management. 
These `.proto` files specify the structure of requests, responses, and data models used in the Tercen ecosystem.

## Repository Structure

```
tercen_grpc_api/
├── tercen.proto          # Main service definitions
├── tercen_model.proto    # Data model definitions (assumed dependency)
└── README.md             # This file
```

## Services

Below is a list of services defined in `tercen.proto` with a brief description based on their messages:

- **`FileService`**  
  Manages file operations such as creating, retrieving, updating, deleting, uploading, and downloading files.
    - Example: `upload` streams file data and returns metadata; `download` streams file content.

- **`FolderService`**  
  Handles folder-related operations including creation, retrieval, updates, and deletion of folder documents.
    - Example: `create` and `update` manage folder metadata.

- **`TableSchemaService`**  
  Manages table schemas with operations for creation, retrieval, updates, deletion, and streaming table data.
    - Example: `uploadTable` processes table uploads; `streamTable` retrieves table data in chunks.

- **`TaskService`**  
  Controls task execution, including creating, retrieving, updating, deleting, running, canceling, and waiting for task completion.
    - Example: `runTask` initiates task execution; `waitDone` returns task results when finished.

- **`WorkflowService`**  
  Manages workflows by supporting creation, retrieval, updates, deletion, and specific operations like querying cubes or copying apps.
    - Example: `getCubeQuery` retrieves cube query details; `copyApp` duplicates workflows.

- **`UserService`**  
  Handles user management, authentication, and token generation.
    - Example: `connect` authenticates users; `createToken` generates session tokens.

- **`ProjectDocumentService`**  
  Manages project documents with operations for creation, retrieval, updates, deletion, and range-based searches.
    - Example: `findKeyRange` retrieves documents within a key range.

- **`TeamService`**  
  Provides team management functionality, including creation, retrieval, updates, and deletion of team entities.
    - Example: `create` sets up a new team.

- **`ProjectService`**  
  Manages projects with operations for creation, retrieval, updates, deletion, and range-based searches.
    - Example: `findKeyRange` retrieves projects within a key range.

- **`DocumentService`**  
  Handles generic document operations such as creation, retrieval, updates, deletion, and library retrieval.
    - Example: `getLibrary` fetches documents from a project library.

## Key Data Models

### `EDocument` Message

The `EDocument` message is a union type (`oneof`) that encapsulates various document subtypes used across the Tercen platform. Each subtype represents a specific entity type.

#### Subtypes of `EDocument`
- **`ComputedTableSchema`** - Represents a computed table schema with query results.
- **`CubeQueryTableSchema`** - Defines a table schema derived from a cube query.
- **`DockerOperator`** - Specifies a Docker-based operator for computations.
- **`DockerWebAppOperator`** - Defines a Docker-based web application operator.
- **`Document`** - A generic document with basic metadata.
- **`FileDocument`** - Represents a file with associated metadata and data URI.
- **`FolderDocument`** - Defines a folder structure within a project.
- **`GitOperator`** - Specifies a Git-based operator for version control integration.
- **`Operator`** - A generic operator for computations or processes.
- **`Project`** - Represents a project entity with metadata and ACLs.
- **`ProjectDocument`** - A generic project document linking to a project.
- **`RLibrary`** - Defines an R library package.
- **`ROperator`** - Specifies an R-based operator.
- **`RSourceLibrary`** - Represents an R source library with file references.
- **`RenvInstalledLibrary`** - Defines an installed R environment library.
- **`Schema`** - A generic schema for data tables.
- **`ShinyOperator`** - Specifies a Shiny-based operator for interactive apps.
- **`SubscriptionPlan`** - Represents a subscription plan with payment details.
- **`TableSchema`** - Defines a table schema with column definitions.
- **`Team`** - Represents a team entity with membership details.
- **`User`** - Defines a user entity with authentication details.
- **`WebAppOperator`** - Specifies a web application operator.
- **`WorkerEndpoint`** - Represents a worker endpoint for task execution.
- **`Workflow`** - Defines a workflow with steps and links.

### `ETask` Message

The `ETask` message is a union type (`oneof`) that represents various task subtypes for executing processes within Tercen.

#### Subtypes of `ETask`
- **`CSVTask`** - Processes CSV file imports into schemas.
- **`ComputationTask`** - Executes general computations with schema inputs.
- **`CreateGitOperatorTask`** - Creates a Git-based operator.
- **`CubeQueryTask`** - Runs a cube query to generate data.
- **`ExportTableTask`** - Exports table data to a specified format or location.
- **`ExportWorkflowTask`** - Exports an entire workflow.
- **`GitProjectTask`** - Manages Git project-related tasks.
- **`GlTask`** - Executes graphical or visualization tasks.
- **`ImportGitDatasetTask`** - Imports datasets from Git repositories.
- **`ImportGitWorkflowTask`** - Imports workflows from Git repositories.
- **`ImportWorkflowTask`** - Imports workflows from files.
- **`LibraryTask`** - Manages library-related operations.
- **`ProjectTask`** - Executes project-specific tasks.
- **`RunComputationTask`** - Runs a computation task with specific inputs.
- **`RunWebAppTask`** - Launches a web application task.
- **`RunWorkflowTask`** - Executes an entire workflow.
- **`SaveComputationResultTask`** - Saves results from a computation task.
- **`Task`** - A generic task with basic execution metadata.
- **`TestOperatorTask`** - Tests an operator's functionality.

## Usage

To use this API:
1. Clone the repository: `git clone https://github.com/tercen/tercen_grpc_api.git`
2. Generate gRPC code for your language using a protocol buffer compiler (e.g., `protoc`).
3. Integrate the generated code into your application to interact with Tercen services.

Refer to the `.proto` files for detailed message structures and service definitions.

