# Get Started

libprocess_extensions is a collection of functions for processing the metadata and images in digital libraries retrieved with [libquery_extensions](https://github.com/oldvis/libquery_extensions).
The classes in libprocess_extensions inherit the classes in [libquery_extensions](https://github.com/oldvis/libquery_extensions).

## Installation

```sh
pip install libprocess_extensions
```

## Usage Example

```python
from libprocess_extensions import BritishLibraryCollectionItems

querier = BritishLibraryCollectionItems(
    query_path=f"./queries.jsonl",
    metadata_path=f"./metadata.jsonl",
    img_dir=f"./imgs",
)
querier.fetch_metadata(
    base_urls=[
        "https://www.bl.uk/collection-items?page=1",
    ]
)
```

More examples can be found in the API Reference.
