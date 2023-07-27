# British Library Images Online

The class for scraping metadata and images from [British Library Images Online](https://imagesonline.bl.uk).

## Usage

Create a querier for British Library Images Online:

```python
from libquery_extensions import BritishLibraryImagesOnline

directory = "./output/british-library-images-online"
querier = BritishLibraryImagesOnline(
    query_path=f"{directory}/queries/queries.jsonl",
    metadata_path=f"{directory}/metadata/metadata.jsonl",
    img_dir=f"{directory}/imgs",
)
```

Query metadata:

```python
base_urls = [
    "https://imagesonline.bl.uk/search/?searchQuery=chart",
    "https://imagesonline.bl.uk/search/?searchQuery=map",
]
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
