# Alabama Maps

The class for scraping metadata and images from [Alabama Maps' Historical Map Archive](http://alabamamaps.ua.edu/historicalmaps/).

## Usage

Create a querier for Alabama Maps:

```python
from libquery_extensions import AlabamaMaps

directory = "./output/alabama-maps"
querier = AlabamaMaps(
    metadata_path=f"{directory}/metadata/metadata.jsonl",
    img_dir=f"{directory}/imgs",
)
```

Query metadata:

```python
base_url = "http://alabamamaps.ua.edu/historicalmaps/"
queries = [
    f"{base_url}worldwarI/index.html",
    f"{base_url}civilwar/unionroutes.html",
]
querier.fetch_metadata(queries=queries)
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
interface ProcessedMetadataEntry {
    uuid: string
    authors: string[] | null
    displayName: string
    publishDate?: TimePoint | [TimePoint, TimePoint]
    viewUrl: string
    downloadUrl: string
    md5?: string
    phash?: string
    resolution?: [number, number]
    fileSize?: number
    languages?: string[]
    tags: []
    abstract: null
    source: {
        name: 'Alabama Maps'
        url: string
        accessDate: string
    }
}
```
