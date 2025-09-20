# glean-client

This is the client for the Glean API.

## Generating the client locally

To generate the client types locally, you need to have the Glean API running on your local machine.

1.  **Start the Glean API server.** Make sure the OpenAPI specification is available at `http://localhost:3000/spec`.
2.  **Generate the types.** Run the following command to generate the TypeScript types for the client:

    ```bash
    npm run generate:types:local
    ```

    This will use `openapi-typescript` to generate the types and save them in `src/types.ts`.

## TODO: Automated Client Generation

Currently, the client generation is a manual process. To improve this, we should automate the generation of the client whenever the API is updated.

Here's a plan to achieve this:

-   **Triggering the generation:** When the API is built and a new OpenAPI spec is generated, a trigger should be sent to this repository to start the client generation process. This could be a webhook or another CI/CD job.
-   **Workflow for generation:** A GitHub Actions workflow in this repository will be responsible for:
    1.  Receiving the trigger.
    3.  Running the `npm run generate:types` command.
    4.  Committing the newly generated `src/types.ts` file to the repository.
    5.  Version bump, creating a new release and publishing the updated client to npm.
