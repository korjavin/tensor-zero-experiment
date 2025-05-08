# TensorZero Experiment: Provider Comparison

This project is an experiment to test and compare different providers using TensorZero. The primary goal is to evaluate the performance of two providers, Mercury and DeepSeek, in generating data, and then use GPT-4-O to judge the generated outputs. Additionally, the experiment explores TensorZero's capabilities to build datasets based on the judged answers and leverage Dynamic In-Context Learning (DICL).

## Project Structure

```
.
├── docker-compose.yml
└── config/
    └── tensorzero.toml
```

### Files

- **`docker-compose.yml`**: Defines the services required for the experiment, including:
  - `clickhouse`: A database service for storing experiment data.
  - `gateway`: The TensorZero gateway for interacting with models via HTTP API.
  - `ui`: The TensorZero UI for monitoring and managing the experiment.

- **`config/tensorzero.toml`**: Configuration file specifying the models, providers, and functions used in the experiment.

## Configuration Details

### Models

1. **Diffuse**
   - Provider: `ollama`
   - Type: `openai`
   - API Base: `https://api.inceptionlabs.ai/v1`
   - Model Name: `mercury-coder-small`

2. **DS**
   - Provider: `ollama`
   - Type: `openai`
   - API Base: `https://api.deepseek.com`
   - Model Name: `deepseek-chat`

### Functions

- **`generate_haiku`**: A function to generate haikus using the `ds` model.

## Experiment Workflow

1. **Data Generation**:
   - Use the Mercury and DeepSeek providers to generate data based on predefined tasks (e.g., generating haikus).

2. **Judgment**:
   - Use GPT-4-O to evaluate the quality of the generated data and provide judgments.

3. **Dataset Building**:
   - Utilize TensorZero's capabilities to build a dataset from the judged answers.

4. **Dynamic In-Context Learning (DICL)**:
   - Experiment with DICL to improve model performance by dynamically updating the context based on the dataset.

## Running the Experiment

1. **Set Environment Variables**:
   - Ensure the `OPENAI_API_KEY` environment variable is set with a valid API key.

2. **Start Services**:
   Run the following command to start the services:
   ```sh
   docker-compose up
   ```

3. **Access the UI**:
   - TensorZero UI: [http://localhost:4000](http://localhost:4000)

4. **Monitor Gateway**:
   - Gateway Health: [http://localhost:3000/health](http://localhost:3000/health)

## Notes

- This setup is for experimental purposes only. For production-ready deployments, refer to the [TensorZero documentation](https://www.tensorzero.com/docs/gateway/deployment).
- The `tensorzero.toml` file is mounted into the containers to configure the models and functions.

## Purpose

This experiment aims to compare the performance of different providers (`ollama` with `openai`-based models) for tasks like generating haikus. The results will help determine the best provider for specific use cases and explore advanced features like DICL for dataset-driven improvements.