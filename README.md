<!-- markdownlint-disable MD033 MD041 -->
<h1 align="center">
    model_deployer
</h1>

<p align="center">
    <strong>Turns your Python functions into microservices REST API in an instant.</strong>
</p>

<p align="center">
    <a href="https://pypi.org/project/opyrator/" title="Python Version"><img src="https://img.shields.io/badge/Python-3.6%2B-blue&style=flat"></a>
    <a href="https://github.com/dubuisa/model_deployer/blob/main/LICENSE" title="Project License"><img src="https://img.shields.io/badge/License-MIT-green.svg"></a>
    <a href="https://github.com/dubuisa/model_deployer/actions?query=workflow/CI" title="Build status"><img src="https://img.shields.io/github/workflow/status/dubuisa/model_deployer/CI?style=flat"></a>
</p>

<p align="center">
  <a href="#getting-started">Getting Started</a>
</p>

Instantly turn your Python functions into production-ready microservices. Deploy and access your services via REST API. model_deployer builds on open standards - OpenAPI,  JSON Schema, and Python type hints - and is powered by FastAPI, and Pydantic. It cuts out all the pain for productizing and sharing your Python code - or anything you can wrap into a single Python function.

This package is based on [opyrator](https://github.com/ml-tooling/opyrator) and was fork as the package was relying on older version of FastAPI and Starlette.


---

## Highlights

- Turn functions into production-ready services within seconds.
- Auto-generated HTTP API based on FastAPI.
- Save and share as self-contained executable file or Docker image.
- Instantly deploy and scale for production usage.
- Track and monitor API's call with correlation_id

## Getting Started

### Installation

> _Requirements: Python 3.7+._

```bash
pip install model_deployer
```

### Usage

1. A simple compatible function could look like this:

    ```python
    from pydantic import BaseModel

    class Input(BaseModel):
        message: str

    class Output(BaseModel):
        message: str

    def hello_world(input: Input) -> Output:
        """Returns the `message` of the input data."""
        return Output(message=input.message)
    ```

    _A compatible function is required to have an `input` parameter and return value based on [Pydantic models](https://pydantic-docs.helpmanual.io/) or an [UploadFile](https://fastapi.tiangolo.com/tutorial/request-files/#uploadfile). The input and output models are specified via [type hints](https://docs.python.org/3/library/typing.html)._

2. Copy this code to a file, e.g. `model.py`
3. Run the HTTP API server from command-line:

    ```bash
    model_deployer launch-api model:hello_world
    ```
    _In the output, there's a line that shows where your web service is being served, on your local machine._