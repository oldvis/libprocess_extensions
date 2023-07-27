# British Library Collection Items

The class for scraping metadata and images from [British Library Collection Items](https://www.bl.uk/collection-items).

## Usage

Create a querier for British Library Collection Items:

```python
from libquery_extensions import BritishLibraryCollectionItems

directory = "./output/british-library-collection-items"
querier = BritishLibraryCollectionItems(
    query_path=f"{directory}/queries/queries.jsonl",
    metadata_path=f"{directory}/metadata/metadata.jsonl",
    img_dir=f"{directory}/imgs",
)
```

Query metadata:

```python
base_urls = ["https://www.bl.uk/collection-items?page=1"]
querier.fetch_metadata(base_urls=base_urls)
```

Validate metadata:

```python
querier.validate_metadata()
```

Query images:

```python
querier.fetch_image()
```

Process metadata:

```python
querier.process_metadata(save_path=f"{directory}/processed/processed.json")
```

## Processed Metadata Schema

Each processed metadata entry is stored as:

```typescript
interface TimePoint {
    year: number
    month?: number
    day?: number
}

interface ProcessedMetadataEntry {
    uuid: string
    authors: string[]
    displayName: string
    publishDate: TimePoint | [TimePoint, TimePoint] | null
    viewUrl: string
    downloadUrl: string
    md5?: string
    phash?: string
    resolution?: [number, number]
    fileSize?: number
    languages: string[] | null
    tags: []
    abstract: string | null
    source: {
        name: string
        url: string
        accessDate: string
    }
}
```
