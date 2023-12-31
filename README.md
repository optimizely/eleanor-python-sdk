WARNING: This is not the supported Eleanor SDK. Please use https://github.com/optimizely/python-optiai

# Optimizely Python Library

[![pypi](https://img.shields.io/pypi/v/fern-optimizely.svg)](https://pypi.python.org/pypi/fern-optimizely)
[![fern shield](https://img.shields.io/badge/%F0%9F%8C%BF-SDK%20generated%20by%20Fern-brightgreen)](https://github.com/fern-api/fern)

## Installation

Add this dependency to your project's build file:

```bash
pip install fern-optimizely
# or
poetry add fern-optimizely
```

## Usage

```python
from optimizely.client import Optimizely

optimizely_client = Optimizely(
  token="API_TOKEN"
)

response = optimizely_client.models.get()

print(response)
```

## Async Client

```python
from optimizely.client import Optimizely
from optimizely import GetVoicesRequestMode

import asyncio

optimizely_client = Optimizely(
  token="API_TOKEN"
)

async def get_response() -> None:
    response = optimizely_client.models.get()
    print(response)

asyncio.run(get_response())
```

## Timeouts
By default, the client is configured to have a timeout of 60 seconds. You can customize this value at client instantiation. 

```python
from optimizely.client import Optimizely

optimizely_client = Optimizely(
  token="API_TOKEN",
  timeout-15
)
```

## Handling Exceptions
All exceptions thrown by the SDK will sublcass [optimizely.ApiError](./src/optimizely/core/api_error.py). 

```python
from optimizely.core import ApiError
from optimizely import BadRequestError

try:
  optimizely_client.models.get()
except BadRequestError as e: 
  # handle bad request error
except APIError as e:  
  # handle any api related error
```

Error codes are as followed:

| Status Code | Error Type                 |
| ----------- | -------------------------- |
| 400         | `BadRequestError`          |
| 401         | `UnauthorizedError`        |
| 403         | `ForbiddenError`           |
| 404         | `NotFoundError`            |
| 422         | `UnprocessableEntityError` |

## Beta status

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning the package version to a specific version in your pyproject.toml file. This way, you can install the same version each time without breaking changes unless you are intentionally looking for the latest version.

## Contributing

While we value open-source contributions to this SDK, this library is generated programmatically. Additions made directly to this library would have to be moved over to our generation code, otherwise they would be overwritten upon the next generated release. Feel free to open a PR as a proof of concept, but know that we will not be able to merge it as-is. We suggest opening an issue first to discuss with us!

On the other hand, contributions to the README are always very welcome!
