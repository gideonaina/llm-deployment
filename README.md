# LLM Local Deployment

This repository provides a local deployment setup for a Large Language Model (LLM) using Docker and Docker Compose. The setup uses Ollama LLM with Open Web UI.
NOTE: All information & artifacts related to this deployment are local.

## Setup and Deployment

To run locally:
- Run  `make start` at the root of this project. This will set up Open Web UI for chatting and is deployed with the `llama3` model. 
- ~~To setup this stack with a different LLM like say `gemma2`, issue this command `make start LOCAL_LLM=gemma2`~~

*NOTE*: If you get an error while pulling the Open Web UI images, you might need to set up the Github container registry. Follow this instruction:
- To get access token go to Github Settings > Developer Settings > Personal access tokens
- From your terminal run
  ```echo YOUR_PERSONAL_ACCESS_TOKEN | docker login ghcr.io -u YOUR_GITHUB_USERNAME --password-stdin```
- You should now be authenticated to pull images from the GitHub Container registry.
 
### Chat UI
2. To access the chat UI, go to `http://localhost:3000`
3. Sign up with a local account and log in (Login information is local to the host machine).
4. Select a model to use for chat.
5. Chat away :)

### API Access.
Ollama exposes some endpoints that one can use to interact with the LLM model.
Some examples are below:

**Chat Endpoint**
```
$ curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "Why is the sky blue?"
}'
```

**Pull Model**

One can use multiple models in the Open Web UI. To pull a model run

`curl http://localhost:11434/api/pull -d '{"name": "llama3"}'`

**Check Models Available locally**
`curl http://localhost:11434/api/tags`



 
