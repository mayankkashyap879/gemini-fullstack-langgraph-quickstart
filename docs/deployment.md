# Deployment Guide

This guide explains how to build the Docker image and run the full stack with `docker-compose`.

## Build the image

Run the build command from the project root:

```bash
docker build -t gemini-fullstack-langgraph -f Dockerfile .
```

This creates an image that contains the backend API and the optimized frontend build.

## Required environment variables

`docker-compose` needs two API keys when starting the stack:

- `GEMINI_API_KEY` – Google Gemini API key used by the LangGraph agent
- `LANGSMITH_API_KEY` – key for LangSmith logging

Pass them on the command line or export them before running `docker-compose up`.

## Accessing the services

Once the containers are running, open `http://localhost:8123/app/` to use the React frontend. The backend API is available at `http://localhost:8123`.

## External services and ports

The default `docker-compose.yml` spins up Redis and Postgres containers. To use external instances, set the `REDIS_URI` and `POSTGRES_URI` environment variables in the `langgraph-api` service. You can also edit the port mappings (for example `8123:8000` or `5433:5432`) if you need to expose different host ports.
