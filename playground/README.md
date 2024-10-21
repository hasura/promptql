# Local PromptQL Playground

Contains docker compose files to get the local promptql playground server up an running.
This can be used via the "Local Development" section of the Hasura console - console.hasura.io (stable) or console.arusah.com (staging).

## Pre-requisites

- Have Hasura DDN (with SQL enabled) running somewhere (either Hasura cloud or locally).
- PromptQL key. Can be created by going to Hasura console -> Your project -> Settings -> PromptQL -> Enable PromptQL -> Generate API Key.
  - Make sure to grab a key from console.arusah.com if using the staging promptql runtime (wss://runtime.promptql.pro.arusah.com) or console.hasura.io if using the stable promptql runtime (wss://runtime.promptql.pro.hasura.io).
- LLM provider API key - either Anthropic or OpenAI.

## Running

```bash
PROMPTQL_SECRET_KEY=<promptql API key> HASURA_DDN_URL=<Hasura DDN SQL endpoint URL> LLM='<anthropic or openai>' ANTHROPIC_API_KEY=<anthropic API key> OPENAI_API_KEY=<openai api key> docker-compose -f staging.compose.yaml up
```
Note: You only need either ANTHROPIC_API_KEY or OPENAI_API_KEY

Example, with DDN running locally and anthropic as LLM provider.
```bash
PROMPTQL_SECRET_KEY=01234567-890a-bcde-f012-3456789abcde HASURA_DDN_URL=http://host.docker.internal:3080/v1/sql LLM=anthropic ANTHROPIC_API_KEY=sk-ant-api03-... docker-compose -f staging.compose.yaml up
```

## Playground Frontend

You can access the playground frontend at https://console.arusah.com/local/chat (staging) or https://console.hasura.io/local/chat (stable).

Click on the settings icon (gear) on the top-left and enter your Playground URL (http://localhost:5000 if you didn't make any changes to the docker compose).

Start doing things with the PromptQL assistant.